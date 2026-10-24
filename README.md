# iLouvor — Plataforma de Gestão de Ministérios de Louvor

**Escalas, repertório musical, integrantes e comunicação em uma única plataforma.**

O **iLouvor** é uma aplicação web Full Stack desenvolvida para organizar a rotina de ministérios de louvor, centralizando escalas, músicas, integrantes, avisos e informações importantes em um só lugar.

O projeto nasceu de uma necessidade prática e evoluiu para uma arquitetura SaaS preparada para atender múltiplas organizações, com membros, permissões e dados organizados por contexto.

**[Acessar o iLouvor](https://ibmmlouvor.com.br)**

---

## 📸 Sobre o projeto

O iLouvor busca simplificar a organização das equipes musicais, facilitando o planejamento de compromissos, a preparação do repertório e a comunicação entre os integrantes.

A plataforma reúne funcionalidades de gestão, automação e controle de acesso em uma aplicação acessível pelo navegador e instalável em dispositivos compatíveis.

## ✨ Funcionalidades

### 📅 Escalas e agenda
- Visualização de escalas e compromissos.
- Organização de escalas mensais.
- Geração automática de escalas.
- Escalas especiais para eventos e datas específicas.
- Organização de integrantes por função musical.
- Distribuição dos integrantes considerando suas funções e a tentativa de evitar repetições em domingos consecutivos.

### 🎵 Repertório musical
- Cadastro, edição, exclusão e pesquisa de músicas.
- Organização das músicas utilizadas nas escalas.
- Biblioteca geral e histórico de repertório.
- Acesso a links de vídeos e plataformas de música.
- Inclusão de músicas na escala com definição do momento do culto.
- Atualização de informações musicais em tempo real por meio do Firestore.

### 👥 Integrantes e organizações
- Cadastro e gerenciamento de usuários.
- Participação de uma conta em múltiplas organizações.
- Gerenciamento de membros e permissões por organização.
- Convites para novos integrantes.
- Controle de participação ativa ou desativada.
- Diferentes níveis de acesso conforme o perfil do usuário.

### 🔔 Comunicação
- Avisos e notificações para os integrantes.
- Envio de e-mails para eventos específicos.
- Mensagens automatizadas, incluindo aniversários, repertórios e versículos.
- Comunicação de informações importantes para a equipe.

### 🔎 Auditoria
- Registro de ações importantes realizadas no sistema.
- Identificação do autor, da operação e da data.
- Consulta de eventos com filtros.
- Acesso restrito conforme as permissões do usuário.

### 📱 Experiência do usuário
- Interface responsiva para diferentes tamanhos de tela.
- Aplicação PWA, com suporte à instalação em dispositivos compatíveis.
- Tema claro, escuro ou conforme a preferência do sistema.
- Notificações visuais para determinadas ações e atualizações.

## 🏢 Arquitetura SaaS

O sistema possui suporte à organização dos dados por igreja ou equipe.

Uma mesma conta pode participar de diferentes organizações, com funções musicais e permissões administrativas definidas individualmente em cada contexto.

A arquitetura inclui:

- Rotas de API associadas à organização.
- Gerenciamento de membros e permissões por organização.
- Fluxo de convites para entrada de novos integrantes.
- Validação da participação do usuário nas operações organizacionais.
- Separação dos dados e das operações entre organizações.

## 🛠️ Tecnologias utilizadas

### Front-end
- React 18
- TypeScript
- Vite
- React Router
- Styled Components
- Framer Motion
- Sonner
- Firebase SDK
- Vite PWA Plugin

### Back-end
- Node.js
- Express 5
- TypeScript
- Firebase Admin SDK
- JWT
- bcrypt
- Helmet
- CORS

### Banco de dados e serviços
- Firebase Cloud Firestore
- Firebase Authentication
- Resend para envio de e-mails
- node-cron para tarefas agendadas
- dayjs para manipulação de datas

### DevOps e publicação
- Git e GitHub
- GitHub Actions
- CI/CD
- Netlify
- Render

## 🏗️ Arquitetura da aplicação

O projeto é dividido em front-end e back-end, com responsabilidades distintas.

```text
iLouvor
│
├── Front-end
│   ├── React
│   ├── TypeScript
│   ├── Vite
│   ├── Providers e gerenciamento de estado
│   └── Integração com API e Firestore
│
├── Back-end
│   ├── Node.js
│   ├── Express
│   ├── API REST
│   ├── Autenticação e autorização
│   ├── Regras de negócio
│   ├── Auditoria
│   └── Tarefas agendadas
│
├── Firebase
│   ├── Authentication
│   └── Cloud Firestore
│
└── Automação
    └── GitHub Actions
```

O front-end utiliza provedores de contexto para organizar funcionalidades como autenticação, usuários, escalas, repertório, notificações e preferências visuais.

O back-end disponibiliza as operações da aplicação, valida as permissões e utiliza o Firestore para persistência dos dados.

## 🔐 Autenticação e segurança

O sistema integra o back-end ao Firebase Authentication para estabelecer sessões autenticadas no navegador. A API utiliza JWT para identificar contas nas requisições.

Entre os mecanismos implementados estão:

- Autenticação e autorização de requisições.
- Controle de acesso conforme o perfil e a organização.
- Validação da participação do usuário nas operações organizacionais.
- Regras de segurança do Firestore para leitura autorizada de músicas.
- Operações de escrita realizadas pela API.
- Proteção de senhas com bcrypt.
- Cabeçalhos HTTP de segurança com Helmet.
- Registro de ações importantes por meio de auditoria.

O back-end também valida o acesso às organizações, pois operações executadas pelo Firebase Admin SDK não são limitadas pelas regras de segurança do Firestore.

## ✉️ Convites de integrantes

A aplicação possui um fluxo para convidar pessoas para uma organização.

Os recursos incluem criação e cancelamento de convites, prazo de validade, aceitação vinculada ao e-mail do convidado e proteção do segredo por meio de hash.

O envio pode ser realizado por e-mail quando o serviço está configurado. Também existe a possibilidade de compartilhar o link do convite manualmente.

## ⚙️ Automação e manutenção

O back-end possui tarefas agendadas para operações como envio de e-mails e manutenção de registros antigos, de acordo com as regras de retenção configuradas.

O projeto também utiliza GitHub Actions para automatizar tarefas e apoiar os processos de publicação.

## 🧪 Testes

A documentação técnica do projeto registra testes com banco simulado e rotas HTTP locais, cobrindo cenários como:

- Controle de acesso entre organizações.
- Permissões administrativas.
- Convites por e-mail.
- Expiração e revogação de convites.
- Aceitação repetida de convites.
- Tratamento de segredos nos registros de auditoria.

A validação das regras de segurança do Firestore no Emulator Suite ou em homologação permanece como uma etapa necessária, conforme a documentação técnica.

## 💻 Minha atuação

Desenvolvi e mantenho o iLouvor, trabalhando em diferentes etapas do ciclo de desenvolvimento de software:

- Desenvolvimento de interfaces com React e TypeScript.
- Implementação e manutenção de APIs REST com Node.js e Express.
- Integração com Firebase e Firestore.
- Implementação de autenticação e controle de permissões.
- Desenvolvimento de funcionalidades para escalas, músicas e comunicação.
- Implementação de recursos para múltiplas organizações.
- Investigação e correção de bugs.
- Integração com serviços externos.
- Configuração de automações e processos de publicação.
- Utilização de ferramentas de inteligência artificial como apoio à investigação de problemas, implementação e revisão de código.

## 🎯 Objetivo do projeto

O iLouvor tem como objetivo facilitar a organização de ministérios de louvor, reunindo em uma única plataforma as ferramentas necessárias para planejar escalas, organizar repertórios e manter os integrantes informados.

O projeto representa minha experiência prática no desenvolvimento e na manutenção de uma aplicação Full Stack, envolvendo interface, API, autenticação, banco de dados, integrações e automações.

## 🔗 Links

- **Aplicação:** https://ibmmlouvor.com.br
- **Portfólio no GitHub:** https://github.com/PatrickBaptist/ilouvor-portfolio

---

**Desenvolvido por Patrick Baptista Coutinho**

*Este repositório apresenta o projeto e suas tecnologias. O código-fonte proprietário da aplicação não está disponível publicamente.*
