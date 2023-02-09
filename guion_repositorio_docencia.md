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

![estructura](https://raw.githubusercontent.com/aprendiendo-cosas/repositorio_docencia/main/imagenes/estructura_repositorios.png?token=GHSAT0AAAAAAB5C54OOU3ZQIOUDM4NC2QFIY7FGIKQ)

*Estructura general de todo el sistema. Se representan tres actos docentes elementales, que corresponden con aspectos teóricos ("Tema 8. Competencia interespecífica") y con aspectos prácticos ("Practica cuantificación tendencia NDVI" y "Teledetección"). En cada uno de ellos hay una evolucion continua de su contenido. Esto se representa por los sucesivos commits que afectan a los distintos elementos que lo componen (presentaciones, mapas mentales, bibliografía, código, etc.). Cada cierto tiempo se alcanza un estado que permite generar una versión concreta. Esto se "fija" mediante la creación de una release. Dado que el repositorio está conectado con Zenodo, se crea un DOI cada vez que se genera una release. Las distintas versiones de los actos docentes fundamentales ("hijos") se agrupan en otros repositorios que corresponden con asignaturas ("Ecología CCAA. 2019-2020", "Ecología CCAA. 2020-2021", etc.). En estos repositorios generales se pueden crear wikis o bien páginas html con enlaces a las releases de los actos docentes elementales*



### Estructura de un acto docente

Como hemos comentado más arriba, hay dos tipos de actos docentes. Los denominados "elementales" (que corresponden con temas de teoría, ejercicios o prácticas) y los "generales" (que agrupan varios elementos de los anteriores y configuran asignaturas). Cada uno de estos dos tipos tiene distinta estructura interna:



#### Actos docentes elementales

Un acto docente elemental puede contener multitud de elementos que se usan en el proceso de aprendizaje: presentaciones (powerpoint, canvas, prezi, etc.), mapas mentales, artículos, vídeos, etc. Para suministrar a los estudiantes toda esta información de manera ordenada y sistematizada, se organiza todo dentro de un guión. Se trata de un documento de texto (escrito en Markdown) que contiene información sobre la secuencia de actividades que ocurren en el acto docente (sesión teórica, práctica, salida de campo, laboratorio, etc.). Este guión tiene también metadatos (versión del documento, asignatura y grado al que va dirigido, autor, etc.). Además este documento contiene enlaces a elementos que se usan durante la sesión docente: videos de youtube, archivos en gdrive o en el moodle, etc. Los guiones tienen una estructura parecida y un diseño homogéneo. La siguiente figura muestra el encabezado tipo de un guión.







#### Actos docentes generales



Cada “acto docente” 

La unidad de trabajo de todo esto es un objeto que hemos llamado “guión”. 

Tanto los guiones como todo el material acompañante (presentaciones, bases de datos, geoinformación, etc.) se almacenan (por ahora) en mi cuenta de go.ugr.es. Las carpetas están ordenadas según mi criterio.

La idea es subir los guiones (que arrastran enlaces a material) a github en formato markdown. Desde allí puedo hacer un control de cambios y documentar la evolución de cada guión. De hecho, con el tiempo, github sería el único sitio en el que estarían los guiones. La página en github sería como el punto de entrada a todo el material docente. 

**Estructura detallada. Ejemplo de caso de uso de un repositorio de acto docente.**



* Creo guión rico en enlaces usando typora. Lo guardo en la carpeta correspondiente de gdrive. 
* Creo un repo de github con el objeto docente en cuestión. Dicho repo contiene:
    * Archivos que subo directamente al repositorio o bien enlaces a los mismos en zenodo.
* Criterios de denominación de repos de actos docentes. Por ahora hay uno definido por mí. Sugiero mantener el mismo criterio para todos los usuarios. Esto facilitará la búsqueda de información. 
    * [Tipo de acto docente]_[nombre corto acto docente]_[nombre corto asignatura]_[Universidad], donde:
        * [Tipo de acto docente]:
            * A: Actividad de estudiante.
            * T: Tarea de estudiante.
            * C: Salida de campo
            * Te: Sesión teórica
            * P: Sesión práctica
            * TP: Sesión teórico-práctica
        * [nombre corto acto docente]: pues eso…. Ejemplo: sp_amenazadas
        * [nombre corto asignatura]:
            * ecologia_ccaa
            * ecologia_I_bio
            * ecologia_II_bio
            * etc
            * 
    * empieza por “teaching_”
* Subo el markdown anterior a mi blog (exportado previamente a html). Básicamente para que se vean los &lt;iframe> que pueda poner (mapas y flujos de trabajo).
* Subo enlaces a todo lo anterior al moodle de la UCO o al classroom de la UGR. Enlazar objetos externos a la versión que haya en github, que está abierta por definición.

**Cómo ordenar videos en youtube**



* Listas de reproducción: añadir etiquetas para que los videos vayan a varias listas de reproducción que sean coherentes con los elementos de la escalas a las que trabajo. Me explico. Un video puede ir a la lista de _docencia_UCO_Ecologia_2019-2020 _y también a otra llamada _practica_competencia_intraespecifica_. 
* Para hacer que esto funcione debes de crear etiquetas con sentido. 
    * Curso académico.
    * Asignatura, grado.
    * Teoría o prácticas.
    * Español o inglés.
    * Nombre del evento docente: ej. sesiones de prácticas sobre competencia intraespecífica. Este nombre debe de coincidir con el del repositorio de Github. 
* Listas de reproducción:
    * Docencia ecología UCO (CCAA). Curso 2019-2020.
        * Si etiqueta es: UCO ecología CCAA 2019-2020
* Forma de nombrar los videos
    * [tipo]_[tema]_[ddmmaaaa]_[x/x]
        * tipo: Teoría o Práctica
        * tema: nombre del tema abordado
        * Fecha
        * x/x: uno de tantos.

**Estructura del repositorio. Definiciones.**



* Objeto docente fundamental: Es el objeto mínimo que no se puede dividir en otro más pequeño. Hay varios tipos.
    * Sesión teórica.
    * Sesión práctica.
* Cada objeto docente fundamental se corresponde con un repositorio de Github. En cada repositorio puede haber archivos con código, imágenes, etc. Se puede organizar como una wiki.
* El versionado de los archivos se gestiona desde Github y también desde Zenodo. En esta última plataforma puedes tener n versiones de un archivo (o paquete de archivos). Cada versión tiene un DOI, pero en la plataforma se puede trazar el versionado.
* Cada vez que hay una versión consolidada o utilizable de un objeto docente, se puede hacer una release con Github. Esa release tiene forma de .zip que, automáticamente adquiere un DOI a través de Zenodo (porque ambas plataformas están unidas). 
* Los objetos docentes fundamentales se agrupan en otros de nivel superior: asignaturas, sesiones conjuntas de prácticas, etc. Para documentar cada uno de estos objetos docentes “superiores” se usa también Github. 

**Actualización de estado en enero de 2021. Al escribir esto no he repasado lo anterior**



* Cada acto docente está en un repositorio. Cada versión es una release que se almacena en una carpeta ignorada por Git. Todo ello está en el drive.
* en cada repositorio hay una carpeta llamada “preparacion” que contiene los archivos usados para preparar el acto docente. Esta carpeta no es gestionada por Git.
* las versiones de cada acto docente que afectan a distintas titulaciones, se consideran como forks o branches diferentes. Aún tengo que ver cómo funciona esta pana. Es decir, no sé bien cómo gestionar esto en local. En git parece fácil. En local no. Como ejejmplo reciente está la práctica de biodiversidad para el grado de UCO y para el Geoforest…
* Además de los repositorios que describen los actos docentes, en Github.com hay otros que contienen índices a los contenidos de cada asignatura. Estos repositorios son los que crean la entidad “asignatura”. Tienen tantas páginas de wiki como años académicos hay para cada asignatura. 
* Me falta organizar algo para llevar un control de los repositorios en local, así como en github.com. Para que no haya redundancia
* criterios de denominación de repositorios:
    * Repositorios de asignatura: [asignatura]_[grado]_[institución]
    * Repositorios de acto docente: [tipo]_[nombre_acto_docente]_[asignatura]_[grado]. 
        * Tipos:
            * A: Actividad
            * E: ejercicio.
            * T: Tarea. [aquí](https://twitter.com/chacon_piris/status/1366089880141508610?s=21) detalles sobre definiciones de los tres tipos anteriores.
            * P: Práctica
            * Te: Teoría
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