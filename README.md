# Documentação Servidor de Imagens (MinIO) - Projeto Daniel

Entenda que este repositório servirá apenas para testes, pois o correto é hospedar esse serviço. 

OBS: Não encontrei uma hospedagem gratuita que ofereça Persistent Disk.


## Tecnologias Usadas
Foi necessário apenas o `docker` e o `docker-compose`, pois esse repositório consiste basicamente do serviço MinIO rodando em um docker.

## Funcionamento
A ideia é que o serviço do MinIO rode em um docker, mas salve todas as imagens no computador host (ou seja, no SEU computador), com caminho especificado pela variável de ambiente **MINIO_DATA_PATH**.

Esse projeto também configura o MinIO para ter um Bucket "news", para armazenar as imagens das notícias, e adiciona um usuário padrão que dá acesso ao Backend em Java.

## Pré-requisitos
- Baixar o `docker` e garantir que o `docker-compose` está presente.

- Possuir um `.env` com as seguintes variáveis de ambientes:

    1. **MINIO_DATA_PATH**: Ele conterá o caminho absoluto para a pasta, do SEU computador, em que os dados ficarão salvos;

    2. **MINIO_POLICY_PATH**: Ele conterá o caminho absoluto para o arquivo policy.json que serve para especificar as políticas de acesso ao banco de imagens;

    3. **MINIO_ROOT_USER**: Nome do usuário ROOT para acessar o MinIO Web UI. OBS: Se encontra em http://localhost:9001;

    4. **MINIO_ROOT_PASSWORD**: Senha do usuário ROOT para acessar o MinIO Web UI. OBS: Se encontra em http://localhost:9001;

    5. **MINIO_BACKEND_USER**: Nome do usuário do Backend Java que tem acesso ao banco de imagens. Esse nome deve ser o mesmo presente na variável de ambiente `minio.access.name` no arquivo `application.properties`;

    6. **MINIO_BACKEND_PASSWORD**: Senha do usuário do Backend Java que tem acesso ao banco de imagens. Esse nome deve ser o mesmo presente na variável de ambiente `minio.access.secret` no arquivo `application.properties`;
    
Ex:
![alt text](docs/exemplodotenv.png)

## Instruções para rodar

Vá para a pasta principal desse projeto e rode no terminal:

```
docker-compose up
```

OU 

Caso queira o terminal livre, utiize a flag `-d`:
```
docker-compose up -d
```
Note que ao user essa flag, o container irá rodar em background em seu computador. Para parar o serviço utilize o comando:

```
docker-compose stop
```