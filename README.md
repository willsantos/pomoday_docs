
# Documentação
Documentação para o ecossistema Pomoday, essa documentação é toda feita em markdown, mas está configurada para ser aberta no Obsidian para os que preferirem.

A ideia principal é separar a documentação em um repositório a parte para cobrir todo o desenvolvimento.

# Objetivos do Sistema
Pomoday é um sistema de gestão de tarefas diarias com base no pomodoro e integração com outros sistemas como Jira, Trello, Todoist, Toggl, Taskade, Calendarios e Alexa.

Baseado em status, o Usuario poderá definir as tarefas da semana e do dia e manter um controle sob o tempo gasto em cada uma delas, a ideia aqui não é gerenciar projetos, por isso terá integração com outros sistemas. Objetivo é gerenciar o dia de cada um.

# Sistemas

API  https://github.com/willsantos/pomoday_api

WEB https://github.com/willsantos/pomoday_web

Mobile 

Desktop

# Diagrama Entidade Relacionamento
![Diagrama de Entidade e Relacionamento v1](/Assets/Pasted%20image%2020230329155340.png)


# Ideias de Features

## Cadastro de Usuários
O usuário precisará se registrar para acessar o sistema, com email e uma senha que deve ser criptografada, alem disso o Id do usuario deve ser um GUID e não um int.

## Projetos
Cada Usuário pode ter vários projetos, mas um projeto pertece apenas um usuário.
Projetos devem ser configurados com um nome e cor(codigo hex).

Ao puxar (GET) um projeto ele deve trazer todas as tarefas relacionadas a ele. Com possibilidade de filtros(Query String) para ordenar por prazo, status, prioridade.

Existe um projeto padrão chamado "Minhas Tarefas".

## Tarefas
Uma tarefa pertece a somente um projeto.
Tarefa tem o titulo como campo obrigatório, status com o padrão "não iniciado", pioridade com o padrão "normal", projeto com o padrão id=1 "Minhas Tarefas" e tempo,tempo estimado, data e prazo opcional.

## Dia
O dia tem inicio e fim, ao iniciar o dia o usuário pode adicionar tarefas a ele, ao finalizar o dia, as tarefas são registradas. O dia guarda o registro de quantas tarefas e quanto tempo foi gasto naquele dia e em cada tarefa.

## Atualizar tempo
Precisa de uma chamada que atulize apenas o tempo de uma tarefa.

Precisa de uma chamada que atualize simultaneamente o tempo e o status de uma tarefa.

Ao atualizar o tempo, nunca pode receber um valor menor que o anterior.


## Relacionamentos

Um Usuário pode ter 0-N projetos
Um Usuario pode ter 0-N Tarefas
Um Usuario pode ter 0-N Dias

Um projeto pertence apenas a 1 usuario
Um projeto pode ter 0-N Tarefas
O projeto não se relaciona diretamente com o Dia.

Uma tarefa pertence 0 ou 1 projeto.
Uma tarefa pertence a 1 usuario obrigatoriamente.
Uma tarefa pode estar em N dias.



