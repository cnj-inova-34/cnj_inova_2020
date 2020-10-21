# ***SOLUÇÃO PREDITIVA - TEMPO DE DECISÃO***

**Equipe**: cnj_inova_34  
**Membros**
- Thiago Gontijo
- Henrique Bona
- Flávio Siqueira

## PROBLEMA A SER SOLUCIONADO
### **RELATO 03: CIDADÃO - AÇÃO NA VARA DE FAMÍLIA**
Josué, 31 anos, sem curso superior e desempregado, ajuizou uma ação na Vara de Família para ter a guarda de sua filha de 2 anos, Sara.
Está muito preocupado porque **NÃO SABE QUANTO TEMPO SEU PROCESSO IRÁ DURAR** e tem medo de que acabe perdendo a infância da sua única filha brigando
na Justiça. Josué gostaria de ter uma **PREVISAO DE QUANTO TEMPO SEU PROCESSO IRÁ LEVAR PARA TER UMA DECISÃO**.
Josué acha muito difícil encontrar informações na internet sobre o seu processo e quando o encontra não consegue entender o real conteúdo do que está escrito ali.
Tudo o que Josué quer é ter seu problema resolvido dentro de um período de tempo razoável.

### **RELATO 04: ADVOGADA – PROCESSO** 
Mariana, 30 anos, é advogada. Quando vai iniciar (1ª INSTÂNCIA) um processo judicial para seus clientes sempre se vê “envergonhada” ao dizer
que **NÃO SABE DIZER QUANDO ESSE TERÁ RESOLUÇÃO**.
Ao cadastrar os novos processos, tem muita dificuldade com as tabelas unificadas, que são muito complexas.
Vê sempre seus colegas falando de artifícios e artimanhas a serem aplicados na hora do cadastramento para terem maior celeridade.
Mariana quer exercer sua profissão da melhor forma possível, mas às vezes erra no cadastramento por não entender como fazê-lo.
Mariana tem tanto trabalho que frequentemente insere dados equivocados por engano e não percebe.
Gostaria que o próprio sistema a ajudasse a sanear esses equívocos.


## DESCRIÇÃO DA SOLUÇÃO PROPOSTA

A **SOLUÇÃO PREDITIVA - TEMPO DE DECISÃO** apresenta painéis inovadores que permitem, na primeira instância da Justiça Federal: 
1. **ANÁLISE PREDITIVA | PREVISÃO DE TEMPO PARA DECISÃO**: predição do tempo estimado para julgamento de cada processo - com ou sem resolução do mérito -, e 
2. **ESTATÍSTICAS | TEMPO MÉDIO DA DECISÃO**: análise estatística dos tempos médios de tramitação processual, desde o ajuizamento até a decisão final.

### Painel ANÁLISE PREDITIVA | PREVISÃO DE TEMPO PARA DECISÃO
Permite que o usuário tenha conhecimento do tempo estimado para o julgamento do processo na primeira instância. 
Previsão que é realizada a partir do cotejo personalizado dos dados processuais de cada caso com os metadados constantes da base de dados do DataJud.
São consideradas como variáveis as informações de Tribunal, Classe Processual, Juízo, Assunto Principal e Assuntos Complementares. 

### Painel ESTATÍSTICAS | TEMPO MÉDIO DA DECISÃO
Plataforma dinâmica, simples e intuitiva, que possibilita ao usuário uma experiência prática e efetiva sobre o tempo de tramitação processual
até a decisão, na primeira instância da Justiça Federal, com ou sem mérito.


## ESCOPO DA SOLUÇÃO

**EMBORA HAJA REDUÇÃO DE ESCOPO DO PONTO DE VISTA DE TRIBUNAIS ANALISADOS, A SOLUÇÃO PROPOSTA FOI CONSTRUÍDA TENDO EM MENTE SER APLICADA - COM POUCA
EVOLUÇÃO - PARA TODOS OS TRIBUNAIS.**

Devido a quantidade de dados disponibilizados para o CNJ INova, e o tempo disponibilizado para construir a solução, foi necessário definir um
escopo para o trabalho. No nosso caso, optamos por trabalhar com a Justiça Federal.

Devido a não estar disponível a informação de quando um determinado processo deu entrada na 2ª instância, então foi necessário limitar a solução
apenas a 1ª instância. Todavia, a solução apresentada funciona para ambas as instância, apenas não existindo, na massa de dados do DataJud, as
informações necessárias para o cálculo dos indicadores de tempo de tramitação do processo na 2ª instância.

Pelo mesmo motivo de limitação de tempo, optou-se por fazer a análise dos dados com base no "assunto principal" do processo. Todavia, não há perdas
significativas, visto que os "assuntos complementares" podem ser derivados a partir do "assunto principal".


