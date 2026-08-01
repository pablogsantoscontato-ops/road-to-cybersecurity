<div align="center">

# 🔎 ARP (Address Resolution Protocol)

### Resolução de endereços IPv4 para MAC

[![Typing SVG](https://readme-typing-svg.demolab.com?font=Fira+Code&weight=600&size=22&duration=3000&pause=500&color=00FFAA&center=true&vCenter=true&width=435&lines=ARP;Address+Resolution+Protocol;IP+para+MAC;Resolu%C3%A7%C3%A3o+de+endere%C3%A7os)](https://git.io/typing-svg)

---

</div>

Este documento apresenta o funcionamento do **ARP (Address Resolution Protocol)**, utilizado em redes IPv4 para realizar a associação entre endereços IP e endereços MAC.

---

## 📌 IP e MAC

Para que uma comunicação aconteça em uma rede Ethernet, dois endereços são importantes:

### Endereço IP

O IP é um endereço lógico utilizado para identificar dispositivos na rede.

Ele atua na Camada 3 (Rede) e permite que os pacotes encontrem o destino.

Exemplo:

```text
IP: 192.168.1.10
```

---

### Endereço MAC

O MAC é o endereço físico da placa de rede (NIC).

Ele atua na Camada 2 (Enlace) e é usado para entregar quadros dentro da rede local.

Exemplo:

```text
MAC: AA-AA-AA-AA-AA-AA
```

---

## ❓ Qual problema o ARP resolve?

Quando um dispositivo quer enviar dados, ele normalmente conhece o IP do destino, mas precisa do endereço MAC para criar o quadro Ethernet.

Exemplo:

PC1 quer enviar para:

```text
IP destino: 192.168.1.20
```

Mas não sabe:

```text
MAC destino: ???
```

O ARP resolve essa associação:

```text
IP → MAC
```

---

## 🔄 Funcionamento do ARP

O processo acontece em três etapas:

### 1. ARP Request

O dispositivo envia uma solicitação em broadcast:

```text
MAC destino: FF:FF:FF:FF:FF:FF
```

Mensagem:

> "Quem possui o IP 192.168.1.20?"

Como é broadcast, todos os dispositivos da rede local recebem.

---

### 2. ARP Reply

O dispositivo que possui aquele IP responde:

```text
IP: 192.168.1.20
MAC: BB-BB-BB-BB-BB-BB
```

Resposta:

> "Esse IP pertence a mim, meu MAC é BB-BB-BB."

---

### 3. Tabela ARP

O dispositivo salva essa informação:

```text
IP              MAC
192.168.1.20 → BB-BB-BB-BB-BB-BB
```

Assim, ele não precisa fazer outro broadcast para esse destino.

---

## 🔀 Papel do Switch

O switch trabalha na Camada 2 e encaminha quadros utilizando endereços MAC.

Quando recebe um ARP Request:

```text
FF:FF:FF:FF:FF:FF
```

Ele entende como broadcast e envia para todas as portas da rede local.

Quando recebe a resposta ARP, encaminha como unicast para o MAC correto.

---

## 🌐 ARP e redes remotas

O ARP funciona apenas dentro da rede local.

Quando o destino está em outra rede, o computador não procura o MAC do destino final.

Ele procura o MAC do gateway padrão.

Exemplo:

```text
PC1
192.168.1.10
    ↓
Roteador
192.168.1.1
    ↓
Servidor
10.0.0.10
```

O PC1 percebe que o servidor está em outra rede.

Então ele faz:

```text
ARP Request:
Quem possui 192.168.1.1?
```

O roteador responde com seu MAC.

---

## 🔁 IP permanece e MAC muda

Durante uma comunicação entre redes:

O IP continua:

```text
Origem: 192.168.1.10
Destino: 10.0.0.10
```

Mas o MAC muda a cada salto:

```text
PC1 → Roteador
MAC: AA-AA-AA → CC-CC-CC
```

Depois:

```text
Roteador → Próximo salto
MAC: DD-DD-DD → EE-EE-EE
```

O IP identifica o destino final.

O MAC identifica o próximo dispositivo dentro daquele enlace.

---

## 📋 Resumo

- ARP associa um endereço IPv4 a um endereço MAC
- O ARP usa broadcast para descobrir o MAC dentro da rede local
- O dispositivo responde com ARP Reply
- A informação é armazenada na tabela ARP
- O switch encaminha os broadcasts dentro do domínio de broadcast
- Para redes remotas, o ARP descobre o MAC do gateway padrão
- No IPv6, o equivalente é o Neighbor Discovery (ND)

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
