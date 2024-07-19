<!-- Improved compatibility of back to top link: See: https://github.com/othneildrew/Best-README-Template/pull/73 -->
<a name="readme-top"></a>
<!--
*** Thanks for checking out the Best-README-Template. If you have a suggestion
*** that would make this better, please fork the repo and create a pull request
*** or simply open an issue with the tag "enhancement".
*** Don't forget to give the project a star!
*** Thanks again! Now go create something AMAZING! :D
-->


[![LinkedIn][linkedin-shield]][linkedin-url]



<!-- PROJECT LOGO -->
<br />
<div align="center">
<h3 align="center">Modelo de Identificação de Fraude de Cartão de Crédito</h3>
</div>



<!-- TABLE OF CONTENTS -->
<details>
  <summary>Índice</summary>
  <ol>
    <li>
      <a href="#about-the-project">Sobre o projeto</a>
      <ul>
        <li><a href="#etl">Análise e Tratamento dos dados</a></li>
      </ul>
      <ul>
        <li><a href="#ml">Modelo de Machine Learning</a></li>
      </ul>
      <ul>
        <li><a href="#conclusion">Conclusão</a></li>
      </ul>
      <ul>
        <li><a href="#built-with">Tecnologia utilizada</a></li>
      </ul>
    </li>
    <li><a href="#contact">Contato</a></li>
  </ol>
</details>



<!-- ABOUT THE PROJECT -->
## Sobre o projeto

Este projeto tem como objetivo a criação de um modelo de machine learning para identificar fraudes em cartão de crédito, a base de dados utilizada está disponibilizada no site kaggle, esta base contém apenas variáveis numéricas, resultado da transformação PCA (Análise de componentes principais), devido a questões de confidencialidade, não podemos fornecer os recursos originais e mais informações básicas sobre os dados.

Para este projeto o foco será na identificação de fraudes o mais precisamente possível mantendo o erro das transações não fraude perto dos 10-15%.

Base de dados utilizada: [https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud](https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud)

Informações da base:
* 'Time' (tempo): contém os segundos decorridos entre cada transação e a primeira transação no conjunto de dados.
* 'Amount' (valor): é o valor da transação.
* 'Class' (classe): é a variável de resposta e assume valor 1 em caso de fraude e 0 caso contrário.
* Características V1, V2, … V28 são os principais componentes obtidos com PCA.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- ABOUT THE PROJECT -->
### Análise e Tratamento dos dados

Nesta etapa, carreguei a base de dados retirada do kaggle, e iniciei a análise, em busca de verificar se haviam dados faltantes, dados com a tipagem incorreta, fiz as correções necessárias, alterei as colunas "Time" e "Amount" para que tivessem apenas valores entre 0 e 1 e por fim verifiquei também a proporção dos dados, como podemos observar no gráfico abaixo, a grande maioria dos dados presente na base eram de transações não fraude, desta forma posteriormente será feito também o balanceamento desta base.

![Grafico Screen Shot][etl-screenshot]

Após as alterações feitas na base realizei a separação dos dados em treino e teste, para podermos treinar e testar adequadamente nosso modelo.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

### Modelo de Machine Learning

Após testar diversos tipos de modelos com parâmetros diferentes, o modelo final escolhido foi o de Regressão Logística, utilizando parâmetros 'C' = 0.001 e 'solver' = 'liblinear', a técnica de balanceamento escolhida foi o Random Under Sampling:

![UnderSampling Screen Shot][under-screenshot]
![RL Screen Shot][rlr-screenshot]

<p align="right">(<a href="#readme-top">back to top</a>)</p>

### Conclusão

Para este modelo, o objetivo que tive foi manter o número de erro nas transações fraude o menor o possível mantendo também uma proporção aceitávei para as transações não fraude.

Desta forma o modelo que será utilizado será o modelo de Regressão Logística, utilizando o RandomUnderSampling e com os seguintes parâmetros:

* 'C': 0.001
* 'solver': 'liblinear'
* 
Este modelo obteve como desempenho a seguinte matriz de confusão:

* Das 93.825 transações não fraude, o modelo identificou 81.700 como não fraude e 12.125 como fraude, desta forma, aproximadamente 12,9% dos dados tiveram a previsão incorreta.
* Das 162 transações fraude, o modelo identificou corretamente 152 como fraude e 10 como não fraude, desta forma, aproximadamente 6,17% dos dados tiveram a previsão incorreta.
* 
Para este projeto escolhi como objetivo priorizar o "recall", que é referente as transações fraude, este modelo teve um recall de aproximadamente 93%, porém seria possível buscar outras formas de priorizar de acordo com as necessidades, podendo buscar uma melhor precisão, um modelo que buscasse o melhor para ambos, tudo dependendo da necessidade do projeto.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

### Tecnologia utilizada 

* Python
  * Pandas (Extração e tratamento dos dados
  * Matplotlib (Visualização gráfica)
  * Seaborn (Visualização gráfica)
  * Scikit-learn (Criação do modelo de machine learning e métricas de avaliação)
  * imblearn (Técnicas de balanceamento da base de dados)
* Jupyter notebook

<p align="right">(<a href="#readme-top">back to top</a>)</p>


<!-- CONTACT -->
## Contato

Leonardo Hideki Itihara - leohi1@hotmail.com - (11)95983-3437

Project Link: [https://github.com/leohideki/modelo_previsao_fraude](https://github.com/leohideki/modelo_previsao_fraude)

<p align="right">(<a href="#readme-top">back to top</a>)</p>



<!-- MARKDOWN LINKS & IMAGES -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->
[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg?style=for-the-badge&logo=linkedin&colorB=555
[linkedin-url]: https://linkedin.com/in/leonardo-itihara
[etl-screenshot]: static/images/screenshot.png
[rl-screenshot]: static/images/screenshot2.png
[under-screenshot]: static/images/screenshot3.png
