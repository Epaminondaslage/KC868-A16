# KC868-A Series Board Protocol – MQTT Command

**Note:** This protocol document applies to KinCony smart controllers:
- KC868-AM, ASR, A2, A4, A4S, A6, A8, A8M, A8S, A16, A16S, E16S, A32, A32M, A64, A128, AG, AK, AI, AIO, AP.

Different boards have different channels for digital output, digital input, ADC, and DAC. The protocol remains the same; only the channel numbers need to be adjusted based on the hardware resources.

---

## MQTT Topics Format

- **Command topic format:** `Board model/UID/SET`
- **State topic format:** `Board model/UID/STATE`

For example, using **KC868-A64**:
- **Command topic:** `KC868_A64/B48A0A404664/SET`
- **State topic:** `KC868_A64/B48A0A404664/STATE`

---

## Protocol Commands

### 1. Set ON/OFF for One Digital Output Channel
- **Send:**
  - `{"output64":{"value":true}}` → Turn **ON** `output64`.
  - `{"output64":{"value":false}}` → Turn **OFF** `output64`.

### 2. Feedback State
- The board will automatically feedback all states when:
  - It first connects to the MQTT broker.
  - A digital input/output state changes.

- **Example feedback:**
  - `{"output1":{"value":true}}` → `output1` is ON.
  - `{"output2":{"value":false}}` → `output2` is OFF.
  - `{"input3":{"value":true}}` → `input3` is triggered.
  - `{"input4":{"value":false}}` → `input4` is not triggered.

- **Feedback all states after a control command:**
  ```json
  {"output1":{"value":true},"output2":{"value":false},"input1":{"value":true},"input2":{"value":true},"adc1":{"value":2610},"dac1":{"value":10}}
  ```

### 3. Set DAC Value
- **Send:**
  - `{"dac1":{"value":58}}` → Set `DAC1` value to 58 (range: 0-255).

### 4. Digital Output All ON/OFF
- **Send:**
  - `{"all_outputs":{"value":true}}` → Turn **ON** all outputs.
  - `{"all_outputs":{"value":false}}` → Turn **OFF** all outputs.

### 5. Read All Board Data
- **Send:**
  - `{"get_datas":{"value":true}}`

- **Feedback example:**
  ```json
  {"input1":{"value":false},"input2":{"value":false},"output1":{"value":false},"adc1":{"value":0},"dac1":{"value":133},"sensor1":{"temperature":77.9,"humidity":-100.0}}
  ```
  
- **Note:** `-100` indicates invalid data.

### 6. Set ON/OFF for Multiple Digital Output Channels
- **Send:**
  ```json
  {"output1":{"value":true},"output2":{"value":false}}
  ```
- **Feedback all states:**
  ```json
  {"output1":{"value":true},"output2":{"value":false},"input1":{"value":true},"adc1":{"value":2610},"dac1":{"value":10}}
  ```

### 7. Send an IR Signal (Pre-learned)
- **Send:**
  - `{"run_ir":{"value":1}}` → Send IR signal with ID = 1.
- **Feedback:**
  - `{"run_ir1":{"value":"success"}}`

### 8. Send an RF Signal (Pre-learned)
- **Send:**
  - `{"run_rf":{"value":1}}` → Send RF signal with ID = 1.
- **Feedback:**
  - `{"run_rf1":{"value":"success"}}`

### 9. Set Beep Output
- **Send:**
  - `{"set_beep":{"value":1}}` → Turn **ON** beep.
  - `{"set_beep":{"value":0}}` → Turn **OFF** beep.
- **Feedback:**
  - `{"set_beep":{"value":"success"}}`

---

## Notes
- The temperature display unit can be set on the device’s webpage.
- Adjust commands and feedback formats based on the specific hardware resources of the KinCony board being used.
