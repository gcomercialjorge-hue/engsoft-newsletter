# Aula — Sistemas Operacionais: História, Conceitos e Estruturas

!!! info "Informações da Aula"
    **Disciplina:** Sistemas Operacionais  
    **Professor:** Rafael Descio, M.Sc.  
    **Data:** Março de 2026  
    **Carga Horária:** 60h (45h teórica / 15h prática)

---

## 🎯 Objetivos da Aula

- Entender a necessidade histórica do surgimento dos Sistemas Operacionais
- Identificar as principais fases evolutivas da computação
- Compreender o SO como **máquina estendida** e **gerenciador de recursos**
- Diferenciar as estruturas arquiteturais modernas (monolítico, microkernel, híbrido)

---

## 🧠 O que é um Sistema Operacional?

Um Sistema Operacional pode ser entendido de duas formas complementares:

### 1. Máquina Estendida (Abstração)

O SO **esconde a complexidade do hardware** e oferece uma interface amigável para o programador.

| Sem SO | Com SO |
|--------|--------|
| Setor de disco | Arquivo |
| Execução binária bruta | Processo |
| Endereços físicos | Memória virtual |

**Analogia:** É como dirigir um carro. Você pisa no acelerador e vira o volante, mas não precisa controlar a injeção eletrônica, combustão ou sincronismo das válvulas. O painel e os controles são a "máquina estendida".

### 2. Gerenciador de Recursos (Eficiência)

O SO atua como **árbitro** decidindo quem usa os recursos, quando e por quanto tempo.

Recursos gerenciados:
- CPU
- Memória
- Disco
- Rede
- Dispositivos de E/S

**Analogia:** Pense em um aeroporto. Aviões querem pousar, pistas são limitadas, portões são disputados. O controle de tráfego aéreo é o Sistema Operacional.

!!! quote "Frase do Professor"
    "A decisão que você toma em alto nível deve ser coerente com o que acontece no baixo nível."

---

## 📜 Linha do Tempo dos Sistemas Operacionais

### Era Zero: Pré-Sistema Operacional (1940–1955)

**Características:**
- Programação manual via painéis de plugues e chaves
- Válvulas eletrônicas (alto consumo, falhas frequentes)
- Um programa por vez
- Operadores humanos controlavam tudo
- Nenhuma abstração de hardware

**Problemas:**
- Máquina ficava ociosa durante o setup manual
- Tempo de preparação maior que tempo de execução
- Extremamente ineficiente

**Marco:** ENIAC (1945) — Electronic Numerical Integrator And Computer

---

### 2ª Geração: Sistemas em Lote / Batch (1955–1965)

**Inovações:**
- Transistores substituem válvulas → menor aquecimento, mais confiabilidade
- Cartões perfurados para entrada de dados
- Fitas magnéticas para armazenamento

**O Monitor Residente** — primeiro "embrião" de SO:
- Pequeno programa sempre carregado na memória
- Carregava automaticamente o próximo trabalho
- Introduziu fila de execução (job queue)
- Reduziu intervenção humana

**Problema persistente:** CPU ainda ficava 90% ociosa esperando E/S (entrada/saída)

---

### 3ª Geração: Multiprogramação e Time-Sharing (1965–1980)

**Inovações:**
- Circuitos Integrados (ICs) substituem transistores
- Mainframes mais poderosos e confiáveis
- Terminais conectados a um computador central

**Multiprogramação:**
- Vários programas na memória simultaneamente
- Quando um espera E/S, o SO alterna para outro
- Nascem os conceitos de **escalonamento** e **gestão de memória**

**Time-Sharing (Tempo Compartilhado):**
- SO divide o tempo da CPU entre múltiplos usuários
- Cada usuário sente que tem a máquina inteira
- Interação em tempo real

**Marcos:** CTSS, MULTICS, e o nascimento do **UNIX** e da **Linguagem C**

!!! tip "Dica"
    A linguagem C é considerada a melhor para programação em nível de máquina por sua proximidade com o hardware.

---

### 4ª Geração: Computadores Pessoais (1980–2000)

**Características:**
- Sistemas multiusuário e multitarefa
- Interfaces gráficas (GUI)
- Suporte a redes
- Maior abstração de hardware
- Proteção de memória e modos usuário/kernel
- Sistemas portáveis e padronizados (**POSIX**)

**Padrão ASCII (1960):** Padronização dos códigos binários para representar caracteres.

---

### 5ª Geração: Dispositivos Móveis e Cloud (2000–hoje)

**Características:**
- SO como plataforma de serviços
- Computação distribuída e móvel
- Recursos provisionados sob demanda
- Kernel é parte de um ecossistema maior
- Sistemas embarcados (IoT, Indústria 5.0)

**Arquitetura ARM:** Dominante em dispositivos móveis e embarcados.

!!! quote "Dica do Professor"
    "Quando vai programar, eu preciso entender qual a necessidade de SO. O que eu vou programar? Qual SO vai me servir melhor?"

---

## 🔧 Conceitos Fundamentais

### Chamadas de Sistema (System Calls)

Programas **não acessam o hardware diretamente** por segurança. Usam chamadas de sistema:

- São solicitações formais de serviços ao SO
- Exemplos: `read()`, `write()`, `fork()`
- Padronização via APIs (ex: POSIX)

