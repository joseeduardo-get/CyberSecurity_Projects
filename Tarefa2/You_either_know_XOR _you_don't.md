# You either know, XOR you don't
###### Solved by @joseeduardo-get

> Desafio de CTF envolvendo técnicas de decodificação, operações bitwise, suas devidas propriedades e comandos de verificação.

## Sobre o Desafio

Foi fornecida uma string codificada em hexadecimal. A mensagem original foi criptografada aplicando-se a operação XOR com uma chave desconhecida com a mensagem original, além disso temos a dica de observar o formato da submissão da flag. A tarefa é descobrir a chave e recuperar a flag.

## Solução

### Passo 1: Conversão de uma string hexadecimal para bytes
Primeiramente, em python, utilizamos a função `bytes.fromhex()` para transformar a string hexadecimal em um array de bytes:

```python
cipher_hex = "0e0b213f26041e480b26217f27342e175d0e070a3c5b103e2526217f27342e175d0e077e263451150104"
cipher_bytes = bytes.fromhex(cipher_hex)
```

### Passo 2: Descobrir com qual byte foi feita a operação XOR

Agora, sabendo que a flag começa com um texto conhecido, ***crypto{***, podemos usar essa informação para recuperar a chave XOR. Para isso, aplicamos a operação XOR byte a byte entre os primeiros bytes cifrados e os bytes do texto conhecido. Com as propriedades da operação XOR de associação e de auto-inversão, ao fazer a operação XOR entre ***cipher_byte*** e ***known_byte*** obtemos o byte da chave original naquela posição. Como a chave provavelmente é maior que esses primeiros bytes, estimamos o comprimento da chave com base no padrão observado (no caso, b"myXORkey"). Em seguida, repetimos a chave usando `itertools.cycle` para aplicar XOR em toda a mensagem cifrada. Essa repetição é necessária porque a criptografia XOR com chave repetida aplica o XOR de cada byte da mensagem com o respectivo byte da chave, repetida ciclicamente. 

```python
from itertools import cycle
known = b'crypto{'
partial_key = bytes([cipher_bytes[i] ^ known[i] for i in range(len(known))])
```

Saída de dados:

```python
key = b"myXORkey"
```

### Passo 3: Decodificar para texto legível

Por fim, tentamos decodificar o resultado para texto legível usando `.decode()`. Se a chave e o processo estiverem corretos, o resultado será a flag no formato esperado. Dessa forma, utilizamos o conhecimento do formato da flag para inferir a chave e realizar a descriptografia completa.

```python
plaintext = bytes([c ^ k for c, k in zip(cipher_bytes, cycle(key))])
print(plaintext.decode())
```

>crypto{1f_y0u_Kn0w_En0uGH_y0u_Kn0w_1t_4ll}
