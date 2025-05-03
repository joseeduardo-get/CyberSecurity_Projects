# RED
###### Solved by @joseeduardo-get
> This is a CTF about steganographic techniques and decrypt from diferent bases
## About the Challenge
O nunciad cita a cor vermelha 4 vezes e disponibiliza um arquivo em formato png para download.
## Solution
Primeiramente ao acessar a imagem temos apenas uma tela vermelha, portanto a imagem deve acarregar algum tipo de mensagem. Para resolver a questão acessamos uma maquina virtual com o sistema operacional kali Linux, nela através do terminal é utilizado o comando "zsteg", que é uma ferramenta de detecção ded esteganografia, ao aplicar o comando acompanhado do nome do arquivo "red.png" temos acesso a uma mensagem que aparentemente esta encrptada na base 64 "cGljb0NURntyM2RfMXNfdGgzX3VsdDFtNHQzX2N1cjNfZjByXzU0ZG4zNTVffQ==cGljb0NURntyM2RfMXNfdGgzX3VsdDFtNHQzX2N1cjNfZjByXzU0ZG4zNTVffQ==cGljb0NURntyM2RfMXNfdGgzX3VsdDFtNHQzX2N1cjNfZjByXzU0ZG4zNTVffQ==cGljb0NURntyM2RfMXNfdGgzX3VsdDFtNHQzX2N1cjNfZjByXzU0ZG4zNTVffQ==" a qual ao ser decriptada fornece a flag.
>picoCTF{r3d_1s_th3_ult1m4t3_cur3_f0r_54dn355_}
 
