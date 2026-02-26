# Detalhe dos Fluxos do Sistema
---
UC01 - Empréstimo de material

atores: bibliotecário

fluxo principal: 

1. bibliotecário informa o ID do exemplar
2. bibliotecário informa o ID do leitor
3. Sistema valida se leitor está apto para emprestar material
4. Sistema associa material emprestado ao leitor e define data de devolução
5. Sistema confirma o empréstimo e retira uma unidade dos exemplares disponíveis

---

UC02 - Cadastro de usuário

atores: bibliotecário

fluxo principal:

1. bibliotecário informa os dados pessoais do leitor (nome, cpf, email, telefone)
2. Sistema verifica se já existe leitor cadastrado com o cpf informado
3. Bibliotecário solicita que leitor cadastre uma senha
4. Sistema verifica se senha está no formato válido
5. Bibliotecário confirma o cadastro
6. Sistema registra os dados do leitor

---

UC03 - Cadastro de material

atores: bibliotecário

fluxo principal:

1. Bibliotecário informa o ISBN do material
2. Sistema valida se é ISBN válido
3. Sistema registra informações referentes ao ISBN (classificação, tipo, idioma, ano de publicação, autores, editora)
4. Bibliotecário confirma o cadastro
5. Sistema registra o cadastro e adiciona uma unidade do material no acervo

---

UC04 - Devolução de material

atores: bibliotecário

fluxo principal:

1. Bibliotecário informa o ID do exemplar devolvido
2. Sistema verifica se devolução está dentro do prazo estabelecido no ato do empréstimo
3. Sistema registra devolução e acrescenta uma unidade dos exemplares disponíveis

---

UC05 - Renovação de material

atores: leitor

fluxo principal:

1. Leitor seleciona o material que gostaria de renovar
2. Sistema verifica se renovação está dentro do prazo estabelecido no ato do empréstimo
3. Sistema confirma a renovação e define nova data de devolução

--- 
# Interfaces do Sistema

\<\<interface\>\> LivroService<br>
\+ cadastrarLivro(dadosLivro)<br>
\+ editarLivro(idLivro, dadosLivro)<br>
\+ listarLivros()<br>
\+ pesquisarLivros(filtro)<br>
\+ visualizarDetalhesLivro(idLivro)<br>

<br>

\<\<interface\>\> UsuarioService<br>
\+ cadastrarUsuario(dadosUsuario)<br>
\+ atualizarUsuario(idUsuario, dadosUsuario)<br>
\+ listarUsuarios()<br>

<br>

\<\<interface\>\> EmprestimoService <br>
\+ registrarEmprestimo(idUsuario, idLivro)<br>
\+ registrarDevolucao(idEmprestimo)<br>
\+ renovarEmprestimo(idEmprestimo)<br>
\+ visualizarEmprestimosAtivos(idUsuario)<br>
\+ validaLeitor(idUsuario)<br>

<br>

\<\<interface\>\>  HistoricoService<br>
\+ acessarHistoricoEmprestimos(idUsuario)<br>
\+ acessarHistoricoUsuario(idUsuario)<br>

<br>

\<\<interface\>\>  RelatorioService<br>
\+ gerarRelatorioEmprestimos(periodo)<br>
