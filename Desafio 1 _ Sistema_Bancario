menu = """
[1] Depositar
[2] Sacar
[3] Extrato
[4] Sair


=> """

saldo = 0
limite = 500
extrato = ""
n_saques = 0
LIMITE_SAQUES = 3

def deposito(valor):
        global saldo, extrato
        if valor > 0: 
                saldo += valor
                extrato = saldo
                print ("Deposito efetuado com sucesso")
             
        else:
                print ("""O Deposito aceita apenas valores positivos, tente novamente""")
            
      
def saque(valor):
    global saldo, extrato, n_saques
    if n_saques >= LIMITE_SAQUES:
          print("Numero maximo de saques atingido")

    if valor > 500:
        print("Não é permitido saques acima de 500 mangos, tente novamente!")

    elif valor <= 0:
        print("Digite valores validos, tente novamente!")

    elif valor > saldo:
          print("Saldo indisponivel")

    elif valor <= 500:
        saldo -= valor
        extrato = saldo
        n_saques += 1
        print("Saque Efetuado com Sucesso - Retire seu dinheiro1")


while True:
    option = input(menu)
    
    if option == "1":
            print("""Deposito - Digite o valor a ser depositado""")
            x = ""
            op = int(input(x))
            deposito(op)

    elif option == "2":
         print("Saque - Digite o valor que deseja sacar")
         x =""
         op = int(input(x))
         saque(op)

    elif option == "3":
            print("Extrato")
            print(extrato if extrato else "Nenhuma movimentação realizada.")
            #print(extrato)

    elif option == "4":
         break

    else:
        print("Operacao invalida, por favor selecione a opcao desejada.")
