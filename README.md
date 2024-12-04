# Análisis de texto con Python

En esta clase del [Diplomado en Ciencia de Datos UC](https://datascience.uc.cl/) nos aproximaremos al análisis de textos usando Python. Abordaremos algunas técnicas que se enmarcan en lo que usualmente se denomina _Minería de texto_ y otras propias del _Procesamiento del Lenguaje Natural_.). Como tenemos una sola clase para cubrir estos temas, será algo más bien introductorio que les permita luego seguir explorando por su cuenta.


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

Hacia el final de la sesión hablaremos brevemente del potencial que tienen los grandes modelos de lenguaje (LLM) para resolver tareas de análisis de texto. Vamos a ejemplificar con el plan gratuito de Google Gemini, pero para el futuro ten en cuenta que ese plan no asegura la privacidad de los datos.



## Actividades 

pronto...

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



