# Função para salvar os contatos em um arquivo
def salvar_contatos(lista):
    arquivo = open("contatos.txt", "w")
    
    for contato in lista:
        arquivo.write(f"{contato['nome']}#{contato['email']}#{contato['tel']}\n")

    arquivo.close()

# Função para carregar os contatos de um arquivo
def carregar_contatos():
    lista = []

    try:
        arquivo = open("contatos.txt", "r")

        for linha in arquivo.readlines():
            coluna = linha.split("#")
            contato = {"email": coluna[1], "nome": coluna[0], "tel": coluna[2].strip()}

            lista.append(contato)
                
        arquivo.close()

    except FileNotFoundError: 
        pass

    return lista

# Função para verificar se um contato já existe na lista
def existe_contato(lista, email):
    if len(lista) > 0:
        for contato in lista:
            if contato['email'] == email:
                return True
            
    return False

# Função para adicionar um novo contato à lista
def adicionar(lista):
    while True:
        email = input("Digite o e-mail do contato:").strip()
        if not existe_contato(lista, email):
            break
        else:
            print("Esse e-mail já foi ultilizado.")
            print("Por favor tente outro e-mail.")

    contato = {
        "email": email,
        "nome": input("Digite o nome: ").strip(),
        "tel": input("Digite o telefone: ").strip()}
    
    lista.append(contato)
    print(f"O contato {contato['nome']} foi cadastrado com sucesso")

# Função para alterar um contato existente na lista
def alterar(lista):
    print("------------  Alterar Contato  ------------")
    if len(lista) > 0:

        email = input("Digite o email do contato a ser alterado:")
        if existe_contato(lista, email):
            print("-----------------------------------------")
            print("O contato foi encontrado:")
            for contato in lista:
                if contato['email'] == email:
                    print(f"Nome:{contato['nome']}")
                    print(f"Email:{contato['email']}")
                    print(f"Telefone:{contato['tel']}")

                    contato['nome'] = input("Digite o novo nome do contato: ")
                    contato['tel'] = input("Digite o novo telefone do contato: ")
                    print("Contato alterado com sucesso")
                    break
                
        else:
            print(f"Não existe contato cadastrado no sistema com esse email: {email}")
    else:
        print("Não existe nenhum contato cadastrado no sistema.")

# Função para excluir um contato da lista
def excluir(lista):
    print("-----------  Excluir Contato  -----------")
    if len(lista) > 0:

        email = input("Digite o email do contato a ser excluído:")
        if existe_contato(lista, email):
            print("-----------------------------------------")
            print("O contato foi encontrado:")
            for i, contato in enumerate(lista):
                if contato['email'] == email:
                    print(f"Nome:{contato['nome']}")
                    print(f"Email:{contato['email']}")
                    print(f"Telefone:{contato['tel']}")

                    del lista[i]

                    print("O contato foi excluído com sucesso!")
            
        else:
            print(f"Não existe contato cadastrado no sistema com esse email {'email'}")
    else:
        print("Não existe nenhum contato cadastrado no sistema.")

# Função para buscar um contato na lista
def buscar(lista):
    print("------------  Buscar Contato  ------------")
    if len(lista) > 0:

        email = input("Digite o email do contato a ser encontrado:")
        if existe_contato(lista, email):
            print("-----------------------------------------")
            print("O contato foi encontrado:")
            for contato in lista:
                if contato['email'] == email:
                    print(f"Nome:{contato['nome']}")
                    print(f"Email:{contato['email']}")
                    print(f"Telefone:{contato['tel']}")
            
        else:
            print(f"Não existe contato cadastrado no sistema com esse email {'email'}")
    else:
        print("Não existe nenhum contato cadastrado no sistema.")

# Função para listar todos os contatos da lista
def listar(lista):
    print("------------ Listar Contatos ------------")
    if len(lista) > 0:
        for i, contato in enumerate(lista):
            print(f"Contato:{i+1}")
            print(f"Nome:{contato['nome']}")
            print(f"Email:{contato['email']}")
            print(f"Telefone:{contato['tel']}")
            print("-----------------------------------------")
        print(f"Quantidade de contatos: {len(lista)}")
    else:
        print("Não existe nenhum contato cadastrado no sistema.")


# Função para adicionar favoritos a lista
def adicionar_favorito(lista, email):
    for contato in lista:
        if contato['email'] == email:
            contato['favorito'] = True
            print(f"Contato {contato['nome']} adicionado aos favoritos.")
            return
    print("Não foi possível encontrar o contato.")


# Função para remover favoritos da lista
def remover_favorito(lista, email):
    for contato in lista:
        if contato['email'] == email:
            if contato.get('favorito'):
                del contato['favorito']
                print(f"Contato {contato['nome']} removido dos favoritos.")
                return
            else:
                print(f"O contato {contato['nome']} não está na lista de favoritos.")
                return
    print("Não foi possível encontrar o contato.")

# Função para listar os favoritos
def listar_favoritos(lista):
    favoritos = [contato for contato in lista if contato.get('favorito')]
    if favoritos:
        print("------------ Listar Favoritos ------------")
        for i, contato in enumerate(favoritos):
            print(f"Contato:{i+1}")
            print(f"Nome:{contato['nome']}")
            print(f"Email:{contato['email']}")
            print(f"Telefone:{contato['tel']}")
            print("-----------------------------------------")
        print(f"Quantidade de favoritos: {len(favoritos)}")
    else:
        print("Não existem contatos favoritos.")

# Função principal para controlar o fluxo do programa
def principal():
    lista = carregar_contatos()

    while True:
        print("----------- Agenda Telefônica -----------")
        print("1 - Adicionar contato")
        print("2 - Alterar contato")
        print("3 - Excluir contato")
        print("4 - Buscar contato")
        print("5 - Listar contatos")
        print("6 - Listar favoritos")
        print("7 - Marcar contato como favorito")
        print("8 - Remover contato dos favoritos")
        print("9 - Sair")
        opção = int(input("Escolha uma opção: "))

        if opção == 1:
            adicionar(lista)
            salvar_contatos(lista)

        elif opção == 2:
            alterar(lista)
            salvar_contatos(lista)

        elif opção == 3:
            excluir(lista)
            salvar_contatos(lista)

        elif opção == 4:
            buscar(lista)

        elif opção == 5:
            listar(lista)

        elif opção == 6:
            listar_favoritos(lista)

        elif opção == 7:
            email = input("Digite o email do contato a ser marcado como favorito: ")
            adicionar_favorito(lista, email)

        elif opção == 8:
            email = input("Digite o email do contato a ser removido dos favoritos: ")
            remover_favorito(lista, email)

        elif opção == 9:
            print("Saindo do programa")
            break

        else:
            print("Opção inválida. Por favor, tente novamente.")

principal()
