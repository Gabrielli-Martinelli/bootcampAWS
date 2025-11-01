# AWS CloudFormation 🚀

## O que é 🔍
O **AWS CloudFormation** é um serviço da AWS que permite **automatizar a criação e gerenciamento de recursos na nuvem** através de **templates** escritos em **JSON** ou **YAML**. Com ele, você consegue definir sua infraestrutura como código (*Infrastructure as Code - IaC*), tornando o processo mais rápido, seguro e reprodutível.

## Como funciona  💻
1. Crie um **template** definindo os recursos AWS que deseja provisionar (EC2, S3, VPC, RDS, etc.).
2. Envie o template para o CloudFormation, que cria uma **stack** contendo todos os recursos definidos.
3. Cada stack é **independente**, permitindo criar, atualizar ou deletar todos os recursos de forma automática.

## Benefícios  🏷️
1. **Automação completa**: elimina a necessidade de criar recursos manualmente no console.
2. **Reutilização e versionamento**: templates podem ser reutilizados quantas vezes quiser e versionados em sistemas de controle de versão (Git).
3. **Consistência e padronização**: garante que recursos criados em diferentes ambientes sigam a mesma configuração.
4. **Economia**: você paga apenas pelos recursos provisionados na stack.
5. **Escalabilidade**: permite criar desde recursos simples até arquiteturas complexas.

## 💡 Casos de uso comuns
- Provisionamento de **ambientes de desenvolvimento** padronizados.
- Criação de **arquiteturas multi-camadas** (aplicações web com banco de dados, VPC, balanceadores, etc.).
- **Automatização de atualizações** em infraestrutura existente.
- **Disaster recovery**: replicação rápida de ambientes em diferentes regiões.

## Estrutura básica de um template
Um template CloudFormation geralmente possui:
- **AWSTemplateFormatVersion**: versão do template.
- **Description**: descrição do template.
- **Resources**: recursos que serão criados.
- **Parameters** (opcional): valores passados na criação da stack.
- **Outputs** (opcional): informações retornadas após a criação.

### Exemplo de template JSON simples
```json
{
  "AWSTemplateFormatVersion": "2010-09-09",
  "Description": "Exemplo de template CloudFormation para criar um bucket S3",
  "Resources": {
    "MeuBucketS3": {
      "Type": "AWS::S3::Bucket",
      "Properties": {
        "BucketName": "meu-bucket-exemplo"
      }
    }
  },
  "Outputs": {
    "NomeBucket": {
      "Value": { "Ref": "MeuBucketS3" },
      "Description": "Bucket Exemplo"
    }
  }
}
