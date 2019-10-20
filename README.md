# TP1-IBD
Base pro TP1 de IBD

Depois de instalar o Jupyter e executar pelo Anaconda tal como no tutorial disponível no TP, o exemplo fornecido não rodou, acredito que é porque o SQL default possui caracteres inválidos pro UTF-8. Utilizei essa base como exemplo:

``` python
IN[1] : 
import io
import sqlite3
import pandas as pd
```
Em seguida criei uma pasta e coloquei o endereço dela no lugar de './SQL/' ('mantive o conn_despesas_publicas_tp1.db' no final do caminho, mesmo que esse arquivo não exista ele será criado).

``` python
IN[2]
conn = sqlite3.connect('./SQL/conn_despesas_publicas_tp1.db')
cursor = conn.cursor()
```
Em s seguida baixei o arquivo SQL que está junto com o pdf do moodle e susbtitui o caminho na parte de baixo. (acontecia um erro no exemplo da professora, corrigi adicionando "encoding = 'latin-1'" acredito que isso é devido aos caracteres especiais como ç e ã no banco de dados.)

``` python
IN[3]
f = io.open('/home/victor/Desktop/IBD/SQL/despesas_publicas_tp1.sql', 'r', encoding = 'latin-1')
sql = f.read()
cursor.executescript(sql)
```

Depois é só ir copiando o código abaixo em um IN diferente no Jupyter e trocar o que está entre aspas pela consulta SQL além de alterar o "NUMERO DA QUESTÃO" pra consulta relacionada no TP.

``` python
IN[4]
print(NUMERO DA QUESTÃO)
df = pd.read_sql_query("SELECT SUA CONSULTA SQL FROM SUA CONSULTA SQL", conn)
df
```
