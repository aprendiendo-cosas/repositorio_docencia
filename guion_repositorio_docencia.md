# Repositorio de docencia



1. [_Objetivos_](#Objetivos)
2. [_Requisitos_](#Requisitos)
3. [_Estructura del sistema propuesto_](#Estructura del sistema propuesto)
    1. [_Definiciones de elementos principales_](#Definiciones de elementos principales)
    2. [_Estructura de un acto docente._](#Estructura de un acto docente)
        1. [_Actos docentes elementales_](#Actos docentes elementales)
        2. [_Actos docentes generales_](#Actos docentes generales)
        3. _carpetas controladas por git_
        4. _carpetas ignoradas_
        5. _esquemas con drawio_
        6. _mapas mentales con xmind_
        7. _archivos de gran tamaño_
        8. _proceso de publicación (rawcdn y más)_
    3. _criterios de denominación de repositorios_
    4. _releases y zenodo_
    5. _repositorios que agrupan actos docentes: asignaturas_
4. _Tareas a realizar_
    6. _Diseño gráfico guiones y webs._
    7. _automatización y simplificación de procesos: ¿cuáles?_
    8. _Manual de usuario_
    9. _Gestión adecuada de archivos grandes_
    10. _Soporte multiusuario_





## Objetivos

* Ordenar el material docente que se va generando para facilitar su acceso y su actualización periódica.
* Llevar un control de cambios que permita la adaptación del material creado a distintas titulaciones.
* Mejorar la coordinación con otros profesores.
* Aumentar la reproducibilidad de la actividad de los profesores.



## Requisitos

* La accesibilidad del material debe de estar controlada por los administradores. Algunas cosas abiertas y otras no accesibles.
* Control de cambios en los materiales creados.
* Flexibilidad en cuanto al contenido: código (en varios lenguajes), imágenes, videos, etc.
* Posibilidad de exportar el material a formatos inteligibles por alumnos sin demasiado conocimiento informático (ej. pdf, html, etc.)



## Estructura del sistema propuesto

La actividad docente tiene una serie de características que dificultan notablemente la construcción de un sistema como el requerido. La más relevante quizás es la “volatilidad” de los recursos docentes utilizados. Éstos se actualizan, cambian cada año y deben de ajustarse a las necesidades de los estudiantes, de los horarios y de los avances en la disciplina en cuestión. Esta complejidad es más intensa, si cabe, en una disciplina como la ecología en la que el grado de interacción entre las cuestiones abordadas es muy alto. 

El sistema propuesto aborda las dificultades anteriores y se basa en una serie de elementos principales:



### Definiciones de elementos principales


* Se define una “unidad elemental” de la docencia. Es lo que llamamos “acto docente”. Se define como un conjunto de materiales que se usa para satisfacer unos objetivos docentes bien acotados La clave ahora es definir qué significa “bien acotado”. La decisión sobre lo que contiene un acto docente recae sobre el profesor en cuestión. Es fácil identificar los límites en situaciones extremas, pero el problema está en la escala reducida. En el caso de la ecología, un acto docente puede ser el conjunto de materiales que se usan para que los estudiantes entiendan el término “sucesión ecológica”, por ejemplo. O un acto docente puede constar del material teórico suministrado para que aprendan el concepto anterior y otro acto docente el material práctico. Los límites de un acto docente vienen dados, en definitiva, por el desarrollo del curso en cuestión. Suelen asemejarse a los clásicos “temas” en los que se dividen las asignaturas. A pesar de la flexibilidad teórica, solemos tener actos docentes elementales que corresponden a los temas de teoría o a cada una de las prácticas y actos docentes generales, que resultan de agrupar los anteriores en asignaturas impartidas en un año concreto. 
* Independientemente de la definición de acto docente, un requisito clave es que su contenido sea actualizable y que dicha actualización esté documentada. Es decir, la evolución en el dominio del tiempo de un acto docente debe ser trazable. Para conseguir esto se ha establecido una relación unívoca entre el concepto de acto docente y el de “repositorio” en el sistema Git. Si bien los actos docentes pueden evolucionar de manera continua en la realidad lo hacen puntualmente. Es decir, cambian cada año. Esto permite crear versiones de cada acto docente. Usando la analogía con el procedimiento Git, cada versión corresponde con una “release”. En Git, cada release lleva asociada una fotografía fija del estado del repositorio en el momento en que se creó. Esta información se almacena en un archivo .zip. Es posible conectar los repositorios con la plataforma [Zenodo](https://zenodo.org/), que asocia un DOI a cada release de cada repositorio. 
* La ambigüedad con la que se define un acto docente puede generar problemas a la hora de llevarlo a la práctica. Estos problemas se pueden matizar si consideramos que hay una jerarquía en los actos docentes. Es decir, hay relaciones de “paternidad” entre los mismos. Muchos actos docentes se pueden agrupar en un momento determinado de su evolución. Esta agrupación permite crear un acto docente especial que se asemeja a la idea de “asignatura”. Este acto docente también es un repositorio dentro de Git. Por ello también puede evolucionar con el tiempo. Lo hace al hacerlo las versiones de los actos docentes que lo componen.



La siguiente figura muestra la estructura del sistema propuesto:

![estructura](https://raw.githubusercontent.com/aprendiendo-cosas/repositorio_docencia/main/imagenes/estructura_repositorios.png)

*Estructura general de todo el sistema. Se representan tres actos docentes elementales, que corresponden con aspectos teóricos ("Tema 8. Competencia interespecífica") y con aspectos prácticos ("Practica cuantificación tendencia NDVI" y "Teledetección"). En cada uno de ellos hay una evolucion continua de su contenido. Esto se representa por los sucesivos commits que afectan a los distintos elementos que lo componen (presentaciones, mapas mentales, bibliografía, código, etc.). Cada cierto tiempo se alcanza un estado que permite generar una versión concreta. Esto se "fija" mediante la creación de una release. Dado que el repositorio está conectado con Zenodo, se crea un DOI cada vez que se genera una release. Las distintas versiones de los actos docentes fundamentales ("hijos") se agrupan en otros repositorios que corresponden con asignaturas ("Ecología CCAA. 2019-2020", "Ecología CCAA. 2020-2021", etc.). En estos repositorios generales se pueden crear wikis o bien páginas html con enlaces a las releases de los actos docentes elementales*



### Estructura y tipos de actos docentes

Como hemos comentado más arriba, hay dos tipos de actos docentes. Los denominados "elementales" (que corresponden con temas de teoría, ejercicios o prácticas) y los "generales" (que agrupan varios elementos de los anteriores y configuran asignaturas). Cada uno de estos dos tipos tiene distinta estructura interna:



#### Actos docentes elementales

Un acto docente elemental puede contener multitud de elementos que se usan en el proceso de aprendizaje: presentaciones (powerpoint, canvas, prezi, etc.), mapas mentales, artículos, vídeos, etc. Para suministrar a los estudiantes toda esta información de manera ordenada y sistematizada, se organiza todo dentro de un guión. Se trata de un documento de texto (escrito en Markdown) que contiene información sobre la secuencia de actividades que ocurren en el acto docente (sesión teórica, práctica, salida de campo, laboratorio, etc.). Este guión tiene también metadatos (versión del documento, asignatura y grado al que va dirigido, autor, etc.). Además este documento contiene enlaces a elementos que se usan durante la sesión docente: videos de youtube, archivos en gdrive o en el moodle, etc. Los guiones tienen una estructura parecida y un diseño homogéneo. La siguiente figura muestra el encabezado tipo de un guión.


![estructura](https://raw.githubusercontent.com/aprendiendo-cosas/repositorio_docencia/main/imagenes/portada_guion.png)



Los repositorios en los que se almacena la información de este tipo de acto docente se nombran de la siguiente forma:

> [tipo_acto_docente]\_[nombre_acto_docente]\_[asignatura]\_[titulación]
>
> Siendo:
>
> + [tipo_acto_docente]:
>   + A: Actividad. 
>   + C: Salida de campo.
>   + P: práctica
>   + T: Tarea
>   + Te: Sesión teórica
>   + TP: Sesión teórico-práctica



Todos los actos docentes comparten la misma licencia de uso: GNU GPLv3. Además, casi todos ellos tienen comparten el mismo árbol de directorios:

+ *entregas*: Cuando esta carpeta está presente almacena las entregas que hacen los alumnos y que están relacionados con el acto docente en cuestión. No es registrado por GitHub.
+ *imagenes*: Carpeta en la que se guardan las imágenes que se muestran en el guión.
+ *preparacion*: En esta carpeta se almacenan los archivos temporales y otro material que no está terminado. Esta carpeta no se almacena en el repositorio de GitHub.
+ *presentacion*: Aquí se guardan los archivos powerpoint, mapas mentales o presentaciones de prezi que se usan en la clase.
+ *releases*: Esta carpeta contiene los archivos .zip que corresponden con las versiones anteriores del acto docente en cuestión. No es registrado por GitHub.
+ *videos_sesiones*: Aquí se guardan los vídeos de las grabaciones del acto docente. Tampoco se registra en GitHub.
+ *guion\_[nombre_acto_docente]\_[asignatura]\_[titulacion].md*: Corresponde con el guión en el que se enlazan los materiales descritos arriba.
+ *guion\_[nombre_acto_docente]\_[asignatura]\_[titulacion].html*: Contiene la misma información que el archivo anterior, pero en formato html para su publicación. 

A continuación se muestra el contenido del archivo *gitignore* de los repositorios específicos:

 ```
/preparacion
/releases
/videos_sesiones
/entregas
.DS_Store
 ```



#### Actos docentes generales

Los actos docentes específicos se pueden agrupar en otros generales que son asimilables a la idea de asignatura. Estas asignaturas se almacenan en un repositorio de Github que tiene un archivo Markdown por cada curso académico. En este archivo se listan los actos docentes que componen la asignatura, así como enlaces a los mismos. La siguiente imagen muestra el aspecto de uno de estos listados:



![estructura](https://raw.githubusercontent.com/aprendiendo-cosas/repositorio_docencia/main/imagenes/asignatura.png)



VAS POR AQUÍ, CHAVAL

* 
* las versiones de cada acto docente que afectan a distintas titulaciones, se consideran como forks o branches diferentes. Aún tengo que ver cómo funciona esta pana. Es decir, no sé bien cómo gestionar esto en local. En git parece fácil. En local no. Como ejejmplo reciente está la práctica de biodiversidad para el grado de UCO y para el Geoforest…
* 
* Criterios de denominación de releases: [año inicio curso académico - año final curso académico]. Ej 2019-2020.
* Posibles carpetas y contenido en el repositorio (en cursiva las que están en gitignore) que podría formar parte de una plantilla.
    * descargables: material útil para ser descargado.
    * imagenes: imágenes que se incrustan en el guión hecho en markdown
    * _preparacion_: cajón de sastre con cosas varias que se usan para prepara el acto docente.
    * presentaciones: Pues eso, las presentaciones.
    * _releases: _Archivos comprimidos que contienen las releases que se van creando para cada respositorio.
    * _Videos_sesiones: _Aquí se incluyen los vídeos que se graban de las sesiones. En los guiones de la sesión se pueden incrustar las URL de las subidas a youtube. 
    * guion_xxx.html: Incluir este archivo mola porque permite incrustar casi cualquier tipo de material. Lo malo es que Github no lo despliega de manera nativa, así que hay que usar: https://htmlpreview.github.io[/](https://htmlpreview.github.io/?[url)?[url del html en github]. Este link puede usarse para distribuir por Telegram. **El único problema que le he encontrado hasta ahora es que apunta a las versiones de los objetos que hay en la versión viva del repo.** Es decir, si borro un archivo, por ejemplo, este html apunta a la URL del archivo borrado, por lo que no funciona. Total, que este html puede ser muy útil para describir secuencialmente el contenido de la sesión actual del acto docente. Es lo que habría que poner en el moodle y en el telegram. 
* Cómo trabajar con los mapas mentales de xmind:
    * subir el xmind original.
    * Luego generar un html más o menos dinámico:
        * exportar el xmind a freemind.
        * Abrirlo en freemind
        * Exportar a html con javascript.
        * Subir los archivos exportados a github.
        * y ya se ve (usando pages de github).
        * Ejemplo aquí: [https://aprendiendo-cosas.github.io/Te_poblaciones_explotacion_ecologia_ccaa/presentacion/explotacion_poblaciones.html](https://aprendiendo-cosas.github.io/Te_poblaciones_explotacion_ecologia_ccaa/presentacion/explotacion_poblaciones.html)

**20/10/2021 Sobre creación de página general con contenidos de todo el curso.**

La idea es que haya una página que muestre los temas de cada curso en cada asignatura. Por ahora en esa página se muestra, para cada tema, lo siguiente:



* guión dinámico: link al html que hay en la rama principal del repositorio. Es lo que publica gitpages por defecto. Y no sé hacer que publique el html de la release del año en curso. He preguntado en el foro de gitpages. Pero mientras me contestan, usaré esta opción: 
    * [http://raw.githack.com/](http://raw.githack.com/). Pegas aquí la URL que te da github de cualquier html que haya en un repositorio (incluso bajo una tag) y te devuelve una URL publicada. Pero esto es una solución provisional.
* Descargar material: link a zenodo para bajar todo el material.
* ver material en github: link a la tag que caracteriza la versión del año en cuestión.

Para mejorar esto tengo que:



* Quizás añadir enlace a turnitin para subir los ejercicios.

**Estructura de las webs que agregan toda la información.**



* [Repositorio de docencia de Curro Bonet García](https://aprendiendo-cosas.github.io/index.html): Es la página principal. Está en un repo colgado de /Volumes/GoogleDrive/My Drive/4_docencia/general/repositorio_docencia/aprendiendo-cosas.github.io
* webs de cada asignatura:
    * [Ecología ccaa: ](https://aprendiendo-cosas.github.io/ecologia_CCAA_UCO/ecologia_ccaa_uco.html)Está en el repo llamado “ecologia_ccaa_UCO” /Volumes/GoogleDrive/My Drive/4_docencia/eco_ccaa_uco/actos_docentes/ecologia_CCAA_UCO
* Web de cada año de cada asignatura: EStá en el mismo repositorio de antes. El archivo se llama: “contenidos_ecologia_ccaa_[curso-academico].html”

**Base de datos de preguntas de examen**

**base de datos de evaluación de actividad docente**



* **Encuestas oficiales uco**
* **encuestas de cada acto docente**
* **buzón anónimo de sugerencias**

**Sistema de almacenamiento de información (NAS)**
kllllllllllllllllll