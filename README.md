# 🏍️ SmartMottu: Sistema de Detecção e Alerta Logístico

Este projeto utiliza **Inteligência Artificial (Visão Computacional)** integrada a um **Banco de Dados Oracle** para monitorar e alertar sobre inconsistências logísticas no pátio de motos da **Mottu**, garantindo a correta alocação de ativos.

---

## 🎯 Resultados Finais e Objetivo

O principal resultado do projeto é a **Interface de Alerta Logístico em Tempo Real (Gradio)**, que valida a detecção da IA contra o status do banco de dados.  
O sistema demonstra a viabilidade da integração entre **Deep Learning** e serviços de banco de dados para a **prevenção de erros logísticos**, aumentando a **eficiência e a segurança** no gerenciamento de ativos.

---

### 🚨 Inconsistência Crítica (Alerta Máximo)

O alerta é acionado quando uma moto com status **AGUARDANDO REPARO** no BD é detectada no setor operacional, o **PATIO_PRINCIPAL**.

---

## 🛠️ Tecnologias Utilizadas

O projeto é baseado em uma arquitetura robusta que combina **Machine Learning** com **serviços de banco de dados**.

---

## 💻 Tecnologias Chave

| Componente | Tecnologia | Finalidade |
|-------------|-------------|-------------|
| Visão Computacional | TensorFlow / Keras | Classificação de modelos de moto (elétrica, pop, sport). |
| Banco de Dados | Oracle Cloud | Armazenamento do status logístico (AGUARDANDO REPARO, DISPONÍVEL, etc.). |
| Conexão BD | Python oracledb | Módulo de conectividade nativa Python com o Oracle. |
| Interface de Usuário | Gradio | Criação do frontend interativo para simulação de câmera e exibição de alertas. |
| Processamento de Imagem | Pillow (PIL) | Desenho dinâmico do ponto de alerta no mini-mapa esquemático (`mapa_setores.png`). |

---

## 🏗️ Estrutura do Projeto e Fluxo de Dados

O código-fonte e a estrutura do projeto seguem uma arquitetura modular que integra os seguintes componentes:

### 📁 Estrutura de Arquivos

- `notebook_principal.ipynb` (ou `main.py`): Contém todo o código-fonte principal (IA, lógica Oracle e Gradio).  
- `meu_modelo.keras`: Arquivo do modelo de Deep Learning treinado.  
- `mapa_setores.png`: Imagem do mapa esquemático da fábrica (500x500 pixels).  

---

### 🔄 Fluxo de Dados

1. **INPUT (Gradio)**: Imagem da moto e o setor atual (`PATIO_PRINCIPAL`).  
2. **CLASSIFICAÇÃO (IA/Keras)**: A IA identifica o modelo da moto (ex: `MOTTU_POP_125`).  
3. **VALIDAÇÃO (Python/Oracle)**: O código consulta o status e a localização esperada daquele modelo no Oracle.  
4. **ALERTA (Lógica Python)**:  
   Se o status indica **reparo (AGUARDANDO REPARO)** e a localização atual é o **PATIO_PRINCIPAL**, um alerta logístico grave é emitido.  
5. **OUTPUT (Gradio)**: Exibição da tabela de status, o alerta detalhado e a marcação no mini-mapa de localização.  

---

## ⚙️ Instruções de Uso e Requisitos

### 1. Requisitos de Ambiente e Dependências

Para executar o projeto, instale todas as bibliotecas no seu ambiente (ex: Google Colab):

```bash
!pip install tensorflow keras oracledb gradio Pillow numpy opencv-python-headless
