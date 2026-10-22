# ☁️ Resumo: Nuvem e Sistemas Operacionais

**Disciplina:** Sistemas Operacionais  
**Professor:** Prof. Me. Deivison S. Takatu  
**E-mail:** deivison.takatu@fatec.sp.gov.br  
**Instituição:** Fatec — Faculdade de Tecnologia

---

## 1. Fundamentos da Computação em Nuvem (Cloud Computing)

A transição da infraestrutura física tradicional para a computação em nuvem representa uma mudança na forma de utilizar os recursos computacionais. Em vez de investir na compra de equipamentos e servidores próprios (**CAPEX**), as organizações podem contratar serviços sob demanda (**OPEX**), reduzindo investimentos iniciais e aumentando a flexibilidade.

### Características da Computação em Nuvem

```text
+-------------------------------------------------------------+
|                     COMPUTAÇÃO EM NUVEM                     |
+-------------------------------------------------------------+
|                                                             |
|  Acesso sob     Rede de acesso    Pool de       Mensuração   |
|  demanda        amplo             recursos      automática   |
|                                                             |
|  Imediato       Vários            Recursos      Pagamento    |
|                 dispositivos      compartilhados pelo uso    |
|                                                             |
+-------------------------------------------------------------+
```

### Características essenciais segundo o NIST

- **Autoatendimento sob demanda:** permite que o usuário solicite recursos computacionais sem precisar da intervenção direta do fornecedor.
- **Amplo acesso à rede:** possibilita o acesso aos serviços pela internet usando computadores, celulares e outros dispositivos.
- **Pool de recursos (*Multi-tenant*):** permite compartilhar recursos físicos e virtuais entre diferentes usuários de forma dinâmica.
- **Elasticidade rápida:** possibilita aumentar ou diminuir os recursos computacionais conforme a necessidade.
- **Serviço mensurável:** monitora o consumo dos recursos e permite a cobrança de acordo com a utilização (*pay-per-use*).

---

## 2. Virtualização como Pilar e Alta Disponibilidade

O sistema operacional é responsável por gerenciar os recursos do computador e fornecer uma interface entre o hardware e os programas. A virtualização permite executar diferentes ambientes computacionais em um mesmo servidor físico, aproveitando melhor os recursos disponíveis.

### Componentes da Virtualização

- **Hardware físico:** formado por componentes como processador (CPU), memória RAM, barramentos e controladores de rede.
- **Hypervisor (VMM):** software responsável por criar, executar e gerenciar máquinas virtuais. Exemplos: VMware ESXi e KVM.
- **Máquinas Virtuais (VMs):** ambientes virtuais independentes que possuem seu próprio sistema operacional e executam aplicações.

### Pilares da Alta Disponibilidade em Nuvem

1. **Zonas de Disponibilidade (AZs):** datacenters isolados dentro de uma mesma região, com infraestrutura de energia e rede redundante.
2. **Balanceamento de Carga (*Load Balancer*):** distribui o tráfego entre diferentes servidores ou instâncias para evitar sobrecargas.
3. **Replicação de Dados:** mantém cópias dos dados em diferentes locais para aumentar a disponibilidade e reduzir o risco de perda de informações.
4. **Failover Automático:** transfere automaticamente as operações de um servidor com falha para outro que esteja funcionando.

---

## 3. Modelos de Serviço em Nuvem

Os serviços de computação em nuvem são divididos em três modelos principais: IaaS, PaaS e SaaS.

| Modelo | Nome completo | O que o provedor gerencia? | O que o cliente gerencia? | Exemplos |
|---|---|---|---|---|
| **IaaS** | *Infrastructure as a Service* | Hardware, rede, armazenamento e virtualização. | Sistema operacional, middleware, ambiente de execução e aplicações. | AWS EC2, Azure VMs e Google Compute Engine. |
| **PaaS** | *Platform as a Service* | Hardware, rede, sistema operacional, atualizações e ambiente de execução. | Código-fonte da aplicação e dados, além das configurações sob sua responsabilidade. | Google App Engine, Heroku, Render e AWS Elastic Beanstalk. |
| **SaaS** | *Software as a Service* | Infraestrutura, plataforma e aplicação, incluindo sua manutenção. | Utilização do software e configurações disponíveis ao usuário. | Microsoft 365, Google Workspace, Slack e Salesforce. |

### Diferenças entre os modelos

