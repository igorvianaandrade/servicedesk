# 🖥️ Comandos Essenciais do CMD na Prática

## 🔒 Segurança do Prompt
- **Executar como administrador:** Clique com botão direito → *Executar como administrador*  
- **Encerrar sessão atual:**  
  ```cmd
  exit
  ```
- **Verificar permissões de usuário:**  
  ```cmd
  whoami
  ```

---

## ⚡ Uso do Prompt
- **Ver versão do Windows:**  
  ```cmd
  ver
  ```
- **Obter ajuda de um comando:**  
  ```cmd
  help
  help dir
  ```

---

## 📂 Navegação de Arquivos
- **Listar arquivos e pastas:**  
  ```cmd
  dir
  ```
- **Entrar em uma pasta:**  
  ```cmd
  cd nome_da_pasta
  ```
- **Voltar uma pasta:**  
  ```cmd
  cd ..
  ```
- **Criar pasta:**  
  ```cmd
  mkdir projetos
  ```
- **Apagar pasta/arquivo:**  
  ```cmd
  rmdir nome_da_pasta
  del arquivo.txt
  ```

---

## 📋 Inventário e Processos da Máquina

"Conhecer e perceber o seu ambiente é um fator importante!"
(Inventário, processos que trabalha, tipo de máquina usada. 
Saber modelo da máquina, modelo do processador, quantidade de Memoria RAM, 
tipo/tamanho de Disco(tem espaço?...) 
 
Durante o atendimento, é essencial verificar **Processamento, Memória RAM, Rede e Disco**.
👉 Os maiores problemas costumam estar em **CPU e RAM**, pois impactam diretamente a performance do usuário.

- **Informações completas do sistema (causa raiz do ticket):**  
  ```cmd
  hostname
  ```
  Identificar o nome de rede da máquina para inventário.
  
  ```cmd
  systeminfo
  ```
  - Versão do SO  
  - Memória física instalada  
  - Tempo de inicialização  
  - Patches aplicados  

  **Dicas importantes:** Hoje em dia temos tipos de máquinas distintas dentro da empresa, devido ao avanço tecnológico ser rápido.
  - Um software ou drive é imaginado a ser instalado na máquina "x" do mesmo modelo e fabricante, normalmente sendo o chipset do mesmo fabricante mas dentro da máquina pode existir um componente, dentro daquela placa mãe, diferente não pelo modelo da máquina e sim pela disponibilidade do que tinha no momento para uso (Exemplo: placa de USB diferente de uma máquina do mesmo modelo, então são drives diferentes).
  - Verificar no systeminfo para entender melhor a tecnologia e poder fazer um atendimento mais eficiente. Montar uma imagem melhor. Instalar o Windows com mais assertividade para o usuário, evitando devolução de tickets de atendimento. 
  
  **Boa prática:** guardar essas evidências no ticket para futuras resoluções mais rápidas.

- **Listar processos ativos:**  
  ```cmd
  tasklist
  ```
  Mostra todos os processos em execução, consumo de memória e PID.

- **Encerrar processo travado ou não autorizado:**  
  ```cmd
  taskkill /PID [pid] /F
  ```
  Exemplo:  
  ```cmd
  taskkill /PID 1234 /F
  ```
  👉 Útil para liberar recursos de CPU/RAM e resolver travamentos.

---

## 🌐 Triagem Inicial de Conectividade

A triagem de rede é o primeiro passo para identificar falhas de conectividade.  
O fluxo ideal segue esta sequência:

1. **Configurações básicas de rede:**  
   ```cmd
   ipconfig
   ```
   - Endereço IP(Endereço local. Importante também saber o endereço de origem do pacote em problemas de conexão com servidor, por exemplo.)  
   - Máscara de sub-rede. (Saber se a rede esta conectável com outra rede)
   - Gateway padrão. (Saber qual a saída para conectar e para ter as rotas ou para que chegue ao roteador e ele rotei para o local certo.)  

2. **Relatório completo da interface:**  
   ```cmd
   ipconfig /all
   ```
   - Todas as interfaces de rede conectadas
   - DNS configurado (primario, secundário..) 
   - Endereço físico (MAC) da placa de rede (O que determina ter alguma regra de firewall, tipo esse macadress tem esse tipo de navegação, ex: apenas o endereço mac do adm. de redes pode acessar os servidores em caso de segurança.)

4. **Testar conectividade (gateway/local/internet):**  
   ```cmd
   ping 8.8.8.8
   ping google.com
   ```
   - Protocolo ICMP(TCP: confirma chegada do pacote | UDP: sem confirmação de chegada do pacote)
   - Verifica se há resposta do gateway ou da internet.

5. **Rastrear caminho até destino:**  
   ```cmd
   tracert google.com
   ```
   - Mostra cada salto (roteador) até o destino.  
   - Útil para identificar onde a conexão falha.  

👉 **Fluxo recomendado:**  
`ipconfig` → validar IP e gateway → `ping` no gateway → `ping` na internet → `tracert` para mapear falha.

- `[ipconfig]` → Configurações básicas de rede  
- `[ipconfig /all]` → Detalhes da interface (DNS, MAC)  
- `[ping]` → Teste de conectividade  
- `[tracert]` → Rastreio da rota até o destino  

---

## 🛠️ Mão na Massa (Exemplos para Praticar)
1. Criar uma pasta chamada `teste` e entrar nela:  
   ```cmd
   mkdir teste
   cd teste
   ```
2. Criar um arquivo de texto vazio:  
   ```cmd
   echo. > exemplo.txt
   ```
3. Listar arquivos e verificar se `exemplo.txt` está lá:  
   ```cmd
   dir
   ```
4. Apagar o arquivo:  
   ```cmd
   del exemplo.txt
   ```
5. Listar processos e encerrar o Notepad:  
   ```cmd
   tasklist
   taskkill /IM notepad.exe /F
   ```

---

## 📌 Guia Rápido de Comandos

| Comando | Função |
|---------|--------|
| `dir` | Lista arquivos e pastas |
| `cd` | Navega entre diretórios |
| `mkdir` | Cria nova pasta |
| `del` | Apaga arquivo |
| `tasklist` | Lista processos ativos |
| `taskkill /PID [pid] /F` | Encerra processo específico |
| `systeminfo` | Exibe informações completas do sistema |
| `ping` | Testa conectividade |
| `tracert` | Mostra rota de rede |
| `ipconfig` | Exibe configurações básicas de rede |
| `ipconfig /all` | Relatório completo da interface |
| `exit` | Fecha o prompt |

---

## 📈 Relevância no Atendimento

- **Processamento e RAM:** principais fontes de lentidão e travamentos.  
- **Systeminfo:** coleta evidências para análise de causa raiz.  
- **Tasklist + Taskkill:** controle direto sobre processos problemáticos.  
- **Triagem de rede:** garante que problemas não sejam confundidos com falhas locais.  

👉 Documentar cada passo no ticket aumenta eficiência e reduz tempo de resolução em atendimentos futuros.

---
