# Relatório de Implementação de Serviços AWS

- **Data:** 19 de janeiro de 2026
- **Empresa**: Abstergo Industries
- **Responsável**: Gabriel de Souza Conceição

## **1. Introdução**

Este relatório apresenta o processo de implementação de ferramentas na empresa Abstergo Industries. O objetivo principal do projeto foi selecionar 3 serviços AWS que permitissem a modernização da infraestrutura de back-end (Java/Spring Boot) com foco em redução de custos imediatos, substituindo gastos fixos por modelos de pagamento por uso (Pay-as-you-go).

## **2. Descrição do Projeto**
O projeto foi estruturado para atacar três frentes: processamento de pedidos, armazenamento de dados e entrega de conteúdo.

### **Arquitetura da Solução**

```mermaid
graph TD
    A[Venda na Farmácia]-->|Trigger| B(AWS Lambda - Java)
    B -->|Salva Receita|   C[Amazon S3]
    B -->|Envia Dados  |   D[AWS Glue]
    D -->|Gera Insight |   E[Relatório de Estoque]
    C -->|Após 30 dias |   F[S3 Glacier]
```

### **Etapa 1: AWS Lambda**
- **Foco da ferramenta**: Computação Serverless (Sem servidor).

- **Descrição de caso de uso**: Substituir servidores EC2 ligados 24/7 para o processamento de notas fiscais e validação de receitas digitais. Como as farmácias têm picos de venda em horários comerciais, o Lambda executa o código em Java apenas quando há uma requisição, eliminando o custo de ociosidade durante a madrugada.

### Etapa 2: Amazon S3 (Simple Storage Service)
- **Foco da ferramenta**: Armazenamento de objetos escalável e de baixo custo.

- **Descrição de caso de uso**: Migrar backups de bancos de dados locais e imagens de receitas médicas para o S3. Utilizando as Lifecycle Policies (S3 Intelligent-Tiering), o sistema move automaticamente documentos antigos para classes de armazenamento mais baratas (como Glacier), reduzindo drasticamente o custo de storage de longo prazo.


### **Etapa 3: AWS Glue**
- **Foco da ferramenta**: Integração de dados (ETL) e redução de custos em Analytics.

- **Descrição de caso de uso**: Consolidar dados de vendas de diferentes filiais para gerar relatórios de estoque. O Glue permite processar grandes volumes de dados sem a necessidade de manter uma infraestrutura de Big Data ativa o tempo todo, permitindo que a farmácia preveja a demanda e evite desperdício de medicamentos vencidos.


## **3. Conclusão**
A implementação das ferramentas na Abstergo Industries tem como esperado uma redução de até 40% nos custos operacionais de TI no primeiro trimestre. Além da economia direta, a empresa ganha em agilidade, pois a infraestrutura agora escala automaticamente conforme o volume de vendas, garantindo que o sistema de vendas nunca fique lento para o cliente final.

## **4. Anexos**

* [Cálculo de Estimativa de Custos (AWS Calculator)](https://calculator.aws/#/) - Simulação de gastos mensais para a infraestrutura da farmácia.
* [Documentação de Boas Práticas (AWS Cloud Adoption Framework)](https://aws.amazon.com/it/cloud-adoption-framework/) - Referência para redução de custos e governança.
* [Guia de Preços do AWS Lambda](https://aws.amazon.com/lambda/pricing/) - Detalhamento do modelo "Pay-as-you-go" aplicado ao processamento de pedidos.

## Assinatura do Responsável pelo Projeto:
Gabriel de Souza Conceição