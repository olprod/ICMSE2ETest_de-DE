---
author: kpacquer
Description: "Aktualisieren des Zeitservers auf IoT Core-Geräten"
MSHAttr: PreferredLib:/library
title: Aktualisieren Sie den Zeitserver
ms.openlocfilehash: 14fae14755309b1fcc6b2c32619f40ddeea50f6f
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="update-the-time-server"></a>Aktualisieren des Zeitservers

Synchronisieren Sie die Systemzeit zwischen IoT Core Geräten und eines Servers. Windows-10 standardmäßig Version 1607 http://time.windows.com mit den Windows-Zeitdienst. Sie können den Zeitserver ändern oder mehrere Zeitserver für hinzufügen, wenn Ihre Geräte auf unterschiedliche Netzwerk-Umgebungen sind.

##<a name="update-the-server-from-a-command-line-for-example-using-a-tool-like-putty"></a>Aktualisieren Sie den Server über die Befehlszeile (beispielsweise mit einem Tool wie kitten):

1.   Hinzufügen des Zeitservers mit einem Registrierungsschlüssel
     ``` syntax
     reg add HKLM\SYSTEM\CurrentControlSet\Services\w32time\Parameters /v NtpServer /t REG_SZ /d "time.windows.com,0x9 tick.usno.navy.mil,0x9 europe.pool.ntp.org,0x9 asia.pool.ntp.org,0x9" /f >nul 2>&1
     ```

2.  Beenden und erneutes Starten der Netzwerkdienste
    
    ``` syntax
    net stop
    net start
    ```

##<a name="update-the-server-in-an-iot-core-image"></a>Aktualisieren Sie den Server in einem IoT Core-Bild

1.  Erstellen einer Paketdefinitionsdatei, und fügen Sie es auf das Bild. Weitere Informationen finden Sie unter [Übung 1c: Hinzufügen einer Datei und eine Einstellung in der Registrierung zu einem Bild](add-a-registry-setting-to-an-image.md). Beispielskript: 

    ``` syntax
    <OSComponent> 
      <RegKeys> 
         <RegKey KeyName="$(hklm.software)\CurrentControlSet\Services\w32time\Parameters">
            <RegValue Name="NtpServer" Value="time.windows.com,0x9 tick.usno.navy.mil,0x9 europe.pool.ntp.org,0x9 asia.pool.ntp.org,0x9" Type="REG_SZ"/>
        </RegKey>
      </RegKeys>
    </OSComponent>
    ```