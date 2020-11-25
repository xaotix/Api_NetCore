# WEBAPI_MySQL

API .Net Core para consultas em banco de dados MYSQL com retorno de Json


Com:

Autenticação por senha

Autenticação Active Directory

Método post para CRUD

Linguagem: C#
https://youtu.be/i66Zt-WaTnM

[![Video explicativo](http://img.youtube.com/vi/i66Zt-WaTnM/0.jpg)](https://www.youtube.com/watch?v=i66Zt-WaTnM "Video explicativo")

## Requisitos

Instale os seguintes aplicativos:

Microsoft Visual Studio Community 2019 ou superior
https://visualstudio.microsoft.com/pt-br/vs/community/

.Net Core SDK 2.1.1
https://dotnet.microsoft.com/download/dotnet-core/2.1

Extensão Keyoti.Conveyor (para poder testar a API com o Postman)
https://marketplace.visualstudio.com/items?itemName=vs-publisher1448185.ConveyorbyKeyoti

Postman versão Desktop (para fazer as requisições HTTP)
https://www.postman.com/downloads/

Heidi SQL (para consultar no banco de dados)
https://www.heidisql.com/download.php

Documentação:
https://github.com/xaotix/Api_NetCore/blob/main/Documenta%C3%A7%C3%A3o.pdf

##Tecnologias usadas

Microsoft .Net Core SDK 2.1.1
Linguagem de programação: C#
Banco de dados: MySQL v. 10.2
Certificado SSL: Let’s Encrypt
Bibliotecas:
Json 4.6.0
MySQL Data 6.10.9
Active Directory 4.5.0

## Configurando a ferramenta

Vá até o arquivo Vars.cs e edite os campos:

a) Chave_Criptografia = Chave usada para criptografar as senhas
b) BancoUsers = Nome do banco de dados MySQL
c) BancoActiveDirectory = Banco MySQL para gravar dados se for usado Active
Directory
d) TabelaUsers = "api_usuarios"
e) Servidor = Nome do servidor MySQL
f) Servidor2 = Nome do servidor MySQL para Active Directory
g) Porta = Porta MySQL (Padrão: 3306)
h) Senha = Senha MySQL
i) Usuario = Usuário MySQL
j) LDAP = Servidor LDAP usado pelo Active Directory

## Utilizando a ferramenta

As chamadas são feitas em POST. É obrigatório o uso dos dados de autenticação para
poder rodar.
Os métodos são:
https://seu.site.com.br/consultar
No mínimo 1 coluna da tabela deve ser especificada.
JSON Exemplo:
```json
{
 "user": "usuario",
 "s": "senha",
 "Banco":"nome_banco",
 "Tabela": "api_usuarios",
 "Filtros":
 {
 "id": "%%"
 }
}
```
https://seu.site.com.br/cadastrar
JSON Exemplo:
```jsson
{
 "user": "usuario",
 "s": "senha",
 "Banco":"nome_banco",
 "Tabela":"api_usuarios",
 "Valores":
 {
 "nome": "João da Silva",
 "user": "joao",
 "email": "joao@email.com"
 }
}
```
https://seu.site.com.br/apagar
Por questões de segurança não é possível enviar comandos de apagar vários itens de
uma vez.
JSON Exemplo:
```json
{
 "user": "usuario",
 "s": "senha",
 "Banco":"nome_banco",
 "Tabela":"api_usuarios",
 "Filtros":
 {
 "user": "joao"
 }
}
```
https://seu.site.com.br/atualizar
Chave filtros obrigatória: Determina na busca qual registro será editado.
```json
{
 "user": "usuario",
 "s": "senha",
 "Banco":"nome_banco",
 "Tabela":"tabela",
 "Valores":
 {
 "user": "joao2"
 },
 "Filtros":
 {
 "user": "joao"
 }
}
```
## Contribuições
Crie um git clone e faça os ajustes. Envie uma mensagem privada para analisarmos.

## Licença
[MIT](https://choosealicense.com/licenses/mit/)
