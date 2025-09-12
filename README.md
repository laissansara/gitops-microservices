# Repositório de Configuração para o Projeto GitOps com Online Boutique

Este repositório contém os manifestos Kubernetes necessários para a implantação da aplicação de microserviços "Online Boutique". Ele serve como a configuração declarativa para um fluxo de trabalho GitOps gerenciado pelo ArgoCD, como parte de um projeto prático do Programa de Bolsas DevSecOps.

## Visão Geral

O princípio do GitOps dita que um repositório Git deve ser usado para armazenar e versionar o estado desejado de uma aplicação. Este repositório cumpre exatamente esse papel. Ele não contém o código-fonte da aplicação, mas sim um único arquivo YAML que descreve todos os recursos Kubernetes (Deployments, Services, etc.) necessários para que a aplicação "Online Boutique" seja executada em um cluster.

A ferramenta de entrega contínua ArgoCD é configurada para monitorar este repositório. Qualquer alteração feita aqui (como um `git push`) é automaticamente detectada e aplicada ao cluster Kubernetes, garantindo que o ambiente de execução esteja sempre sincronizado com esta configuração.

## Conteúdo do Repositório

A estrutura deste repositório é intencionalmente minimalista para manter a clareza da configuração:

```
.
└── k8s/
    └── online-boutique.yaml
```

* **`k8s/`**: Um diretório para organizar os manifestos Kubernetes.
* **`online-boutique.yaml`**: Um arquivo de manifesto consolidado que contém as definições de todos os microserviços que compõem a aplicação "Online Boutique". Este é o único arquivo necessário para o deploy.

## Como Utilizar

Este repositório não é destinado à execução direta. Ele deve ser utilizado como a fonte (`Source`) em uma configuração de Aplicação (`Application`) no ArgoCD.

As configurações essenciais no ArgoCD para utilizar este repositório são:

* **`Repository URL`**: `https://github.com/laissansara/gitops-microservices`
* **`Revision`**: `HEAD`
* **`Path`**: `k8s`
* **`Destination Namespace`**: Um namespace de destino no cluster Kubernetes (ex: `online-boutique`).

## Projeto Associado

Este repositório de configuração foi criado como parte do projeto "GitOps na Prática", que demonstrou a implantação de uma aplicação cloud-native em um ambiente local utilizando as seguintes tecnologias:

* **Orquestração:** Kubernetes (via Rancher Desktop)
* **Automação de Deploy:** ArgoCD
* **Aplicação:** Online Boutique (Microservices Demo)

A documentação principal do projeto, detalhando todo o processo, desafios e aprendizados, pode ser encontrada no repositório `PB-Compass`:

* **[Documentação Completa do Projeto](https://github.com/laissansara/PB-Compass/tree/main/Projeto-GitOps-Online%20Boutique)**

**Autores do Projeto:**

* Laís Sansara Sampaio Silva
