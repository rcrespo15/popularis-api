### Popularis API

Este API (Application Programming Interface) busca alimentar la aplicación [Popularis](http://popularis.herokuapp.com) con sentencias judiciales panameñas e información sobre el equipo detrás de este proyecto.

## Para empezar

Estas instrucciones serán para aprender como agregar/eliminar sentencias/miembros de la base de datos de Popularis

### Antes de empezar

(1) Tener una cuenta en GitHub
(2) Esa cuenta debe estar agregada como [contribuidora](https://github.com/juliet-tech/popularis-api/settings/collaboration) a este repositorio

### Para editar el JSON

(1) Buscar dentro los folderes el JSON file que busca cambiar <br>
(2) Clickear donde dice `Edit` <br>
(3) Una vez termina de editar el documento, al final de la página verá un espacio de texto para comentar. Le recomiendo ser lo más específicx en la descripción que se escriba ahí sobre los cambio hechos para que quede de record por cualquier cosa a futuro. <br>
(4) Cuando termina de escribir, selecciona el botón verde que dice `Commit Changes`. -- Asegurarse de mandarlo al `master` branch. <br>

--> Para este punto ya ha cambiado el API. Sin embargo, falta updatear la plataforma para que reciba esta nueva información.

### La plataforma

(1) Configurar `Heroku remote` para la aplicación localmente en su computadora. Esto se puede hacer desde la Terminal:

```
# OS X
$ brew install heroku/brew/heroku
# UBUNTU
$ wget -qO- https://toolbelt.heroku.com/install-ubuntu.sh | sh

$ heroku login

$ git remote -v
# => heroku https://git.heroku.com/popularis.git (fetch)
#    heroku  https://git.heroku.com/popularis.git (push)
```

(2) En la Terminal:

```
$ cd PATH_TO_POPULARIS_APP
$ git push heroku master
$ heroku run rails db:seed
```

--> Una vez finalizado este proceso y si el JSON está bien estructurado, se verán las nuevas sentencias en la plataforma.