### Modos de Execução

| Modo | Descrição |
|------|-----------|
| **Modo Usuário** | Restrito, sem acesso direto ao hardware |
| **Modo Kernel** | Privilegiado, controle total da máquina |

O processador alterna entre esses modos para garantir segurança e integridade.

### Sistema de Cache

- Quanto mais próximo da CPU, mais rápido o acesso
- Quanto mais próximo da máquina, mais "desagradável" a programação
- Hierarquia: Registradores → Cache L1 → L2 → L3 → RAM → Disco

---

## 🏗️ Estruturas de Sistemas Operacionais

### 1. Kernel Monolítico

```
┌─────────────────────────────────────┐
│           MODO KERNEL               │
│  ┌─────────────────────────────┐    │
│  │    Todo o SO num bloco      │    │
│  │  (drivers, sistema de arq,  │    │
│  │   gerência de memória...)   │    │
│  └─────────────────────────────┘    │
└─────────────────────────────────────┘
```

| Vantagens | Desvantagens |
|-----------|--------------|
| Alto desempenho | Baixo isolamento |
| Comunicação direta | Falha pode derrubar tudo |

**Exemplos:** Linux, Android

---

### 2. Microkernel

```
┌─────────────────────────────────────┐
│          MODO USUÁRIO               │
│  ┌───────┐ ┌───────┐ ┌───────┐     │
│  │Driver │ │Sistema│ │ Rede  │     │
│  │       │ │Arquiv.│ │       │     │
│  └───────┘ └───────┘ └───────┘     │
└─────────────────────────────────────┘
          ↕ IPC ↕ IPC ↕
┌─────────────────────────────────────┐
│           MODO KERNEL               │
│  ┌─────────────────────────────┐    │
│  │     Kernel Mínimo           │    │
│  │  (apenas o essencial)       │    │
│  └─────────────────────────────┘    │
└─────────────────────────────────────┘
```

| Vantagens | Desvantagens |
|-----------|--------------|
| Alto isolamento | Menor desempenho |
| Falha de serviço não derruba tudo | Comunicação via IPC (mais lenta) |

**Exemplos:** MINIX, QNX, FreeRTOS (Arduino), dispositivos IoT

---

### 3. Kernel Híbrido

Combina o **desempenho do monolítico** com a **modularidade do microkernel**.

**Exemplos:** Windows, macOS

---

### Comparativo

| Característica | Monolítico | Microkernel | Híbrido |
|----------------|------------|-------------|---------|
| Desempenho | Alto | Médio | Alto |
| Isolamento | Baixo | Alto | Médio |
| Complexidade | Média | Alta | Alta |
| Exemplos | Linux | MINIX, QNX | Windows, macOS |

---

## 📖 Glossário

| Termo | Significado |
|-------|-------------|
| **SO** | Sistema Operacional |
| **Kernel** | Núcleo do SO, parte que roda em modo privilegiado |
| **Batch** | Processamento em lote, execução sequencial de jobs |
| **Time-Sharing** | Compartilhamento de tempo da CPU entre usuários |
| **Multiprogramação** | Vários programas na memória ao mesmo tempo |
| **POSIX** | Padrão de interface para sistemas operacionais Unix-like |
| **IPC** | Inter-Process Communication (comunicação entre processos) |
| **ASCII** | Padrão de codificação de caracteres (1960) |
| **System Call** | Chamada de sistema, solicitação de serviço ao SO |
| **Assembly** | Linguagem de programação de baixo nível |

---

## 🎬 Para Aprofundar

| Recurso | Link/Descrição |
|---------|----------------|
| **Livro** | Sistemas Operacionais Modernos, 5ª Ed. - Tanenbaum e Bos (2022) |
| **Vídeo** | [O que é Sistema Operacional](https://www.youtube.com/watch?v=B9VWL3gXBaI) - Diolinux |
| **Vídeo** | [História dos Computadores](https://www.youtube.com/watch?v=HI9OVS5XKGI) - Fabio Akita |
| **Vídeo** | [Como funciona o Linux](https://www.youtube.com/watch?v=K05cyftMvxI) - Akitando |

---

## ✅ Perguntas para Fixação

Responda as perguntas abaixo para consolidar o aprendizado:

!!! question "1. Máquina Estendida"
    Explique com suas palavras o que significa dizer que o SO é uma "máquina estendida". Dê um exemplo prático de abstração que o SO oferece.

!!! question "2. Evolução Histórica"
    Por que os Sistemas Operacionais surgiram? Qual era o principal problema da era pré-SO (1940-1955) que motivou a criação do Monitor Residente?

!!! question "3. Multiprogramação"
    Qual a diferença entre processamento em lote (batch) e multiprogramação? Por que a multiprogramação foi uma evolução importante?

!!! question "4. Arquiteturas de Kernel"
    Compare o Kernel Monolítico e o Microkernel. Em qual situação você usaria cada um? (Dica: pense em desempenho vs. segurança/isolamento)

---

## 🔜 Próxima Aula

**Conceitos Fundamentais de SO:**

- Processos (estado, registradores, execução)
- Threads (compartilhamento de memória, paralelismo)
- Concorrência (múltiplos processos disputando recursos)
- Deadlock (recursos bloqueados aguardando outros recursos)
