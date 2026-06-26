# RoboPV ESP32-CAM

Firmware da **ESP32-CAM** utilizada no protótipo robótico **RoboPV** para transmissão de imagem em tempo real durante a operação remota de limpeza de módulos fotovoltaicos.

Este código é executado em uma placa **ESP32-CAM**, responsável exclusivamente pela captura e disponibilização do vídeo para a interface de operação do robô.

O sistema foi desenvolvido como parte do Trabalho de Conclusão de Curso:

**Desenvolvimento de um protótipo robótico para limpeza de sistemas fotovoltaicos de pequeno porte**

## Visão geral

O RoboPV é um protótipo robótico operado remotamente, projetado para auxiliar a limpeza de módulos fotovoltaicos de pequeno porte. O sistema utiliza um **ESP32 DevKit** como controlador principal e uma **ESP32-CAM** como módulo dedicado de supervisão visual.

A ESP32-CAM se conecta à rede Wi-Fi local criada pelo ESP32 DevKit e disponibiliza a transmissão de imagem em tempo real. Esse vídeo pode ser acessado pelo navegador e incorporado à interface web de controle do protótipo.

## Função da ESP32-CAM no projeto

A ESP32-CAM não controla motores, sensores ou atuadores. Sua função principal é fornecer supervisão visual ao operador durante a operação remota.

Principais funções:

- conectar-se à rede Wi-Fi local do protótipo;
- inicializar a câmera embarcada;
- configurar resolução e parâmetros de imagem;
- iniciar servidor de vídeo;
- disponibilizar fluxo de imagem em tempo real;
- permitir que o operador acompanhe a região de limpeza.

## Arquitetura geral do sistema

O sistema do RoboPV é dividido em duas unidades embarcadas principais:

| Unidade | Função |
|---|---|
| ESP32 DevKit | Controle dos motores, escovas, válvula solenoide, sensores, interface web e controle PI das esteiras |
| ESP32-CAM | Captura e transmissão de imagem em tempo real |

A separação entre controle principal e câmera reduz a carga computacional sobre o ESP32 DevKit, deixando a ESP32-CAM dedicada ao processamento e transmissão de vídeo.

## Estrutura dos arquivos

```text
ESP32CAM_V1/
├── ESP32CAM_V1.ino
├── app_httpd.cpp
├── board_config.h
├── camera_index.h
├── camera_pins.h
├── partitions.csv
└── ci.yml
