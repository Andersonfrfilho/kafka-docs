# kafka-docs
# kafka-docs-Windows
* apos baixar o arquivo binario do [kafka](https://kafka.apache.org/downloads)
  - descompact a pasta .tgz
  - mova a pasta para c:

<hr/>

* configurando as pastas no servidor
  - abra a pasta c:/kafka onde vc moveu o arquivo
  - dentro de config/server.properties
    - va em `logs.dir=coloque no inicio c:/pasta_descompactada`
  - depois em zookepers
    - `dataDir=coloque no inicio c:/pasta_descompactada`

<hr/>

* initialized o zookeper dependencia do kafka suas propriedades.
  - `.\bin\windows\zookeeper-server-start.bat .\config\zookeeper.properties`
  - so conected 0.0.0.0:2181

<hr/>

* initialized kafka-server processador de conexão de mensagens
  - dentro da pasta do kafka inicie o [terminal](https://www.microsoft.com/pt-br/p/windows-terminal/9n0dx20hk701?activetab=pivot:overviewtab)
  - utilize o seguinte comando onde esta o executavel do kafka e suas propriedades.
  - `.\bin\windows\kafka-server-start.bat .\config\server.properties`
  - executando 0.0.0.0:9092

<hr/>

* criar um topico
  - primeiro o executavel --flag de criacao --conexao com o kafka na porta 9092
  - `.\bin\windows\kafka-topics.bat --create --bootstrap-server localhost:9092 --replication-factor 1 --partitions 1 --topic LOJA_NOVO_PEDIDO`
  *  verificar tópico criado
     - `.\bin\windows\kafka-topics.bat --list --bootstrap-server localhost:9092`
* produtor de mensagem
  - acessar o código do producer, informar qual broker e qual o tópico e executar
  - `.\bin\windows\kafka-console-producer.bat --broker-list localhost:9092 --topic LOJA_NOVO_PEDIDO`
  - pode digitar a mensagem mensagem que vc digitar 

* Consumindo mensagem
  - consumir mensagem de qual tópico a partir do momento atual
  - `.\bin\windows\kafka-console-consumer.bat --bootstrap-server localhost:9092 --topic LOJA_NOVO_PEDIDO`
  - consumir mensagem desde o inicio do kafka
  - `.\bin\windows\kafka-console-consumer.bat --bootstrap-server localhost:9092 --topic LOJA_NOVO_PEDIDO --from-beginning`

