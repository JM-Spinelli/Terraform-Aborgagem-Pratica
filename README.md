``Repositorio Dedicado a evolução em Terraform`` 

<p>O Terraform é uma ferramenta de Infraestrutura como Código (IaC), ou seja, através de código é  possível provisionar e gerenciar infraestrutura em nuvem e local de forma segura e eficiente.<br>
Segue uma estrtura de Provider e Resource, sendo o Provider as infomações configurações necessárias para se conectar ao provedor e a o Resourve as configurações feitas para provisionar a infraestrtura na nuvem escolhida</p>

<h3>Comandos Terraform</h3>

<h4>Principais Comandos</h4>

 - <b>Terraform init -</b> Inicia o Terraform<br>
 - <b>Terraform validate -</b> Faz a valdação do código para determinar se está tudo correto<br>
 - <b>Terraform plan -</b> Apresenta as alterações realizadas no código antes de aplicar<br>
 - <b>Terraform apply -</b> Aplica as alterações realizadas no código Terraform<br>
 - <b>Terraform refresh -</b> Faz com que o sistema entenda modificações realizadas no código<br>
 - <b>Terraform destroy -</b> Deleta toda a infraestrutura cloud criada via código<br>
 - <b>Terraform Output -</b> Exibe na tela informações definidas nos arquivos output<br>
 - <b>Terraform Show -</b> Mostra detalhes do arquivo Tfstate(arquivo de estado atual do código terraform), que é o código principal da infraestrutura em nuvem<br>
 - <b>Terraform * -</b> *<br>
 - <b>Terraform * -</b> *<br>
 - <b>Terraform * -</b> *<br>
 - <b>Terraform * -</b> *<br>

<h3>Arquivos Terraform</h3>
<p>O Terraform tem também sua estrutura de arquivos. A utilização desses arquivos pode sim variar conforme a escolha do profissional, no entanto, os arquivos comunmente utilizados são:</p>

 - <b>main.tf -</b> Como o prórpio nome diz, é o arquivo principal. É nele que são configurados os recursos que mais tarde construirão a infraestrtura cloud.<br>
 - <b>terraform.tfstate -</b> Esse arquivo é um espelho exato do main.tf após executado. Ele presenta o arquivo de estado atual da infraestrutura cloud criada.<br>
 - <b>terraform.tfstate.backup  -</b> É o arquivo de backup do tfstate. Ou seja, caso haja uma alteração errônea no terraform.tfstate ou se perca o arquivo, basta utilizar o tfstate.backup para reestabelecer a infraestrutura.<br>

 <p>Estes arquivos devem ser manipulados sempre com bastante cuidado, pois representam diretamente o código da infraestrtutura executada no provedor cloud. Perder esses arquivos compromete a operação da infraestrutura em caso de qualquer incidente gerada no ambiente de TI.</p> 

#

<h3>Preparando o ambiente Terraform</h3>

Para começo de uso do terraform, vamos realizar a instalação do Visual Studio no computador. Recomendo instalar no seu sitema operacinal de escolha. 
Como estou usando o Ubuntu, sua instalação é muito simples.

<h4>1 - Instalando VS code</h4>

<h5>Comandos com permissão root:</h5> 

```
apt update
apt install gpg -y
apt install wget -y 
apt install software-properties-common apt-transport-https wget -y
wget -qO- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor | tee /etc/apt/trusted.gpg.d/microsoft.gpg >
echo "deb [arch=amd64] https://packages.microsoft.com/repos/code stable main" | tee /etc/apt/sources.list.d/vscode.list
apt update
apt install code -y
```
<h5>Comando no linux para rodar vs code como root</h5>

```
code --no-sandbox --user-data-dir "dirtorio que o vs ta"
```
<h5>Comandos sem permissão root:</h5> 

```
sudo apt update
sudo apt install gpg -y
sudo apt install wget -y 
sudo apt install software-properties-common apt-transport-https wget -y
wget -qO- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor | sudo tee /etc/apt/trusted.gpg.d/microsoft.gpg >
echo "deb [arch=amd64] https://packages.microsoft.com/repos/code stable main" | sudo tee /etc/apt/sources.list.d/vscode.list
sudo apt update
sudo apt install code -y
```
#
<h3>2 - Começando com Terraform </h3>
Com o Vs Code já instalado, começamos a colocar a mão na massa com terraform. 

<h4>1º - Criando pasta para armazenamento de arquivos</h4>

<p>No meu sistema operacional, a fim de manter a melhor organização, iremos criar uma pasta para armazenar todos os arquivos de terraform em um só lugar. Para isso, criarei a pasta ``Projetos``.
 
 ![Meu Print](https://github.com/JM-Spinelli/Minhas-Imagens/raw/main/img1.png)
 </p>

 <h4>2º - Indo para o VS-Code</h4>
 <p>No terminal, dentro da pasta <b>'projeto'</b>, abriremos o Vs code com o comando <b>``code .``</b>
  
 ![Meu Print](https://github.com/JM-Spinelli/Minhas-Imagens/raw/main/img2.PNG)
 
 VS Code já aberto ta pasta <b>'projetos'</b>
 
![Meu Print](https://github.com/JM-Spinelli/Minhas-Imagens/raw/main/img03.PNG)
 
 </p>
<br>
 <h4>3º - Criando arquivo ``main`` </h4>
 <p>
  Para criarmos o arquivo main, basta gerarmos um novo arquivo no Vs code com o nome ``main.tf``. No entanto, antes eu irei criar uma pasta ``terraform`` dedicada para esse nosso primeiro projeto.
 
 ![Meu Print](https://github.com/JM-Spinelli/Minhas-Imagens/raw/main/img04.png)

 
</p>
