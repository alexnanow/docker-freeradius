# docker-freeradius
Repositório da suite freeradius em Docker para conexão de usuários de forma emergencial

Utiliza o Docker, Docker-compose e Freeradius (versão alpine-linux, sem plugins extras).

Instalação do Docker e git:

```
apt update && apt install -y ca-certificates curl gnupg lsb-release git
curl -fsSL https://download.docker.com/linux/debian/gpg | gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/debian $(lsb_release -cs) stable" | tee /etc/apt/sources.list.d/docker.list > /dev/null
apt update && apt install -y docker-ce docker-ce-cli containerd.io
curl -L "https://github.com/docker/compose/releases/download/v2.5.1/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
chmod +x /usr/local/bin/docker-compose
```

Verificar se o docker e docker-compose foi instalado:

```
docker version
docker-compose --version
```
Para instalar a suite:

1. Clonar o repositório via GIT. 

Por estar em desenvolvimento, necessário baixar a branch develop:

```
cd /root
git clone https://github.com/alexnanow/docker-freeradius
```

2. Entrar e executar o docker-compose para baixar e rodar os containers das aplicações

```
cd /root/docker-freeradius
docker-compose build
docker-compose up -d
```
