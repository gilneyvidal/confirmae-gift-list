# Confirmaê Gift List

Sistema web separado para criação e gerenciamento de **Lista de Presentes** para eventos.

Este projeto nasce como uma base independente do sistema principal **Confirmaê**, mas preparado para integração futura com o painel do anfitrião.

---

## Status do projeto

Projeto em fase inicial de arquitetura e MVP.

Nesta etapa, o objetivo é construir uma base separada, segura e escalável para o recurso de Lista de Presentes, sem alterar o sistema Confirmaê já existente.

---

## Repositório

Repositório oficial do projeto:

```text
gilneyvidal/confirmae-gift-list
```

---

## Objetivo

Criar um sistema web de Lista de Presentes para eventos, permitindo que anfitriões organizem presentes, cotas, recados e contribuições de convidados.

O sistema deve permitir:

* criação de lista de presentes por evento;
* cadastro de chave Pix do anfitrião;
* itens prontos;
* itens personalizados;
* presentes de valor fechado;
* presentes por cotas;
* convidados identificados ou anônimos;
* mural de recados;
* confirmação manual de contribuições;
* futura integração com o painel do anfitrião do Confirmaê.

---

## Contexto importante

O sistema principal Confirmaê já existe, está aprovado e em uso.

A estrutura atual do Confirmaê inclui:

* múltiplas páginas HTML separadas;
* JavaScript modularizado por área;
* CSS centralizado;
* Firebase Authentication;
* Firestore;
* painel master;
* checkout;
* painel do anfitrião;
* convite;
* portaria;
* manual;
* PWA.

Este novo projeto **não deve alterar o Confirmaê atual nesta fase**.

---

## Regra de isolamento

Este projeto deve nascer separado.

Não é permitido nesta etapa:

* alterar o visual atual do Confirmaê;
* alterar o CSS atual do Confirmaê;
* alterar páginas existentes do Confirmaê;
* alterar JavaScript atual do Confirmaê;
* alterar service worker atual do Confirmaê;
* alterar checkout atual;
* alterar painel master atual;
* alterar painel do anfitrião atual;
* alterar Firebase atual do Confirmaê;
* alterar regras de autenticação atuais;
* fazer merge direto de código;
* reaproveitar automaticamente arquivos do sistema principal.

Qualquer integração com o Confirmaê só deverá acontecer depois que o sistema de Lista de Presentes estiver concluído, testado e validado.

---

## Nome comercial do recurso

Para o cliente final, o recurso deve ser chamado sempre de:

```text
Lista de Presentes
```

O termo `gift list` deve ficar apenas em contexto técnico, como nome do repositório, arquivos, variáveis ou estrutura interna.

---

## Produto futuro avulso

Além da integração com os planos do Confirmaê, o sistema deve ficar preparado para futuramente existir como produto independente:

```text
Confirmaê Presentes
```

Modelo comercial previsto:

```text
Taxa única de R$29,90
```

Esse produto seria destinado a pessoas que desejam apenas uma Lista de Presentes, sem contratar o sistema completo de RSVP, convite, portaria ou outros recursos do Confirmaê.

---

## Regra comercial dentro dos planos do Confirmaê

O index do Confirmaê deverá futuramente informar quais planos incluem ou não a Lista de Presentes.

Exemplo de regra prevista:

```text
Planos menores:
Lista de Presentes disponível por taxa única de R$29,90.
```

```text
Plano mais alto:
Lista de Presentes incluída gratuitamente.
```

A comunicação deve ser simples e clara para o cliente final.

---

## Responsabilidade sobre pagamentos

A plataforma não intermedeia pagamentos.

A Lista de Presentes funciona apenas como ferramenta de organização.

Os pagamentos são feitos diretamente para o anfitrião, usando a chave Pix informada por ele.

O sistema não deve:

* receber dinheiro dos convidados;
* processar pagamentos;
* intermediar transações;
* reter valores;
* validar Pix automaticamente;
* garantir pagamento;
* assumir responsabilidade financeira entre convidado e anfitrião.

Mensagem obrigatória em áreas sensíveis do sistema:

