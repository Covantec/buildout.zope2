zope2.buildout
==============

Configuración de buildout para el servidor de aplicaciones Zope2

Requerimientos
==============

Estos son los requerimientos mínimos de instalación: ::

  aptitude install gcc g++ make tar unzip bzip2 libssl-dev libxml2-dev zlib1g-dev libjpeg62-dev libreadline6-dev readline-common wv xpdf-utils python2.7-dev libxslt1-dev

Inicialización del proyecto
===========================

::
  python bootstrap.py

Construcción del proyecto
=========================

::
  ./bin/buildout

Ejecutar servidor Zope2
=======================

::
  ./bin/zope2 fg

