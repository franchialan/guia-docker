<p align="center">
  <a href="" rel="noopener">
 <img width=200px height=200px src="docker-logo.png" alt="Project logo"></a>
</p>

<h3 align="center">Guia de Comandos Docker</h3>

<div align="center">

[![Status](https://img.shields.io/badge/status-active-success.svg)]()
<!-- [![GitHub Issues](https://img.shields.io/github/issues/kylelobo/The-Documentation-Compendium.svg)](https://github.com/kylelobo/The-Documentation-Compendium/issues)
[![GitHub Pull Requests](https://img.shields.io/github/issues-pr/kylelobo/The-Documentation-Compendium.svg)](https://github.com/kylelobo/The-Documentation-Compendium/pulls) -->
[![License](https://img.shields.io/badge/license-MIT-blue.svg)](/LICENSE)

</div>

---

<p align="center"> Visite <a href="https://docker.com">Docker</a> <br> Play with Docker <a href="https://labs.play-with-docker.com/"> Playground Docker</a>
    <br> 
</p>

# 📝 Conteúdo

- [Sobre](#about)
- [Criando Containers](#run_containers)
- [Gerenciando Containers](#management)
- [Gerenciando Imagens Docker](#images)
- [Informações e Status](#status)
- [Autor](#author)

<br></br>

# 🐳 Sobre <a name = "about"></a>

Esse é um guia de comandos básicos do Docker que funcionam tanto no Docker Desktop quanto no Docker Engine <br></br>

## 🚀 Criando Containers <a name = "run_containers"></a><br></br>

Inicie um container a partir de uma imagem

````
docker run <NOME_DA_IMAGEM_DOCKER>
Ex: docker run nginx
````

Inicie um container com um nome definido

````
docker run --name <NOME_PARA_O_CONTAINER> <IMAGEM>
Ex: docker run --name web01 nginx
````

Inicie um container mapeando uma porta

````
docker run -p <HOSTPORT:CONTAINERPORT> <IMAGEM>
Ex: docker run -p 8080:80 nginx
````

Inicie um container mapeando todas as portas

````
docker run -P <IMAGEM>
Ex: docker run -P nginx
````

Inicie um container em background

```
docker run -d <IMAGEM>
Ex: docker run -d nginx
```

Inicie um container adicionando um mapeamento Host-para-IP personalizado

````
docker run --add-host <HOSTNAME:IP> <IMAGEM>
Ex docker run --add-host meudominio.com:10.0.0.1 nginx
````

Inicie um container mapeando um diretório local dentro dele

````
docker run -v <HOSTDIR:TARGETDIR> <IMAGEM>
EX: docker run -v ~/:/usr/share/nginx/html nginx
````

Inicie um container em modo interativo alterando seu entrypoint

````
docker run -it --entrypoint <EXECUTÁVEL> <IMAGEM>
Ex: docker run -it --entrypoint bash nginx
````

<br></br>

## ⚙️ Gerenciando Containers <a name="management"></a><br></br>

Exibe a lista de containers em execução

````
docker ps
````

Exibe a lista de todos os containers (em execução, parados e com erros)

````
docker ps -a
````

Delete um container

````
docker rm -f <ID_OU_NOME_CONTAINER>
Ex: docker rm -f web01
Obs: utilizamos a flag "-f" para forçar uma deleção de um container em execução. Caso o container não esteja com o status "running" podemos utilizar apenas o comando docker rm.
````

Delete todos os containers que estão parados

````
docker container prune
````

Pause um container em execução

````
docker stop <ID_OU_NOME_CONTAINER>
Ex: docker stop web01
````

Inicie um container  que está parado

````
docker start <ID_OU_NOME_CONTAINER>
Ex: docker start web01
````

Copie um arquivo de dentro do container para o host

````
docker cp <CONTAINER:ORIGEM> <DESTINO>
Ex: docker cp web:/index.html index.html
````

Copie um arquivo do host para dentro do container

````
docker cp <ORIGEM> <CONTAINER:DESTINO>
Ex: docker cp index.html web:/index.html
````

Inicie um container em modo interativo utilizando o shell

````
docker run -it <CONTAINER> bash
Ex: docker run -it web01 bash
````

Renomeie um container

````
docker raname <NOME_ANTIGO> <NOME_NOVO>
Ex: docker raname web01 web01-new
````

Crie uma imagem a partir de um container 

````
docker commit <CONTAINER>
Ex: docker commit web01
````

<br></br>

## 🛠️ Gerenciando Imagens Docker<a name = "images"></a><br></br>

Exibe todas as imagens

````
docker images ls
````

Baixe uma imagem

````
docker pull <IMAGEM:TAG>
Ex: docker pull ubuntu:latest
````

Sube uma imagem para um repositório

````
docker push <IMAGEM:TAG>
Ex: docker push minhaimagem:1.0
````

Delete uma imagem

````
docker rmi <IMAGEM>
Ex: docker rmi minhaimagem
````

Delete todas as imagens penduradas

````
docker image prune
````

Delete todas as imagens que não estão em uso

````
docker image prune -a
````

Crei uma imagem com Dockerfile

````
docker build <DIRETORIO_DOCKERFILE>
Ex: docker build .
Obs: o "." significa que você estará fazendo a construção da imagem a partir do Dockerfile no diretório onde você está.
````

Edicione uma marcação à imagem Docker

````
docker tag <IMAGEM> <NOVA_IMAGEM>
Ex: docker tag minhaimagem minhaimagem:v1
````

Crie e adicione uma marcação à imagem a partir de um Dockerfile

````
docker build -t <IMAMGE> <DIRETORIO_DOCKERFILE>
Ex: docker build -t minhaimamge:v1 .
````

Salve uma imagem em um arquivo .tar

````
docker save <IMAGEM> > <ARQUIVO>
Ex: docker save ubuntu > ubuntu.tar
````

Carregue uma imagem a partir de um arquivo .tar 

````
docker load -i <ARQUIVO_.TAR>
Ex: docker load -i ubuntu.tar
````

<br></br>

## 📊 Informações e Status <a name = "status"></a><br></br>

Exibe os logs de um container

````
docker logs <CONTAINER>
Ex: docker logs web01
````

Exibe o status dos containers em execução

````
docker stats
````

Exibe os processos em execução de um container

````
docker top <CONTAINER>
Ex: docker top web01
````

Exibe a versão instalada do Docker 

````
docker version
````

Exibe de forma detalhada informações sobre um objeto

````
docker inspect <CONTAINER_NETWORK_IMAGEM>
Ex: docker inspect web01
````

Exibe todos os arquivos modificados no container
````
docker diff <CONTAINER>
Ex: docker diff web01
````

Exibe as portas mapeadas de um container

````
docker ports <CONTAINER>
Ex: docker ports web01
````
<br></br>

## ✍️ Autor <a name = "author"></a>

- [@franchialan](https://github.com/franchialan) - Platform Engineer