```text
A Lista de Presentes é uma ferramenta de organização. Os pagamentos são feitos diretamente ao anfitrião, por meio da chave Pix informada por ele. A plataforma não recebe, processa, intermedeia, retém ou garante qualquer transação financeira entre convidados e anfitriões.
```

---

## Forma de pagamento

O Pix será sempre direto para o anfitrião.

Cada lista deverá permitir o cadastro de:

* chave Pix;
* tipo da chave Pix;
* nome do recebedor;
* instruções de pagamento;
* observações para os convidados.

---

## Liberação Beta

Na versão Beta, a liberação da Lista de Presentes será manual.

Fluxo previsto:

1. O anfitrião clica em ativar Lista de Presentes.
2. O sistema mostra instruções de uso.
3. O sistema informa se há taxa de R$29,90 ou se o plano já inclui o recurso.
4. O sistema gera uma mensagem formatada para WhatsApp.
5. O anfitrião envia a solicitação para a equipe.
6. A equipe libera manualmente.
7. O painel do anfitrião passa a mostrar a Lista de Presentes ativa.

---

## WhatsApp comercial para liberação

O sistema deve preparar uma mensagem para envio ao WhatsApp comercial do Confirmaê:

```text
11968649673
```

A mensagem deve conter os dados necessários para liberação manual.

Exemplo conceitual:

```text
Olá, quero solicitar a liberação da Lista de Presentes no Confirmaê.

Dados do evento:
Evento: [nome do evento]
Anfitrião: [nome do anfitrião]
Plano: [plano contratado]
ID do evento: [eventId]
E-mail: [email]
WhatsApp: [whatsapp]

Status:
[plano inclui gratuitamente ou taxa de R$29,90 necessária]

Estou ciente de que os pagamentos dos convidados serão feitos diretamente para o Pix do anfitrião e que o Confirmaê funciona apenas como ferramenta de organização.
```

---

## Acesso do anfitrião

O acesso principal do anfitrião deverá acontecer pelo painel do Confirmaê.

O anfitrião não deve precisar:

* criar nova conta;
* criar nova senha;
* fazer login em outro sistema;
* acessar outro painel separado;
* entender a parte técnica da integração.

Fluxo ideal:

```text
Anfitrião entra no Confirmaê
↓
Acessa o painel do evento
↓
Vê o bloco Lista de Presentes
↓
Ativa ou gerencia a lista dentro do próprio painel
```

A separação será técnica, não visual.

---

## Firebase Authentication

O Firebase Authentication foi ativado no novo projeto, mas o sistema principal não deve depender dele para o anfitrião integrado ao Confirmaê.

Uso previsto do Auth:

```text
Anfitrião via Confirmaê:
não precisa de login próprio no confirmae-gift-list.
```

```text
Admin/testes:
pode usar login interno controlado.
```

```text
Produto avulso futuro:
pode usar login próprio caso o Confirmaê Presentes seja vendido separadamente.
```

Não deve haver cadastro público aberto nesta fase.

---

## Experiência no painel do anfitrião

### Antes da liberação

O anfitrião verá um bloco informativo simples:

```text
Lista de Presentes

Receba presentes e contribuições direto no seu Pix, com organização automática pelo Confirmaê.

[ Ativar Lista de Presentes ]
```

Ao clicar em ativar, o sistema deverá exibir:

* explicação de funcionamento;
* informação sobre taxa ou gratuidade;
* aviso de Pix direto ao anfitrião;
* mensagem pronta para WhatsApp;
* botão para enviar solicitação;
* status de aguardando liberação.

---

### Após a liberação

O anfitrião verá um bloco ativo no próprio painel:

```text
Lista de Presentes ativa

[ Gerenciar Lista de Presentes ]
[ Copiar link da lista ]
[ Ver contribuições ]
[ Ver mural de recados ]
```

Dentro de gerenciamento, deverá haver campos para:

