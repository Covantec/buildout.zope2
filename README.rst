buildout.zope2
==============

Configuración de buildout para el servidor de aplicaciones Zope2

Requerimientos
==============

Estos son los requerimientos mínimos de instalación: ::

  sudo apt-get install gcc g++ make tar unzip bzip2 libssl-dev libxml2-dev zlib1g-dev \
                       libjpeg62-dev libreadline6-dev readline-common wv xpdf-utils \
                       python2.7-dev libxslt1-dev

Inicialización del proyecto
===========================

Para la inicialización del proyecto Buildout, ejecute el siguiente comando: ::

  python bootstrap.py

Construcción del proyecto
=========================

Para la construcción del proyecto Buildout, ejecute el siguiente comando: ::

  ./bin/buildout

Ejecutar servidor Zope2
=======================

Para ejecutar servidor Zope2, ejecute el siguiente comando: ::

  ./bin/zope2 fg

Otros comandos disponibles
==========================

./bin/addzope2user

  Permite agregar un nuevo usuario Zope, ejecutando el siguiente comando: ::

    ./bin/addzope2user <username> <password>

./bin/mkzopeinstance

  Permite crear una instancia de Zope. agregar un nuevo usuario Zope, ejecutando el siguiente comando: ::

    ./bin/mkzopeinstance -d $PWD/z2instance -u admin:admin --python=$PWD/bin/zopepy

  Para mas información consulte la ayuda incluida en el script con el siguiente comando ``./bin/mkzopeinstance -h``.

./bin/runzope

  Es el script ejecutor del ZDaemon (servicio) Zope, para ejecutarlo ejecute el siguiente comando: ::

    ./bin/runzope -C $PWD/parts/zope2/etc/zope.conf

  Para mas información consulte la ayuda incluida en el script con el siguiente comando ``./bin/runzope -h``.

./bin/zope2

  Es el script que lleva por nombre de la sección buildout que construye automáticamente Zope 2 ``zope2``, eso quiere decir, controla la instancia Zope usando ZDaemon, como lo hace el ``zopectl`` (mas adelante se detalla), para ejecutarlo el siguiente comando: ::

    ./bin/zope2 fg

  Para mas información consulte la ayuda incluida en el script con el siguiente comando ``./bin/zope2 -h``.

./bin/zopectl

  Es el script que controla la instancia Zope usando ZDaemon, para ejecutarlo el siguiente comando: ::

    ./bin/zopectl start

  Para mas información consulte la ayuda incluida en el script con el siguiente comando ``./bin/zopectl -h``. Adicionalmente consulte `Installing and Zope with zc.buildout — Zope 2 v2.x documentation <http://docs.zope.org/zope2/releases/2.12/INSTALL-buildout.html>`_.

./bin/zopepy

  Es el script que acceder a una consola interactiva de Python al contexto de la instalación de Zope 2, para ejecutarlo el siguiente comando: ::

    ./bin/zopepy
    >>>

  Este script es usado tanto por el comando ``mkzopeinstance`` para crear una instancia nueva de Zope, como hacer introspección de Python al contexto de la instalación de Zope 2.

./bin/zpasswd

  Es una utilidad que permite crear un archivo de contraseña Zope ('access') para la cuenta de superusuario en Zope. Este creará un archivo de contraseña con una sola línea con dos o tres campos separados por dos puntos: ``username:encrypted password[:domainlist]``.

  Si este archivo se denomina ``access`` y poner en el directorio ``INSTANCE_HOME`` de una instancia de Zope, Zope usará nombre de usuario y contraseña como valores para el superusuario (administrador) de ese instancia.

  Si este programa se llama la línea de comandos sin opciones, este le mostrara toda la información necesaria para ejecutar correctamente el comando ::

    ./bin/zpasswd

  Aquí hay un ejemplo mas real donde se define al usuario ``NUEVO-USUARIO``, con la contraseña ``CONTRASENA-SUPER-SECRETA`` como administrador de uns instancia en especifica, ejecutando el siguiente comando: ::

    ./bin/zpasswd -u NUEVO-USUARIO -p CONTRASENA-SUPER-SECRETA $INSTANCE_HOME/access

  Para mas información consulte `Special Users - Zope 2 v2.x documentation <http://docs.zope.org/zope2/releases/2.12/USERS.html>`_.

