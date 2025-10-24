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

No meu sistema operacional, a fim de manter a melhor organização, iremos criar uma pasta para armazenar todos os arquivos de terraform em um só lugar. Para isso, criarei a pasta ``Projetos``.
<img src="https://github.com/JM-Spinelli/Minhas-Imagens/raw/main/img1.png" alt="Meu Print" width="2000">


 <h4>2º - Indo para o VS-Code</h4>
 No terminal, dentro da pasta <b>'projeto'</b>, abriremos o Vs code com o comando <b>code .</b>
 <img src="https://github.com/JM-Spinelli/Minhas-Imagens/raw/main/img2.png" alt="Meu Print" width="2000">
 
 VS Code já aberto ta pasta <b>'projetos'</b>
 <img src="https://github.com/JM-Spinelli/Minhas-Imagens/raw/main/img3.png" alt="Meu Print" width="2000">

<br>
 <h4>3º - Criando arquivo <b>main</b> </h4>

  Para criarmos o arquivo main, basta gerarmos um novo arquivo no Vs code com o nome `` main.tf ``. No entanto, antes eu irei criar uma pasta chamada ``terraform`` dedicada para esse nosso primeiro projeto.<br>
  
  <b>3.1</b> - Pasta Criada
  
  <img src="https://github.com/JM-Spinelli/Minhas-Imagens/raw/main/img4.png" alt="Meu Print" width="2000">
 
  <b>3.2</b> - Abrindo terminal e elevando user para root
  <img src="https://github.com/JM-Spinelli/Minhas-Imagens/raw/main/img05.png" alt="Meu Print" width="2000">
  ![Meu Print](https://github.com/JM-Spinelli/Minhas-Imagens/raw/main/img006.png)

  <b>3.3</b> - Arquivo criado a partir do comando ``touch main.tf``
  ![Meu Print](https://github.com/JM-Spinelli/Minhas-Imagens/raw/main/img007.png)
  ![Meu Print](https://github.com/JM-Spinelli/Minhas-Imagens/raw/main/img008.png)<br>
  Recomendo fazer desta forma, pois assim você conseguirá executar todos os comando do terraform sem a necessidade de a cada comando digitar ``sudo`` no início de cada comando. <br><br>

  <h4>4º - Difinindo as configurações principais do <b>main.tf</b></h4>
  Antes de começarmos a criar o recursos (resources) em si, primeiro precisamos criar as definições do provedor, de versão do terraform e estabelecer a comunicação com a nossa conta aws. 

   <b>1º - Definição de ``provider`` e ``versao``</b>
   
  Para definir o provdor e a versão, estruturamos da seguinte forma
  ```
  terraform {
  required_providers {
   aws = {
    source = "hashicorp/aws"
    version = "~>5.0"
    }
 }
  required_version = ">= 1.12.2"
}
```
Imagem exemplo

![Meu Print](https://github.com/JM-Spinelli/Minhas-Imagens/raw/main/img009.png)

<b>Explicando</b>
 - <b>terraform {} -</b> Este é o bloco terraform e ele server justamente para configurar o próprio Terraform antes de qualquer recurso ser declarado. Esse bloco define configurações globais que afetam todo o comportamento do Terraform <br>
 - <b>required_providers -</b> É dentro dessa estrutura que eu informo o meu terraform que provider eu vou utilizar (Aws, Azure, Gcp etc), sua origem (caminho se onde vai buscar seus pacotes e dependências, e a última versão lançada do pelo provedor, que contempla as últimas atualizações.<br>
 - <b>required_version -</b> É o local onde defino qual a versão do terraform eu utilizarei. É recomendável sempre utilizar a última lançada para pegar todas as atualizações<br>
 
 Veja, todas essa definições ficam dentro do bloco de terraform porque são informações necessárias para que o terraform funcione adequadamente. 

 <b>2º - Definição de usuário </b>
 Para que o terraform possa conversar com a console AWS, é necessário que seja criado um usuário (podendo ser uma Role ou um par de chaves) para que a infraestrutura seja provisionada via código. Sendo assim, você primeiro irá configurar um usuário no IAM da sua console e após ele estar criado, setar ele no terraform. 

 Usuario criado no IAM
 
 ![Meu Print](https://github.com/JM-Spinelli/Minhas-Imagens/raw/main/img10.png)

 Definição de usário no código terraform
 ![Meu Print](https://github.com/JM-Spinelli/Minhas-Imagens/raw/main/img11.png)

 ```
provider "aws" {
profile = "jm-tf"
region = "us-east-1"
}
```
Observação: A região é a mesma em que seu ambiente está executando. Eu coloquei us-east-1, por a região em que minha infra esta.
#

 <h3>3º Lançando primeiro recurso na console AWS</h3>
 
 Os resources - que são os recursos da AWS - é o que provisiona a infraestrtura da console aws. Para utilizarmos, usamos a seguinte estrtutura ``resource "tipo-de-recurso" "nome-recurso" {}``

 Como exemplo, EC2 lançada. Após o script pronto, iniciado o terraform (terraform init) e aplicado a código (terraform apply)
 ![Meu Print](https://github.com/JM-Spinelli/Minhas-Imagens/raw/main/img15.png)

  EC2 lançada na console AWS
  ![Meu Print](https://github.com/JM-Spinelli/Minhas-Imagens/raw/main/img14.png)
 
 ```
resource "aws_instance" "Minha-EC2" {
 intance_type = "t3.micro"
 ami = "ami-052064a798f08f0d3"
 subnet_id = "subnet-0c1f2ca01ca4b66d7" #Subnet da VPC
 security_groups = ["sg-0268d6a0a7c8ebe9e"] #Security Group atribuído a EC2
}
```
Uma observação importante é que, exceto ao utilizar uma VPC Default (criada pela própria AWS), ao lançar uma EC2 é necessário definir uma Subnet_id e um Security_Group para que a EC2 seja lançada com sucesso. 

#

 <h3>4º Criando Security Group </h3>
 
 O security group é bem simples de lançar. Sem que o adicione a uma VPC ou Uma EC2, basta apenas duas configurações, a ``description`` e a ``name``. 
 ![Meu Print](https://github.com/JM-Spinelli/Minhas-Imagens/raw/main/img16.png)
 
 ```
 resource "aws_security_group" "SG-custom-2" {
  description = "Meu SG customizado"
  name = "SG-custom-2"
 }
```
observação: Quando você não define uma VPC, esse security group é automaticamente associado a um security group default

 <h4>Adicioando a uma VPC </h4>
 
 Veja que neste exemplo eu irei adicionei uma VPC manualmente (uma VPC customizada criada por mim) e o terraform, ao eu executar um terraform apply, irá realizar um ``replaced``. Ou seja, irá derrubar o que está rodando para aplicar a nova alteração. Essa condição é algo que você tem que ter ciência quando estiver atuando em um ambiente produtivo.
 ![Meu Print](https://github.com/JM-Spinelli/Minhas-Imagens/raw/main/img17.png)

  VPC alterada
  ![Meu Print](https://github.com/JM-Spinelli/Minhas-Imagens/raw/main/img19.png)

 ```
 resource "aws_security_group" "SG-custom-2" {
  description = "Meu SG customizado"
  name = "SG-custom-2"
  vpc_id = "vpc-0efcc7cbfc8c0040c"
 }
```
<h4>Criando regras de entrada (inbound) e saida (outbound)</h4>

É justamente em Inbound e Outbound que estabelecemos a comunicação entre os variados tipos de serviços fornecidos pela AWS. No terraform, o inboud é referenciado como ``ingress`` e o outbound por ``egress``. e dentro do bloco de cada um, adiconamos as configurações.
![Meu Print](https://github.com/JM-Spinelli/Minhas-Imagens/raw/main/img20.png)

```
 resource "aws_security_group" "SG-custom-2" {
  description = "Meu SG customizado"
  name = "SG-custom-2"
  vpc_id = "vpc-0efcc7cbfc8c0040c"

  ingress {
  from_port = "80"
  to_port = "80"
  protocol = "tcp"
  cid_blocks = ["0.0.0.0/0"]
  description = "entrada porta 80" 
    }

  egress {
  from_port = "0" # De todas as portas
  to_port = "0" # Para todas as portas
  protocol = "-1" # Determina a saída para toda as portas
  cidr_blocks = ["0.0.0.0/0"]
  description = "saida para o mundo"
  
   }
 }
```
para atribuir um nome ao security group, utilizamos o bloco ``tags``. 

Definindo Tag no código
![Meu Print](https://github.com/JM-Spinelli/Minhas-Imagens/raw/main/img22.png)

Tag Name
![Meu Print](https://github.com/JM-Spinelli/Minhas-Imagens/raw/main/img21.png)


<h4>5º Criando VPC, Subnet e Internet Gateway</h4>

Para criar uma rede e suas depedências (subnet, route table, Internet Gateway etc), é necessária a criação de diversos blocos de resources. Abaixo, segue contrução total da rede. 

<b>Criação VPC</b>

Para criar a VPC, utilizamos o resouce  ``"aws_vpc" "Identificador_name" { cidr_block = "ip_rede"}``
![Meu Print](https://github.com/JM-Spinelli/Minhas-Imagens/raw/main/img23.png)

![Meu Print](https://github.com/JM-Spinelli/Minhas-Imagens/raw/main/img25.png)

```
resource "aws_vpc" "teste" {
 cidr_block = "10.0.0.0/24"
}
```
O ``Cidr_block`` é um identificador de endereço de rede e também determina a quantidade de endereços deponíveis de hosts. Numa rede ``/24``, temos um total de 256 endereços disponíveis para hosts. 

<b>Criação subnet</b>

Vou criar aqui apenas uma subnet e dini-la para rodar na avaiability_zone a (us-east-1a).
![Meu Print](https://github.com/JM-Spinelli/Minhas-Imagens/raw/main/img24.png)
![Meu Print](https://github.com/JM-Spinelli/Minhas-Imagens/raw/main/img26.png)

```
resource "aws_subnet" "Sub_a" {
 vpc_id = aws_vpc.teste.id
cidr_block = "10.0.0.64/26"
avaibility_zone = "us-east-1a"

tags = {
 name = "Sub-a"
 }
}
```
<br>
<b>Criação Internet Gateway</b>
O internet Gateway (ig) é o recurso que permite a rede interna ter acesso a internet (rede externa). 

![Meu Print](https://github.com/JM-Spinelli/Minhas-Imagens/raw/main/img27.png)
![Meu Print](https://github.com/JM-Spinelli/Minhas-Imagens/raw/main/img28.png)

```
resource "aws_internet_gateway" "my-ig" {
 vpc_id = aws_vpc.teste.id

  tags = {
  name = "my-ig"
}
}
```

<b>Criação Route Table</b>
A Route Table determina para onde o tráfego de rede é direcionado, atuando como um controlador de tráfego da VPC. É nela que setamos o internet Gateway. 

![Meu Print](https://github.com/JM-Spinelli/Minhas-Imagens/raw/main/img29.png)
![Meu Print](https://github.com/JM-Spinelli/Minhas-Imagens/raw/main/img30.png)

```
resource "aws_route_table" "my-rt" {
 vpc_id = aws_vpc.teste.id

route {
 cidr_block = "0.0.0.0/0"
 gateway_id = aws_internet_gateway.my-ig.id
  }
 }
```

<b>Associando Route Table a Subnet</b>
Mesmo criando os resources (subnet, internet gateway e route table, é necessário associá-los através do bloco ``aws_route_table_association``

![Meu Print](https://github.com/JM-Spinelli/Minhas-Imagens/raw/main/img31.png)

![Meu Print](https://github.com/JM-Spinelli/Minhas-Imagens/raw/main/img32.png)

```
resource "aws_route_table_association" "associate" {
 subnet_id = aws_subnet.Sub_a.id
 route_table_id = aws_route_table.my-rt.id
}
```





  
