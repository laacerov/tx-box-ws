FROM alphacep/kaldi-vosk-server:latest

ENV MODEL_VERSION 0.42
RUN mkdir /opt/vosk-model-es \
   && cd /opt/vosk-model-es \
   && wget -q https://alphacephei.com/vosk/models/vosk-model-es-${MODEL_VERSION}.zip \
   && unzip vosk-model-es-${MODEL_VERSION}.zip \
   && mv vosk-model-es-${MODEL_VERSION} /opt/vosk-server/webrtc/model \
   && rm -rf vosk-model-es-${MODEL_VERSION}.zip

RUN cd /opt/vosk-server/webrtc
RUN python3 -m pip install aiortc aiohttp aiorpc vosk

EXPOSE 2700

WORKDIR /opt/vosk-server/webrtc
CMD [ "python3", "./asr_server_webrtc.py", "/opt/vosk-server/webrtc/model" ]
