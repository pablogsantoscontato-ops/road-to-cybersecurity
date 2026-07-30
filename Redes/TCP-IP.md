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

| Camada | Função |
|--------|--------|
| Aplicação | Fornece serviços de rede para aplicações |
| Transporte | Controla a comunicação entre dispositivos |
| Internet | Realiza endereçamento e roteamento |
| Acesso à Rede | Responsável pela transmissão física dos dados |

---

## 🌐 1. Camada de Aplicação

Responsável pela interação entre os serviços de rede e as aplicações.

Principais protocolos:

| Protocolo | Função |
|-----------|--------|
| HTTP | Transferência de páginas web |
| HTTPS | Comunicação web segura |
| DNS | Conversão de nomes em endereços IP |
| DHCP | Distribuição automática de endereços IP |
| FTP | Transferência de arquivos |
| SMTP | Envio de e-mails |
| SSH | Acesso remoto seguro |

Exemplo:

Ao acessar um site utilizando HTTPS, a camada de aplicação utiliza o protocolo HTTPS para realizar a comunicação com o servidor.

---

## 🚚 2. Camada de Transporte

Responsável pela comunicação entre origem e destino, controlando a entrega dos dados.

Principais protocolos:

| Protocolo | Características |
|-----------|-----------------|
| TCP | Comunicação confiável e orientada à conexão |
| UDP | Comunicação rápida sem garantia de entrega |

---

### TCP

O TCP (*Transmission Control Protocol*) garante maior confiabilidade na transmissão.

Características:

- Confirma recebimento dos dados
- Organiza a sequência dos pacotes
- Realiza retransmissões quando necessário

Utilizado em:

- Navegação web
- Transferência de arquivos
- E-mails

---

### UDP

O UDP (*User Datagram Protocol*) prioriza velocidade e menor latência.

Características:

- Não realiza confirmação de entrega
- Possui menor controle sobre os dados
- Reduz o tempo de comunicação

Utilizado em:

- Jogos online
- Streaming
- Chamadas de vídeo

---

## 🌎 3. Camada de Internet

Responsável pelo endereçamento lógico e encaminhamento dos pacotes.

Principal protocolo:

### IP (Internet Protocol)

O protocolo IP identifica dispositivos através de endereços IP e permite que os pacotes sejam encaminhados entre redes.

Exemplo:

192.168.1.10

Principais protocolos:

| Protocolo | Função |
|-----------|--------|
| IPv4 | Endereçamento baseado em 32 bits |
| IPv6 | Endereçamento baseado em 128 bits |
| ICMP | Diagnóstico e mensagens de controle |

Exemplo:

O comando `ping` utiliza ICMP para verificar a comunicação entre dispositivos.

---

## 🔌 4. Camada de Acesso à Rede

Responsável pela comunicação entre o dispositivo e o meio físico.

Inclui:

- Placas de rede
- Cabos
- Wi-Fi
- Endereços MAC

Principais tecnologias:

- Ethernet
- Wi-Fi

---

## 🔄 Encapsulamento

Durante a transmissão, os dados passam pelas camadas do modelo TCP/IP e recebem informações adicionais.

Processo:

Dados
↓
Segmento (TCP/UDP)
↓
Pacote (IP)
↓
Quadro (Ethernet)
↓
Bits

No destino, ocorre o processo inverso chamado **desencapsulamento**.

---

## 📋 Resumo

- TCP/IP é o modelo utilizado na Internet
- Possui 4 camadas principais
- Cada camada possui protocolos específicos
- TCP fornece confiabilidade
- UDP fornece velocidade
- IP realiza o endereçamento e roteamento dos pacotes

---

## 👨‍💻 Autor

**Pablo Gonçalves Santos**

* Sistemas da Informação
* Redes e Cibersegurança

---

<div align="center">

[![GitHub](https://img.shields.io/badge/Voltar_ao_Perfil-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/pablogsantoscontato-ops)

---

<sub>Documentação sobre TCP/IP e Redes de Computadores</sub>

</div>
