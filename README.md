# Problema de Negócio e Solução:

**Problema de Negócio:** O Departamento de relações públicas da empresa gostaria de uma maneira mais rápida e eficiênte de monitorar o tipo de sentimentos que os clientes estão tendo com relação a seus produtos, pois o processo atual de monitoramento é muito demorado, sem nenhum tipo de automação.

**Solução proposta:** Criar um modelo de machine learning que passado o comentário o modelo possa classificar o sentimento entre negativo ou positivo.

# Bibliotecas Usadas:

* Scikit learn
* NLTK
* Pandas
* Numpy
* Seaborn
* MatPlotLib

# Técnicas de Machine Learning:

* Algoritmos de Classificação (Logistic Regression e Naive Bayes)
* Tipo de Aprendizagem: Supervisionada
* Processamento de linguagem natural
* Padronização dos dados (StandardScaler)
* Divisão de dados: Holdout

# Construção:

Após a coleta dos dados foi feita a análise exploratória e estatística para entendermos melhor o comportamento da base. Foi feita também uma nuvem de palavras para visualização das palavras mais frequentes nas avaliações

Na fase de pré-processamento foi feita a verificação de valores nulos e vazios mas não encontramos nenhum registro. Foi feita também a padronização dos dados. Foram removidas as colunas data e voto pois não seriam relevantes para a construção do modelo e gerariam ruído. Apliquei o OneHotEnconder na features categoricas da base ele transforma cada categoria da variável em uma nova coluna e preenche a linha com 0 ou 1 dependendo se o registro possui ou não a categoria, teria a opção de usar o label encoder que transforma o texto categorico em 1 número sendo números diferentes (1,2,3...) para cada texto distinto mas o algoritmo na hora da aprendizagem pode levar essa ordem em consideração o que não representa a realidade nesse caso

Para a construção do modelo de classificação, primeiro foi feito o processamento do texto, removendo stop words, pontuação e tokenizando o texto, essas três etapas foram colocadas em uma função para ser passada registro por registro na base. Aplicando o vectorizer que pega cada palavra única da base de dados e transforma em uma array com a contagem de vezes que a palavra aparece para passar ao modelo. A base foi dividida utilizando o método padrão Houldout, separei 20% dos dados para teste sendo que dos 80% de treino 20% foram selecionados para validação para evitarmos vazamento de dados. Foram Feitos Testes com outros tipos de classificadores mas o Naive Bayes e o Logistic Regression apresentaram melhores resultados. O modelo escolhido para produção foi o Naive Bayes.
