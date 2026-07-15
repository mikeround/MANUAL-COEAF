# Metodología para elaborar expedientes completos de autores y personajes

**Versión:** 1.0  
**Fecha:** 15 de julio de 2026  
**Ámbito:** `F:\IA\CEREBRO 1` y `F:\IA\EXPEDIENTE`  
**Resultado esperado:** un expediente independiente que combine un agente-personalidad y un cerebro documental verificable.

## 1. Qué es un expediente completo

Un expediente completo no es solo una biografía, un resumen de obras ni una colección de archivos. Es una unidad de conocimiento autosuficiente con dos capas que se controlan mutuamente:

1. **Agente-personalidad:** reconstruye cómo el autor define problemas, razona, compara evidencias, formula objeciones y responde. No intenta imitar gestos, acentos o frases teatrales.
2. **Cerebro documental:** conserva los textos, las variantes, la procedencia, los fragmentos de evidencia y un índice de búsqueda local. Impide que la personalidad se convierta en un estereotipo sin fuentes.

La regla fundamental es:

> Sin personalidad, el índice es una biblioteca pasiva. Sin corpus, la personalidad es una ficción no controlada.

El expediente debe poder copiarse fuera de CEREBRO 1 y seguir siendo utilizable. La carpeta contiene su propio corpus, base SQLite, buscador, manifiesto y controles de integridad.

## 2. Estructura común obligatoria

Cada autor se guarda en una carpeta con su nombre en mayúsculas:

```text
F:\IA\EXPEDIENTE\NOMBRE DEL AUTOR\
├── EXPEDIENTE_NOMBRE_DEL_AUTOR.md
├── AGENTE_PERSONALIDAD.md
├── PROMPT_AGENTE.md
├── REGLAS_Y_PRUEBAS.md
├── FUENTES.md
├── DICCIONARIO.md
├── MAPA_CONCEPTUAL.md
├── PREGUNTAS_DE_INVESTIGACION.md
├── GUIA_DE_USO.md
├── LEEME.md
├── buscar.py
├── expediente_nombre_del_autor.sqlite3
├── corpus\
│   ├── primarias\
│   │   └── textos completos y variantes
│   └── secundarias\
│       └── fragmentos_contextuales.md
├── evidencias\
│   └── EVIDENCIAS_TEMATICAS.md
└── state\
    ├── manifest.json
    └── checksums.sha256
```

Puede haber archivos adicionales justificados, como el Word original de Platón o una síntesis anterior de Aristóteles, pero nunca deben faltar los módulos comunes.

## 3. Datos necesarios antes de empezar

### 3.1. Catálogo documental

La fuente de inventario es:

```text
F:\IA\CEREBRO 1\state\catalog.jsonl
```

Cada registro debe proporcionar, en la medida de lo posible:

- `id`: identificador estable.
- `title`: título catalogado.
- `author`: autor atribuido por el catálogo.
- `path`: ubicación del archivo original en `raw/`.
- `text_path`: texto extraído en `extracted/`.
- `status`: estado de extracción.
- `words`: número de palabras.
- `units`: páginas, fragmentos u otras unidades.
- `sha256`: huella criptográfica del original.
- `duplicate_of`: identificador de la copia canónica cuando existe duplicación documentada.
- `warnings`: problemas de codificación, contenedor o extracción.

### 3.2. Índice general de CEREBRO 1

La base general es:

```text
F:\IA\CEREBRO 1\state\brain.sqlite3
```

Se usa en modo de solo lectura para:

- localizar pasajes temáticos dentro de las fuentes primarias;
- encontrar menciones del autor en otras obras;
- construir evidencias con localizadores;
- detectar títulos opacos o fuentes mal catalogadas;
- separar corpus primario de recepción secundaria.

### 3.3. Archivos extraídos

Los textos de trabajo se leen desde:

```text
F:\IA\CEREBRO 1\extracted\
```

Los originales de `raw/` permanecen inmutables. El expediente copia el texto extraído; nunca modifica el documento original.

### 3.4. Información conceptual mínima

Antes de redactar la personalidad se necesitan:

- obras disponibles y obras ausentes;
- conceptos recurrentes;
- operaciones de razonamiento;
- tensiones internas;
- evolución entre épocas, géneros o series;
- riesgos de interpretación;
- diferencias entre voz del autor, personajes, editores e intérpretes;
- preguntas de control que puedan probarse en el corpus.