* personalizar título da lista;
* personalizar mensagem de boas-vindas;
* cadastrar chave Pix;
* definir tipo da chave Pix;
* informar nome do recebedor;
* escrever instruções para os convidados;
* adicionar imagem ou banner;
* ativar ou desativar presente anônimo;
* ativar ou desativar mural de recados;
* mostrar ou ocultar valores;
* cadastrar itens prontos;
* cadastrar itens personalizados;
* cadastrar itens de valor fechado;
* cadastrar itens por cotas;
* pausar lista;
* reativar lista.

---

## Página pública da lista

A página pública será acessada pelos convidados.

Ela deverá exibir:

* nome do evento;
* nome do anfitrião;
* mensagem de boas-vindas;
* lista de presentes;
* itens disponíveis;
* itens por cotas;
* progresso das cotas;
* botão para presentear;
* mural de recados;
* aviso sobre Pix direto ao anfitrião.

O convidado poderá:

* escolher um item fechado;
* escolher uma ou mais cotas;
* informar nome;
* informar WhatsApp ou e-mail, se desejar;
* presentear anonimamente;
* deixar recado;
* copiar chave Pix;
* registrar intenção de presente.

---

## Tipos de presentes

### Item fechado

Um presente de valor único.

Exemplo:

```text
Micro-ondas
Valor: R$450,00
```

Fluxo:

1. Convidado escolhe o item.
2. Sistema mostra dados Pix do anfitrião.
3. Convidado se identifica ou escolhe anonimato.
4. Convidado pode deixar recado.
5. Sistema registra a intenção.
6. Anfitrião confirma manualmente o recebimento.

---

### Item por cotas

Um presente dividido em várias partes.

Exemplo:

```text
Lua de mel
Valor total: R$2.000,00
20 cotas de R$100,00
```

Fluxo:

1. Convidado escolhe quantidade de cotas.
2. Sistema calcula o valor total.
3. Sistema mostra dados Pix do anfitrião.
4. Convidado se identifica ou escolhe anonimato.
5. Convidado pode deixar recado.
6. Sistema registra a contribuição.
7. Anfitrião confirma manualmente o recebimento.

---

## Mural de recados

O mural de recados faz parte do MVP.

Funcionalidades previstas:

* convidado pode deixar recado ao presentear;
* recado pode aparecer publicamente;
* recado pode ser anônimo;
* anfitrião pode ocultar recados;
* anfitrião pode visualizar os recados no painel;
* recados devem estar relacionados ou não a uma contribuição.

---

## Status de contribuição

Como o pagamento é externo e direto ao anfitrião, o sistema deve tratar contribuições como intenção até confirmação manual.

Status previstos:

```text
pending
confirmed
cancelled
expired
```

Significados:

```text
pending:
intenção registrada, aguardando confirmação do anfitrião.
```

```text
confirmed:
anfitrião confirmou que recebeu.
```

```text
cancelled:
contribuição cancelada manualmente.
```

```text
expired:
reserva ou intenção expirada, caso seja usada regra de prazo.
```

---

## Status da lista

Status previstos:

```text
draft
pendingApproval
active
paused
blocked
finished
```

Significados:

```text
draft:
lista criada, mas ainda incompleta.
```

```text
pendingApproval:
aguardando liberação manual.
```

```text
active:
lista liberada e disponível.
```

```text
paused:
lista pausada pelo anfitrião.
```

```text
blocked:
lista bloqueada pela administração.
```

```text
finished:
evento encerrado.
```

---

## Integração futura com o Confirmaê

A integração ideal será por API.

Fluxo previsto:

```text
Painel do anfitrião no Confirmaê
↓
API de Lista de Presentes
↓
Banco separado do confirmae-gift-list
↓
Página pública da Lista de Presentes
```

O Confirmaê poderá enviar dados como:

```text
confirmaeEventId
eventName
hostName
hostEmail
hostWhatsapp
planType
paymentStatus
giftListEnabled
```

O sistema de Lista de Presentes deverá criar, liberar, bloquear ou sincronizar a lista com base nesses dados.

---

## Botão futuro no painel do Confirmaê

O painel do anfitrião do Confirmaê deverá futuramente conter um bloco ou botão:

```text
Lista de Presentes
```

Estados previstos:

### Lista não solicitada

```text
Ative sua Lista de Presentes

[ Ativar Lista de Presentes ]
```