- **IaaS:** oferece infraestrutura virtualizada para o cliente configurar e administrar.
- **PaaS:** oferece uma plataforma pronta para desenvolver, executar e publicar aplicações.
- **SaaS:** disponibiliza um software pronto para uso, geralmente acessado pela internet.

---

## 4. Modelos de Implantação e Provedores

A computação em nuvem também pode ser classificada de acordo com a forma como sua infraestrutura é disponibilizada.

### Tipos de Nuvem

- **Nuvem Pública:** infraestrutura oferecida por provedores a diferentes clientes, com recursos compartilhados e capacidade de expansão. Exemplos: AWS, Microsoft Azure, Google Cloud Platform e Oracle Cloud.
- **Nuvem Privada:** infraestrutura dedicada a uma única organização, podendo ser mantida internamente ou em instalações de terceiros.
- **Nuvem Híbrida:** combina nuvens públicas e privadas, permitindo distribuir aplicações e dados conforme as necessidades da organização.

### Vantagens e Desafios

| Vantagens | Desafios |
|---|---|
| Redução do investimento inicial em equipamentos (CAPEX). | Dependência de um fornecedor específico (*Vendor lock-in*). |
| Escalabilidade e elasticidade dos recursos. | Atendimento a exigências legais e regulatórias, como a LGPD e o GDPR. |
| Maior resiliência geográfica e disponibilidade, quando bem projetada. | Custos inesperados quando não existe controle de consumo (*FinOps*). |
| Facilidade para utilizar tecnologias de IA e Big Data. | Possível aumento da latência na comunicação pela rede. |

### Modelo de Responsabilidade Compartilhada

Nesse modelo, a segurança é dividida entre o provedor de nuvem e o cliente.

- **Segurança da nuvem:** responsabilidade do provedor, incluindo a proteção da infraestrutura física e dos componentes que administra.
- **Segurança na nuvem:** responsabilidade do cliente, conforme o serviço contratado, incluindo permissões de acesso, configurações, dados e aplicações.

A divisão exata das responsabilidades varia de acordo com o modelo de serviço utilizado.

---

## 5. Containers e Microsserviços

Os containers são uma tecnologia utilizada para executar aplicações em ambientes isolados. Diferentemente das máquinas virtuais tradicionais, eles não precisam incluir um sistema operacional convidado completo para cada instância. Em vez disso, compartilham o kernel do sistema operacional hospedeiro.

### Arquitetura de Containers

```text
+-------------------------------------------------------------+
|                    APLICAÇÕES A E B                         |
+-------------------------------------------------------------+
|                 MOTOR DE CONTAINERS                         |
|                       (Docker)                              |
+-------------------------------------------------------------+
|             SISTEMA OPERACIONAL / KERNEL                    |
+-------------------------------------------------------------+
|                        HARDWARE                             |
+-------------------------------------------------------------+
```

### Principais Tecnologias

- **Docker:** plataforma utilizada para criar, executar e distribuir containers com suas aplicações e dependências.
- **Kubernetes:** ferramenta de orquestração que gerencia containers, automatiza sua distribuição e auxilia na escalabilidade e na recuperação de falhas.
- **Microsserviços:** arquitetura que divide uma aplicação em serviços menores e independentes, cada um responsável por uma função específica. Esses serviços podem se comunicar por meio de APIs, como as APIs REST.

### Diferenças entre Máquinas Virtuais e Containers

| Característica | Máquinas Virtuais | Containers |
|---|---|---|
| Sistema operacional | Cada VM possui seu próprio sistema operacional convidado. | Compartilham o kernel do sistema operacional hospedeiro. |
| Consumo de recursos | Geralmente maior. | Geralmente menor. |
| Inicialização | Normalmente mais demorada. | Normalmente mais rápida. |
| Isolamento | Isolamento por virtualização de hardware. | Isolamento por recursos do sistema operacional. |
| Uso comum | Executar sistemas operacionais diferentes no mesmo servidor. | Empacotar e executar aplicações de maneira consistente. |

---

## 📚 Referências Bibliográficas

TANENBAUM, Andrew S.; BOS, Herbert. *Sistemas Operacionais Modernos*. 4. ed. São Paulo: Pearson, 2016.

SILBERSCHATZ, Abraham; GALVIN, Peter B.; GAGNE, Greg. *Fundamentos de Sistemas Operacionais*. 9. ed. Rio de Janeiro: LTC, 2015.

STALLINGS, William. *Sistemas Operacionais: Conceitos e Projetos*. 8. ed. São Paulo: Pearson, 2015.
