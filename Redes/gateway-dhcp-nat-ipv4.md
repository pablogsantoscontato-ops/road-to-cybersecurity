<div align="center">

# 🌐 Gateway, DHCP, NAT e IPv4

### Conceitos fundamentais de Redes de Computadores

[![Typing SVG](https://readme-typing-svg.demolab.com?font=Fira+Code&weight=600&size=22&duration=3000&pause=500&color=00FFAA&center=true&vCenter=true&width=435&lines=Gateway%2C+DHCP%2C+NAT+e+IPv4;Fundamentos+de+redes;Comunica%C3%A7%C3%A3o+entre+redes;IPv4)](https://git.io/typing-svg)

---

</div>

Este documento apresenta conceitos fundamentais de Redes de Computadores, abordando como dispositivos recebem configurações de rede, como se comunicam com outras redes e como acessam a Internet.

---

## 🚪 Gateway Padrão (Default Gateway)

O Gateway Padrão é o dispositivo responsável por permitir que um equipamento saia da sua rede local e se comunique com outras redes.

Normalmente, o gateway é a interface do roteador conectada à rede local.

Exemplo:

Computador:
IP: 192.168.1.10

Gateway:
192.168.1.1

Quando o computador deseja acessar um servidor fora da rede local, ele envia o tráfego para o gateway.

---

## 🌐 Roteadores como Gateways

O roteador conecta diferentes redes e encaminha pacotes entre elas.

Cada interface do roteador pertence a uma rede diferente e possui um endereço IP próprio.

Exemplo:

Rede Local:
192.168.1.0/24
    |
    |
Roteador
    |
    |
Internet

O roteador funciona como o caminho entre a rede interna e outras redes.

---

## 🔒 Roteador como Limite entre Redes

O roteador cria uma separação entre:

- Rede interna (LAN)
- Rede externa (Internet)

A rede interna utiliza geralmente endereços privados, enquanto a Internet utiliza endereços públicos.

Exemplo:

Rede Interna

192.168.1.10
192.168.1.20
192.168.1.30
    |
    |
Roteador
    |
    |
Internet

IP Público
200.100.50.20

---

## 📡 DHCP (Dynamic Host Configuration Protocol)

O DHCP é um protocolo responsável por configurar automaticamente dispositivos em uma rede.

Ele fornece:

- Endereço IP
- Máscara de sub-rede
- Gateway padrão
- Servidor DNS

Exemplo:

IP: 192.168.1.15
Máscara: 255.255.255.0
Gateway: 192.168.1.1
DNS: 8.8.8.8

Sem DHCP, cada dispositivo precisaria ser configurado manualmente.

---

## 🔄 Processo DORA do DHCP

O DHCP utiliza quatro etapas para entregar uma configuração de rede.

### 1. Discover

O dispositivo procura um servidor DHCP disponível.

Cliente:
"Existe algum servidor DHCP?"

---

### 2. Offer

O servidor responde oferecendo uma configuração.

Servidor:
"Você pode usar o IP 192.168.1.15"

---

### 3. Request

O dispositivo aceita a oferta.

Cliente:
"Aceito esse endereço IP"

---

### 4. Acknowledge

O servidor confirma a configuração.

Servidor:
"Configuração aplicada com sucesso"

---

## 🔄 NAT (Network Address Translation)

O NAT é responsável por traduzir endereços IP privados em endereços IP públicos.

Ele permite que vários dispositivos de uma rede interna utilizem um único IP público para acessar a Internet.

Exemplo:

Antes do NAT:

IP Privado: 192.168.1.10

Depois do NAT:

IP Público: 200.100.50.20

O roteador mantém uma tabela NAT para saber qual dispositivo realizou cada conexão.

---

## 🌍 Endereços IP Privados e Públicos

### IP Privado

São endereços utilizados dentro de redes internas.

Eles não são roteáveis diretamente na Internet.

Principais faixas:

10.0.0.0/8
172.16.0.0/12
192.168.0.0/16

Exemplo:

192.168.1.50

---

### IP Público

São endereços utilizados na Internet e fornecidos pelo ISP.

Exemplo:

200.100.50.20

---

## 🔢 Classes IPv4

As classes IPv4 são uma forma histórica de organizar endereços IP.

Atualmente, o modelo CIDR é mais utilizado.

| Classe | Primeiro Octeto | Uso |
|--------|-----------------|-----|
| A | 1 - 126 | Redes grandes |
| B | 128 - 191 | Redes médias |
| C | 192 - 223 | Redes pequenas |
| D | 224 - 239 | Multicast |
| E | 240 - 255 | Reservada |

---

## 📌 Faixas IPv4 Importantes

| Endereço | Função |
|----------|--------|
| 10.0.0.0/8 | Rede privada |
| 172.16.0.0/12 | Rede privada |
| 192.168.0.0/16 | Rede privada |
| 127.0.0.1 | Loopback |
| 169.254.0.0/16 | APIPA |

---

## 🔁 Outros Endereços Importantes

### Loopback

Usado para comunicação do próprio computador.

Exemplo:

127.0.0.1

---

### APIPA

Endereço atribuído automaticamente quando o dispositivo não consegue obter IP através do DHCP.

Faixa:

169.254.0.0/16

Exemplo:

169.254.10.20

Normalmente indica falha na comunicação com o servidor DHCP.

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

## 👨‍💻 Autor

**Pablo Gonçalves Santos**

* Sistemas da Informação
* Redes e Cibersegurança

---

<div align="center">

[![GitHub](https://img.shields.io/badge/Voltar_ao_Perfil-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/pablogsantoscontato-ops)

---

<sub>Documentação sobre Gateway, DHCP, NAT e IPv4</sub>

</div>
