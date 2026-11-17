# Placar Eletrônico Digital / Contador de Pontos

Repositório destinado ao projeto final da disciplina de **Circuitos Digitais** do curso de Engenharia da Computação da Universidade Federal do Maranhão (UFMA). 

**Orientador:** Prof. Luiz Henrique Neves Rodrigues

## 👥 Equipe (4 Integrantes)
* André Luis Aguiar do Nascimento
* Guilherme Haniel Costa Passinho
* Hugo Samuel de Lima Oliveira
* Rai Abreu Machado

## 🎯 Sobre o Projeto
O projeto consiste no desenvolvimento de um placar eletrônico digital projetado para marcar pontos (de 0 a 9) para dois jogadores de forma independente. O circuito foi modelado através da metodologia de problemas, análise, síntese e verificação, utilizando lógica combinacional e sequencial com circuitos integrados da família 74HC e série 4000.

### Principais Funcionalidades
- **Contagem Independente:** Contagem de 0 a 9 para dois jogadores (Jogador A e Jogador B).
- **Filtro de Debounce:** Circuito RC projetado para evitar múltiplas contagens em um único acionamento mecânico do botão de incremento.
- **Reset Geral:** Um botão de reset unificado que zera simultaneamente a pontuação de ambos os jogadores de forma assíncrona.

## ⚙️ Arquitetura do Sistema
O sistema é dividido em três blocos funcionais principais, replicados para cada jogador:

1. **Entrada e Condicionamento (Debounce):** 
   Utiliza um botão de incremento com um filtro RC (Resistor de 10kΩ e Capacitor de 10μF) para criar um atraso (constante de tempo de 100ms) que limpa o ruído do contato mecânico (*bounce*).
2. **Módulo de Contagem (MOD-10):** 
   Utiliza o CI **74HC93** (contador binário de 4 bits). Ele é configurado como contador de década (0 a 9) através das portas OR do CI **74HC32**, que identificam o estado 10 (1010 em binário) e enviam um sinal de reset assíncrono.
3. **Decodificação e Visualização:** 
   O sinal BCD gerado pelo contador passa pelo decodificador/driver **CD4511**, que converte a lógica para ativar os segmentos correspondentes em um **Display de 7 Segmentos (Catodo Comum)**, com resistores limitadores de 330Ω.

## 🛠️ Tecnologias e Ferramentas Utilizadas
* **Softwares de Simulação:** 
  * [Tinkercad Circuits](https://www.tinkercad.com/) (Montagem em protoboard virtual)
  * [NI Multisim](https://www.ni.com/pt-br/support/downloads/software-products/download.multisim.html) (Desenho e validação esquemática e instrumentos virtuais como Osciloscópio e Analisador Lógico)
* **Componentes de Hardware:**
  * CI 74HC93 (Contador Binário)
  * CI CD4511 (Decodificador BCD → 7 Segmentos)
  * CI 74HC32 (Portas OR de 2 entradas)
  * Displays 7 Segmentos Catodo Comum
  * Resistores (330Ω, 10kΩ), Capacitores (10μF) e Chaves Tácteis (Push buttons)

## 📁 Estrutura do Repositório
*(Sugestão de pastas para você organizar seus arquivos no GitHub)*
* `/simulacoes`: Arquivos de projeto do Multisim e capturas de tela do Tinkercad.
* `/documentacao`: Relatórios técnicos, tabelas-verdade, mapas de Karnaugh e PDFs do projeto.
* `/esquematicos`: Imagens dos esquemáticos em nível de CIs e portas lógicas.

## 🚀 Status do Projeto
O circuito foi totalmente validado matematicamente, simulado com sucesso (cobrando testes de entradas normais, condições de limite e casos extremos de *bounce*) e encontra-se na fase de montagem física e validação em protoboard.
```eof
