# Practica_master_slave

Este repositorio contiene la práctica de despliegue de aplicaciones web con configuración de DNS.

1. Se inicializó el archivo `Vagrantfile` utilizando el comando `vagrant init`.
2. Las máquinas virtuales fueron configuradas según las indicaciones del ejercicio 2. Se emplearon contenedores de Vagrant, específicamente bullseye64. A cada máquina se le asignó un nombre de host, una IP fija y se incluyó un script de provisión que actualiza la VM e instala las herramientas necesarias para la configuración del DNS.

3. En la máquina `Tierra`, se configuró el archivo `named.conf.options` con los siguientes ajustes:
   1. Deshabilitar la escucha en direcciones IPv6.
   2. Permitir consultas desde la red interna.
   3. Habilitar consultas recursivas.
   4. Activar DNSSEC.
   5. Establecer la dirección `208.67.222.222` para el reenvío de consultas.

   ![Configuración de Tierra](./imagenes/configuracionTierra.png)

4. Se editó el archivo `named.conf.local` en `Tierra`, otorgándole autoridad sobre las zonas directa e inversa.

   ![Configuración de named.conf.local en Tierra](./imagenes/zonasDeTierra.png)

5. Se crearon y configuraron los archivos `db.sistema.test` y `db.192`, donde se definieron los detalles de las zonas y los puertos para las conexiones.

   ![Configuración de db.sistema.test](./imagenes/baseDatos1.png)

   ![Configuración de db.192](./imagenes/baseDatos2.png)

6. Luego de configurar la máquina `Tierra`, se procedió a configurar el DNS en la máquina `Venus`. Se modificó el archivo `named.conf.local` para añadir la configuración de las zonas directa e inversa.

   ![Configuración de named.conf.local en Venus](./imagenes/configuracionVenus.png)

7. Una vez completada la edición de los archivos, se ajustó la provisión de cada VM para copiar los archivos a los directorios correspondientes, garantizando que el sistema pueda replicarse en otros entornos. Se añadieron líneas de código en los scripts de provisión para automatizar este proceso.

8. Finalmente, se llevaron a cabo las comprobaciones requeridas en la práctica para verificar la correcta configuración del DNS.

   ![Imagen 1](./imagenes/foto1.png)

   ![Imagen 2](./imagenes/foto2.png)

   ![Imagen 3](./imagenes/foto3.png)

   ![Imagen 4](./imagenes/foto4.png)

   ![Imagen 5](./imagenes/foto5.png)

   ![Imagen 6](./imagenes/foto6.png)

   ![Imagen 7](./imagenes/foto7.png)