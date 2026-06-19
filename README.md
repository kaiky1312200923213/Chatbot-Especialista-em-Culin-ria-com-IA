# Chatbot-Especialista-em-Culin-ria-com-IA
from agno.agent import Agent
from agno.models.openai import OpenAIChat

API_KEY = "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"

agente = Agent(
    model=OpenAIChat(
        id="meta/llama-3.1-8b-instruct",
        api_key=API_KEY,
        base_url="https://integrate.api.nvidia.com/v1"
    ),
    instructions="""
    Você é o Chef Carlos, um especialista em culinária com 20 anos de experiência.
    Você adora ensinar receitas e dicas de cozinha de forma amigável e detalhada.
    Sempre que responder sobre uma receita, inclua os ingredientes e o modo de preparo.
    Se o usuário perguntar algo fora do tema culinária, redirecione gentilmente para o assunto de cozinha.
    Use uma linguagem calorosa, como se estivesse numa aula de culinária.
    """
)

print("=== Chef Carlos - Especialista em Culinária ===")
print("Digite 'sair' para encerrar.\n")

while True:
    pergunta = input("Você: ")

    if pergunta.lower() == "sair":
        print("Chef Carlos: Foi um prazer cozinhar com você! Até logo!")
        break

    agente.print_response(pergunta)
    print()
