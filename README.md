<h1 align="center">
<img src="https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F47ad6ad0-55bc-44a2-b989-e88243834d4d%2Felixir-icon.png?table=block&id=9d73d4ee-fa70-43f5-93d9-c768922306ca&width=250&userId=c0530cfd-b499-49b5-9557-57b445ee0294&cache=v2" width="124" height="124">
 <br>
</h1>

Faaaala Dev! Seja muito bem vindo à **Next Level Week 05**, trilha **Elixir**!

Nesse guia iremos realizar as configurações de ambiente necessárias para colocar a mão na massa. 

Para que você consiga configurar tudo de acordo com o seu sistema operacional, deixamos aqui um guia específico para cada ambiente 💜

# Instalação do Elixir e Phoenix

Para a instalação no Linux e macOS, recomendamos a instalação com o gerenciador de pacotes **asdf** e caso você enfrente algum problema com esse método, use o [método de instalação padrão](https://www.notion.so/Configura-es-do-ambiente-9d73d4eefa7043f593d9c768922306ca).

## Instalação do Elixir com asdf (Linux e macOS)

O **asdf** é um gerenciador de versões que pode ser usado para diversos runtimes como Node.js, Ruby, Python, inclusive o Elixir.

O **asdf** não é suportado pelo Windows, para esse sistema utilize o [método de instalação padrão](https://www.notion.so/Configura-es-do-ambiente-9d73d4eefa7043f593d9c768922306ca).

Você pode seguir o passo a passo para a instalação de acordo com o seu sistema operacional a partir do site oficial:

[asdf - An extendable version manager](https://asdf-vm.com/#/core-manage-asdf)

Após ter instalado com sucesso o asdf, agora iremos instalar plugins que nos permitirá instalar o Erlang e o Elixir.

### Instalando os plugins

Para instalar os plugins necessários basta rodar os comandos:

```bash
asdf plugin-add erlang
asdf plugin-add elixir
```

### Instalando Elixir e Erlang

Para instalar o Elixir, basta rodar o seguinte comando:

```bash
asdf install elixir 1.11.3
```

E agora precisamos informar ao asdf qual versão do Elixir deve ser usada pela máquina:

```bash
asdf global elixir 1.11.3
```

Para que o Elixir funcione normalmente é necessário instalar o Erlang e, antes disso, instalar algumas outras ferramentas para que o Erlang funcione. Para o **Linux Ubuntu 20.04 LTS**: 

```bash
apt-get -y install build-essential autoconf m4 libncurses5-dev libwxgtk3.0-gtk3-dev libgl1-mesa-dev libglu1-mesa-dev libpng-dev libssh-dev unixodbc-dev xsltproc fop libxml2-utils libncurses-dev openjdk-11-jdk
```

---

Para diferentes versões e distribuições do Linux, e OSX você pode acompanhar o passo a passo por aqui:

[asdf-vm/asdf-erlang](https://github.com/asdf-vm/asdf-erlang#before-asdf-install)

Agora com as ferramentas instaladas, basta rodar:

```bash
asdf install erlang 23.2
```

E depois é só configurar essa versão para ser usada globalmente pela máquina:

```bash
asdf global erlang 23.2
```

---

## Método de instalação padrão

Para realizar a instalação do Elixir, basta acessar o link e seguir os passos de acordo com seu sistema operacional:

[Installing Elixir](https://elixir-lang.org/install.html)

Caso queira, você pode seguir por aqui mesmo mas prefira sempre seguir diretamente do site oficial para o caso de alguma atualização no método de instalação.

### Windows

Para o Windows, usaremos o gerenciador de pacotes Chocolatey. A instalação por meio dele evita alguns problemas, facilita a atualização e também, em caso de necessidade, a desinstalação.

Se você já possui o Chocolatey instalado, pode partir direto para a instalação do Elixir [clicando aqui](https://www.notion.so/Configura-es-do-ambiente-9d73d4eefa7043f593d9c768922306ca).

Para instalar o **Chocolatey** seguiremos os passos citados no site oficial:

[Chocolatey - The package manager for Windows](https://chocolatey.org/)

1. Busque no campo de busca do Windows por **Windows PowerShell**, clique com o botão direito em cima do programa e escolha a opção **Executar como administrador**.

    O Powershell trabalha com um esquema de autorizações (conhecido como `Execution Policy`) para execução de scripts e, por isso, precisamos verificar se o presente no sistema está compatível com o que o Chocolatey precisa. 

2. Execute o seguinte comando:

```powershell
Get-ExecutionPolicy
```

Caso ele retorne `Restricted`, execute o comando:

```powershell
Set-ExecutionPolicy RemoteSigned
```

E escolha a opção `[A] Sim para Todos`

Caso o comando acima apresente erro, tente usar:
`Set-ExecutionPolicy Bypass -Scope Process`

Verifique se alteração de permissão ocorreu com sucesso executando novamente o comando:

```powershell
Get-ExecutionPolicy
```

 3.  Alterada a permissão, basta instalar o **Chocolatey** com o comando:

```powershell
Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))
```

Caso o comando acima apresente um erro, verifique se a sua máquina atende às requisições mínimas

`Windows 7+ / Windows Server 2003+
PowerShell v3+
.NET Framework 4.5+`

Caso o erro apresentado seja `Exceção ao definir "SecurityProtocol": "Não é possível converter o valor "3312"`, siga **[esse guia](https://chocolatey.org/blog/remove-support-for-old-tls-versions)**

 4.  Após o fim da instalação, feche, abra o Powershell como **administrador** novamente e execute:

```powershell
choco -v
```

Caso ele retorne a versão do **Chocolatey**, a instalação foi um sucesso. Para finalizar, basta instalar a versão mais recente do Elixir com o seguinte comando (ainda com o PowerShell em modo administrador:

```powershell
cinst elixir
```

Ao realizar a instalação do Elixir com sucesso, você pode verificar se deu tudo certo rodando `elixir --version` no terminal. Caso retorne algum erro, reinicie sua máquina e tente novamente e se mesmo assim o erro persistir, você pode seguir a recomendação de adicionar manualmente o Elixir nas configurações de variáveis de ambiente do seu sistema operacional. A seção (chamada **Setting PATH environment variable**) está logo abaixo das instruções de download no site do Elixir linkado [aqui](https://www.notion.so/Ambiente-de-desenvolvimento-Trilha-Elixir-aa2399b4ec17447582d04cbce8ffa12f).

### Debian/Ubuntu

Aqui teremos duas opções de instalação: uma normal e outra usando o **asdf** que é um gerenciador de versões de runtimes

1. Adicione o repositório do Erlang:

    ```bash
    wget https://packages.erlang-solutions.com/erlang-solutions_2.0_all.deb && sudo dpkg -i erlang-solutions_2.0_all.deb
    ```

2. Rode:

    ```bash
    sudo apt-get update
    ```

3. Instale o Erlang:

    ```bash
    sudo apt-get install esl-erlang
    ```

4. Instale o Elixir:

    ```bash
    sudo apt-get install elixir
    ```

### macOS

1. Atualize o Homebrew para a ultima versão:

    ```bash
    brew update
    ```

2. Instale o Elixir rodando o seguinte comando:

    ```bash
    brew install elixir
    ```

Ao realizar a instalação do Elixir com sucesso, você pode verificar se deu tudo certo rodando `elixir --version` no terminal. Caso retorne algum erro, reinicie sua máquina e tente novamente e se mesmo assim o erro persistir, você pode seguir a recomendação de adicionar manualmente o Elixir nas configurações de variáveis de ambiente do seu sistema operacional. A seção (chamada **Setting PATH environment variable**) está logo abaixo das instruções de download no site do Elixir linkado acima ([ou clicando aqui](https://elixir-lang.org/install.html)).

## Phoenix

O Phoenix é um framework para a construção de aplicações web que também será usado ao longo da jornada, e por isso é importante que você faça também essa instalação.

Com o Elixir instalado corretamente, basta rodar o seguinte comando para instalar o Phoenix:

```bash
mix archive.install hex phx_new 1.5.8
```

Caso pergunte algo, basta aceitar tudo com `Y`.

Você pode também acompanhar isso na documentação do Phoenix e checar se está com a versão mais recente:

[Installation](https://hexdocs.pm/phoenix/installation.html#phoenix)

---

# Instalação do PostgreSQL

## Instalação padrão (Sem Docker)

Para instalar o PostgreSQL na sua máquina basta escolher a opção adequada para o seu sistema operacional e fazer a instalação como recomendado:

[Downloads](https://www.postgresql.org/download/)

Caso queira, você pode seguir os passos listados aqui de forma mais simples.

### Linux Ubuntu 20.04 LTS

Para a instalação no Linux Ubuntu rode os seguintes comandos separadamente:

```bash
sudo sh -c 'echo "deb http://apt.postgresql.org/pub/repos/apt $(lsb_release -cs)-pgdg main" > /etc/apt/sources.list.d/pgdg.list'

wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -

sudo apt-get update

sudo apt-get -y install postgresql
```

---

### macOS

A instalação no macOS é bem mais simples. Com o Homebrew, basta rodar:

```bash
brew install --cask postgres
```

### Windows

Para o Windows a única forma de instalação disponível é através do instalador. Você pode realizar o download através desse link:

[PostgreSQL Tutorials, Resources and Training | EDB](https://www.enterprisedb.com/postgresql-tutorial-resources-training?cid=437)

## Instalação do PostgreSQL com Docker

Se você não conseguiu instalar o PostgreSQL localmente na sua máquina, é possível instalar usando o Docker mas prefira a instalação padrão quando possível. 

Para isso, antes precisaremos do Docker instalado:

### Instalação do Docker

O Docker é uma ferramenta que nos permite pular as etapas chatas de configuração de serviços para nossa aplicação. Além disso, ele permite reaproveitarmos o Kernel da máquina hospedeira entre vários serviços executados simultaneamente, conhecidos como containers.

Para iniciar a instalação do Docker vamos prosseguir para a seção "**Get Started**" presente no site da ferramenta: 

[Get Started with Docker | Docker](https://www.docker.com/get-started)

---

**Windows (64 Bit)**

O Docker no Windows possui alguns requisitos: 

- Microsoft Windows 10 Professional  ou Enterprise 64-bit
- Caso você possua o Windows 10 Home 64-bit também é possível usar o Docker mas será necessário instalar o WSL2 também (o instalador já se encarrega disso para você)

Caso você possua o Windows 10 32-bit, o Docker não é compatível e a instalação de serviços como banco de dados deverá ser feita diretamente no sistema operacional conforme mencionado [aqui](https://www.notion.so/Configura-es-do-ambiente-9d73d4eefa7043f593d9c768922306ca). 

Caso tenha todos requisitos, então faça a instalação do Docker para Windows:

[Docker Desktop for Mac and Windows | Docker](https://www.docker.com/products/docker-desktop)

Depois de instalar o Docker e abrir o software você já está pronto para continuar. Lembrando que essa versão do Docker para Windows tem uma interface visual muito bacana, ou seja, você pode usar a interface para visualizar os serviços sendo executados, logs, imagens e muito mais.

Para verificar que o Docker foi instalado corretamente, em **uma nova janela** do terminal execute:

```bash
docker version
```

---

**Windows (32 Bit)**

Infelizmente o Docker não possui suporte para sistemas 32 Bit, nesse caso é recomendável que você instale manualmente cada serviço (como o PostgreSQL que será utilizado nessa trilha). 

Na [seção de instalação do Postgres para o Windows](https://www.notion.so/Configura-es-do-ambiente-9d73d4eefa7043f593d9c768922306ca) deixaremos um link para que você possa instalar o PostgreSQL manualmente.

---

**Mac OSX**

No macOS o processo de instalação do Docker é extremamente simples, você precisa apenas baixar o app executável e executa-lo na máquina para iniciar o Docker:

[Docker Desktop for Mac - Docker Hub](https://hub.docker.com/editions/community/docker-ce-desktop-mac)

Depois de aberto você pode garantir que o Docker foi instalado corretamente executando o comando abaixo em uma nova janela do terminal:

```bash
docker version
```

---

**Linux (Ubuntu/Debian)**

No Linux, vamos instalar o Docker utilizando o `apt`, para isso, em seu terminal, execute os comandos abaixo:

```bash
sudo apt update
sudo apt remove docker docker-engine docker.io
sudo apt install docker.io
```

Agora com o Docker instalado, vamos habilitar para que seu serviço seja iniciado automaticamente com o sistema:

```bash
sudo systemctl start docker
sudo systemctl enable docker
```

Para garantir que o Docker foi instalado da forma correta, execute no terminal:

```bash
docker version
```

Você precisará executar todos comandos do Docker utilizando o `sudo`, mas caso queira executa-los sem o `sudo`, utilize [esse guia](https://docs.docker.com/engine/install/linux-postinstall/#manage-docker-as-a-non-root-user).

**Com o Docker instalado na sua máquina, basta rodar no terminal o comando:**

```bash
docker run --name postgres -e POSTGRES_PASSWORD=postgres -p 5432:5432 -d postgres
```

Os dados para autenticação no banco nesse caso serão:
usuário: postgres
senha: postgres

Lembrando que caso você esteja usando Ubuntu/Debian é necessário usar `sudo` antes do comando.

# Configurações para o Visual Studio Code

Para o Visual Studio Code, precisaremos apenas instalar algumas extensões.

## Elixir Linter (Credo)

A primeira delas é a **Elixir Linter (Credo)**. Se atente bem ao nome pois ao buscar por essa extensão no VS Code, você terá vários resultados. 

A correta é essa: 

[Elixir Linter (Credo) - Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=pantajoe.vscode-elixir-credo)

Inclusive você pode clicar para instalar a partir desse link que será solicitada a permissão para abrir no VS Code e instalar a extensão.
Após instalar, acesse as configurações da extensão e deixe as últimas configurações da seguinte maneira:

<img src="https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2Fa07c3649-47c0-4bf7-998f-3af5f1785c54%2FUntitled.png?table=block&id=8b17d068-6bb9-48a8-907c-bf63c3ff3539&width=2040&userId=c0530cfd-b499-49b5-9557-57b445ee0294&cache=v2" width="708" height="283.9">

## ElixirLS

A próxima extensão a ser instalada é a ElixirLS, que também pode ser acessada diretamente pelo link:

[ElixirLS: Elixir support and debugger - Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=JakeBecker.elixir-ls)

Após finalizar a instalação, precisamos ajustar duas pequenas coisas nas configurações da própria extensão. Para isso, clique no ícone da engrenagem e depois em "Extension Settings".

Aqui você irá desmarcar a primeira caixinha que diz "Elixir LS: Dialyzer Enabled":

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/474c4c38-3efe-4c7f-b168-a14c6635f9e4/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/474c4c38-3efe-4c7f-b168-a14c6635f9e4/Untitled.png)

E mais abaixo, desmarque também a opção que diz "Elixir LS: Suggest Specs":

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/8cdf63ad-5e4f-4abc-bddc-881ea4ffdb10/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/8cdf63ad-5e4f-4abc-bddc-881ea4ffdb10/Untitled.png)

---

# Instalando o Insomnia

Antes de instalar o Insomnia, é importante ressaltar que ele é compatível somente com sistemas 64-bit. Mas você pode usar o [Postman](https://www.postman.com/) que é bastante semelhante ao Insomnia e é acessado diretamente pelo navegador.

## Windows

Para instalar o Insomnia no Windows, basta fazer o [download do instalador](https://updates.insomnia.rest/downloads/windows/latest?app=com.insomnia.app&source=website) e concluir a instalação.

## Linux

Para instalar o Insomnia no Linux, você pode usar o snapd que é semelhante à um gerenciador de pacotes. Com ele podemos instalar diversos aplicativos com um único comando.

Para verificar se você possui ou não o snapd instalado, pode checar nesse link: 

[Installing snapd | Snapcraft documentation](https://www.notion.so/image/https%3A%2F%2Fassets.ubuntu.com%2Fv1%2F4726d040-Snap%2Blogo%2Bwhite%2Bbg.jpg?table=block&id=387a2274-cb14-4bef-b3be-4874dccc0b2c&width=500&userId=c0530cfd-b499-49b5-9557-57b445ee0294&cache=v2)

Se a distribuição Linux instalada na sua máquina estiver na seção **Distributions without snap pre-installed** significa que você não possui o snapd instalado. Para instalar basta clicar no link com o nome da sua distribuição e você irá para uma página com o passo a passo para a instalação. 

Com o snapd instalado, tudo que você precisa fazer é rodar o seguinte comando no seu terminal:

```bash
sudo snap install insomnia
```

## Mac

Para instalar o Insomnia no Mac, você pode fazer isso através do disk image que pode ser [baixado diretamente do site do Insomnia](https://updates.insomnia.rest/downloads/mac/latest?app=com.insomnia.app&source=website) ou você pode instalar usando o Homebrew através do seguinte comando:

```bash
brew install --cask insomnia
```

# FAQ

### Windows

- **Invoke-Expression : Não é possível localizar um parâmetro que coincida com o nome de parâmetro 'S'.**

Tem alguma sugestão ou encontrou algum problema? Chama a gente na comunidade que iremos te ajudar 💜
