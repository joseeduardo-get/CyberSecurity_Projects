# XOR Properties
###### Solved by @joseeduardo-get

> Desafio de CTF envolvendo técnicas de decodificação e operações bitwise e suas devidas propriedades.

## Sobre o Desafio

O enunciado da questão apresenta brevemente o funcionamento das operações e suas propriedades bitwise XOR. A tarefa é aplicar a operação XOR em diferentes situações observando as propriedades do operador XOR entre diferentes operações fornecidas, e então reconstruir a flag a partir dos dados fornecidos.

## Solução

### Passo 1: Definir uma função auxiliar

Primeiramente, em python, vamos definir uma função auxiliar `"xor_bytes"` que vai realizar multiplas sequências de XOR byte a byte, entre múltiplos arrays de bytes. O operador `"*args"` permite inserir vários elementos ao chamar a função. Já o operador `"zip(*args)"` coloca o bytes na mesma posição da entrada. O operador `"reduce(lambda x, y: x ^ y, values)"` aplica o XOR sucessivamente em cada grupo de bytes e o operador `"bytes()"` converte o resultado em um array de bytes.

```python
def xor_bytes(*args):
     from functools import reduce
     return bytes([reduce(lambda x, y: x ^ y, values) for values in zip(*args)])
```
### Passo 2: Inserção de dados e conversão para bytes

Agora, vamos inserir os dados e com o operador `"bytes.fromhex()"` fazemos a conversão de hexadecimal para bytes.

```python
key1 = bytes.fromhex("a6c8b6733c9b22de7bc0253266a3867df55acde8635e19c73313")
key1_xor_key2 = bytes.fromhex("37dcb292030faa90d07eec17e3b1c6d8daf94c35d4c9191a5e1e")
key2_xor_key3 = bytes.fromhex("c1545756687e7573db23aa1c3452a098b71a7fbf0fddddde5fc1")
encrypted = bytes.fromhex("04ee9855208a2cd59091d04767ae47963170d1660df7f56f5faf")
```

### Passo 3: Decodificação

Com os dados em mãos podemos realizar as funções montadas. A primeira recuperação é a do ***key2*** pela qual através da propriedade associativa e da propriedade da auto-inversão obtemos uma identidade que gera a ***key2***.

key1 &oplus; key2 = key2 &oplus; key1   --->    (key1 &oplus; key2) &oplus; key1 = (key1 &oplus; key1) &oplus; key2    --->    (0) &oplus; key2 = key2

```python
key2 = xor_bytes(key1, key1_xor_key2)
```

 A segunda recuperação é a do ***key3*** pela qual através da propriedade associativa e da propriedade da auto-inversão obtemos uma identidade que gera a ***key3***.
 
key3 &oplus; key2 = key2 &oplus; key3   --->    (key3 &oplus; key2) &oplus; key2 = (key2 &oplus; key2) &oplus; key3    --->    (0) &oplus; key3 = key3

```python
key3 = xor_bytes(key2, key2_xor_key3)
```
 A terceira recuperação é a da ***flag*** pela qual através da propriedade associativa e da propriedade da auto-inversão obtemos identidades três vezes que geram a ***flag***.

flag = xor_bytes(encrypted, key1, key2, key3)
 
print(flag.decode())


Saída de dados:

```python

```


>crypto{x0r_i5_ass0c1at1v3}
