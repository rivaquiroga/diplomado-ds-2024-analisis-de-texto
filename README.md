# Análisis de texto con Python

En esta clase del [Diplomado en Ciencia de Datos UC](https://datascience.uc.cl/) nos aproximaremos al análisis de textos usando Python. Abordaremos algunas técnicas que se enmarcan en lo que usualmente se denomina _Minería de texto_ y otras propias del _Procesamiento del Lenguaje Natural_. Como tenemos una sola clase para cubrir estos temas, será algo más bien introductorio que les permita luego seguir explorando por su cuenta.


## Preparación

En la primera parte de la clase nos enfocaremos en el proceso de extracción de datos. Primero abordaremos la extracción de texto de archivos PDF y luego la conversión de un audio a texto (lo que se conoce como "speech-to-text"). **La sugerencia es trabajar en Google Colab en esta parte de la clase**, sobre todo si tu sistema operativo es Windows, ya que se requiere instalar más cosas que solo librerías de Python para hacer que el código funcione. De todos modos, en la sección [Recursos Adicionales](#recursos-adicionales) quedarán indicaciones sobre cómo instalar todo en tu máquina personal. 

Haremos el paso a paso en clases, pero dejo acá las indicaciones como respaldo. 

Para el trabajo con PDFs, primero instala tesseract en Google Colab:

```
!sudo apt install tesseract-ocr-spa
```

Esa línea de código instalará el modelo para español (y el para inglés, que queda instalado por defecto). Puedes chequear que está todo en orden ejecutando lo siguiente

```
!tesseract --list-langs
```

También es necesario instalar Poppler:

```
!apt-get install poppler-utils
```

Las librerías que utilizaremos en esta parte de la sesión son las siguientes:

```
!pip install pytesseract
!pip install pdf2image
!pip install PyPDF2
```

Luego, para convertir un audio a texto, necesitarás instalar lo siguiente:

```
!pip install setuptools-rust 
!pip install -U openai-whisper
!sudo apt update && sudo apt install ffmpeg
```

(La línea de rust es importante si estás trabajando en tu computador personal. Si estás en Google Colab no es necesario). 

En la segunda parte de la clase, discutiremos algunas nociones vinculadas al preprocesamiento de textos. Para esa parte de la sesión será necesario tener instalado lo siguiente:

```
!pip install nltk
!pip install -U pip setuptools wheel
!pip install -U spacy
!python -m spacy download es_core_news_sm
```

Hacia el final de la sesión hablaremos brevemente del potencial que tienen los grandes modelos de lenguaje (LLM) para resolver tareas de análisis de texto. Vamos a ejemplificar con [el plan gratuito de Google Gemini](https://aistudio.google.com/app/apikey), pero para el futuro ten en cuenta que ese plan no asegura la privacidad de los datos (y solo permite 15 requests por minuto).



## Actividades 

### Ejercicio 1: extracción de texto de archivos en formato PDF

:page_facing_up: [Código escrito en clases](https://www.dropbox.com/scl/fi/47pkmu8hg2bvb5rf4khr6/01_extraccion-pdfs.py?rlkey=e56d4k1djdplckjxawbsd8f7h&st=arjzpc4y&dl=0)

📖 [PDF escaneado](https://www.dropbox.com/scl/fi/yy9894lex6zf6sbyyj2yv/amanda_labarca.pdf?rlkey=03xplf67hh9gh5ffjfizs3h7m&dl=0)

✍️ [PDF nativo](https://www.dropbox.com/scl/fi/kiwtke3zbkel1etcee51h/historia_python.pdf?rlkey=16oiuxjx7eliyn9165u1by9sj&dl=0)


### Ejercicio 2: "speech-to-text"

:page_facing_up: [Código escrito en clases](https://www.dropbox.com/scl/fi/nw78epjuw2ulis7149k4t/02_speech-to-text.py?rlkey=52ldwa73ory7wa48yjve50sju&st=1rntx4ln&dl=0)

🎤 [Audio de prueba]()

### Ejercicio 3: Discutir algunas cosas sobre preprocesamiento de texto
 
:page_facing_up: [Código escrito en clases](https://www.dropbox.com/scl/fi/a7vjlqifx1v9tq628ejwx/03_sobre-preprocesamiento.py?rlkey=3t8tw0acvhbst2d7gev7qwenk&st=hlo2fbzf&dl=0)

### Ejercicio 4: Probando LLMs

:page_facing_up: [Código escrito en clases](https://colab.research.google.com/drive/1I-xIX2p5fsD9jKOcArrz1LLazbdgSFUe)

## Recursos adicionales

### Documentación librerías utilizadas

pronto...

### Sobre expresiones regulares
- En Python usualmente las usamos a través de la librería [re](https://docs.python.org/es/3/library/re.html). La documentación está parcialmente traducida al español e incluye un [tutorial](https://docs.python.org/es/3/howto/regex.html).
- [regex101](https://regex101.com/): un sitio web para probar nuestras expresiones regulares
- [Hoja de referencia de la sintaxis de expresiones regulares](https://developer.mozilla.org/es/docs/Web/JavaScript/Guide/Regular_expressions/Cheatsheet)

### Instalar tesseract en tu máquina personal

Si trabajas en tu computador, puedes revisar la forma de instalación que corresponda a tu sistema operativo [en la documentación de tesseract](https://tesseract-ocr.github.io/tessdoc/Installation.html). 

**Personas que usan Windows**: pueden revisar [estas indicaciones en español para instalar tesseract](https://ucd-dnp.github.io/ConTexto/versiones/master/instalacion/instalacion_popple_teseract_windows.html). 

### Instalar Poppler
Las librerías para trabajar con archivos PDF requieren tener instalada una herramienta llamada Poppler. Si al tratar de usar pdf2image o tesseract te aparece un error relativo a Poppler, significa que tienes que instalarlo. Puedes encontrar indicaciones sonre cómo hacerlo [en la documentación de pdf2image](https://pdf2image.readthedocs.io/en/latest/installation.html#installing-poppler). En el caso de Windows, hay que descargarlo directamente [desde el repositorio de GitHub](https://github.com/oschwartz10612/poppler-windows/releases/tag/v24.08.0-0).
Ojo que Poppler requiere tener permisos de administración del dispositivo para su instalación, por lo que si estás trabajando en el computador de tu institución puede que no sea posible instalarlo directamente. 

### Más sobre PDFs, OCR y HRC

- Para liberar tablas en un pdf nativo: [Tabula](https://tabula.technology/). Tiene versión para trabajar desde [Python](https://tabula-py.readthedocs.io/en/latest/) y desde [R](https://docs.ropensci.org/tabulapdf/articles/tabulapdf.html)
- Para OCR y reconocimiento óptico de letra manuscrita (HCR) sin tener que usar código: [Transkribus](https://www.transkribus.org/). El plan gratuito permite 50 páginas por mes. 

### En R
El año pasado el diplomado contemplaba tres clases sobre análisis de texto usando R. Los materiales están disponibles [en este repositorio](https://github.com/rivaquiroga/analisis-de-textos-r-2023). Además del código escrito en clases, hay enlaces a recursos adicionales para seguir profundizando.

### Para explorar: usar LLMs de modo local en un dataframe
Recientemente apareció _mall_, una librería de Python y Paquete de R que permite trabajar localmente con Ollama y que está pensada en casos en que tenemos nuestros datos en un dataframe: https://mlverse.github.io/mall/. 
