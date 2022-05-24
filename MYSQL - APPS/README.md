# MYSQL - APPS

## Que hace este Dockerfile?
Este Dockerfile tiene como imagen base de MySql el cual correra una una base de datos y montara sus datos de manera local para tener sus datos almacenados de manera persistente.

Este Contenedor puedes cambiarlo a tu voluntad para usarlo.

## Docker-Compose
En el archivo docker-compose.yml se tiene la posibilidad de correr mas de un solo contenedor, donde correras el contenedor que contiene MySQL ademas de tener la posibilidad de agregar otro servicio el cual sea una app que dependa de una base de datos.
