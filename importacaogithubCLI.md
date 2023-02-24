<h1 align="center">:file_cabinet: importacaogithuburl.md</h1>

## :memo: Descrição
Importação de repositorio via Comando/CLI no github 

## :books: Funcionalidades

* <b></b> 
Realizar a importação os repositorio do gitlab, migrando com integridade para o repositório criado no github. 

Dica: o Importador do GitHub não é adequado para todas as importações. Por exemplo, se o código existente está hospedado em uma rede privada, sua ferramenta não conseguirá acessá-lo. Nesses casos, recomendamos importá-lo usando a linha de comando para repositórios Git ou uma ferramenta de migração de código-fonte externa para projetos importados de outros sistemas de controle de versão.

## :wrench: Tecnologias utilizadas
* Tecnologia; GITLAB/GITHUB

![image](https://user-images.githubusercontent.com/48971064/220732325-1001b5b9-b3a9-4b2f-b28e-cb7bf4577161.png)

![image](https://user-images.githubusercontent.com/48971064/220731911-1d49b128-d791-4773-a6ce-5c2312eb8500.png)


## :rocket: Rodando o projeto

Para iniciar a importação no github será necessário acessar primeiramente o gitlab, ir no repositório e copiar a url do micro_serviço. Segue o exemplo:

 * Crie um repositório no GitHub. Você importará o repositório Git externo para este novo repositório.
 * Na linha de comando, faça um clone "vazio" do repositório externo usando a URL clone externo. Isso criará uma cópia integral dos dados, mas sem um diretório de trabalho para editar arquivos, e garantirá uma exportação limpa e recente de todos os dados antigos.
 * 
$ git clone --bare https://external-host.com/EXTUSER/REPO.git

# Makes a bare clone of the external repository in a local directory

* Faça o push do repositório clonado localmente em GitHub usando a opção "mirror" (espelho), que assegura que todas as referências, como branches e tags, são copiadas para o repositório importado.

$ cd REPO.git

$ git push --mirror https://github.com/USER/REPO.git
# Pushes the mirror to the new repository on GitHub.com

* Acessar o botão clone, seleciona copy URL

![image](https://user-images.githubusercontent.com/48971064/220737194-ba02dd33-f9c6-4e6b-a4f1-690acc30b834.png)

* Após ter efetuado o login no github, deverá acessar na parte superior da pagina no canto direito a opção de 'Import repository' 

![image](https://user-images.githubusercontent.com/48971064/220737678-1967246f-0b24-4cbc-b58c-9552457b424c.png)


![image](https://user-images.githubusercontent.com/48971064/220737955-dd21a855-8114-48ed-a0d3-fca6a5c4c4ab.png)

* Será aberta a opção para colar a URL copiada no gitlab, na sequencia deverá add o nome do repositório, marcar a opção como privado e clicar em "Begin Import". 

![image](https://user-images.githubusercontent.com/48971064/220738407-19227050-01a0-4b92-bdc1-cdaa9500b055.png)

* Ao clicar em 'Begin Import' será realizada a importação do repositório automaticamente. 

![image](https://user-images.githubusercontent.com/48971064/220738639-1edf50ce-887b-4b30-9233-7ba75290a954.png)

* Navegue até o repositório importado para que possa vincular a um time ou uma organização.

![image](https://user-images.githubusercontent.com/48971064/220739415-2b4bf9e5-7135-4959-a5e7-c7be72e1006d.png)

* Clica em add repository no 'teams'

![image](https://user-images.githubusercontent.com/48971064/220739674-e3ddb3d8-8a61-461c-87b3-044f4f34e41d.png)

* Add o token de autenticação para proceguir.

![image](https://user-images.githubusercontent.com/48971064/220739777-dc694c85-d921-4aba-8a14-f990aec5bf6b.png)

![image](https://user-images.githubusercontent.com/48971064/220740192-7c4bb9d0-96ad-409e-a9da-b82a881c143c.png)

* Repositório importado com sucesso.

## :handshake: Colaboradores DevOps

| [<img src="https://github.com/jonathas32/DevopsTeste/blob/main/img/john.jpg?raw=true" width=115><br><sub>Jonathas Benevides</sub>](http://github.com/jonathas32) | [<img src="https://github.com/jonathas32/DevopsTeste/blob/main/img/bruno.jpg?raw=true" width=115><br><sub>Bruno Baltazar</sub>](http://github.com/jonathas32) | [<img src="https://github.com/jonathas32/DevopsTeste/blob/main/img/Leandro.jpg?raw=true" width=115><br><sub>Leandro Dionizio</sub>](http://github.com/jonathas32) |
| :---: | :---: | :---: |

## :dart: Status do projeto
