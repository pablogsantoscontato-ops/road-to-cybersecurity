<div align="center">

# 🔎 ARP (Address Resolution Protocol)

### Resolução de endereços em redes IPv4

[![Typing SVG](https://readme-typing-svg.demolab.com?font=Fira+Code&weight=600&size=22&duration=3000&pause=500&color=00FFAA&center=true&vCenter=true&width=435&lines=ARP;Address+Resolution+Protocol;IP+para+MAC;Resolu%C3%A7%C3%A3o+de+endere%C3%A7os)](https://git.io/typing-svg)

---

</div>

Este documento apresenta o funcionamento do **ARP (Address Resolution Protocol)**, utilizado em redes IPv4 para realizar a associação entre endereços IP e endereços MAC.

---

## 📌 Relação entre IP e MAC

Antes de entender o ARP, é importante compreender a função de cada endereço.

### Endereço IP

O endereço IP é um endereço lógico utilizado para identificar um dispositivo em uma rede.

Ele atua na **Camada 3 (Rede)** e permite que os pacotes sejam enviados entre diferentes redes.

Exemplo:

```text
PC1
IP: 192.168.1.10
```

---

### Endereço MAC

O endereço MAC é o endereço físico da placa de rede (NIC).

Ele atua na **Camada 2 (Enlace)** e é utilizado para entregar quadros dentro de uma rede local.

Normalmente o endereço MAC é associado à placa de rede e permanece o mesmo, porém pode ser alterado por software (MAC spoofing).

Exemplo:

```text
MAC:
AA-AA-AA-AA-AA-AA
```

Em uma comunicação Ethernet, o dispositivo precisa do MAC de destino para criar o quadro que será enviado pela rede.

---

## ❓ O problema que o ARP resolve

Imagine que o PC1 quer enviar dados para outro computador:

```text
PC1
IP: 192.168.1.10

Destino:
IP: 192.168.1.20
```

O PC1 sabe o endereço IP do destino, mas não sabe o MAC.

Ele precisa descobrir:

```text
Qual dispositivo possui o IP 192.168.1.20?
Qual é o endereço MAC dele?
```

Para resolver isso, ele utiliza o ARP.

---

## 🔄 Funcionamento do ARP

O ARP funciona basicamente em três etapas.

### 1. ARP Request (Solicitação)

Primeiro, o dispositivo verifica sua tabela ARP para saber se já possui aquele endereço.

Caso não encontre, ele envia uma solicitação ARP em broadcast.

Exemplo:

```text
MAC destino:
FF:FF:FF:FF:FF:FF
```

A mensagem é:

> "Quem possui o endereço IP 192.168.1.20? Informe seu endereço MAC."

Como é um broadcast, todos os dispositivos da rede local recebem essa mensagem.

---

### 2. ARP Reply (Resposta)

O dispositivo que possui aquele endereço IP responde diretamente.

Exemplo:

```text
IP: 192.168.1.20
MAC: BB-BB-BB-BB-BB-BB
```

A resposta informa:

> "O IP 192.168.1.20 pertence ao MAC BB-BB-BB-BB-BB-BB."

---

### 3. Armazenamento na tabela ARP

Após receber a resposta, o dispositivo salva essa informação:

```text
Tabela ARP:

IP                  MAC
192.168.1.20   →    BB-BB-BB-BB-BB-BB
```

Agora, quando precisar enviar novamente para esse destino, não será necessário realizar outro broadcast.

---

## 🔄 Funcionamento visual do ARP

O ARP acontece quando um dispositivo conhece o endereço IP de destino, mas ainda não sabe qual é o endereço MAC correspondente.

### Cenário inicial

Dois dispositivos estão na mesma rede local:

```text
PC1                              PC2

IP: 192.168.1.10                 IP: 192.168.1.20
MAC: AA-AA-AA                    MAC: BB-BB-BB
          |
          |
      +-------+
      | SWITCH|
      +-------+
```

O PC1 deseja enviar dados para o PC2, mas ele possui apenas o IP:

```text
Destino:
IP: 192.168.1.20
MAC: ???
```

---

### 1️⃣ ARP Request (Solicitação)

O PC1 envia um broadcast perguntando:

```text
Quem possui o IP 192.168.1.20?
Informe seu endereço MAC.
```

O quadro Ethernet é enviado para todos:

```text
MAC destino:
FF:FF:FF:FF:FF:FF
```

Fluxo:

```text
      +-------+
      | SWITCH|
      +-------+
    ↙    ↓    ↘
  PC1    PC2   PC3
  ARP    ARP   ARP
Request Request Request
```

Todos recebem, mas apenas o dispositivo correto responde.

---

### 2️⃣ ARP Reply (Resposta)

O PC2 reconhece que aquele IP pertence a ele.

Então responde:

```text
192.168.1.20 pertence a mim.
Meu MAC é: BB-BB-BB
```

Comunicação:

```text
PC2 ─────────► PC1
IP: 192.168.1.20
MAC: BB-BB-BB
```

---

### 3️⃣ Tabela ARP

Após receber a resposta, o PC1 armazena a informação:

```text
Tabela ARP

IP                  MAC
192.168.1.20  →  BB-BB-BB
```

Agora ele já sabe como enviar os próximos quadros.

---

## 🔀 Papel do Switch no ARP

O switch opera na Camada 2 e não entende endereços IP. Ele apenas analisa endereços MAC.

Quando recebe um ARP Request com destino:

```text
FF:FF:FF:FF:FF:FF
```

ele trata como broadcast e envia o quadro para todas as portas, exceto a porta de origem.

Quando recebe a resposta ARP (unicast), ele encaminha diretamente para o MAC aprendido.

---

## 📡 ARP em uma rede remota

O ARP nunca é usado para descobrir o MAC de um dispositivo que está em outra rede. Ele só funciona dentro da rede local.

Quando o destino está em outra rede, o ARP funciona de forma diferente.

Exemplo:

```text
PC1                         Servidor
192.168.1.10                10.0.0.10
    |
    |
Roteador
192.168.1.1
```

O PC1 percebe:

```text
192.168.1.10 e 10.0.0.10 não pertencem à mesma rede.
```

Então ele NÃO procura o MAC do servidor.

Ele procura o MAC do gateway:

```text
ARP Request:
Quem possui 192.168.1.1?
```

Resposta:

```text
192.168.1.1
MAC: CC-CC-CC
```

Depois:

```text
PC1 → Roteador → Servidor
```

---

## 🔁 O que muda e o que permanece

Durante uma comunicação entre redes:

### IP (permanece)

```text
Origem: 192.168.1.10
Destino: 10.0.0.10
```

O IP identifica o destino final.

---

### MAC (muda)

O endereço MAC possui importância apenas dentro do enlace atual.

Cada roteador remove o quadro Ethernet recebido e cria um novo quadro para o próximo salto.

Por isso:

- O IP permanece apontando para o destino final.
- O MAC muda a cada rede percorrida.

Primeiro salto:

```text
PC1 → Roteador
MAC: AA-AA-AA → CC-CC-CC
```

Segundo salto:

```text
Roteador → Próximo dispositivo
MAC: DD-DD-DD → EE-EE-EE
```

O MAC identifica apenas o próximo dispositivo no caminho.

---

## 🖥️ Exemplo 1: ARP dentro da mesma rede

Rede:

```text
192.168.1.0/24
```

PC1:

```text
IP: 192.168.1.10
MAC: AA-AA-AA
```

PC2:

```text
IP: 192.168.1.20
MAC: BB-BB-BB
```

Processo:

1. PC1 verifica a tabela ARP.
2. Não encontra o IP 192.168.1.20.
3. Envia ARP Request em broadcast.
4. PC2 responde com seu MAC.
5. PC1 salva a informação.
6. PC1 envia os dados para o MAC do PC2.

Comunicação:

```text
IP: 192.168.1.10 → 192.168.1.20
MAC: AA-AA-AA → BB-BB-BB
```

---

## 🌎 Exemplo 2: Comunicação com uma rede remota

PC1:

```text
IP: 192.168.1.10
```

Servidor:

```text
IP: 10.0.0.10
```

Como o servidor está em outra rede:

1. PC1 identifica que o destino é remoto.
2. PC1 não faz ARP para o servidor.
3. PC1 faz ARP para descobrir o MAC do roteador.
4. Envia o quadro para o gateway padrão.
5. O roteador encaminha o pacote para o destino.

Nesse caso:

O IP permanece:

```text
192.168.1.10 → 10.0.0.10
```

Mas o MAC muda em cada etapa:

```text
PC1 → Roteador → Próximo salto → Destino
```

---

## 🔎 Visualizando a tabela ARP

Os sistemas armazenam temporariamente as associações IP → MAC.

No Windows:

```bash
arp -a
```

Exemplo:

```text
Interface: 192.168.1.10

Endereço IP        Endereço MAC
192.168.1.1        AA-BB-CC-DD-EE-FF
192.168.1.20       BB-BB-BB-BB-BB-BB
```

Essas entradas possuem tempo de expiração e são removidas caso não sejam utilizadas.

---

## 📋 Resumo visual

```text
IP conhecido
    |
    ↓
Preciso descobrir o MAC
    |
    ↓
ARP Request (Broadcast FF:FF:FF:FF:FF:FF)
    |
    ↓
Dispositivo responde (ARP Reply)
    |
    ↓
IP + MAC armazenados na tabela ARP
    |
    ↓
Comunicação normal
```

---

## 📋 Resumo

- O ARP realiza a resolução de endereço IPv4 para endereço MAC dentro de uma rede local.
- O ARP utiliza mensagens broadcast para localizar o dispositivo que possui determinado endereço IP.
- Após receber uma resposta, o dispositivo armazena a relação IP → MAC em sua tabela ARP.
- O ARP funciona apenas no mesmo domínio de broadcast.
- Para redes remotas, o dispositivo utiliza o MAC do gateway padrão, não o MAC do destino final.
- No IPv6, essa função é realizada pelo Neighbor Discovery (ND).

---

## 👨‍💻 Autor

**Pablo Gonçalves Santos**

* Sistemas de Informação
* Redes e Cibersegurança

---

<div align="center">

[![GitHub](https://img.shields.io/badge/Voltar_ao_Perfil-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/pablogsantoscontato-ops)

---

<sub>Documentação sobre ARP (Address Resolution Protocol)</sub>

</div>
