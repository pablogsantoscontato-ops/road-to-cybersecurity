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

## 📡 ARP e Broadcast

O ARP utiliza broadcast porque inicialmente o dispositivo não sabe quem possui determinado endereço IP.

O endereço MAC de broadcast é:

```text
FF:FF:FF:FF:FF:FF
```

Quando um switch recebe um quadro broadcast, ele encaminha para todos os dispositivos da mesma rede local.

Por isso, o ARP funciona apenas dentro do mesmo domínio de broadcast.

---

## 🚪 ARP e Gateway Padrão

O ARP é utilizado apenas para descobrir dispositivos dentro da mesma rede local.

Quando o destino está em uma rede diferente, o dispositivo não procura o MAC do destino final.

Ele procura o MAC do **gateway padrão** (roteador).

Exemplo:

```text
PC1
IP: 192.168.1.10

Servidor remoto:
IP: 10.0.0.10
```

Como estão em redes diferentes, o PC1 envia o quadro para o roteador:

```text
MAC origem: MAC do PC1
MAC destino: MAC do roteador
```

O pacote IP continua tendo como destino:

```text
10.0.0.10
```

O roteador então encaminha o pacote até a rede de destino.

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

## 📋 Resumo

- O **ARP** descobre o MAC de um dispositivo através do seu endereço IP.
- O ARP utiliza **broadcast** para encontrar o dispositivo correto.
- O switch encaminha broadcasts dentro da rede local.
- A resposta ARP cria uma entrada na tabela ARP.
- O ARP funciona para IPv4.
- No IPv6, o processo equivalente é o **Neighbor Discovery (ND)**.
- Quando o destino está em outra rede, o ARP descobre o MAC do gateway padrão, não do destino final.

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
