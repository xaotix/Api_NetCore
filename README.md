# WEBAPI_MySQL

API .Net Core para consultas em banco de dados MYSQL com retorno de Json


Com:

Autenticação por senha

Autenticação Active Directory

Método post para CRUD

Linguagem: C#

https://youtu.be/i66Zt-WaTnM

[![Video explicativo](http://img.youtube.com/vi/i66Zt-WaTnM/0.jpg)](https://www.youtube.com/watch?v=i66Zt-WaTnM "Video explicativo")

### Tecnologias usadas

Microsoft .Net Core SDK 2.1.1

Linguagem de programação: C#

Banco de dados: MySQL v. 10.2

Certificado SSL: Let’s Encrypt

### Versões das Bibliotecas Usadas
Json 4.6.0

MySQL Data 6.10.9

Active Directory 4.5.0


### Requisitos

Instale os seguintes aplicativos:

[IDE Microsoft Visual Studio Community 2019 ou superior](https://visualstudio.microsoft.com/pt-br/vs/community/)

[.Net Core SDK 2.1.1](https://dotnet.microsoft.com/download/dotnet-core/2.1)

[Extensão Keyoti.Conveyor (para poder testar a API com o Postman)](https://marketplace.visualstudio.com/items?itemName=vs-publisher1448185.ConveyorbyKeyoti)

[Postman versão Desktop (para fazer as requisições HTTP)](https://www.postman.com/downloads/)

[Heidi SQL (para consultar no banco de dados)](https://www.heidisql.com/download.php)

[Mysql v10.2 ou superior](https://www.mysql.com/downloads/)


## Configurando a ferramenta

Vá até o arquivo Vars.cs e edite os campos:

a) Chave_Criptografia = Chave usada para criptografar as senhas

b) BancoUsers = Nome do banco de dados MySQL

c) BancoActiveDirectory = Banco MySQL para gravar dados se for usado Active Directory

d) TabelaUsers = "api_usuarios"

e) Servidor = Nome do servidor MySQL

f) Servidor2 = Nome do servidor MySQL para Active Directory

g) Porta = Porta MySQL (Padrão: 3306)

h) Senha = Senha MySQL

i) Usuario = Usuário MySQL

j) LDAP = Servidor LDAP usado pelo Active Directory


## Utilizando a ferramenta

As chamadas são feitas em POST. É obrigatório o uso dos dados de autenticação para poder rodar.

Os métodos são:

#### https://seu.site.com.br/consultar
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
#### https://seu.site.com.br/cadastrar
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
#### https://seu.site.com.br/apagar
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
#### https://seu.site.com.br/atualizar
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

## [Documentação em PDF] (https://github.com/xaotix/Api_NetCore/blob/main/Documenta%C3%A7%C3%A3o.pdf)


## Montando o Ambiente de Desenvolvimento

### Criando Tabelas

SGBD Utilizado: MySQL

api_usuarios = tabela onde são gravados os registros de usuários

api_usuarios_denunciar = tabela onde são gravados os registros de denúncia

Scripts para criação das tabelas:

Tabela api_usuarios
```mysql
CREATE TABLE IF NOT EXISTS `api_usuarios` (
 `id` int(11) NOT NULL AUTO_INCREMENT,
 `nome` varchar(150) DEFAULT NULL,
 `user` varchar(50) DEFAULT NULL,
 `email` varchar(50) DEFAULT NULL,
 `s` varchar(500) DEFAULT NULL,
 `ultima_edicao` timestamp NULL DEFAULT current_timestamp() ON UPDATE
current_timestamp(),
 `criado` timestamp NULL DEFAULT current_timestamp(),
 PRIMARY KEY (`id`),
 KEY `nome` (`nome`),
 KEY `ma` (`user`) USING BTREE
) ENGINE=InnoDB AUTO_INCREMENT=2 DEFAULT CHARSET=latin1;
```

Tabela api_usuarios_denunciar

```mysql
CREATE TABLE IF NOT EXISTS `api_usuarios_denuncia` (
 `nome` varchar(150) DEFAULT NULL,
 `email` varchar(150) DEFAULT NULL,
 `denunciado_login` varchar(150) DEFAULT NULL,
 `denunciado_id` int(11) DEFAULT NULL,
 `denunciado_nome` varchar(150) DEFAULT NULL,
 `denunciado_descricao` varchar(5000) DEFAULT NULL
) ENGINE=InnoDB DEFAULT CHARSET=latin1;
```

### Rodando o código no ambiente de desenvolvimento

Após todos os aplicativos instalados, o servidor MySQL rodando com as tabelas criadas, abra o projeto no Visual Studio Community e coloque rodar.
Utilize as chamadas post demonstradas na documentação acima.

## Contribuições

Crie um git clone e faça os ajustes. Envie uma mensagem privada para analisarmos.

## Licença

[MIT](https://choosealicense.com/licenses/mit/)
