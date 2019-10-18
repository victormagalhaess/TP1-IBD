# TP1-IBD
Base pro TP1 de IBD

Depois de instalar o Jupyter e executar pelo Anaconda tal como no tutorial disponível no TP, o exemplo fornecido não roda pois o SQL default possui caracteres inválidos pro UTF-8. Usem essa base como exemplo:

``` python
IN[1] : 
import io
import sqlite3
import pandas as pd
import matplotlib.pyplot as plt
```
Em seguida criem uma pasta e coloquem o endereço dela no lugar de './SQL/' (mantenham o 'conn_despesas_publicas_tp1.db' no final do caminho, mesmo que esse arquivo não exista ele será criado.

``` python
IN[2]
conn = sqlite3.connect('./SQL/conn_despesas_publicas_tp1.db')
cursor = conn.cursor()
```
Em s seguida baixem o arquivo SQL que está junto com o pdf do moodle e susbtituam o caminho na parte de baixo. (o que causava erro no exemplo da professora é a ausência do encoding = 'latin-1')

``` python
IN[3]
f = io.open('/home/victor/Desktop/IBD/SQL/despesas_publicas_tp1.sql', 'r', encoding = 'latin-1')
sql = f.read()
cursor.executescript(sql)
```

Depois é só ir copiando o códifo abaixo em um IN diferente no Jupyter e trocar o que tá entre aspas pela sua consulta SQL além de alterar o "NUMERO DA QUESTÃO" pra consulta relacionada no TP.

``` python
IN[4]
print(NUMERO DA QUESTÃO)
df = pd.read_sql_query("SELECT SUA CONSULTA SQL FROM VOCÊS", conn)
df
```
