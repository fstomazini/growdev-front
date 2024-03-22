Skip to content
fstomazini
/
growdev-front

Type / to search

Code
Issues
Pull requests
Actions
Projects
Wiki
Security
Insights
Settings
Commit
Add Comments.md
 main
fstomazini committed 4 minutes ago 
1 parent 68880ff
commit ee83e9a
Showing 1 changed file with 33 additions and 0 deletions.
 33 changes: 33 additions & 0 deletions33  
sistema-de-matricula/COMMENTS.md
@@ -0,0 +1,33 @@
Desafio Felipe Schimidt Tomazini


# arquitetura 

Decidi por serguir um padrão CDP (Component Driver Pattern)para o front end comunmente usado em conjunto com a tecnologia Vuejs

para a implementação do backend decidi seguir um padrão MVC, que por questões de tempo e simplicidade de uma primeira versão do backend acabou por ficar bastante sucinto.

para comunicação entre o backend e fronten foi usado um padrão rest, com chamadas http .

Foi utilizado um banco SQL Postgresql

# Projeto
    Foram utilizadas no projeto poucas bibliotecas externas alem dos requisitos basicos solicitados foram utilizadas no frontend a biblioteca axios e no backend express e nodemon

 # Melhorias

    por questões de tempo não foi possivel refinar os processos descritos
    houve tambem um pequeno bug na atualização dos request reativos do vue

# Pendencias 

    Todas as funcionalidades do backend foram concluidas, no entanto as chamadas não foram devidamente listadas no front por questões de tempo

# Se eu tivesse mais tempo

Se tivesse mais tempo, focaria primeiro em melhorar a usabilidade das funcoes core e melhorar as funcoes de pesquisa no lado do backend, tambem implementaria autênticação JWT que apesar de ser de relativa facil implementação não era uma dos requisitos necessarios

# links uteis 

Repositorio frontend : https://github.com/fstomazini/growdev-front
Repositorio backend: https://github.com/fstomazini/growdev-back
0 comments on commit ee83e9a
@fstomazini
Comment
 
Leave a comment
 
 You’re receiving notifications because you’re watching this repository.
Footer
© 2024 GitHub, Inc.
Footer navigation
Terms
Privacy
Security
Status
Docs
Contact
Manage cookies
Do not share my personal information
Add Comments.md · fstomazini/growdev-front@ee83e9a 
