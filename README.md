# Validação de CNH integrado com Drools

Este projeto tem como objetivo implementar um sistema de validação de CNHs (Carteira Nacional de Habilitação) utilizando a tecnologia **Drools** para processar e aplicar regras de negócio em objetos CNH, conforme definido nas especificações de negócio. O Drools é um motor de regras de negócios que permite separar as regras do código Java, facilitando a manutenção e expansão das validações.

## Descrição

O projeto utiliza um arquivo `.drl` (Drools Rule Language) para definir as regras de negócio, que são processadas no motor Drools em um sistema Java. As CNHs são verificadas com base em três regras principais:

- **Validade da CNH**: A CNH é inválida se estiver expirada.
- **Pontos da CNH**: A CNH é inválida se tiver mais de 20 pontos.
- **Processamento anterior**: A CNH deve ser validada apenas se ainda não tiver sido processada anteriormente.

Após o processamento das regras, o status da CNH é atualizado para **"válida"** ou **"inválida"** com a causa específica da invalidação (expirada, pontos excedidos, etc.).

## Tecnologias Utilizadas

- **Java**: Linguagem principal para o desenvolvimento da aplicação.
- **Drools**: Ferramenta de Business Rules Management System (BRMS) utilizada para processar e validar as regras de negócio.
- **Maven**: Ferramenta de gerenciamento de dependências e construção do projeto.

## Estrutura do Projeto

- **src/main/java**: Contém as classes Java que definem os objetos CNH e o processamento de regras.
- **src/main/resources**: Contém o arquivo `.drl` com as regras de negócio.
- **src/test**: Contém os casos de teste utilizados para validar a implementação.

## Como Rodar o Projeto

### Pré-requisitos

1. **Java 8+** instalado.
2. **Maven** instalado para gerenciar as dependências do projeto.

### Passos para execução

1. **Clone o Repositório**:
   ```bash
   git clone https://github.com/thiagowaib/cnh-validation-drools.git
   cd cnh-validation-drools
```

2. **Construir o Projeto com Maven**:
Execute o comando abaixo para compilar o projeto e baixar as dependências:
   ```bash
mvn clean install
```

3. **Executar o Programa**:
Após a construção bem-sucedida, execute a classe principal para iniciar o processamento das CNHs e validar as regras de negócio:
   ```bash
mvn exec:java -Dexec.mainClass="com.example.DroolsAplication"
```

4. **Testar o Sistema**:
Existem exemplos de CNHs no diretório de testes que podem ser usados para verificar o funcionamento correto do sistema:
   ```bash
mvn test
```

## Arquivo .drl e Regras de Negócio
As regras de negócio são definidas no arquivo rules.drl, que pode ser encontrado em src/main/resources. As regras aplicadas são:

* Validade: Verifica se a data de validade da CNH expirou.
* Pontos: Verifica se a CNH tem mais de 20 pontos acumulados.
* Processamento: Verifica se a CNH já foi processada anteriormente.

## Demonstração
A seguir, um exemplo do resultado final de uma CNH processada que se mostrou inválida devido à expiração:
[![Exemplo de Execução](https://github.com/thiagowaib/cnh-validation-drools/blob/main/src/test/drool.png?raw=true "Exemplo de Execução")](https://github.com/thiagowaib/cnh-validation-drools/blob/main/src/test/drool.png?raw=true "Exemplo de Execução")

