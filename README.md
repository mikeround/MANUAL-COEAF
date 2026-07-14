# MANUAL COEAF

<!-- Imagen: colocar image_cere.png en images/image_cere.png o ajustar la ruta según donde la subas -->
![Imagen CEREBRO 1](images/image_cere.png)

> A continuación se incluye íntegramente el archivo `E-AgenteFil.md` para poder leerse directamente desde este README. Fuente original: [E-AgenteFil.md](https://github.com/mikeround/MANUAL-COEAF/blob/410484ea00446ca92e44c1de637052c72cd83ac1/E-AgenteFil.md).

# Manual para construir y operar un expediente-agente filosófico

> Arquitectura documental y cognitiva para reconstrucciones de Platón y Aristóteles con inteligencia artificial.

Este documento explica el proceso completo para convertir un corpus filosófico en un **agente reconstructivo documentado**, trazable y capaz de dialogar con otros agentes sin reducir el sistema a [...]

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
4. [Capa documental: qué textos entran y cómo se clasifican](#4-capa-documental-qu%C3%A9-textos-entran-y-c%C3%B3mo-se-clasifican)
5. [Conceptos técnicos clave](#5-conceptos-t%C3%A9cnicos-clave)
6. [Función de cada archivo](#6-funci%C3%B3n-de-cada-archivo)
7. [Proceso completo de construcción](#7-proceso-completo-de-construcci%C3%B3n)
8. [Cómo se carga la memoria en una IA](#8-c%C3%B3mo-se-carga-la-memoria-en-una-ia)
9. [Modos de despliegue](#9-modos-de-despliegue)
10. [Cómo mantener un diálogo entre Platón y Aristóteles](#10-c%C3%B3mo-mantener-un-di%C3%A1logo-entre-plat%C3%B3n-y-arist%C3%B3teles)
11. [Efecto de cada capa sobre el resultado final](#11-efecto-de-cada-capa-sobre-el-resultado-final)
12. [Pruebas de aceptación](#12-pruebas-de-aceptaci%C3%B3n)
13. [Límites del resultado](#13-l%C3%ADmites-del-resultado)
14. [Conclusión operativa](#14-conclusi%C3%B3n-operativa)
15. [Procedencia documental](#procedencia-documental)

<details>
<summary><strong>Petición original</strong></summary>

Analiza el expediente de Aristóteles o Platón y dime en qué consiste su estructura, explicando conceptos claves para su elaboración y efectos sobre el trabajo último que sería algo así como[...]

</details>

---

## 1. OBJETO REAL DEL SISTEMA

El resultado no consiste en «copiar la mente» de Aristóteles o Platón ni en introducir literalmente su memoria en una inteligencia artificial. Consiste en construir una representación operati[...]

1. lo que el autor puede sostener según el corpus disponible;
2. cómo tiende a definir, ordenar, objetar y concluir;
3. qué límites, contradicciones e incertidumbres deben conservarse.

El expediente de Aristóteles define expresamente esta arquitectura como la unión de dos capacidades inseparables:

- un agente-personalidad, que reconstruye una disciplina de razonamiento;
- un cerebro documental, que conserva fuentes, evidencias, procedencia, variantes y búsqueda.

La primera capa determina cómo razona el agente. La segunda determina con qué derecho documental puede afirmar algo. Cuando ambas funcionan juntas, la IA no se limita a hablar «con tono aristot[...]

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

Una personalidad sin cerebro documental produce una representación teatral y vulnerable a tópicos. Un cerebro documental sin personalidad produce un buscador o una síntesis académica sin una f[...]

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

Esta división es importante porque transforma un conjunto de libros en un sistema operativo comprensible. El documento principal no sustituye al corpus: actúa como mapa maestro que explica qué[...]

## 4. CAPA DOCUMENTAL: QUÉ TEXTOS ENTRAN Y CÓMO SE CLASIFICAN

### 4.1. Fuentes primarias

Son las obras atribuidas al autor que constituyen la autoridad principal. En el expediente aristotélico actual aparecen nueve obras únicas representadas por once testimonios: Acerca del alma; D[...]

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

Aportan interpretación, historia de recepción y contexto. En Aristóteles se conserva una monografía completa sobre el aristotelismo y su influencia. Su función es explicar recepción y trans[...]

### 4.3. Fuentes contextuales

Son fragmentos de otras obras de CEREBRO 1 que mencionan, interpretan o emplean conceptos aristotélicos. Sirven para comparación y recepción. Deben quedar identificados como contexto, porque u[...]

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

Es la cadena que permite regresar desde una afirmación hasta su archivo original, edición, ruta, estado de extracción y localizador. Sin procedencia, la respuesta puede sonar correcta pero no [...]

### 5.4. Localizador

Es la referencia interna que permite volver al pasaje: página cuando la extracción conserva paginación fiable, o número de fragmento cuando no la conserva.

### 5.5. Evidencia temática

Es una selección de pasajes de control organizada por conceptos: sustancia, causas, acto y potencia, alma, memoria, virtud, ciudadanía, mímesis, etc. No sustituye al texto completo, pero acele[...]

### 5.6. Síntesis

Es una reconstrucción transversal elaborada a partir de varias obras. Debe estar identificada como síntesis y no como formulación literal del autor.

### 5.7. Inferencia operativa

Es una regla derivada para hacer funcionar al agente: por ejemplo, que ante una pregunta Aristóteles distinga sentidos, clasifique el objeto, examine causas y gradúe la conclusión. Puede estar[...]

### 5.8. Tensión doctrinal

Es una dificultad que el expediente conserva sin resolver artificialmente: por ejemplo, teleología y contingencia, forma e individualidad, felicidad contemplativa y vida política, o ideal de ci[...]

### 5.9. Conocimiento negativo

Es el registro explícito de lo que falta. En el expediente aristotélico no están cubiertos de primera mano el Órganon, la Retórica ni los tratados biológicos completos, y la Poética está [...]

### 5.10. Recuperación documental

Es el mecanismo por el cual la IA busca sólo los fragmentos pertinentes para una pregunta. El expediente utiliza una base SQLite y un script de búsqueda. Esto permite trabajar con un corpus gra[...]

### 5.11. Integridad

Es la capacidad de verificar que los archivos no han cambiado silenciosamente. El manifiesto registra fuentes, rutas, estados, recuentos, advertencias y huellas SHA-256; el archivo de checksums p[...]

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
