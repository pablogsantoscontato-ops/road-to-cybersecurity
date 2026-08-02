<div align="center">

# 🌐 Roteamento entre Redes

### Comunicação entre redes e roteamento

[![Typing SVG](https://readme-typing-svg.demolab.com?font=Fira+Code&weight=600&size=22&duration=3000&pause=500&color=00FFAA&center=true&vCenter=true&width=435&lines=Roteamento+entre+redes;Comunica%C3%A7%C3%A3o+entre+redes;Roteadores+e+gateways;Redes)](https://git.io/typing-svg)

---

</div>

Este documento apresenta o processo de **roteamento entre redes**, abordando como os dados são encaminhados entre diferentes redes utilizando roteadores.

---

## 📌 Introdução

O roteamento é o processo utilizado para enviar dados entre redes diferentes. Quando um dispositivo precisa se comunicar com outro dispositivo que está em outra rede, é necessário o uso de um roteador para encontrar o melhor caminho até o destino.

Dentro de uma mesma rede local, os dispositivos conseguem se comunicar diretamente utilizando endereços MAC. Porém, quando o destino está em outra rede, o tráfego precisa passar por um roteador.

Exemplo:

Um computador de uma empresa acessa um servidor que está em outra filial. Como estão em redes diferentes, o tráfego precisa passar por roteadores.

---

## 🖥️ Comunicação na mesma rede

Quando um dispositivo envia uma mensagem para outro dispositivo da mesma rede, ele verifica se o endereço IP de destino pertence ao mesmo segmento de rede.

Caso esteja na mesma rede:

- O dispositivo utiliza ARP para descobrir o endereço MAC do destino.
- O pacote IP é encapsulado em um quadro Ethernet.
- O quadro é enviado diretamente ao dispositivo de destino através do switch.

Nesse caso, o roteador não participa da comunicação.

Exemplo:

```text
PC1
IP: 192.168.1.10
    ↓
Switch
    ↓
PC2
IP: 192.168.1.20
```

Como os dois estão na rede `192.168.1.0/24`, o PC1 usa ARP para descobrir o MAC do PC2 e envia diretamente pelo switch.

---

## 🌐 Comunicação entre redes diferentes

Quando um dispositivo precisa enviar dados para uma rede diferente, ele não consegue enviar diretamente para o destino.

Nesse caso, ele envia o quadro para o seu gateway padrão, que normalmente é um roteador.

Exemplo:

```text
Host H1
192.168.1.10
    ↓
Gateway padrão
192.168.1.1
    ↓
Host H3
192.168.2.50
```

O processo ocorre da seguinte forma:

1. O host verifica que o destino está em outra rede.
2. Envia o quadro Ethernet para o MAC do roteador.
3. O roteador recebe o pacote e remove o cabeçalho Ethernet.
4. Consulta sua tabela de roteamento para encontrar o melhor caminho.
5. Encapsula novamente o pacote em um novo quadro Ethernet.
6. Envia para a rede de destino.

Exemplo:

Um computador de casa acessando um site:

```text
Computador: 192.168.1.10
Servidor: 142.250.x.x
```

O computador envia o pacote para o roteador doméstico, que encaminha para a internet.

---

## 🔁 Endereço IP x Endereço MAC

O endereço IP é o endereço lógico do dispositivo na rede, enquanto o endereço MAC é o endereço físico da placa de rede.

Formato do endereço MAC:

```text
XX:XX:XX:XX:XX:XX
```

Exemplo:

```text
AA:BB:CC:DD:EE:FF
```

Durante a comunicação entre redes:

O endereço IP permanece o mesmo do início ao fim:

```text
Origem: 192.168.1.10
Destino: 192.168.2.50
```

Porém, os endereços MAC mudam a cada salto.

O MAC é utilizado apenas para comunicação dentro da rede local, enquanto o IP identifica a origem e o destino final.

Exemplo:

Um pacote passa por três roteadores:

```text
PC → R1 → R2 → Servidor
```

O IP do servidor continua sendo o destino, mas o MAC muda em cada ligação.

---

## 🚪 Gateway Padrão

O gateway padrão é o endereço IP da interface do roteador conectada à rede local.

Ele funciona como uma saída para outras redes.

Quando um host precisa acessar uma rede remota, ele envia o quadro para o MAC do gateway padrão.

Exemplo:

```text
Computador: 192.168.1.10
Gateway: 192.168.1.254
```

Sem um gateway padrão configurado corretamente, o dispositivo consegue se comunicar apenas dentro da própria rede local.

---

## 📋 Tabela de Roteamento

Os roteadores utilizam tabelas de roteamento para decidir para onde encaminhar os pacotes.

A tabela contém:

- Redes de destino.
- Melhor caminho para alcançar essas redes.
- Interface de saída.

Exemplo:

| Rede de destino | Interface |
|-----------------|-----------|
| 192.168.1.0/24 | Fa0/1 |
| 192.168.2.0/24 | Fa0/2 |

As rotas podem ser:

- **Estáticas:** configuradas manualmente pelo administrador.
- **Dinâmicas:** aprendidas automaticamente através de protocolos de roteamento.

Exemplo:

Um roteador recebe um pacote para `192.168.2.50`. Ele consulta sua tabela e encontra a rota `192.168.2.0/24 → Fa0/2`, então encaminha pela interface correta.

---

## 🎯 Rota Padrão

Quando um roteador não encontra uma rota específica para o destino, ele pode utilizar uma rota padrão.

A rota padrão é representada por:

```text
0.0.0.0/0
```

Ela indica para onde enviar pacotes cujo destino não está presente na tabela de roteamento.

Exemplo:

Um roteador doméstico possui `0.0.0.0/0 → Internet`. Qualquer destino desconhecido é enviado para o provedor.

---

## 🔀 Segmentação de Redes

Dividir uma rede grande em segmentos menores ajuda a melhorar desempenho, segurança e organização.

Uma rede única possui um grande domínio de broadcast onde todos os dispositivos recebem broadcasts.

Ao dividir a rede:

```text
Rede 1: 192.168.1.0
    ↓
Roteador
    ↓
Rede 2: 192.168.2.0
```

Cada rede possui seu próprio domínio de broadcast.

Exemplo:

Uma empresa separa departamentos:

```text
Financeiro: 192.168.10.0/24
RH: 192.168.20.0/24
```

Cada setor possui seu próprio domínio de broadcast.

---

## 🏢 LAN única x Redes segmentadas

### Uma única LAN

Vantagens:

- Menor custo.
- Menor complexidade.
- Comunicação mais direta.

Desvantagens:

- Mais tráfego de broadcast.
- Menor segurança.
- Mais difícil de gerenciar em redes grandes.

Exemplo:

Pequeno escritório com 10 computadores e 1 switch em uma única rede.

---

### Redes segmentadas

Vantagens:

- Redução de broadcasts.
- Melhor desempenho.
- Maior segurança.
- Melhor organização.

Desvantagens:

- Necessita de roteamento.
- Maior custo e complexidade.

Exemplo:

Empresa com VLANs separadas para Funcionários, Servidores e Visitantes.

---

## 🔗 VLAN

Uma VLAN permite dividir uma LAN em redes lógicas menores utilizando switches.

Cada VLAN cria um domínio de broadcast separado.

Exemplo:

```text
VLAN 10 - Financeiro: 192.168.10.0/24
VLAN 20 - TI: 192.168.20.0/24
```

Para que VLANs diferentes se comuniquem, é necessário roteamento entre elas.

Exemplo:

Wi-Fi corporativo com SSID Empresa (VLAN Funcionários) e SSID Visitantes (VLAN Visitantes). Visitantes não acessam a rede interna.

---

## 📚 Conceitos aprendidos

| Conceito | Descrição |
|----------|-----------|
| **Roteamento** | Processo de encaminhar pacotes entre redes diferentes usando roteadores. |
| **Roteador** | Dispositivo de Camada 3 que conecta redes e decide o melhor caminho para os pacotes. |
| **Gateway Padrão** | Endereço IP do roteador usado pelos hosts para acessar outras redes. |
| **Tabela de Roteamento** | Conjunto de informações que o roteador usa para escolher por onde encaminhar os pacotes. |
| **Rota Padrão** | Caminho usado quando o roteador não possui uma rota específica para o destino. |
| **ARP** | Protocolo usado para descobrir o endereço MAC associado a um endereço IP dentro da rede local. |
| **Endereço IP** | Identifica a origem e o destino final de uma comunicação. |
| **Endereço MAC** | Identifica dispositivos dentro da rede local e é usado na comunicação Ethernet. |
| **Domínio de Broadcast** | Área da rede onde uma mensagem broadcast é recebida por todos os dispositivos. |
| **Segmentação de Rede** | Divisão de uma rede grande em redes menores para melhorar desempenho, segurança e organização. |
| **LAN** | Rede local onde dispositivos se comunicam dentro de uma área administrada. |
| **VLAN** | Tecnologia que permite criar redes lógicas separadas dentro de um mesmo switch. |
| **Roteamento entre Redes** | Permite a comunicação entre diferentes redes através de dispositivos de Camada 3. |

---

## 📋 Resumo

- Switches encaminham dados usando endereços MAC.
- Roteadores encaminham dados usando endereços IP.
- Comunicação dentro da mesma rede usa ARP e entrega direta.
- Comunicação entre redes diferentes utiliza o gateway padrão.
- Roteadores utilizam tabelas de roteamento para escolher caminhos.
- Segmentar redes melhora desempenho, segurança e organização.

---

## 👨‍💻 Autor

**Pablo Gonçalves Santos**

* Sistemas de Informação
* Redes e Cibersegurança

---

<div align="center">

[![GitHub](https://img.shields.io/badge/Voltar_ao_Perfil-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/pablogsantoscontato-ops)

---

<sub>Documentação sobre Roteamento entre Redes</sub>

</div>
