# Web APIs
Usando web APIs na disciplina de Programação para Internet II

## Covid-19-API for MMedia Group

#### INTRODUÇÃO
A API destina-se a desenvolvedores, máquinas, programas e outros sites para obter rapidamente informações atualizadas sobre a epidemia de COVID-19. Ele pode ser usado para construir ferramentas e sistemas que são usados para análise de dados até sites que atuam como painéis e gráficos públicos.

#### TESTES COM MÉTODO GET

- **Browser(application/x-www-form-urlencoded)**

	- #1 [https://covid-api.mmediagroup.fr/v1/cases?country=Brazil](https://covid-api.mmediagroup.fr/v1/cases?country=Brazil)
	- #2 [https://covid-api.mmediagroup.fr/v1/history?country=Brazil&status=confirmed](https://covid-api.mmediagroup.fr/v1/history?country=Brazil&status=confirmed)

- **Python**
```python
import requests

#1
# get = 'cases'

#2
get = 'history'

url = 'https://covid-api.mmediagroup.fr/v1/{get}'
url = url.format(get=get)

payload = {'country':'Brazil','status':'Confirmed'} # "status" not considered when used "history"

response = requests.get(url, params=payload).json()

print(response)
```

#### DOCUMENTAÇÃO

[M-Media-Group/Covid-19-API](https://github.com/M-Media-Group/Covid-19-API)


## SearchLy v1

#### INTRODUÇÃO

A API SearchLy fornece pesquisa por similaridade com base nas letras das músicas.

#### OPERAÇÕES

A API permite a `/similarity/by_song` operação, o que permite que os clientes 
pesquisem a similaridade de uma música existente no banco de dados. Além disso,
a API tem um `/similarity/by_content` ponto de extremidade adicional que permite
que os clientes pesquisem similaridade com uma entrada de String livre por meio 
de um corpo de solicitação JSON. Uma `/song/search` operação adicional está 
disponível para pesquisar músicas com uma string de consulta.


#### TESTES COM MÉTODO GET

- **Browser(application/x-www-form-urlencoded)**

	- #1 [https://searchly.asuarez.dev/api/v1/similarity/by_song?song_id=1](https://searchly.asuarez.dev/api/v1/similarity/by_song?song_id=1)
	- #2 [https://searchly.asuarez.dev/api/v1/song/search?query=Bruno+Mars](https://searchly.asuarez.dev/api/v1/song/search?query=Bruno+Mars)

- **Python**
```python
import requests

#1
get = 'similarity/by_song'
payload = {'song_id': 1}

#2
# get = 'song/search'
# payload = {'query':"Bruno Mars"}

url = 'https://searchly.asuarez.dev/api/v1/{get}'
url = url.format(get=get)

response = requests.get(url, params=payload).json()

print(response)
```

#### DOCUMENTAÇÃO

[Searchly/docs](https://searchly.asuarez.dev/docs/v1)

## Jikan

#### INTRODUÇÃO

Jikan é uma API MyAnimeList não oficial.
Ele vasculha o site para satisfazer a necessidade de uma API - que falta no MyAnimeList.
A palavra Jikan é traduzida literalmente como Tempo em Japonês (時間). 
E é disso que essa API economiza. ;)

#### TESTES COM MÉTODO GET

- **Browser(application/x-www-form-urlencoded)**

	- #1 [https://api.jikan.moe/v3/season/2020/winter](https://api.jikan.moe/v3/season/2020/winter)
	- #2 [https://api.jikan.moe/v3/top/anime](https://api.jikan.moe/v3/top/anime)
	- #3 [https://api.jikan.moe/v3/search/anime?q=Naruto&limit=1](https://api.jikan.moe/v3/search/anime?q=Naruto&limit=1)

- **Python**
```python
import requests

#1
# animes = '2020/winter'
# get = 'season/{animes}'

#2
get = 'top/anime'

#3
# animes = 'anime'
# # animes = 'manga'
# get = 'search/{animes}'

#For 2 e 3
# get = get.format(animes=animes)

url = 'https://api.jikan.moe/v3/{get}'
url = url.format(get=get)

payload = {'q':'Naruto','limit':1}

response = requests.get(url, params=payload).json()

print(response)
```

#### DOCUMENTAÇÃO

[Jikan/docs](https://jikan.docs.apiary.io)


## CleanURI

#### INTRODUÇÃO
Cleanuri.com expõe seus dados por meio de uma interface de programação 
de aplicativo (API), para que os desenvolvedores possam interagir de forma 
rogramática com o aplicativo.

#### DESCRIÇÃO
Serviço de encurtador de URL

- PARÂMETROS
	- `url` - um URL longo a ser encurtado (exemplo: http://google.com/).

- NOTAS
	- URLs longos devem ser codificados por URL . 
    - Você não pode incluir um longUrl na solicitação que tenha "&","?","#" 
    - Ou outros parâmetros reservados sem primeiro codificá-lo.

URLs longos não devem conter espaços: qualquer longUrl com espaços será rejeitado. Todos os espaços devem ter codificação de porcentagem"%20" ou codificação de mais"+". Observe que tabulações, novas linhas e espaços finais são todos indicações de erros. Lembre-se de remover os espaços em branco à esquerda e à direita de qualquer entrada do usuário antes de reduzir.

#### TESTES COM MÉTODO POST

```python
import requests

base = 'https://cleanuri.com/api/v1/shorten'

data = {
	"url" : "https://ifpi.edu.br/",
}

response = requests.post(base, data).json()

try:
	print("Generated short url: %s" % (response['result_url']))
except Exception as e:
	print(response)
```

#### DOCUMENTAÇÃO

[CleanURI/docs](https://cleanuri.com/docs)
