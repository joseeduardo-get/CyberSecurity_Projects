# XOR Starter
###### Solved by @joseeduardo-get
> This is a CTF about decoding techniques, bitwise developer tools
## About the Challenge
No enunciado da questão é introduzido o funcionamento do método bitwise, a tarefa atribuída a quem esta resolvendo a questão é utilizar do método XOR entre a string "label" e o inteiro 13, apos isso converter novamente para texto.
## Solution
Primeiramente devemos converter a string em valores da tabela ASCII, para isso em Python vamos inicialmente atribuir o string a uma variável depois faremos uma estrutura de repetição, que utiliza o comando "ord()" para converter digito por digito, depois iremos imprimir os valores equivalentes ao texto.

>>> text = "label"
>>> ascii_list = [ord(char) for char in text]
>>> print (ascii_list)
[108, 97, 98, 101, 108]

Depois disso devemos converter os valores para binario, em seguida fazer o XOR entre os valores depois coverter os resultados para ASCII e por fim para texto. No caso todas as etapas serão executadas pelo seguinte código em python

numeros = [108, 97, 98, 101, 108]
chave = 13
texto = ""

print("Resultado do XOR e conversões:")
for n in numeros:
    resultado = n ^ chave
    caractere = chr(resultado)
    texto += caractere
    print(f"{n} ^ {chave} = {resultado} (bin: {bin(resultado)}) -> ASCII: '{caractere}'")

print("\nTexto final reconstruído:", texto)

Na saída teremos a string "aloha".

>`crypto{aloha}
