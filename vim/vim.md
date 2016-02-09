# Vim

## searching

  * g* ou g# busca por parte da palavra.

## movimentação

* `n|`: movimenta para a coluna n da linha
* `zt | z<cr>`: Shifts page content so current line sits at the top of the viewport
* `zb | z`: "Shifts page content so current line sits at the bottom of the viewport"
* `zz | z`:  "Shifts page content so current line sits at the middle of the viewport"
* 200zt:  posiciona a linha 200 no top da tela.
* `H`: Moves cursor to the top of the viewport
* `M`: Moves cursor to the middle of the viewport
* `L`: Moves cursor to the bottom of the viewport"
* `gv`: seleciona de novo a ultima seleção visual.
* `o` | `v_o`: quando um bloco de texto está selecionado, você pode usar 'o' para se movimentar do começo para o fim da seleção e vice-versa.
* `g; e g,`:  back and forward na changelist (:changes)
* `<c-i>, <c-o>` -> back and forward na jumplist (:jumps ou :ju)

## folding
  * `zf#j` creates a fold from the cursor down # lines.
  * `zf/string` creates a fold from the cursor to string .
  * `zj` moves the cursor to the next fold.
  * `zk` moves the cursor to the previous fold.
  * `zo` opens a fold at the cursor.
  * `zO` opens all folds at the cursor.
  * `zm` increases the foldlevel by one.
  * `zM` closes all open folds.
  * `zr` decreases the foldlevel by one.
  * `zR` decreases the foldlevel to zero -- all folds will be open.
  * `zd` deletes the fold at the cursor.
  * `zE` deletes all folds.
  * `[z` move to start of open fold.
  * `]z` move to end of open fold.
## text objects
  * `e`: vim-textobj-entire
  * `x`: vim-textobj-xmlattr
  * `gn`: -> para fazer o match do last pattern.
  * `w`: palavra
  * `t`: html tag
  * `{`, `(`, `[`, `'`: objetos surround do tim pope
    * `ys + obj + surround`: 'you surround'. ex: `ysiw'` coloca asapas em volta de um objeto `iw`.
    * `ds + surround`: apaga o surround
    * `cs + oldsurround + newsurround`: muda o surround
## vimdiff
  * `:diffput`
  * `:diffget`
  * `:diffupdate`
  * `:diffoff!`
  * `:windo` diffthis
  * `[c` | `]c` -> movimentação entre diffs.
  * para comparar (diffar) dois buffers abertos verticalmente um do lado do outro
    * para começar o diff `:windo diffthis`
    * para terminar: `diffoff!`
## copy/paste

  * `<C-R> + registrador`: paste from register in insert mode. repeatable with `.` operator.
  * `<C-R> + <C-O>`: resultado "mais dinâmico". ver [link](http://vimcasts.org/episodes/pasting-from-insert-mode).

## shell interaction

### suspender o vim

* `ctrl + z` -> suspende o vim.
* para ver quais processos estão suspensos: 'jobs'
* para des-suspender o vim: `fg`, ou `fg vim`.

### invocar um vim limpo (tipo `zsh -f`)

* `vim -u NONE`

## lists

* command list: `q:`
* search list: `q/`
* change list: `:changes`
* jump list -> `:jumps` ou `:ju`

## block mode

* para 'emparelhar' dois blocos de texto
    1. entra no block mode, seleciona as linhas e aperta `$` para ir até o final de todas
    2. insere 2 espaços no começo de cada linha
    3. seleciona a primeira coluna de espaços em block mode
    4. aperta `p` para substituir a primeira coluna de espaços pelo bloco desejado.

## modo ex
* search/replace de uma vez só: `:%s/antiga/nova/g`
* search/replace interativo (vim 7.4+).
    * primeiro encontra os highlight com '/' e depois soca o comando 'cgn'.
    * vc vai entrar no modo insert, muda a palavra e depois usa `.` para repetir pro resto
* search/replace c/ atalho:
    * acha os highlight com '/' e depois
    * soca: `%s//nova/g`
* `:e!`: reverte o buffer para o estado original do arquivo sem sair do vim.
* mostrar o nome do arquivo corrente: `:echo expand('%:p')`
* mesma tarefa, mas cola no register: `let @a = expand('%:p')`
* mesma tarefa, mas cola direto no buffer `"a`: `put = expand('%:p')`
* mostra ou muda para o diretório escolhido: `:pwd | :cd`
* cola no buffer o conteúdo do register 'a': `:put a:`
* para gerar helptags é só rodar `:helpt[ags] ~/.vim/bundle/nomedoplugin/doc`
* forçando a syntax de um scratch buffer `:set syntax=html`
* mostrar ou esconder os números relativos `:set nornu`
* mostrar ou esconder os números de linha normais: `set nonu`