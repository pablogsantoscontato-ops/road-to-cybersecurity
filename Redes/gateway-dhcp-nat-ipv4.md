<div align="center">

# 🌐 Gateway, DHCP, NAT e IPv4

### Conceitos fundamentais de Redes de Computadores

[![Typing SVG](https://readme-typing-svg.demolab.com?font=Fira+Code&weight=600&size=22&duration=3000&pause=500&color=00FFAA&center=true&vCenter=true&width=435&lines=Gateway%2C+DHCP%2C+NAT+e+IPv4;Fundamentos+de+redes;Comunica%C3%A7%C3%A3o+entre+redes;IPv4)](https://git.io/typing-svg)

---

</div>

Este documento apresenta conceitos fundamentais de Redes de Computadores, abordando como dispositivos recebem configurações de rede, como se comunicam dentro de uma rede e como acessam outras redes através de roteadores.

---

## 🚪 Gateway Padrão (Default Gateway)

O Gateway Padrão é o endereço IP da interface do roteador responsável por encaminhar o tráfego da rede local para outras redes.

Quando um dispositivo precisa acessar um destino que não pertence à sua rede local, ele envia os pacotes para o gateway.

Exemplo:

```text
Computador:
IP: 192.168.1.10

Gateway:
192.168.1.1
```

Nesse exemplo, o roteador com endereço `192.168.1.1` funciona como a saída da rede local.

---

## 🌐 Roteadores como Gateways

O roteador é responsável por conectar diferentes redes e encaminhar pacotes entre elas.

Cada interface do roteador pertence a uma rede diferente e possui seu próprio endereço IP.

Exemplo:

```text
Rede Local
192.168.1.0/24
    |
    |
    v
Roteador
Gateway: 192.168.1.1
    |
    |
    v
Outra Rede
```

O roteador permite a comunicação entre redes que possuem endereçamentos diferentes.

---

## 🔒 Roteador como Limite entre Redes

O roteador cria uma separação entre:

- Rede interna (LAN)
- Rede externa (Internet)

A rede interna normalmente utiliza endereços privados, enquanto a rede externa utiliza endereços públicos.

Exemplo:

```text
Rede Interna

192.168.1.10
192.168.1.20
192.168.1.30
    |
    |
    v
Roteador
    |
    |
    v
Internet

IP Público:
200.100.50.20
```

O roteador controla a comunicação entre esses dois ambientes.

---

## 📡 DHCP (Dynamic Host Configuration Protocol)

O DHCP é um protocolo responsável por configurar automaticamente dispositivos dentro de uma rede.

Ele fornece:

- Endereço IP
- Máscara de sub-rede
- Gateway padrão
- Outras configurações de rede

Exemplo:

```text
IP: 192.168.1.15
Máscara: 255.255.255.0
Gateway: 192.168.1.1
```

Sem DHCP, cada dispositivo precisaria receber essas informações manualmente.

---

## 🔄 Processo DORA do DHCP

O DHCP funciona através de quatro etapas:

### 1. Discover

O dispositivo procura um servidor DHCP disponível.

```text
Cliente:
"Existe algum servidor DHCP?"
```

---

### 2. Offer

O servidor oferece uma configuração de rede.

```text
Servidor:
"Você pode utilizar o IP 192.168.1.15"
```

---

### 3. Request

O dispositivo aceita a configuração oferecida.

```text
Cliente:
"Aceito esse endereço IP"
```

---

### 4. Acknowledge

O servidor confirma a atribuição.

```text
Servidor:
"Configuração aplicada com sucesso"
```

---

## 🔄 NAT (Network Address Translation)

O NAT é uma técnica utilizada pelo roteador para traduzir endereços IP privados em um ou mais endereços IP públicos, permitindo comunicação com a Internet.

Ele permite que vários dispositivos de uma rede interna acessem a Internet utilizando um único endereço público.

Exemplo:

Antes do NAT:

```text
IP Privado: 192.168.1.10
```

Depois do NAT:

```text
IP Público: 200.100.50.20
```

O roteador mantém uma tabela NAT para identificar quais dispositivos realizaram cada conexão.

---

## 🌍 Endereços IP Privados e Públicos

### 🔒 Faixas de IP Privado (RFC 1918)

São endereços usados **apenas em redes internas** e **não são roteáveis na Internet**.

| Faixa | Classe | Uso comum |
|-------|--------|-----------|
| 10.0.0.0 – 10.255.255.255 | A | Grandes empresas |
| 172.16.0.0 – 172.31.255.255 | B | Redes corporativas |
| 192.168.0.0 – 192.168.255.255 | C | Redes domésticas e pequenas empresas |

Exemplos:

```text
10.20.30.40 → Rede corporativa
172.16.5.10 → Rede empresarial
192.168.1.50 → Rede doméstica
```

---

### 🌍 Faixas de IP Público

Os endereços públicos são **roteáveis na Internet** e são atribuídos por um ISP ou um registro regional (RIR).

Como as faixas privadas ocupam apenas uma pequena parte do espaço IPv4, os endereços públicos correspondem às demais faixas **válidas**, excluindo também os intervalos reservados (como loopback, APIPA, multicast etc.).

| Faixa | Observação |
|-------|------------|
| 1.0.0.0 – 9.255.255.255 | Público |
| 11.0.0.0 – 126.255.255.255 | Público |
| 128.0.0.0 – 172.15.255.255 | Público |
| 172.32.0.0 – 191.255.255.255 | Público |
| 192.0.0.0 – 192.167.255.255 | Público |
| 192.169.0.0 – 223.255.255.255 | Público |

> **Observação:** Dentro dessas faixas ainda existem alguns blocos reservados para finalidades específicas (como `127.0.0.0/8` para loopback, `169.254.0.0/16` para APIPA e `224.0.0.0/4` para multicast). Na prática, qualquer endereço que **não pertença a uma faixa privada ou reservada** pode ser um endereço IP público.

---

## 🔢 Classes IPv4

As classes IPv4 são uma forma histórica de organizar endereços IP.

Atualmente, o modelo CIDR é mais utilizado, porém as classes ainda ajudam na compreensão dos fundamentos.

| Classe | Primeiro Octeto | Uso |
|--------|-----------------|-----|
| A | 1 - 126 | Redes muito grandes |
| B | 128 - 191 | Redes médias |
| C | 192 - 223 | Redes pequenas |
| D | 224 - 239 | Multicast |
| E | 240 - 255 | Reservada |

> Observação: O endereçamento por classes é um conceito histórico. Atualmente, redes utilizam principalmente CIDR (Classless Inter-Domain Routing) para definir tamanhos de redes.

---

## 📍 Intervalos de Endereços IPv4

Os endereços IPv4 possuem faixas que indicam sua classificação e finalidade.

| Faixa de IP | Classificação | Uso |
|-------------|---------------|-----|
| 1.0.0.0 - 126.255.255.255 | Classe A | Redes muito grandes |
| 128.0.0.0 - 191.255.255.255 | Classe B | Redes médias |
| 192.0.0.0 - 223.255.255.255 | Classe C | Redes pequenas |
| 224.0.0.0 - 239.255.255.255 | Classe D | Multicast |
| 240.0.0.0 - 255.255.255.255 | Classe E | Reservada |

---

## 🔁 Endereços Especiais

| Faixa | Função |
|-------|--------|
| 127.0.0.0 - 127.255.255.255 | Loopback |
| 169.254.0.0 - 169.254.255.255 | APIPA (falha no DHCP) |

Exemplos:

```text
127.0.0.1 → Próprio computador
169.254.10.20 → IP automático quando DHCP falha
```

---

## 🎯 Importância em Redes e Cibersegurança

Dominar esses conceitos é essencial para áreas como:

- Redes de Computadores
- Cibersegurança
- Administração de Sistemas
- SOC (Security Operations Center)
- Blue Team

Esses conhecimentos são utilizados em:

- Configuração de redes
- Análise de tráfego
- Monitoramento de segurança
- Investigação de logs
- Solução de problemas de conectividade

---

## 📚 Conceitos aprendidos

| Conceito | Descrição |
|----------|-----------|
| **Gateway Padrão** | Endereço IP do roteador utilizado como saída da rede local para acessar outras redes. |
| **Roteador** | Dispositivo de Camada 3 responsável por conectar redes diferentes e encaminhar pacotes. |
| **LAN** | Rede local onde dispositivos se comunicam dentro de uma mesma organização ou ambiente. |
| **DHCP** | Protocolo que configura automaticamente dispositivos de rede, fornecendo IP, máscara, gateway e outras informações. |
| **DORA** | Processo de funcionamento do DHCP dividido em Discover, Offer, Request e Acknowledge. |
| **NAT** | Técnica que traduz endereços IP privados em públicos, permitindo que dispositivos internos acessem a Internet. |
| **IP Privado** | Endereço utilizado dentro de redes internas e que não é roteável diretamente na Internet. |
| **IP Público** | Endereço utilizado para comunicação na Internet, normalmente fornecido por um ISP. |
| **IPv4** | Protocolo de endereçamento que utiliza endereços de 32 bits para identificar dispositivos em redes. |
| **Classes IPv4** | Modelo histórico de organização dos endereços IP em classes A, B, C, D e E. |
| **CIDR** | Método moderno de divisão de redes IP baseado em prefixos, substituindo o modelo de classes. |
| **Endereços Especiais IPv4** | Faixas reservadas para funções específicas, como loopback e APIPA. |
| **APIPA** | Endereço automático atribuído quando um dispositivo não consegue comunicação com um servidor DHCP. |
| **Comunicação entre redes** | Processo em que dispositivos utilizam roteadores e gateways para acessar redes externas. |
| **Segurança de Redes** | Conhecimento fundamental para análise de tráfego, monitoramento, logs e atuação em Blue Team. |

---

## 👨‍💻 Autor

**Pablo Gonçalves Santos**

* Sistemas de Informação
* Redes e Cibersegurança

---

<div align="center">

[![GitHub](https://img.shields.io/badge/Voltar_ao_Perfil-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/pablogsantoscontato-ops)

---

<sub>Documentação sobre Gateway, DHCP, NAT e IPv4</sub>

</div>
