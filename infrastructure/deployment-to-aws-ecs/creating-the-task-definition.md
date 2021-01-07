# Creating the Task Definition

This article will be referencing the following repositories as the Docker image codebase:

{% embed url="https://gitlab.com/PBSA/PeerplaysIO/tools-libs/peerid/peerid-gui/-/tree/support/docker" %}

{% embed url="https://gitlab.com/PBSA/PeerplaysIO/tools-libs/peerid/peerid-backend/-/tree/support/docker" %}

In ECS, create a new Task Definition and choose the desired launch type compatibility \(Fargate or EC2\)

### Attach the Task Role

Attach the task role created from [Storing Secrets in Amazon Parameter Store to use in ECS](https://peerplays.gitbook.io/peerid/infrastructure/deployment-to-aws-ecs/storing-secrets-in-amazon-parameter-store-to-use-in-ecs).

### Attach the Task Execution Role

This role is required by tasks to pull container images and publish container logs to Amazon CloudWatch on your behalf. You can use the default one created by Amazon.

### Adjust the Task Size

We can assign total memory and CPU to the task. For PeerID, choose:

* 2GB Task Memory \(GB\)
* 1 vCPU Task CPU \(vCPU\)

### Adding the Containers

Create two containers:

* PeerID Backend
* PeerID Frontend + Webserver \(we will be using NGINX\)

#### PeerID Backend

1. Enter the container name.
2. Enter the path to the Docker registry with the container Image.
3. Enter `1024` ****for a soft limit for the memory.
4. Enter `3000` tcp for the port mappings.
5. Enter `756` CPU units.
6. Tick the essential box.
7. Enter  `/peerid-backend/docker-entrypoint.sh` for the entry point.
8. Enter `npm,run,start` for the command.
9. Enter `peerid-backend` for the working directory.
10. Enter the environment variables for PeerID Backend using `ValueFrom` and referencing the parameters from Systems Manager Parameter Store.

```text
# List of variables

## Auth for a PostgreSQL database
DB_DATABASE
DB_HOST
DB_PASSWORD
DB_PORT
DB_USER

## Third party login
DISCORD_ID
DISCORD_SECRET
FACEBOOK_ID
FACEBOOK_SECRET
GOOGLE_ID
GOOGLE_SECRET

## Routes
FRONTEND_CALLBACK_URL # https://example.com/callback
FRONTEND_URL # https://example.com
BACKEND_URL # https://example.com/api

## Mailer settings
MAILER_HOST
MAILER_PASS
MAILER_PORT
MAILER_SENDER
MAILER_USER

## Peerplays Settings

PEERPLAYS_FAUCET_URL
PEERPLAYS_PAYMENT_ACCOUNT_ID
PEERPLAYS_PAYMENT_ACCOUNT_WIF
PEERPLAYS_REFERRER
PEERPLAYS_WS # node api endpoint
PEERPLAYS_ASSET_ID

## NodeJS
MODULE # API
SESSION_SECRET # randoms string
```

**PeerID Frontend**

1. Enter the container name.
2. Enter the path to the Docker registry with the container Image.
3. Enter `256` for a soft limit for the memory.
4. Enter `80` and `443` tcp for the port mappings.
5. Enter `256` CPU units.
6. Tick the essential box.
7. Enter `/docker-entrypoint.sh` for the entry point.
8. Enter `nginx,-g,daemon off;` for the command.
9. Enter the environment variables for PeerID GUI using `ValueFrom` and referencing the values created from Systems Manager Parameter Store.

```text
# List of variables

BACKEND_NAME # peerid-backend
BACKEND_PORT # 3000
FRONTEND_NAME # peerid-gui
VHOST # DNS/localhost
```

