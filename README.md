# Agenda de Contatos

Este é um projeto de uma WEBAPI feita em .NET com C# que utiliza o Entity Framework para criar, ler, atualizar e excluir contatos em um banco de dados SQL Server.

## Instalação

Caso queira rodar este projeto em sua maquina siga essas instruções:

* Clone o repositório para sua máquina local usando git clone https://github.com/juaovitu13/ModuloAPI.git
* Abra o projeto no Visual Studio
* Instale as dependências necessárias executando o comando dotnet restore no terminal do Visual Studio
* Crie o banco de dados com o nome Agenda e a tabela Contatos usando o script a seguir:
```
CREATE DATABASE Agenda
GO

USE Agenda
GO

CREATE TABLE Contatos (
    Id INT PRIMARY KEY IDENTITY,
    Nome VARCHAR(100) NOT NULL,
    Telefone VARCHAR(20) NOT NULL,
    Ativo BIT NOT NULL
)
```
* Altere as configurações de conexão com o banco de dados no arquivo `appsettings.Development.json`
* Execute o projeto com o comando `dotnet watch run` no terminal do Visual Studio, ao executar esse comando será aberto o swagger no seu navegador no endereço: `http://localhost:5236/swagger/index.html`.

## Uso

A API tem as seguintes rotas:

* `GET /Contato/{id}`: Retorna o contato com o id especificado
* `POST /Contato`: Adiciona um novo contato ao banco de dados. O corpo da requisição deve conter o nome, telefone e o status (ativo ou inativo) do contato.
* `PUT /Contato/{id}`: Atualiza as informações de um contato já existente no banco de dados. O corpo da requisição deve conter as informações atualizadas do contato.
* `DELETE /Contato/{id}`: Exclui um contato existente do banco de dados.

## Exemplos

### Adicionando um contato
```
POST /Contato

{
    "nome": "João Silva",
    "telefone": "11 9999-9999",
    "ativo": true
}
```
### Atualizando um contato
```
PUT /Contato/1

{
    "nome": "João Silva",
    "telefone": "11 9999-9999",
    "ativo": false
}
```
### Excluindo um contato
```
DELETE /Contato/1
```
## Criação

Para criar este projeto, eu segui os seguintes passos:

* Criei um novo projeto WEBAPI no Visual Studio usando o modelo padrão.
* Adicionei o pacote do Entity Framework através do gerenciador de pacotes NuGet.
* Criei uma classe de contexto do banco de dados, herdando de DbContext e adicionando uma propriedade DbSet para a minha entidade Contato.
* Utilizei o comando "Add-Migration" do Entity Framework para criar as migrações iniciais e "Update-Database" para aplicar essas migrações no banco de dados.
* Criei controllers e models para lidar com as operações CRUD, usando as classes do Entity Framework para interagir com o banco de dados.
* Adicionei as rotas na classe Startup para que as operações possam ser acessadas através da API.
* Testei minhas operações usando ferramentas de teste de API, como o Postman.
* Foi necessário fazer algumas configurações no arquivo appsettings.Development.json para realizar a conexão com o banco de dados, e também alguns ajustes na classe de contexto do banco de dados para garantir que as operações estão sendo realizadas corretamente. Além disso, algumas validações foram adicionadas nas classes de modelo para garantir que os dados enviados sejam válidos.




