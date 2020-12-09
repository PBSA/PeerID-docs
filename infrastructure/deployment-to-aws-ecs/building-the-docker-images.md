# Building the Docker Images

## PeerID Backend

{% embed url="https://gitlab.com/PBSA/PeerplaysIO/tools-libs/peerid/peerid-backend/-/tree/support/docker" %}

```text
git clone https://gitlab.com/PBSA/PeerplaysIO/tools-libs/peerid/peerid-backend.git -b support/docker
cd peerid-backend
docker build .
```

## PeerID GUI

{% embed url="https://gitlab.com/PBSA/PeerplaysIO/tools-libs/peerid/peerid-gui/-/tree/support/docker" %}

```text
git clone https://gitlab.com/PBSA/PeerplaysIO/tools-libs/peerid/peerid-gui.git -b support/docker
cd peerid-gui

# edit the hompage in package.json with your DNS
vim package.json

# edit the .env with your variable values
vim .env

docker build . -f prod.Dockerfile
```

