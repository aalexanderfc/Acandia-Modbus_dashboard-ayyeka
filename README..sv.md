# 🛰️ Acandia Modbus Dashboard med Ayyeka-integration

Detta portföljprojekt demonstrerar en säker och skalbar IoT-lösning för att avkoda, visualisera och vidarebefordra telemetridata från **Ayyeka Wavelet-enheter** med hjälp av **Modbus Dashboard UI**, och valfritt vidarebefordra data till **Ayyeka Cloud**.

> 💡 Detta är ett fullt automatiserat system byggt med **Python**, **MQTT**, **Protobuf**, **Flask** och **Modbus TCP** – och körs på en **Robustel-router**.

---

## 📸 Systemarkitektur

Diagrammet nedan visar arkitekturen för **Ayyeka-varianten** av dashboarden:

![Systemarkitektur](/images/AyyekaDiagram.png)

---

## 🔧 Nyckelfunktioner

- ✅ **Avkoda Protobuf binär telemetri** från Ayyeka Wavelets via MQTT
- ✅ **Visualisera data lokalt** i ett Modbus-liknande dashboardgränssnitt
- ✅ **Vidarebefordra telemetri till Ayyeka Cloud** med enhetsspecifika autentiseringsuppgifter
- ✅ **Registrera enheter och tilldela Modbus-registermappningar**
- ✅ **Exponera avkodade värden som Modbus-register** för externa system
- ✅ **Dubbel driftläge**:
  - **Endast lokalt**: all telemetri stannar i routern
  - **Molnkopplad**: data vidarebefordras även till Ayyeka Cloud

---

## 🖥️ Dashboard-gränssnitt

### 1. **Modbus Dashboard – Huvudgränssnitt**

Används för att visualisera data, visa alla anslutna enheter och interagera med dem.

![Dashboardvy](/images/modbus-dashboard-view.png)

---

### 2. **Registervy för enhet**

Visar detaljerade Modbus-register för en vald enhet, inklusive sensortyp, skalade värden, enheter och adresser.

![Registervy](/images/modbus_register_view.png)

---

### 3. **Enhetshantering**

Används för att hantera upptäckta och bekräftade enheter. Här kan du ta bort, byta namn eller tilldela slave-ID:n.

![Enhetshantering](/images/device_management_overview.png)

---

### 4. **Molnvariant – Ayyeka Cloud UI**

När vidarebefordran är aktiverad visas data även i **Ayyeka Cloud-plattformen**.

---

## 🔀 Gränssnittsvarianter

| Variant             | Beskrivning                                                                      |
|---------------------|-----------------------------------------------------------------------------------|
| 🟢 **Endast lokalt**     | All telemetri avkodas och används lokalt i Modbus + UI, inget moln inblandat.      |
| ☁️ **Ayyeka-vidarebefordran** | Telemetrin vidarebefordras även som RAW Protobuf (plus `reportend`) till molnet. |

Båda varianterna använder samma användargränssnitt och MQTT-avkodning. Enda skillnaden är om vidarebefordran till molnet är aktiverad.

---

## 📬 Kontakt

Acandia AB – [info@acandia.se](mailto:info@acandia.se)  
🔗 https://www.acandia.se

---

## 🧠 Författare

**Alexander Flores**  
IoT-utvecklare @ Acandia  
🔗 https://github.com/aalexanderfc

