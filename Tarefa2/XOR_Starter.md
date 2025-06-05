# XOR Starter
###### Solved by @joseeduardo-get

> Desafio de CTF envolvendo técnicas de decodificação e operações bitwise.

## Sobre o Desafio

O enunciado da questão apresenta brevemente o funcionamento da operação bitwise XOR. A tarefa é aplicar a operação XOR entre cada caractere da string `"label"` e o número inteiro `13`, e então reconstruir o texto original a partir dos valores resultantes.

## Solução

### Passo 1: Converter a string para ASCII

Primeiramente, vamos converter cada caractere da string `"label"` para seus respectivos valores na tabela ASCII. Em Python, isso pode ser feito utilizando a função `ord()`:

```python
text = "label"
ascii_list = [ord(char) for char in text]
print(ascii_list)
```
Saída de dados:

```python
[108, 97, 98, 101, 108]
```

### Passo 2: Aplicar a operação XOR

Agora, com os valores ASCII em mãos, aplicamos a operação XOR (^) com o valor 13. Em seguida, convertemos o resultado novamente para caracteres com chr() e reconstruímos a string:

```python
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
```

Saída de dados:

```python
108 ^ 13 = 97 (bin: 0b1100001) -> ASCII: 'a'
97 ^ 13 = 108 (bin: 0b1101100) -> ASCII: 'l'
98 ^ 13 = 111 (bin: 0b1101111) -> ASCII: 'o'
101 ^ 13 = 104 (bin: 0b1101000) -> ASCII: 'h'
108 ^ 13 = 97 (bin: 0b1100001) -> ASCII: 'a'
```

Texto final reconstruído: aloha

>crypto{aloha}
