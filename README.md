# BASICO-BB-BBC

**BASado en Idioma Castellano y Operativo, derivado de BBC BASIC para BBC Micro**

BASICO-BB es una adaptación del célebre lenguaje **BBC BASIC**, caracterizada por la localización de los comandos al idioma español. En su estado actual, las palabras clave y las instrucciones de BASIC han sido traducidas en su totalidad, mientras que los mensajes de error aún se encuentran en fase de finalización.

## Compatibilidad e intercambiabilidad de los códigos fuente

Gracias a la estructura interna heredada de BBC BASIC, las instrucciones del lenguaje no se guardan como texto sin formato, sino en forma de **tokens numéricos**. Esto garantiza una total compatibilidad bidireccional entre los programas:

* **De BBC BASIC a BASICO**: Un programa guardado en BBC BASIC puede cargarse en BASICO. Las palabras clave se mostrarán e interpretarán automáticamente con sus comandos correspondientes en español.

* **De BASICO a BBC BASIC**: Un programa guardado en BASICO, una vez abierto de nuevo en el entorno original de BBC BASIC, mostrará y ejecutará los comandos en su forma estándar en inglés.

### Notas y advertencias sobre las variables

Aunque la estructura del código sigue siendo perfectamente compatible, se debe prestar atención a los **nombres de las variables**:

1. Dado que BASICO utiliza palabras clave en español, un nombre de variable válido en el BBC BASIC en inglés podría coincidir con una nueva instrucción reservada en BASICO (y viceversa), generando conflictos de sintaxis.

2. Siempre es recomendable elegir nombres de variables neutros o comprobar que no coincidan con las palabras clave tokenizadas de la versión de destino.

## Requisitos y uso

Para ejecutar **BASICO-BB** en un emulador de BBC Micro (ej. BeebEM):

1. Descargar el archivo `basico.rom`

2. Configurar el mencionado archivo como ROM de BASIC en el emulador de BBC Micro

3. Reiniciar el emulador ("Reset")

## Ensamblador integrado

El ensamblador integrado funciona, pero presenta algunas anomalías. Por ejemplo, la instrucción `ORA` del procesador 6502 en el ensamblador de BASICO se ha convertido en `L-OA`, utilizando el token `OR` de BBC BASIC. Se ha preferido priorizar la traducción al español (`L-O`) del comando `OR` en lugar de dejar intacta la instrucción `ORA` de ensamblador.

## Propiedad intelectual y notas sobre derechos

Este proyecto es una modificación de una obra preexistente y no reclama la titularidad del código fuente ni del binario original. La propiedad intelectual se divide de la siguiente manera:

* **BBC BASIC (Núcleo e implementación 6502)**: Todos los derechos relativos al código original pertenecen a **Acorn Computers Ltd.** (y a sus causahabientes).

* **Localización al español**: La traducción de los tokens, la adaptación de la sintaxis al español y la consiguiente reasignación de bytes corren a cargo del autor de este repositorio.

El código fuente original y los archivos derivados siguen sujetos a los respectivos avisos de derechos de autor de los titulares de los derechos (**Acorn Computers** y sus causahabientes).

## Créditos

Un agradecimiento especial a **Sophie Wilson** junto con **Acorn Computers** por la creación del lenguaje original.
