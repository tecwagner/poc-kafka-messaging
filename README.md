## Apache Kafka

# Criando um serviço com apache kafka.

    - Execuntando o comando para a criação do container: docker-compose up -d.

    - Será criado três container, kafka, zookeper e control-center.

# Acessando o container kafka docker

    - docker exec -it kafka-container bash

# Criar um topic no kafka por meio de linha de comando

    - Comando que lista todos os comandos de: kafka-topics

    - Para criar um topic por meio de linha de comando: kafka-topics --create --topic=teste --bootstrap-server=localhost:9092 --partitions=3

    - Sempres que for acessar o kafka ou topic é necessario informar o bootstap-server=localhost:9092.

    - Comando para listar os topics: kafka-topics --list --bootstrap-server=localhost:9092

    - __consumer_offsets: É referencia de onde topic para de ler e continuar

# Detalhando nosso tópico

    - Listando os topics: kafka-topics --bootstrap-server=localhost:9092 --topic=teste --describe

        Topic           Praticao        Lider           Replicas        Online

        Topic: teste    Partition: 0    Leader: 1       Replicas: 1     Isr: 1
        Topic: teste    Partition: 1    Leader: 1       Replicas: 1     Isr: 1
        Topic: teste    Partition: 2    Leader: 1       Replicas: 1     Isr: 1

# Consumindo e produzindo mensagens

    - Comando kafka que lista todas as regras do consumer: kafka-console-consumer

    - Consumer
        - Comando é responsavel por consumir as mensagens no kafka: kafka-console-consumer --bootstrap-server=localhost:9092 --topic=teste

        - Se o consumidor ainda não tiver um deslocamento estabelecido para consumir, comece com a mensagem mais antiga presente no log em vez da mensagem mais recente.
            - Informe ao comando: --from-beginning
            - Será listado todas as mensagens
            - Comando: kafka-console-consumer --bootstrap-server=localhost:9092 --topic=teste --from-beginning

    - Producer
        - Comando é responsavel por prodizir as mensagens no kafka: kafka-console-producer --bootstrap-server=localhost:9092 --topic=teste

# Introdução aos consumer groups

    - Crinado grupo para o consumer.
        - comando: - Comando: kafka-console-consumer --bootstrap-server=localhost:9092 --topic=teste --group=X

    - Observação: Não tem perigo de dois grupos ouvir a mesma mensagem, ou um só ouvir um partição

# Por dentro de um consumer group

    - Identificar o que cada grupo esta lendo!

    - consultar: kafka-console-consumer --groups

    - Exexutando o consumer de grupo, será carregado uma tabela das partições Group: kafka-consumer-groups --bootstrap-server=localhost:9092 --group=x --describe
