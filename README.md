# SmartAgent
import random
import matplotlib.pyplot as plt

class GameAgent:
  def __init__(self, secret_number, max_attempts=5):
    self.secret_number = secret_number
    self.max_attempts = max_attempts
    self.attempts = 0
    self.state = "Esperando tentativa"
    self.history = []

  def GameAgent(self):
    print("Bem-vindo ao jogo do Número Secreto!")
    dificuldade= int(input("Escolha uma dificuldade: Fácil(1), Normal(2), Difícil(3)"))
    if dificuldade ==1:
      max_attempts = 10
    elif dificuldade ==2:
      max_attempts = 7
    elif dificuldade ==3:
      max_attempts = 5

  def make_guess(self , guess):
    self.attempts += 1
    self.history.append(guess)

    if guess == self.secret_number:
      self.state = "Acertou!"
      return f"Parabéns! Você acertou o número em {self.attempts} tentativa(s)!"
    elif self.attempts >= self.max_attempts:
      self.state = "Fim do jogo."
      return f"Game Over! O número era {self.secret_number}."
    elif guess < self.secret_number:
      self.state = "Tentativa errada (muito baixo)."
      return "O número é maior. Tente novamente."
    else:
      self.state = "Tentativa errada (muito alto)."
      return "O número é menor. Tente novamente."

  

   
  agent = GameAgent(secret_number=random.randint(1, 100))
  agent.GameAgent()

  while agent.state not in ["Acertou!", "Fim do jogo."]:
     guess = int(input("Digite um número: "))
     print(agent.make_guess(guess))

  import matplotlib.pyplot as plt
  def plot_attempts(agent):
    plt.figure(figsize=(8,5))
    plt.plot(range(1, len(agent.history) + 1), agent.history, marker='o', linestyle ='-')
    plt.axhline(y=agent.secret_number, color='r', linestyle ='--', label ='Número Secreto')
    plt.xlabel("Tentativas")
    plt.ylabel("Valor do Palpite")
    plt.title("Evolução das Tentativas do Jogador")
    plt.legend()
    plt.show()
