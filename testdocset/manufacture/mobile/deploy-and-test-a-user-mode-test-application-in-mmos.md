---
author: kpacquer
Description: Bereitstellen und Testen einer Benutzermodus-testanwendung in MMOS
ms.assetid: f8a7c14f-66b6-4023-86cb-c10bc3f52734
MSHAttr: PreferredLib:/library/windows/hardware
title: Bereitstellen und Testen einer Benutzermodus-testanwendung in MMOS
ms.openlocfilehash: 9cdb6abfb13eab870c71976b58a7f20aeb6aebe0
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="deploy-and-test-a-user-mode-test-application-in-mmos"></a>Bereitstellen und Testen einer Benutzermodus-testanwendung in MMOS


Zum Kopieren von Dateien zu einem Bild MMOS und Programme ausführen, können Sie FTP und Telnet über eine virtuelle Ethernet-Verbindung verwenden.

**Wichtige**  
Der USB-Treiber und Protokolle, die hier beschriebenen müssen in der Fertigung oder bei der Wartung Retail nicht verwendet werden. Sie werden aus Gründen der benutzerfreundlichkeit für engineering bringen-nach-oben bereitgestellt.

 

## <a name="span-idpreparingthedevicespanspan-idpreparingthedevicespanspan-idpreparingthedevicespanpreparing-the-device"></a><span id="Preparing_the_device"></span><span id="preparing_the_device"></span><span id="PREPARING_THE_DEVICE"></span>Vorbereiten des Geräts


Ping, FTP und Telnet-Server in der Regel mit Engineering Builds des Betriebssystems einschließen. Bestätigen Sie, dass diese in das Betriebssystem aktiv sind, überprüfen die Startkonfiguration ein, oder stellen eine Debug-Verbindung zu MMOS So zeigen Sie die Dateien an, die geladen werden.

Um ein Gerät, um die Unterstützung von TCP/IP über USB zu konfigurieren, müssen Sie Installieren der erforderlichen Tools und verwenden Sie das Tool BCDEdit Startoptionen das Gerät ändern, die in der BCD-Datei gespeichert sind.

## <a name="span-idrunningvirtualethernetanddeterminingtheipaddressofthedevicespanspan-idrunningvirtualethernetanddeterminingtheipaddressofthedevicespanspan-idrunningvirtualethernetanddeterminingtheipaddressofthedevicespanrunning-virtual-ethernet-and-determining-the-ip-address-of-the-device"></a><span id="Running_Virtual_Ethernet_and_determining_the_IP_address_of_the_device"></span><span id="running_virtual_ethernet_and_determining_the_ip_address_of_the_device"></span><span id="RUNNING_VIRTUAL_ETHERNET_AND_DETERMINING_THE_IP_ADDRESS_OF_THE_DEVICE"></span>Ausführen von virtuellen Ethernet und bestimmen die IP-Adresse des Geräts


Virtuelle Ethernet erstellt eine Verbindung zwischen dem Gerät USB-Verbindung und die TCP/IP-Transport auf dem PC. Starten Sie Herstellen einer Verbindung mit dem Gerät oder einschalten, virtuelle Ethernet auf dem PC. VirtEth.exe befindet sich der "%ProgramFiles(x86)%\\Microsoft Windows Phone 8 KDBG Connectivity\\Bin" Ordner.

Eine virtuelle Ethernet-Konsolenfenster wird geöffnet. Lassen Sie dieses Fenster zur Aufrechterhaltung der Verbindungs an das Telefon; Schließen des Fensters schließt die Verbindung.

1.  Mit virtuelle Ethernet-ausgeführt, eine Verbindung herstellen Sie, und schalten Sie das Telefon. Wenn das Gerät verbunden ist, sehen Sie Zeilen der Ausgabe, die die MAC-Adresse des Geräts enthalten. Virtuelle Ethernet-MAC-Adresse des Geräts in der Ausgabe ähnlich der folgenden Berichte:

    ``` syntax
    NIC UP: 00-11-38-EA-88-7E : SUCCESS
    ```

    Notieren Sie das Gerät 12 Ziffern MAC-Adresse aus dem Konsolenfenster VirtEth, und verwenden Sie es im nächsten Schritt, um das Gerät TCP/IP-Adresse zu ermitteln.

2.  Öffnen Sie ein neues Eingabeaufforderungsfenster, und geben Sie **Arp - ein**. Ausgabe ähnlich der folgenden wird angezeigt.

    ``` syntax
    C:\>arp -a

    Interface: 10.178.1.40 --- 0xb
      Internet Address      Physical Address      Type
      10.178.0.1            cc-ef-48-a7-6f-3f     dynamic
      10.178.1.94           00-11-38-ea-88-7e     dynamic
      10.178.3.255          ff-ff-ff-ff-ff-ff     static
      ... 
    ```

Verwenden Sie die IP-Adresse, die das Gerät für die Verbindung mit dem Gerät über FTP und Telnet-MAC-Adresse zugeordnet ist.

## <a name="span-idestablishinganftpconnectionspanspan-idestablishinganftpconnectionspanspan-idestablishinganftpconnectionspanestablishing-an-ftp-connection"></a><span id="Establishing_an_FTP_connection"></span><span id="establishing_an_ftp_connection"></span><span id="ESTABLISHING_AN_FTP_CONNECTION"></span>Herstellen einer FTP-Verbindung


Suchen nach, und Kopieren von Dateien über FTP:

