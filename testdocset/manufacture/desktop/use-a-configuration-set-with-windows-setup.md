---
author: Justinha
Description: Verwenden Sie einen Konfigurationssatz mit Windows-Setup
ms.assetid: 6dc2e7b3-f1fb-4d46-b248-1e96c912db38
MSHAttr: PreferredLib:/library/windows/hardware
title: Verwenden Sie einen Konfigurationssatz mit Windows-Setup
ms.openlocfilehash: 45398fde83bbe1d8e10f544f9e23cc35d1967aaf
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="use-a-configuration-set-with-windows-setup"></a>Verwenden Sie einen Konfigurationssatz mit Windows-Setup


Verwenden Sie einen Konfigurationssatz Applications, Treibern, Pakete, Skripts, Dateien und Ordner zu Windows während der Installation hinzufügen. Ein Konfigurationssatz ist eine portable Auflistung von Dateien und Ordnern, die auf einem USB Flash Drive (UFD) oder auf einer Netzwerkfreigabe einordnen.

Festlegen, um eine Konfiguration verwenden, benötigen Sie Folgendes:

-   Eine Konfiguration festgelegt. Weitere Informationen finden Sie unter [Erstellen einer Konfiguration festgelegt](https://msdn.microsoft.com/library/windows/hardware/dn915081).

-   Eine Windows-Produkt-DVD.

-   Einem Wechselmedium, beispielsweise ein USB-flash-Laufwerk (UFD), wenn Sie beabsichtigen, ohne ein Netzwerk zu installieren.

-   Eine startbare Windows PE-Medium, wenn Sie über ein Netzwerk installieren möchten. Weitere Informationen finden Sie unter [Windows PE: Erstellen startbaren USB-Laufwerk](winpe-create-usb-bootable-drive.md).

**Gewusst wie: Verwenden mit einer Windows-DVD Konfigurationssatz**

1.  Aktivieren Sie auf dem Computer.

2.  Legen Sie das Wechselmedium, die den Konfigurationssatz und die Windows-Produkt-DVD in den neuen Computer enthält ein.

    **Hinweis**  
    Wenn Sie ein USB-Flashlaufwerk verwenden, fügen Sie das Laufwerk direkt in am primären Satz der USB-Anschlüsse für den Computer an. Bei einem Desktopcomputer ist dies normalerweise Rückseite des Computers.

     

3.  Neustart des Computers durch Drücken von STRG + ALT + ENTF.

4.  Beim Neustart des Computers werden Sie möglicherweise aufgefordert, drücken eine beliebige Taste, um von der CD-ROM-Laufwerk zu starten. Drücken Sie eine beliebige Taste, und Windows Setup (**Setup.exe**) wird automatisch gestartet.

    Standardmäßig durchsucht Windows Setup alle Wechseldatenträger für eine Antwortdatei mit dem Namen **Autounattend.xml**. Autounattend.XML muss sich im Stammverzeichnis des das Wechselmedium befinden.

    Installation wird gestartet, und die Sie in die Antwortdatei konfigurierten Einstellungen angewendet werden.

**Gewusst wie: Verwenden Sie eine Konfiguration, die über ein Netzwerk festgelegt**

1.  Erstellen Sie zwei Ordner auf einer Netzwerkfreigabe Store der Produkt-DVD-Quelldateien und Konfiguration. Beispielsweise

    ``` syntax
    net use N: \\server\share
    md N:\WindowsDVD
    md N:\ConfigurationSets
    ```

2.  Kopieren Sie den Inhalt der Produkt-DVD auf die ** \\WindowsDVD** Ordner.

3.  Kopieren Sie die Konfiguration zum Festlegen der ** \\ConfigurationSets** Ordner.

4.  Starten Sie den Zielcomputer mithilfe einer startbare Windows PE-Medium.

    Informationen zum Erstellen von startbare Windows PE-Medium, finden Sie unter [Windows PE: Erstellen startbaren USB-Laufwerk](winpe-create-usb-bootable-drive.md).

5.  An einer Eingabeaufforderung in Windows PE Ihre Netzwerkfreigabe Zuordnen eines Netzlaufwerks. Beispielsweise

    ``` syntax
    net use N: \\server\share
    ```

6.  Führen Sie Windows Setup aus dem Netzwerk, und verweisen auf die Antwortdatei in den Konfigurationssatz. Beispielsweise

    ``` syntax
    N:\WindowsDVD\setup /unattend:N:\ConfigurationSets\autounattend.xml
    ```

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Technische Referenz zu Windows Setup](windows-setup-technical-reference.md)

[Hinzufügen eines benutzerdefinierten Befehls zu einer Antwortdatei](https://msdn.microsoft.com/library/windows/hardware/dn915058)

[Starten Sie von einer DVD](boot-from-a-dvd.md)

[Bereitstellen eines benutzerdefinierten Abbilds](deploy-a-custom-image.md)

[Boot Windows im Überwachungsmodus oder OOBE](boot-windows-to-audit-mode-or-oobe.md)

[Hinzufügen von Gerätetreibern Windows während der Installation von Windows](add-device-drivers-to-windows-during-windows-setup.md)

[Hinzufügen eines benutzerdefinierten Skripts zu Windows Setup](add-a-custom-script-to-windows-setup.md)

 

 






