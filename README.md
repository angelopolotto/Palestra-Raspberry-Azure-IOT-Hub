# Palestra-Raspberry-Azure-IOT-Hub
Código do conteúdo apresentado na palestra "Azure e Raspberry Pi: um exemplo de monitoramento remoto""
Apresentação: https://goo.gl/k725qJ .

# Organização do diretório
* Leitura do Sensor Tag: Exemplo de leitura de dados do sensor tag
* Monitoramento Remoto: Monitoramento remoto dos dados utilizanod Azure IOT Hub
* Scripts Node JS Azure IOT: Ferramentas para ajudar no desenvolvimento com o Azure IOT Hub

# Materiais necessários:
* Raspberry Pi 3 com o Raspbian Instalado
* Texas Instruments Sensor Tag CC2650

# Configurando o Raspberry
* Atualizar o Node Red através desse tutorial: https://nodered.org/docs/hardware/raspberrypi
* Abrir o terminal
* Instalar os drivers bluetooth com os comandos:

```
  sudo apt-get install libbluetooth-dev libudev-dev pi-bluetooth
  sudo setcap cap_net_raw+eip $(eval readlink -f 'which node')
```

* Ir até o diretório .nod-red na pasta do usuário
* Instalar o Node Red Sensor Tag: npm i node-red-node-sensortag
* Instalar o Node Red Dashboard: npm i node-red-dashboard
* Instalar o Azure IOT Hub Node Red: npm install -g node-red-contrib-azure-iot-hub
* Iniciar o Node Red com o comando: node-red-start
* Abrir o Node Red no navegador: enderecoIpRaspberry:1880
* Copiar o texto do arquivo: Monitoramento Remoto/Exemplo2_Azure_IOT_Raspberry.json
* Ir até o menu/importar no Node Red e colar o texto

# Configurando o computador remoto onde os dados chegarão:
* Instalar o Node.js para o seu sistema
* Instalar o Node Red de acordo com o seu sistema: http://nodered.org/docs/getting-started/installation.html
* Ir até a pasta onde o Node Red foi instalado
* Instalar o Node Red Dashboard: npm i node-red-dashboard
* Instalar o Azure Event Hubs: npm install azure-event-hubs
* Abrir o arquivo .node-red/settings.js, na pasta onde o Node Red foi instalado
* Escrever o seguinte comando dentro da função functionGlobalContext: azureEventHubs:require('azure-event-hubs')
* Inicie o Node Red: http://nodered.org/docs/getting-started/running
* Abrir o Node Red no navegador, o endereço será fornecido no terminal
* Copiar o texto do arquivo: Monitoramento Remoto/Exemplo2_Azure_IOT_Remoto.json
* Ir até o menu/importar no Node Red e colar o texto

# Configurando o Azure IOT Hub:
* Seguir o tutorial: https://docs.microsoft.com/en-us/azure/iot-hub/iot-hub-node-node-getstarted
* Cadastrar um novo dispositivo no azure portal em _Device Explorer_
* Copiar sua cadeia (string) de conexão do dispositivo, chave primária e ID
* Inserir no flow do Node Red do raspberry
* Ir em _Políticas de acesso compartilhado_ no azure portal
* Copiar a cadeia (string) de conexão do _iothubowner_
* Inserir no flow do Node Red de monitoramento no computador

# Testando as funcionalidades do Azure IOT Hub:
* Clone os códigos disponíveis em: Scripts Node JS Azure IOT
* Escolha um script
* Utilize as credenciais obtidas no item anterior
* Instale os pacotes necessários: _npm install_
* Execute o script: node nome_do_arquivo.js