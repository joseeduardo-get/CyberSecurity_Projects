# Favourite byte
###### Solved by @joseeduardo-get

> Desafio de CTF envolvendo técnicas de decodificação, operações bitwise, suas devidas propriedades e comandos de verificação.

## Sobre o Desafio

Foi fornecida uma string codificada em hexadecimal. A mensagem original foi criptografada aplicando-se a operação XOR com uma chave de 1 byte sobre cada byte da mensagem original. A tarefa é descobrir a chave e recuperar a flag.

## Solução

### Passo 1: Conversão de uma string hexadecimal para bytes
Primeiramente, em python, utilizamos a função `bytes.fromhex()` para transformar a string hexadecimal em um array de bytes:


```python
hex_string = "73626960647f6b206821204f21254f7d694f7624662065622127234f726927756d"
cipher_bytes = bytes.fromhex(hex_string)
```
### Passo 2: Descobrir com qual byte foi feita a operação XOR

Agora, sabendo que a chave tem apenas um byte (valores entre 0 e 255) com o comando `range(256)`, devemos aplicar a operação XOR em cada byte da mensagem com cada possível valor de chave, logo em seguida testamos se o resultado forma uma string válida. Ao final filtramos as saídas liberadas, com o comado `if "crypto" in text` e o `break` para finalizar a repetição, considerando a palavra "crypto" que necessariamente esta no início da flag decodificada. Por fim com o objetivo de tratar erros que ocorrem ao tentar converter bytes para texto legível utilizamos o `try`, e o bloco `except UnicodeDecodeError:` para possíveis exeções levantadas pelo python.

```python
for key in range(256):
     decrypted = bytes([b ^ key for b in cipher_bytes])
     try:
         text = decrypted.decode('utf-8')
         if "crypto" in text:
             print(f"Key: {key} => {text}")
     except UnicodeDecodeError:
        continue
```
Saída de dados:

```python
Key: 16 => crypto{0x10_15_my_f4v0ur173_by7e}
```

>crypto{0x10_15_my_f4v0ur173_by7e}
