
# Configuracion de BIND9

## Indice

- [1. Introducción](#1-introduccion)
- [2. Instalacición](#2-instalación)
    - [2.1 Comandos para la instalación](#21-comandos-para-la-instalación)
- [3. Configuracion de la maquina](#3-confifuracion-de-la-maquina)
- [4. Conceptos de bind9](#4-conceptos-de-bind9)
    - [4.1 Enlace a recursos de bind9](#41-enlace-a-recursos-de-bind9)

## 1. Introduccion

**BIND9** es el software de servidor DNS más utilizado en        internet, especialmente en sistemas Linux y Unix. Su función principal es actuar como una "guía telefónica" para las redes, traduciendo nombres de dominio que las personas pueden recordar.

> “***Idea clave**: traduce IPs a nombres de dominio.*”

## 2. Instalación


1. **Instalar el paquete:** Descargar e instalar BIND9 desde el gestor de paquetes de tu sistema operativo.
2. **Definir la zona:** Declarar tu dominio y la ruta de su archivo de configuración en `named.conf.local`.
3. **Crear el archivo de zona:** Copiar la plantilla base para rellenar los registros de tu dominio.
4. **Configurar el registro SOA:** Definir el servidor principal y los tiempos de actualización del DNS.
5. **Añadir registros A y CNAME:** Mapear el dominio y sus subdominios (como `www`) a sus respectivas direcciones IP.
6. **Verificar la sintaxis:** Validar que los archivos de configuración no tengan errores con `named-checkconf`.
7. **Reiniciar el servicio:** Aplicar los cambios reiniciando el demonio de BIND9 para que empiece a responder consultas.


---

 ### 2.1 Comandos para la instalación

- 1. Actualizar la maquina

``` Bash
sudo apt update
sudo apt upgrade -y
```
- 2. Instalacion de bind9

``` bash
sudo apt install bind9
```

## 3. Confifuracion de la maquina

| Funcion | Path | Comando
|--- | --- | ---
| Cambio de nombre | /etc/hostname | nano
| Cambio de nombre bucle local | /etc/hosts | nano
| Configuracion de red | /etc/network/interfaces | nano


## Comandos útiles
Para consultar la configuración de red:
```bash
ip addr
```
Para comprobar la conectividad:
```bash
ping 8.8.8.8
```


## 4. Conceptos de bind9

* **Resolución directa:** Transforma un dominio en una dirección IP.
* **Resolución inversa:** Traduce una dirección IP de vuelta a su nombre de dominio.
* **Servidor Caché:** Guarda las consultas frecuentes para acelerar la navegación local.
* **Autoridad de Zona:** Almacena y administra los registros oficiales de tus propios dominios.
* **Seguridad (DNSSEC):** Firma digitalmente las consultas para evitar falsificaciones de identidad.
* **Control local:** Permite mapear nombres internos para dispositivos dentro de una red privada.

### 4.1 Enlace a recursos de bind9
>  🌐 [Servidor DNS bind ](https://manuais.iessanclemente.net/index.php/Servidor_DNS_bind)

![Representacion del BIND9](https://cibersafety.com/wp-content/uploads/2025/09/Todo-sobre-BIND-768x512.png)
