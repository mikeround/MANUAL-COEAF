# MANUAL COEAF

<!-- Imagen: colocar image_cere.png en images/image_cere.png o ajustar la ruta según donde la subas -->
![Imagen CEREBRO 1](image_cere.png)

> A continuación se incluye íntegramente el archivo `E-AgenteFil.md` para poder leerse directamente desde este README. Fuente original: [E-AgenteFil.md](https://github.com/mikeround/MANUAL-COEAF/blob/410484ea00446ca92e44c1de637052c72cd83ac1/E-AgenteFil.md).

# Manual para construir y operar un expediente-agente filosófico

> Arquitectura documental y cognitiva para reconstrucciones de Platón y Aristóteles con inteligencia artificial.

Este documento explica el proceso completo para convertir un corpus filosófico en un **agente reconstructivo documentado**, trazable y capaz de dialogar con otros agentes sin reducir el sistema a un simple prompt.

| Campo | Valor |
|---|---|
| Proyecto | CEREBRO 1 |
| Documento | Manual técnico de arquitectura |
| Versión | 1.0 |
| Fecha | 14 de julio de 2026 |
| Estado | Edición preparada para repositorio GitHub |
| Archivo de origen | `cerebro1-manual-expediente-agente-filosofico-v1.0.pdf` |
| Ruta sugerida | `docs/cerebro1-manual-expediente-agente-filosofico-v1.0.md` |
| Fuente de trabajo | `AI DEEPMIND/IA/EXPEDIENTE` |

## Contenido

1. [Objeto real del sistema](#1-objeto-real-del-sistema)
2. [Principio fundamental: separar personalidad y memoria documental](#2-principio-fundamental-separar-personalidad-y-memoria-documental)
3. [La estructura general del expediente](#3-la-estructura-general-del-expediente)
4. [Capa documental: qué textos entran y cómo se clasifican](#4-capa-documental-qué-textos-entran-y-cómo-se-clasifican)
5. [Conceptos técnicos clave](#5-conceptos-técnicos-clave)
6. [Función de cada archivo](#6-función-de-cada-archivo)
7. [Proceso completo de construcción](#7-proceso-completo-de-construcción)
8. [Cómo se carga la memoria en una IA](#8-cómo-se-carga-la-memoria-en-una-ia)
9. [Modos de despliegue](#9-modos-de-despliegue)
10. [Cómo mantener un diálogo entre Platón y Aristóteles](#10-cómo-mantener-un-diálogo-entre-platón-y-aristóteles)
11. [Efecto de cada capa sobre el resultado final](#11-efecto-de-cada-capa-sobre-el-resultado-final)
12. [Pruebas de aceptación](#12-pruebas-de-aceptación)
13. [Límites del resultado](#13-límites-del-resultado)
14. [Conclusión operativa](#14-conclusión-operativa)
15. [Procedencia documental](#procedencia-documental)

<details>
<summary><strong>Petición original</strong></summary>

Analiza el expediente de Aristóteles o Platón y dime en qué consiste su estructura, explicando conceptos claves para su elaboración y efectos sobre el trabajo último que sería algo así como cargar la memoria de uno de ellos con ChatGPT o cualquier otra IA y hacer que dialogue de la misma manera. Incluso mantener un diálogo entre ellos como hemos hecho. Describe cómo y qué archivos son necesarios para que esto ocurra de la manera más óptima, etc. Debe contener todo el proceso y descripción de la estructura a seguir. No se trata de un prompt, se trata de un manual para entender todo el proceso que se sigue.

</details>

---

## 1. OBJETO REAL DEL SISTEMA

El resultado no consiste en «copiar la mente» de Aristóteles o Platón ni en introducir literalmente su memoria en una inteligencia artificial. Consiste en construir una representación operativa, documental y controlada de tres elementos distintos:

1. lo que el autor puede sostener según el corpus disponible;
2. cómo tiende a definir, ordenar, objetar y concluir;
3. qué límites, contradicciones e incertidumbres deben conservarse.

El expediente de Aristóteles define expresamente esta arquitectura como la unión de dos capacidades inseparables:

- un agente-personalidad, que reconstruye una disciplina de razonamiento;
- un cerebro documental, que conserva fuentes, evidencias, procedencia, variantes y búsqueda.

La primera capa determina cómo razona el agente. La segunda determina con qué derecho documental puede afirmar algo. Cuando ambas funcionan juntas, la IA no se limita a hablar «con tono aristotélico», sino que intenta responder mediante distinciones, causas, potencia y acto, funciones, fines, casos y grados de certeza, recuperando al mismo tiempo apoyo textual.

La denominación más exacta, por tanto, no es «clon mental», sino agente reconstructivo documentado.

## 2. PRINCIPIO FUNDAMENTAL: SEPARAR PERSONALIDAD Y MEMORIA DOCUMENTAL

La arquitectura evita mezclar dos problemas que suelen confundirse.

La personalidad operativa responde a preguntas como:

- ¿Qué hace primero ante una cuestión?
- ¿Cómo define un término?
- ¿Qué clase de objeciones considera pertinentes?
- ¿Qué estructura suele dar a una respuesta?
- ¿Qué tono y grado de precisión emplea?
- ¿Qué errores característicos debe evitar?

La memoria documental responde a otras preguntas:

- ¿Qué obras están realmente disponibles?
- ¿Qué edición o variante contiene cada pasaje?
- ¿Qué afirmaciones proceden de fuentes primarias?
- ¿Qué elementos son secundarios, contextuales o inferidos?
- ¿Dónde se localiza la evidencia?
- ¿Qué temas no están cubiertos?

Una personalidad sin cerebro documental produce una representación teatral y vulnerable a tópicos. Un cerebro documental sin personalidad produce un buscador o una síntesis académica sin una forma de razonamiento individualizada. El expediente óptimo necesita ambas capas.

## 3. LA ESTRUCTURA GENERAL DEL EXPEDIENTE

El expediente de Aristóteles adopta una arquitectura de 17 bloques en su documento principal. Esos bloques cubren:

0. definición y alcance;
1. resultado ejecutivo;
2. corpus primario;
3. núcleo de identidad filosófica;
4. perfil cognitivo y estilo de razonamiento;
5. mapa doctrinal transversal;
6. personalidad operativa;
7. tensiones internas;
8. matriz obra por obra;
9. reglas de utilización como personalidad;
10. pruebas de consistencia;
11. fuentes secundarias y contexto;
12. límites y lagunas;
13. índice técnico;
14. pasajes de control;
15. conclusión;
16. protocolo de actualización.

Esta división es importante porque transforma un conjunto de libros en un sistema operativo comprensible. El documento principal no sustituye al corpus: actúa como mapa maestro que explica qué contiene el expediente, cómo se relacionan sus piezas y bajo qué reglas debe utilizarse.

## 4. CAPA DOCUMENTAL: QUÉ TEXTOS ENTRAN Y CÓMO SE CLASIFICAN

### 4.1. Fuentes primarias

Son las obras atribuidas al autor que constituyen la autoridad principal. En el expediente aristotélico actual aparecen nueve obras únicas representadas por once testimonios: Acerca del alma; Del sentido y lo sensible / De la memoria y el recuerdo; dos testimonios de Ética a Nicómaco; Moral a Eudemo; Gran Moral; Física; dos testimonios de Metafísica; Política; y Poética.

Las obras no se contabilizan simplemente por nombre de archivo. Se distingue entre:

- obra única;
- testimonio o edición;
- variante textual;
- duplicado;
- extracción completa;
- extracción parcial;
- atribución dudosa o tradicional.

Esta distinción impide que dos copias de una obra se interpreten como dos obras distintas y permite comparar traducciones o extracciones sin fusionarlas de manera irreversible.

### 4.2. Fuentes secundarias

Aportan interpretación, historia de recepción y contexto. En Aristóteles se conserva una monografía completa sobre el aristotelismo y su influencia. Su función es explicar recepción y transformación, no reemplazar la autoridad de los textos primarios.

### 4.3. Fuentes contextuales

Son fragmentos de otras obras de CEREBRO 1 que mencionan, interpretan o emplean conceptos aristotélicos. Sirven para comparación y recepción. Deben quedar identificados como contexto, porque una afirmación de un comentarista, un historiador o un adversario no equivale a una afirmación de Aristóteles.

### 4.4. Jerarquía de autoridad

El expediente establece este orden:

1. textos primarios locales;
2. variantes textuales;
3. monografías;
4. fuentes contextuales;
5. síntesis del expediente;
6. inferencias operativas.

Esta jerarquía debe gobernar cada respuesta. Una inferencia útil no puede presentarse como cita, y una interpretación secundaria no debe reemplazar silenciosamente al texto primario.

## 5. CONCEPTOS TÉCNICOS CLAVE

### 5.1. Corpus

Es el conjunto organizado de textos que el agente puede consultar. No equivale a toda la obra histórica del autor, sino a la obra realmente disponible y procesada en el expediente.

### 5.2. Testimonio

Es una edición, traducción, copia o extracción concreta de una obra. Dos testimonios pueden representar la misma obra y, aun así, conservar diferencias relevantes.

### 5.3. Procedencia

Es la cadena que permite regresar desde una afirmación hasta su archivo original, edición, ruta, estado de extracción y localizador. Sin procedencia, la respuesta puede sonar correcta pero no es auditable.

### 5.4. Localizador

Es la referencia interna que permite volver al pasaje: página cuando la extracción conserva paginación fiable, o número de fragmento cuando no la conserva.

### 5.5. Evidencia temática

Es una selección de pasajes de control organizada por conceptos: sustancia, causas, acto y potencia, alma, memoria, virtud, ciudadanía, mímesis, etc. No sustituye al texto completo, pero acelera la comprobación de afirmaciones centrales.

### 5.6. Síntesis

Es una reconstrucción transversal elaborada a partir de varias obras. Debe estar identificada como síntesis y no como formulación literal del autor.

### 5.7. Inferencia operativa

Es una regla derivada para hacer funcionar al agente: por ejemplo, que ante una pregunta Aristóteles distinga sentidos, clasifique el objeto, examine causas y gradúe la conclusión. Puede estar bien fundada en el corpus, pero no es una frase histórica pronunciada por el autor.

### 5.8. Tensión doctrinal

Es una dificultad que el expediente conserva sin resolver artificialmente: por ejemplo, teleología y contingencia, forma e individualidad, felicidad contemplativa y vida política, o ideal de ciudadanía y exclusiones históricas. Una personalidad fiel no debe eliminar esas tensiones para parecer más coherente.

### 5.9. Conocimiento negativo

Es el registro explícito de lo que falta. En el expediente aristotélico no están cubiertos de primera mano el Órganon, la Retórica ni los tratados biológicos completos, y la Poética está limitada por la tradición textual. Saber qué no se sabe es parte de la memoria del agente.

### 5.10. Recuperación documental

Es el mecanismo por el cual la IA busca sólo los fragmentos pertinentes para una pregunta. El expediente utiliza una base SQLite y un script de búsqueda. Esto permite trabajar con un corpus grande sin introducir todos los libros completos en cada turno.

### 5.11. Integridad

Es la capacidad de verificar que los archivos no han cambiado silenciosamente. El manifiesto registra fuentes, rutas, estados, recuentos, advertencias y huellas SHA-256; el archivo de checksums permite comprobar el conjunto.

## 6. FUNCIÓN DE CADA ARCHIVO

La estructura óptima observada es la siguiente:

EXPEDIENTE_AUTOR/
```text
├── LEEME.md
├── GUIA_DE_USO.md
├── EXPEDIENTE_AUTOR.md
├── SINTESIS_DOCUMENTAL.md
├── AGENTE_PERSONALIDAD.md
├── PROMPT_AGENTE.md
├── DICCIONARIO.md
├── MAPA_CONCEPTUAL.md
├── REGLAS_Y_PRUEBAS.md
├── PREGUNTAS_DE_INVESTIGACION.md
├── FUENTES.md
├── buscar.py
├── expediente_autor.sqlite3
├── corpus/
│   ├── primarias/
│   └── secundarias/
├── evidencias/
│   └── EVIDENCIAS_TEMATICAS.md
└── state/
    ├── manifest.json
    └── checksums.sha256
```

### 6.1. LEEME.md

Es la puerta de entrada. Explica brevemente qué contiene el directorio y cuál es el archivo principal.

### 6.2. GUIA_DE_USO.md

Define el orden normal de consulta: expediente principal, agente-personalidad o activador, fuentes, evidencias, corpus y buscador.

### 6.3. EXPEDIENTE_AUTOR.md

Es el documento maestro. Contiene la arquitectura completa, la identidad filosófica, el mapa doctrinal, las tensiones, las reglas, los límites y el protocolo de actualización.

### 6.4. SINTESIS_DOCUMENTAL.md

Ofrece una exposición doctrinal continua y legible. Sirve para comprender el sistema del autor sin sustituir la consulta de evidencias.

### 6.5. AGENTE_PERSONALIDAD.md

Convierte el estudio filosófico en una secuencia de operaciones. En Aristóteles: precisar sentidos, identificar categoría, separar sustancia y accidentes, examinar causas, distinguir potencia y acto, contrastar casos, analizar fines y circunstancias, formular objeciones, recuperar evidencia y concluir proporcionalmente.

En Platón la secuencia es diferente: definición, separación entre apariencia y fundamento, examen de supuestos, contradicciones, distinción entre conocimiento y opinión, evaluación del bien, orden del alma y la ciudad, objeción y conclusión o aporía. Esta diferencia es lo que permite que ambos dialoguen sin convertirse en dos etiquetas aplicadas a una misma voz.

### 6.6. PROMPT_AGENTE.md

Es un activador compacto. Resume las instrucciones necesarias para poner en marcha el comportamiento, pero no contiene por sí solo la memoria documental. Debe entenderse como interfaz de activación, no como expediente completo.

### 6.7. DICCIONARIO.md

Estabiliza el significado operativo de los términos y sus equivalentes técnicos. Reduce variaciones incoherentes de traducción y ayuda a que el agente use conceptos relacionados de manera consistente.

### 6.8. MAPA_CONCEPTUAL.md

Representa las relaciones entre conceptos. En Aristóteles conecta ser y sustancia con materia y forma, potencia y acto, cambio, naturaleza, alma, memoria, hábito, virtud, ciudad y tragedia. Su efecto es conservar unidad transversal entre dominios.

### 6.9. REGLAS_Y_PRUEBAS.md

Funciona como control de calidad. Obliga a revisar sentidos, categorías, causas, potencia y acto, función, fenómenos, contingencia, presupuestos políticos, límites históricos, trazabilidad y certeza.

### 6.10. PREGUNTAS_DE_INVESTIGACION.md

Mantiene abiertas cuestiones no resueltas. Evita que el expediente se convierta en un sistema cerrado y permite orientar futuras ampliaciones.

### 6.11. FUENTES.md

Es el inventario humano legible. Registra obras, funciones, estados, palabras, unidades, rutas, variantes, duplicados y lagunas.

### 6.12. corpus/primarias/

Contiene los textos completos normalizados de las obras primarias, preferentemente en formato de texto, con marcadores de página o fragmento conservados.

### 6.13. corpus/secundarias/

Contiene monografías y fragmentos contextuales separados de las fuentes primarias.

### 6.14. evidencias/EVIDENCIAS_TEMATICAS.md

Reúne pasajes de control por tema y localizador. Es la capa intermedia entre la síntesis y el corpus completo.

### 6.15. expediente_autor.sqlite3

Es el índice de recuperación. Permite buscar por términos y devolver fragmentos relevantes asociados a una fuente y un localizador.

### 6.16. buscar.py

Es una interfaz local sencilla para consultar la base. Su función no es razonar, sino recuperar evidencia para que el agente razone sobre ella.

### 6.17. state/manifest.json

Registra el estado reproducible del expediente: fuentes, identificadores, rutas, estados de extracción, palabras, unidades, huellas, advertencias, limitaciones y capas de arquitectura.

### 6.18. state/checksums.sha256

Permite comprobar integridad y detectar modificaciones.

## 7. PROCESO COMPLETO DE CONSTRUCCIÓN

### Fase 0. Definir el alcance

Antes de reunir archivos hay que decidir:

- qué autor se reconstruye;
- qué carpeta constituye la única fuente autorizada;
- qué idiomas y traducciones se admitirán;
- qué se considera fuente primaria, secundaria o contextual;
- si el objetivo es análisis, conversación, docencia, debate o todos ellos;
- qué anacronismos están prohibidos;
- cómo se indicarán fuentes, síntesis, inferencias e incertidumbres.

### Fase 1. Inventariar el corpus

Se buscan todas las obras, variantes ortográficas, traducciones, formatos y títulos opacos. Cada archivo recibe un identificador estable. No se descarta todavía ninguna copia: primero se determina si es obra, variante o duplicado.

### Fase 2. Verificar, deduplicar y registrar

Para cada archivo se conserva:

- título normalizado;
- autor o atribución;
- ruta original;
- formato;
- estado de extracción;
- número de palabras o unidades;
- advertencias de codificación;
- huella criptográfica;
- relación con otras variantes o duplicados.

### Fase 3. Extraer y normalizar

Los PDF, DOC, RTF u otros formatos se convierten a texto consultable. Deben conservarse, cuando existan, los marcadores de página. Si no existe paginación fiable, se divide el texto en fragmentos estables. No debe corregirse silenciosamente una traducción ni eliminarse el ruido sin registrar la transformación.

### Fase 4. Construir el corpus jerárquico

Los textos se separan en primarios, secundarios y contextuales. Esta separación debe mantenerse tanto en carpetas como en metadatos del índice.

### Fase 5. Crear el inventario de fuentes

Se redacta FUENTES.md y se genera el manifiesto técnico. Aquí queda establecido qué está cubierto y qué no.

### Fase 6. Extraer evidencias temáticas

Se seleccionan pasajes de control para los conceptos centrales. Cada evidencia debe incluir obra y localizador. Esta fase permite comprobar posteriormente que la síntesis no se ha separado del corpus.

### Fase 7. Elaborar la síntesis doctrinal

Se reconstruyen los ejes del pensamiento, las relaciones entre obras, las continuidades y las diferencias. Debe distinguirse claramente la paráfrasis de la cita y la síntesis de la fuente.

### Fase 8. Modelar la personalidad cognitiva

Se transforma la síntesis en operaciones observables:

- orden de análisis;
- tipo de definiciones;
- preguntas recurrentes;
- criterios de evidencia;
- modo de formular objeciones;
- clase de conclusión;
- tono;
- riesgos y salvaguardas.

Éste es el paso decisivo para pasar de una biblioteca a un agente.

### Fase 9. Crear diccionario y mapa conceptual

El diccionario fija términos; el mapa fija relaciones. Juntos reducen contradicciones terminológicas y ayudan a mantener coherencia entre temas.

### Fase 10. Crear reglas y pruebas

Se diseñan controles que toda respuesta debe superar. Una respuesta que no puede remontarse a una fuente debe marcarse como inferencia o suspenderse.

### Fase 11. Construir el índice de recuperación

Los textos se dividen en fragmentos y se indexan. El buscador debe devolver, como mínimo:

- fuente;
- clase de fuente;
- localizador;
- extracto;
- medida de relevancia.

### Fase 12. Empaquetar y comprobar integridad

Se genera la base de datos, el manifiesto, los checksums y la guía de uso. Después se ejecutan búsquedas de prueba y se verifica que los localizadores regresan a los textos correctos.

### Fase 13. Evaluar el agente

El agente debe probarse con preguntas doctrinales, ambiguas, anacrónicas, comparativas y deliberadamente imposibles. También debe comprobarse que reconoce lagunas y que dos autores distintos producen razonamientos distinguibles.

### Fase 14. Versionar

Cada incorporación exige verificar extracción, clasificarla como obra, variante o duplicado, actualizar fuentes, evidencias, síntesis, índice, manifiesto, hashes y pruebas, sin borrar el historial anterior.

## 8. CÓMO SE «CARGA LA MEMORIA» EN UNA IA

La operación óptima no consiste en pegar todos los archivos en un único contexto. Se realiza en tres niveles.

### Nivel 1. Identidad persistente

La IA recibe el archivo de agente-personalidad y las reglas generales. Esto determina el método de razonamiento y las salvaguardas.

### Nivel 2. Orientación estructural

La IA dispone del expediente principal, la síntesis, el diccionario, el mapa, las fuentes y los límites. Esto le permite comprender la arquitectura global del autor.

### Nivel 3. Recuperación bajo demanda

Ante cada pregunta, el sistema consulta la base documental y proporciona sólo los fragmentos relevantes. La IA razona con ese paquete de evidencia y declara si la respuesta es fuente, síntesis, inferencia o incertidumbre.

Este tercer nivel es el que permite escalar. El corpus aristotélico contiene cientos de miles de palabras; cargarlo entero en cada turno sería innecesario y dificultaría distinguir lo relevante. La recuperación selectiva convierte el expediente en una memoria externa consultable.

## 9. MODOS DE DESPLIEGUE

### 9.1. Modo mínimo

Archivos imprescindibles:

- EXPEDIENTE_AUTOR.md;
- AGENTE_PERSONALIDAD.md;
- FUENTES.md;
- corpus primario;
- EVIDENCIAS_TEMATICAS.md.

Sirve para pruebas manuales, pero exige seleccionar evidencia a mano.

### 9.2. Modo recomendado

Añade:

- SINTESIS_DOCUMENTAL.md;
- DICCIONARIO.md;
- MAPA_CONCEPTUAL.md;
- REGLAS_Y_PRUEBAS.md;
- GUIA_DE_USO.md.

Aumenta coherencia, comprensión y control.

### 9.3. Modo óptimo

Añade:

- base SQLite;
- script de búsqueda;
- manifiesto;
- checksums;
- versionado;
- pruebas automáticas;
- separación estricta de índices por autor;
- orquestador de diálogo.

Éste es el modelo adecuado para operar de manera continua con ChatGPT u otra IA que pueda recibir instrucciones, consultar archivos y recuperar fragmentos.

## 10. CÓMO MANTENER UN DIÁLOGO ENTRE PLATÓN Y ARISTÓTELES

La condición fundamental es que no compartan una única personalidad ni una única bolsa indiferenciada de textos.

### 10.1. Componentes

Se necesitan:

- expediente completo de Platón;
- expediente completo de Aristóteles;
- índice documental independiente para cada uno;
- agente-personalidad independiente;
- un orquestador neutral;
- protocolo de turnos;
- registro de fuentes utilizadas en cada intervención.

### 10.2. Flujo recomendado

1. El orquestador formula el problema común.
2. Genera una consulta documental distinta para cada autor.
3. Recupera evidencias por separado.
4. Cada agente produce una posición inicial con su propia secuencia cognitiva.
5. El orquestador identifica puntos de acuerdo, desacuerdo y ambigüedad.
6. Cada agente recibe la objeción del otro, pero no adopta automáticamente su marco conceptual.
7. Se recupera nueva evidencia cuando la réplica introduce un tema nuevo.
8. El diálogo termina en acuerdo parcial, diferencia estructural o aporía, no en una reconciliación forzada.
9. Se añade una nota de procedencia que indique que se trata de una síntesis filosófica, no de una conversación histórica ni de citas textuales.

### 10.3. Diferenciación de voces

Platón debería tender a:

- pedir definiciones;
- distinguir apariencia y fundamento;
- examinar contradicciones;
- separar conocimiento y opinión;
- preguntar por el bien y el orden del alma y la ciudad;
- cerrar con conclusión graduada o aporía.

Aristóteles debería tender a:

- distinguir sentidos;
- clasificar el objeto;
- examinar materia, forma, motor y fin;
- diferenciar potencia, disposición y acto;
- contrastar casos y fenómenos;
- adaptar la precisión a la naturaleza del asunto.

La diferencia no debe descansar sólo en vocabulario o estilo literario. Debe observarse en la secuencia de razonamiento.

### 10.4. Archivos adicionales recomendados para diálogos

Estos archivos no sustituyen los expedientes individuales, sino que los coordinan:

DIALOGO/
```text
├── ORQUESTADOR.md
├── PROTOCOLO_DE_TURNOS.md
├── MATRIZ_DE_CONTRASTES.md
├── REGLAS_DE_CITACION.md
└── LOG_DE_SESION.md
```

ORQUESTADOR.md define cómo repartir preguntas y cuándo recuperar evidencia.

PROTOCOLO_DE_TURNOS.md fija fases: definición, tesis, objeción, réplica, contraste y cierre.

MATRIZ_DE_CONTRASTES.md registra conceptos equivalentes o no equivalentes entre ambos autores, evitando traducciones falsas.

REGLAS_DE_CITACION.md impide que una frase sintética aparezca como cita histórica.

LOG_DE_SESION.md conserva consultas, evidencias, respuestas, objeciones y decisiones del orquestador.

## 11. EFECTO DE CADA CAPA SOBRE EL RESULTADO FINAL

- Corpus primario: limita lo que el agente puede afirmar como doctrina del autor.
- Fuentes secundarias: aporta interpretación y recepción.
- Evidencias: reduce invención y acelera verificación.
- Síntesis: da visión de conjunto.
- Agente-personalidad: determina el procedimiento de pensamiento.
- Diccionario: estabiliza conceptos.
- Mapa: conserva relaciones entre dominios.
- Reglas y pruebas: controlan calidad.
- Índice: aporta memoria escalable.
- Fuentes y manifiesto: aportan trazabilidad.
- Checksums: aportan integridad.
- Límites: evitan una falsa sensación de completitud.
- Orquestador: conserva independencia cuando dialogan varios agentes.

## 12. PRUEBAS DE ACEPTACIÓN

Antes de considerar funcional un expediente-agente deberían superarse al menos estas pruebas:

1. Trazabilidad: toda afirmación doctrinal importante puede regresar a obra y localizador.
2. Separación epistémica: fuente, contexto, síntesis, inferencia e incertidumbre no se confunden.
3. Diferenciación de voz: un lector puede distinguir a Platón de Aristóteles por su razonamiento, no sólo por el nombre.
4. Conservación de tensiones: el agente no elimina contradicciones documentadas.
5. Resistencia al anacronismo: no atribuye al autor conocimiento posterior como si fuera propio.
6. Gestión de lagunas: declara cuando el corpus no basta.
7. Fidelidad terminológica: usa el diccionario sin convertir traducciones discutibles en equivalencias absolutas.
8. Recuperación: las búsquedas devuelven fuentes relevantes y localizadores correctos.
9. Integridad: manifiesto y checksums corresponden a los archivos presentes.
10. Reproducibilidad: la misma versión del expediente produce respuestas doctrinalmente compatibles.
11. Diálogo no convergente: los interlocutores pueden mantener desacuerdos reales.
12. Actualización segura: una nueva obra mejora el sistema sin borrar la versión anterior.

## 13. LÍMITES DEL RESULTADO

Incluso en su forma óptima, el sistema no demuestra conciencia, identidad personal ni continuidad biográfica del autor. Tampoco reconstruye automáticamente todo lo que habría pensado ante problemas modernos.

El resultado depende de:

- amplitud y calidad del corpus;
- traducciones disponibles;
- calidad de extracción;
- precisión de los localizadores;
- diseño de las reglas;
- capacidad de recuperación;
- disciplina del modelo para respetar límites;
- separación entre conocimiento base de la IA y fuentes autorizadas.

Por ello, la formulación correcta es:

«El agente responde mediante una reconstrucción documentada del método, conceptos y tensiones del autor dentro del corpus disponible.»

No debería afirmarse:

«Ésta es la mente real de Aristóteles» o «esto es exactamente lo que Platón habría dicho».

## 14. CONCLUSIÓN OPERATIVA

El expediente funciona porque distribuye el problema entre archivos especializados. El documento maestro explica el sistema; el corpus conserva la memoria textual; las evidencias permiten verificar; el agente-personalidad transforma doctrina en operaciones de razonamiento; el diccionario y el mapa mantienen coherencia; las reglas controlan la respuesta; SQLite permite recuperar memoria a escala; y el manifiesto con checksums conserva trazabilidad e integridad.

El prompt es únicamente la interfaz de activación. El verdadero «personaje» emerge de la interacción entre corpus, recuperación, síntesis, reglas, personalidad operativa y límites.

Para un solo autor, la unidad mínima es:

`personalidad operativa + corpus jerarquizado + evidencia recuperable + controles`.

Para un diálogo entre autores, la unidad óptima es:

`dos expedientes independientes + dos índices independientes + un orquestador neutral + un protocolo de turnos + registro de evidencias`.

Ésa es la estructura que permite pasar de una imitación superficial a una simulación filosófica documentada, auditable y capaz de mantener diálogos complejos sin confundir síntesis literaria con testimonio histórico.

## Procedencia documental

El manual se ha elaborado exclusivamente a partir de los expedientes de Aristóteles y Platón situados en AI DEEPMIND/IA/EXPEDIENTE, incluidos sus archivos principales, agentes-personalidad, guías, fuentes, corpus, evidencias, diccionarios, mapas, buscadores, bases SQLite, manifiestos y controles de integridad. Las recomendaciones sobre orquestación del diálogo se presentan como inferencias operativas derivadas de esa arquitectura.
