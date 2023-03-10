# MONITOR
## Que es ELK?

ELK es un conjunto de Aplicaciones las cuales tienen como objetivo visualizar los registros 
de distintos contenedores de una manera mas sencilla, todo esto ha sido compilado en varios 
Docker Compose y luego he decidido correrlo en **Makefile** para asi automatizarlo con solo 
un comando el cual seria `Make build_elk` en la consola de comandos de windows o terminal 
de linux.

Actualmente **ELK** se encuentra en su `version:1.0`, posiblemente existan mas actualizaciones 
a medida que salgan nuevas herramientas o tenga nuevas ideas a desarrollar.

NOTA: Para usarlo es requerido tener instalado **Make** y **Docker** para poder usarlo sin problemas.

## Como usarlo?

### EJECUCION:
Es simple y sencillo de usar, lo unico es correr `Make build_elk` para su ejecucion luego para 
visualizar los recursos tendrias que ir a la direccion `localhost:5601` para visualizar 
**KIBANA** en el navegador.

### DETENCION:
Solo debes usar `stop_elk` o indicar cual es el **Servicio (Contenedor)** que 
deseas detener de monitor.

### ELIMINACION:
Por igual solo debes usar `delete_elk` o indicar cual es el **Servicio (Contenedor)** que desees 
eliminar de ELK, ahora si deseas eliminar todo ELK de raiz (Imagenes, contenedores y Networks) 
debes usar `deep_delete` y no tendras los archivos mencionados.

### EXISTEN MAS COMANDOS:
Para ver todos los comandos puedes ver el archivo `Makefile` y tendras comentarios que indicara
sus funciones, ahora si usas estos archivos en Linux puedes usar el **comando** `Make help` para
poder ver todas las funciones.

## INFORMACION IMPORTANTE

Esta SECCION puedes usarla para visualizar registros no solo de los contenedores que tengas en 
ejecucion sino de apps donde obtengas informacion que desees ver en graficos o de una manera mas 
dinamica, ademas si deseas puedes editar y mejorar su uso si deseas ya que es totalmente 
personalizable y facil de escalar.
