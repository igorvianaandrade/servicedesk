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

Durante o atendimento, é essencial verificar **Processamento, Memória RAM, Rede e Disco**.  
👉 Os maiores problemas costumam estar em **CPU e RAM**, pois impactam diretamente a performance do usuário.

- **Informações completas do sistema (causa raiz do ticket):**  
  ```cmd
  systeminfo
  ```
  - Versão do SO  
  - Memória física instalada  
  - Tempo de inicialização  
  - Patches aplicados  

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

1. **Configurações básicas de rede:**  
   ```cmd
   ipconfig
   ```
   - Endereço IP  
   - Máscara de sub-rede  
   - Gateway padrão  

2. **Relatório completo da interface:**  
   ```cmd
   ipconfig /all
   ```
   - DNS configurado  
   - Endereço físico (MAC)  

3. **Testar conectividade (gateway/local/internet):**  
   ```cmd
   ping 8.8.8.8
   ping google.com
   ```
   - Verifica se há resposta do gateway ou da internet.  

4. **Rastrear caminho até destino:**  
   ```cmd
   tracert google.com
   ```
   - Mostra cada salto (roteador) até o destino.  
   - Útil para identificar onde a conexão falha.  

👉 **Fluxo recomendado:**  
`ipconfig` → validar IP e gateway → `ping` no gateway → `ping` na internet → `tracert` para mapear falha.

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
