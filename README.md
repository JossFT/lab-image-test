Descrição: 
Neste projeto, exploramos as capacidades do Azure AI para imagens a partir de texto.
![image](https://github.com/user-attachments/assets/3368a89b-9241-4fb2-9f0d-5b3143357d08)

Tecnologias: Azure AI, DALL-E 3, Python

# Note: DALL-E 3 requires version 1.0.0 of the openai-python library or later
import os
from azure.identity import DefaultAzureCredential
from openai import AzureOpenAI
import json

credential = DefaultAzureCredential()
client = AzureOpenAI(
    api_version="2024-05-01-preview",
    azure_endpoint="https://jocel-m6d2bvpu-swedencentral.openai.azure.com/",
    credential=credential
)

result = client.images.generate(
    model="dall-e-3", # the name of your DALL-E 3 deployment
    prompt="A maior cidade da América do Sul e um dos maiores centros urbanos do mundo, é um caldeirão cultural, econômico e social que pulsa com energia 24 horas por dia. A cidade é um mosaico de culturas, raças e classes sociais, o que a torna um lugar fascinante e complexo.",
    n=1
)

image_url = json.loads(result.model_dump_json())['data'][0]['url']