### Solicitação em andamento

```text
Solicitação em análise

Sua Lista de Presentes está aguardando liberação manual pela equipe Confirmaê.
```

### Lista ativa

```text
Lista de Presentes ativa

[ Gerenciar Lista de Presentes ]
[ Copiar link da lista ]
[ Ver contribuições ]
[ Ver mural de recados ]
```

### Lista pausada ou bloqueada

```text
Lista de Presentes temporariamente indisponível
```

---

## Estrutura inicial prevista do projeto

Estrutura base planejada:

```text
confirmae-gift-list/
│
├── README.md
├── index.html
├── lista.html
├── admin.html
├── painel-simulado.html
│
├── assets/
│   ├── css/
│   │   └── style.css
│   │
│   ├── js/
│   │   ├── firebase-config.js
│   │   ├── app.js
│   │   ├── lista-publica.js
│   │   ├── admin.js
│   │   └── painel-simulado.js
│   │
│   └── img/
```

Observação:

O arquivo `painel-simulado.html` servirá apenas para desenvolvimento e testes antes da integração real com o painel do Confirmaê.

---

## Coleções previstas no Firestore

Coleções iniciais:

```text
users
events
giftLists
giftItems
presetItems
contributions
messages
adminApprovals
integrationLogs
```

---

## Coleção `users`

Guarda usuários internos, admins, testes e possíveis contas futuras do produto avulso.

Campos previstos:

```text
uid
name
email
whatsapp
role
createdAt
updatedAt
```

Roles previstas:

```text
host
admin
```

---

## Coleção `events`

Guarda os dados do evento relacionado à lista.

Campos previstos:

```text
id
ownerUid
eventName
eventType
hostName
eventDate
city
location
description
bannerUrl
sourceSystem
confirmaeEventId
externalEventId
integrationMode
createdAt
updatedAt
```

---

## Coleção `giftLists`

Guarda a lista principal do evento.

Campos previstos:

```text
id
eventId
ownerUid
publicSlug
title
welcomeMessage
pixKey
pixType
pixReceiverName
pixInstructions
giftListEnabled
giftListStatus
planType
addonPaid
isFreeByPlan
activationRequested
activationRequestedAt
activationRequestMessage
activationRequestWhatsappUrl
approvalStatus
approvedBy
approvedAt
integrationSource
confirmaePanelVisible
confirmaeEventId
confirmaeHostUid
integrationCreated
integrationLastSyncAt
giftListUrl
createdAt
updatedAt
```

---

## Coleção `giftItems`

Guarda os presentes cadastrados.

Campos previstos:

```text
id
giftListId
eventId
ownerUid
name
description
imageUrl
itemType
price
quotaTotal
quotaValue
quotaAvailable
quotaReserved
quotaConfirmed
status
sortOrder
createdAt
updatedAt
```

Tipos de item:

```text
fixed
quota
```

Status do item:

```text
available
reserved
partiallyFunded
completed
paused
removed
```

---

## Coleção `presetItems`

Guarda os presentes prontos.

Campos previstos:

```text
id
name
description
suggestedPrice
category
itemType
imageUrl
active
createdAt
```

Categorias previstas:

```text
cozinha
casa
lua_de_mel
cha_de_bebe
casamento
aniversario
formatura
livre
```

---

## Coleção `contributions`

Guarda intenções de presente/contribuição feitas pelos convidados.

Campos previstos:

```text
id
giftListId
giftItemId
eventId
ownerUid
guestName
guestWhatsapp
guestEmail
isAnonymous
quantity
amount
status
messageId
createdAt
confirmedAt
cancelledAt
```

---

## Coleção `messages`

Guarda o mural de recados.

Campos previstos:

```text
id
giftListId
eventId
contributionId
giftItemId
guestName
isAnonymous
message
status
createdAt
hiddenAt
```

Status previstos:

```text
visible
hidden
pendingReview
```

---

## Coleção `adminApprovals`

Guarda liberações manuais da versão Beta.

Campos previstos:

