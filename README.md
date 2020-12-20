# Web_APIs
Learning and using web APIs in Internet Programming II

## Covid-19-API - for MMedia Group

### INTRODUÇÃO
	# A API destina-se a desenvolvedores, máquinas, programas e outros sites 
	# para obter rapidamente informações atualizadas sobre a epidemia de COVID-19.
	# Ele pode ser usado para construir ferramentas e sistemas que são usados 
	# para análise de dados até sites que atuam como painéis e gráficos públicos.

### TESTES WITH GET METHOD

	# BROWSER:

	# https://covid-api.mmediagroup.fr/v1/cases?country=Brazil
	# https://covid-api.mmediagroup.fr/v1/history?country=Brazil&status=confimerd

	# PYTHON:
'''
import requests

# get = 'cases'
get = 'history'

url = 'https://covid-api.mmediagroup.fr/v1/{get}'
url = url.format(get=get)

payload = {'country':'Brazil','status':'Confirmed'} # "status" not considered when used "history"

response = requests.get(url, params=payload).json()

print(response)
'''

### DOCUMENTAÇÃO

[M-Media-Group/Covid-19-API](https://github.com/M-Media-Group/Covid-19-API)
