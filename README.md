# Manipulando-HDFS
 O objetivo deste respositório é desenvolver um exercício do treinamento da empresa @Semantix. Esse exercício tem como base a manipulação do HDFS (Hadoop Distributed File System) distribuindo por etapas. Vale ressaltar que desafio foi desenvolvido em docker!
 
 ### ✍️ 1- Iniciar o cluster de Big Data.
> Para acessar o cluster Bigdata é necessária a utilização do comando: `docker-compose up -d `.
![imagem1](https://github.com/vandisney/Manipulando-HDFS/blob/main/images/imagem1.png)

### ✍️ 2- Acessar o container do namenode.
> É possível acessar o namenode através do comando: `docker exec -it namenode bash ` .
>![imagem2](https://github.com/vandisney/Manipulando-HDFS/blob/main/images/imagem2.png)

### ✍️ 3- Criar a estrutura de pastas user\aluno\nomeAluno com as seguintes sub-pastas:

<ul>
  <li>data</li>
  <li>delete</li>
  <li>recover</li>
</ul>
   Para realização das atividades acima foi necessário os seguintes comandos:
<p>
   hdfs dfs -mkdir -p /user/aluno/vandisney/data <br />
   hdfs dfs -mkdir -p /user/aluno/vandisney/delete <br/ >
   hdfs dfs -mkdir -p /user/aluno/vandisney/recover
</p>
Após a criação das pastas, foi possível validar a existência das mesmas através do comando: 
<p>
   hdfs dfs -ls /user/aluno/vandisney
<p/>
>![imagem4](https://github.com/vandisney/Manipulando-HDFS/blob/main/images/imagem4.png)

### ✍️ 4- Enviar a pasta /input/exercises-data/escola e o arquivo /input/exercises-data/entrada1.txt para data.
  Para realizar esse processo foi necessário aplicar o seguinte comando para mover a pasta escola e o arquivo entrada1.txt para a pasta data:

`hdfs dfs -put /input/exercises-data/escola /user/aluno/vandisney/data`
 Para validação da ação,pode-se lista a pasta com o comando:
 'hdfs dfs -ls /user/aluno/vandisney/data

>![imagem5](https://github.com/vandisney/Manipulando-HDFS/blob/main/images/imagem5.png)

### ✍️ 5- Mover o arquivo "entrada1.txt" para a pasta recover.
Para realizar esse processo vamos aplicar o seguinte comando: `hdfs dfs -mv /user/aluno/vandisney/data/entrada1.txt /user/aluno/vandisnet/recover ` , através da imagem abaixo é possível observar que dentro da pasta recover se encontra o arquivo entrada1.txt! E dentro da pasta data agora se encontra vazia!
>![imagem7](https://github.com/vandisney/Manipulando-HDFS/blob/main/images/imagem7.png)

### ✍️ 6- Deletar a pasta recover.
Para realizar a questão foi necessario aplicar o seguinte comando: `hdfs dfs -rm -r /user/aluno/vandisney/recover`, e como é possível observar na imagem abaixo, a pasta recover foi direcionado para a lixeira utilizando o TrashPolicyDefault!
>![imagem8](https://github.com/vandisney/Manipulando-HDFS/blob/main/images/imagem8.png)

### ✍️ 7- Procurando o arquivo "alunos.csv" no HDFS.
Agora vamos procurar o arquivo alunos.csv dentro do HDFS e o terminal vai retornar o caminho que se encontra esse arquivo!
>![imagem9](https://github.com/vandisney/Manipulando-HDFS/blob/main/images/imagem9.png)

### ✍️ 8- Mostrar o último 1KB do arquivo “alunos.csv”.
Para realizar essa questão foi necessário aplicar o comando: `hdfs dfs -tail /user/aluno/vandisney/data/escola/alunos.csv ` e o sistema irá retornar os registro que equivalem a 1KB do arquivo todo.
>![imagem10](https://github.com/vandisney/Manipulando-HDFS/blob/main/images/imagem10.png)

### ✍️ 9- Mostrar as 5 primeiras linhas do arquivo “alunos.csv”.
A questão pede que detalhamos os 5 primeiros registros do arquivos selecionado, para isso vamos aplicar o comando: `hdfs dfs -cat /user/aluno/gabriel/data/escola/alunos.csv | head -n 5`
>![imagem11](https://github.com/vandisney/Manipulando-HDFS/blob/main/images/imagem11.png)

### ✍️ 10- Verificação de soma das informações do arquivo “alunos.csv”.
O objetivo principal agora é aplicar um comando que retorne se o arquivo tem consistencia para retornos com put e get.

>![imagem12](https://github.com/vandisney/Manipulando-HDFS/blob/main/images/imagem12.png)

### ✍️ 11- Criar um arquivo em branco com o nome de “test”  e alterar o fator de replicação do arquivo “test” para 2.

> A criação dO arquivo test foi usado o comando: `hdfs dfs -touchz /user/aluno/vandisney/data/teste `
> É possível listar a pasta para Validação da ação acima através do comando: `hdfs dfs -ls /user/aluno/vandisney/data/ ` 
>![imagem13](https://github.com/vandisney/Manipulando-HDFS/blob/main/images/imagem13.png)

> Para replicamos o arquivo teste em 2 datanodes, e para isso vamos aplicar o comando: ` hdfs dfs -setrep 2 /user/aluno/vandisney/data/teste ` Conforme é possível observar na imagem abaixo, a segunda coluna mostra a quantidade de replicação.
![imagem14](https://github.com/vandisney/Manipulando-HDFS/blob/main/images/imagem14.png)

### ✍️ 12- Exibir o espaço livre do data e o uso do disco.
Agora vamos realizar algumas consultas do arquivo alunos.csv e do disco. O comando stat permite trazer alguns informações do arquivo, como é demostrado na imagem abaixo.
Para realizar a consulta do disco aplicamos o comando: `hdfs dfs -du -h /user/aluno/vandisney/data `, onde é possível observar que a pasta escola tem 29.2M e o arquivo teste com o tamanho 0.

![imagem15](https://github.com/vandisney/Manipulando-HDFS/blob/main/images/imagem15.png)
