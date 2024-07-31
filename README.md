# Projeto: Criar uma máquina virtual, instalar o servidor web Apache e servir uma página teste.

Esse repositório contém um projeto simples de IaC(Infraestructure as Code), seguindo a própia documentação da plataforma Harshicorp Vagrant. O objetivo é provisionar uma máquina virtual com o sistema GNU/Linux, instalar um servidor Web através de um Shell Script e disponibilizar uma página através da máquina convidada.

## Descrição

Etapas do projeto:

- Configurar uma máquina com a box hashicorp/bionic64 (Ubuntu 18.04 LTS 64 bits).
- Definir uma versão específica da box (1.0.282).
- Utilizar um script de provisionamento (bootstrap.sh).
- Configurar o redirecionamento de portas.

Esse projeto é parte da documentação oficial da Hashicorp (https://developer.hashicorp.com/vagrant/tutorials/getting-started)

## Pré-requisitos
- Instale a versão mais recente do Vagrant.
- Instale um virtualizador como VirtualBox, VMware ou Hyper-V.

## Instalação
1. Clone este repositório para a sua máquina local:
  ```sh
  git clone https://github.com/juliutux/vagrant_getting_started
  ```
2. Navegue até o diretório do projeto:
  ```sh
   cd vagrant_getting_started
  ```
3. Instale o Vagrant se ainda não estiver instalado:
  ```sh
    # No Ubuntu
    sudo apt-get install vagrant
    
    # No MacOS
    brew install vagrant
  ```

## Uso

1. Iniciar a máquina virtual:
    ```sh
    vagrant up
    ```
2. Acessar a máquina virtual:
    ```sh
    vagrant ssh
    ```
3. A aplicação provisionada estará disponível na porta 4567 do host. Podendo ser acessada através do navegador (http://127.0.0.1:4567)

## Código do Script

Este script instala o Apache e cria um link simbólico entre o diretório de arquivos sincronizados e o local onde o Apache procurará a página.

```bash
#!/usr/bin/env bash

apt-get update
apt-get install -y apache2

if ! [ -L /var/www ]; then
  rm -rf /var/www
  ln -fs /vagrant /var/www
fi
```
## Conteúdo da página
```html
<!DOCTYPE html> 
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
</head>
  <body> 
    <h1>Testando máquinas virtuais com o Vagrant!</h1> 
  </body> 
</html>
```
## Sincronizar arquivos locais e máquinas convidadas
Por padrão, o Vagrant compartilha o diretório do seu projeto (aquele que contém o Vagrantfile) com o diretório `/vagrant` da máquina convidada.

## Licença

Este projeto está licenciado sob a licença MIT - veja o arquivo [LICENSE.md](LICENSE.md) para mais detalhes.

## Contato

Júlio Chagas

[![LinkedIn](https://img.shields.io/badge/LinkedIn-000?style=for-the-badge&logo=linkedin&logoColor=0E76A8)](https://www.linkedin.com/in/julio-chagas/)
[![GitHub](https://img.shields.io/badge/GitHub-000?style=for-the-badge&logo=github&logoColor=white)](https://github.com/juliutux)
[![Outlook](https://img.shields.io/badge/Email-000?style=for-the-badge&logo=microsoft-outlook&logoColor=0078D4)](mailto:juliu12@outlook.com.br)

