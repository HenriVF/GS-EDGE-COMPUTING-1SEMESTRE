# 🌌 Edge Computing - OBC de um CubeSat (Global Solution 1Semestre)

## 📋 Descrição do Projeto
Este projeto consiste na arquitetura e prototipagem do Computador de Bordo (OBC - On-Board Computer) de um CubeSat (nanossatélite orbital). O sistema foi concebido com foco absoluto em eficiência energética crítica para o ambiente aeroespacial. Eliminando indicadores visuais locais redundantes (como LEDs), o software embarcado realiza o processamento de borda (Edge Computing) para monitorar variáveis físicas orbitais e automatizar de forma inteligente o subsistema de geração de energia fotovoltaica.

## 🎯 Objetivo da Solução
* **Gerenciamento Térmico:** Monitorar a temperatura interna do satélite, identificando janelas críticas de congelamento ou superaquecimento espacial.
* **Automação de Atuadores:** Orientar dinamicamente o ângulo dos painéis solares através de um servo motor baseado na incidência de luz captada.
* **Telemetria Espacial:** Transmitir pacotes condensados de dados em tempo real para as estações terrestres e atualizar o display físico de diagnóstico de bordo.

## 🛠️ Componentes Utilizados
* 1x Arduino Uno (Processador OBC)
* 1x Servomotor (Atuador de Orientação dos Painéis Fotovoltaicos)
* 1x Potenciômetro (Simulador do Sensor de Temperatura Interna do Satélite)
* 1x Display LCD 16x2 com Módulo I2C integrado (Monitor de Diagnóstico de Bordo)
* 1x Protoboard Half-Size e Cabos de Conexão Jumpers

## 🧠 Explicação do Funcionamento
O algoritmo de bordo executa em um loop contínuo dividindo-se em:
1. **Coleta e Mapeamento de Dados:** Lê o sensor de temperatura simulado (convertendo a escala para uma variação espacial de -40°C a 80°C) e a incidência de luz.
2. **Atuação Proporcional:** Caso haja luz solar viável (>20%), o servomotor ajusta o ângulo das placas de 10° a 180° para otimizar a geração elétrica. Se o satélite entrar no cone de sombra da Terra (Modo Eclipse), as placas são recolhidas automaticamente para 0° para proteção térmica.
3. **Triagem de Segurança e Estados:** Classifica a operação da missão em três estados: `NOMINAL` (operação segura), `LOW POWER` (atenção por baixa energia ou variação térmica) e `CRITICAL` (alerta térmico severo abaixo de -10°C ou acima de 50°C).
4. **Transmissão:** Envia os dados estruturados de telemetria via rádio simulado (Monitor Serial) e escreve o status diretamente no LCD I2C.

## 🔌 Estrutura do Circuito e Instruções de Execução
O circuito utiliza a interface de comunicação simplificada I2C para operação do Display LCD, conectando os pinos SDA e SCL nas portas analógicas `A4` e `A5` do Arduino, minimizando o uso de barramentos elétricos. O potenciômetro está mapeado na entrada analógica `A1` e o servomotor recebe os pulsos de controle PWM na porta digital `9`.

## LINK DO PROJETO WOKWI
https://wokwi.com/projects/465037091130342401
## LINK DA SIMULAÇÃO DO PROJETO WOKWI

## LINK DO VIDEO DA SOLUÇÃO DO PROJETO

**Para executar a simulação:**
1. Copie o arquivo `diagram.json` para o ambiente do Wokwi para carregar o layout.
2. Certifique-se de incluir a biblioteca `LiquidCrystal I2C` no gerenciador de dependências do simulador.
3. Carregue o código do `sketch.ino` e clique em "Iniciar Simulação".
4. Altere os valores no potenciômetro para testar as mudanças de estados no LCD e as mensagens no Monitor Serial.

## 👥 Integrantes do Grupo
* **Nome:** Henrique Vieira Ferreira - RM:569586
* **Nome:** Leonardo Barrocal - RM:571031
