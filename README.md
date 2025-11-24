# horta_automatizada_iot

Estufa Inteligente IoT (ESP32 + Arduino) 🌿💧
Projeto de automação agrícola desenvolvido como Trabalho de Conclusão de Curso (TCC) / Semana Técnica na ETEC de Embu (2025).

📖 Sobre o Projeto

O objetivo deste projeto foi resolver um problema comum em hortas urbanas: a falta de consistência na irrigação e o monitoramento ambiental.
Desenvolvemos uma estufa que não apenas "liga a água", mas toma decisões baseadas em dados (umidade do solo) e permite o monitoramento remoto via Wi-Fi. A arquitetura utiliza dois microcontroladores trabalhando em conjunto para dividir as tarefas de leitura de sensores e conectividade web.

👥 A Equipe

Este projeto foi um esforço conjunto da turma de Redes de Computadores:
Firmware & Integração: Rafael Pinheiro (Líder), Matheus Leal, Samir Silva, Vitor Dourado.
Design & Montagem Física: Pedro Henrique, Natasha Gascón, Sthefany Eloisa.
Documentação & Pesquisa: Mario Silveira, Mikael Paes, Samuel Militão.

🛠 Como Funciona (A Lógica)

1. O Cérebro Sensorial (Arduino Uno)

Decidimos usar o Arduino para lidar com a parte "física" e pesada dos sensores por ele ser robusto com 5V. Ele roda um loop não-bloqueante (sem usar delay) para ler:

Temperatura (DS18B20)
Umidade do Solo (Capacitivo)
Luminosidade (BH1750)
Nível do Reservatório (Boia)

Ele processa essas informações e controla o relé da bomba d'água com uma lógica de segurança (timer) para evitar que a bomba queime se a água acabar.

2. A Conectividade (ESP32)

O Arduino envia os dados formatados via Serial (UART) para o ESP32. O ESP32 atua como:
Access Point: Cria a rede Wi-Fi ESTUFA-NET.
Web Server: Hospeda um Dashboard responsivo armazenado na memória Flash.
Interface: Permite visualizar os dados em tempo real pelo celular.

🚀 Como Executar

Hardware: Monte o circuito conforme o esquema na pasta /schematics (ou verifique a pinagem no código).
Bibliotecas: Instale as dependências no Arduino IDE (LiquidCrystal_I2C, DallasTemperature, BH1750).

Upload:
Carregue estufa_arduino.ino no Arduino Uno.
Carregue estufa_esp32.ino no ESP32.
Acesso: Conecte no Wi-Fi ESTUFA-NET (Senha: ESTUFA@ETEC) e acesse o IP mostrado no LCD (geralmente 192.168.4.1).
Orientação: Professora Rosana | ETEC de Embu
