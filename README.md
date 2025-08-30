# embedDelphiHelp
### Ayuda para aplicaciones Delphi, como parte de la misma aplicación

## Motivación
Es un problema que la ayuda no sea parte del proyecto de las aplicaciones, y que haya que tener un programa externo para generar la ayuda, compilarla e incluirla en la aplicación, como un archivo adicional.\
Este proyecto permite desarrollar la ayuda (escribirla) "dentro" del proyecto, quedando guardada en 3 archivos de ClientDataSet.\

## Implementación
El proyecto es muy pequeño y consiste en un par de Frames que implementan la estructura de árbol de los contenidos y los contenidos mismos, como texto RichEdit e imágenes, que se conservan por separado y se "inyectan" en el RichEdit al momento de la visualización.\
Para escribir la ayuda se ejecuta la aplicación y se arma la estructura de contenidos y los contenidos mismos.\
Para incluir la ayuda en la aplicación en cuestión, se puede agregar el Form de visualización, o crear uno utilizando los dos Frames de árbol y contenidos. Además se deben incluir los tres archivos generados como recursos de la aplicación (ayuda.rc es un ejemplo que se puede utilizar), si quiere que sea parte del exe, o bien distribuirlos junto con el exe.

## Creación de la ayuda
Se debe abrir el proyecto y construirlo. Al cerrar, o al apretar el botón "Guardar", se generan 3 archivos con el contenido desarrollado.
Al volver a ejecutar la aplicación, se cargan los contenidos que tengan estos archivos.

## Inclusión de la ayuda en la aplicación documentada
Se deben llevar los 3 archivos con los contenidos al directorio del proyecto de la aplicación y se debe incluir una pantalla de visualización de la ayuda, para lo cual se puede usar la que esparte de este proyecto, o bien crear una propia utilizando el Frame para el árbol, y el Frame para el contenido.\

### Embebida
Si se quieren embeber los 3 archivos en el ejecutable, se debe generar un archivo de recursos para el proyecto, o incluir el archivo 'ayuda.rc' (modificadas las rutas de ser necesario).\
Si se genera un archivo de recursos para el proyecto, se deben agregar como recurso los 3 archivos, como tipo RC_DATA, y el nombre de los 3 debe comenzar igual, y terminar con 'C' (contenidos), 'E' (estructura) e 'I' (imágenes).\
Si se utilizan nombres diferentes a los del archivo 'ayuda.rc' para los recursos, se debe especificar el nombre (sin la última letra), en los Frames de ayuda, para que se puedan encontrar los recuros al momento de cargarlos.\

### Externa
Si se quieren distribuir los 3 archivos junto con el ejecutable, u ofrecer descargarlos, o incluso armar una ayuda compleja como un conjunto de diferentes juegos de archivos, se deben ubicar los archivos en directorios dentro de la aplicación (si son varios juegos), o directamente en el directorio de la aplicación.\
Si los archivos se renombran, se debe modificar la propiedad FileName de los ClientDataSet de los Frame, antes de que se intente cargar el contenido.\
Si se colocan en directorios dentro de la aplicación (o en otra ruta), se debe especificar la ruta hasta los archivos a cargar, al momento de la carga.