## PRINCIPAIS MÉTRICA DA SOLUÇÃO
A métrica utilizada na solução proposta e a **média de tempo decorrido entre o ajuizamento do processo e a primeira decisão relevante do mesmo**.

Ressalta-se a importância da **relevância da decisão**, visto que várias decisões são tomadas ao longo do processo. Sendo várias delas relacionadas aos trãmites processuais, e não ao julgamento do processo em si.

Sendo que o tempo até o efetivo julgamento, e decisão relacionada, é o que importa para as partes envolvidas no processo.


## ARQUITETURA DA SOLUÇÃO E FLUXO DE DADOS
A solução proposta exige o cálculo do indicador de tempo transcorrido desde ajuizamento do processo até o julgamento e decisão do mesmo.

Para tal, os dados provenientes do DataJud são sucessivamente tratrados, utilizando notebooks jupyter e linguagem python.

O processo de extração dos dados é descrito pela figura abaixo:
![extracao_dados](https://github.com/cnj-inova-34/cnj_inova_2020/blob/main/imagens/cnj_inova_extracao_dados.png?raw=true)


Feita a extração dos dados, segue a transformação dos mesmos:
![transformacao_dados](https://github.com/cnj-inova-34/cnj_inova_2020/blob/main/imagens/cnj_inova_tranformacao_dados.png?raw=true)


Após da extração, transformação - permeada pela análise dos dados - produz-se o indicador desejado. Posteriormente, a visualização do mesmo para o cliente é
realizado através de painéis QlikSense:
![interface_usuario](https://github.com/cnj-inova-34/cnj_inova_2020/blob/main/imagens/cnj_inova_interface_usuario.png?raw=true)


## INSTRUÇÕES DE USO
**Instruções detalhadas de acesso ao ambiente de teste estão no arquivo "acesso_ambiente_teste_equipe_34.pdf"**

A primeira parte da solução é executada em Jupyter Notebooks, esses hospedados no Microsoft Azure.

Link para o ambiente JupiterLab hospedado no Azure: https://data-comp.brazilsouth.instances.azureml.ms/lab

O Jupyter Notebook alcançou grande sucesso, entre outros méritos, pelo fato de permitir permear o código com explicações sobre o mesmo. Nesse sentido, os notebooks são auto-explicativos, e apresentados na ordem que devem ser executados.


A camada de visualização da solução, interface com o usuário, foi desenvolvida no QlikSense. Por sua vez, o Qlik é famoso pela sua fácil utilização e amigabilidade com o usuário.

Link para o ambiente QlikSense Cloud: https://vc89vy4bxhgztcd.us.qlikcloud.com/

Pensamos que, se precisar de muita explicação, a interface não é boa e intuitiva o suficiente. Mas fica uma dica: **no QlikSense, quase tudo que você vê na tela pode ser clicado, e a seleção refletirá os dados na tela**. 

**Boa diversão!!!**


## LICENÇAS UTILIZADAS
O Jupyter Notebook está hospedado no Microsoft Azure para conveniência dos jurados, os quais contarão com uma solução funcional sem nenhuma necessidade de configuração local. De forma que não há nenhuma licença envolvida nessa etapa.

No ambiente de produção, cabe ao cliente escolher a plataforma onde desejará hospedar a solução, podendo ser rodado em qualquer ambiente operacional, inclusive em computadores locais.

Com relação a interface do usuário, que roda no QlikSense, foi escolhido pois o CNJ possui licenças para o utilização do mesmo, e pode usar essa tecnologia caso assim o deseje.

Todavia, o motivo principal da escolha foi o curto tempo disponível para desenvolvimento. Com a intenção de entregar a melhor interface possível, no tempo disponível, o QlikSense se mostrou uma boa escolha.

Por fim, e caso o licenciamento se mostre um empecilho, sugere-se a evolução da solução e construção de uma interface com o usuário baseada em HTML5 e livre de ônus de licenciamento.


## ÁREAS DE CONHECIMENTO E TÉCNICAS ENVOLVIDAS
Solução multidisciplinar que envolve, entre outras, as seguintes competências:
- Análise de dados;
- Business Intelligence - BI;
- Ciências de Dados;
- Inteligência Artificial;
- Python;
- Jupyter Notebooks;
- QlikSense;
- Inteligência negocial na área de Direito.


## EVOLUÇÕES SUGERIDAS

1. Portar a solução de Jupyter Notebook para um serviço REST, de forma que os arquivos de dados JSON possam ser consumidos continuamente, e alimentar a base de indicadores em tempo real;
2. Ampliar o cálculo de dados para todos os tribunais disponíveis na base do DataJud;
3. Caso haja problemas de licenciamento, evoluir a interface QlikSense para tecnologias como HTML5
4. Melhorar a qualidade dos dados.
