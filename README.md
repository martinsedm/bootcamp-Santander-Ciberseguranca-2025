# bootcamp-Santander-Ciberseguranca-2025
Bootcamp Santander - Cibersegurança 2025

# 📘 Estudos, Reflexões e Exemplos de Código sobre Ataques de Força Bruta com Medusa e Kali Linux

## 📌 Sobre este Repositório
Este repositório foi criado como entrega do desafio da DIO:  
**"Simulando um Ataque de Brute Force de Senhas com Medusa e Kali Linux"**.

Devido a limitações de hardware, não consegui instalar o VirtualBox na minha máquina, então não foi possível montar o laboratório usando máquinas virtuais.  

Por isso este projeto **documenta em detalhes todo o aprendizado adquirido**, abordando:

- Conceitos de ataques de força bruta, password spraying e credential stuffing  
- Estudo teórico das ferramentas utilizadas no Kali Linux  
- Funcionamento do Medusa e seus módulos  
- Exemplos de códigos e comandos  
- Reflexões sobre vulnerabilidades  
- Recomendações de mitigação  

---

# 🧠 1. Conceitos Fundamentais Aprendidos

## 🔐 1.1 Ataques de Força Bruta
Ataques de força bruta consistem em tentar repetidamente combinações de usuário e senha até encontrar uma credencial válida. São realizados de maneira automatizada e podem atingir centenas de tentativas por segundo.

### Onde ocorrem:
- SSH  
- FTP  
- SMB  
- HTTP (formulários de login)  
- APIs expostas  

### Riscos:
- Acesso indevido  
- Exfiltração de dados  
- Escalonamento de privilégios  
- Comprometimento total do sistema  

---

## 🎯 1.2 Password Spraying
Diferente da força bruta tradicional, no password spraying o atacante:

- Escolhe **poucas senhas comuns**
- Testa essas senhas **em muitos usuários**

Assim evita bloqueios por tentativas consecutivas.

---

## 🎭 1.3 Credential Stuffing
Ocorre quando o atacante usa listas de credenciais vazadas de outros serviços.  
É altamente eficaz devido ao hábito comum de reutilizar senhas.

Ferramentas úteis:
- Medusa  
- Hydra  
- Ncrack  
- Burp Suite Intruder  

---

# 🛠️ 2. Ferramentas Estudadas

## 🐉 Kali Linux
Distribuição voltada para testes de intrusão.  
Possui ferramentas como:

- Nmap  
- Hydra  
- Medusa  
- Sqlmap  
- Enum4Linux  
- John the Ripper  
- Burp Suite  

Mesmo sem rodar a VM, estudei seus módulos e funcionamento interno.

---

## 🐍 Medusa — foco do desafio
Medusa é uma ferramenta rápida e modular para força bruta.

### Suporta:
- FTP  
- SMB  
- SSH  
- HTTP Form  
- MySQL  
- POP3  

### Recursos:
- Execução multi‑thread  
- Testes cruzados user × pass  
- Suporte a módulos específicos  
- Detecção automática de respostas  

---

# 🧾 3. Exemplos de Comandos Estudados

Mesmo sem laboratório prático, compreendi a sintaxe e funcionamento dos comandos.

---

## 📘 3.1 Ataque FTP com Medusa
```bash
medusa -h 192.168.0.10 -U users.txt -P senhas.txt -M ftp -t 4 -f

Parâmetros:
-h: IP alvo
-U: lista de usuários
-P: lista de senhas
-M ftp: módulo FTP
-t 4: número de threads
-f: parar ao encontrar credencial válida

## 🌐 3.2 Ataque a Formulário Web (DVWA) — Teórico
medusa -h 192.168.0.10 -u admin -P senhas.txt -M web-form \

Parâmetros:
  -m FORM:"/dvwa/login.php" \
  -m USER_FIELD:"username" \
  -m PASS_FIELD:"password" \
  -m DENY:"Login failed"

Usado quando:
. Endereço do formulário é conhecido
. Campos HTML podem ser identificados
. Mensagem de erro é previsível

📡 3.3 Enumeração SMB + Password Spraying
1. Enumerar usuários
enum4linux -U 192.168.0.10

2. Testar uma única senha
medusa -h 192.168.0.10 -U usuarios.txt -P senha_unica.txt -M smbnt

🔎 3.4 Nmap — Varredura de Portas
nmap -sV -p- 192.168.0.10

Resultados esperados:
. Lista de portas abertas
. Serviços e versões identificadas

📂 4. Criação de Wordlists — Estudos
🧾 4.1 Wordlist manual

users.txt
admin
root
user
test


passwords.txt
123456
password
admin
root
toor
msfadmin

🔧 4.2 Gerando wordlists com Crunch
crunch 4 6 abc123 -o wordlist.txt

🧩 5. Vulnerabilidades Comuns Observadas (Estudo)

. Falta de limite de tentativas
. Usuários padrão ativos
. Senhas fracas
. Exposição de serviços sem necessidade (FTP, SMB, Telnet)
. Ausência de MFA
. Formulários web sem proteção (CAPTCHA, rate limit)

🛡️ 6. Medidas de Mitigação — Reflexões Importantes
✔️ Boas práticas gerais

Políticas de senha forte
. Bloqueio após tentativas inválidas
. Monitoramento de logs
. Uso de autenticação multifator
. Remoção de serviços desnecessários
. Diminuição de superfície de ataque
. Autenticação baseada em chave pública (SSH)

🛑 Em aplicações web
. Rate limiting
. Captcha
. Proteção CSRF
. Detecção de comportamentos suspeitos

🔐 Em redes internas

. Restrições de firewall
. VPN para acesso administrativo
. Segmentação de rede
. Honeypots para detecção ativa

📈 7. Reflexão Pessoal Sobre o Aprendizado

Mesmo sem o ambiente prático, este estudo permitiu:

. Entender profundamente os métodos de ataque
. Aprender a linha de comando das principais ferramentas
. Desenvolver visão crítica sobre segurança de autenticação
. Documentar processos de forma profissional
. Compreender a importância do hardening e da prevenção

A maior lição é que segurança é um processo contínuo, não um produto.
