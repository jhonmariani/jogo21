import random

# Função para criar um baralho de cartas
def criar_baralho():
    baralho = []
    for valor in range(1, 14):  # Valores de 1 (Ás) a 13 (Rei)
        for _ in range(4):  # Cada valor aparece 4 vezes
            baralho.append(valor)
    random.shuffle(baralho)
    return baralho

# Função para calcular a pontuação
def calcular_pontuacao(mao):
    pontuacao = 0
    for carta in mao:
        if carta > 10:  # Valete, Dama, Rei valem 10 pontos
            pontuacao += 10
        elif carta == 1:  # Ás pode valer 1 ou 11 pontos
            if pontuacao + 11 > 21:
                pontuacao += 1
            else:
                pontuacao += 11
        else:
            pontuacao += carta
    return pontuacao

# Função para jogar uma rodada
def jogar_rodada(baralho, fichas):
    mao_jogador = [baralho.pop(), baralho.pop()]
    mao_casa = [baralho.pop(), baralho.pop()]

    print(f"Você tem {fichas} fichas.")
    print("Bem-vindo ao jogo de 21! O objetivo é chegar o mais próximo possível de 21 pontos sem ultrapassar.")

    while True:
        print(f"Sua mão: {mao_jogador}, Pontuação: {calcular_pontuacao(mao_jogador)}")
        if calcular_pontuacao(mao_jogador) > 21:
            print("Você estourou! A casa vence.")
            return False

        escolha = input("Deseja pegar outra carta? (s/n): ").lower()
        if escolha == 's':
            mao_jogador.append(baralho.pop())
        else:
            break

    while calcular_pontuacao(mao_casa) < 17:
        mao_casa.append(baralho.pop())

    print(f"Mão da casa: {mao_casa}, Pontuação: {calcular_pontuacao(mao_casa)}")
    if calcular_pontuacao(mao_casa) > 21 or calcular_pontuacao(mao_jogador) > calcular_pontuacao(mao_casa):
        print("Você vence!")
        return True
    else:
        print("A casa vence.")
        return False

# Função principal para jogar o jogo
def jogar():
    fichas = 1000  # Quantidade inicial de fichas
    while True:
        baralho = criar_baralho()
        if jogar_rodada(baralho, fichas):
            fichas += 10  # Ganha 10 fichas se vencer
        else:
            fichas -= 10  # Perde 10 fichas se perder

        if fichas <= 0:
            print("Você ficou sem fichas! Fim de jogo.")
            break

        jogar_novamente = input("Deseja jogar novamente? (s/n): ").lower()
        if jogar_novamente != 's':
            break


    jogar()
