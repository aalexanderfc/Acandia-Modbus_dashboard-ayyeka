# 🚀 Acandia Modbus Dashboard with Ayyeka Integration

This portfolio project demonstrates a secure and scalable IoT solution for decoding, visualizing, and optionally forwarding telemetry data from **Ayyeka Wavelet devices** using a **Modbus Dashboard UI**.

> 💡 The system runs fully automated on a **Robustel router** (or any Linux-based SBC) and is built using **Python**, **Flask**, **MQTT**, **Protobuf**, and **Modbus TCP**.

---

## 📸 System Architecture

This diagram illustrates the Ayyeka-integrated version of the dashboard:

![System Architecture](/images/AyyekaDiagram.png)

---

## 🔧 Key Functionalities

- ✅ **Decode Protobuf telemetry** from Ayyeka Wavelets over MQTT
- ✅ **Visualize structured data** in a responsive Modbus dashboard UI
- ✅ **Register and manage devices**, including slave ID assignment
- ✅ **Expose decoded values as Modbus registers** for external systems
- ✅ **Auto-started systemd services** for persistent operation
- ✅ **Dual-mode operation**:
  - **Local-Only**: All telemetry stays inside the local device
  - **Cloud-Forwarded**: Data is also forwarded to **Ayyeka Cloud**

---

## 🧱 Technologies Used

- 🐍 Python 3.11  
- 🧪 Flask (backend API), Jinja2 (UI templating)  
- 📶 MQTT with TLS using **Mosquitto**  
- 🧹 Protobuf (Google) for decoding Ayyeka payloads  
- ⚙️ systemd for reliable background services  
- 🔐 TLS certificates for encrypted MQTT communication

---

## 🔐 Security & Robustness

- 🔐 MQTT communication uses **port 8883** with **TLS certificates** and **user/password authentication**
- ↻ Services are launched using `systemd` for automatic recovery and persistence
- 🚫 No anonymous access: all brokers require valid authentication
- 🔄 Capable of running offline (local-only mode) or online (with cloud)

---

## 🖥️ User Interfaces

### 1. **Main Modbus Dashboard UI**
Lists all connected devices and their current status.

![Dashboard View](/images/modbus-dashboard-view.png)

---

### 2. **Device Register View**
Displays mapped Modbus registers for each device, showing register address, value, type, and unit.

![Register View](/images/modbus_register_view.png)

---

### 3. **Device Management Page**
Allows manual assignment of slave IDs, deletion of old devices, and confirmation of pending devices.

![Device Management](/images/device_management_overview.png)

---

## ☁️ Ayyeka Cloud Forwarding (Optional)

If enabled, telemetry is forwarded to the **Ayyeka Cloud**:

- Each device uses its credentials from `ayyeka_devices.json`
- Topics published:
  - `samp/<device_id>`
  - `reportend/<device_id>`
- Forwarding uses the same binary Protobuf payloads received locally
- MQTT broker: `mqtt.ayyeka.com` over port 8883 with TLS

---

## 🔀 Interface Variants

| Variant            | Description                                                                 |
|--------------------|-----------------------------------------------------------------------------|
| 🟢 **Local-Only**       | All telemetry is decoded and used internally; nothing leaves the device. |
| ☁️ **Cloud-Forwarded** | Telemetry is also sent to Ayyeka Cloud using MQTT and per-device creds.   |

The system supports toggling between these modes by enabling/disabling cloud-forwarding logic.

---

## 🧹 Modular Architecture

- 🧠 **Decoder**: `mqtt_decoder.py` runs as an independent background service
- 💻 **Web UI**: Flask-based dashboard served from `app.py` on port 5000
- ⚖️ **Modbus Server**: Handles register mappings in real time
- 🔌 **Separation of Concerns**:
  - `src/` contains all Modbus, Flask, and UI logic
  - `ayyeka_proto/` handles MQTT decoding and cloud forwarding

---

## 💠 Disabling Cloud Forwarding

To switch to **Local-Only Mode**, simply **disable the cloud forwarding logic** inside `mqtt_decoder.py`.

In the file `ayyeka_proto/mqtt_decoder.py`, comment or remove the following function call (if it exists):

```python
forward_to_ayyeka_cloud(device_id, binary_payload)
```

Also, you can **disable the MQTT publishing logic** to external brokers by skipping:

```python
client_cloud.publish(...)  # <- This can be commented or removed
```

📅 This allows the system to function **entirely offline**, decoding telemetry, mapping registers, and serving the local UI — without sending anything externally.

---

## 🧱 Contact

Acandia AB – [info@acandia.se](mailto:info@acandia.se)  
🔗 https://www.acandia.se

---

## 🧪 Author

**Alexander Flores**  
IoT Developer @ Acandia  
🔗 [github.com/aalexanderfc](https://github.com/aalexanderfc)

---

Made with ☕️ in Sweden 🇸🇪

