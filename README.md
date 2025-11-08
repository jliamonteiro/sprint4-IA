# 🏍️ SmartMottu: Sistema de Detecção e Alerta Logístico

Este projeto utiliza Inteligência Artificial (Visão Computacional) integrada a um Banco de Dados Oracle para monitorar e alertar sobre inconsistências logísticas no pátio de motos da Mottu.

---

## 🚀 Visão Geral do Projeto

O **SmartMottu** garante que as motocicletas em manutenção ou bloqueio não sejam movimentadas para áreas operacionais (como o **Pátio Principal**), gerando um alerta imediato em tempo real.

O sistema verifica o status da moto detectada (Ex: `MOTTU_POP_125`) no banco de dados e compara sua localização esperada com a localização atual (fornecida pela câmera/Gradio).

### Inconsistência Crítica

O alerta máximo é acionado quando:
* **Moto Detectada (IA):** `MOTTU_POP_125`
* **Status no BD:** `AGUARDANDO REPARO`
* **Localização Atual (Câmera):** `PATIO_PRINCIPAL`

---
## 🏗️ Tecnologias Utilizadas e Arquitetura

O projeto é baseado em uma arquitetura robusta que combina **machine learning** com **serviços de banco de dados** para criar um sistema de **alerta logístico em tempo real**.

---

## 💻 Tecnologias Chave

| **Componente**           | **Tecnologia**          | **Finalidade**                                                                 |
|---------------------------|--------------------------|--------------------------------------------------------------------------------|
| **Visão Computacional**   | TensorFlow / Keras       | Classificação de modelos de moto (*elétrica, pop, sport*).                     |
| **Banco de Dados**        | Oracle Cloud             | Armazenamento do status logístico (*AGUARDANDO REPARO, DISPONÍVEL*, etc.).     |
| **Conexão BD**            | Python `oracledb`        | Módulo de conectividade nativa Python com o Oracle.                            |
| **Interface de Usuário**  | Gradio                   | Criação do frontend interativo para simulação de câmera e exibição de alertas. |
| **Processamento de Imagem** | Pillow (PIL)            | Desenho dinâmico do ponto de alerta no mini-mapa esquemático (*mapa_setores.png*). |

---

## 🏗️ Arquitetura e Fluxo de Dados

O projeto integra quatro componentes principais:

1.  **Modelo de IA (Keras/TensorFlow):** Classifica imagens em `eletrica`, `pop`, ou `sport`.
2.  **Base de Dados (Oracle Cloud):** Armazena o status logístico, placa e localização **esperada** das motos.
3.  **Lógica de Alerta (Python):** Faz a ponte entre a classificação da IA e a consulta ao BD, executando a lógica de comparação.
4.  **Interface de Usuário (Gradio):** *Frontend* para upload de imagem, seleção do setor de detecção e exibição dos resultados em texto e mapa.

---

## ⚙️ Requisitos e Configuração

### Dependências Python

Instale todas as dependências necessárias no Colab:

```bash
!pip install tensorflow keras oracledb gradio Pillow numpy opencv-python-headless
