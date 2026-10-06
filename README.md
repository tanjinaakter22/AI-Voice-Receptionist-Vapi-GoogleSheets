
# 🎙️ AI Voice Receptionist & Booking System for Salon & Spa

An end-to-end automated **AI Voice Agent** for **"AI Salon & Spa"** built using **Vapi.ai** and **Google Sheets**. This voice assistant handles incoming phone calls, answers customer inquiries about salon services, pricing, and availability, and logs confirmed bookings directly into Google Sheets in real time.

---

## 📹 Demo Video

[AI Salon.webm](https://github.com/user-attachments/assets/7f575e7b-a28d-4d7b-99e2-280c36b88008)



---

## ✨ Key Features

- 🗣️ **Conversational Voice AI**: Human-like interaction powered by Vapi.ai with fast response latency.
- 💅 **Automated Inquiry Handling**: Dynamically provides pricing, duration, and details for Haircare, Skincare, Nails, and Makeup services.
- 📅 **Real-time Appointment Booking**: Collects customer details and generates sequential booking IDs (e.g., `A005`, `A006`).
- 📊 **Google Sheets Backend Integration**: Direct connection with Google Sheets to store booking details without third-party webhook dependencies.
- 🔄 **Dynamic Data Schema**: Strict column mapping ensuring zero column-shifting errors during data insertion.

---

## 📐 Architecture & Workflow

1. **Incoming Call**: Customer calls the AI Salon & Spa phone line.
2. **Context Resolution**: The voice agent queries its system instructions to answer questions regarding services, prices, or staff availability.
3. **Information Extraction**: The agent prompts for customer details (Name, Contact Number, Preferred Service, Date, Time Slot, and Staff preference).
4. **Tool Triggering**: Calls the native `CreateApponintments` Google Sheets tool.
5. **Database Log**: Data appends into the `Appointments!A:H` range with `Status` marked as `Booked`.

---

## 📊 Google Sheets Database Structure

### 1. `Appointments` Tab (Bookings Database)

| Column | Header | Description | Example |
| :---: | :--- | :--- | :--- |
| **A** | `Appointment Id` | Auto-generated sequential ID | `A005` |
| **B** | `Name` | Customer's full name | `Tanjina` |
| **C** | `Phone` | Customer's contact number | `01963 454559` |
| **D** | `Service` | Requested service name | `Haircut` / `Hair Coloring` |
| **E** | `Date` | Appointment date | `10 October 2026` |
| **F** | `Time` | Preferred appointment time | `3:00 PM` |
| **G** | `Stuff` | Assigned staff member or 'Any' | `Any` / `Sarah` |
| **H** | `Status` | Current booking state | `Booked` |

---

### 2. `search_service` Tab (Knowledge Base)

| Service_ID | Service_Name | Category | Price (BDT) | Duration | Staff | Available |
| :---: | :--- | :--- | :---: | :---: | :--- | :---: |
| **S001** | Haircut | Hair | 500 | 45 min | Any | Yes |
| **S002** | Hair Coloring | Hair | 2500 | 120 min | Sarah | Yes |
| **S003** | Hair Spa | Hair Treatment | 1200 | 60 min | Sarah | Yes |
| **S004** | Facial | Skincare | 1500 | 60 min | Maria | Yes |
| **S005** | Deep Cleansing | Skincare | 2000 | 75 min | Maria | Yes |
| **S006** | Manicure | Nails | 800 | 45 min | Lisa | Yes |
| **S007** | Pedicure | Nails | 1000 | 60 min | Lisa | Yes |
| **S008** | Manicure + Pedicure | Nails | 1600 | 100 min | Lisa | Yes |
| **S009** | Bridal Makeup | Makeup | 5000 | 150 min | Maria | Yes |
| **S010** | Party Makeup | Makeup | 3000 | 90 min | Maria | Yes |

---

## 🛠️ Tech Stack

- **Voice AI Platform**: [Vapi.ai](https://vapi.ai)
- **Database Backend**: Google Sheets API
- **AI Engine**: GPT-4o / Google Gemini
- **Integration Layer**: Vapi Native Workspace Integrations

---

## 🚀 Setup & Configuration Guide

### 1. Database Setup
1. Create a Google Sheet named `AI Salon & Spa Database`.
2. Add an `Appointments` tab with headers: `Appointment Id`, `Name`, `Phone`, `Service`, `Date`, `Time`, `Stuff`, `Status`.
3. Add a `search_service` tab with your service list, prices, and staff assignments.

### 2. Vapi Tool Setup
1. Go to **Vapi Dashboard** > **Integrations** > Connect **Google Workspace**.
2. Navigate to **Tools** > **Create Tool** > Select **Google Sheets**.
3. **Tool Name**: `CreateApponintments`
4. **Spreadsheet ID**: `1tx_yigwoZ4J-WTEEHEWyVg4884VeLmWjmK1xn2RTruQ`
5. **Range**: `Appointments!A:H`

### 3. Vapi Assistant Configuration
1. Open your Assistant under **Assistants** > **AI Salon & Spa**.
2. Set the System Prompt to enforce passing parameters in the exact 8-column sequence:
   - `Appointment Id` (e.g., A005)
   - `Name`
   - `Phone`
   - `Service`
   - `Date`
   - `Time`
   - `Stuff`
   - `Status` (`Booked`)
3. Attach `CreateApponintments` tool and click **Publish**.

---



