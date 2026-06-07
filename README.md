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
R2 → Deficiência de nitrogênio
R4 → Plano de correção nutricional criado
R3 → Aplicar adubação nitrogenada
R5 → Monitorar recuperação da planta

DIAGNÓSTICO FINAL:
- Correção nutricional
- Deficiência nutricional

RECOMENDAÇÕES:
- Adubação nitrogenada
```

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
R7 → Estresse hídrico
R8 → Aumentar irrigação
R10 → Monitorar umidade do solo
R9 → Plano de irrigação criado

DIAGNÓSTICO FINAL:
- Estresse hídrico

RECOMENDAÇÕES:
- Aumentar irrigação
```

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

R11 → Suspeita de fungos
R12 → Risco elevado de fungos
R15 → ALERTA: fungicida não aplicado
R14 → Monitorar evolução da doença
R13 → Aplicar fungicida

DIAGNÓSTICO FINAL:
- Doença fúngica

RECOMENDAÇÕES:
- Fungicida
```

---

## Como Executar

### 1. Executar o Programa

Abra o arquivo `projeto_I.ipynb` no Google Colab e execute as células em ordem, do início ao fim.

O sistema solicitará ao usuário que informe os sintomas observados na plantação respondendo com "s" (sim) ou "n" (não) para cada pergunta apresentada.

### 2. Saída Esperada

Ao executar o programa, o motor de inferência processará os fatos declarados e exibirá no terminal as regras acionadas, os diagnósticos identificados e as recomendações correspondentes ao cenário informado pelo usuário.

---
