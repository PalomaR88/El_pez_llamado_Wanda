---
title: "Creación de un sitio web estático"
description: "Creación de una página web estática con Hugo"
date: 2019-10-03T22:21:42+01:00
publishDate: 2019-10-03T22:21:42+01:00
author: "Paloma R. García"
images: []
draft: false
tags: ["aplicaciones_web", "ASIR" , "Hugo"]
---

- Selecciona una combinación entre generador de páginas estáticas y servicio donde desplegar la página web. Escribe tu propuesta en redmine, cada propuesta debe ser original.

Surge - Hugo

- Comenta la instalación del generador de página estática. Recuerda que el generador tienes que instalarlo en tu entorno de desarrollo. Indica el lenguaje en el que está desarrollado y el sistema de plantillas que utiliza. (1 punto)

HUGO: Lenguaje: JavaScript. Sistema de plantillas: React.

Instalación de Hugo:
~~~
sudo apt-get install hugo
~~~

~~~
$ hugo new site quickstart
Congratulations! Your new Hugo site is created in /home/paloma/DISCO2/CICLO II/IMPLANTACIÓN DE APLICACIONES WEB/1.Generador_pag_estatica/quickstart.

Just a few more steps and you're ready to go:

1. Download a theme into the same-named folder.
   Choose a theme from https://themes.gohugo.io/, or
   create your own with the "hugo new theme <THEMENAME>" command.
2. Perhaps you want to add some content. You can add single files
   with "hugo new <SECTIONNAME>/<FILENAME>.<FORMAT>".
3. Start the built-in live server via "hugo server".

Visit https://gohugo.io/ for quickstart guide and full documentation.
~~~

~~~
$ cd quickstart
$ git init
Inicializado repositorio Git vacío en /home/paloma/DISCO2/CICLO II/IMPLANTACIÓN DE APLICACIONES WEB/1.Generador_pag_estatica/quickstart/.git/
paloma@coatlicue:~/DISCO2/CICLO II/IMPLANTACIÓN DE APLICACIONES WEB/1.Gene
rador_pag_estatica/quickstart$ git submodule add https://github.com/budparr/gohugo-theme-ananke.git themes/ananke
Clonando en '/home/paloma/DISCO2/CICLO II/IMPLANTACIÓN DE APLICACIONES WEB/1.Generador_pag_estatica/quickstart/themes/ananke'...
remote: Enumerating objects: 5, done.
remote: Counting objects: 100% (5/5), done.
remote: Compressing objects: 100% (5/5), done.
remote: Total 1416 (delta 0), reused 1 (delta 0), pack-reused 1411
Recibiendo objetos: 100% (1416/1416), 4.15 MiB | 3.55 MiB/s, listo.
Resolviendo deltas: 100% (764/764), listo.
$ echo 'theme = "ananke"' >> config.toml
~~~




- Configura el generador para cambiar el nombre de tu página, el tema o estilo de la página,… Indica cualquier otro cambio de configuración que hayas realizado. (1 punto)

Modifico el fichero quickstart/content/posts/my-first-post.md para añadir nuevos post. 

Para cambiar el nombre de la página ha que modificar el fichero config.toml.

~~~
$ hugo server -D

                   | EN  
+------------------+----+
  Pages            | 10  
  Paginator pages  |  0  
  Non-page files   |  0  
  Static files     |  3  
  Processed images |  0  
  Aliases          |  1  
  Sitemaps         |  1  
  Cleaned          |  0  

Total in 31 ms
Watching for changes in /home/paloma/DISCO2/CICLO II/IMPLANTACIÓN DE APLICACIONES WEB/1.Generador_pag_estatica/quickstart/{content,data,layouts,static,themes}
Watching for config changes in /home/paloma/DISCO2/CICLO II/IMPLANTACIÓN DE APLICACIONES WEB/1.Generador_pag_estatica/quickstart/config.toml
Environment: "development"
Serving pages from memory
Running in Fast Render Mode. For full rebuilds on change: hugo server --disableFastRender
Web Server is available at http://localhost:1313/ (bind address 127.0.0.1)
Press Ctrl+C to stop
~~~



