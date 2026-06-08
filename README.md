# VerificaMalha
Poderia ajustar os arquivos do repositorio para atingir o objetivo abaixo? 

Com base nos arquivos desse repositório, estive tentando fazer um projeto que produzisse arquivos html onde eu consiga gerenciar restrições de malha da Cargolux. Eu baixaria esse arquivo de DayRep (aqui definido no repositório como um arquivo de exemplo chamado “DayRep_Sample”) para dias específicos e gostaria de gerar avisos e alertas para situações específicas que vou listar a seguir. A ideia é rodar na minha máquina, assim as instruções em html ficariam em uma pasta local no computador do usuário. Abaixo listo as instruções em html que gostaria que vc produzisse: 

1. Com base no arquivo DayRep_Sample no repositorio, a ideia é organizar os voos em linha do tempo, colocando a matrícula, data e hora em ordem cronológica, assim saberá quando voo anterior e sucessor de cada etapa. Esse item seria definido pelo Index.html, subindo o arquivo da malha. 

2. Para produzir alertas e avisos, o arquivo restricoes.html deveria armazenar e gerenciar as restrições de malha. Esse arquivo deveria ter uma lista completa de cadastro para identificar eventos na DayRep. Deria ser capaz de identificar:  

a) Restriction Type (already in file restricoes.html),  

b) ARPT_IATA_Arr (based on DayRep),  

c) ARPT_IATA_Orig (based on DayRep),  

d) Weekday (based on DayRep),  

e) Day (based on DayRep),  

f) Month (based on DayRep),  

g) Year (based on DayRep),  

h) Init_Hour1,  

i) End-Hour1,  

j) Init_Hour2,  

k) End-Hour2,  

l) Init_Hour3,  

m) End-Hour3,  

n) Fleet_Type (based on DayRep). Usar mesmos nomes de variaveis disponiveis no campo “AC” de DayRep,  

o) Max Delay Time (based on flight segments). Deve ser calculado pelo DayRep em ETA menos ETD ou STA menos STD (caso os campos ETA ou ETD nao esteja presentes). Converter os horarios em datas completas para facilitar os calculos,  

p) Max Ground Time (based on flight segments). O Ground Time Estimado deve ser calculado pelo DayRep em ETA menos ETD ou STA menos STD (caso os campos ETA ou ETD nao esteja presentes). Converter os horarios em datas completas para facilitar os calculos, 

q) Min Crew Composition (based on DayRep). O actual crew composition esta no campo “Crew #” presente no DayRep. 

Quando as condicoes acima forem encontrada na DayRep, o resultado deveria ser encontrado em analise.html (item5 abaixo).  

A logica de conjuncao das condicoes acima deveria ser “e”, ou seja, quando as conjuncoes forem atingidas o alerta deveria ser gerado. A excecao seriam os itens de hora, que poderiam ter a logica “ou” se encontados: 

h) Init_Hour1,  

i) End-Hour1,  

ou 

j) Init_Hour2,  

k) End-Hour2,  

ou 

l) Init_Hour3,  

m) End-Hour3,  

3. As referencias a “aeronaves.html” podem ser removidas e tudo deve ser concentrado em restricoes.html. 

4. As referencias a “aeronaves.html” podem ser removidas e tudo deve ser concentrado em restricoes.html. 

5. Tendo o upload do arquivos DayRep e as telas de cadastro, gostaria de ter uma página html para listar os eventos cadastrados na tela de “Restriction Insertions” e que possam ser identificados na malha DayRep. Seria o arquivo analise.html no repositorio.  

6. A visualizacao de analise.html deve ser mantida ate que um novo DayRep seja inserido para analise.  

7. A restricoes em restricoes.html devem ser salvas de forma a terem uma data de validade e possibilidade de exclusao e edicao. 