## 4. Proceso 1: inventario inicial del autor

### Objetivo

Encontrar todas las fuentes potencialmente relacionadas con una persona, incluso cuando el catálogo utiliza variantes ortográficas.

### Procedimiento

1. Buscar el apellido y sus variantes en `id`, `title`, `author` y `path`.
2. Normalizar mayúsculas, tildes y orden del nombre.
3. Reunir alias evidentes.
4. Contar fuentes utilizables, palabras y estados.
5. Enumerar títulos para detectar anomalías.
6. Comparar el inventario con las carpetas ya existentes en `EXPEDIENTE`.

### Ejemplo: Isaac Asimov

El catálogo utilizaba tres formas:

- `Isaac Asimov`
- `asimov, isaac`
- `Asimov, Isaac`

Sin unificarlas, el inventario habría contado 32, 4 y 3 fuentes separadas. Al normalizarlas se obtuvieron 39 testimonios utilizables y 885.712 palabras.

### Ejemplo: Max Weber

Las variantes eran:

- `Weber, Max`
- `Max Weber`

La unión produjo siete testimonios y 388.119 palabras.

### Caso especial: autores no confirmados

Heródoto, Nietzsche, Platón y Aristóteles aparecían en varias fuentes como `Autor no confirmado`. En esos casos no basta agrupar por el campo `author`; hay que identificar los textos por título, ruta, contenido interno e identificador.

## 5. Proceso 2: clasificación de fuentes

Cada fuente candidata se asigna a una función.

### 5.1. Fuente primaria

Texto atribuido al autor y utilizable como evidencia directa. Puede ser una obra completa, un cuento, un ensayo, una carta o un volumen.

### 5.2. Variante primaria

Otra edición o extracción de la misma obra. Se conserva cuando su contenido, extensión o huella difieren.

Ejemplo: *Rendezvous with Rama* aparece en varios testimonios. No se eliminan automáticamente porque tienen hashes y estructuras distintas.

### 5.3. Coautoría

Texto producido con otra persona. Se incorpora con una función explícita y nunca se usa como voz individual incontestable.

Ejemplos de Arthur C. Clarke:

- *Cradle*, con Gentry Lee.
- *Rama II* y *Rama III*, con Gentry Lee.
- *The Light of Other Days*, con Stephen Baxter.

### 5.4. Fuente asociada, no primaria

Obra situada en el entorno del autor, pero escrita por otra persona.

Caso práctico: *Venus Prime Vol. 1* figuraba bajo Arthur C. Clarke, pero el propio archivo identifica a Paul Preuss como autor. Se excluyó de la voz primaria de Clarke.

### 5.5. Fuente secundaria o contextual

Texto que interpreta, menciona o reutiliza al autor. Sirve para recepción y contraste, no para atribuirle doctrinas.

Ejemplo: los ensayos de Foucault y Heidegger sobre Nietzsche se mantienen separados de la voz primaria de Nietzsche.

### 5.6. Duplicado

Archivo cuyo `sha256` coincide con otro o que está marcado mediante `duplicate_of`. Solo se conserva la copia canónica.

Ejemplos:

- una copia de *Caza mayor* de Asimov fue excluida como duplicado exacto;
- una copia de *The Sentinel* fue excluida en Clarke;
- una versión de *Homero y la filología clásica* fue excluida en Nietzsche.

## 6. Proceso 3: control de duplicados y variantes

El título no es suficiente para decidir si dos archivos son duplicados.

### Reglas

1. **Mismo hash:** duplicado binario. Se conserva una copia.
2. **`duplicate_of` informado:** se respeta el catálogo.
3. **Mismo título, hash distinto:** se conserva como variante hasta demostrar equivalencia.
4. **Extensiones o palabras muy diferentes:** se presume que hay diferencias editoriales o de extracción.
5. **Texto parcial frente a texto completo:** ambos pueden conservarse si la copia parcial aporta control de procedencia, pero la completa recibe prioridad.
6. **Coautoría o edición distinta:** se conserva y se etiqueta.

### Caso práctico: Esquirol, de Asimov

Existen dos fuentes con títulos cercanos y extensiones diferentes. No se eliminan por coincidencia nominal; quedan como testimonios separados.

### Caso práctico: Weber

