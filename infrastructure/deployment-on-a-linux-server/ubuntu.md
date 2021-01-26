# Ubuntu

## Prerequisites

* PostgreSQL
* NodeJS 12+
* Ubuntu 18.04+ recommended

### Installing PostgreSQL

```text
sudo apt-get update
sudo apt-get -y install postgresql
```

### Installing NodeJS

Using nvm: [https://github.com/nvm-sh/nvm](https://github.com/nvm-sh/nvm)

```text
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.37.2/install.sh | bash
```

Restart the terminal and install node:

```text
nvm install 12
```

## Installing PeerID

### PeerID-GUI

{% embed url="https://gitlab.com/PBSA/PeerplaysIO/tools-libs/peerid/peerid-gui" %}

```text
git clone https://gitlab.com/PBSA/PeerplaysIO/tools-libs/peerid/peerid-gui.git
cd peerid-gui
npm install
```

#### Configure the environment file

```text
touch .env
```

Configure the `.env` with the specified values:

```text
DEV_API_ROUTE='http://example.com/'
PRODUCTION_API_ROUTE='http://examples.com/'

DEV_BASE_ROUTE='http://example.com/api'
PRODUCTION_BASE_ROUTE='http://examples.com/api'

BLOCKCHAIN_ENDPOINTS='wss://example-endpoint.com/api'

PEERPLAYS_USD_ASSET_ID='1.3.0'
PEERPLAYS_ESCROW_ACCOUNT_ID='1.2.23'
PEERPLAYS_PAYMENT_ACCOUNT_ID='1.2.21'
```

Start the application \(dev mode\)

```text
npm start
```

For a production environment build the static files:

```text
npm run build
```

After building the static files, you can host them using any web server.

### PeerID-backend

{% embed url="https://gitlab.com/PBSA/PeerplaysIO/tools-libs/peerid/peerid-backend.git" %}

```text
git clone https://gitlab.com/PBSA/PeerplaysIO/tools-libs/peerid/peerid-backend
cd peerid-backend
npm install
```

configure the `config/default.json` and `config/development.json` files:

**default.json**

```text
{
  "logLevel": "trace",
  "db": {
    "user": "",
    "password": "",
    "host": "127.0.0.1",
    "port": "5432",
    "database": "peerid"
  },
  "swagger": {
    "host": "virtserver.swaggerhub.com",
    "schemes": [
      "https"
    ]
  },
  "sessionSecret": "sessionSecret",
  "cors": true,
  "port": 3000,
  "google": {
    "clientId": "",
    "clientSecret": ""
  },
  "facebook": {
    "clientId": "",
    "clientSecret": ""
  },
  "discord": {
    "clientId": "",
    "clientSecret": ""
  },
  "raven": {
    "enabled": false,
    "url": ""
  },
  "mailer": {
    "host": "smtp.gmail.com",
    "port": 587,
    "secure": false,
    "auth": {
      "user": "",
      "pass": ""
    },
    "sender": "",
    "tls": {
        "rejectUnauthorized": false
    }
  },
  "frontendUrl": "http://localhost:8082",
  "backendUrl": "http://localhost:3000",
  "frontendCallbackUrl": "http://localhost:8082/callback",
  "peerplays": {
    "peerplaysWS": "wss://irona.peerplays.download/api",
    "peerplaysFaucetURL": "https:/irona-faucet.peerplays.download/api/v1/accounts",
    "referrer": "1.2.0",
    "feeAssetId": "1.3.0",
    "paymentAccountID": "1.2.21",
    "paymentAccountWIF": "5HttHcgL2NgFc5XsFY8bs51VehVDS2Tb4NGkRuwjJ6v6Mq7eC7S"
  }
}
```

**development.json**

```text
{
  "logLevel": "trace",
  "db": {
    "user": "",
    "password": "",
    "host": "127.0.0.1",
    "port": "5432",
    "database": "peerid"
  },
  "swagger": {
    "host": "virtserver.swaggerhub.com",
    "schemes": [
      "https"
    ]
  },
  "sessionSecret": "sessionSecret",
  "cors": true,
  "port": 3000,
  "google": {
    "clientId": "",
    "clientSecret": ""
  },
  "facebook": {
    "clientId": "",
    "clientSecret": ""
  },
  "discord": {
    "clientId": "",
    "clientSecret": ""
  },
  "raven": {
    "enabled": false,
    "url": ""
  },
  "mailer": {
    "host": "smtp.gmail.com",
    "port": 587,
    "secure": false,
    "auth": {
      "user": "",
      "pass": ""
    },
    "sender": "",
    "tls": {
        "rejectUnauthorized": false
    }
  },
  "frontendUrl": "http://localhost:8082",
  "backendUrl": "http://localhost:3000",
  "frontendCallbackUrl": "http://localhost:8082/callback",
  "peerplays": {
    "peerplaysWS": "wss://irona.peerplays.download/api",
    "peerplaysFaucetURL": "https:/irona-faucet.peerplays.download/api/v1/accounts",
    "referrer": "1.2.0",
    "feeAssetId": "1.3.0",
    "paymentAccountID": "1.2.21",
    "paymentAccountWIF": "5HttHcgL2NgFc5XsFY8bs51VehVDS2Tb4NGkRuwjJ6v6Mq7eC7S"
  }
}
```

Start the application:

```text
npm start
```

