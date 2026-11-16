# ☕ Kultive IoT — Inteligência Espacial e Telemetria Agrícola

![Status](https://img.shields.io/badge/Status-MVP%20Conclu%C3%ADdo-brightgreen)
![NASA Data](https://img.shields.io/badge/NASA-SMAP%20%7C%20GPM-blue)
![Hardware](https://img.shields.io/badge/IoT-ESP32%20%2B%20MQTT-orange)
![Mobile](https://img.shields.io/badge/App-Flutter%20%2B%20Leaflet-02569B)

> **Transformando dados orbitais da NASA e sensores IoT de baixo custo em decisões precisas de irrigação e rotação de culturas na palma da mão do agricultor.**

---

## 🔗 Links Rápidos (Demonstração)
* 🎥 **Vídeo Pitch (3 min):**[Site Demo](https://sites.google.com/view/kultive-app-iot/in%C3%ADcio)
* 🔌 **Simulação Hardware (Wokwi):** [Testar Circuito ESP32 Online](https://wokwi.com/projects/480639315244838913)
* 🌐 **Mockup App Mobile (Web):** [Acessar Mapa Interativo](https://sites.google.com/view/kultive-app-iot/simula%C3%A7%C3%A3o-fazenda)
* ⚡ **API Backend (Swagger):** [Documentação FastAPI](LINK_DA_SUA_API/docs)

---

## 🎯 O Problema
Produtores rurais enfrentam crescente imprevisibilidade climática, estresse hídrico e degradação do solo. Dados de satélite possuem excelente cobertura regional, mas baixa resolução espacial (~9 km) para a realidade de um talhão específico. Por outro lado, sensores físicos isolados não oferecem visão macro nem previsão climática integrada.

## 💡 A Solução
O **Kultive IoT** realiza a fusão de dados em duas camadas:
1. **Camada Orbital (Macro):** Extração automatizada de umidade superficial do solo (**NASA SMAP L4**) e precipitação (**NASA GPM IMERG**) via **Google Earth Engine**.
2. **Camada Terrestre (Micro):** Estações de campo baseadas em **ESP32** que coletam umidade e temperatura na zona radicular e transmitem via **MQTT**.

Nosso backend cruza ambas as fontes e aplica **calibração estatística por regressão linear**, eliminando o viés do satélite e entregando alertas críticos em tempo real no aplicativo mobile.

---

## 🏗️ Arquitetura do Sistema

```text
[ Satélites NASA (SMAP / GPM) ] ──► [ Google Earth Engine ]
                                              │
                                              ▼
[ Estação ESP32 ] ──(MQTT)──► [ Broker ] ──► [ Backend FastAPI (Calibração) ]
                                              │
                                              ▼
                                    [ App Mobile Flutter ]
                                    (Mapas Offline & Alertas)
