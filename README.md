# Desafio Dio - Criar um sistema de assistência virtual do zero usando Python



## Reconhecimento de Fala e Análise de Precisão em Python



Este script Python foi desenvolvido para realizar o reconhecimento de fala em arquivos de áudio gravados, transcrevendo-os para texto e avaliando a precisão das palavras reconhecidas em relação a um texto de referência.

#### **Código para criar um sistema de assistência virtual do zero usando Python**

python



```python
import speech_recognition as sr
import pyttsx3
import wikipedia
import datetime

# Criar objetos de reconhecimento de fala e síntese de voz
recognizer = sr.Recognizer()
speaker = pyttsx3.init()

# Função para obter comandos de voz do usuário
def get_voice_command():
    with sr.Microphone() as source:
        print("Ouvindo...")
        audio = recognizer.listen(source)

    try:
        command = recognizer.recognize_google(audio)
        print(f"Você disse: {command}")
        return command.lower()
    except sr.RequestError:
        print("Não consegui entender o que você disse.")
    except sr.UnknownValueError:
        print("Não consegui reconhecer sua fala.")

# Função para responder aos comandos do usuário
def respond_to_command(command):
    if "qual é o seu nome" in command:
        speaker.say("Meu nome é Assistente Virtual.")
        speaker.runAndWait()
    elif "qual é a hora" in command:
        time = datetime.datetime.now().strftime("%H:%M")
        speaker.say(f"São {time}.")
        speaker.runAndWait()
    elif "qual é o tempo" in command:
        weather = get_weather()
        speaker.say(f"O tempo hoje é {weather}.")
        speaker.runAndWait()
    elif "quem é" in command:
        person = command.replace("quem é", "")
        info = wikipedia.summary(person, sentences=2)
        speaker.say(info)
        speaker.runAndWait()
    else:
        speaker.say("Sinto muito, não entendi seu comando.")
        speaker.runAndWait()

# Loop principal para executar o assistente virtual
while True:
    command = get_voice_command()
    respond_to_command(command)
```



#### **Observações:**



- Este código usa o módulo `speech_recognition` para reconhecimento de fala e o módulo `pyttsx3` para síntese de voz.

  

- Você pode personalizar as respostas do assistente virtual adicionando mais condições ao método `respond_to_command`.

  

- Este é apenas um exemplo básico e você pode expandir o código para adicionar mais funcionalidades, como controle de dispositivos domésticos ou envio de mensagens.

  

## Funcionalidades



- **Transcrição de Áudio para Texto:** Utiliza a biblioteca SpeechRecognition para converter áudios em formatos diversos (como WAV, MP3, etc.) em texto escrito.
  
- **Avaliação da Precisão:** Compara a transcrição obtida do áudio com um texto de referência predefinido para calcular a precisão das palavras reconhecidas.
  
- **Integração com Processamento de Linguagem Natural (NLTK):** Utiliza o Natural Language Toolkit para tokenização, permitindo uma análise mais granular e precisa.



## Utilização



1. **Instalação de Dependências:** Certifique-se de ter as bibliotecas necessárias instaladas com o `pip install -r requirements.txt`.
   
2. **Configuração de Parâmetros:** Defina o arquivo de áudio que deseja transcrever e o texto de referência no script.
   
3. **Execução do Script:** Execute o script Python para obter a transcrição do áudio e a precisão das palavras reconhecidas.



## Como Contribuir



Contribuições são bem-vindas! Sinta-se à vontade para abrir uma issue para discutir novos recursos, problemas ou sugestões de melhoria. Se quiser contribuir com código, faça um fork do repositório, faça suas alterações e submeta um pull request.



## Licença

Este projeto está licenciado sob a [MIT License](LICENSE).
