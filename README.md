# Projeto I - Sistema Especialista para Diagnóstico de Problemas em Plantações

## Descrição do Domínio

Este projeto implementa um Sistema Baseado em Conhecimento (SBC), desenvolvido com a biblioteca Experta em Python, para auxiliar no diagnóstico de problemas em plantações.

O sistema utiliza regras de produção do tipo IF–THEN organizadas em uma base de conhecimento para analisar características observadas na plantação e inferir possíveis causas para os problemas identificados, além de sugerir ações corretivas adequadas. Os diagnósticos contemplam quatro áreas principais:

- Deficiência nutricional
- Problemas de irrigação
- Doenças fúngicas
- Infestação por pragas

O mecanismo de inferência utiliza encadeamento progressivo (forward chaining), disparando regras a partir dos fatos informados pelo usuário. O sistema possui uma interface simples baseada em perguntas e respostas. Durante a execução, o usuário informa os sintomas observados na plantação respondendo "s" (sim) ou "n" (não) para cada pergunta apresentada. Com base nessas informações, o mecanismo de inferência aplica as regras da base de conhecimento para gerar diagnósticos e recomendações.

---

## Descrição das Regras

### Nutrição

**Regra 1:**	Folhas amarelas indicam possível deficiência nutricional.

**Regra 2:**	Deficiência nutricional juntamente com crescimento lento sugere deficiência de nitrogênio.

**Regra 3:** Confirma o diagnóstico de deficiência de nitrogênio.

**Regra 4:** Recomenda aplicação de adubação nitrogenada.

**Regra 5:** Recomenda monitorar a recuperação nutricional da plantação.

### Irrigação

**Regra 6:**	Solo seco indica possível falta de irrigação.

**Regra 7:**	Falta de água e folhas murchas caracterizam estresse hídrico.

**Regra 8:**	Recomenda aumento da irrigação.

**Regra 9:**	Cria um plano de irrigação.

**Regra 10:** Recomenda monitoramento da umidade do solo.

### Doenças Fúngicas

**Regra 11:** Manchas escuras indicam possível infecção fúngica.

**Regra 12:** Umidade elevada aumenta o risco da doença.

**Regra 13:** Recomenda aplicação de fungicida.

**Regra 14:** Recomenda monitoramento da evolução da doença.

**Regra 15:** Gera alerta de prioridade alta quando existe risco de fungos sem tratamento aplicado.

### Pragas

**Regra 16:** Folhas perfuradas indicam possível presença de insetos.

**Regra 17:** Presença de lagartas confirma infestação.

**Regra 18:** Recomenda controle biológico.

**Regra 19:** Em caso de dano severo, recomenda controle químico.

**Regra 20:** Gera alerta de aplicação química urgente.

---

## Casos de Teste

### Caso de Teste 1 - Deficiência Nutricional

#### Entrada (sintomas):

```
SISTEMA ESPECIALISTA AGRÍCOLA

RESPONDA COM S OU N

Folhas amarelas (s/n): s
Crescimento lento (s/n): s
Solo seco (s/n): n
Folhas murchas (s/n): n
Manchas escuras (s/n): n
Alta umidade (s/n): n
Folhas perfuradas (s/n): n
Presença de lagartas (s/n): n
Dano severo (s/n): n
```

#### Saída Obtida:

```
PROCESSANDO...

R1 → Suspeita de deficiência nutricional
R2 → Deficiência de nitrogênio porque existe deficiência nutricional e crescimento lento.
R5 → Monitorar recuperação da planta
R4 → Plano de correção nutricional criado
R3 → Aplicar adubação nitrogenada

DIAGNÓSTICO FINAL:
- Correção nutricional
- Deficiência nutricional

RECOMENDAÇÕES:
- Adubação nitrogenada
```

As regras R1 e R2 foram acionadas porque a plantação apresentou folhas amarelas e crescimento lento. A partir dessas inferências, o sistema identificou uma deficiência nutricional associada à falta de nitrogênio. Em seguida, as regras R3, R4 e R5 geraram recomendações relacionadas à adubação nitrogenada e ao monitoramento da recuperação da plantação.

### Caso de Teste 2 - Estresse Hídrico

#### Entrada (sintomas):

```
SISTEMA ESPECIALISTA AGRÍCOLA

RESPONDA COM S OU N

Folhas amarelas (s/n): n
Crescimento lento (s/n): n
Solo seco (s/n): s
Folhas murchas (s/n): s
Manchas escuras (s/n): n
Alta umidade (s/n): n
Folhas perfuradas (s/n): n
Presença de lagartas (s/n): n
Dano severo (s/n): n
```

#### Saída Obtida:

```
PROCESSANDO...

R6 → Falta de irrigação suspeita
R7 → Estresse hídrico porque o solo está seco e as folhas estão murchas.
R9 → Plano de irrigação criado
R8 → Aumentar irrigação
R10 → Monitorar umidade do solo

DIAGNÓSTICO FINAL:
- Estresse hídrico

RECOMENDAÇÕES:
- Aumentar irrigação
```

As regras R6 e R7 foram disparadas devido à combinação de solo seco e folhas murchas. O sistema inferiu a ocorrência de estresse hídrico e acionou as regras R8, R9 e R10, responsáveis pelas recomendações de aumento da irrigação e monitoramento da umidade do solo.

### Caso de Teste 3 - Doença Fúngica

#### Entrada (sintomas):

```
SISTEMA ESPECIALISTA AGRÍCOLA

RESPONDA COM S OU N

Folhas amarelas (s/n): n
Crescimento lento (s/n): n
Solo seco (s/n): n
Folhas murchas (s/n): n
Manchas escuras (s/n): s
Alta umidade (s/n): s
Folhas perfuradas (s/n): n
Presença de lagartas (s/n): n
Dano severo (s/n): n
```

#### Saída Obtida:

```
PROCESSANDO...

R11 → Suspeita de fungos porque foram detectadas manchas escuras.
R12 → Risco elevado de fungos porque há manchas escuras e alta umidade.
R15 → ALERTA: fungicida não aplicado
R13 → Aplicar fungicida
R14 → Monitorar evolução da doença

DIAGNÓSTICO FINAL:
- Doença fúngica

RECOMENDAÇÕES:
- Fungicida
```

As regras R11 e R12 foram acionadas pela presença de manchas escuras e alta umidade. Como o sistema inferiu risco elevado de doença fúngica, a regra R15 gerou um alerta prioritário devido à ausência do fato fungicida_aplicado. Em seguida, as regras R13 e R14 recomendaram a aplicação de fungicida e o monitoramento da evolução da doença.

---

## Como Executar

### 1. Executar o Programa

Abra o arquivo `projeto_I.ipynb` no Google Colab e execute as células em ordem, do início ao fim.

O sistema solicitará ao usuário que informe os sintomas observados na plantação respondendo com "s" (sim) ou "n" (não) para cada pergunta apresentada.

### 2. Saída Esperada

Ao executar o programa, o motor de inferência processará os fatos declarados e exibirá no terminal as regras acionadas, os diagnósticos identificados e as recomendações correspondentes ao cenário informado pelo usuário.

---
