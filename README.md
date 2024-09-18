# Smart-stock-gti-
class Estoque:
    def __init__(self):
        self.estoque = {}

    def adicionar_ferramenta(self, nome, quantidade):
        if nome in self.estoque:
            self.estoque[nome] += quantidade
        else:
            self.estoque[nome] = quantidade
        print(f'Adicionado {quantidade} de {nome}. Total: {self.estoque[nome]}')

    def remover_ferramenta(self, nome, quantidade):
        if nome in self.estoque:
            if self.estoque[nome] >= quantidade:
                self.estoque[nome] -= quantidade
                print(f'Removido {quantidade} de {nome}. Total restante: {self.estoque[nome]}')
                if self.estoque[nome] == 0:
                    del self.estoque[nome]
            else:
                print(f'Quantidade insuficiente de {nome} para remoção.')
        else:
            print(f'{nome} não encontrado no estoque.')

    def visualizar_estoque(self):
        if not self.estoque:
            print('O estoque está vazio.')
        else:
            print('Estoque de ferramentas:')
            for nome, quantidade in self.estoque.items():
                print(f'- {nome}: {quantidade}')


def main():
    estoque = Estoque()

    while True:
        print("\nEscolha uma opção:")
        print("1. Adicionar ferramenta")
        print("2. Remover ferramenta")
        print("3. Visualizar estoque")
        print("4. Sair")

        opcao = input("Digite o número da opção: ")

        if opcao == '1':
            nome = input("Digite o nome da ferramenta: ")
            quantidade = int(input("Digite a quantidade: "))
            estoque.adicionar_ferramenta(nome, quantidade)
        elif opcao == '2':
            nome = input("Digite o nome da ferramenta: ")
            quantidade = int(input("Digite a quantidade a remover: "))
            estoque.remover_ferramenta(nome, quantidade)
        elif opcao == '3':
            estoque.visualizar_estoque()
        elif opcao == '4':
            print("Saindo...")
            break
        else:
            print("Opção inválida. Tente novamente.")

if __name__ == "__main__":
    main()
