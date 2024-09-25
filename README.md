# Sistema-de-Notifica-o-para-Lan-amentos-de-Livros
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
## Configuração

### 1. Iniciar o RabbitMQ

No Ubuntu, inicie o serviço RabbitMQ com o seguinte comando:

```bash
sudo systemctl start rabbitmq-server
