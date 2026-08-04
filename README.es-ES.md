

# Kimchi Grammar

Este repositorio aloja los datos utilizados en la sección de gramática de Kimchi Reader, puedes verlo en vivo en [kimchi-reader.app/grammar](https://kimchi-reader.app/grammar).
Por ahora, contiene exclusivamente datos en forma de archivos .yaml, no se incluye código.

## Propósito y alcance

### Objetivos

- **Eficiencia:** El contenido gramatical de este repositorio está diseñado para ser conciso y directo, proporcionando explicaciones claras y precisas.
- **Orientado a la referencia:** Busca crear un recurso de referencia integral o tipo Wiki que pueda consultarse fácilmente.
- **Enfoque en la comprensión:** El contenido se centra principalmente en mejorar la comprensión de la gramática a través de la lectura y la escucha; este enfoque apoya a los estudiantes en la absorción natural de estructuras y usos gramaticales, con menos énfasis en la producción activa del idioma, como la escritura y la conversación.

### Objetivos excluidos

- **No es un curso:** Este repositorio no está diseñado para funcionar como un curso de idiomas estructurado ni como una serie de lecciones.

## Estructura del proyecto

| ruta               | detalles                                                                                                                                                                                                         |
|--------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `point/`           | Contiene los datos para los puntos gramaticales. Cada archivo `.yaml` corresponde a una página en el sitio web.                                                                                                                           |
| `comparison/`      | Estos datos se utilizan para enriquecer las páginas `point/*` con comparaciones.                                                                                                                                              |
| `relation.yaml`    | Este archivo se utiliza para generar el gráfico de relaciones entre los puntos gramaticales. Aún no he definido qué constituye exactamente una relación. Si crees tener una buena manera de organizar los datos aquí, por favor sugiérela. |
| `inheritance.yaml` | Documenta los bloques de construcción entre cada punto gramatical. Por ejemplo, existe `ㄹ_수_있다.yaml` y, en su interior, hace uso de `verb_ㄴ_은_는_ㄹ_을.yaml` para la primera parte.                                                         |

## Sintaxis Markdown personalizada

Dentro de los archivos .yaml, puedes utilizar markdown en los siguientes campos:

| carpeta              | campos             |
|---------------------|--------------------|
| `point/*.yaml`      | `details`          |
| `comparison/*.yaml` | `details`          |
| `comparison/*.yaml` | `points[].details` |

El markdown utilizado por Kimchi ha sido extendido con algunas directivas personalizadas, html, etc., como:

| sintaxis                                      | efecto                                                                                             | ejemplo                                                                                                                                  |
|---------------------------------------------|----------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------|
| `:dict[lemma]`                              | Crea un enlace a la entrada del diccionario `lemma`                                                        | `:dict[가다]`                                                                                                                              |
| `:dict[lemma]{word}`                        | Crea un enlace a la entrada del diccionario `lemma` con el texto `word`                                   | `:dict[가다]{가요}`                                                                                                                          |
| `:grammar[grammar_id]`                      | Crea un enlace a la entrada gramatical `grammar_id`                                                      | `:grammar[verb_며_으며]`                                                                                                                    |
| `:grammar[grammar_id]{slug}`                | Crea un enlace a la entrada gramatical `grammar_id` en la definición `slug`                             | `:grammar[noun_같이]{similarity}`                                                                                                          |
| `:grammar[grammar_id]{noprefix}`            | Crea un enlace a la entrada gramatical `grammar_id` sin el prefijo (Ej. V+)                          | `:grammar[noun_이다]{noprefix}`                                                                                                            |
| `:grammar[grammar_id]{noprefix slug}`       | Crea un enlace a la entrada gramatical `grammar_id` en la definición `slug` sin el prefijo (Ej. V+) | `:grammar[noun_은_는]{noprefix topic}`                                                                                                     |
| `::example[korean \| english]`              | Añade un ejemplo en el cuerpo con traducción                                                        | `::example[제<f>가</f> 할게요. \| I will do it.]`                                                                                             |
| `::example[korean \| english \| audio_url]` | Añade un ejemplo en el cuerpo con traducción y audio                                              | `::example[제<f>가</f> 할게요. \| I will do it. \| https://r2.kimchi-reader.app/grammar/제가_할게요__2024-04-13.mp3]`                              |
| `:correct[text]`                            | Muestra un ejemplo válido                                                                               | `:correct[새벽<f>같이</f> 떠나다]`                                                                                                              |
| `:wrong[text]`                              | Muestra un ejemplo inválido                                                                            | `:wrong[새벽<f>처럼</f> 떠나다]`                                                                                                                |
| `:source[url]`                              | Cita una fuente para la información                                                                  | `:source[https://namu.wiki/w/절#s-4.1]`                                                                                                   |
| `:::alert {rule}`                           | Inicia un bloque de reglas                                                                                 | [irregular_verb.yaml](https://github.com/Alaanor/kimchi-grammar/blob/a3315d175a29da4ca4d48916810745031570f1ef/point/irregular_verb.yaml) |
| `<f>text</f>`                               | Muestra el texto `text` en negrita y color                                                               | `<f>bold</f>`                                                                                                                            |

## Contribuciones

Las contribuciones son muy bienvenidas, no dudes en abrir un issue, hablar al respecto en el [Discord de Kimchi Reader](https://discord.gg/aEm5eDRpeZ) y/o abrir un pull request. Las contribuciones deben introducir cambios pequeños y enfocados que aborden aspectos específicos sin incluir modificaciones no relacionadas.

### Cómo contribuir

Normalmente, contribuir en un repositorio de GitHub requiere conocimientos de git. Hay cientos de tutoriales en internet y/o alternativamente siempre puedes pedir ayuda en nuestro servidor de Discord. El flujo de trabajo general es el siguiente:

1. Crea un fork (bifurcación) de Kimchi Grammar
2. Crea una nueva rama desde `main`
3. Aplica el cambio que deseas realizar (por ejemplo, crea un nuevo punto gramatical o edita uno existente: aquí es donde pasarás la mayor parte del tiempo)
4. Haz commit del cambio
5. Abre un pull request

> [!TIP]
> Todos estos pasos pueden realizarse directamente en el sitio web de GitHub sin instalar nada.

## Directrices y Nomenclatura

### Esquema para un punto gramatical

```yaml
name: [ Forma en hangul de la gramática, aparece en el diccionario emergente ]
definitions:
  - slug: [ Aparece al final de la URL en el navegador ]
    name: [ Resume la gramática en el diccionario emergente ]
    english_alternatives: [ Frases en inglés con significado similar ]
    meaning: [ Describe la gramática en una o dos oraciones ]
    examples:
      - type: simple
        sentence: [ Oración de ejemplo en coreano ]
        translated: [ Traducción al inglés de la oración en coreano ]
        audio_url: [ Lectura de audio generada, déjala en blanco ]
metadata:
  type: [ sustantivo, verbo o compuesto ]
details: |-
  [Usa la sintaxis markdown para explicar más detalles sobre la gramática]
```

En cuanto al nombre del archivo yaml en sí, puedes inspirarte en los archivos vecinos.

Una nota sobre el campo `type`. `noun` y `verb` se utilizan cuando la gramática relacionada solo se adjunta a un tipo determinado de palabra. `composite` es para puntos gramaticales que aparecen en un grupo de palabras. (Por ejemplo, `ㄹ 수 있다` es algo que se adjunta a 3 palabras)

### Directrices para nombrar puntos gramaticales

> [!TIP]
> Las directrices no son reglas estrictas, sino sugerencias para ayudar a mantener la coherencia y claridad en todo el contenido.

Donde corresponda, el campo `name` aparece en el diccionario emergente junto al punto gramatical. Mantén el nombre corto y consulta los ejemplos para obtener consejos sobre cómo nombrarlos. Si no estás seguro de cuál de los dos estilos de nomenclatura utilizar, elige el que parezca más simple y tenga sentido.

**Cuándo usar voz descriptiva activa**

- Al transmitir una emoción o intención específica:
    - "Expresa sorpresa" (para -네)

- Al describir la funcionalidad o propósito de un punto gramatical:
    - "Expresa posibilidad" (para -을 수 있다)

- Al reflejar la actitud o perspectiva del hablante:
    - "Transmite cortesía" (para -습니다/습니다)

**Qué evitar**

- Presente progresivo: "Indicando preocupación", "Expresando contraste"
- Tiempos no presentes: "Mostró intención", "Demostrará énfasis"
- Imperativo (orden): "Expresa sorpresa", "Clarifica la razón"
- Voz pasiva: "Cortesía transmitida"

**Cuándo usar etiquetas en lugar de voz activa**

- Descripciones neutras de la secuencia o estructura de una oración sin matices emocionales o intencionales.
    - "Causa y efecto" (para -기 때문에)
    - "Acciones simultáneas" (para -면서)

- Cuando el punto gramatical encaja en un propósito o categoría "gramatical" genérico.
    - "Condición" (para -면)
    - "Comparación" (para -보다)

- Indicar tiempo o aspecto
    - "Pasado" (para -았/었)
    - "Progresivo" o "En curso" (para -고 있다)

**Qué evitar**

- Términos técnicos o lingüísticos: "**Aspecto** progresivo", "Oraciones subordinadas".
- Los términos deben entenderse sin conocimientos lingüísticos más allá de conceptos gramaticales básicos, es decir, "verbo", "tiempo".

## Licencia

El contenido del repositorio Kimchi Grammar está disponible bajo la [Licencia Internacional de Atribución Creative Commons 4.0 (CC-BY 4.0)](LICENSE).
Esta licencia permite compartir, copiar, distribuir y transmitir la obra, o adaptarla para cualquier fin, incluso comercial, siempre que se dé el crédito correspondiente, se proporcione un enlace a la licencia y se indiquen los cambios realizados.

Ten en cuenta que el contenido de audio proporcionado en este repositorio se genera utilizando Elevenlabs y está licenciado bajo una licencia comercial separada.
El uso de este contenido de audio debe ajustarse a los términos especificados por la licencia comercial de Elevenlabs.
