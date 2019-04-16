# Popularis API

Este API (Application Programming Interface) busca alimentar la aplicación [Popularis](http://popularis.herokuapp.com) con sentencias judiciales panameñas e información sobre el equipo detrás de este proyecto.

Estas instrucciones serán para aprender como agregar/eliminar sentencias/miembros de la base de datos de Popularis

## Prerequisitos

(1) Tener una cuenta en GitHub <br>
(2) Esa cuenta debe estar agregada como [contribuidora](https://github.com/juliet-tech/popularis-api/settings/collaboration) a este repositorio <br>
(3) Tener acceso a la cuenta en [Heroku](https://heroku.com) --> para programadores

## Para editar la data

### Cambiar el JSON

(1) Dentro de este repositorio, buscar el JSON file que busca cambiar <br>
(2) Clickear donde dice `Edit` <br>
(3) Una vez termina de editar el documento, al final de la página verá un espacio de texto para comentar. Le recomiendo ser lo más específicx en la descripción que se escriba ahí sobre los cambio hechos para que quede de record por cualquier cosa a futuro. <br>
(4) Cuando termina de escribir, selecciona el botón verde que dice `Commit Changes`. -- Asegurarse de mandarlo al `master` branch. <br>

--> Para este punto ya ha cambiado el API. Sin embargo, falta updatear la plataforma para que reciba esta nueva información.

### Publicar el cambio a la plataforma

#### Por medio de la plataforma misma

(1) Acceder a http://popularis.herokuapp.com/feedbacks <br>
(2) Clickear en el botón que dice 'Actualizar la base de datos'

#### Para programadores

(1) Configurar `Heroku remote` para la aplicación localmente en su computadora. Esto se puede hacer desde la Terminal:

```
$ cd PATH_TO_POPULARIS_APP       #popularis-app no popularis-api

# OS X
$ brew install heroku/brew/heroku
# UBUNTU
$ wget -qO- https://toolbelt.heroku.com/install-ubuntu.sh | sh

$ heroku login

$ heroku git:remote -a popularis
$ git remote -v
 => heroku https://git.heroku.com/popularis.git (fetch)
    heroku  https://git.heroku.com/popularis.git (push)

```

(2) Para publicar el sitio online con migration + seeding, corra el siguiente `rake task` en el Terminal:

```
$ rake deploy:production
```

--> Una vez finalizado este proceso (y si el JSON está bien estructurado), se verán las nuevas sentencias en la plataforma.

--> De querer automatizar este proceso, se puede configurar el `postdeploy script` del Heroku Ruby buildpack para agregarle `rails db:seed` luego de cada deployment. Más información de como hacer esto se puede encontrar en [aquí](https://devcenter.heroku.com/articles/github-integration-review-apps#the-postdeploy-script).

Tambien he agregado un rake task `rake deploy:production` que se asegura que cada vez que se utilice, se hará la migración y el seeding de la información automáticamente.

