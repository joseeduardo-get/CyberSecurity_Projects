# interencdec
###### Solved by @joseeduardo-get
> This is a CTF about decode multiple times
## About the Challenge
O enunciado sugere o desafio de encontrar o real significado no arquivo disponibilizado. Ao abrir o arquivo nos deparamos a seguinte mensagem encriptada "YidkM0JxZGtwQlRYdHFhR3g2YUhsZmF6TnFlVGwzWVROclgyMHdNakV5TnpVNGZRPT0nCg==".
## Solution
Observando a mensagem fica sugestivo que se trata de uma conversão para a base 64, ao decriptar encontramos a seguinte mensagem "b'd3BqdkpBTXtqaGx6aHlfazNqeTl3YTNrX20wMjEyNzU4fQ=='" nesta percebe-se que a real mensagem está dentre aspas portanto removemos o seguinte trecho (b'') ao decodifica-lo novamente da base 64 encontramos a mensagem "wpjvJAM{jhlzhy_k3jy9wa3k_m0212758}" que aparentemente não esta na base 64 mas já se apresenta no formato da flag, para finalizar identifica-se que se trata de uma encriptação através de cifra de césar ao decripta-la descobrimos a flag.
>picoCTF{caesar_d3cr9pt3d_f0212758}
