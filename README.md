# Manipulando-HDFS
 O objetivo deste respositório é desenvolver um exercício do treinamento da empresa @Semantix. Esse exercício tem como base a manipulação do HDFS (Hadoop Distributed File System) distribuindo por etapas. Vale ressaltar que desafio foi desenvolvido em docker!
 
 ### ✍️ 1- Iniciar o cluster de Big Data.
> Para acessar o cluster Bigdata é necessária a utilização do comando: `docker-compose up -d `.
![imagem1](https://github.com/vandisney/Manipulando-HDFS/blob/main/images/imagem1.png)

### ✍️ 2- Acessar o container do namenode.
> É possível acessar o namenode através do comando: `` docker exec -it namenode bash ` .
>![imagem2](https://github.com/vandisney/Manipulando-HDFS/blob/main/images/imagem2.png)

### ✍️ 3- Criar a estrutura de pastas user\aluno\nomeAluno
<ul>
  <li>data</li>
  <li>delete</li>
  <li>recover</li>
</ul>

>  Para realização das atividades acima foi necessário os seguintes comandos:
>
<p>
 hdfs dfs -mkdir -p /user/aluno/vandisney/data <br />
 hdfs dfs -mkdir -p /user/aluno/vandisney/delete <br/ >
 hdfs dfs -mkdir -p /user/aluno/vandisney/recover
</p>

Após a craição das pastas, foi poss´vel validar a existência das mesmas através do comando: 
<p>
> hdfs dfs -ls /user/aluno/vandisney
<p/>

>![imagem4](https://github.com/vandisney/Manipulando-HDFS/blob/main/images/imagem4.png)


### ✍️ 4-: Enviar a pasta /input/exercises-data/escola e o arquivo /input/exercises-data/entrada1.txt para data

Para realizar esse processo foi necessário aplicar o seguinte comando para mover a pasta e depois o arquivo:

`hdfs dfs -put /input/exercises-data/escola /user/aluno/vandisney/data`

>![imagem5](https://github.com/vandisney/Manipulando-HDFS/blob/main/images/imagem5.png)