*Política y ciencia* contiene *La política como vocación*, pero existe además un testimonio independiente de esta última. Se conservan ambos y el solapamiento queda documentado.

## 7. Proceso 4: evaluación de extracción

### Estados principales

- `extracted`: texto recuperado de forma satisfactoria.
- `partial`: contenido utilizable con ruido, pérdida de estructura, codificación o contenedor.
- `duplicate`: copia no incorporada como fuente independiente.
- estado pendiente o fallido: no se incorpora hasta rescatar el contenido.

### Qué significa realmente `partial`

No siempre significa que falten páginas. Puede indicar:

- RTF con códigos de formato visibles;
- TXT sin paginación;
- codificación antigua;
- contenedor que impide reconstruir unidades;
- caracteres dañados;
- texto completo tratado como una sola unidad.

### Ejemplos

- En Max Weber, dos RTF conservan el contenido, pero incluyen ruido de contenedor.
- En Clarke, muchos TXT están marcados como parciales porque no conservan paginación fiable.
- En Nietzsche, la fuente local de *La genealogía de la moral* solo representa su segunda parte y se documenta como cobertura incompleta.

### Localizadores

Cuando el texto contiene marcadores como:

```text
[[PAGE 238]]
```

el expediente utiliza `p. 238`. Si no hay paginación fiable, utiliza `fragmento 1`, `fragmento 2`, etc. Nunca se inventa una página.

## 8. Proceso 5: definición del alcance

Antes de escribir se establece qué puede y qué no puede representar el expediente.

### Preguntas obligatorias

- ¿Cuántas obras únicas hay?
- ¿Cuántos testimonios o variantes?
- ¿Cuántas palabras primarias?
- ¿Qué géneros están representados?
- ¿Qué etapas faltan?
- ¿Hay correspondencia, notas, ediciones críticas o solo traducciones?
- ¿Existen textos de autoría dudosa?
- ¿Hay compilaciones o extractos presentados como libros?
- ¿Qué conclusiones quedarían debilitadas por las ausencias?

### Ejemplos

- Platón dispone de 21 obras y 29 testimonios, pero faltan *Leyes*, *Parménides*, *Sofista*, *Teeteto* y *Filebo*.
- Aristóteles carece de *Órganon*, *Retórica* y tratados biológicos completos.
- Asimov tiene un corpus amplio, pero la serie Fundación no está completa.
- Weber no dispone de *La ética protestante y el espíritu del capitalismo* como volumen completo.
- Clarke carece de obras relevantes como *The City and the Stars* y *The Songs of Distant Earth*.

El expediente se declara completo respecto de CEREBRO 1, nunca respecto de la bibliografía histórica total.

## 9. Proceso 6: jerarquía epistémica

Toda afirmación se clasifica según su autoridad.

### FUENTE

Contenido directamente localizable en una obra primaria.

### CONTEXTO EDITORIAL

Introducción, prólogo o nota de una edición. No es automáticamente voz del autor.

### CONTEXTO SECUNDARIO

Interpretación de otro autor.

### SÍNTESIS

Integración razonada de varias fuentes primarias.

### INFERENCIA

Reconstrucción probable de cómo razonaría el autor ante un problema no tratado directamente.

### INCERTIDUMBRE

Conclusión que el corpus no permite cerrar.

### Caso práctico

Una respuesta nietzscheana no puede atribuirle directamente una formulación de Foucault. Puede decir:

```text
FUENTE: Nietzsche analiza la genealogía de los valores en el corpus local.
CONTEXTO SECUNDARIO: Foucault reelabora la genealogía como análisis de procedencias y emergencias.
INFERENCIA: aplicado al problema actual, el agente examinaría quién obtiene poder al imponer esa categoría.
```

## 10. Proceso 7: redacción de los 17 bloques

El documento principal contiene siempre los bloques 0 a 16.

### 0. Definición y alcance

Explica qué contiene, número de fuentes, palabras, jerarquía de autoridad y advertencias.

### 1. Resultado ejecutivo

Condensa en uno o dos párrafos el problema central del autor. Debe ser suficientemente específico para diferenciarlo de otros perfiles.

Ejemplo:

- Asimov: la ficción como laboratorio de reglas y consecuencias.
- Weber: comprensión del sentido y explicación causal de órdenes históricos.
- Heródoto: investigación de versiones, costumbres y causas del conflicto.

