# Guia basica para usar el notebook de Easy Scripts
Hola!, este va a ser una pequeña guia de como usar mi notebook de entrenador de loras usando la ui de [Lora Easy Scripts](https://github.com/67372a/LoRA_Easy_Training_scripts).
Lo primero que tienen que hacer es descargar la GUi de Lora Easy Training Script, la cual encontraras el enlace en el hipervinculo de arriba.
<img width="1334" height="594" alt="image" src="https://github.com/user-attachments/assets/042b5c11-7d27-46be-9ada-97a0974ff3e1" />

Una vez descargado y descomprimido, tienen que abrir el `install.bat` si estas en windows, o `install.sh` si estas en linux, este comenzara a instalar las dependencias del programa, y llegara un punto que les preguntara "**Are you using this locally? (y/n)**", el cual tendrian que responder con `n`.

Terminado esto ya podran abrir el programa con el archivo `run.bat`, esperando unos segundos podran abrir la UI.
La interfaz puede verse complicada al principio, pero si alguna vez han usado notebooks de colab para entrenar loras, tendran contexto de que significa algunos de los menús que se encuentran.

## General Args

<img width="1167" height="667" alt="image" src="https://github.com/user-attachments/assets/64798fd4-cb6f-4880-b69a-93712e75c774" />

En este apartado vemos las configuraciones basicas del entrenador, ya sea los modelos base a entrenar lora, resolución, semilla, entre otros.
En el apartado de los modelos, este es principalmente para definir el path de los modelos SDXL y el VAE para entrenar loras.

## Network Args

<img width="1167" height="520" alt="image" src="https://github.com/user-attachments/assets/48ab2186-3d18-4f05-b28d-2b1e67f88d5e" />

Aqui se podra elegir el tipo de lora que se querrá entrenar, puede ser el basico Lora, LoCon, Loha, LoKr, etc.
Los valores de network dim, Network alpha, Conv dim y Conv alpha, el cual estos 2 ultimos solo se tendran en cuenta si usan el tipo de lora `LoCon`.

## Optimizer Args

<img width="1164" height="592" alt="image" src="https://github.com/user-attachments/assets/93e0c679-02b2-4a0e-898c-c24f13a248e3" />

Esta es la parte crucial para entrenar loras, ya que aqui se especifica que optimizer usar, asi como el scheduler, el learning rate, etc.

## Saving Args

<img width="1167" height="360" alt="image" src="https://github.com/user-attachments/assets/45829b75-a853-483f-81c6-06e22741bcc1" />

Se tiene que especificar en que carpeta se debe de guardar el lora entrenado, asi como su nombre final, precision, etc.

## Sample Args

<img width="1175" height="247" alt="image" src="https://github.com/user-attachments/assets/cbab3827-4462-4568-9df8-3f10fa9495be" />

Esta pestaña no es obligatoria, mas bien opcional, si quieres generar una preview de como esta quedando el lora a medida que va generandose los epoch.
Se tiene que especificar la ruta del archivo .txt com los datos de la generacion (Prompt, negative prompt, res, steps, seed), esto se va a explicar mas adelante como establecerlo.

## Anima Args

<img width="1154" height="457" alt="image" src="https://github.com/user-attachments/assets/9f126f22-1b48-4997-8bb2-d8c93fe28476" />

Si van a entrenar loras de anima, tienen que activar esta pestaña y establecer el path cada uno de los modelos usables: "Modelo de anima", "Text Encoder" y "VAE".
Por lo general solo tienen que modificar esto y dejar el resto de valores tal cual como esta en la imagen de referencia.

## Subset Args

<img width="1201" height="613" alt="image" src="https://github.com/user-attachments/assets/0bee1b88-b75d-4f58-877c-6921f9fa6348" />

Este seria el lugar donde vamos a establecer el path en donde se encuentra nuestras imagenes junto a sus .txt con los tags a entrenar, establecer el numero de repeats, los trigger tags (o keep tags), el shuffle captions, etc.

En este apartado solo tienen que enfocarse en el numero de repeats, Keep tags y shuffle captions, el resto lo pueden dejar en predeterminado.

Pueden agregar tantas carpetas (subset) que quieran para el entrenamiento.


# Notebook

Ahora vamos a la explicacion de como integrar colab (usando mi notebook) a la UI que tenemos instalado en nuestra computadora.
Cabe recalcar que la ui que descargamos simplemente es un frontend del entrenador, esto quiere decir que los modelos, el dataset, y el output del lora resultante entrenado se encontrara fuera de su equipo local. Para el dataset y el ouput, existe una celda concreta en la cual se tiene que especificar en que lugar se encuentra el dataset y se alojara el lora resultante, ya sea dentro del propio entorno de colab o dentro del drive de la cuenta que se esta usando en ese momento, si se usa el metodo dentro de colab, el dataset se tendra que subir manualmente a travez del gestor de archivos del mismo y tambien se debera descargar el lora antes de apagar el entorno, ya que se borra todos los datos y no se podrá recuperar nada.

Mencionado anteriormente que la UI solo es frontend, hay que establecer el directorio de los modelos en donde se encuentran dentro de colab y no localmente, asi como el directorio donde se encuentra el dataset, el archivo de los prompt para los samples, y el output de los loras.  Para ello se les menciona como resultado de las celdas el directorio donde se encuentra cada uno de los mencionados anteriormente para mas comodidad, y simplemente tienen que poner cada directorio donde corresponde.

Por si no les aparece los paths de los modelos, aqui se los dejo:

### Modelos Illustrious

Illustrious 0.1 = **/content/models/Illustrious-XL-v0.1.safetensors** n/
Illustrious 2.0 = **/content/models/Illustrious-XL-v2.0.safetensors**

SDXL Vae & Vae FP16 Fix = **/content/models/sdxl_vae.safetensors**

### Modelo Anima V1 Base

Modelo Anima Base = **/content/models/anima-base-v1.0.safetensors**
Vae de Anima = **/content/models/qwen_image_vae.safetensors**
Text Encoder de Anima = **/content/models/qwen_3_06b_base.safetensors**

## Funcionamiento

Una vez que ya tengamos todo seteado e iniciado el backend, copiamos el enlace de gradio (si este esta caido, pueden usar el de cloudflare, no hay ningun problema en eso), y pegamos en el cuadro de texto en la ezquina inferior derecha.

<img width="1359" height="741" alt="image" src="https://github.com/user-attachments/assets/e083fc4d-8717-4896-a60b-da8bc8f09c60" />

Y con esto ya estaria comenzando a entrenar, si por algun momento no entrena nada, lo cual lo pueden notar en colab porque no muestra ningun mensaje en el log, puede ser que algun directorio este mal escrito o falta, pueden verificarlo a travez de la ventana de comandos que tienen abierta cuando abren la UI en su ordenador.
Recuerden que una vez entrenado, si estan usando el propio colab para alojar el dataset, tendran que descargar los loras resultantes!.










