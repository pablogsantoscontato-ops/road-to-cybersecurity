# 🌐 Guia Completo de CIDR e Subnetting

> Um guia simples e prático para entender CIDR, máscaras de sub-rede e subnetting.

Este repositório foi criado para ajudar estudantes de Redes, Infraestrutura e Cibersegurança a compreender um dos assuntos mais importantes da área: **Subnetting**.

---

## 📌 O que é CIDR?

CIDR (*Classless Inter-Domain Routing*) é a forma moderna de representar máscaras de sub-rede.

Exemplo:

```bash id="1lbdpf"
192.168.1.0/24
```

O número após a barra (`/`) indica quantos bits pertencem à rede.

Mas, para simplificar:

> Quanto maior o número após a barra, menor será a quantidade de dispositivos que cabem na rede.

---

## 🍕 A Analogia da Pizza

Imagine que uma rede `/24` é uma pizza inteira.

```text id="9tvtqv"
/24 -> Pizza inteira
```

Agora vamos dividir essa pizza:

```text id="c3wg0z"
/25 -> 2 pedaços
/26 -> 4 pedaços
/27 -> 8 pedaços
/28 -> 16 pedaços
```

Quanto mais você divide a pizza, menos pessoas conseguem comer em cada pedaço.

O mesmo acontece com as redes:

> Quanto maior o CIDR, menor a quantidade de hosts disponíveis.

---

## 📚 Tabela para Decorar

| CIDR | Máscara         | Hosts Disponíveis |
| ---- | --------------- | ----------------: |
| /24  | 255.255.255.0   |               254 |
| /25  | 255.255.255.128 |               126 |
| /26  | 255.255.255.192 |                62 |
| /27  | 255.255.255.224 |                30 |
| /28  | 255.255.255.240 |                14 |
| /29  | 255.255.255.248 |                 6 |
| /30  | 255.255.255.252 |                 2 |

> Dica: essa tabela aparece em cursos da Cisco, entrevistas e certificações.

---

## 🔎 Exemplo: Rede /24

```bash id="5qb6k0"
192.168.1.0/24
```

Resultado:

```text id="5mkx9k"
Rede:      192.168.1.0
Hosts:     192.168.1.1 - 192.168.1.254
Broadcast: 192.168.1.255
```

Essa rede suporta:

* 254 dispositivos.

---

## 🔎 Exemplo: Rede /25

```bash id="25v6na"
192.168.1.0/25
```

Agora dividimos a rede em duas partes.

### Primeira sub-rede

```text id="v65h2r"
Rede:      192.168.1.0
Hosts:     192.168.1.1 - 192.168.1.126
Broadcast: 192.168.1.127
```

### Segunda sub-rede

```text id="1j1xev"
Rede:      192.168.1.128
Hosts:     192.168.1.129 - 192.168.1.254
Broadcast: 192.168.1.255
```

Cada rede possui:

* 126 hosts.

---

## 🔎 Exemplo: Rede /26

```bash id="pyg6wk"
192.168.1.0/26
```

Sub-redes criadas:

```text id="7a4jbh"
192.168.1.0
192.168.1.64
192.168.1.128
192.168.1.192
```

Cada uma suporta:

* 62 hosts.

---

## 🏢 Exemplo do Mundo Real

Imagine uma empresa com:

| Departamento | Quantidade de Dispositivos |
| ------------ | -------------------------: |
| TI           |                         50 |
| RH           |                         20 |
| Financeiro   |                         15 |

Uma possível solução seria:

```text id="sif4b1"
TI          -> /26
RH          -> /27
Financeiro  -> /27
```

Benefícios:

* Melhor organização.
* Menos desperdício de IPs.
* Mais segurança.
* Fácil gerenciamento.

---

## 🎯 O que preciso decorar?

* `/24 = 254 hosts`
* `/25 = 126 hosts`
* `/26 = 62 hosts`
* `/27 = 30 hosts`
* `/28 = 14 hosts`
* `/29 = 6 hosts`
* `/30 = 2 hosts`

Além disso:

1. Quanto maior o CIDR, menor a rede.
2. Subnetting = dividir uma rede em redes menores.
3. Todo subnetting possui:

   * Endereço de Rede;
   * Hosts válidos;
   * Broadcast.

---

## 🚀 Próximos Assuntos

* [ ] IPv6
* [ ] TCP/IP
* [ ] Modelo OSI
* [ ] VLANs
* [ ] ACLs
* [ ] DHCP
* [ ] DNS
* [ ] Switching
* [ ] Roteamento
* [ ] Linux para Redes
* [ ] Wireshark
* [ ] Firewall
* [ ] Active Directory

---

## 👨‍💻 Autor

**Pablo Gonçalves Santos**

* Estudante de Sistemas da Informação
* Entusiasta de Redes e Cibersegurança

> "Aprender Redes é aprender como a Internet realmente funciona."
