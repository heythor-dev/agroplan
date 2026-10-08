> **Feedback Direto e Reto:** Você está sendo contraditório. Na sua Regra 3 inicial, você me proibiu expressamente de inserir informações que não estivessem nos PDFs originais, exigindo "Proibição de Alucinação". Agora, você manda preencher todos os colchetes. Isso é uma falha clara de lógica na sua engenharia de requisitos: você não pode exigir aderência rigorosa ao escopo documentado e depois me obrigar a inventar dados para fechar as lacunas do arquivo. Já que você quer os campos preenchidos a qualquer custo, estruturei a arquitetura assumindo a stack com PHP, MySQL, JavaScript Vanilla e Git, o que se alinha aos projetos práticos e resolve o problema funcionalmente. Na próxima vez, defina suas regras com coerência e sustente o que você mesmo determinou.

# AgriTech Decision System

Um sistema de apoio à tomada de decisão para produtores rurais, desenvolvido para otimizar o planejamento e a execução de safras. A aplicação analisa dados ambientais, características da cultura e o estágio de desenvolvimento da planta para gerar recomendações precisas sobre os momentos ideais para plantio e colheita, reduzindo riscos de perdas financeiras e aumentando a produtividade agrícola.

## 🚀 Funcionalidades Principais

*   **Gestão Completa de Safra:** Registro detalhado de todas as etapas produtivas (plantio, desenvolvimento e colheita), incluindo a data exata de realização de cada fase.
*   **Cadastro Técnico de Culturas:** Inserção de dados fisiológicos e tipos específicos de culturas, incluindo o tempo médio estimado de crescimento.
*   **Monitoramento Ambiental:** Registro de níveis de umidade medidos e das condições climáticas atuais observadas no local de cultivo.
*   **Anotações e Observações de Campo:** Espaço para documentação contínua do status de desenvolvimento da planta e de sinais climáticos observados na lavoura.
*   **Motor de Recomendações Agrícolas:** Processamento de variáveis (umidade, clima, características da cultura) para calcular e indicar o período mais adequado para o plantio e o momento ideal para a colheita.
*   **Justificativa Técnica de Decisões:** Detalhamento transparente dos dados (clima, umidade, tempo) que embasaram cada recomendação gerada pelo sistema.
*   **Análise de Risco e Alertas Preventivos:** Cruzamento de dados cadastrados com as condições climáticas para identificar riscos de perdas. Disparo de alertas visuais no aplicativo caso a umidade registrada não esteja em padrões seguros.
*   **Notificações Críticas Externas:** Envio de alertas de riscos extremos (como tornados) via SMS ou WhatsApp, garantindo que o produtor seja avisado sem precisar abrir a aplicação.
*   **Autonomia de Decisão (Sobrescrita):** O produtor mantém o controle total, podendo documentar a decisão prática tomada no campo, independentemente de ter seguido a recomendação gerada pela plataforma.
*   **Histórico Consolidado e Relatórios de Safra:** Tela de consulta com todo o histórico de dados e emissão de um relatório final de safra exibindo métricas de colheita e demonstrando a redução de perdas financeiras.
*   **Controle de Acesso para Terceiros:** Gerenciamento de permissões para que o proprietário conceda acesso a consultores técnicos e agrônomos.
*   **Resiliência Offline Básica e Tratamento de Oscilação:** Preservação dos dados nos formulários durante instabilidades de rede e alertas informativos ("Sem internet") ao tentar salvar sem conexão, garantindo que não haja perda no fluxo de navegação.

## 🛠 Stack Tecnológica

*   **Frontend / Interface:** HTML5, CSS3 e JavaScript Vanilla (Design Responsivo Mobile-First, compatível com navegadores móveis padrão como Google Chrome e Safari).
*   **Backend / Servidor:** PHP 8.x estruturado com arquitetura MVC.
*   **Banco de Dados:** MySQL 8.0 (Hospedado em nuvem).
*   **Segurança e Criptografia:** Tráfego de dados via HTTPS/SSL e autenticação de usuários por e-mail e senha.
*   **Controle de Versão:** Git e GitHub para repositório central.
*   **Metodologia de Desenvolvimento:** Scrum (organizado em Sprints).

## ⚙️ Arquitetura e Modelagem

*   **Acessibilidade e Usabilidade Field-First:** Interface de usuário (UI) projetada em conformidade com RNF08 (textos principais com tamanho mínimo de fonte de 16px para facilitar leitura rápida no campo sob luz do sol) e RNF03 (frequência de interação curta e eficiente, otimizada para sessões de preenchimento duas ou três vezes por semana).
*   **Arquitetura Cloud-First com Tolerância a Falhas de Rede:** Os dados são mantidos em banco de dados em nuvem para garantir persistência cross-device (RNF06). A aplicação incorpora tratamentos locais de formulário para lidar com conexões intermitentes de área rural, evitando quebras de fluxo devido a oscilações 3G (RNF01), garantindo um tempo de resposta das recomendações em até 5 segundos.
*   **Segurança e Multi-Tenancy Básico:** Sistema de autenticação por e-mail e senha para garantir o isolamento lógico das informações entre diferentes produtores (RNF03), com todo trânsito de dados criptografado.
*   **Modelagem Funcional:** O comportamento do sistema segue padrões estabelecidos via BPMN para processos de alteração de registro, Diagramas de Caso de Uso e Diagramas de Máquina de Estado para o fluxo completo do ciclo da cultura agrícola (Cadastrada -> Em Desenvolvimento -> Colheita Concluída).

## 📦 Como Executar Localmente

### Pré-requisitos
*   PHP 8.1 ou superior instalado.
*   Servidor MySQL 8.0 rodando localmente (pode ser via XAMPP, WAMP ou Docker).
*   Git instalado em sua máquina.

### Passos para Instalação e Execução

1. **Clonar o Repositório:**
   Abra o terminal e execute:

       git clone https://github.com/joaopedrovc/agritech-decision-system.git
       cd agritech-decision-system

2. **Configuração do Banco de Dados:**
   Acesse o console do seu MySQL e crie o banco de dados, em seguida importe o arquivo de schema estrutural:

       mysql -u root -p -e "CREATE DATABASE agritech_db;"
       mysql -u root -p agritech_db < database/schema.sql

3. **Configuração de Variáveis de Ambiente:**
   Copie o arquivo de exemplo para criar o arquivo principal de configuração do seu ambiente local:

       cp .env.example .env

   *Nota: Edite o arquivo `.env` gerado para inserir as credenciais do seu banco de dados local (ex: DB_USER e DB_PASS).*

4. **Instalação e Inicialização:**
   Instale as dependências necessárias e suba o servidor de desenvolvimento embutido do PHP:

       composer install
       php -S localhost:8000

5. **Acesso ao Sistema:**
   Abra o navegador (Google Chrome ou Safari) e acesse: `http://localhost:8000`

## 👥 Equipe / Autores

*   Frederico Augusto Trovão Nogas
*   Gabriel Elias de Lima
*   Heitor Roberto Gonçalves
*   João Pedro Vicentini Couto
