 # Infraestrutura na AWS com Kubernetes

Este repositório tem como objetivo fazer a criação e a exclusão da infraestrutura na AWS com Terraform.

## Configuração do Repositório

A configuração da infraestrutura e a aplicação no Kubernetes são realizadas por meio de pipelines automatizadas. Não é necessário ter o Terraform ou configurações da AWS na máquina local.


## Atualização do Código `main.tf`

Para atualizar o código `main.tf` com as informações necessárias, siga estas etapas:

1. **Subnets:** 
   - Localize a seção relacionada à definição de subnets no arquivo `main.tf`.
   - Substitua os IDs das subnets existentes na sua VPC pelos IDs correspondentes.

Exemplo:
```hcl
subnet_ids = ["subnet-12345678", "subnet-87654321"]
```

2. **ARN da Conta:**
   - Localize a variável `role_arn` no arquivo `main.tf`.
   - Atualize o valor com o ARN do role da sua conta AWS.

Exemplo:
```hcl
role_arn = "arn:aws:iam::123456789012:role/your-role-name"
```

Certifique-se de salvar as alterações após atualizar o código `main.tf`.

## Configuração
Antes de executar a pipeline, certifique-se de configurar as seguintes variáveis de ambiente:

 - AWS_CREDENTIALS: Credenciais de acesso à AWS.
   
Certifique-se de que essas variáveis de ambiente estejam configuradas corretamente para garantir o funcionamento adequado da pipeline.

## Criação da infraestrutura
A Pipeline de criação da infraestrutura acontece automaticamente após dar commit na main, criando:

**Security Group**

Recurso: aws_security_group.web-sg

Nome: api-fiap-sg


**EKS Cluster**

Recurso: aws_eks_cluster.my_cluster

Nome: cluster-terraform


**EKS Node Group**

Recurso: aws_eks_node_group.my_node_group

Nome: my-nodegroup-terraform


## Exclusão da infraestrutura

Para realizar a exclusão de todos os recursos criados na aws é necessario acessar a aba "actions", ir no menu a esquerda chamado "All workflows", e clicar no workflow "Create and Destroy infra".

![image](https://github.com/user-attachments/assets/2be5ae81-26c0-4789-9cb7-79ea75840ff5)

Após selecionado o workflow em questão, basta apenas selecionar o job destroy e confirmar.

![image](https://github.com/user-attachments/assets/0e233d57-59de-4ed5-a923-e452f699fc28)



