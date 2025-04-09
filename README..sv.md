
# 🛰️ Acandia Modbus Dashboard med Ayyeka-integration

Detta portfolioprojekt demonstrerar en säker och skalbar IoT-lösning för att avkoda, visualisera och vidarebefordra telemetridata från **Ayyeka Wavelet-enheter** via **Modbus Dashboard UI**, med möjlighet att även skicka datan till **Ayyeka Cloud**.

> 💡 Systemet är helt automatiserat och byggt med **Python**, **MQTT**, **Protobuf**, **Flask** och **Modbus TCP** – och körs på en **Robustel-router**.

---

## 📸 Systemarkitektur

Diagrammet visar arkitekturen för **Ayyeka-varianten** av Modbus Dashboard-systemet:

![Systemarkitektur](/images/AyyekaDiagram.png)

---

## 🔧 Funktioner

- ✅ **Avkodar Protobuf-baserad binärdata** från Ayyeka Wavelets via MQTT
- ✅ **Visualiserar data lokalt** i ett Modbus-inspirerat gränssnitt
- ✅ **Vidarebefordrar telemetri till Ayyeka Cloud** med enhetsspecifika autentiseringsuppgifter
- ✅ **Registrerar enheter och tilldelar Modbus-register**
- ✅ **Exponerar avkodade värden som Modbus-register** för andra system
- ✅ **Två driftslägen**:
  - **Endast lokalt**: data stannar inom det lokala nätverket
  - **Moln-vidarebefordrat**: data skickas även till Ayyeka Cloud

---

## 🖥️ Dashboard-gränssnitt

### 1. **Modbus Dashboard – Huvudvy**

Används för att visualisera data, lista anslutna enheter och interagera med dem.

![Dashboard-vy](/images/modbus-dashboard-view.png)

---

### 2. **Registervy för enheter**

Visar detaljerad registermappning för en vald enhet – inklusive sensortyp, skalade värden, enheter och registeradresser.

![Registervy](/images/modbus_register_view.png)

---

### 3. **Enhetshantering**

Hantera upptäckta och bekräftade enheter. Här kan du ta bort eller döpa om enheter, samt tilldela slav-ID:n.

![Enhetshantering](/images/device_management_overview.png)

---

### 4. **Molnvariant – Ayyeka Cloud**

När vidarebefordran är aktiverad syns data också i **Ayyeka Cloud-portalen**.

(Bild saknas, men du kan lägga till den om du vill)

---

## 🔀 Gränssnittsvarianter

| Variant              | Beskrivning                                                                 |
|----------------------|-----------------------------------------------------------------------------|
| 🟢 **Endast lokalt**      | All telemetri avkodas och används lokalt för Modbus och UI, inget skickas till molnet. |
| ☁️ **Ayyeka-vidarebefordrat** | Telemetri skickas även vidare som rå Protobuf (plus `reportend`) till Ayyeka Cloud.  |

Båda varianterna delar samma UI och MQTT-avkodningslogik. Skillnaden ligger i huruvida data skickas vidare till molnet eller inte.

---

## 📬 Kontakt

**Acandia AB**  
📧 [info@acandia.se](mailto:info@acandia.se)  
🌐 https://www.acandia.se

---

## 🧠 Författare

**Alexander Flores**  
IoT-utvecklare @ Acandia  
🔗 https://github.com/aalexanderfc