### 2. Corpus primario localizado

Resume obras, testimonios, variantes, géneros y estados.

### 3. Núcleo de identidad intelectual

Describe operaciones estables, no adjetivos vagos. Es mejor escribir "distingue poder, dominación y legitimidad" que "es profundo y analítico".

### 4. Perfil cognitivo y estilo de razonamiento

Reconstruye una secuencia ejecutable: cómo formula una pregunta, qué evidencia busca, qué distinciones introduce y cómo concluye.

### 5. Mapa doctrinal transversal

Relaciona conceptos que aparecen en varias obras. No es un glosario aislado; muestra dependencias.

### 6. Perfil de personalidad operativa

Convierte los patrones en comportamiento conversacional: tono, ritmo, tipos de preguntas, tolerancia a la incertidumbre y criterios de calidad.

### 7. Tensiones internas

Preserva contradicciones y cambios. No fuerza una unidad artificial.

Ejemplos:

- Nietzsche: perspectivismo y comparación de perspectivas.
- Weber: relación con valores y neutralidad del análisis.
- Clarke: optimismo tecnológico y riesgo existencial.

### 8. Matriz obra por obra

Registra título, función, estado, palabras, procedencia y, cuando procede, coautoría o variante.

### 9. Reglas de uso como personalidad

Define conductas obligatorias y prohibidas.

### 10. Pruebas de consistencia

Convierte la fidelidad en preguntas verificables.

### 11. Fuentes secundarias y contexto

Separa recepción de voz primaria. Si no existen fuentes suficientemente sustantivas, la sección permanece vacía y lo declara.

### 12. Límites y lagunas

Documenta ausencias, extracciones parciales, traducciones, autorías y cobertura incompleta.

### 13. Índice técnico

Lista cada fuente con ruta, estado, palabras y archivo local.

### 14. Pasajes de control

Remite a `EVIDENCIAS_TEMATICAS.md` y explica cómo ampliar contexto.

### 15. Conclusión

Explica qué combinación de personalidad y documentación hace singular al expediente.

### 16. Protocolo de actualización

Define cómo añadir nuevas obras sin perder procedencia ni consistencia.

## 11. Proceso 8: construcción del agente-personalidad

### 11.1. Tesis operativa

Debe describir una forma de trabajar, no una consigna decorativa.

Ejemplo weberiano:

```text
Comprender el sentido de la acción y explicar causalmente cómo produce órdenes históricos.
```

### 11.2. Operaciones dominantes

Se formulan con verbos:

- definir;
- distinguir;
- comparar;
- reconstruir;
- comprobar;
- contextualizar;
- objetar;
- graduar la certeza.

### 11.3. Secuencia de respuesta

Una secuencia general es:

1. Precisar la pregunta.
2. Identificar el concepto central.
3. Determinar si requiere fuente, síntesis o inferencia.
4. Recuperar evidencia.
5. Reconstruir el argumento.
6. Presentar tensiones y objeciones.
7. Concluir con grado de confianza.

Después se especializa.

Ejemplo platónico: definición, examen, refutación, objeción y aporía.  
Ejemplo aristotélico: distinción de sentidos, causas, potencia/acto, casos y conclusión graduada.  
Ejemplo freudiano: indicio, formación del conflicto, defensa, interpretación rival y límite clínico.  
Ejemplo asimoviano: reglas, restricción, anomalía, consecuencia y caso límite.

### 11.4. Tono

El tono deriva del método:

- Platón: interrogativo y examinador.
- Aristóteles: sobrio, clasificatorio y causal.
- Nietzsche: aforístico, genealógico y provocador, sin convertir la provocación en insulto.
- Weber: analítico, comparativo y atento a consecuencias.
- Asimov: claro, secuencial, racionalista y con ironía controlada.

### 11.5. Prohibiciones

- no inventar citas;
- no atribuir al autor hechos posteriores;
- no confundir personaje y autor;
- no ocultar coautorías;
- no presentar una hipótesis como evidencia;
- no completar lagunas sin avisar;
- no convertir conceptos ficticios en ciencia disponible;
- no adoptar sin crítica prejuicios históricos.

## 12. Proceso 9: prompt reutilizable

`PROMPT_AGENTE.md` contiene una instrucción breve que activa ambas capas.

Plantilla:

