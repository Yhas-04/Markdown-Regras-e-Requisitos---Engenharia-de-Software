# Sistema de Gestão de Portarias
**Documento de Regras de Negócio e Requisitos Funcionais**

---

## 1. Regras de Negócio

As regras de negócio definem as restrições, obrigações e condições que o sistema deve respeitar independentemente de como é implementado.

---

### 1.1 Portarias

**RN001 — Numeração**
- A numeração é gerada automaticamente pelo sistema.
- A sequência é reiniciada a cada ano.
- Não é permitida duplicidade de números no mesmo ano.

**RN002 — Campos Obrigatórios**
Toda portaria deve obrigatoriamente conter:
- Título
- Ementa
- Fundamentação legal
- Texto articulado
- Vigência
- Assinatura
- Data

**RN003 — Categorias**
As categorias permitidas são:
- Normativa
- Administrativa
- Nomeação
- Exoneração
- Comissão
- Grupo de trabalho
- Designação

---

### 1.2 Usuários e Permissões

**RN004 — Perfis**
O sistema deve possuir os seguintes perfis:
- Solicitante
- Área Técnica
- Jurídico
- Assinante
- Publicador
- Administrador

**RN005 — Assinatura**
- Somente usuários com perfil "Assinante" podem assinar portarias.
- Após a assinatura, o texto da portaria é bloqueado para edição.
- A data e o usuário que assinou são registrados automaticamente.

---

### 1.3 Fluxo da Portaria

**RN006 — Fluxo Obrigatório**
Toda portaria deve percorrer obrigatoriamente as seguintes etapas, nesta ordem:
1. Solicitação
2. Elaboração
3. Revisão
4. Assinatura
5. Publicação

Não é permitido pular etapas.

**RN007 — Solicitação**
A solicitação deve conter:
- Justificativa
- Categoria
- Setor
- Participantes
- Vigência pretendida

---

### 1.4 Participantes

**RN008 — Servidores**
- Somente servidores ativos podem participar de portarias.
- Dados obrigatórios: nome, CPF, SIAPE, cargo e lotação.

**RN009 — Comissões**
Comissões designadas por portaria devem possuir:
- Presidente definido
- No mínimo 3 membros
- Data inicial e data final

---

### 1.5 Vigência

**RN010 — Controle de Vigência**
Toda portaria deve possuir:
- Data inicial obrigatória
- Data final ou declaração de vigência indeterminada

**RN011 — Expiração Automática**
- Portarias com data final atingida recebem automaticamente o status **"Expirada"**.

---

### 1.6 Publicação

**RN012 — Publicação Obrigatória**
- A portaria só possui validade jurídica após publicação.
- Locais de publicação aceitos: boletim interno, portal institucional e diário oficial.

---

### 1.7 Auditoria

**RN013 — Histórico de Auditoria**
O sistema deve registrar toda ação realizada, contendo:
- Usuário responsável
- Ação executada
- Data e hora

---

### 1.8 Situações da Portaria

**RN018 — Status Possíveis**
Uma portaria pode estar em um dos seguintes estados:

| Status | Descrição |
|---|---|
| Rascunho | Em preenchimento pelo solicitante ou área técnica |
| Em Revisão | Aguardando análise jurídica |
| Assinada | Assinatura realizada; edição bloqueada |
| Publicada | Publicada e com validade jurídica |
| Expirada | Data final atingida |
| Cancelada | Cancelada antes ou após publicação |

---

### 1.9 Controle e Arquivamento

**RN019 — Versionamento**
- Toda alteração no texto da portaria gera uma nova versão no histórico.

**RN020 — Exclusão**
- Portarias com status "Publicada" não podem ser excluídas, apenas canceladas.

---

### 1.10 Conformidade Legal

**RN021 — Fundamentação Legal**
- Toda portaria deve possuir base legal válida e declarada no preâmbulo.

**RN022 — Conformidade Normativa**

- O sistema deve estar em conformidade com leis. 

---

---

## 2. Requisitos Funcionais

Os requisitos funcionais descrevem o que o sistema deve ser capaz de fazer — suas funcionalidades e comportamentos esperados.

---

### 2.1 Gestão de Portarias

**RF001 — Criação de Portaria**
- O sistema deve permitir a criação de portarias com todos os campos estruturados (RN002).
- O formulário deve validar campos obrigatórios antes de avançar de etapa.

