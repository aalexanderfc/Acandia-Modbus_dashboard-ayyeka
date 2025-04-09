# 🛰️ Acandia Modbus Dashboard with Ayyeka Integration

This portfolio project demonstrates a secure and scalable IoT solution for decoding, visualizing, and forwarding telemetry data from **Ayyeka Wavelet devices** using **Modbus Dashboard UI** and optionally forwarding data to **Ayyeka Cloud**.

> 💡 This is a fully automated system powered by **Python**, **MQTT**, **Protobuf**, **Flask**, and **Modbus TCP** – running on a **Robustel router**.

---

## 📸 System Architecture

This diagram shows the architecture of the **Ayyeka variant** of the dashboard:

![System Architecture](/images/AyyekaDiagram.png)

---

## 🔧 Key Functionalities

- ✅ **Decode Protobuf binary telemetry** from Ayyeka Wavelets over MQTT
- ✅ **Visualize data locally** in a Modbus-style dashboard interface
- ✅ **Forward telemetry to Ayyeka Cloud** with device-specific credentials
- ✅ **Register devices and assign Modbus register mappings**
- ✅ **Expose decoded values as Modbus registers** for external systems
- ✅ **Dual-mode operation**:
  - **Local-Only**: telemetry stays inside the local router
  - **Cloud-Forwarded**: telemetry is also forwarded to Ayyeka Cloud

---

## 🖥️ Dashboard Interfaces

### 1. **Modbus Dashboard - Main UI**

Used for visualizing data, listing all connected devices, and interacting with them.

![Dashboard View](/images/modbus-dashboard-view.png)

---

### 2. **Device Register View**

Displays detailed Modbus register mappings for a selected device, including sensor type, scaled values, units, and addresses.

![Register View](/images/modbus_register_view.png)

---

### 3. **Device Management Interface**

Allows management of discovered and confirmed devices. You can delete or rename devices, assign slave IDs, etc.

![Device Management](/images/device_management_overview.png)

---

### 4. **Cloud Variant – Ayyeka Cloud UI**

When forwarding is enabled, data is also visible in the **Ayyeka Cloud platform**.



---

## 🔀 Interface Variants

| Variant          | Description                                                                 |
|------------------|-----------------------------------------------------------------------------|
| 🟢 **Local-Only**     | All telemetry is decoded and used internally for Modbus + UI, no cloud involved. |
| ☁️ **Ayyeka-Forwarded** | Telemetry is also forwarded as RAW Protobuf (plus `reportend`) to Ayyeka Cloud.  |

Both variants share the same UI and MQTT decoding pipeline. The only difference is whether or not the Ayyeka Cloud forwarding logic is activated.



## 📬 Contact

Acandia AB – [info@acandia.se](mailto:info@acandia.se)  
🔗 https://www.acandia.se

---

## 🧠 Author

**Alexander Flores**  
IoT Developer @ Acandia  
🔗 https://github.com/aalexanderfc

---

### ✅ Let me know if you'd like me to generate the final `README.md` file or push it to your repository via CLI instructions!
