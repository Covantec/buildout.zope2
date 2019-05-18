==============
buildout.zope2
==============

Configuración de buildout para el servidor de aplicaciones Zope 2 con Python 2.7.

.. image:: https://travis-ci.org/Covantec/buildout.zope2.svg?branch=master
   :target: https://travis-ci.org/Covantec/buildout.zope2


Características
===============

- `Zope 2.13.29 <https://pypi.org/project/Zope2/2.13.29/>`_, la ultima versión soporta Zope 2.

- `Zope 2.13.27 <https://pypi.org/project/Zope2/2.13.27/>`_, la ultima versión de Zope 2, la cual soporta 
  el proyecto Plone en su versión 5.1.

- `Python 2.7 <https://www.python.org/download/releases/2.7/>`_.


Requerimientos
==============

Estos son los requerimientos mínimos de instalación: ::

  sudo apt-get update && sudo apt-get upgrade -y
  sudo apt-get install git gcc g++ make tar unzip bzip2 libssl-dev libxml2-dev zlib1g-dev \
                       libjpeg62-turbo-dev libreadline-dev readline-common wv poppler-utils \
                       python2.7-dev libxslt1-dev python-wheel

Descargar
=========

Para la descargar del proyecto Buildout, ejecute el siguiente comando: ::

  git clone https://github.com/Covantec/buildout.zope2.git


Entorno virtual
===============

Se requiere crear y activar un entorno virtual Python para proyecto Buildout, ejecute los siguientes 
comando: ::

  virtualenv --python=/usr/bin/python2 venv
  source ./venv/bin/activate


Inicialización del proyecto
===========================

Para la inicialización del proyecto Buildout, ejecute el siguiente comando: ::

  python bootstrap.py


Construcción del proyecto
=========================

Para la construcción del proyecto Buildout para obtener Zope 2.13.27, ejecute el siguiente comando: ::

  ./bin/buildout

Para la construcción del proyecto Buildout para obtener Zope 2.13.29, ejecute el siguiente comando: ::

  ./bin/buildout -c 2.13.29.cfg


Ejecutar servidor Zope2
=======================

Para ejecutar servidor Zope2, ejecute el siguiente comando: ::

  ./bin/zope2 fg

El servidor Zope 4 puede ser consultado en la dirección http://localhost:8080 entonces abra un navegador 
con esa dirección y le presentara la siguiente pantalla:

.. image:: https://github.com/Covantec/buildout.zope2/raw/master/zope2_index_html.png
   :target: http://localhost:8080

Para acceder a la Zope Managment Interface - ZMI abra en su navegador la dirección http://localhost:8080/manage la cual le 
solicitara el nombre de usuario **admin** y contraseña **admin** y le presentara la siguiente pantalla: 

.. image:: https://github.com/Covantec/buildout.zope2/raw/master/zope2_manage.png
   :target: http://localhost:8080/manage


Otros comandos disponibles
==========================

./bin/addzope2user

  Permite agregar un nuevo usuario Zope, ejecutando el siguiente comando: ::

    ./bin/addzope2user <username> <password>

  Para más información consulte la ayuda incluida en el script con el siguiente comando ``./bin/addzope2user -h``.


./bin/mkzopeinstance

  Permite crear una instancia de Zope. agregar un nuevo usuario Zope, ejecutando el siguiente comando: ::

    ./bin/mkzopeinstance -d $PWD/z2instance -u admin:admin --python=$PWD/bin/zopepy

  Para más información consulte la ayuda incluida en el script con el siguiente comando ``./bin/mkzopeinstance -h``.


./bin/runzope

  Es el script ejecutor del ZDaemon (servicio) Zope, para ejecutarlo ejecute el siguiente comando: ::

    ./bin/runzope -C $PWD/parts/zope2/etc/zope.conf

  Para más información consulte la ayuda incluida en el script con el siguiente comando ``./bin/runzope -h``.


./bin/zope2

  Es el script que lleva por nombre de la sección buildout que construye automáticamente Zope 2 ``zope2``, eso 
  quiere decir, controla la instancia Zope usando ZDaemon, como lo hace el ``zopectl`` (mas adelante se detalla), 
  para ejecutarlo el siguiente comando: ::

    ./bin/zope2 fg

  Para más información consulte la ayuda incluida en el script con el siguiente comando ``./bin/zope2 -h``.


./bin/zopectl

  Es el script que controla la instancia Zope usando ZDaemon, para ejecutarlo el siguiente comando: ::

    ./bin/zopectl start

  Para más información consulte la ayuda incluida en el script con el siguiente comando ``./bin/zopectl -h``. 
  Adicionalmente consulte el articulo `Installing and Zope with zc.buildout — Zope 2 v2.13 documentation <https://zope.readthedocs.io/en/2.13/INSTALL-buildout.html>`_.


./bin/zopepy

  Es el script que acceder a una consola interactiva de Python al contexto de la instalación de Zope 2, para 
  ejecutarlo el siguiente comando: ::

    ./bin/zopepy
    >>>

  Este script es usado tanto por el comando ``mkzopeinstance`` para crear una instancia nueva de Zope, como hacer 
  introspección de Python al contexto de la instalación de Zope 2.


./bin/zpasswd

  Es una utilidad que permite crear un archivo de contraseña Zope ('access') para la cuenta de superusuario en Zope. 
  Este creará un archivo de contraseña con una sola línea con dos o tres campos separados por dos puntos: ``username:encrypted password[:domainlist]``.

  Si este archivo se denomina ``access`` y poner en el directorio ``INSTANCE_HOME`` de una instancia de Zope, el 
  servidor de aplicación Zope usará nombre de usuario y contraseña como valores para el superusuario (administrador) 
  de ese instancia.

  Si este programa se llama la línea de comandos sin opciones, este le mostrara toda la información necesaria para 
  ejecutar correctamente el comando ::

    ./bin/zpasswd

  Aquí hay un ejemplo mas real donde se define al usuario ``NUEVO-USUARIO``, con la contraseña ``CONTRASENA-SUPER-SECRETA`` 
  como administrador de unas instancia en especifica, ejecutando el siguiente comando: ::

    ./bin/zpasswd -u NUEVO-USUARIO -p CONTRASENA-SUPER-SECRETA $INSTANCE_HOME/access

  Para más información consulte la ayuda incluida en el script con el siguiente comando ``./bin/zpasswd -h``. 
  Adicionalmente consulte el articulo `Special Users - Zope 2 v2.13 documentation <https://zope.readthedocs.io/en/2.13/USERS.html>`_.

