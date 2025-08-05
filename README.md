# Framework de Testes API - REST Assured + Cucumber

Este projeto implementa um framework de testes automatizados para APIs REST utilizando REST Assured, Cucumber e JUnit.

## 📋 Pré-requisitos

- **Java 24** ou superior
- **Maven 3.6+**
- **IDE** (IntelliJ IDEA, Eclipse, VS Code)
- **API em execução** na porta `http://localhost:3000`

## 🛠️ Configuração do Ambiente

### 1. Clonagem do Projeto
```bash
git clone <url-do-repositorio>
cd testFrameworkRestAssured


2. Instalação das Dependências
mvn clean install


3. Estrutura do Projeto
src/
├── test/
│   ├── java/
│   │   ├── hooks/           # Hooks do Cucumber (setup/teardown)
│   │   ├── maps/            # Classes para gerenciar dados dos testes
│   │   ├── runner/          # Configuração de execução dos testes
│   │   ├── steps/           # Implementação dos steps do Cucumber
│   │   └── utils/           # Utilitários para requisições REST
│   └── resources/
│       └── features/        # Arquivos .feature com cenários BDD


🚀 Execução dos Testes
Execução via Maven
Executar todos os testes
mvn test


Executar testes específicos por tag
# Executar apenas testes de produtos
mvn test -Dcucumber.filter.tags="@produtos"

# Executar teste específico
mvn test -Dcucumber.filter.tags="@criar-produto"

# Executar múltiplas tags
mvn test -Dcucumber.filter.tags="@criar-produto or @editar-produto"


Execução via IDE
IntelliJ IDEA/Eclipse:
Navegue até src/test/java/runner/RunnerTest.java
Clique com botão direito → "Run RunnerTest"
Executar cenário específico:
Abra o arquivo .feature desejado
Clique no ícone de execução ao lado do cenário

📊 Relatórios
Relatório Cucumber
Após a execução dos testes, os relatórios são gerados automaticamente:

# Gerar relatórios
mvn verify

Localização dos relatórios:

JSON: target/reports/cucumberReports.json
HTML: target/reports/cucumber-html-reports/
Visualizar Relatórios
# Abrir relatório HTML no navegador
open target/reports/cucumber-html-reports/overview-features.html


🏷️ Tags Disponíveis
@produtosTodos os testes relacionados a produtos@criar-produtoTestes de criação de produtos@criar-produto-nome-existenteTeste de produto com nome duplicado@criar-produto-sem-tokenTeste de criação sem autorização@buscar-produto-por-idTeste de busca por ID@buscar-produto-inexistenteTeste de busca de produto inexistente@editar-produtoTestes de edição de produtos@editar-produto-sem-tokenTeste de edição sem autorização@deletar-produtoTestes de exclusão de produtos@deletar-produto-inexistenteTeste de exclusão de produto inexistente@deletar-produto-sem-tokenTeste de exclusão sem autorização@listar-produtosTeste de listagem de produtos
⚙️ Configurações
Configuração da API Base
A URL base da API está configurada em UsuariosHooks.java:

RestUtils.setBaseURI("http://localhost:3000");

Configuração do Runner
O arquivo RunnerTest.java contém as configurações principais:

Features: src/test/resources/features/
Tags: @produtos
Glue: steps, hooks
Plugins: Relatórios JSON e console
Snippets: CamelCase

🔧 Personalização
Alterar URL da API
Edite o arquivo src/test/java/hooks/UsuariosHooks.java:

RestUtils.setBaseURI("http://sua-api.com");

Adicionar Novos Cenários
Crie/edite arquivos .feature em src/test/resources/features/
Implemente os steps correspondentes em src/test/java/steps/
Execute os testes para validar
Configurar Novos Relatórios
Edite o pom.xml na seção do plugin maven-cucumber-reporting:

<plugin>
    <groupId>net.masterthought</groupId>
    <artifactId>maven-cucumber-reporting</artifactId>
    <!-- configurações personalizadas -->
</plugin>

🐛 Troubleshooting
Problemas Comuns
Erro de conexão com API:
Verifique se a API está rodando em http://localhost:3000
Confirme se os endpoints estão acessíveis
Falha na autenticação:
Verifique se as credenciais de administrador estão corretas
Confirme se o token está sendo gerado corretamente
Testes falhando:
Execute mvn clean install para recompilar
Verifique se todos os hooks estão funcionando (limpeza de dados)
Logs e Debug
Para habilitar logs detalhados:

mvn test -Dlog4j.configuration=file:log4j.properties


📝 Contribuição
Crie uma branch para sua feature: git checkout -b feature/nova-funcionalidade
Implemente os testes seguindo o padrão BDD
Execute todos os testes: mvn test
Commit suas mudanças: git commit -m "Adiciona testes para nova funcionalidade"
Push para a branch: git push origin feature/nova-funcionalidade
Abra um Pull Request

📚 Tecnologias Utilizadas
Java 24 - Linguagem de programação
Maven - Gerenciamento de dependências
REST Assured - Framework para testes de API REST
Cucumber - Framework BDD para escrita de cenários
JUnit - Framework de testes unitários
JSON Schema Validator - Validação de esquemas JSON

📄 Licença
Este projeto está sob a licença MIT.
