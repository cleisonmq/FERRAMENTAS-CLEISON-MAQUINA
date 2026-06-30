# Documentação Técnica: backdoor_by_cm

## 1. Informações Gerais
* **Criador:** Cleison Máquina
* **Ano:** 2026
* **Sistemas:** Linux
* **GitHub:** [cleisonmq](https://github.com/cleisonmq)

---

## 2. Descrição Técnica
A `backdoor_by_cm` é uma ferramenta desenvolvida em **Python** projetada para estabelecer uma conexão remota a um dispositivo de forma persistente. O termo *backdoor* (porta das traseiras) é aplicado porque o script atua de forma silenciosa no sistema operativo, minimizando a visibilidade das suas atividades para o utilizador comum.

---

## 3. Funcionamento e Comportamento Interno
Quando executada, a ferramenta realiza as seguintes ações estruturais no sistema:

1. **Criação de Ficheiros Ocultos:** Gera dois scripts secundários denominados `backdoor_principal.py` e `backdoor_secundaria.py`. Ambos são movidos e armazenados na diretoria do sistema `/var/sys/`.
2. **Persistência do Sistema:** Cria e configura dois serviços nativos do sistema operativo vinculados aos scripts criados. Isto garante o **modo persistente**, permitindo que a ameaça seja iniciada automaticamente sempre que o sistema for ligado ou reiniciado.
3. **Execução e Notificação:** Inicia os processos a partir de `/var/sys/` e dispara uma notificação por e-mail para o utilizador/atacante (utilizando os campos de credenciais configurados), informando que o acesso remoto está ativo.

---

## 4. Como Utilizar (Ambiente de Testes)
> ⚠️ **Aviso:** Esta ferramenta deve ser utilizada exclusivamente para fins de aprendizagem e em ambientes controlados de laboratório.

1. **Configuração de Credenciais:** Após transferir a ferramenta, abra o ficheiro de configuração e edite os campos `email` e `senha_app` para ativar as notificações de ativação.
2. **Execução:** Com privilégios de administrador (root/sudo), execute o comando principal no terminal:
   ```bash
   python3 backdoor_by_cm.py