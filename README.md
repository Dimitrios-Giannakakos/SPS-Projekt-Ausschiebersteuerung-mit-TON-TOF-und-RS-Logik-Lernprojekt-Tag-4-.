# SPS-Projekt: Ausschiebersteuerung mit TON, TOF und RS-Logik (Lernprojekt Tag 4)

Dieses Projekt zeigt eine SPS-Steuerung für eine Förderanlage mit Ausschieberfunktion.  
Es wurde in TIA Portal erstellt und dokumentiert meinen Lernfortschritt am 4. Tag meiner SPS-Reise.

## 🔧 Funktionen
- Start/Stop/Not-Aus mit RS-Speicher
- RUN-Zustandsverwaltung (%M0.1)
- Förderbandfreigabe nach Einlaufbelegung (TOF)
- Ausschieberaktivierung bei Paketgroß (TON + RS)
- Rückstellung über Lichttaster und Timer
- Meldeleuchten für Anlagenstatus

## 🔍 Vorschau

![Netzwerk 2 – Start/Stop](SPS_Fup_01.PNG)  
![Netzwerk 3 – Förderbandfreigabe](SPS_Fup_02.PNG)  
![Netzwerk 4 – Ausschiebersteuerung](SPS_Fup_03.PNG)


## 💻 Logik-Ausschnitt

```plaintext
TON (PT = T#3s500ms)
IN: %M0.3  // Paketgroß erkannt
Q → RS.S

RS-Speicher
S: TON.Q
R: %M0.3
Q → TON2.IN

TON2 (PT = T#500ms)
IN: RS.Q
Q → %Q0.3 (Ausschieber)
     %Q0.4 (Ausschieber-Band)
