# Transcriptor de Charlas para multiples agentes. 

🎙️[Probar en Google Colab <img src="https://camo.githubusercontent.com/f5e0d0538a9c2972b5d413e0ace04cecd8efd828d133133933dfffec282a4e1b/68747470733a2f2f636f6c61622e72657365617263682e676f6f676c652e636f6d2f6173736574732f636f6c61622d62616467652e737667" />](https://colab.research.google.com/github/SetHet/TranscriptorCharlas/blob/main/TranscriptorCharlas_v10.ipynb)

Este proyecto se basa en este Google Colab [transcripts with speaker names](https://colab.research.google.com/drive/1V-Bt5Hm2kjaDb4P1RyMSswsDKyrzc2-3?usp=sharing#scrollTo=O0_tup8RAyBy). Realize mejoras para mejorar la precision y generar archivos de texto. Dividí el archivo entrante de audio y lo procese en fragmentos para corregir un error de transcripción que afectaba a audios demasiado extensos.

Este proyecto esta diseñado para ser ejecutado en Google Colab con sus ambientes de GPU.

### Notas de uso

- Utilizar el modo GPU de Google Colab, Recomendado T4 GPU. Esto se encuentra en "Entorno de ejecución/Cambiar tipo de entorno de ejecución/T4 GPU" (https://www.tutorialspoint.com/google_colab/google_colab_using_free_gpu.htm).
- La transcripción se guardara en formato TXT y HTML y se descargaran automáticamente, puede que el explorador pida permiso de multi descargas.
- Cambie el numero de hablantes según el audio entregado.
- Seleccione un modelo más grande si tu quieres más precision y un modelo menor si tu quieres que se ejecute rápidamente. Para T4_GPU se puede usar el modelo de mayor tamaño ([más información](https://github.com/openai/whisper#available-models-and-languages)).
- Si el lenguaje es ingles, selecciona el idioma, sino el general funciona bastante bien, especialmente en español.

### Vista de alto nivel de lo que ocurre en el código

1.  Se sube un audio por el sistema de Google Colab, este proceso puede tardar bastante según el tamaño del archivo.
2.  Se instalaran los paquetes necesarios para el funcionamiento y cargara el modelo en memoria de video.
3.  Se separara el audio en trozos que se procesaran individualmente para mejorar la precision de la transcripción. Esto se realiza con PyDub.
4.  Se procesaran lada trozo en varios segmentos de audio y generaran las transcripciones. Esto se realiza con Whisper de OpenAI.
5.  Se reagruparan los trozos de audio y texto, para su procesamiento de detección de hablantes. Esto se realiza mediante CLusters de aglomeración.
6.  Se generara un archivo de texto y otro de html para una mejor lectura.

<hr>

Espero que te sea util. Dime si esto puede ser mejorado ❤️.
