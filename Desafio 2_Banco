import textwrap

def menu():
    menu = """
        =============== MENU ===============
        [1] Depositar
        [2] Sacar
        [3] Extrato
        [4] Nova conta
        [5] Listar contas
        [6] Novo usuário
        [7] Sair
        \n
        => """
    return input(textwrap.dedent(menu))


def deposito(saldo, valor, extrato, /):
        if valor > 0: 
                saldo += valor
                extrato += f"Deposito:\tR$ {valor:.2f}\n"
                print ("\n === Deposito efetuado com sucesso! === ")
             
        else:
                print ("""\n @@@ O Deposito aceita apenas valores positivos, tente novamente @@@""")

        return saldo, extrato
            
      
def saque(*, saldo, valor, extrato, limite, n_saques, limite_saques):
    
        if valor > saldo:
                print("\n@@@ Saldo indisponivel!!!   @@@")

        elif valor > 500:
                print("\n@@@ Não é permitido saques acima de 500 mangos, tente novamente!  @@@")

        elif n_saques >= limite_saques:
                print("\n@@@ Numero maximo de saques atingido!  @@@")

        elif valor <= 0:
                print("\n@@@ Digite valores validos, tente novamente!   @@@")

        elif valor <= 500:
                saldo -= valor
                extrato += f"Saque:\t\tR$ {valor:2f}\n"
                n_saques += 1
                print("\n===Saque Efetuado com Sucesso - Retire seu dinheiro!! ===")

        else:
                print("\n@@@ Operacao falhou! Tente Novamente!!!")

        return saldo, extrato

def exibir_extrato(saldo, /, *, extrato):
      print("\n ================ EXTRATO ================")
      print("Nao foram realizadas movimentacoes." if not extrato else extrato)
      print(f"\n Saldo:\t\tR$ {saldo:.2f}")

def criar_usuario(usuarios):
        cpf = input("Informe o CPF (apenas numeros):  ")
        usuario = filtrar_usuario(cpf, usuarios)

        if usuario: 
                print("\n@@@ Ja existe usuario com esse CPF! @@@")
                return
        nome = input("Informe o nome completo:   ")
        data_nascimento = input("Informe a data de nascimento (dd-mm-aa):   ")
        endereco = input("Informe o endereco (logradouro, nro - bairro - cidade/sigla estado):  ")

        usuarios.append({"nome": nome, "data_nascimento": data_nascimento, "cpf": cpf, "endereco": endereco})
        print("=== Usuario criado com sucesso! ===\n")
       
def filtrar_usuario(cpf, usuarios):
        usuarios_filtrados = [usuario for usuario in usuarios if usuario ["cpf"] == cpf]
        return usuarios_filtrados[0] if usuarios_filtrados else None

def criar_conta(agencia, numero_conta, usuarios):
        
        cpf = input("Informe o CPF (apenas numeros):  ")
        usuario = filtrar_usuario(cpf, usuarios)
        
        if usuario:
                print("\n=== Conta criada com sucesso! ===")
                return {"agencia": agencia, "numero_conta": numero_conta, "usuario": usuario}
        print("\n @@@ Usuario nao encontrado, fluxo de criacao de conta encerrado!!! @@@")

def listar_contas(contas):
    for conta in contas:
        linha = f"""\
            Agência:\t{conta['agencia']}
            C/C:\t\t{conta['numero_conta']}
            Titular:\t{conta['usuario']['nome']}
        """
        print("=" * 100)
        print(textwrap.dedent(linha))


def main():
        LIMITE_SAQUES = 3
        AGENCIA = "0001"

        saldo = 0
        limite = 500
        extrato = ""
        n_saques = 0
        usuarios = []
        contas = []

        while True:
                option = menu()
                
                if option == "1":
                        valor = float(input("Deposito - Digite o valor a ser depositado: \n"))
                        saldo, extrato = deposito(saldo, valor, extrato)

                elif option == "2":
                        valor = float(input("Saque - Digite o valor a ser sacado: \n"))

                        saldo, extrato = saque(
                              saldo = saldo,
                              valor = valor,
                              extrato = extrato,
                              limite = limite,
                              n_saques = n_saques,
                              limite_saques = LIMITE_SAQUES,
                        )

                elif option == "3":
                       exibir_extrato(saldo, extrato = extrato)

                elif option == "4":
                       numero_conta = len(contas) + 1
                       conta = criar_conta(AGENCIA, numero_conta, usuarios)

                       if conta:
                               contas.append(conta)
                
                elif option == "5":
                        listar_contas(contas)

                elif option == "6":
                       criar_usuario(usuarios)

                elif option == "7":
                        break

                else:
                        print("Operacao invalida, por favor selecione a opcao desejada.")

main()
