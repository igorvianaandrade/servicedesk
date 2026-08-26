# 🌐 Redes de Computadores – Conteúdo Detalhado

Este documento reúne os conceitos fundamentais de redes de computadores, com foco no **modelo OSI**, **endereçamento IP**, **DNS**, **protocolos**, e na **jornada do pacote de dados**. Inclui também exercícios práticos para fixação.

---

## 🧩 Modelo OSI – Camadas em Detalhe

1. **Física (Physical)**
   - Função: Transmissão de bits crus pelo meio físico.
   - Exemplos: Cabos UTP, fibra óptica, Wi-Fi, sinais elétricos.
   - Problemas comuns: cabo desconectado, sinal fraco, falha no adaptador.

2. **Enlace (Data Link)**
   - Função: Comunicação dentro da LAN, controle de acesso ao meio.
   - Exemplos: Endereço MAC, switches, placas de rede.
   - Problemas comuns: colisões, VLAN incorreta, porta do switch desativada.

3. **Rede (Network)**
   - Função: Endereçamento lógico e roteamento de pacotes.
   - Exemplos: IP, roteadores, gateway padrão.
   - Problemas comuns: IP incorreto, gateway errado, rota inexistente, conflito de IP.

4. **Transporte (Transport)**
   - Função: Segmentação e entrega confiável dos dados.
   - Exemplos: TCP (confiável), UDP (rápido).
   - Problemas comuns: porta bloqueada, firewall ativo, perda de pacotes.

5. **Sessão (Session)**
   - Função: Estabelecer e manter sessões de comunicação.
   - Exemplos: RPC, NetBIOS, sockets.
   - Problemas comuns: sessão expirada, falha de autenticação, timeout.

6. **Apresentação (Presentation)**
   - Função: Tradução, criptografia e compressão dos dados.
   - Exemplos: SSL/TLS, JSON, UTF-8.
   - Problemas comuns: certificado inválido, incompatibilidade de codificação.

7. **Aplicação (Application)**
   - Função: Interface direta com o usuário.
   - Exemplos: HTTP, HTTPS, DNS, SSH.
   - Problemas comuns: site fora do ar, erro 404/500.

---

## 🔢 Endereçamento IP, Máscara e Gateway

- **IP:** Identifica o dispositivo na rede.  
- **Máscara:** Define qual parte é rede e qual parte é host.  
- **Gateway:** Roteador que conecta sua rede local à internet.  

Exemplo:
- IP: `192.168.1.10`
- Máscara: `255.255.255.0`
- Gateway: `192.168.1.1`

---

## 📛 DNS, Portas e Protocolos

- **DNS:** Traduz nomes em IPs.  
- **Portas:** Identificam serviços (80 → HTTP, 443 → HTTPS, 53 → DNS).  
- **Protocolos:** Regras de comunicação (TCP → confiável, UDP → rápido, HTTP → web, SMTP → e-mail).

---

## 📦 Jornada do Pacote de Dados

### Etapas
1. Usuário digita `www.site.com` no navegador.
2. DNS resolve o nome para um IP.
3. Pacote sai pelo **gateway**.
4. Passa por roteadores até chegar ao servidor.
5. Servidor responde e o pacote retorna.
6. Navegador monta a página.

### Problemas possíveis por camada
- **Física:** cabo desconectado, sinal fraco no Wi-Fi.  
- **Enlace:** porta do switch desligada, MAC bloqueado.  
- **Rede:** IP incorreto, gateway errado, rota inexistente.  
- **Transporte:** firewall bloqueando porta, congestionamento.  
- **Sessão:** timeout, sessão não estabelecida.  
- **Apresentação:** certificado SSL inválido, falha de criptografia.  
- **Aplicação:** servidor web fora do ar, erro 500.

---

## 🛠️ Ferramentas Práticas

- `ping`: testa se o host responde.  
- `tracert` (Windows) / `traceroute` (Linux): mostra o caminho do pacote.  
- `ipconfig` (Windows) / `ifconfig` (Linux): exibe configuração de rede.  
- **Wireshark:** analisa tráfego em detalhes.  
- **Nmap:** varredura de portas e serviços.  
- **nslookup / dig:** teste de resolução DNS.  

---

## 🧠 Exercícios Práticos de Redes

### 🔍 Diagnóstico e Testes Básicos
1. **Verifique sua configuração de rede**
   ```bash
   ipconfig   # Windows
   ifconfig   # Linux/Mac
   ```
   - Identifique seu IP, máscara e gateway.

2. **Teste de conectividade**
   ```bash
   ping 8.8.8.8
   ping www.google.com
   ```
   - Se o primeiro falhar → problema local (camadas 1–3).
   - Se o segundo falhar → problema de DNS (camada 7).

3. **Rastreamento de rota**
   ```bash
   tracert www.microsoft.com   # Windows
   traceroute www.microsoft.com   # Linux/Mac
   ```

4. **Análise de portas**
   ```bash
   telnet www.google.com 80
   ```

---

### 🧩 Exercícios de Interpretação do Modelo OSI

| Problema | Camada OSI | Ferramenta de Diagnóstico |
|-----------|-------------|---------------------------|
| Cabo desconectado | Física | Verificar conexões físicas |
| MAC bloqueado no switch | Enlace | Painel do switch |
| IP incorreto | Rede | `ipconfig` / `ifconfig` |
| Porta bloqueada | Transporte | `telnet`, firewall |
| Sessão expirada | Sessão | Logs de autenticação |
| Certificado SSL inválido | Apresentação | Navegador / Wireshark |
| Site fora do ar | Aplicação | `ping`, navegador |

---

### 🧠 Desafio Final: Jornada do Pacote
Explique, com suas palavras, o caminho de um pacote de dados quando você acessa `www.microsoft.com`, indicando:
- As camadas envolvidas.
- Os protocolos utilizados.
- Um possível problema em cada etapa.

---

## 🗺️ Mapa Conceitual

```
[Física] → [Enlace] → [Rede] → [Transporte] → [Sessão] → [Apresentação] → [Aplicação]
       ↓
[IP/Máscara/Gateway] → [DNS/Portas/Protocolos] → [Cliente-Servidor] → [Jornada do Pacote]
       ↓
[Ferramentas práticas: ping, tracert, Wireshark]
```

---

## 🚀 Conclusão

A jornada de um pacote de dados é uma viagem pelas camadas do modelo OSI. Cada camada tem sua função e possíveis falhas, e entender isso é essencial para diagnosticar problemas de rede. Com ferramentas práticas, é possível identificar e corrigir rapidamente onde está o gargalo.
```

## 🔍 Fonte e de pesquisa 

Introdução a Redes
https://www.youtube.com/live/vlmf5-bYaOQ?si=ImqghAVdUTdNsw0f
