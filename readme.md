Olá!

Esse aqui é um código refatorado do antigo repositório, a atualização do código foi feita totalmente por mim (https://github.com/ramiropolla/matrufsc_dbs).

Esse código serve para fazer um scrapping nas matérias, aulas e professores da UFSC pelo CAGR. Estes scripts em python 2.7 são específicos para o sistema decadastro de disciplinas da UFSC.

Vou em seguida, explicar como usar essa ferramenta, os requisitos necessários, e explicar o código.

============================================================================

NECESSÁRIO TER PARA EXECUTAR O CÓDIGO:

Python 2.17

PIP

BeautifulSoup

============================================================================

O arquivo get_turmas.py pega o CAGR e faz um scrapping, ele cria um arquivo db dentro da pasta "py", e nessa pasta ele guarda todos os XML's e HTML's que conseguiu baixar.
o arquivo parse_turmas.py ele vai pegar todos os arquivos dentro do db novo criado dentro do arquivo py e "transforma" eles em um arquivo único JSON com mais de 4 mil linhas.

AVISO: Para o get_turmas.py rodar, você precisa primeiro logar no CAGR, apertar F12, e pegar os cookies de sessão. Aí você cola tais cookies nas linhas 52 e 53 do código no arquivo get_turmas.py

ESSE É O CÓDIGO:
```py
#cole aqui seus cookies
JSESSIONID = 'adicione aqui sua sessão ID cookie'
INGRESSCOOKIE = "adicione aqui sua sessão ID cookie"
```

============================================================================

E agora para rodar o código, você deve entrar na pasta py dentro do terminal, e usar os seguintes comandos:

```bash
py -2.7-32 get_turmas.py [SEMESTRE QUE VOCE QUER OS DADOS]
py -2.7-32 get_turmas.py 20251 

py -2.7-32 parse_turmas.py [CAMINHO PARA O ARQUIVO XML DENTRO DO DB]
py -2.7-32 parse_turmas.py ..\db\20251_FLO.xml ..\db\20251_JOI.xml ..\db\20251_CBS.xml ..\db\20251_ARA.xml ..\db\20251_BLN.xml ..\20251_turmas.json
```
============================================================================

```
Os dados relativos a horas_aula e vagas são em números, não strings.
Os horários são no formato disponibilizado pela UFSC:
"2.1010-2 / ARA-ARA209"
 | |    |   |   \----- código da sala
 | |    |   \--------- código do departamento
 | |    \------------- número de aulas seguidas no bloco
 | \------------------ horário da primeira aula do bloco
 \-------------------- dia da semana

Os professores são dispostos numa lista de strings.
```

============================================================================








