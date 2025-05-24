# Sistema IoT de Monitoramento e Controle de Nível de Água

Este projeto utiliza ESP32, sensor ultrassônico HC-SR04 e válvula solenoide para controle automatizado de nível de água, com comunicação via MQTT.

## 🔧 Hardware Utilizado
- ESP32 (Wi-Fi + MQTT)
- Sensor Ultrassônico HC-SR04
- Válvula Solenoide 12V
- Driver de potência (relé ou transistor)
- Fonte 12V/5V
- Protoboard e jumpers

## 🌐 Comunicação
Utiliza protocolo MQTT para envio e recepção de dados. Broker: `broker.hivemq.com`.

## 📦 Estrutura do Projeto
- `/src`: Código do ESP32
- `/fritzing`: Esquema eletrônico
- `/doc`: Fluxogramas, gráficos e diagramas

## 📈 Como usar
1. Compile o código com Arduino IDE
2. Suba para o ESP32
3. Conecte aos tópicos MQTT via Node-RED ou MQTT Explorer

## 📡 Tópicos MQTT
- `nivelagua/estado`: Publica dados do nível
- `nivelagua/comando`: Recebe comandos externos

