# Limitar uso de procesador
Limitar la cantidad de núcleos de CPU:
```
--cpus=<número de núcleos>
```

Asignar núcleos de CPU específicos:
```
--cpuset-cpus=<lista de núcleos>
```

**¿Como saber el numero de procesadores virtuales que tiene una máquina?**
Para averiguar la cantidad de procesadores lógicos (núcleos virtuales) de tu equipo, puedes utilizar la terminal dependiendo de tu sistema operativo:

* **En Linux o WSL (Entorno nativo de Docker):** Ejecuta el comando `nproc`. También puedes usar `lscpu` para obtener un detalle completo de la arquitectura del procesador.
* **En Windows (Git Bash):** Ejecuta el comando `echo $NUMBER_OF_PROCESSORS` o `wmic cpu get NumberOfLogicalProcessors`.

## Ejemplos
_Puedes copiar y ejecutar directamente cada uno de los comandos_

Limitar el uso de CPU a 1.5 núcleos
```
docker run -d --name server-nginx --cpus="1.5" nginx:alpine
```

Restringir el contenedor para que use los núcleos de CPU 0 a 2:
```
docker run -d --name server-nginx --cpuset-cpus="0-2" nginx:alpine
```

Restringir el contenedor para que use los núcleos de CPU 1 y 3:
```
docker run -d --name server-nginx --cpuset-cpus="1,3" nginx:alpine
```
