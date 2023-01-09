<h1 align="center">:file_cabinet: README.md</h1>

## :memo: Descrição
Instalação de executores auto-hostados em servidores linux

## :books: Funcionalidades
* <b></b> 
Oferecer mais controle de ferramentas de hardware, sistema operacional e software do que os executores hospedados no GitHub fornecem. Com 
os executores auto-hospedados, você pode criar configurações de hardware personalizadas de acordo com suas necessidades, com o poder de processamento ou a memória para 
executar trabalhos maiores, instalar programas de software disponíveis na sua rede local e escolher um sistema operacional não oferecido pelos executores hospedados no 
GitHub. Os executores auto-hospedados podem ser físicos, virtuais, em um contêiner, no local ou em uma nuvem. 

(Executor auto-hospedado é um sistema que gerencia e executa os trabalhos por meio do GitHub Actions no GitHub.com).

Compatibilidade:

![image](https://user-images.githubusercontent.com/48971064/211373337-ec4be184-09cf-4406-ab66-f7e0eab95c62.png)

## :wrench: Tecnologias utilizadas
* Tecnologia; AWS/GITHUB

## :rocket: Rodando o projeto

Após as Vms geradas e em execução na AWS, será preciso acessar o GiHUB. 

![image](https://user-images.githubusercontent.com/48971064/211009038-a27aeb50-45ae-44a0-bc98-3985e0c5822b.png)

![image](https://user-images.githubusercontent.com/48971064/211009257-f826fbf6-98fe-476c-863e-1a57ada5f3fa.png)

![image](https://user-images.githubusercontent.com/48971064/211010248-138ff65e-1e48-4604-9169-94b15f4cf43a.png)

* Navegue até a página principal do repositório. 
1. Abaixo do nome do repositório, clique em  'Settings'. 

![image](https://user-images.githubusercontent.com/48971064/211005192-16b4e297-8fdf-4385-aca1-f18481cb90e6.png)

2. Na barra lateral esquerda, clique em  Ações, depois em Executores.

3. Clique em Novo executor auto-hospedado.

![image](https://user-images.githubusercontent.com/48971064/211388179-f4dc12a8-d6ab-4763-999c-ae604835dd31.png)

4. Selecione a imagem e a arquitetura do sistema operacional do computador do executor auto-hospedado.

![image](https://user-images.githubusercontent.com/48971064/211006234-8131f061-601f-4695-98d9-03591ea18b01.png)


5. Você verá instruções mostrando como baixar o executor e instalá-lo em sua máquina de executor auto-hospedada.
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

Seguem os comandos para configurações:

* Create the runner and start the configuration experience
```
./config.sh --url https://github.com/jonathas32/DevopsTeste --token ALVT2OEK*************
```
Obs: O token gerado expira, para configuração deverá realizar com agilidade.

* Caso apresente o erro: /lib64/libicui18n.so.50: undefined symbol: ucol_setMaxVariable_50. Será preciso realizar a Instalação do .NET 5 no Amazon Linux 2 para ARM64 

![image](https://user-images.githubusercontent.com/48971064/211013139-e7bfb46e-1d33-4f50-b020-d563dbdf5d28.png)

Segue o passo a passo da instalação do Dotnet.

# Installing .NET 5 in Amazon Linux 2 for ARM64

Esta é uma maneira de instalar o .NET 5 em seu diretório inicial sem modificar o
sistema.

1. Inicie o Amazon Linux 2 e faça login. (Eu recomendo uma instância **m6g.medium**
   para isso, embora os menores possam funcionar. Instâncias ARM maiores irão
   definitivamente funciona, mas custa mais por unidade de tempo.)

2. Obtenha o tarball .NET 5.

```
wget https://download.visualstudio.microsoft.com/download/pr/27840e8b-d61c-472d-8e11-c16784d40091/ae9780ccda4499405cf6f0924f6f036a/dotnet-sdk-5.0.100-linux-arm64.tar.gz
```

3. Descompacte-o em seu próprio diretório.

```
mkdir dotnet5
cd dotnet5
tar -xzf ../dotnet-sdk-5.0.100-linux-arm64.tar.gz
```

4. você pode rodar `./dotnet --version` neste momento, mas você receberá este erro:

```
Cannot get symbol ucol_setMaxVariable_50 from libicui18n
Error: /lib64/libicui18n.so.50: undefined symbol: ucol_setMaxVariable_50
Aborted
```

5. Para corrigir isso, você deve baixar a biblioteca ICU mais recente:

```
cd
wget https://github.com/unicode-org/icu/releases/download/release-68-1/icu4c-68_1-src.tgz
mkdir icubuild
cd icubuild
tar -xzf ../icu4c-68_1-src.tgz
cd icu/source
```

6. Você precisa do compilador C++ para construir a biblioteca ICU.

```
sudo yum install gcc-c++
```

7. Agora você pode configurar e fazer a instalação. Se você escolheu uma instância
   ,por exemplo, com várias CPUs, você pode acelerar esta parte passando o `-j`
   opção de criar.

```
mkdir ~/libicu
./configure --prefix=/home/ec2-user/libicu
make
make install
cd
```

8. Edita o arquivo `.bash_profile` e adicione o seguinte (você pode querer alterar isso
   um pouco dependendo da sua configuração):

Obs: No terminal acesse com o comando: 

```
nano $HOME/.bash_profile
```
![image](https://user-images.githubusercontent.com/48971064/211395351-dc7fceaf-ba36-46f8-bf61-2fb22263cb09.png)

```
PATH=$PATH:$HOME/dotnet5
export PATH
DOTNET_ROOT=$HOME/dotnet5
export DOTNET_ROOT
LD_LIBRARY_PATH=$HOME/libicu/lib
export LD_LIBRARY_PATH
```

9. Aqui estão algumas etapas opcionais de limpeza:

```
rm dotnet-sdk-5.0.100-linux-arm64.tar.gz
rm icu4c-68_1-src.tgz
rm -rf icubuild
```

10. Saia e faça login novamente e confirma a instalação com o comando `dotnet --version`.
   
link de referencia: https://gist.github.com/Sunlighter/fe602d2a090e64a01c3369fe7d7d7325

Após a instalação do Dotnet5, rodar novamente o comando.

```
./config.sh --url https://github.com/jonathas32/DevopsTeste --token ALVT2OEK4O**********
```
* Para finalizar, execute-o!
```
./run.sh
```
![image](https://user-images.githubusercontent.com/48971064/211368154-3c6ff3e1-fadf-4ba3-9d68-0928c7e6040e.png)

![image](https://user-images.githubusercontent.com/48971064/211368016-ca13c1f1-381f-40f0-b2b7-acb83712193a.png)

## :handshake: Colaboradores DevOps
<table>
  <tr>
    <td align="center">
      <a href="http://github.com/jonathas32">
        <img src="https://github.com/jonathas32/DevopsTeste/blob/main/img/john.jpg?raw=true" width="100px;" alt="Foto de jonathas Benevides no GitHub"/><br>
        <sub>
          <b>Jonathas Benevides</b>
        </sub>
      </a>
    </td>
  </tr>
</table>

<table>
  <tr>
    <td align="center">
      <a href="http://github.com/jonathas32">
        <img src="https://github.com/jonathas32/DevopsTeste/blob/main/img/bruno.jpg?raw=true" width="100px;" alt="Foto de Bruno no GitHub"/><br>
        <sub>
          <b>Bruno Baltazar</b>
        </sub>
      </a>
    </td>
  </tr>
</table>

## :dart: Status do projeto
