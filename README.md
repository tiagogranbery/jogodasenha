# jogodasenha
import random
def gerar_codigo():
    codigo = []
    for i in range(4):
        codigo.append(random.randint(1, 6))
    return codigo

def fazer_jogada():
    jogada = []
    for i in range(4):
        numero = int(input("Insira um número (entre 1 e 6): "))
        while numero < 1 or numero > 6:
            numero = int(input("Número inválido. Insira um número (entre 1 e 6): "))
        jogada.append(numero)
    return jogada

def obter_dica(codigo, jogada):
    posicao_correta = 0
    posicao_errada = 0

    for i in range(4):
        if jogada[i] == codigo[i]:
            posicao_correta = posicao_correta + 1

        if jogada[i] == codigo:
            posicao_errada = posicao_errada + 1
    return posicao_correta, posicao_errada

def jogar():
    codigo_secreto = gerar_codigo()
    tentativas = 10
    print(codigo_secreto)
    while tentativas > 0:
        print("Você tem :", tentativas, "tentativas para acertar o código:")
        jogada = fazer_jogada()
        posicao_correta, posicao_errada = obter_dica(codigo_secreto, jogada)
        print("Números corretos e em posição correta:", posicao_correta)
        print("Números corretos e em posição errada:", posicao_errada)
        if posicao_correta == 4:
            print("Parabéns! Você adivinhou o código secreto!")
            return
        tentativas = tentativas - 1
    print("Você excedeu o número de tentativas. O código secreto era:", codigo_secreto)


jogar()
