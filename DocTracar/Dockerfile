# Usa una imagen base de Debian 12
FROM openjdk:11-jre-slim

# Establece la variable de entorno para evitar interacciones durante la instalación
ENV DEBIAN_FRONTEND=noninteractive

# Actualiza los repositorios e instala dependencias necesarias
RUN apt-get update && \
    apt-get install -y  wget systemctl && \
    rm -rf /var/lib/apt/lists/*

# Copia el instalador de Traccar al contenedor
COPY . /app
WORKDIR /app

# Da permisos de ejecución al instalador y lo ejecuta
RUN chmod +x /app/traccar-linux-64-6.5/traccar.run && \
    /app/traccar-linux-64-6.5/traccar.run
# copia nuetro tracar modificado

RUN cp -f /app/tracker-server.jar /opt/traccar/

# Exponer el puerto 8082 (puerto por defecto de Traccar)
EXPOSE 8082

# Comando para inicializar el servicio al arrancar el contenedor
CMD ["bash", "-c", "systemctl restart traccar && tail -f /dev/null"]