```text
Actúa como especialista en [AUTOR] construido exclusivamente desde este expediente.
Combina la personalidad intelectual descrita en AGENTE_PERSONALIDAD.md con
recuperación documental en la base SQLite. Antes de responder, precisa el
problema, busca evidencia cuando la afirmación sea textual o doctrinal,
distingue FUENTE, SÍNTESIS, INFERENCIA e INCERTIDUMBRE, presenta la mejor
objeción y concluye proporcionalmente a la evidencia. No inventes citas ni
ocultes lagunas, variantes o límites históricos.
```

El prompt no sustituye el expediente. Es una puerta de entrada que obliga al agente a consultarlo.

## 13. Proceso 10: evidencias temáticas

### Selección de temas

Cada perfil define consultas específicas. Ejemplos:

- Weber: `poder dominacion`, `burocracia funcionario`, `religion capitalismo`.
- Nietzsche: `verdad mentira`, `resentimiento culpa`, `zaratustra superhombre`.
- Asimov: `robot ley`, `fundacion imperio`, `entropia universo`.
- Clarke: `Rama ship`, `monolith human`, `God star`.
- Heródoto: `costumbres leyes`, `persas rey`, `griegos guerra`.

### Recuperación

La búsqueda se restringe a los identificadores primarios. Para cada tema se conservan los mejores pasajes según BM25, normalmente entre tres y cuatro.

### Extracto

El extracto se centra cerca de los términos encontrados, se normalizan espacios y se mantiene obra y localizador.

### Resultado

```markdown
## Estado y violencia legítima

### La política como vocación - fragmento 2

[extracto controlado]
```

Las evidencias no sustituyen la lectura completa. Funcionan como puntos de entrada y pruebas de trazabilidad.

## 14. Proceso 11: fuentes contextuales

El índice general se consulta con el apellido y variantes conceptuales:

```text
weber OR weberiano OR weberiana
nietzsche OR nietzscheano OR nietzscheana
```

Se exige un umbral mínimo de fragmentos para evitar llenar el expediente con menciones casuales. Normalmente se utilizan fuentes con cinco o más coincidencias sustantivas, limitando el número total.

### Caso práctico: Asimov

No se localizaron fuentes secundarias que alcanzaran el umbral. La sección permanece presente pero vacía. Es preferible declarar ausencia que introducir comentarios débiles.

### Caso práctico: Nietzsche

Se incorporó recepción de Foucault y Heidegger, siempre separada de la voz primaria.

## 15. Proceso 12: copia del corpus

Cada testimonio aceptado se copia desde `extracted/` a:

```text
corpus\primarias\NN_identificador.txt
```

El prefijo numérico estabiliza la navegación. El nombre incluye el identificador para preservar correspondencia con el catálogo.

El expediente no reescribe ni normaliza silenciosamente el contenido. Errores antiguos, ortografía, marcadores de página o ruido pueden mantenerse porque forman parte de la trazabilidad. Las correcciones analíticas se realizan en los documentos del expediente, no en el corpus preservado.

## 16. Proceso 13: construcción de SQLite

### Esquema

```sql
CREATE TABLE sources(
    id TEXT PRIMARY KEY,
    title TEXT,
    kind TEXT,
    origin TEXT
);

CREATE VIRTUAL TABLE chunks USING fts5(
    source_id UNINDEXED,
    locator UNINDEXED,
    content,
    tokenize='unicode61 remove_diacritics 2'
);
```

### Fragmentación

Los textos se dividen aproximadamente en bloques de 4.500 caracteres con 450 caracteres de solapamiento.

El solapamiento evita perder una idea situada justo en el límite entre dos bloques. El corte busca preferentemente un salto de línea o final de frase.

### Fuentes indexadas

La base incluye:

- corpus primario;
- variantes;
- fuentes contextuales seleccionadas;
- expediente principal;
- personalidad;
- prompt y reglas;
- fuentes y diccionario;
- evidencias temáticas.

### Búsqueda

`buscar.py` transforma una consulta en términos FTS5 y devuelve:

- título;
- tipo de fuente;
- localizador;
- fragmento resaltado;
- orden de relevancia BM25.

Ejemplo:

```powershell
python buscar.py "burocracia funcionario" 10
```

Resultado esperado:

```text
[1] Sociología del poder | primaria | p. 31
    ... tipo puro de >>>burocracia<<< ... cargo del >>>funcionario<<< ...
```

