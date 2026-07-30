<div align="center">

# 🌐 Guia de CIDR, Subnetting e Máscaras de Sub-rede

### CIDR, máscaras de sub-rede e subnetting

[![Typing SVG](https://readme-typing-svg.demolab.com?font=Fira+Code&weight=600&size=22&duration=3000&pause=500&color=00FFAA&center=true&vCenter=true&width=435&lines=Subnetting;Dividindo+redes;Entendendo+CIDR;Redes)](https://git.io/typing-svg)

---

</div>

Este documento apresenta os fundamentos de **CIDR, máscaras de sub-rede e subnetting**, explicando como redes IPv4 podem ser divididas em sub-redes menores para melhorar organização, aproveitamento de endereços IP e segmentação de redes.

---

## 📌 O que é CIDR?

CIDR (*Classless Inter-Domain Routing*) é a forma moderna de representar máscaras de sub-rede.

Exemplo:

192.168.1.0/24

O número após a barra (`/`) indica quantos bits pertencem à rede.

> Quanto maior o número após a barra, menor será a quantidade de dispositivos que cabem na rede.

---

## 🔀 O que é Subnetting?

Subnetting é o processo de dividir uma rede IP maior em redes menores chamadas sub-redes.

Exemplo:

Uma rede:

192.168.1.0/24

Pode ser dividida em:

192.168.1.0/25
192.168.1.128/25

Cada nova sub-rede possui seus próprios:

* Endereço de rede
* Hosts disponíveis
* Endereço de broadcast

---

## 🍕 A Analogia da Pizza

Uma rede `/24` pode ser comparada a uma pizza inteira.

/24 -> Pizza inteira (1 rede)

Divisões possíveis:

/25 -> 2 pedaços (2 sub-redes)
/26 -> 4 pedaços (4 sub-redes)
/27 -> 8 pedaços (8 sub-redes)
/28 -> 16 pedaços (16 sub-redes)

Quanto mais divisões, menor o tamanho de cada parte.

O mesmo acontece com as redes:

> Quanto maior o CIDR, menor a quantidade de hosts disponíveis.

---

## 📚 Tabela de CIDR e Máscaras

| CIDR | Máscara | Sub-redes criadas a partir de /24 | Hosts por sub-rede |
|------|---------|----------------------------------:|-------------------:|
| /24 | 255.255.255.0 | 1 | 254 |
| /25 | 255.255.255.128 | 2 | 126 |
| /26 | 255.255.255.192 | 4 | 62 |
| /27 | 255.255.255.224 | 8 | 30 |
| /28 | 255.255.255.240 | 16 | 14 |
| /29 | 255.255.255.248 | 32 | 6 |
| /30 | 255.255.255.252 | 64 | 2 |

---

## 🔎 Exemplo: Rede /24

192.168.1.0/24

Resultado:

Rede: 192.168.1.0
Hosts: 192.168.1.1 - 192.168.1.254
Broadcast: 192.168.1.255

Essa rede possui:

* 254 dispositivos.

---

## 🔎 Exemplo: Rede /25

192.168.1.0/25

Divisão em 2 sub-redes:

### Primeira sub-rede

Rede: 192.168.1.0
Hosts: 192.168.1.1 - 192.168.1.126
Broadcast: 192.168.1.127

### Segunda sub-rede

Rede: 192.168.1.128
Hosts: 192.168.1.129 - 192.168.1.254
Broadcast: 192.168.1.255

Cada rede possui:

* 126 hosts.

---

## 🔎 Exemplo: Rede /26

192.168.1.0/26

Divisão em 4 sub-redes:

192.168.1.0
192.168.1.64
192.168.1.128
192.168.1.192

Cada uma suporta:

* 62 hosts.

---

## 🏢 Exemplo de Aplicação

Cenário com departamentos:

| Departamento | Quantidade de Dispositivos |
|--------------|---------------------------:|
| TI | 50 |
| RH | 20 |
| Financeiro | 15 |

Alocação sugerida:

TI -> /26 (62 hosts)
RH -> /27 (30 hosts)
Financeiro -> /27 (30 hosts)

Características:

* Organização
* Otimização de IPs
* Segmentação
* Gerenciamento

---

## 📋 Resumo de CIDR

| CIDR | Hosts | Sub-redes a partir de /24 |
|------|------:|---------------------------:|
| /24 | 254 | 1 |
| /25 | 126 | 2 |
| /26 | 62 | 4 |
| /27 | 30 | 8 |
| /28 | 14 | 16 |
| /29 | 6 | 32 |
| /30 | 2 | 64 |

Observações:

1. Quanto maior o CIDR, menor a rede.
2. Subnetting = divisão de uma rede em redes menores.
3. Cada subnetting possui:

   * Endereço de Rede
   * Hosts válidos
   * Broadcast

---

## 👨‍💻 Autor

**Pablo Gonçalves Santos**

* Sistemas da Informação
* Redes e Cibersegurança

---

<div align="center">

[![GitHub](https://img.shields.io/badge/Voltar_ao_Perfil-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/pablogsantoscontato-ops)

---

<sub>Documentação sobre CIDR e Subnetting</sub>

</div>
