# introml

Esse projeto irá analisar o desempenho de alguns algoritmos de machine learning 
aplicados a um problema de classificação de uma empresa de delivery de comidas. 

## Apresentação do problema

O problema está relacionado com uma campanha a ser realizada pela companhia.
A empresa deseja prever se seus consumidores irão aceitar ou não uma oferta 
a ser realizada em uma próxima campanha. 

Os dados do problema, assim como uma solução base do autor Nailson (que será usada para fins de
comparação), podem ser encontrados [aqui](https://github.com/nailson/ifood-data-business-analyst-test).

O tipo dos dados pode ser visto pelo dicionário de dados a seguir (tabela extraída do repositório de [Nailson](https://github.com/nailson/ifood-data-business-analyst-test/blob/master/dictionary.png)):
![alt text](https://github.com/pcelin/introml/blob/main/dictionary.png)

A implementação dos algoritmos foi feita em python, usando principalmente a biblioteca scikit-learn.
Bibliotecas auxiliares foram usadas, como pandas, numpy, matplotlib e time, para avaliar o tempo de 
treinamento de modelos mais demorados.

Do conjunto de dados, 40% ficaram reservados para teste, de acordo com o que foi feito pela solução base, de Nailson.
Para manter o conjunto de teste intocado, do que restou para treinamento (60%), 80% foi usado efetivamente para treinamento
dos modelos, e o resto foi usado para validação.

Os algoritmos testados foram: Regressão Logística, Support Vector Machines (SVM) e Multi Layer Perceptron (MLP).
Eles foram treinados usando as features padronizadas e não padronizadas, com exceção do MLP que só foi treinado com 
features padronizadas.

## Breve análise exploratória

A feature AcceptedCmpOverall parece ser relevante, segundo modelo de Nailson. A visualização de sua distribuição revela que poucas pessoas
aceitaram as campanhas:

![all text](https://github.com/pcelin/introml/blob/main/campanha.png)

A imagem abaixo mostra duas variáveis, e a classificação de cada ponto. Pontos verdes indicam que esses indivíduos aceitaram a
ultima campanha, pontos vermelhos não aceitaram:

![all text](https://github.com/pcelin/introml/blob/main/campanha_compras.png)

Pode-se observar que valores mais altos da variável AcceptedCmpOverall e mais altos de NumStorePurchases podem estar relacionados com a aceitação
da campanha.


## Principais resultados

Os algoritmos que melhor classificam o conjunto de teste foi o modelo de regressão logística sem a padronização dos dados, embora
os outros modelos tenham performance parecida.

A acurácia da solução base foi melhorada 87% para 89%.

Importante destacar que caso seja importante a minimização de falsos negativos ou falsos positivos, alguns algoritmos serão preferíveis.
Se esse for o caso, matrizes de confusão encontradas no código `projeto_ml.ipynb` podem mostrar o melhor modelo.  

Uma análise foi feita acerca das features com maior importância de cada modelo (com exceção do MLP)
A tabela a seguir mostra a ordem decrescente de importância das 4 features de maior peso em cada modelo:
|Random Forest     |RegLog            |SVM               |
|------------------|------------------|------------------|
|Recency           |Recency           |NumStorePurchases |
|Customer_Days     |NumStorePurchases |Recency           |
|AcceptedCmpOverall|Customer_Days     |Customer_Days     |
|Income            |Teenhome          |Teenhome          |

Destaca-se então a importância de variáveis como Recency, NumStorePurchases e Customer_Days, para a manutenção dessa base de dados.

**Importante**: no código a tabela é exibida com dados da regressão logística e SVM com features padronizadas. Entretanto, a importância 
das features é a mesma quando não realizada a padronização das variáveis.

# Autor
* Marcelo Paiva