## 17. Proceso 14: manifiesto de procedencia

`state/manifest.json` registra:

- nombre del expediente;
- fecha de creación;
- origen;
- alias del autor;
- arquitectura 0-16;
- capas del expediente;
- lista de fuentes primarias;
- función de cada testimonio;
- palabras y unidades;
- rutas originales y extraídas;
- estado y advertencias;
- fuentes contextuales;
- limitaciones.

El manifiesto permite auditar el expediente sin leer todos los textos.

Ejemplo conceptual:

```json
{
  "id": "fuente-estable",
  "title": "Título",
  "role": "coautoría con otra persona",
  "source_path": "raw/original.pdf",
  "text_path": "extracted/original.txt",
  "status": "partial",
  "words": 78500,
  "sha256": "..."
}
```

## 18. Proceso 15: hashes de integridad

`state/checksums.sha256` contiene una huella de cada archivo del expediente, salvo el propio listado de hashes.

Formato:

```text
SHA256  ruta/relativa/del/archivo
```

### Finalidad

- detectar modificaciones accidentales;
- comprobar copias entre el área de preparación y `F:\IA\EXPEDIENTE`;
- asegurar que una base SQLite o un texto no quedó truncado;
- permitir futuras actualizaciones controladas.

Después de cualquier modificación material se regeneran todos los hashes.

## 19. Proceso 16: validación automática

Un expediente no se entrega solo porque los archivos existan.

### Pruebas obligatorias

1. Existe exactamente un documento `EXPEDIENTE_*.md` principal.
2. Existe exactamente una base `expediente_*.sqlite3`.
3. Están presentes los documentos y subdirectorios comunes.
4. El documento principal contiene los encabezados 0 a 16.
5. El número de TXT primarios coincide con `primary_witnesses` del manifiesto.
6. Todos los hashes coinciden.
7. Las tablas `sources` y `chunks` pueden leerse.
8. Una consulta FTS produce resultados.
9. El buscador funciona desde la ubicación final.
10. Una consulta temática recupera al menos una fuente primaria pertinente.

### Ejemplos de pruebas reales

- Asimov: `robot ley humano` recuperó *Yo, robot*, *El hombre bicentenario* y *Lenny*.
- Clarke: `Rama ship` recuperó testimonios de *Rendezvous with Rama*.
- Weber: `estado violencia legitima` recuperó *La política como vocación* y *Política y ciencia*.
- Nietzsche: `zaratustra superhombre` recuperó *Así habló Zaratustra*.
- Heródoto: `persas griegos guerra` recuperó los tomos primarios.

## 20. Proceso 17: instalación en EXPEDIENTE

La construcción se realiza primero en un área de preparación escribible. Solo después de superar las verificaciones se copia a:

```text
F:\IA\EXPEDIENTE\NOMBRE EN MAYÚSCULAS\
```

No se elimina el contenido anterior de forma destructiva. Los archivos originales o síntesis previas se preservan cuando aportan valor.

Después de copiar:

1. se vuelve a ejecutar la validación sobre `F:\IA\EXPEDIENTE`;
2. se prueba `buscar.py` desde esa carpeta;
3. se comparan hashes;
4. se confirma el número final de archivos.

La verificación del área de preparación no sustituye la comprobación de la ubicación final.

## 21. Casos prácticos completos

### 21.1. Platón: convertir una monografía en cerebro documental

Situación inicial: un único Word de 6.807 palabras, con 17 bloques conceptuales y referencias a CEREBRO 1.

Acciones:

1. extracción completa del Word a Markdown;
2. preservación del Word original;
3. identificación de 21 obras y 29 testimonios;
4. copia de 1.044.490 palabras;
5. creación de evidencias y contexto;
6. construcción de SQLite con 68 fuentes y 1.941 fragmentos;
7. incorporación de prompt, diccionario, mapa, manifiesto y hashes.

Aprendizaje: un documento interpretativo puede ser una excelente personalidad, pero no es todavía un cerebro independiente si no incorpora corpus e índice.

### 21.2. Aristóteles: convertir un cerebro documental en personalidad

Situación inicial: corpus, evidencias, buscador y síntesis documental, pero menor desarrollo de comportamiento conversacional.

Acciones:

