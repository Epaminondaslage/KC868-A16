# KC868-A16 Smart Controller para Automação Residencial

![Hardware KC 868-A16](https://github.com/Epaminondaslage/KC868-A16/blob/main/a16-connections.jpg)

# KC868-A Series Board Protocol – Comandos MQTT  

🔗 [KC868-A16 – Comandos MQTT](https://github.com/Epaminondaslage/KC868-A16/blob/main/KC868-A_mqtt%20comands.md)  

## MQTT para KC868-A16  
📎 [Documento MQTT](https://www.kincony.com/forum/attachment.php?aid=2872)  

## "KCS" Firmware System  
📌 [Fórum Oficial](https://www.kincony.com/forum/forumdisplay.php?fid=40)  

## Guia de Uso do Firmware "KCS" v2 para o KC868-A16  

> **Nota:** Este documento se aplica aos controladores inteligentes KinCony:  
> KC868-AM, ASR, A2, A4, A4S, A6, A8, A8M, A8S, A16, A16S, E16S, A32, A32M, A64, A128, AG, AK, AI, AIO, AP.  

### Firmware e Ferramenta de Flash para ESP32  

🔹 **KCS Firmwares (Site Oficial):**  
📌 [Acesse aqui](https://www.kincony.com/forum/showthread.php?tid=7283)  

🔹 **Firmware (Dezembro/2024) no meu Google Drive:**  
📂 [Baixar](https://drive.google.com/drive/folders/1Fup9QsRdzn4ofuia9ehP4mfLLNi64piE?usp=drive_link)  

🔹 **Firmware Kincony v2.2.10 (Janeiro/2025):**  
📌 [Acesse aqui](https://www.kincony.com/forum/showthread.php?tid=7283)  


## Hardware Resource  

- Ethernet/WiFi/Bluetooth/RS485  
- 16 canais de saída de relé  
- 16 canais de entrada digital  
- Transmissor RF 433MHz  
- Receptor RF 433MHz  
- 2 canais de entrada analógica (DC 0-5V)  
- 2 canais de entrada analógica (4-20mA)  
- 4 canais GPIO (com resistor pull-up)  
- Porta de expansão IIC  

🔗 [Mais informações sobre o firmware KCS v2](https://www.kincony.com/esp32-kcsv2-firmware.html)  

## Como Usar o Firmware "KCS" v2 para a Placa KinCony ESP32  

🔹 [Site Oficial da KinCony](https://www.kincony.com/)  
📄 [Guia do Usuário - KCS v2](https://www.kincony.com/images/user-guide/KCS_V2/KCS_user_guide_v2.0.pdf)  

### Download e Configuração do Firmware KCS v2  

1. **Baixar Ferramentas:**  
   - Baixe a ferramenta **ESP32 download tool** do link:  
     📂 [flash_download_tool_3.9.2.zip](https://www.kincony.com/wp-content/uploads/2022/08/flash_download_tool_3.9.2.zip)  
   - Baixe o arquivo BIN do firmware no **Fórum da KinCony**:  
     📌 [Acesse aqui](https://www.kincony.com/forum/forumdisplay.php?fid=40)  

2. **Abrir a Ferramenta:**  
   - Execute o programa `flash_download_tool_3.9.2.exe`.  

3. **Selecionar Configurações de Chip:**  
   - **Se o chip da sua PCB for ESP32-WROOM-32E/32UE**, escolha:  
     - **ESP32** e o item **develop**.  

     ![ESP32 Download Tool](how%20to%20use_arquivos/image001.png)  

   - **Se o chip da sua PCB for ESP32-S3-WROOM-1U**, escolha:  
     - **ESP32-S3** e os modos de trabalho **develop** e **usb**.  

     ![ESP32-S3 Download Tool](how%20to%20use_arquivos/image002.png)  

4. **Selecionar Arquivo e Porta COM:**
   - Escolha o arquivo BIN do firmware KCS v2.
   - Selecione a porta COM correspondente e inicie o download em 5 etapas.
 <img border=0 width=508 height=697 id="Imagem 142" src="how%20to%20use_arquivos/image003.png" alt="esp32 download tool"><span lang=EN-US><br>
<b>2. Use o cabo ethernet or WiFi config setting.</b></span></p>

1. use a placa de conexão do cabo Ethernet ao seu roteador, certifique-se de que seu computador também se conecte ao mesmo roteador, apenas em uma rede local.
2. Ligue sua placa, você pode usar a ferramenta de digitalização do dispositivo KinCony para encontrar o endereço IP da placa de saída.

 <a href="https://www.kincony.com/download/UDP_SCAN_LIST.zip"><span
lang=EN-US>https://www.kincony.com/download/KinCony-SCAN_Device.zip</span></a></p>

 <img border=0 width=567 height=257 id="Imagem 141"
src="how%20to%20use_arquivos/image137.jpg" alt="scan device"></p>

 ## Uso da Ferramenta de Varredura de Dispositivos KinCony

![Scan Device](how%20to%20use_arquivos/image137.jpg)

## Passos para encontrar o endereço IP

1. Escolha o adaptador de rede do seu computador que está em uso.
2. Escolha o item do endereço IP do seu computador.
3. Clique no botão **"StartMonitorPort"**.
4. Clique no botão **"SCAN"**.
5. O endereço IP da placa (Ethernet ou WiFi), ID e nome do tipo serão listados.

Se esta for a primeira vez que a placa for ligada, ela será encontrada pelo endereço IP da Ethernet, pois, por padrão, o WiFi opera no modo **"AP"**.  
Após configurar o WiFi no modo **"STA"**, você poderá encontrar o endereço IP do WiFi usando a ferramenta KinCony Scan Device.

Você pode usar o endereço IP da Ethernet para acessar a configuração da placa pelo navegador.

### Observação:
Se desejar configurar a placa apenas pelo WiFi, ao ligá-la, seu computador encontrará o ponto de acesso **"AP"** com um sinal WiFi nomeado como **"Nome da Placa" + "ID"**.

![Modo AP](how%20to%20use_arquivos/image006.png)

## Conectando ao Modo AP

Deixe seu computador se conectar ao **"AP"**, que não possui senha.  
Após a conexão, acesse a página de login pelo navegador usando:  
[http://192.168.4.1](http://192.168.4.1)

Se você não conseguir ver o **"AP"**, mantenha pressionado o botão de função da placa (ESP32 GPIO0) por mais de **10 segundos**. Isso irá restaurar as configurações de fábrica, onde o estado padrão é **"AP"**.

![Login IoT](how%20to%20use_arquivos/image007.png)

## Login via Ethernet ou WiFi

Você pode acessar a página de configuração pelo endereço IP da Ethernet ou do WiFi.  
Exemplo de login usando o endereço IP da Ethernet: **192.168.1.200**.

Os dados padrão de login são:  

**Usuário:** `admin`  
**Senha:** `admin`

![Página Inicial](how%20to%20use_arquivos/image138.jpg)

Após o login, a página inicial será exibida, mostrando alguns parâmetros do dispositivo.

![Página de Entrada](how%20to%20use_arquivos/image139.jpg)

## Configuração de Entradas Digitais

Na página **INPUT**, você pode configurar como cada porta de entrada digital interage com as portas de saída.


## Reverse Level - Inversão de Nível da Entrada Digital  

Se marcado, o nível efetivo na porta de entrada digital será **invertido**.  
A entrada digital é utilizada apenas com nível **"HIGH"** ou **"LOW"**.  

Normalmente, a porta de entrada digital conectada ao **GND** = **acionamento**.  

<img border=0 width=566 height=388 id="Imagem 136"
src="how%20to%20use_arquivos/image140.jpg" alt="output type"></p>

 Aqui está a homepage de saida.</p>

 <img border=0 width=554 height=402 id="Imagem 135"
src="how%20to%20use_arquivos/image014.png" alt="output type"></p>

## Hold on
keep the state after turn ON/OFF

## Delay
 
 Depois de ligar a saída digital, ela será desligada automaticamente após um "tempo de atraso" pré-definido.

## Jogging  

Quando mantenho o **INPUT** conectado ao **GND**, a **saída digital** fica **LIGADA**.  
Ao soltar o **INPUT** do **GND**, a **saída digital** será **DESLIGADA** imediatamente.  

 <img border=0 width=567 height=299 id="Imagem 134"
src="how%20to%20use_arquivos/image141.jpg" alt=interlock></p>

 ## Grupo de Intertravamento  

**"Grupo de intertravamento"**: define o grupo de intertravamento para a saída digital. Se definido como **"0"**, a função de intertravamento será desativada.  

- Se **"Output1"** for definido como **"1"** e **"Output2"** for definido como **"1"**, então **Output1 e Output2 trabalharão com intertravamento**.  
- Se **"Output3"** for definido como **"2"** e **"Output4"** for definido como **"2"**, então **Output3 e Output4 trabalharão com intertravamento**.  

Por exemplo, o **KC868-A64** possui **64 saídas digitais**, portanto, o total será **64/2 = 32 grupos de intertravamento**.  


## Página de Configuração RF

![RF 433](how%20to%20use_arquivos/image142.jpg)

Nesta página, é possível **"Aprender"**, **"Transmitir"** e **"Excluir"** códigos RF.  
Compatível com os códigos de controle remoto sem fio **EV1527, PT2262 e PT2264**.

Quando pressionar o botão azul **"Learn"**, o modo de aprendizado será iniciado.  
Aguarde e pressione um botão no controle remoto. A seguinte mensagem será exibida:

![RF 433](how%20to%20use_arquivos/image143.jpg)

Em seguida, pressione um botão do controle remoto:

![RF 433](how%20to%20use_arquivos/image144.jpg)

Se o sinal for aprendido com sucesso, será exibido:

![RF 433](how%20to%20use_arquivos/image145.jpg)

Se o aprendizado falhar ou houver um tempo limite, será exibido:

![RF 433](how%20to%20use_arquivos/image146.jpg)

Após o aprendizado do sinal, ele será salvo no controlador.

---

## Página de Configuração IR

![IR Webpage](how%20to%20use_arquivos/image147.jpg)

Nesta página, é possível **"Aprender"**, **"Transmitir"** e **"Excluir"** códigos IR.  
Compatível com dispositivos como **TVs, DVDs, ar-condicionado, ventiladores** e outros dispositivos infravermelhos.

Ao pressionar o botão azul **"Learn"**, o modo de aprendizado será iniciado.  
Aguarde e pressione um botão no controle remoto IR. A seguinte mensagem será exibida:

![IR](how%20to%20use_arquivos/image148.jpg)

Em seguida, pressione um botão do controle remoto:

![IR Remote](how%20to%20use_arquivos/image149.jpg)

Se o sinal for aprendido com sucesso, será exibido:

![IR Remote](how%20to%20use_arquivos/image150.jpg)

Se o aprendizado falhar ou houver um tempo limite, será exibido:

![IR Remote](how%20to%20use_arquivos/image151.jpg)

Após o aprendizado do sinal, ele será salvo no controlador.

---

## Página de Configuração de Sensores

![Sensor Webpage](how%20to%20use_arquivos/image152.jpg)

Nesta página, você pode configurar diferentes sensores para as portas GPIO de 1-wire.

### **Limite de Temperatura**
Se a diferença predefinida for excedida, os dados de temperatura serão **atualizados automaticamente**.

Exemplo:  
Se o **"Limite de Temperatura"** for **2°C** e a temperatura atual for **28°C**,  
os dados serão atualizados quando a temperatura for **maior que 30°C (28+2)** ou **menor que 26°C (28-2)**.

### **Limite de Umidade**
Se a diferença predefinida for excedida, os dados de umidade serão **atualizados automaticamente**.

Exemplo:  
Se o **"Limite de Umidade"** for **10%** e a umidade atual for **75%**,  
os dados serão atualizados quando a umidade for **maior que 85% (75+10)** ou **menor que 65% (75-10)**.

## Página de Monitoramento

![Monitor IoT](how%20to%20use_arquivos/image154.jpg)

Nesta página, é possível monitorar o estado de funcionamento de todos os protocolos.  
É possível verificar se há conexão com o servidor ou se algum cliente está conectado.

![Monitor de Protocolo](how%20to%20use_arquivos/image155.jpg)

Também é possível monitorar os valores do ADC.

![Monitor ADC](how%20to%20use_arquivos/image156.jpg)

Para facilitar a visualização dos valores de cada sensor, podemos configurar:  
- Nome do canal do sensor  
- Faixa de medição  
- Unidade de exibição  
- Limite para atualização automática  

Para acessar a página de configuração, clique no ícone de **"engrenagem"**.

![Configuração ADC](how%20to%20use_arquivos/image157.jpg)

### **Exemplo de Configuração**
Se configurarmos um sensor analógico de nível de água:
- Nome: **"Nível da Água"**
- Unidade: **M (metro)**
- **Custom value1** e **Custom value2** definem a conversão do sensor analógico de 0-5V.  
  - Se a tensão do sensor for **0V**, qual o valor correspondente?  
  - Se a tensão do sensor for **5V**, qual o valor correspondente?  

Exemplo: Um sensor de **0-5V** pode ser convertido para **0-3 metros**.

Se estiver usando um sensor de **4-20mA**, a conversão será:
- **4mA = Custom value1**
- **20mA = Custom value2**

![Leitura ADC](how%20to%20use_arquivos/image158.jpg)

Após a configuração, o nome do sensor, o valor e a unidade serão exibidos na página de monitoramento.

![Renomear Entrada](how%20to%20use_arquivos/image159.jpg)

### **Renomeando Entradas e Saídas**
- **Clique duas vezes** no nome de uma entrada para renomeá-la.

![Renomeação](how%20to%20use_arquivos/image160.jpg)

Após a alteração, o novo nome será exibido.

![Renomeação de Saída](how%20to%20use_arquivos/image161.jpg)

O mesmo procedimento pode ser usado para renomear as **saídas**.

![Estado do Sensor](how%20to%20use_arquivos/image162.jpg)

### **Ícones de Estado**
- **Ícone verde para ENTRADA**: Significa que foi acionada.  
- **Ícone verde para SAÍDA**: Significa que a saída está LIGADA.

---

## Página de Automação IFTTT

![Página IFTTT](how%20to%20use_arquivos/image163.jpg)

Nesta página, é possível criar **automação IFTTT**.  
- Pressione o botão azul **"Run"** para testar a execução.  
- Pressione o botão amarelo **"Edit"** para modificar a automação.

![Configuração IFTTT](how%20to%20use_arquivos/image164.jpg)

![Configuração IFTTT](how%20to%20use_arquivos/image165.jpg)

Se sua placa suportar o **módulo 4G SIM7600**, haverá opções para envio de **SMS** e **chamadas de voz**.

Também é possível renomear a automação, além de **ativá-la ou desativá-la**.

![Ativar ou Desativar Automação](how%20to%20use_arquivos/image166.jpg)

## Opções de Configuração

### **Opções de Entrada Digital (DI)**
![Opções DI](how%20to%20use_arquivos/image167.jpg)

### **Opções de Entrada Analógica (AI)**
![Opções AI](how%20to%20use_arquivos/image168.jpg)

### **Opções de RF**
![Opções RF](how%20to%20use_arquivos/image169.jpg)

### **Opções de Sensores**
![Opções de Sensores](how%20to%20use_arquivos/image170.jpg)

---

## **Opções de Temporizador**
Se sua placa for compatível com o **módulo 4G SIM7600**, as opções de **SMS** e **chamada de voz** estarão disponíveis.

![Opções de Temporizador](how%20to%20use_arquivos/image171.jpg)

### **Opções de SMS**
![Opções de SMS](how%20to%20use_arquivos/image172.jpg)

### **Opções de Chamadas de Voz**
![Opções de Chamadas de Voz](how%20to%20use_arquivos/image173.jpg)

---

## **Opções Lógicas**
Se a opção **[AND Lógico]** estiver ativada, **todas as condições IF devem ser atendidas** antes da execução da ação.  
Se a opção estiver **desativada**, todas as condições IF funcionarão com a lógica **"OU"**.

![Configuração Lógica](how%20to%20use_arquivos/image174.jpg)

---

## **Opções de Saída Digital (DO)**

Você pode definir várias saídas digitais separadas por um **espaço**.  
Por exemplo, insira `"1 2 3 4 5"` ou `"1-5"` na opção correspondente para ativar ou desativar as saídas digitais **1 a 5**.

![Opções DO](how%20to%20use_arquivos/image175.jpg)

### **Exemplo de Configuração**
A imagem abaixo representa a seguinte configuração:
- **Ligar** as saídas digitais **1, 2 e 3**
- **Desligar** as saídas digitais **4, 5 e 6**
- **Alternar** (toggle) as saídas digitais **7, 9, 10, 15-32**

![Exemplo de Configuração](how%20to%20use_arquivos/image176.jpg)

---

## **Opções de Saída Analógica (AO)**
![Opções AO](how%20to%20use_arquivos/image177.jpg)

## Opções de Configuração

### **Opções de RF**
![Opções RF](how%20to%20use_arquivos/image178.jpg)

### **Opções de Infravermelho (IR)**
![Opções IR](how%20to%20use_arquivos/image179.jpg)

### **Opções de Atraso (Delay)**
![Opções Delay](how%20to%20use_arquivos/image180.jpg)

### **Opções de Protocolo Personalizado**
![Protocolo Personalizado](how%20to%20use_arquivos/image181.jpg)

### **Opções de SMS**
![Opções SMS](how%20to%20use_arquivos/image182.jpg)

### **Opções de Chamadas de Voz**
![Opções de Chamadas de Voz](how%20to%20use_arquivos/image183.jpg)

---

## **Automação IFTTT**
Após criar uma automação, será possível visualizar todas as condições **IF** e **THEN**.  
É possível **salvar** a automação como **"scene1"** ou modificar clicando no pequeno ícone de edição.

![Configuração IFTTT](how%20to%20use_arquivos/image184.jpg)

---

## **Configuração de Rede**
Ajustes para **Ethernet** e **WiFi**.

Se configurar o WiFi no **modo AP**, dispositivos como celulares ou tablets poderão se conectar diretamente à placa sem precisar de um roteador.

![Modo AP](how%20to%20use_arquivos/image103.png)

Se configurar o WiFi no **modo STA** e conectar a placa ao roteador via cabo Ethernet,  
a placa usará a conexão Ethernet prioritariamente. Caso o cabo seja desconectado,  
ela alternará automaticamente para WiFi, garantindo conectividade contínua com o roteador.

![Configuração GPRS](how%20to%20use_arquivos/image185.jpg)

---

## **Rede GSM**
Nesta página, é possível ativar ou desativar o **módulo GSM**.  
Se desativado, **SMS, chamadas de voz e GPRS** não funcionarão.

É possível cadastrar até **6 números de telefone** como administradores.  
Apenas esses números poderão utilizar as funções de SMS e chamadas.

![Teste de GSM](how%20to%20use_arquivos/image186.jpg)

Você pode selecionar um número e enviar uma **mensagem** ou realizar uma **chamada de teste**.

![Configuração de SMS](how%20to%20use_arquivos/image187.jpg)

É possível **personalizar o conteúdo do SMS** para ser usado nas **condições IF**.  
Os textos podem ser definidos em qualquer idioma, não apenas em inglês.

![Configuração de Notificação SMS](how%20to%20use_arquivos/image188.jpg)

Também é possível definir um SMS para **ações THEN**, como notificações de alarme.

![Configuração de Chamadas de Voz](how%20to%20use_arquivos/image189.jpg)

### **Controle de Chamadas de Voz**
É possível definir **códigos DTMF** para ações IF.  
Por exemplo:
- Quando ligar para a placa, ao conectar, pressione **"10#"** para **ligar o relé 1**.
- Pressione **"11#"** para **desligar o relé 2**.

![Configuração de Protocolo](how%20to%20use_arquivos/image190.jpg)

---

## **Configuração de Protocolos**
![Protocolo RS485](how%20to%20use_arquivos/image191.jpg)

Nesta página, é possível ativar ou desativar diferentes protocolos.  
Os documentos de referência podem ser baixados no site da **KinCony**.

![Protocolo Tuya](how%20to%20use_arquivos/image118.png)

### **Configuração do Tuya**
Se desejar controlar e monitorar remotamente sua placa via internet pelo **Tuya App**,  
é necessário adquirir uma **licença Tuya** com a KinCony.

Caso tenha comprado a licença, basta preencher os campos:
- **Product ID**
- **Device ID**
- **Device Secret**
- **Bind Code**

Após preencher, um **QR Code** será gerado automaticamente para adicionar a placa ao **Tuya App**.

Se a placa possuir um **módulo 4G SIM7600**, também é possível usar o Tuya via **GPRS**.

![Configuração do Tuya App](how%20to%20use_arquivos/image192.jpg)

---

## **Protocolos Personalizados**
![Página de Protocolos](how%20to%20use_arquivos/image193.jpg)

Nesta página, é possível criar mensagens para os seguintes protocolos:
- **TCP Client**
- **UDP Client**
- **RS232**
- **RS485**
- **HTTP GET**
- **HTTP POST**

Se a opção **"HEX"** não estiver marcada, as mensagens serão enviadas como **strings ANSI**.

### **Exemplo**
Se desejar enviar um comando **TCP** para outro módulo de relé e ativar **relay1**:

![Protocolo TCP](how%20to%20use_arquivos/image194.jpg)

![Cliente TCP](how%20to%20use_arquivos/image195.jpg)

Certifique-se de que o **protocolo TCP Client** está ativado.  
O endereço **192.168.1.215**, porta **4196**, é outro módulo de relé.

A string **"RELAY-SET-255,1,1"** será enviada para **IP: 192.168.1.215**, porta **4196**, via TCP.

### **Exemplo**
Enviar um comando HTTP GET:

![Exemplo HTTP](how%20to%20use_arquivos/image196.jpg)

Isso significa que será enviado o comando:

´´[
http://192.168.1.200/sw_ctl.cgi?Relay01=ON&postpwd=abcd
´´´

Se precisar adicionar parâmetros adicionais, basta preenchê-los no campo **"Message"**.

![Configuração HTTP Server](how%20to%20use_arquivos/image197.jpg)

Certifique-se de ativar o **protocolo HTTP Server** e definir a **chave de requisição** para segurança.

---

## **Configuração RS485**
Se sua placa possuir suporte ao **RS485**, essa opção será exibida.

![Configuração RS485](how%20to%20use_arquivos/image198.jpg)

---

## **Configuração do Sistema**
![Página do Sistema](how%20to%20use_arquivos/image199.jpg)

### **Opções do Sistema**
- **"Manter saída após reinício"**: Após uma queda de energia, a placa pode restaurar automaticamente o estado das saídas digitais.
- **"Envio automático de valores ADC"**: A cada 5 segundos, os valores das entradas analógicas são enviados pelo protocolo configurado.
- **"Tempo de clique duplo"**: Ajusta a velocidade do clique duplo.
- **"Tempo de pressionamento"**: Ajusta o tempo para reconhecimento de pressionamento longo ou curto.

![Reinicialização do Sistema](how%20to%20use_arquivos/image200.jpg)

### **Opções de Reinicialização**
- **"Reiniciar Placa"**: Reinicia o dispositivo.
- **"Restaurar Configuração de Fábrica"**: Apaga todas as configurações e retorna ao modo **AP**.

---

## **Links Úteis**
- [Guia do Usuário](https://www.kincony.com/user-guide)
- [Autor: Admin](https://www.kincony.com/author/kinconyadminuu)
- **Data da Publicação:** 20/07/2023
- **Página do Produto:** [ESP32 Board 16-Channel Relay](https://www.kincony.com/esp32-board-16-channel-relay-hardware.html)


