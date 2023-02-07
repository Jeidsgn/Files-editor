# Frame_overlay

Este repositorio contiene el código necesario para facilitar un proceso necesario al usar superponer los fotogramas resultantes cuando se usa Ebsynth.

##Descripción

Este código fue creado para automatizar la superposición de fotogramas al usar EbSynth.

al usar Ebsynth se crean varias carpetas, una por cada keyframe, que contiene los frames circundantes a ese keyframe, y que están duplicados en otras carpetas. Para crear el video resultante es necesario superponer estos frames conuna opacidad relativa a su distancia para que se vea suavizado.

Este script recorre todas las carpetas dentro de "directorio" y busca aquellas que cumplen con el patrón "out_[#####]". Para cada una de estas carpetas, se obtienen los fotogramas contenidos en ella y se almacenan en una lista "frames".

Por último, se vuelve a recorrer cada carpeta cumpliendo el patrón "out_[#####]" y se realiza la superposición de las imágenes. Para cada fotograma, se abre y se aplica una opacidad que depende de la distancia entre el fotograma actual y el fotograma clave. La opacidad se aplica sobre la imagen base que puede ser el fotograma abierto o una imagen previamente superpuesta. La imagen resultante se guarda en la carpeta "resultado".

En general, este código realiza una superposición de imágenes, donde la opacidad de cada imagen depende de su distancia con respecto a una imagen clave. La imagen resultante se almacena en una carpeta específica.

##Instalación

Para utilizar este código, siga estos pasos:

Clone o descargue el repositorio en su sistema.
Abra el archivo con su editor de código preferido (fue hecho en google colab, así que recomiendo ejecutarlo ahí).
Siga las instrucciones en el archivo para configurar y ejecutar el código.

##Uso

Una vez que haya seguido los pasos de instalación, el código estará listo para su uso. Siga las instrucciones en el archivo para ejecutar el proceso deseado.

##Contribución

Si desea contribuir a este proyecto, por favor abra una solicitud de extracción o envíenos un correo electrónico. Estaré encantado de revisar cualquier cambio o mejora que se proponga.
