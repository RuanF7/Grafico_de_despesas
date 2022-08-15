from sklearn.linear_model import LinearRegression
import numpy as np
import matplotlib.pyplot as plt

class Grafico:  
  def __init__(self, lista_despesas):
    self.lista_despesas=lista_despesas
    self.imprimir_graficos()

  def padrao_do_grafico(self):
    plt.xlabel('Dia')
    plt.ylabel('Despesa em Reais(R$)')
    plt.title('Gráficos de Despesas')    

  def imprimir_graficos(self):
    self.padrao_do_grafico()
    for despesa in self.lista_despesas:
      mLista = despesa.dicionario.items()
      cor = despesa.cor
      nome = despesa.nome
      x, y = zip(*mLista)
      plt.plot(x, y, label = nome, marker='o', 
               markerfacecolor='blue', 
               markersize=12, 
               color=cor, 
               linewidth=4)
    plt.legend()
    plt.show()

  def regressao_linear(self, id_grafico):
    despesa = self.lista_despesas[id_grafico]
    mLista = despesa.dicionario.items()    
    cor = despesa.cor
    nome = despesa.nome
    dias, valores = zip(*mLista)
    dias = np.array(dias)
    valores = np.array(valores)
    dias = dias.reshape(-1, 1)
    valores = valores.reshape(-1, 1)
    regr = LinearRegression()
    regr.fit(X=dias, y=valores)
    plt.plot(dias, regr.predict(dias), 
             color='blue',
             label = "Regressão Linear")

    x, y = zip(*mLista)
    plt.plot(x, y, label = nome+str(" - original"), 
             marker='o', 
             markerfacecolor='olive', 
             markersize=12, 
             color=cor, 
             linewidth=4)

    plt.legend()
    plt.show()


class Despesas:
    def __init__(self, dicionario, cor, nome):
        self.dicionario = dicionario
        self.cor=cor
        self.nome = nome
        
maio = Despesas({1:13.99,5:10.76,7:9.00,17:101.09,20:0.50,29:300.00},'skyblue','maio')
junho = Despesas({1:100.00,3:150.98,5:500.00,7:20.21,15:15.87,20:17.00,27:0.88},'red','junho')
julho = Despesas({1:140.00,3:1.00,5:300.90,7:12.23,10:30.00,15:21.50,20:270.00,27:200.99},'olive','julho')
lista_despesas = [maio,junho,julho]

grafico = Grafico(lista_despesas)

id_mes = 0 #mês de maio
grafico.regressao_linear(id_mes)

id_mes = 1 #mês de junho
grafico.regressao_linear(id_mes)

id_mes = 2 #mês de julho
grafico.regressao_linear(id_mes)
