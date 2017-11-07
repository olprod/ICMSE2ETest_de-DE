---
title: Diagnostizieren von Fehlern in Windows 10 MDM
description: "Damit die diagnose Registrierung oder Gerät Management in Windows-10-Geräte von einem MDM Server verwaltet werden, können Sie die auf dem desktop oder mobilen Gerät erfassten MDM Protokolle überprüfen. Den folgenden Abschnitten werden die Verfahren zum Erfassen von Protokollen MDM."
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 12D8263B-D839-4B19-9346-31E0CDD0CBF9
ms.openlocfilehash: e3c1cea0b7aea25149c65989440e3c38018b062c
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="diagnose-mdm-failures-in-windows-10"></a>Diagnostizieren von Fehlern in Windows 10 MDM

Sie können damit diagnose Registrierung oder Gerät Management in Windows 10 Geräte von einem MDM Server verwaltet werden, die auf dem desktop oder mobilen Gerät erfassten MDM Protokolle überprüfen. Den folgenden Abschnitten werden die Verfahren zum Erfassen von Protokollen MDM.

## <a name="collect-logs-directly-from-windows-10-pcs"></a>Erfassen von Protokollen direkt aus Windows 10 PCs

Beginnend mit dem Windows-10, Version 1511, werden in der Ereignisanzeige an folgendem Speicherort MDM Protokolle erfasst werden:

-   Anwendungs- und Dienstprotokolle &gt; Microsoft &gt; Windows &gt; DeviceManagement-Enterprise-Diagnose-Anbieter

Es folgt ein Screenshot:

![MDM-Ereignisanzeige](images/diagnose-mdm-failures1.png)

An diesem Speicherort protokolliert der **Admin** -Kanal Ereignisse in der Standardeinstellung. Jedoch, wenn Sie weitere Details Protokolle benötigen, können Sie **Debugprotokolle** durch auswählen, dass **Anzeigen analytische und Debugprotokolle** Option im Menü " **Ansicht** " in der Ereignisanzeige protokolliert.

**Das Erfassen von Admin-Protokolle**

1.  Klicken Sie mit der rechten Maustaste auf den Knoten **Admin** .
2.  Wählen Sie **alle Ereignisse speichern unter**.
3.  Wählen Sie einen Speicherort aus, und geben Sie einen Dateinamen.
4.  Klicken Sie auf **Speichern**.
5.  Wählen Sie **Anzeigeinformationen für diese Sprachen aus** , und wählen Sie dann aus **englischen**.
6.  Klicken Sie auf **Ok**.

Für die ausführliche Protokollierung können Sie **Debugprotokolle** aktivieren. Klicken Sie mit der rechten Maustaste auf den Knoten **Debuggen** , und klicken Sie dann auf **Protokoll aktivieren**.

**Das Erfassen von Debug-Protokolle**

1.  Klicken Sie mit der rechten Maustaste auf den Knoten **Debuggen** .
2.  Wählen Sie **alle Ereignisse speichern unter**.
3.  Wählen Sie einen Speicherort aus, und geben Sie einen Dateinamen.
4.  Klicken Sie auf **Speichern**.
5.  Wählen Sie **Anzeigeinformationen für diese Sprachen aus** , und wählen Sie dann auf **Englisch**.
6.  Klicken Sie auf **Ok**.

Sie können die Protokolldateien (EVTX-Dateien) in der Ereignisanzeige auf einem Windows-10-PC ausführen das Update vom November 2015 öffnen.

## <a name="collect-logs-remotely-from-windows-10-pcs"></a>Erfassen von Protokollen Remote von Windows 10 PCs

Bei der PC bereits MDM registriert ist, können Sie Protokolle remote auf dem PC über den DDE-Kanal MDM sammeln, falls Ihre MDM Server dies unterstützt. [DiagnosticLog CSP](diagnosticlog-csp.md) kann zum Aktivieren eines Event Viewer Kanals durch den vollständigen Namen verwendet werden. Es folgen die Ereignisanzeige Namen für die Kanäle Admin und Debuggen:

-   Microsoft-Windows-DeviceManagement-Enterprise-Diagnostics-Provider%2FAdmin
-   Microsoft-Windows-DeviceManagement-Enterprise-Diagnostics-Provider%2FDebug

Beispiel: Debug-Channel-Protokollierung aktivieren

``` syntax
<SyncML xmlns="SYNCML:SYNCML1.2">
    <SyncBody>
        <Replace>
            <CmdID>2</CmdID>
            <Item>
                <Target>
                    <LocURI>./Vendor/MSFT/DiagnosticLog/EtwLog/Channels/Microsoft-Windows-DeviceManagement-Enterprise-Diagnostics-Provider%2FDebug/State</LocURI>
                </Target>
                <Meta>
                    <Format xmlns="syncml:metinf">bool</Format>
                </Meta>
                <Data>true</Data>
            </Item>
        </Replace>
        <Final/>
    </SyncBody>
</SyncML>
```

