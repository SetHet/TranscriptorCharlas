Transcriptor de Charlas para multiples agentes.

Este proyecto se basa en este Google Colab [transcripts with speaker names](https://colab.research.google.com/drive/1V-Bt5Hm2kjaDb4P1RyMSswsDKyrzc2-3?usp=sharing#scrollTo=O0_tup8RAyBy). Realize mejoras para mejorar la precision y generar archivos de texto. Dividi el archivo entrante de audio y lo procese en fragmentos para corregir un error de transcripcion que afectaba a audios demaciado extensos.

Este proyecto esta diseñado para ser ejecutado en Google Colab con sus ambientes de GPU.



Notas de uso:

- Utilizar el modo GPU de Google Colab, Recomendado T4 GPU. Esto se encuentra en "Entorno de ejecución/Cambiar tipo de entorno de ejecucion/T4 GPU" (https://www.tutorialspoint.com/google_colab/google_colab_using_free_gpu.htm).
- La transcripcion se guardara en formato TXT y HTML y se descargaran automaticamente, puede que el explorador pida permiso de multi descargas.
- Cambie el numero de hablantes segun el audio entregado.
- Seleccione un modelo más grande si tu quieres más precision y un modelo menor si tu quieres que se ejecute rapidamente. Para T4_GPU se puede usar el modelo de mayor tamaño ([más información](https://github.com/openai/whisper#available-models-and-languages)).
- Si el lenguaje es ingles, selecciona el idioma, sino el general funciona bastante bien, especialmente en español.


Vista de alto nivel de lo que ocurre en el codigo:


1.   Se sube un audio por el sistema de google colab, este proceso puede tardar bastante segun el tamaño del archivo.
2.   Se instalaran los paquetes necesarios para el funcionamiento y cargara el modelo en memoria de video.
3.   Se separara el audio en trozos que se procesaran individualmente para mejorar la precision de la transcripcion. Esto se realiza con PyDub.
4.   Se procesaran lada trozo en varios segmentos de audio y generaran las transcripciones. Esto se realiza con Whisper de OpenAI.
5.   Se reagruparan los trozos de audio y texto, para su procesamiento de deteccion de hablantes. Esto se realiza mediante CLusters de aglomeración.
6.   Se generara un archivo de texto y otro de html para una mejor lectura.

Espero que te sea util. Dime si esto puede ser mejorado.
