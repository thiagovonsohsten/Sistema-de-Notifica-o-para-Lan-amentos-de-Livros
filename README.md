# Sistema de Notificação para Lançamentos de Livros

Este sistema utiliza RabbitMQ para enviar e receber notificações sobre lançamentos de livros. O sistema é composto por:
- Um **produtor** (em Java) que envia informações sobre os livros.
- Um ou mais **consumidores** (em Python) que recebem as notificações baseadas em tópicos.
- Um **backend de auditoria** (em Python) que monitora todas as mensagens enviadas.

## Requisitos

1. **RabbitMQ** deve estar instalado e rodando.
2. **Java 8+** para o produtor.
3. **Python 3.6+** para o consumidor e o backend de auditoria.
4. **Biblioteca `pika`** no Python para conexão com RabbitMQ:
   ```bash
   pip install pika

# Configuração

## 1. Iniciar o RabbitMQ
No Ubuntu, inicie o serviço RabbitMQ com:

```bash
sudo systemctl start rabbitmq-server
```

Verifique o status do RabbitMQ:

```bash
sudo systemctl status rabbitmq-server
```

## 2. Executar o Produtor (Java)
Compile e execute o produtor no Eclipse ou na linha de comando:

```bash
javac BookProducer.java
java BookProducer
```

## 3. Executar o Consumidor (Python)
No terminal, execute o consumidor Python:

```bash
python3 consumidor.py
```

O consumidor pedirá que você insira uma chave de roteamento (por exemplo, `livros.ficcao` ou `livros.*`).

## 4. Executar o Backend de Auditoria (Python)
Para rodar o backend de auditoria, execute:

```bash
python3 auditoria.py
```

O backend de auditoria estará configurado para receber todas as mensagens usando a routing key `#`.

# Testes

## Cenários para Testar

### 1. Um Produtor e Mais de Um Consumidor
- Execute um produtor e dois consumidores com diferentes padrões de tópicos para ver como as mensagens são distribuídas.

### 2. Mais de Um Produtor e Mais de Um Consumidor
- Execute mais de um produtor, cada um enviando mensagens com diferentes routing keys, e observe como os consumidores recebem as mensagens apropriadas.

# Conclusão
Este sistema simula um ambiente de notificações para lançamentos de livros, com a possibilidade de múltiplos consumidores e produtores conectados a um RabbitMQ com roteamento baseado em tópicos.
