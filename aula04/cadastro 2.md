# ============================================================
# SISTEMA DE CADASTRO E LOGIN DE CLIENTES (COM TRATAMENTO DE ERROS)
# ============================================================
# Este código foi feito para iniciantes entenderem com facilidade.
# Ele permite:
# - cadastrar clientes (nome, email e senha)
# - fazer login com email e senha
# - listar clientes cadastrados (modo simples)
#
# Também possui tratamento rigoroso de erros, como:
# - campos vazios
# - email inválido
# - senha fraca
# - email já cadastrado
# - login com email inexistente
# - senha incorreta
# - erros de digitação do usuário no menu
# ============================================================


# ----------------------------
# "Banco de dados" em memória
# ----------------------------
# Aqui vamos guardar os clientes cadastrados dentro de uma lista.
# Cada cliente será um dicionário:
# {"nome": "...", "email": "...", "senha": "..."}
clientes = []


# ============================================================
# FUNÇÃO: validar_email(email)
# ============================================================
# Verifica se o email tem um formato minimamente válido.
# Regras simples:
# - precisa conter "@"
# - precisa conter "."
# - não pode ter espaços
# - não pode começar ou terminar com "@"
# ============================================================
def validar_email(email):
    if " " in email:
        return False

    if "@" not in email:
        return False

    if "." not in email:
        return False

    # split divide o texto em partes
    partes = email.split("@")

    # se tiver mais de 1 "@", o split terá mais de 2 partes
    if len(partes) != 2:
        return False

    usuario = partes[0]
    dominio = partes[1]

    # usuário e domínio não podem ser vazios
    if usuario == "" or dominio == "":
        return False

    # domínio precisa ter um ponto, exemplo: gmail.com
    if "." not in dominio:
        return False

    return True


# ============================================================
# FUNÇÃO: validar_senha(senha)
# ============================================================
# Regras para senha:
# - mínimo 6 caracteres
# - precisa ter pelo menos 1 número
# - precisa ter pelo menos 1 letra
# ============================================================
def validar_senha(senha):
    if len(senha) < 6:
        return False

    tem_numero = False
    tem_letra = False

    for caractere in senha:
        if caractere.isdigit():
            tem_numero = True
        if caractere.isalpha():
            tem_letra = True

    if tem_numero and tem_letra:
        return True
    else:
        return False


# ============================================================
# FUNÇÃO: email_existe(email)
# ============================================================
# Verifica se o email já está cadastrado no sistema.
# ============================================================
def email_existe(email):
    for cliente in clientes:
        if cliente["email"] == email:
            return True
    return False


# ============================================================
# FUNÇÃO: cadastrar_cliente()
# ============================================================
# Permite cadastrar um cliente novo com validações fortes.
# ============================================================
def cadastrar_cliente():
    print("\n=== CADASTRO DE CLIENTE ===")

    try:
        nome = input("Digite o nome: ").strip()
        email = input("Digite o email: ").strip().lower()
        senha = input("Digite a senha: ").strip()

        # ----------------------------
        # Tratamento de campos vazios
        # ----------------------------
        if nome == "" or email == "" or senha == "":
            print("❌ ERRO: Nenhum campo pode estar vazio.")
            return

        # ----------------------------
        # Validação de email
        # ----------------------------
        if not validar_email(email):
            print("❌ ERRO: Email inválido. Exemplo válido: exemplo@gmail.com")
            return

        # ----------------------------
        # Verificar se email já existe
        # ----------------------------
        if email_existe(email):
            print("❌ ERRO: Este email já está cadastrado.")
            return

        # ----------------------------
        # Validação de senha forte
        # ----------------------------
        if not validar_senha(senha):
            print("❌ ERRO: Senha fraca.")
            print("A senha deve ter pelo menos 6 caracteres, letras e números.")
            return

        # ----------------------------
        # Se passou por tudo, cadastra
        # ----------------------------
        cliente = {
            "nome": nome,
            "email": email,
            "senha": senha
        }

        clientes.append(cliente)

        print("✅ Cliente cadastrado com sucesso!")

    except Exception as erro:
        # Esse except pega qualquer erro inesperado do Python
        print("❌ ERRO inesperado no cadastro.")
        print("Detalhes:", erro)


# ============================================================
# FUNÇÃO: login_cliente()
# ============================================================
# Permite login com validação e tratamento de erros.
# ============================================================
def login_cliente():
    print("\n=== LOGIN DE CLIENTE ===")

    try:
        email = input("Digite o email: ").strip().lower()
        senha = input("Digite a senha: ").strip()

        # ----------------------------
        # Campos vazios
        # ----------------------------
        if email == "" or senha == "":
            print("❌ ERRO: Email e senha não podem estar vazios.")
            return

        # ----------------------------
        # Validar formato do email
        # ----------------------------
        if not validar_email(email):
            print("❌ ERRO: Formato de email inválido.")
            return

        # ----------------------------
        # Verificar se existe cliente com esse email
        # ----------------------------
        for cliente in clientes:
            if cliente["email"] == email:
                # achou o email, agora compara senha
                if cliente["senha"] == senha:
                    print(f"✅ Login realizado com sucesso! Bem-vindo(a), {cliente['nome']}!")
                    return
                else:
                    print("❌ ERRO: Senha incorreta.")
                    return

        # Se saiu do loop, significa que não encontrou o email
        print("❌ ERRO: Email não encontrado. Cadastre-se primeiro.")

    except Exception as erro:
        print("❌ ERRO inesperado no login.")
        print("Detalhes:", erro)


# ============================================================
# FUNÇÃO: listar_clientes()
# ============================================================
# Mostra os clientes cadastrados (sem mostrar senha).
# ============================================================
def listar_clientes():
    print("\n=== LISTA DE CLIENTES CADASTRADOS ===")

    if len(clientes) == 0:
        print("⚠️ Nenhum cliente cadastrado ainda.")
        return

    for i, cliente in enumerate(clientes, start=1):
        print(f"{i}. Nome: {cliente['nome']} | Email: {cliente['email']}")


# ============================================================
# FUNÇÃO: menu()
# ============================================================
# Mostra opções para o usuário e controla o sistema.
# ============================================================
def menu():
    while True:
        print("\n===============================")
        print("   SISTEMA DE CADASTRO/LOGIN   ")
        print("===============================")
        print("1 - Cadastrar cliente")
        print("2 - Fazer login")
        print("3 - Listar clientes")
        print("4 - Sair")

        try:
            opcao = input("Escolha uma opção: ").strip()

            # Verifica se o usuário digitou número mesmo
            if not opcao.isdigit():
                print("❌ ERRO: Você deve digitar um número (1, 2, 3 ou 4).")
                continue

            opcao = int(opcao)

            if opcao == 1:
                cadastrar_cliente()
            elif opcao == 2:
                login_cliente()
            elif opcao == 3:
                listar_clientes()
            elif opcao == 4:
                print("Saindo do sistema... Até mais!")
                break
            else:
                print("❌ ERRO: Opção inválida. Escolha entre 1 e 4.")

        except KeyboardInterrupt:
            # Se o usuário apertar Ctrl+C
            print("\n❌ Programa interrompido pelo usuário (Ctrl+C).")
            break

        except Exception as erro:
            print("❌ ERRO inesperado no menu.")
            print("Detalhes:", erro)


# ============================================================
# INÍCIO DO PROGRAMA
# ============================================================
menu()