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