Beispiel: Exportieren der Debug-Protokolle

``` syntax
<?xml version="1.0"?>
<SyncML xmlns="SYNCML:SYNCML1.2">
    <SyncBody>
        <Exec>
            <CmdID>2</CmdID>
            <Item>
                <Target>
                    <LocURI>./Vendor/MSFT/DiagnosticLog/EtwLog/Channels/Microsoft-Windows-DeviceManagement-Enterprise-Diagnostics-Provider%2FDebug/Export</LocURI>
                </Target>
            </Item>
        </Exec>
        <Final/>
    </SyncBody>
</SyncML>
```

## <a name="collect-logs-from-windows-10-mobile-devices"></a>Erfassen von Protokollen durch Windows 10 Mobile Geräte

Da kein Ereignisanzeige in Windows 10 Mobile vorhanden ist, können Sie die app [Feld Sanitäter]( http://go.microsoft.com/fwlink/p/?LinkId=718232) das Erfassen von Protokollen verwenden.

**Das Erfassen von Protokollen manuell**

1.  Herunterladen Sie und installieren Sie die [Feld Sanitäter]( http://go.microsoft.com/fwlink/p/?LinkId=718232) app aus dem Speicher.
2.  Öffnen Sie die app Sanitäter Feld ein, und klicken Sie dann auf **Erweitert**.

    ![Feld Sanitäter screenshot](images/diagnose-mdm-failures2.png)

3.  Klicken Sie auf **auswählen, mit ETW-Anbieter verwendet**.

    ![Feld Sanitäter screenshot](images/diagnose-mdm-failures3.png)

4.  Überprüfen Sie **Enterprise** und deaktivieren Sie die restlichen.

    ![Feld Sanitäter screenshot](images/diagnose-mdm-failures4.png)

5.  Klicken Sie in der app auf **Protokollierung starten** , und führen Sie den Vorgang, den Sie behandeln möchten.

    ![Feld Sanitäter screenshot](images/diagnose-mdm-failures2.png)

6.  Wenn der Vorgang abgeschlossen ist, klicken Sie auf **Protokollierung stoppen**.

    ![Feld Sanitäter screenshot](images/diagnose-mdm-failures5.png)

7.  Speichern Sie die Protokolle. Sie werden in das Feld Sanitäter Protokollspeicherort auf dem Gerät gespeichert.
8.  Sie können die Protokolle per e-Mail senden, indem die Dateien aus der Anfügen **Dokumente &gt; Feld Sanitäter &gt; Berichte &gt; ...** Ordner.

    ![Gerät-Dokumentordner](images/diagnose-mdm-failures6.png)![Gerät Ordner screenshot](images/diagnose-mdm-failures7.png)![Gerät Ordner screenshot](images/diagnose-mdm-failures8.png)

Die folgende Tabelle enthält eine Liste der Anbieter für gemeinsame und ihre entsprechenden GUIDs.

| GUID                                 | Name des Anbieters                                          |
|--------------------------------------|--------------------------------------------------------|
| 099614a5-5dd7-4788-8bc9-e29f43db28fc | Microsoft-Windows-LDAP-Client                          |
| 0f67e49f-fe51-4e9f-b490-6f2948cc6027 | Microsoft-Windows-Kernel-Prozessor-Energie               |
| 0ff1c24b-7f05-45c0-ABDC-3c8521be4f62 | Microsoft-Windows-Mobile-Broadband-Experience-SmsApi   |
| 10e4f0e0-9686-4e62-b2d6-fd010eb976d3 | Microsoft-WindowsPhone-Shell-Ereignisse                    |
| 1e39b4ce-d1e6-46ce-b65b-5ab05d6cc266 | Microsoft-Windows-Netzwerk-RealTimeCommunication     |
| 22a7b160-f6e8-46b9-8e0b-a51989c85c66 | Microsoft-WindowsPhone-Bluetooth-AG                    |
| 2f94e1cc-a8c5-4fe7-a1c3-53d7bda8e73e | Microsoft-WindowsPhone-ConfigManager2                  |
| 331c3b3a-2005-44c2-ac5e-77220c37d6b4 | Microsoft-Windows-Kernel-Leistung                         |
| 33693e1d-246a-471b-83be-3e75f47a832d | Microsoft-Windows-BTH-BTHUSB                           |
| 3742be72-99a9-42E6-9fd5-c01a330e3625 | Microsoft-WindowsPhone-PhoneAudio                      |
| 3b9602ff-e09b-4c6c-bc19-1a3dfa8f2250 | Microsoft-WindowsPhone-OmaDm-Client-Anbieter           |
| 3da494e4-0fe2-415C-b895-fb5265c5c83b | Microsoft-WindowsPhone-Enterprise-Diagnose-Anbieter |
| 3f471139-acb7-4a01-b7a7-ff5da4ba2d43 | Microsoft-Windows-AppXDeployment-Server                |
| 4180c4f7-e238-5519-338f-ec214f0b49aa | Microsoft.Windows.ResourceManager                      |
| 4637124c-1d40-4b4d-892f-2aaecf24ff06 | Microsoft-Windows-WinJson                              |
| 4d13548f-c7b8-4174-bb7a-d7f64bf22d29 | Microsoft-WindowsPhone-LocationServiceProvider         |
| 4eacb4d0-263b-4b93-8cd6-778a278e5642 | Microsoft-Windows-GenericRoaming                       |
| 4f386063-ef17-4629-863c-d71597af743d | Microsoft-WindowsPhone-NotificationService             |
| 55404e71-4db9-4deb-a5f5-8f86e46dde56 | Microsoft-Windows-Winsock-NameResolution               |
| 59819d0a-adaf-46b2-8d7c-990bc39c7c15 | Microsoft-Windows-Batterie                              |
| 5c103042-7e75-4629-a748-bdfa67607fac | Microsoft-WindowsPhone-Leistung                           |
| 69c1c3f1-2b5c-41d0-A14A-c7ca5130640e | Microsoft-WindowsPhone-Cortana                         |
| 6ad52b32-d609-4be9-ae07-ce8dae937e39 | Microsoft-Windows-RPC-                                  |
| 7263516b-6eb0-477b-b64f-17b91d29f239 | Microsoft-WindowsPhone-BatterySense                    |
| 7dd42a49-5329-4832-8dfd-43d979153a88 | Microsoft-Windows-Kernel-Netzwerk                       |
| ae4bd3be-f36f-45b6-8d21-bdd6fb832853 | Microsoft-Windows-Audio                                |
| daa6a96b-f3e7-4d4d-a0d6-31a350e6a445 | Microsoft-Windows-WLAN-Treiber                          |
| 4d13548f-c7b8-4174-bb7a-d7f64bf22d29 | Microsoft-WindowsPhone-LocationServiceProvider         |
| 74e106b7-00be-4a55-b707-7ab58d6a9e90 | Microsoft-WindowsPhone-Shell-OOBE                      |
| cbda4dbf-8d5d-4f69-9578-be14aa540d22 | Microsoft-Windows-AppLocker                            |
| e595f735-b42a-494b-afcd-b68666945cd3 | Microsoft-Windows-Firewall                             |
| e5fc4a0f-7198-492f-9b0f-88fdcbfded48 | Microsoft Windows-VPN-Netzwerk                       |
| e5c16d49-2464-4382-bb20-97a4b5465db9 | Microsoft-Windows-WiFiNetworkManager                   |

 

## <a name="collect-logs-remotely-from-windows-10-mobile-devices"></a>Protokoll speichern Remote Windows 10 Mobile Geräte

Für mobile Geräte, die bereits in MDM registriert werden können Sie Remote MDM Protokolle über den mit dem [DiagnosticLog CSP](diagnosticlog-csp.md)MDM Kanal gespeichert.

DiagnosticLog CSP können zum Aktivieren des ETW-Anbieters. Die ID des Datenanbieters ist 3DA494E4-0FE2-415C-B895-FB5265C5C83B. In den folgenden Beispielen wird gezeigt, wie Sie zum Aktivieren des ETW-Anbieters:

Hinzufügen eines Knotens collector

``` syntax
<?xml version="1.0"?>
<SyncML xmlns="SYNCML:SYNCML1.2">
    <SyncBody>
        <Add>
            <CmdID>1</CmdID>
            <Item>
                <Target>
                   <LocURI>./Vendor/MSFT/DiagnosticLog/EtwLog/Collectors/MDM</LocURI>
                </Target>
                <Meta>
                    <Format xmlns="syncml:metinf">node</Format>
                </Meta>
            </Item>
        </Add>
        <Final/>
    </SyncBody>
</SyncML>
```

Fügen Sie den ETW-Anbieter zur Spur

``` syntax
<?xml version="1.0"?>
<SyncML xmlns="SYNCML:SYNCML1.2">
    <SyncBody>
        <Add>
            <CmdID>1</CmdID>
            <Item>
                <Target>
                    <LocURI>./Vendor/MSFT/DiagnosticLog/EtwLog/Collectors/MDM/Providers/3DA494E4-0FE2-415C-B895-FB5265C5C83B</LocURI>
                </Target>
                <Meta>
                    <Format xmlns="syncml:metinf">node</Format>
                </Meta>
            </Item>
        </Add>
        <Final/>
    </SyncBody>
</SyncML>
```

Starten von Ablaufverfolgungsprotokollen für die Sammlung

``` syntax
<?xml version="1.0"?>
<SyncML xmlns="SYNCML:SYNCML1.2">
    <SyncBody>
        <Exec>
            <CmdID>2</CmdID>
            <Item>
                <Target>
                    <LocURI>./Vendor/MSFT/DiagnosticLog/EtwLog/Collectors/MDM/TraceControl</LocURI>
                </Target>
                <Meta>
                    <Format xmlns="syncml:metinf">chr</Format>
                </Meta>
                <Data>START</Data>
            </Item>
        </Exec>
        <Final/>
    </SyncBody>
</SyncML>
```

Collector Trace Protokollierung beenden

``` syntax
<?xml version="1.0"?>
<SyncML xmlns="SYNCML:SYNCML1.2">
    <SyncBody>
        <Exec>
            <CmdID>2</CmdID>
            <Item>
                <Target>
                    <LocURI>./Vendor/MSFT/DiagnosticLog/EtwLog/Collectors/MDM/TraceControl</LocURI>
                </Target>
                <Meta>
                    <Format xmlns="syncml:metinf">chr</Format>
                </Meta>
                <Data>STOP</Data>
            </Item>
        </Exec>
        <Final/>
    </SyncBody>
</SyncML>
```

Nachdem die Protokolle auf dem Gerät erfasst werden, können Sie die Dateien über den MDM DDE-Kanal mithilfe des FileDownload Teils der DiagnosticLog CSP abrufen. Weitere Informationen hierzu finden Sie unter [DiagnosticLog CSP](diagnosticlog-csp.md).

## <a name="view-logs"></a>Anzeigen von Protokollen

Stellen Sie sicher, dass der PC oder virtueller Computer, auf denen Sie Protokolle anzeigen, den Build des Betriebssystems übereinstimmt, aus der die Protokolle erfasst wurden, um optimale Ergebnisse zu.

1.  Öffnen Sie eventvwr.msc.
2.  Mit der rechten Maustaste auf das **Ereignis Viewer(Local)** , und wählen Sie **Gespeichertes Protokoll öffnen**.

    ![Screenshot der Ereignis-viewer](images/diagnose-mdm-failures9.png)

3.  Navigieren Sie zu der Etl-Datei, die Sie von dem Gerät erhalten haben, und öffnen Sie dann die Datei.
4.  Klicken Sie auf **Ja,** Wenn Sie aufgefordert werden, auf das neue Format zu speichern.

    ![Aufforderung](images/diagnose-mdm-failures10.png)

    ![Diagnostizieren von Fehlern mdm](images/diagnose-mdm-failures11.png)

5.  Die neue Ansicht enthält Spuren aus dem Kanal. Klicken Sie auf im Menü **Aktionen** auf **Aktuelles Protokoll filtern** .

    ![Ereignisanzeige](images/diagnose-mdm-failures12.png)

6.  Fügen Sie einen Filter, indem Sie **DeviceManagement-EnterpriseDiagnostics-Anbieter** auswählen und Ereignisquellen, und klicken Sie auf **OK**.

    ![Ereignisfilters](images/diagnose-mdm-failures13.png)

7.  Jetzt sind Sie bereit, um die Überprüfung der Protokolle zu starten.

    ![Ereignisanzeige](images/diagnose-mdm-failures14.png)

## <a name="collect-device-state-data"></a>Sammeln von Zustandsdaten Gerät

Es folgt ein Beispiel zum Sammeln von aktuellen MDM Gerät Zustandsdaten mit dem [DiagnosticLog CSP](diagnosticlog-csp.md), Version 1.3, die im Windows 10, Version 1607 hinzugefügt wurde. Sie können die Datei auf dem Gerät mit demselben FileDownload Knoten im CSP, wie für die ETL-Dateien erfassen.

``` syntax
<?xml version="1.0"?>
<SyncML xmlns="SYNCML:SYNCML1.2">
  <SyncBody>
    <Exec>
      <CmdID>2</CmdID>
      <Item>
        <Target>
          <LocURI>./Vendor/MSFT/DiagnosticLog/DeviceStateData/MdmConfiguration</LocURI>
        </Target>
        <Meta>
           <Format xmlns="syncml:metinf">chr</Format>
        </Meta>
        <Data>SNAP</Data>
      </Item>
    </Exec>
    <Final/>
  </SyncBody>
</SyncML>
```

 






