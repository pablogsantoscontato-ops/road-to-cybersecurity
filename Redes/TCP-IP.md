<div align="center">

# 🌐 Guia de TCP/IP

### Modelo TCP/IP e seus principais protocolos

[![Typing SVG](https://readme-typing-svg.demolab.com?font=Fira+Code&weight=600&size=22&duration=3000&pause=500&color=00FFAA&center=true&vCenter=true&width=435&lines=TCP%2FIP;Camadas+do+modelo;Protocolos+de+rede;Comunica%C3%A7%C3%A3o)](https://git.io/typing-svg)

---

</div>

Este documento apresenta os fundamentos do **modelo TCP/IP**, seu funcionamento, camadas e os principais protocolos utilizados na comunicação entre dispositivos em redes.

---

## 📌 O que é TCP/IP?

TCP/IP (*Transmission Control Protocol / Internet Protocol*) é um conjunto de protocolos responsável pela comunicação entre dispositivos em uma rede.

Ele define como os dados são:

- Preparados para transmissão
- Endereçados
- Transportados
- Entregues ao destino

O modelo TCP/IP é a base das redes modernas e da comunicação na Internet.

---

## 🏗️ Camadas do Modelo TCP/IP

O modelo TCP/IP é dividido em 4 camadas:

| Camada | Função | Exemplos de Protocolos |
|--------|--------|----------------------|
| Aplicação | Fornece serviços de rede para aplicações | HTTP, HTTPS, DNS, DHCP, FTP, SMTP, SSH |
| Transporte | Controla a comunicação entre dispositivos | TCP, UDP |
| Internet | Realiza endereçamento e roteamento | IPv4, IPv6, ICMP |
| Acesso à Rede | Responsável pela transmissão física dos dados | Ethernet, Wi-Fi |

---

## 🌐 1. Camada de Aplicação

Responsável pela interação entre os serviços de rede e as aplicações.

Principais protocolos:

| Protocolo | Função |
|-----------|--------|
| HTTP | Transferência de páginas web |
| HTTPS | HTTP com criptografia através de TLS |
| DNS | Conversão de nomes de domínio em endereços IP |
| DHCP | Distribuição automática de endereços IP |
| FTP | Transferência de arquivos entre computadores |
| SMTP | Envio de e-mails entre servidores |
| SSH | Acesso remoto seguro a dispositivos |
| Telnet | Acesso remoto não criptografado (obsoleto) |
| SNMP | Monitoramento e gerenciamento de redes |

Exemplos:

- Ao acessar um site utilizando HTTPS, a camada de aplicação utiliza o protocolo HTTPS para realizar a comunicação com o servidor.
- Ao enviar um e-mail, o protocolo SMTP é utilizado para a transferência da mensagem entre os servidores.
- Ao digitar um nome de domínio no navegador, o DNS é acionado para traduzir o nome para um endereço IP.

---

## 🚚 2. Camada de Transporte

Responsável pela comunicação entre origem e destino, controlando a entrega dos dados.

Principais protocolos:

| Protocolo | Características |
|-----------|-----------------|
| TCP | Comunicação confiável e orientada à conexão |
| UDP | Comunicação rápida sem garantia de entrega |

---

### TCP (*Transmission Control Protocol*)

O TCP garante maior confiabilidade na transmissão.

Características:

- Confirma recebimento dos dados (ACK)
- Organiza a sequência dos pacotes
- Realiza retransmissões quando necessário
- Estabelece conexão através do Three-Way Handshake
- Controle de fluxo e congestionamento

Funcionamento do Three-Way Handshake:

SYN (Cliente) → SYN-ACK (Servidor) → ACK (Cliente)

Utilizado em:

- Navegação web (HTTP/HTTPS)
- Transferência de arquivos (FTP)
- E-mails (SMTP, POP3, IMAP)
- Acesso remoto (SSH)

---

### UDP (*User Datagram Protocol*)

O UDP prioriza velocidade e menor latência.

Características:

- Não realiza confirmação de entrega
- Possui menor controle sobre os dados
- Reduz o tempo de comunicação
- Não estabelece conexão prévia
- Menor overhead de dados

Utilizado em:

- Jogos online
- Streaming de vídeo e áudio
- Chamadas de vídeo
- DNS (consultas rápidas)
- VoIP (Voice over IP)

---

## 🌎 3. Camada de Internet

Responsável pelo endereçamento lógico e encaminhamento dos pacotes.

Principal protocolo:

### IP (*Internet Protocol*)

O protocolo IP identifica dispositivos através de endereços IP e permite que os pacotes sejam encaminhados entre redes.

Endereços:

- IPv4: 192.168.1.10 (32 bits)
- IPv6: 2001:0db8:85a3:0000:0000:8a2e:0370:7334 (128 bits)

Diferenças entre IPv4 e IPv6:

| Característica | IPv4 | IPv6 |
|----------------|------|------|
| Tamanho do endereço | 32 bits | 128 bits |
| Quantidade de endereços | 4.3 bilhões | 340 undecilhões |
| Representação | Decimal com pontos | Hexadecimal com dois-pontos |
| Segurança | Suporte a IPSec | Suporte aprimorado a IPSec |
| NAT | Amplamente utilizado | Geralmente desnecessário |

Principais protocolos:

| Protocolo | Função |
|-----------|--------|
| IPv4 | Endereçamento baseado em 32 bits |
| IPv6 | Endereçamento baseado em 128 bits |
| ICMP | Diagnóstico e mensagens de controle |
| ARP | Resolução de endereços MAC a partir de IP |
| RARP | Resolução de IP a partir de MAC (obsoleto) |

Exemplos:

- O comando `ping` utiliza ICMP para verificar a comunicação entre dispositivos.
- O roteamento de pacotes entre redes utiliza o protocolo IP para definir o caminho até o destino.
- O ARP descobre o endereço MAC correspondente a um endereço IP na rede local.

---

## 🔌 4. Camada de Acesso à Rede

Responsável pela comunicação entre o dispositivo e o meio físico.

Inclui:

- Placas de rede (NIC)
- Cabos (Ethernet, Fibra Óptica)
- Wi-Fi
- Endereços MAC

Principais tecnologias:

| Tecnologia | Descrição |
|------------|-----------|
| Ethernet | Padrão de redes cabeadas (10/100/1000 Mbps) |
| Wi-Fi | Redes sem fio (802.11a/b/g/n/ac/ax) |
| PPP | Protocolo ponto a ponto |
| Frame Relay | Tecnologia WAN legada |

Endereço MAC:

- Endereço físico único de 48 bits
- Formato: XX:XX:XX:XX:XX:XX
- Utilizado para comunicação na rede local

---

## 🔑 Portas e Sockets

Portas são identificadores numéricos utilizados para direcionar a comunicação para serviços específicos dentro de um dispositivo.

Enquanto o endereço IP identifica o dispositivo na rede, a porta identifica a aplicação ou serviço.

Exemplo:

```text
192.168.1.10:443
```

IP → dispositivo
443 → serviço HTTPS

### Categorias de Portas

As portas TCP e UDP são divididas em três categorias principais, variando de 1 a 65.535.

| Categoria | Intervalo | Descrição |
|-----------|-----------|-----------|
| Portas bem conhecidas (*Well-Known Ports*) | 1 - 1023 | Associadas a serviços comuns da Internet |
| Portas registradas | 1024 - 49151 | Utilizadas por aplicações específicas e empresas |
| Portas privadas/dinâmicas | 49152 - 65535 | Geralmente usadas como portas de origem temporárias |

Exemplos de portas bem conhecidas:

| Porta | Protocolo | Serviço |
|-------|-----------|---------|
| 20 | TCP | FTP (dados) |
| 21 | TCP | FTP (controle) |
| 22 | TCP | SSH |
| 23 | TCP | Telnet (acesso remoto não seguro) |
| 25 | TCP | SMTP |
| 53 | TCP/UDP | DNS |
| 80 | TCP | HTTP |
| 110 | TCP | POP3 |
| 143 | TCP | IMAP |
| 443 | TCP | HTTPS |
| 3389 | TCP | RDP |

### Portas de Origem e Destino

Toda comunicação TCP ou UDP possui duas portas:

- **Porta de origem:** identifica a aplicação que iniciou a comunicação.
- **Porta de destino:** identifica o serviço solicitado no servidor.

Exemplo de uma conexão Web:

```text
Cliente                              Servidor
192.168.1.10:52000 ──────────→ 142.250.190.14:443

Porta origem: 52000                  Porta destino: 443
```

A porta de destino informa ao servidor qual serviço deve receber a solicitação.

A porta de origem permite que o cliente identifique para qual aplicação a resposta deve retornar.

### Socket e Par de Sockets

Um **socket** é formado pela combinação:

```text
Endereço IP + Número da Porta
```

Exemplo:

```text
192.168.1.10:52000
```

Representa:

- IP: dispositivo na rede
- Porta: aplicação ou serviço utilizado

Uma comunicação completa utiliza dois sockets:

```text
Socket do cliente: 192.168.1.10:52000
Socket do servidor: 142.250.190.14:443
```

Juntos eles formam um **par de sockets**, que identifica uma conexão específica entre dois dispositivos.

Os sockets permitem que várias aplicações utilizem a rede simultaneamente sem que os dados sejam entregues ao programa errado.

---

## 📡 Multiplexação e Desmultiplexação

A camada de transporte permite que vários serviços utilizem a rede ao mesmo tempo através das portas.

### Multiplexação

No dispositivo de origem, várias aplicações enviam dados utilizando diferentes portas.

Exemplo:

```text
Navegador → porta 443
E-mail → porta 25
DNS → porta 53
```

Esses dados são enviados pela mesma interface de rede utilizando o protocolo IP.

### Desmultiplexação

No dispositivo destino, a camada de transporte analisa a porta de destino e entrega os dados ao serviço correto.

Exemplo:

```text
Porta 80 → HTTP
Porta 443 → HTTPS
Porta 53 → DNS
```

---

## 🔄 Encapsulamento

Durante a transmissão, os dados passam pelas camadas do modelo TCP/IP e recebem informações adicionais.

Processo de encapsulamento:

1. Dados da aplicação
2. Segmento (TCP/UDP) - Adiciona porta de origem e destino
3. Pacote (IP) - Adiciona IP de origem e destino
4. Quadro (Ethernet) - Adiciona MAC de origem e destino
5. Bits - Transmissão física

No destino, ocorre o processo inverso chamado **desencapsulamento**, onde os dados são reorganizados para a aplicação receptora.

---

## 📚 Conceitos aprendidos

| Conceito | Descrição |
|----------|-----------|
| **Modelo TCP/IP** | Conjunto de protocolos utilizado para comunicação entre dispositivos em redes, sendo a base da Internet. |
| **Camadas TCP/IP** | Divisão da comunicação em quatro camadas: Aplicação, Transporte, Internet e Acesso à Rede. |
| **Camada de Aplicação** | Responsável pelos serviços utilizados pelos usuários, como HTTP, HTTPS, DNS, DHCP, FTP e SSH. |
| **Camada de Transporte** | Controla a comunicação entre dispositivos através dos protocolos TCP e UDP. |
| **TCP** | Protocolo orientado à conexão que garante entrega confiável dos dados, utilizando confirmações, retransmissões e controle de fluxo. |
| **UDP** | Protocolo mais rápido e simples, utilizado quando baixa latência é mais importante que garantia de entrega. |
| **Camada de Internet** | Responsável pelo endereçamento lógico e roteamento utilizando protocolos como IPv4 e IPv6. |
| **IP** | Protocolo responsável por identificar dispositivos e encaminhar pacotes entre redes. |
| **IPv4 e IPv6** | Protocolos de endereçamento que identificam dispositivos dentro de uma rede. |
| **ICMP** | Protocolo utilizado para mensagens de controle e diagnóstico, como o comando ping. |
| **ARP** | Protocolo utilizado para descobrir o endereço MAC associado a um endereço IP na rede local. |
| **Camada de Acesso à Rede** | Responsável pela comunicação física utilizando tecnologias como Ethernet, Wi-Fi e endereços MAC. |
| **Endereço MAC** | Endereço físico de uma placa de rede utilizado para comunicação dentro da rede local. |
| **Portas** | Identificadores numéricos utilizados para direcionar a comunicação para serviços específicos em um dispositivo. |
| **Portas bem conhecidas** | Portas de 1 a 1023 associadas a serviços comuns da Internet. |
| **Portas registradas** | Portas de 1024 a 49151 utilizadas por aplicações específicas e empresas. |
| **Portas privadas/dinâmicas** | Portas de 49152 a 65535 usadas como portas de origem temporárias. |
| **Porta de origem** | Identifica a aplicação que iniciou a comunicação. |
| **Porta de destino** | Identifica o serviço solicitado no servidor. |
| **Socket** | Combinação entre endereço IP e porta que identifica uma comunicação específica. |
| **Par de sockets** | Combinação dos sockets do cliente e servidor que identifica uma conexão única. |
| **Multiplexação** | Processo em que várias aplicações enviam dados através da mesma interface de rede. |
| **Desmultiplexação** | Processo em que a camada de transporte entrega os dados ao serviço correto baseado na porta de destino. |
| **Encapsulamento** | Processo em que cada camada adiciona informações aos dados antes da transmissão. |
| **Desencapsulamento** | Processo inverso, onde o dispositivo destino remove as informações adicionadas pelas camadas. |
| **Protocolos de rede** | Regras que permitem a comunicação entre dispositivos, definindo como os dados são enviados e recebidos. |

---

## 📋 Resumo

- TCP/IP é o modelo utilizado na Internet
- Possui 4 camadas principais: Aplicação, Transporte, Internet e Acesso à Rede
- Cada camada possui protocolos específicos
- TCP fornece confiabilidade na transmissão
- UDP fornece velocidade com menor overhead
- IP realiza o endereçamento e roteamento dos pacotes
- Portas identificam serviços em um dispositivo
- Encapsulamento adiciona cabeçalhos a cada camada
- Desencapsulamento remove os cabeçalhos no destino

---

## 👨‍💻 Autor

**Pablo Gonçalves Santos**

* Sistemas de Informação
* Redes e Cibersegurança

---

<div align="center">

[![GitHub](https://img.shields.io/badge/Voltar_ao_Perfil-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/pablogsantoscontato-ops)

---

<sub>Documentação sobre TCP/IP e Redes de Computadores</sub>

</div>
