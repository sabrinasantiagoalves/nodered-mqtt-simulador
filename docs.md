
# 📘 Documentação Técnica – Sistema de Controle de Nível de Água com ESP32

## 1. Visão Geral

O projeto tem como objetivo monitorar o nível de água em um reservatório e controlar automaticamente uma válvula com base nas leituras de um sensor ultrassônico. A comunicação com o usuário ocorre por meio do protocolo MQTT.

---

## 2. Hardware Utilizado

### Microcontrolador:
- ESP32 DevKit V1 – com Wi-Fi integrado e suporte a MQTT

### Sensor:
- HC-SR04 – sensor de distância ultrassônico
  - VCC → 5V
  - GND → GND
  - Trigger → GPIO 5
  - Echo → GPIO 18

### Atuador:
- Válvula Solenoide (simulada com LED vermelho)
  - Anodo → GPIO 19 (via resistor 220Ω)
  - Cátodo → GND

### Outros:
- Protoboard, cabos jumper, fonte 5V
- Resistor de 220Ω para simulação segura do LED

---

## 3. Esquema de Montagem

📷 *Ver imagem em `diagram.png` ou `diagram.fzz`*

- Sensor conectado diretamente ao ESP32
- LED simula o comportamento da válvula
- Alimentação via USB ou fonte 5V externa
- Comunicação com broker MQTT via Wi-Fi

---

## 4. Fluxo de Funcionamento

```plaintext
Início
  ↓
Ler distância com HC-SR04
  ↓
Determinar nível de água (baixo, médio, alto)
  ↓
Se "baixo" → liga válvula (LED ON)
Se "alto" → desliga válvula (LED OFF)
  ↓
Envia dados ao broker MQTT
  ↓
Aguarda próximo ciclo
  ↓
(recomeça)
```

---

## 5. Protocolo e Interface de Comunicação

### Protocolo: MQTT

- **Broker usado:** broker.hivemq.com
- **Cliente:** ESP32 com biblioteca PubSubClient
- **Tópicos:**
  - `nivelagua/sabrina` (publicação)

### Formato da mensagem:

```
"💧 Válvula ABERTA (nível: %ldcm)"
"🚫 Válvula FECHADA (nível: %ldcm)"
"🔄 Nível dentro do intervalo (%ldcm). Nenhuma ação."

```

---

## 6. Requisitos de Software

- [Arduino IDE](https://www.arduino.cc/en/software)
- Bibliotecas:
  - `PubSubClient`
  - `WiFi.h`
  - `NewPing.h` (ou similar para HC-SR04)

---

## 7. Melhorias Futuras

- Substituir HC-SR04 por sensor à prova d’água (ex: JSN-SR04T)
- Adicionar banco de dados para histórico dos níveis
- Integração com dashboard web ou aplicativo móvel
- Inclusão de notificações por e-mail ou Telegram em caso de alerta

---

## 8. Créditos

Desenvolvido por **Sabrina Santiago Alves**  
Universidade Presbiteriana Mackenzie – FCI  
Análise e Desenvolvimento de Sistemas
2025
