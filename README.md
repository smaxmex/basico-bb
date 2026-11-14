# BASICO-BB-C64

**BASado en Idioma Castellano y Operativo, derivado de BBC BASIC para Commodore 64*

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

Para ejecutar **BASILICO-BB-C64** en un emulador de Commodore 64 (ej. VICE, incluso en versión navegador/en línea) o en un Commodore 64 / 128 real:

1. Descargar el archivo PRG del sistema.
2. Cargarlo y ejecutarlo mediante el comando:
```basic
LOAD "BASILICO-BB",8
RUN
```

## Utilidad DISCO y gestión de archivos

El lenguaje original no dispone de comandos nativos para las operaciones de E/S en disco (como la lectura del directorio, el cambio de nombre de archivos, la inicialización o el formateo de un disquete). Para suplir esta carencia, dentro del repositorio se incluye la utilidad **DISCO**, que integra todas las funcionalidades de gestión de archivos necesarias.

## Ensamblador integrado

La utilidad DISCO está desarrollada íntegramente en ensamblador aprovechando el **ensamblador integrado** heredado de BBC BASIC. Durante la programación en ensamblador dentro del entorno BASILICO, conviene tener en cuenta algunas particularidades sintácticas y de arquitectura:

* **Mnemónico ORA**: La instrucción `ORA` (Logical OR with Accumulator) se expresa mediante el mnemónico **`L-OA`**.
* **Notación Hexadecimal**: El prefijo para los valores hexadecimales es **`&`** (en lugar del clásico símbolo `$` comúnmente empleado en los ensambladores para C64).
* **Acceso a los Registros de Vídeo/E/S (`&D020` / `&D021`)**: Para modificar directamente los colores de borde y fondo mediante las posiciones de memoria `&D020` y `&D021`, es indispensable conmutar previamente la configuración de memoria del registro de CPU `&01` para hacer visibles los registros de E/S en lugar de la ROM. El bloque de código debe estructurarse de la siguiente manera:

```assembly
SEI          ; Deshabilita las interrupciones
LDA &01
PHA          ; Guarda la configuración de memoria actual en la pila
LDA #&36     ; Selecciona el mapa de memoria con E/S habilitada
STA &01

; --- Inicio del código de modificación de registros de E/S (ej. &D020 / &D021) ---
; ...
; --- Fin del código de modificación ---

PLA          ; Restaura la configuración de memoria original
STA &01
CLI          ; Vuelve a habilitar las interrupciones
```
## Propiedad intelectual y notas sobre derechos

Este proyecto es una modificación de una obra preexistente y no reclama la titularidad del código fuente ni del binario original. La propiedad intelectual se divide de la siguiente manera:

* **BBC BASIC (Núcleo e implementación 6502)**: Todos los derechos relativos al código original pertenecen a **Acorn Computers Ltd.** (y a sus causahabientes).

* **Localización al español**: La traducción de los tokens, la adaptación de la sintaxis al español y la consiguiente reasignación de bytes corren a cargo del autor de este repositorio.

El código fuente original y los archivos derivados siguen sujetos a los respectivos avisos de derechos de autor de los titulares de los derechos (**Acorn Computers** y sus causahabientes).

## Créditos

Un agradecimiento especial a **Sophie Wilson** junto con **Acorn Computers** por la creación del lenguaje original.
