<h1 align="center">:file_cabinet: README.md</h1>

## :memo: Descrição
Instalar executores auto-hostados no servidor linux

## :books: Funcionalidades
* <b></b> Implantar, gerenciamento e executação dos trabalhos por meio do GitHub Actions no em GitHub.com

## :wrench: Tecnologias utilizadas
* Tecnologia; AWS/GITHUB

## :rocket: Rodando o projeto

Depois que as Vms estiverem criada e em execução na AWS, será preciso acessar o GiHUb. Navegue até a página principal do repositório. 

![image](https://user-images.githubusercontent.com/48971064/211009038-a27aeb50-45ae-44a0-bc98-3985e0c5822b.png)

![image](https://user-images.githubusercontent.com/48971064/211009257-f826fbf6-98fe-476c-863e-1a57ada5f3fa.png)

![image](https://user-images.githubusercontent.com/48971064/211010248-138ff65e-1e48-4604-9169-94b15f4cf43a.png)

1. Abaixo do nome do repositório, clique em  'Settings'. 

![image](https://user-images.githubusercontent.com/48971064/211005192-16b4e297-8fdf-4385-aca1-f18481cb90e6.png)

1. Na barra lateral esquerda, clique em  Ações, depois em Executores.

2. Clique em Novo executor auto-hospedado.

![image](https://user-images.githubusercontent.com/48971064/211006027-7e296fcd-05fb-4989-a72f-d70bb7f14a84.png)

3. Selecione a imagem e a arquitetura do sistema operacional do computador do executor auto-hospedado.

![image](https://user-images.githubusercontent.com/48971064/211006234-8131f061-601f-4695-98d9-03591ea18b01.png)

4. Você verá instruções mostrando como baixar o executor e instalá-lo em sua máquina de executor auto-hospedada.
Abra um shell em sua máquina de executor auto-hospedado e execute cada comando shell na ordem mostrada.

Segue os comandos para Download:

* Create a folder
```
mkdir actions-runner && cd actions-runner
```
* Download the latest runner package
```
curl -o actions-runner-linux-arm64-2.299.1.tar.gz -L https://github.com/actions/runner/releases/download/v2.299.1/actions-runner-linux-arm64-2.299.1.tar.gz
```
* Optional: Validate the hash
```
echo "debe1cc9656963000a4fbdbb004f475ace5b84360ace2f7a191c1ccca6a16c00  actions-runner-linux-arm64-2.299.1.tar.gz" | shasum -a 256 -c
```
* Extract the installer
```
tar xzf ./actions-runner-linux-arm64-2.299.1.tar.gz
```

Segue os comandos para configuração:

* Create the runner and start the configuration experience
```
./config.sh --url https://github.com/jonathas32/DevopsTeste --token ALVT2OEK4ORUQNTKYO43YCLDXALZA
```
* Caso apresentar o error: /lib64/libicui18n.so.50: undefined symbol: ucol_setMaxVariable_50

![image](https://user-images.githubusercontent.com/48971064/211013139-e7bfb46e-1d33-4f50-b020-d563dbdf5d28.png)

Será preciso realizar a Instalação do .NET 5 no Amazon Linux 2 para ARM64 
segue o link: https://gist.github.com/Sunlighter/fe602d2a090e64a01c3369fe7d7d7325

* Last step, run it!
```
./run.sh
```
## :soon: Implementação futura
* O que será implementado na próxima sprint?

## :handshake: Colaboradores
<table>
  <tr>
    <td align="center">
      <a href="http://github.com/tatialveso">
        <img src="https://avatars.githubusercontent.com/u/56259137?v=4" width="100px;" alt="Foto de jonathas Benevides no GitHub"/><br>
        <sub>
          <b>Jonathas Benevides</b>
        </sub>
      </a>
    </td>
  </tr>
</table>

## :dart: Status do projeto