```text
id
giftListId
eventId
ownerUid
status
planType
addonPaid
isFreeByPlan
approvedBy
approvedAt
blockedBy
blockedAt
internalNote
createdAt
updatedAt
```

Status previstos:

```text
pending
approved
blocked
cancelled
```

---

## Coleção `integrationLogs`

Guarda registros da futura integração com o Confirmaê.

Campos previstos:

```text
id
sourceSystem
action
confirmaeEventId
giftListId
payload
status
errorMessage
createdAt
```

Ações previstas:

```text
createGiftListFromConfirmae
enableGiftList
disableGiftList
syncEventData
hostRequestedGiftListActivation
```

Status previstos:

```text
success
error
pending
```

---

## Regras de segurança

O Firestore não deve permanecer aberto em modo teste após a fase inicial.

As regras deverão proteger:

* dados de listas;
* dados de anfitriões;
* contribuições;
* recados;
* área administrativa;
* ações de liberação;
* integrações futuras.

O acesso público deverá ser limitado apenas ao necessário para a página pública da lista.

O painel administrativo deverá ser restrito.

O acesso do anfitrião integrado ao Confirmaê deverá ser controlado por camada segura de integração/API.

---

## Hospedagem

O projeto poderá ser publicado inicialmente via GitHub Pages para testes estáticos.

Porém, para integração profissional por API, será necessário avaliar uma camada backend, como:

```text
Firebase Cloud Functions
Vercel Functions
Netlify Functions
Cloudflare Workers
```

A recomendação técnica inicial é considerar Firebase Cloud Functions por já existir Firebase no projeto.

---

## Roadmap do MVP

### Fase 1 — Base e documentação

* Criar repositório separado.
* Criar Firebase separado.
* Ativar Authentication.
* Ativar Firestore.
* Documentar regras no README.
* Definir estrutura de banco.

### Fase 2 — Interface pública

* Criar página pública informativa.
* Criar página pública da lista.
* Mostrar presentes.
* Mostrar cotas.
* Mostrar mural.
* Exibir aviso sobre Pix direto.

### Fase 3 — Gerenciamento

* Criar painel simulado para desenvolvimento.
* Permitir configurar lista.
* Permitir cadastrar Pix.
* Permitir cadastrar itens.
* Permitir ver contribuições.
* Permitir ocultar recados.

### Fase 4 — Administração Beta

* Criar tela admin.
* Listar solicitações.
* Liberar lista manualmente.
* Bloquear lista.
* Adicionar observações internas.

### Fase 5 — Integração futura

* Criar API de integração.
* Adicionar bloco no painel do anfitrião do Confirmaê.
* Gerar solicitação pelo WhatsApp.
* Sincronizar dados do evento.
* Permitir gerenciamento dentro do painel do anfitrião.

---

## Ordem de desenvolvimento

Os arquivos devem ser criados um por vez.

Ordem sugerida:

```text
1. README.md
2. index.html
3. assets/css/style.css
4. lista.html
5. assets/js/firebase-config.js
6. assets/js/app.js
7. assets/js/lista-publica.js
8. painel-simulado.html
9. assets/js/painel-simulado.js
10. admin.html
11. assets/js/admin.js
```

Nenhum arquivo do Confirmaê atual deve ser alterado nesta fase.

---

## Diretriz de desenvolvimento

Durante o desenvolvimento:

* gerar um arquivo por vez;
* sempre enviar o arquivo completo;
* nunca enviar trechos soltos;
* explicar cada alteração de forma didática;
* pedir validação antes de prosseguir;
* proteger o Confirmaê atual contra regressões;
* manter tudo separado até autorização expressa para integração.

---

## Observação final

Este projeto deve ser desenvolvido com foco em simplicidade para o usuário final.

Muitos anfitriões podem não ter conhecimento técnico.

Por isso, o sistema deve ser:

* intuitivo;
* guiado;
* claro;
* sem termos técnicos;
* com botões objetivos;
* com instruções prontas;
* com mensagens automáticas para WhatsApp;
* com gestão centralizada no painel do anfitrião do Confirmaê na integração final.

A complexidade deve ficar escondida na arquitetura, não aparecer para o cliente.
