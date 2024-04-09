# Automate Terraform with GitHub Actions

This repo is a companion repo to the [Automate Terraform with GitHub Actions tutorial](https://developer.hashicorp.com/terraform/tutorials/automation/github-actions).

## Execução

### 1. Criação de conta no Terraform

Inicialmente, criei uma conta no Terraform e segui as etapas iniciais de setup e criação do workspace "getting-started" seguindo as instruções indicado no Terraform. Essas instruções contemplaram o "clone" do repositório `hashcorp/tfc-getting-started`, a navegação até ele e execução do script `setup.sh`.

<center>
    <img src="/assets/img1.png" width="80%">
</center>
<center>
    <img src="/assets/img3.png" width="80%">
</center>
<center>
    <img src="/assets/img2.png" width="80%">
</center>
<center>
    <img src="/assets/img4.png" width="80%">
</center>
<center>
    <img src="/assets/img5.png" width="80%">
</center>
<center>
    <img src="/assets/img6.png" width="80%">
</center>

### 2. Criação de um novo workspace

Nessa etapa, efetuei a criação de um workspace chamado de `learn-terraform-github-actions` e criei variáveis de ambiente de acordo com as credenciais da AWS.

<center>
    <img src="/assets/img7.png" width="80%">
</center>
<center>
    <img src="/assets/img8.png" width="80%">
</center>
<center>
    <img src="/assets/img9.png" width="80%">
</center>

### 3. Criação do User Token para o Github Actions
<center>
    <img src="/assets/img10.png" width="80%">
</center>

### 4. Criação do repositório e congiguração da "Secret" das Actions

Nessa etapa, criei o repositório com mesmo nome do workspace, levando em consideração as instruções do tutorial e utilizei como base o template `hashicorp-education/learn-terraform-github-actions`

<center>
    <img src="/assets/img11.png" width="80%">
</center>

Em seguida, peguei o User Token criado na etapa 3 e criei uma `Repository Secret` para as Actions desse repositório.

<center>
    <img src="/assets/img13.png" width="80%">
</center>

### 5. Clonando o repositório e alterando o código em uma nova branch

Nessa etapa, clonei o repositório para a minha máquina e fiz as alterações relevantes para o funcionamento do tutorial, que consistem em alterar as variáveis `TF_CLOUD_ORGANIZATION` nos arquivos `terraform-apply.yml`` e `terraform-plan.yml`.

<center>
    <img src="/assets/img14.png" width="80%">
</center>
<center>
    <img src="/assets/img15.png" width="80%">
</center>
<center>
    <img src="/assets/img16.png" width="80%">
</center>

Depois disso, trouxe as alterações para uma nova branch e efetuei o commit e o push após o commit.

<center>
    <img src="/assets/img17.png" width="80%">
</center>

### 6. Abertura do Pull Request e falha na execução do plano

<center>
    <img src="/assets/img18.png" width="80%">
</center>
<center>
    <img src="/assets/img19.png" width="80%">
</center>

Foi aqui que observei uma falha na autenticação com a AWS e concluí que o problema certamente estava no início, quando inseri as credenciais no Terraform.

### 7. Ajustando as variáveis de ambiente da AWS e reexecutando

Aqui, tentei adicionar o AWS_SESSION_TOKEN, que é uma variável que não estava inclusa no tutorial, mas foi uma suposição de como isso poderia garantir a autenticação com a AWS com sucesso.

<center>
    <img src="/assets/img20.png" width="80%">
</center>

Além disso, percebi que a região da AWS configurada no `main.tf` estava incorreta. Portanto, alterei para a região correta e efetuei o commit e o push.

<center>
    <img src="/assets/img21.png" width="80%">
</center>

### 8. Verificação dos resultados

Ao fim, verifiquei que com as modificações que foram feitas, tive sucesso nos resultados.

<center>
    <img src="/assets/img22.png" width="80%">
</center>

<center>
    <img src="/assets/img23.png" width="80%">
</center>

<center>
    <img src="/assets/img24.png" width="80%">
</center>

## Tecnologias

### Terraform
Terraform é uma ferramenta de código aberto desenvolvida pela HashiCorp, projetada para automatizar a infraestrutura de TI de maneira declarativa. Ele permite a criação, atualização e gerenciamento de recursos de infraestrutura em diversos provedores de nuvem e serviços, como AWS, Azure, Google Cloud, entre outros, usando uma linguagem de configuração simples e legível.

### Github Actions
GitHub Actions é um serviço de automação oferecido pelo GitHub, projetado para permitir a criação, execução e automação de fluxos de trabalho diretamente em repositórios do GitHub. Ele permite a execução de tarefas automatizadas, como testes de software, implantações, integração contínua e muito mais, tudo dentro do ambiente do GitHub.

### Amazon Web Services(AWS)
Amazon Web Services (AWS) é uma plataforma de computação em nuvem oferecida pela Amazon. Ele fornece uma ampla gama de serviços de computação, armazenamento, banco de dados, análise, inteligência artificial, Internet das Coisas (IoT), segurança e muito mais, permitindo que empresas e desenvolvedores construam e implantem aplicações escaláveis e altamente disponíveis.

## Conceitos aprendidos

### Infraestrutura como Código (Infra as Code)
Terraform segue o conceito de IaC, o que significa que toda a infraestrutura é definida em arquivos de configuração .yml, permitindo versionamento e rastreabilidade.

### Gerenciamento de Estado
Terraform mantém um estado atual da infraestrutura implantada, permitindo que ele compare esse estado com as definições no código e aplique as mudanças necessárias.

### Actions
GitHub Actions permite que os desenvolvedores configurem facilmente fluxos de trabalho personalizados usando arquivos YAML diretamente no repositório e escala automaticamente para atender à demanda, permitindo a execução de workflows em paralelo e em diferentes ambientes.

