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

3. Confirmar se o Freeradius está rodando:

```
docker ps
```

Deve aparecer algo semelhante assim:

```
CONTAINER ID   IMAGE                          COMMAND                  CREATED         STATUS         PORTS                                                           NAMES
17d51d56c640   freeradius-docker_freeradius   "/docker-entrypoint.…"   2 minutes ago   Up 2 minutes   0.0.0.0:1812-1813->1812-1813/udp, :::1812-1813->1812-1813/udp   freeradius01
```
Caso apareça conforme acima, o serviço já está rodando.

## Informações extras

1. Para autenticar no servidor radius, basta utilizar a secret **radiusmagico**

2. Qualquer host poderá se autenticar no servidor. Então **cuidado com a segurança do servidor RADIUS, utilizando um firewall para limitar a consulta do mesmo nas portas padrão (1812 e 1813 UDP)**
