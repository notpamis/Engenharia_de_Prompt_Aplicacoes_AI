# Cadastro simples de clientes em Python
# Usa lista e dicionário (conceitos básicos)

clientes = []  # lista onde vamos guardar os clientes

while True:
    print("\n=== MENU CADASTRO DE CLIENTES ===")
    print("1 - Cadastrar cliente")
    print("2 - Listar clientes")
    print("3 - Buscar cliente pelo CPF")
    print("4 - Remover cliente pelo CPF")
    print("5 - Sair")

    opcao = input("Escolha uma opção: ")

    # CADASTRAR
    if opcao == "1":
        nome = input("Digite o nome: ")
        cpf = input("Digite o CPF: ")
        idade = input("Digite a idade: ")

        # Verificar se CPF já existe
        cpf_existe = False
        for cliente in clientes:
            if cliente["cpf"] == cpf:
                cpf_existe = True
                break

        if cpf_existe:
            print("❌ Erro: CPF já cadastrado!")
        else:
            cliente = {
                "nome": nome,
                "cpf": cpf,
                "idade": idade
            }
            clientes.append(cliente)
            print("✅ Cliente cadastrado com sucesso!")

    # LISTAR
    elif opcao == "2":
        if len(clientes) == 0:
            print("⚠ Nenhum cliente cadastrado.")
        else:
            print("\n=== LISTA DE CLIENTES ===")
            for cliente in clientes:
                print(f"Nome: {cliente['nome']} | CPF: {cliente['cpf']} | Idade: {cliente['idade']}")

    # BUSCAR
    elif opcao == "3":
        cpf_busca = input("Digite o CPF para buscar: ")
        encontrado = False

        for cliente in clientes:
            if cliente["cpf"] == cpf_busca:
                print("\n✅ Cliente encontrado:")
                print(f"Nome: {cliente['nome']}")
                print(f"CPF: {cliente['cpf']}")
                print(f"Idade: {cliente['idade']}")
                encontrado = True
                break

        if not encontrado:
            print("❌ Cliente não encontrado.")

    # REMOVER
    elif opcao == "4":
        cpf_remover = input("Digite o CPF para remover: ")
        removido = False

        for cliente in clientes:
            if cliente["cpf"] == cpf_remover:
                clientes.remove(cliente)
                removido = True
                print("✅ Cliente removido com sucesso!")
                break

        if not removido:
            print("❌ CPF não encontrado.")

    # SAIR
    elif opcao == "5":
        print("👋 Saindo do sistema...")
        break

    else:
        print("❌ Opção inválida! Tente novamente.")