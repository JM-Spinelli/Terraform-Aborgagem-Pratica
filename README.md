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
 - <b>Terraform plan -</b> Apresenta as alterações realizadas no código antes de aplicar<br>
 - <b>Terraform apply -</b> Aplica as alterações realizadas no código Terraform<br>
 - <b>Terraform refresh -</b> Faz com que o sistema entenda modificações realizadas no código<br>
 - <b>Terraform destroy -</b> Deleta toda a infraestrutura cloud criada via código<br>


#
Para começo de uso do terraform, vamos realizar a instalação do Visual Studio no computador. Recomendo instalar no seu sitema operacinal de escolha. 
Como estou usando o Ubuntu, sua instalação é muito simples.

<h3>1 - Instalando VS code</h3>

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
Com o Vs Code instalado, começamos a sí colocar 