**RF002 — Numeração Automática**
- O sistema deve gerar automaticamente o número sequencial por ano.
- Deve impedir o cadastro de portarias com numeração duplicada (RN001).

**RF003 — Categorização**
- O sistema deve permitir classificar a portaria em uma das categorias previstas (RN003).

**RF004 — Controle de Status**
- O sistema deve atualizar o status da portaria conforme o avanço no fluxo (RN018).
- O status "Expirada" deve ser aplicado automaticamente ao atingir a data final (RN011).

---

### 2.2 Fluxo de Aprovação

**RF005 — Fluxo por Etapas**
- O sistema deve implementar as cinco etapas obrigatórias do fluxo (RN006).
- Cada etapa só deve ser liberada após a conclusão da etapa anterior.
- O sistema deve notificar o responsável da próxima etapa ao avançar.

**RF006 — Formulário de Solicitação**
- O sistema deve disponibilizar formulário de solicitação com os campos exigidos pela RN007.

**RF007 — Elaboração**
- O sistema deve permitir que a área técnica edite e estruture o texto da portaria.

**RF008 — Revisão Jurídica**
- O perfil Jurídico deve ter acesso de leitura e inclusão de parecer, sem alterar o texto original.

**RF009 — Assinatura Digital**
- O sistema deve permitir assinatura apenas por usuários com perfil "Assinante" (RN005).
- Após assinatura, o texto deve ser bloqueado para edição.
- Data, hora e usuário assinante devem ser registrados automaticamente.

**RF010 — Publicação**
- O sistema deve registrar o local de publicação (boletim, portal ou diário oficial) (RN012).
- Somente após publicação a portaria deve ter status "Publicada".

---

### 2.3 Participantes e Servidores

**RF011 — Cadastro de Participantes**
- O sistema deve permitir vincular servidores ativos a portarias (RN008).
- Deve validar os dados obrigatórios: nome, CPF, SIAPE, cargo e lotação.

**RF012 — Gestão de Comissões**
- O sistema deve permitir constituir comissões com presidente e no mínimo 3 membros (RN009).
- Deve registrar data inicial e final da comissão.

---

### 2.4 Controle de Vigência

**RF013 — Vigência**
- O sistema deve exigir data inicial e data final ou marcação de vigência indeterminada (RN010).
- Deve monitorar automaticamente as datas e atualizar o status para "Expirada" quando vencida (RN011).

---

### 2.5 Usuários e Permissões

**RF014 — Autenticação**
- Acesso apenas com conta institucional e senha segura (RN016).

**RF015 — Controle de Perfis**
- O sistema deve implementar os seis perfis previstos (RN004).
- Cada usuário deve acessar apenas as funcionalidades do seu perfil (RN017).

---

### 2.6 Auditoria e Versionamento

**RF016 — Log de Auditoria**
- O sistema deve registrar todas as ações: usuário, ação, data e hora (RN013).

**RF017 — Histórico de Versões**
- Toda alteração no conteúdo da portaria deve gerar uma nova versão rastreável (RN019).

**RF018 — Restrição de Exclusão**
- O sistema deve impedir a exclusão de portarias publicadas (RN020).

---

### 2.7 Relatórios

**RF019 — Relatórios Mínimos Obrigatórios** (RN014)
O sistema deve gerar os seguintes relatórios:

| Relatório | Filtros |
|---|---|
| Portarias por período | Data inicial / Data final |
| Portarias por servidor | Nome, CPF ou SIAPE |
| Portarias vigentes | Categoria, status |
| Auditoria | Usuário, ação, período |

**RF020 — Exportação**
- Todos os relatórios devem ser exportáveis em PDF e Excel (RN014).

---

### 2.8 Integrações

**RF021 — Integração com Sistemas Externos** (RN015)
O sistema deve integrar-se com:

| Sistema | Finalidade |
|---|---|
| SUAP | Sincronização de dados de servidores |
| SIGRH | Informações de gestão de pessoas |
| SEI | Processo eletrônico e tramitação documental |

---

## 3. Resumo por Perfil

| Perfil | Principais Permissões |
|---|---|
| Solicitante | Abrir solicitação, acompanhar status |
| Área Técnica | Elaborar e editar texto da portaria |
| Jurídico | Revisar e emitir parecer (somente leitura do texto) |
| Assinante | Assinar portarias autorizadas |
| Publicador | Publicar nos canais oficiais |
| Administrador | Gerenciar usuários, perfis e acessos |

---
