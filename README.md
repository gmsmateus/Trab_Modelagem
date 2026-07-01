# 🍔 BurguerFlow - Sistema de Gestão de Hamburgueria

O **BurguerFlow** é um protótipo de sistema de gestão interna desenvolvido para a disciplina de **Modelagem de Sistemas (DCC117)**. O foco do projeto é otimizar o fluxo de trabalho entre o atendimento, a cozinha e o fechamento financeiro de pequenas hamburguerias.

---

## 🚀 Funcionalidades

### 🪑 Gestão de Mesas e Comandas
- Controle de mesas com status (Livre / Ocupada), numeradas sequencialmente.
- Suporte a **múltiplas comandas por mesa** — cada cliente pode ter a sua própria comanda.
- Nomeação personalizada de comandas pelo garçom (ex: nome do cliente).
- Abertura e fechamento individual de comandas; mesa só é liberada quando todas as comandas forem encerradas.
- Gerenciamento de mesas pelo administrador (adicionar e remover a última mesa).

### 📝 Módulo de Atendimento (Garçom)
- Lançamento de itens com observações por comanda.
- Categorização automática de itens: **Cozinha** (requerem preparo) e **Balcão** (disponíveis imediatamente).
- Envio de pedidos para a cozinha com roteamento automático por categoria.
- Indicadores visuais de alerta nas mesas e comandas: 🟡 itens a enviar, 🟢 itens prontos para entrega.
- Cancelamento de itens permitido apenas nos status **Rascunho** e **Pendente**.
- Confirmação de entrega de itens prontos diretamente pelo garçom.

### 👨‍🍳 Módulo de Cozinha
- Fila de preparo em tempo real, atualizada automaticamente entre abas.
- Cards identificados por **Mesa + Comanda** para facilitar a comunicação verbal com o garçom.
- Fluxo de preparo: **Iniciar Preparo → Marcar como Pronto**.
- Itens de balcão nunca aparecem na fila da cozinha.

### 💰 Módulo de Caixa
- Listagem de todas as comandas abertas com filtro por mesa ou nome de comanda.
- Detalhamento de consumo por comanda com bloqueio de pagamento para itens não entregues.
- Seleção de forma de pagamento: Dinheiro, Cartão de Crédito, Cartão de Débito ou Pix.
- Fechamento individual de comandas; liberação automática da mesa ao encerrar todas.

### ⚙️ Painel Administrativo
- **Cardápio:** Cadastro, edição e remoção de itens com nome, preço e categoria (Cozinha / Balcão). Filtro de busca por nome ou categoria.
- **Mesas:** Adição e remoção sequencial de mesas com confirmação.
- **Relatório de Vendas:** Período filtrável com resumo geral, formas de pagamento, receita por categoria, top 5 mais vendidos, itens menos vendidos e histórico de atendimentos agrupado por sessão de mesa (com hora de fechamento). Exportação para planilha `.xlsx` estilizada.
- **Edição do Histórico:** O gerente pode corrigir ou remover registros de vendas diretamente no relatório (edição de itens consumidos e forma de pagamento; registros corrigidos são marcados com ✏️).
- **Senhas:** Gerenciamento separado da senha do sistema (acesso geral) e da senha do administrador.

### 🔄 Ciclo de Vida de um Pedido
```
Rascunho → Pendente → Em preparo → Pronto → Entregue
                ↑
         (Balcão pula direto para Pronto)
```

---

## 🔐 Instruções de Acesso

### Senha do Sistema
Solicitada na tela inicial (`index.html`) para todos os usuários.
- **Senha padrão:** `1234`
- Pode ser alterada pelo administrador em: **Painel Admin → Senha do Sistema**.

### Senha do Administrador
Solicitada na tela de login administrativo (`login-admin.html`), acessível pelo ícone de engrenagem ⚙️ no dashboard.
- **Senha padrão:** `1234`
- Pode ser alterada em: **Painel Admin → Senha do Administrador**.

> ⚠️ As senhas são armazenadas localmente no navegador (`localStorage`). Ao limpar os dados do navegador, voltam para o padrão `1234`.

---

## 🛠️ Tecnologias Utilizadas

- **Linguagens:** HTML5, CSS3, JavaScript (ES6+).
- **Framework Visual:** Bootstrap 5.3.
- **Biblioteca de Ícones:** Bootstrap Icons 1.11.
- **Persistência de Dados:** `localStorage` do navegador (sem backend).
- **Exportação de Planilhas:** [xlsx-js-style](https://github.com/gitbrent/xlsx-js-style) 1.2.0 (via CDN).
- **Design:** CSS Custom Properties para padronização de paleta de cores e componentes visuais.

---

## 📂 Estrutura do Projeto

| Arquivo | Descrição |
|---|---|
| `index.html` | Tela de login do sistema (senha de acesso geral). |
| `dashboard.html` | Menu principal com acesso aos três módulos operacionais. |
| `garcom.html` | Módulo de atendimento: gestão de mesas, comandas e pedidos. |
| `cozinha.html` | Módulo de cozinha: fila de preparo em tempo real. |
| `caixa.html` | Módulo financeiro: fechamento de comandas e recebimento. |
| `login-admin.html` | Tela de login do painel administrativo (senha de gerência). |
| `admin.html` | Painel administrativo: cardápio, mesas, relatório e senhas. |
| `estilo.css` | Arquivo centralizado de estilos e identidade visual. |

---

## 💾 Dados no localStorage

| Chave | Conteúdo |
|---|---|
| `burguerflow_mesas` | Estado atual de todas as mesas e suas comandas. |
| `burguerflow_cardapio` | Lista de itens do cardápio. |
| `burguerflow_precos` | Preços dos produtos. |
| `burguerflow_categorias` | Categorias dos produtos (Cozinha / Balcão). |
| `burguerflow_historico` | Histórico de vendas fechadas. |
| `burguerflow_senha_sistema` | Senha de acesso ao sistema. |
| `burguerflow_senha_admin` | Senha de acesso ao painel administrativo. |

---

## 👥 Desenvolvedores

- **Mateus Gomes**
- **Savio Machado**

---

*DCC117 — Modelagem de Sistemas · UFJF*
