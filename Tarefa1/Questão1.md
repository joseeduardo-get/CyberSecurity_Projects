# Cookie Monster Secret Recipe
###### Solved by @joseeduardo-get
> This is a CTF about inspecting cookies, decoding techniques, browser developer tools
## About the Challenge
No enunciado da questão é introduzida uma pequena história sobre o "Monstro dos cookies" que escondeu sua receita secreta de cookies em algum lugar em seu website, a tarefa atribuída a quem esta resolvendo a questão é buscar pelo "segredo", logo em seguida é disposto o site para realização da busca.
## Solution
Ao acessar o site observamos uma simples tela de login, na qual ao tentar realizar o acesso com qualquer chave obtem-se a dica de procurar pelos seus cookies, ao voltar a página inicial podemos clicar com botão direito em qualquer parte da tela, podeos acessar a aba "inspecionar" através desta procuramos pela aba aplicações a qual por sua vez dara acesso a várias opções, dentre essas acessamos a aba "cookies" nesta temos acesso a um domínio de nome "http://verbal-sleep.picoctf.net" que exibe uma linha com nome "secret-recipe" com valor "cGljb0NURntjMDBrMWVfbTBuc3Rlcl9sMHZlc19jMDBraWVzXzc3MUQ1RUIwfQ%3D%3D" que é aparentemente uma mensagem encriptada. Em seguida colocamos a mensagen em um identificador de cifras que observa compatibilidade com a base 64, ao decriptar a mensagem obtemos a flag.
>`picoCTF{c00k1e_m0nster_l0ves_c00kies_E634DFBB}
