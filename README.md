Sem repositório



### Subir a aplicação

```bash
docker-compose up
```

### bootstrap-server (Criando um tópico na mão)

Para criamos algo no kafka, apenas para teste,
primeiro abra o terminal dos containers que foram iniciado.

Execute para acessar o container do kafka: 
```bash
docker exec -it kafkafullcycle-kafka-1 bash
```

Caso não saiba o nome do container: 
```bash
docker-compose ps
```

Agora podemos criar um topic com partições: 
```bash
kafka-topics --create --topic=teste --bootstrap-server=localhost:9092 --partitions=3
```
Resposta após o comando: $ Created topic teste.

---

Listar todos os tópicos: 

```bash
kafka-topics --list --bootstrap-server=localhost:9092
```

Default Tipics

| Topic Name            | Reason                                                                         |
|-----------------------|--------------------------------------------------------------------------------|
| __consumer_offsets    | guarda qual offset determinado consumer esta no momento da leitura dos tópicos |
| _confluent-metrics    |                                                                                |
| _confluent-monitoring |                                                                                |

---

Descrição do Kafka

```bash
kafka-topics --bootstrap-server=localhost:9092 --topic=teste --describe
```

## Criando um Producer
Vamos criar um produtor de mensagens com o comando:
```bash
kafka-console-producer --bootstrap-server=localhost:9092 --topic=teste
```

## Criando um Consumer 
Responsável para começar a consumir o tópico.
```bash
kafka-console-consumer --bootstrap-server=localhost:9092 --topic=teste
```

Após rodar o comando acima, abra outro terminal para podermos criar o produtor.
Não feche o terminal onde foi criado o consumer! :) [emoji palminhas]

Após isso, basta digitar qualquer mensagem no terminal do produtor e depois ir até
o terminal do consumidor e você verá a mesma mensagem lá! 
Chique né? :) [gif com animação]


---
Visualizar o histórico de mensagens
```bash
kafka-console-consumer --bootstrap-server=localhost:9092 --topic=teste --from-beginning
```


--- 
# Consumer Groups

Para isso basta copiarmos o mesmo comando usado na criação de um consumer
simples, e adicionar o parâmetro group ao final do comando.

```bash
kafka-console-consumer --bootstrap-server=localhost:9092 --topic=teste --group=x
```

 
Por dentro de um consumer group:
```bash
kafka-consumer-groups --bootstrap-server=localhost:9092 --group=x --describe
```

![group details](/sources/group_details.png)


- [ ] inserir print explicando que um mesmo consumer esta atrelado a duas partições.

---




# Todo 

- [ ] ReplicationFactor
- [ ] http://localhost:8080/ui/clusters/create-new-cluster
- [ ] http://localhost:19000/ 


# Referências

https://github.com/codeedu/fc2-kafka/blob/main/docker-compose.yaml