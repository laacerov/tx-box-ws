FROM ubuntu:22.04

# Instalar dependencias necesarias
RUN apt-get update && apt-get install -y \
    gstreamer1.0-tools \
    gstreamer1.0-plugins-good \
    gstreamer1.0-plugins-bad \
    gstreamer1.0-plugins-ugly \
    gstreamer1.0-libav \
    wget \
    && apt-get clean

# Descargar e instalar websocat
RUN wget -qO /usr/local/bin/websocat https://github.com/vi/websocat/releases/latest/download/websocat.x86_64-unknown-linux-musl -O /usr/local/bin/websocat && \
#RUN wget https://github.com/vi/websocat/releases/latest/download/websocat.x86_64-unknown-linux-gnu -O /usr/local/bin/websocat && \
    chmod +x /usr/local/bin/websocat

# Instalamos WebSocket Sink (si es necesario) desde su repositorio
RUN apt-get update && apt-get install -y \
    gstreamer1.0-websocketsink \
    && apt-get clean

ENV GST_PLUGIN_SCANNER=/usr/lib/x86_64-linux-gnu/gstreamer1.0/gst-plugin-scanner

# Establecer un directorio de trabajo
WORKDIR /root

# Comando por defecto para el contenedor
CMD ["/bin/bash"]
