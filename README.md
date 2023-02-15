  

O  que é Airflow                                                      
O Apache Airflow é uma plataforma de código aberto para desenvolver, agendar e monitorar fluxos de trabalho orientados a lotes. A estrutura Python extensível dAirflow permite que você crie fluxos de trabalho conectados a praticamente qualquer tecnologia. Uma interface da Web ajuda a gerenciar o estado de seus fluxos de trabalho. O Airflow pode ser implantado de várias maneiras, variando de um único processo em seu laptop a uma configuração distribuída para suportar até mesmo os maiores fluxos de trabalho.

Airflow como código

A principal característica dos fluxos de trabalho do Airflow é que todos os fluxos de trabalho são definidos em código Python. “Fluxos de trabalho como código” serve a vários propósitos:

Dinâmico : os pipelines do Airflow são configurados como código Python, permitindo a geração dinâmica de pipelines.

Extensível : a estrutura do Airflow contém operadores para conectar-se a várias tecnologias. Todos os componentes do Airflow são extensíveis para se ajustar facilmente ao seu ambiente.

Flexível : a parametrização do fluxo de trabalho é integrada, aproveitando o mecanismo de modelagem 

# Conorme código abaixo:
from datetime import datetime

from airflow import DAG
from airflow.decorators import task
from airflow.operators.bash import BashOperator

# A DAG represents a workflow, a collection of tasks
with DAG(dag_id="demo", start_date=datetime(2022, 1, 1), schedule="0 0 * * *") as dag:

    # Tasks are represented as operators
    hello = BashOperator(task_id="hello", bash_command="echo hello")

    @task()
    def airflow():
        print("airflow")

    # Set dependencies between tasks
    hello >> airflow()
    
   # No Código acima podemos ver

Um DAG chamado “demo”, começando em 1º de janeiro de 2022 e sendo executado uma vez por dia. Um DAG é a representação do Airflow de um fluxo de trabalho.

Duas tarefas, um BashOperator executando um script Bash e uma função Python definida usando o @taskdecorador

>>entre as tarefas define uma dependência e controla a ordem em que as tarefas serão executadas

O Airflow avalia esse script e executa as tarefas no intervalo definido e na ordem definida. O status do DAG “demo” é visível na interface da web:

# Projeto

Este projeto tem o objetivo de  Rodar uma DAG  smples utilizando  o Smooth.py onde estaria expondo video.

- Para  Rodar  o Airflow foi utilizado o docker compose para criar o  container onde todas as imagens foram baixadas  apartir  de  um codigo YAML  que pode ser obtido na documetação oficial.

#Comandos Basicos

Para iniciar  baixar as Imagen s no compose

docker compose up airflow-init   ( inicia a baixar as imagens do repositorio oficial)

![Pismo1](https://user-images.githubusercontent.com/62898524/219027860-86374568-1490-40e4-b5f6-f135da42da8b.JPG)

docker compose Up.
 
 A  DAG  descrita  no projeto  pode ser acessada localmente  na porta especificada  NO  airflow-webserver:  neste caso 8080(http://localhoast:8080)

#  BAIXANDO IMAGENS AIRFLOW
Na Primeira Imagem acima temos  as imagens do airflow sendo baixadas  no compose .
O projeto inicial precisou identificar possíveis erros existentes no codigo YAML que tornaria a criação do Airflow utilizando o Docker compose. Após tais problemas encontrados e modificados conforme relatados em Problemas.txt iniciou o processo de baixar as imagens do airflow.
Rodando na pasta onde estavam os fontes:
- C:\Users\Dioeliton> docker compose up airflow-init![Pismo2](https://user-images.githubusercontent.com/62898524/219017513-49e8c5b3-b468-4895-8f90-4f72a28e9ab4.JPG)

Para ter acesso ao Airflow seguimos com comando basicos:![Pismo3](https://user-images.githubusercontent.com/62898524/219018811-fd237fbc-50e2-4ab4-8cb2-0f4b85cd8f20.JPG)


C:\Users\Dioeliton> docker compose up

e apos expor o Airflow localmente:

http://localhost:8080

 
Acessando o Airflow localmente verificar se a Dag criada estaria funcionando corretamente mostra

A  DaG  que  mostra  link para video youtube rodou com sucesso  

![image](https://user-images.githubusercontent.com/62898524/219026734-b68f368e-d3a5-47e7-ad3a-dc3147b8ec4f.png)


Após a DAG rodar os logs podem ser observados na Pasta LOGS que foi criada.

![Pismo4](https://user-images.githubusercontent.com/62898524/219027088-11e39a12-37b0-4aef-bfee-1a633b66579d.JPG)