1. conservación de la síntesis documental anterior;
2. reconstrucción de los bloques 0-16;
3. definición de operaciones: sentidos, categorías, causas, potencia/acto y casos;
4. creación de prompt y pruebas de consistencia;
5. reinserción de los nuevos documentos en SQLite;
6. regeneración de manifiesto y hashes.

Aprendizaje: la personalidad debe derivarse del método real del corpus, no de una lista de adjetivos.

### 21.3. Nietzsche: distinguir autor e intérpretes

Problemas encontrados:

- 26 testimonios primarios;
- una duplicación de *Homero y la filología clásica*;
- una *Genealogía de la moral* limitada a la segunda parte;
- estudios de Foucault y Heidegger;
- riesgos de apropiación política y lectura por consignas.

Solución:

- duplicado excluido;
- parcialidad documentada;
- recepción separada;
- reglas contra relativismo simplista, autoritarismo automático y confusión entre Nietzsche y Zaratustra;
- pruebas con `verdad mentira` y `zaratustra superhombre`.

### 21.4. Heródoto: corpus completo por volúmenes

Se localizaron nueve tomos extraídos, con 330.446 palabras. Cada tomo se preservó como testimonio primario. El perfil se orientó a investigación, comparación de versiones, geografía, costumbres, causalidad humana y divina, imperio y guerra.

Aprendizaje: una serie completa facilita la matriz, pero no elimina la necesidad de distinguir narrador, testimonios, discursos y relatos maravillosos.

### 21.5. Asimov: muchos textos y poca recepción secundaria

Se unificaron tres alias, se excluyó un duplicado y se documentaron cuatro extracciones parciales. El corpus tiene 39 testimonios y 885.712 palabras.

No hubo fuentes secundarias que superaran el umbral mínimo. La sección contextual se mantuvo vacía.

Aprendizaje: cantidad primaria no justifica rebajar el criterio de selección secundaria.

### 21.6. Clarke: atribuciones y coautorías

El inventario inicial mostraba 37 fuentes utilizables bajo varios alias. La auditoría interna reveló:

- *Venus Prime* escrito por Paul Preuss;
- coautorías con Gentry Lee;
- coautorías y variantes con Stephen Baxter;
- múltiples testimonios de Rama y Odisea;
- una duplicación exacta de *The Sentinel*.

Resultado: 36 testimonios incorporados y 1.603.251 palabras, con roles específicos.

Aprendizaje: el campo `author` del catálogo es un punto de partida, no una autoridad final.

### 21.7. Weber: extractos, compilaciones y solapamientos

Los siete testimonios incluyen una selección de *Economía y sociedad*, una compilación de dos conferencias y una versión independiente de *La política como vocación*.

La matriz registra estas funciones. Las limitaciones advierten que el expediente no contiene la obra completa ni una edición crítica integral.

Aprendizaje: contar archivos sin describir su función produciría una cobertura engañosa.

## 22. Casos de uso del expediente terminado

### Caso A: pregunta doctrinal

Pregunta: "¿Cómo entiende Weber la burocracia?"

Proceso:

1. buscar `burocracia funcionario`;
2. abrir los pasajes de *Sociología del poder*;
3. comprobar si el texto procede de la selección de *Economía y sociedad*;
4. responder distinguiendo descripción, ventajas técnicas y riesgos;
5. indicar la limitación editorial.

### Caso B: aplicación contemporánea

Pregunta: "¿Las Tres Leyes resolverían la seguridad de una IA actual?"

Proceso:

1. recuperar pasajes de Asimov sobre leyes y daño;
2. describir las leyes como dispositivo ficticio;
3. mostrar casos límite y conflictos de interpretación;
4. marcar la aplicación a sistemas actuales como INFERENCIA;
5. rechazar la idea de que constituyen una especificación técnica suficiente.

### Caso C: comparación de autores

Pregunta: "¿Cómo estudiarían Platón y Nietzsche el origen de un valor?"

Proceso:

- Platón pediría definición, fundamento y relación con el bien del alma y la ciudad.
- Nietzsche investigaría procedencia, fuerzas, beneficiarios, resentimiento y tipo de vida producido.
- la respuesta debe citar cada expediente por separado y evitar una síntesis que borre sus tensiones.

### Caso D: verificación de una cita

