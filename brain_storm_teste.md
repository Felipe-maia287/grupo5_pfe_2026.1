# 🚩 Análise e Reestruturação de UX/UI: Site ACBrasil (Projeto Front-end)


## 1. 🎨 Experiência do Usuário (UX) e Interface Visual (UI)

* **Erro Crítico no Menu Principal:** O topo do site atual exibe o erro *"Click here - to use the wp menu builder"*. No novo projeto front-end, isso será resolvido com um menu de navegação semântico e responsivo.
* **Falta de uma "Hero Section" Clara:** A primeira dobra do site não apresenta a proposta de valor. O visitante não descobre em 3 segundos o que é a ACBrasil. O layout atual lembra um feed cru de blog, e não o portal de uma associação de alto nível.
* **Barreira de Entrada (Foco no Login):** O usuário é recebido com formulários enormes de "Entrar/Bem-vindo". Isso passa a falsa impressão de que o site é um sistema fechado.
* **Poluição Visual:** O banner de política de cookies domina a interface de forma desproporcional, competindo com o conteúdo principal.

## 2. 🧭 Navegação e Usabilidade

* **Fluxo de Login e Área Logada:** O botão "Entrar" atual está misturado com a busca. Para um público executivo, a área do associado deve transmitir exclusividade e merecer um botão de destaque isolado (Call to Action).
* **Paginação vs. Descoberta de Conteúdo:** A navegação por páginas (1, 2, 3... 6) no final da lista de artigos é ineficiente. Faltam filtros visuais e categorias.
* **Responsividade Comprometida:** A navegação via dispositivos móveis (smartphones) no site original está severamente prejudicada. O novo projeto deverá garantir uma experiência *mobile-first*.

## 3. 🏗️ Estrutura de Informação e Conteúdo (Arquitetura)

Mapeamento de onde as informações estão mal posicionadas e como devem ser reorganizadas na nova interface:

| Informação Atual | Problema Encontrado | Sugestão de Reposicionamento |
| :--- | :--- | :--- |
| **Artigos Longos na Home** | Ocupam todo o "primeiro scroll". | **Mover para:** Uma página "Artigos". A Home deve ter apenas um carrossel com os 3 mais recentes em cards. |
| **Newsletters como Posts** | Misturadas com artigos de opinião. | **Criar uma seção:** "Media Center" ou página dedicada apenas para o arquivo de Newsletters. |
| **"Sobre Nós" no Rodapé** | A história e a diretoria estão escondidas. | **Mover para:** Um item de menu principal "A Associação" com subpáginas/seções de Estatuto e Diretoria. |
| **Formulário de Contato** | Perdido no site e com problemas técnicos. | **Mover para:** Página dedicada "Contato" acessível no menu superior, com layout limpo e formulário validado. |
| **Benefícios do Associado** | Informação inexistente para não-logados. | **Criar página:** "Associe-se", detalhando os benefícios antes de pedir o login. |

---

## 4. 📋 Análise de Requisitos (Entrevista)

Requisitos técnicos e de negócio mapeados para o projeto da disciplina:

* **Natureza da Instituição:** Organização sem fins lucrativos, gerida por voluntários. 
* **Identidade Visual (UI/Branding):** É obrigatório manter o logo atual e a fonte das letras (seguir manual da marca). A paleta de cores exigida é composta por cinza, amarelo, azul escuro e preto. Inserir ícones das redes sociais.
* **Requisitos de Conteúdo (Home):** O usuário precisa ver as últimas notícias imediatamente ao entrar. A página deve conter um carrossel destacando os 3 últimos itens publicados no blog.
* **Ferramentas e Funcionalidades:** Interface para newsletter e blog, além de uma funcionalidade/área para a publicação de eventos.
* **Integrações Externas:** Implementação de um quadro de RSS e integração (ou simulação) com a API da bolsa de valores.
* **Estrutura de Páginas:** Deve haver uma área de contato e uma seção repensada para os associados/membros.

---

## 5. 🚀 Proposta da Nova Versão (O Novo Site)

### O Novo Cabeçalho (Header) e Identidade
* **Visual:** Fundo branco ou cinza claro, utilizando o logo original e a tipografia do manual da marca.
* **Navegação Consertada:** Menu limpo com: *Início | A Associação | Notícias e Artigos | Eventos | Contato*.
* **CTA Principal:** Um botão na cor amarela ou azul escuro no canto direito escrito **"Área do Membro"**.

### A Nova Página Inicial (Home Dinâmica)
1. **Ticker / Top Bar:** Uma barra fina no topo do site rodando a **API da Bolsa de Valores** (consumida via `fetch` no client-side) e o **Quadro de RSS**.
2. **Hero Section:** Painel dinâmico de introdução e destaque da manchete principal do dia.
3. **Resumo Institucional:** Faixa (fundo azul escuro, texto claro) explicando que a ACB é uma associação sem fins lucrativos feita por voluntários.
4. **Carrossel do Blog:** Slider horizontal configurado para exibir os **3 últimos artigos/itens** (podem ser puxados de um arquivo JSON estático).
5. **Radar de Eventos:** Bloco destacando as próximas publicações de eventos, com data e botão de inscrição.
6. **Rodapé (Footer):** Ícones das redes sociais em destaque, links úteis e o selo de transparência.

### 💻 Desafios de Implementação

* **Simulação do Formulário de Contato:** Criar uma validação robusta no front-end (verificando e-mail, campos vazios, etc.). Ao clicar em enviar, simular um *loading* (spinner) de 2 segundos e exibir um modal de sucesso ("Mensagem enviada!").
* **Consumo de Dados (APIs e Blog):** Usar a Fetch API ou Axios para tentar consumir a API da Bolsa e o RSS. Para contornar problemas de CORS (comuns em projetos de aula), ter um plano B: criar arquivos `dadosMockados.json` locais para simular o retorno das APIs e popular o carrossel do blog e os eventos.
* **Simulação da Área de Membros:** O botão "Entrar" redireciona para uma tela de login. Ao inserir qualquer dado e clicar em acessar, o front-end pode salvar uma flag simples (`isLogged = true`) no `localStorage` ou `sessionStorage` e redirecionar o usuário para a interface do Dashboard do Associado, mostrando como as rotas protegidas se pareceriam visualmente.