# Software Testing Suite: Open Hospital - Vaccine Browser

## 📌 Sobre o Projeto
Este repositório contém o desenvolvimento e a análise de uma suíte de testes de software aplicada à funcionalidade **Vaccine Browser** do [Open Hospital](https://www.openhospital.org/), uma aplicação gratuita e *open-source* projetada para gestão hospitalar. 

O projeto explora a eficácia de diferentes métodos de teste na verificação e validação de sistemas complexos. O foco dos testes foi garantir o bom funcionamento do gerenciamento de vacinas (adição, edição, exclusão e listagem) e o correto tratamento de exceções da aplicação.

## 📁 Estrutura do Projeto
O arquivo principal que contém a suíte de testes unitários e de interface desenvolvida para este projeto está localizado no seguinte caminho dentro do repositório:

```text
software_testing/openhospital-core-1.11.5/src/test/java/org/isf/vacmanager/test/VaccineBrowserManagerTest.java
```

## 🧪 Metodologias de Teste Aplicadas

Para garantir uma validação rigorosa e abrangente, o projeto foi dividido em três abordagens principais:

### 1. Testes de Interface (Caixa Preta)
Foram desenvolvidos testes a nível de sistema focados nas interações entre a interface de gerenciamento de vacinas e a camada de acesso a dados.
* **Técnicas:** Particionamento em classes de equivalência e análise de valores limite dos domínios de entrada (como tamanho do código, descrição, tipo e situação de cadastro no banco de dados).
* **Isolamento e Injeção:** Utilização de recursos avançados do Java, como **Reflexão** (`ReflectTestUtils` do Spring Test) para acessar métodos privados, e funções **Mock** (`IoOperations`) para isolar o ambiente de testes do banco de dados real.
* **Ferramenta de Apoio:** Equivalence Partition Organizer (EPO).

### 2. Testes Baseados em Modelos de Estado
Geração de casos de teste a partir da modelagem de um grafo representando os possíveis fluxos de interação do usuário com a aplicação.
* **Estados Mapeados:** `EmptyList`, `NotEmptyList`, e redirecionamentos para `OHException`.
* **Testes Executados:** *Smoke Test*, *Functional Test* e *Stability Test*.
* **Ferramenta:** GraphWalker.

### 3. Geração Automatizada de Testes
Exploração de caminhos no código para geração automática de cenários de execução focados em maximizar a cobertura.
* **Ferramenta:** EvoSuite.

## 🛠️ Tecnologias e Ferramentas
* **Linguagem:** Java
* **Framework de Testes:** JUnit 5
* **Análise de Mutação:** Pitest (PIT)
* **Modelagem:** GraphWalker
* **Geração Automática:** EvoSuite

## 📊 Resultados e Conclusão
A análise comparativa demonstrou que os **testes de interface, aprimorados por simulação (*mocks*) e reflexão, emergiram como a ferramenta mais eficaz**. Esta abordagem atingiu uma cobertura completa (100%) da classe `VaccineBrowserManager` e um escore de mutação de 61%. 

Em contrapartida, os testes gerados automaticamente pelo EvoSuite, embora tenham alcançado alta cobertura de linhas em alguns pacotes, não foram capazes de matar os mutantes injetados pelo PIT, revelando-se insuficientes para validar as condições específicas das exceções lançadas pelo sistema.

---

## 🚀 Como Executar o Projeto

Como este projeto utiliza o ecossistema Java com JUnit 5, você precisará ter o **JDK** (Java Development Kit) e o **Maven** instalados em sua máquina.

### Clonando o Repositório
```bash
git clone git@github.com:seu-usuario/nome-do-repo.git
cd nome-do-repo
```

### Executar os Testes Unitários e de Interface (JUnit 5)
Para correr a suíte principal de testes desenvolvida:
```bash
mvn test
```

### Executar a Análise de Mutação (Pitest)
Para gerar o relatório de testes de mutação e verificar a resiliência do código:
```bash
mvn org.pitest:pitest-maven:mutationCoverage
```

### Executar os Testes Baseados em Modelos (GraphWalker):
```bash
mvn graphwalker:test
```