1. buscar palabras distintivas;
2. abrir el texto completo del resultado;
3. comprobar localizador y variante;
4. distinguir cita literal de paráfrasis;
5. si no aparece, declarar que el corpus local no permite confirmarla.

## 23. Criterios para decidir si un autor merece expediente

Un perfil completo requiere suficiente base. Indicadores favorables:

- varias obras o un corpus extenso;
- diversidad temática o cronológica;
- textos extraídos con calidad utilizable;
- posibilidad de distinguir voz primaria y recepción;
- conceptos recurrentes verificables;
- suficientes pasajes para construir pruebas;
- lagunas documentables.

No basta con que el nombre aparezca muchas veces. Un autor con una sola mención contextual no permite construir una personalidad fiable.

En caso de corpus pequeño, el expediente puede construirse, pero debe reducir sus pretensiones y declarar que representa solo las obras disponibles.

## 24. Errores que deben evitarse

1. Agrupar solo por el campo `author` y perder alias.
2. Considerar iguales dos archivos por compartir título.
3. Atribuir al autor una introducción editorial.
4. Ocultar coautorías.
5. Usar contexto secundario como voz primaria.
6. Inventar páginas en textos sin marcadores.
7. Convertir `partial` en sinónimo automático de inutilizable.
8. Presentar el expediente como bibliografía completa universal.
9. Crear una personalidad basada en tópicos.
10. Generar un buscador sin probar consultas reales.
11. Calcular hashes antes de la última modificación.
12. Verificar solo el área temporal y no la carpeta final.
13. Borrar versiones anteriores sin necesidad.
14. Introducir conocimiento externo sin marcarlo.
15. Resolver tensiones del autor para producir una voz artificialmente coherente.

## 25. Lista de comprobación reutilizable

### Inventario

- [ ] Buscar nombre, apellido y alias.
- [ ] Contar fuentes, palabras y estados.
- [ ] Revisar títulos y contenidos iniciales.
- [ ] Detectar autorías dudosas y coautorías.

### Corpus

- [ ] Excluir duplicados documentados.
- [ ] Conservar variantes justificadas.
- [ ] Copiar textos primarios.
- [ ] Construir contexto secundario con umbral.
- [ ] Documentar ausencias.

### Análisis

- [ ] Formular tesis operativa.
- [ ] Identificar operaciones cognitivas.
- [ ] Construir mapa doctrinal.
- [ ] Registrar tensiones y riesgos.
- [ ] Diseñar reglas y pruebas.
- [ ] Completar los bloques 0-16.

### Cerebro documental

- [ ] Crear evidencias temáticas.
- [ ] Construir SQLite FTS5.
- [ ] Generar `buscar.py`.
- [ ] Crear manifiesto.
- [ ] Calcular hashes.

### Verificación

- [ ] Comprobar archivos obligatorios.
- [ ] Confirmar encabezados 0-16.
- [ ] Comparar corpus con manifiesto.
- [ ] Validar todos los hashes.
- [ ] Ejecutar búsquedas temáticas.
- [ ] Copiar a `EXPEDIENTE`.
- [ ] Repetir verificación en destino.

## 26. Protocolo de actualización futura

Cuando se añade una obra:

1. identificar su autoría y estado;
2. calcular o comprobar su hash;
3. decidir si es obra, variante, duplicado, coautoría o contexto;
4. copiar el texto al corpus correcto;
5. añadir metadatos al manifiesto;
6. actualizar la matriz obra por obra;
7. comprobar si modifica la tesis, doctrinas, tensiones o límites;
8. generar nuevas evidencias;
9. reconstruir SQLite;
10. regenerar hashes;
11. ejecutar búsquedas de control;
12. incrementar la versión y conservar historial.

Una actualización no consiste únicamente en añadir un TXT. Debe comprobar si el nuevo material cambia la representación intelectual del autor.

## 27. Resultado de calidad esperado

Un expediente está terminado cuando:

- puede responder preguntas con evidencia local;
- distingue texto, síntesis e inferencia;
- conserva variantes y límites;
- no confunde autor, personaje, editor e intérprete;
- puede copiarse fuera de CEREBRO 1;
- ofrece una personalidad operativa específica;
- supera búsquedas reales;
- posee manifiesto y hashes válidos;
- declara honestamente aquello que no sabe.

Ese es el estándar aplicado a los expedientes actuales de `F:\IA\EXPEDIENTE`.
