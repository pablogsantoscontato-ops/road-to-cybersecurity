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

### IP Privado

São endereços utilizados dentro de redes internas.

Eles não são roteáveis diretamente pela Internet.

Principais faixas:

```text
10.0.0.0/8
172.16.0.0/12
192.168.0.0/16
```

Exemplo:

```text
192.168.1.50
```

---

### IP Público

São endereços utilizados na Internet e fornecidos por provedores de acesso (ISP).

Exemplo:

```text
200.100.50.20
```

---

## 🔢 Classes IPv4

As classes IPv4 são uma forma histórica de organizar endereços IP.

Atualmente, o modelo CIDR é mais utilizado, porém as classes ainda ajudam na compreensão dos fundamentos.

| Classe | Primeiro Octeto | Uso |
|--------|-----------------|-----|
| A | 1 - 126 | Redes grandes |
| B | 128 - 191 | Redes médias |
| C | 192 - 223 | Redes pequenas |
| D | 224 - 239 | Multicast |
| E | 240 - 255 | Reservada |

> Observação: O endereçamento por classes é um conceito histórico. Atualmente, redes utilizam principalmente CIDR (Classless Inter-Domain Routing) para definir tamanhos de redes.

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

Usado para testar a comunicação do próprio computador.

Exemplo:

```text
127.0.0.1
```

---

### APIPA

Endereço atribuído automaticamente quando o dispositivo não consegue obter uma configuração através do DHCP.

Faixa:

```text
169.254.0.0/16
```

Exemplo:

```text
169.254.10.20
```

Normalmente indica um problema na comunicação com o servidor DHCP.

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

* Sistemas de Informação
* Redes e Cibersegurança

---

<div align="center">

[![GitHub](https://img.shields.io/badge/Voltar_ao_Perfil-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/pablogsantoscontato-ops)

---

<sub>Documentação sobre Gateway, DHCP, NAT e IPv4</sub>

</div>