-   Öffnen Sie Windows Explorer, und geben: **FTP:\\***W.X.Y.Z* in die Adressleiste ein, und Ersetzen Sie *W.X.Y.Z* durch die IP-Adresse des Geräts.

Die Dateien auf dem Gerät aufgeführten sollte angezeigt werden. Verwenden Sie Windows Explorer zum Kopieren von Dateien zum oder vom Gerät wie ausführbare Testprogramme oder Protokolle von Testergebnissen.

Um die FTP-Verbindung zu schließen, hängen Sie das Dateisystem Telefon durch Auswählen von **Hardware sicher entfernen** im Infobereich der Windows.

## <a name="span-idestablishingatelnetsessionspanspan-idestablishingatelnetsessionspanspan-idestablishingatelnetsessionspanestablishing-a-telnet-session"></a><span id="Establishing_a_Telnet_session"></span><span id="establishing_a_telnet_session"></span><span id="ESTABLISHING_A_TELNET_SESSION"></span>Einrichten einer Telnetsitzung


Stellen Sie sicher, dass auf dem PC Telnet aktiviert ist. Aktivieren, um aktivieren Telnet in das Betriebssystem Microsoft Windows **-Systemsteuerung** &gt; **Programme und Funktionen** &gt; **Windows-Features aktivieren oder deaktivieren**. Wählen Sie **Telnet-Client**, und klicken Sie dann auf **OK**, in der Liste Windows-Features.

So richten Sie eine Telnet-Sitzung mit dem Gerät

-   Öffnen Sie ein Eingabeaufforderungsfenster und geben: **Telnet** *W.X.Y.Z*, und Ersetzen Sie *W.X.Y.Z* durch die IP-Adresse des Geräts

Klicken Sie im Eingabeaufforderungsfenster wird cmd.exe auf dem Gerät ausgeführt. Diese Eingabeaufforderung können Sie Befehle ausführen, auf dem Gerät, z. B. testanwendungen, die Sie in das Bild MMOS enthalten ausgeführt.

## <a name="span-idtroubleshootingconfirmingtcpipconnectivityspanspan-idtroubleshootingconfirmingtcpipconnectivityspanspan-idtroubleshootingconfirmingtcpipconnectivityspantroubleshooting-confirming-tcpip-connectivity"></a><span id="Troubleshooting__Confirming_TCP_IP_connectivity"></span><span id="troubleshooting__confirming_tcp_ip_connectivity"></span><span id="TROUBLESHOOTING__CONFIRMING_TCP_IP_CONNECTIVITY"></span>Problembehandlung: Bestätigt wird TCP/IP-Konnektivität


**Ping** können Sie um die TCP/IP-Verbindung mit dem Gerät zu testen:

-   Öffnen Sie ein Eingabeaufforderungsfenster und geben: **Ping***W.X.Y.Z*, und Ersetzen Sie *W.X.Y.Z* durch die IP-Adresse des Geräts

Der Befehl sollte angegeben werden, dass die Pakete zurückgegeben wurden. Wenn dies nicht funktioniert, ist ein häufiges Problem zum Untersuchen der Konfiguration der Firewall auf dem PC.

## <a name="span-iddebugginginmmosspanspan-iddebugginginmmosspanspan-iddebugginginmmosspandebugging-in-mmos"></a><span id="Debugging_in_MMOS"></span><span id="debugging_in_mmos"></span><span id="DEBUGGING_IN_MMOS"></span>Debuggen in MMOS


Um Debugger-Unterstützung in MMOS zu aktivieren, müssen die Kommunikation und OS Einstellungen geändert werden.

### <a name="span-idenablingdebugsupportspanspan-idenablingdebugsupportspanspan-idenablingdebugsupportspanenabling-debug-support"></a><span id="Enabling_debug_support"></span><span id="enabling_debug_support"></span><span id="ENABLING_DEBUG_SUPPORT"></span>Aktivieren der Debug-Unterstützung

Um Debugunterstützung in MMOS zu aktivieren, geben Sie die folgende interne optionale Feature in der Datei MfgOEMInput.xml.

``` syntax
<Microsoft>
  ...
  <Feature>KDNETUSB_ON</Feature>
   ...
</Microsoft>
```

Dadurch wird das Bild MMOS die erforderlichen Pakete hinzugefügt. Weitere Informationen über das Arbeiten mit der Datei MfgOEMInput.xml finden Sie unter [MMOS image-Definition](mmos-image-definition.md).

### <a name="span-idenablingcommunicationsettingsspanspan-idenablingcommunicationsettingsspanspan-idenablingcommunicationsettingsspanenabling-communication-settings"></a><span id="Enabling_communication_settings"></span><span id="enabling_communication_settings"></span><span id="ENABLING_COMMUNICATION_SETTINGS"></span>Aktivieren für die Netzwerkkommunikation

Um das Betriebssystem zu aktivieren, müssen für die Netzwerkkommunikation geändert werden, nachdem das Bild aktualisiert wird.

### <a name="span-idestablishingthedebugconnectionspanspan-idestablishingthedebugconnectionspanspan-idestablishingthedebugconnectionspanestablishing-the-debug-connection"></a><span id="Establishing_the_debug_connection"></span><span id="establishing_the_debug_connection"></span><span id="ESTABLISHING_THE_DEBUG_CONNECTION"></span>Herstellen der Verbindung Debuggen

Verwenden Sie die Verbindung mit MMOS für das debugging WinDbg an die Schlüssel und der Port, die Sie zuvor mithilfe von BCDEdit konfiguriert.

``` syntax
windbg.exe -k net:Port=50000,Key=1.2.3.4
```

 

 





