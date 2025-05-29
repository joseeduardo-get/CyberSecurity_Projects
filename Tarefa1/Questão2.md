# Flag Hunters
###### Solved by @joseeduardo-get
> This is a CTF about input manipulation, control flow
## About the Challenge
O enunciado da questão fala sobre letras de uma música que "pulam" dos versos para o refrão como uma chamada de inesperada, além disso foi citado um refrão escondido que o progama não imprime devido ao default. Após isso é fornecido o arquivo do progama em python. 
## Solution
Para resolver a solução acessei o progama através de um maquina virtual com kali linux, ao abrir seu terminal e inserir a entrada do progama com "nc verbal-sleep.picoctf.net 61138" temos acesso a música que começa a ser impressa no terminal logo em seguida aparece uma opção de input "Crowd: " na qual quando inserido qualquer valor temos a continuidade da música sem nenhuma solução, no entanto ao inserir ";RETURN 0" na entrada obrigamos o progama a voltar a linha 0 fornecendo assim a letra completa que em seu meio possui a flag. 
>picoCTF{70637h3r_f0r3v3r_710a5048}
