---
author: Justinha
Description: Windows-Setup-Edition-Konfiguration und Produkt-ID-Dateien (EI.cfg und PID.txt)
ms.assetid: 1c0f17a9-6a74-40af-8d0b-fc6d807a6616
MSHAttr: PreferredLib:/library/windows/hardware
title: Windows-Setup-Edition-Konfiguration und Produkt-ID-Dateien (EI.cfg und PID.txt)
ms.openlocfilehash: f52df3e504fec7e65d37abefa50dc46723d5e734
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="windows-setup-edition-configuration-and-product-id-files-eicfg-and-pidtxt"></a>Windows-Setup-Edition-Konfiguration und Produkt-ID-Dateien (EI.cfg und PID.txt)


Edition-Konfigurationsdatei (EI.cfg) und die Produkt-ID (PID.txt)-Datei sind optional Konfigurationsdateien, die Sie zum Angeben der Windows® Product Key und die Windows-Version während der Installation von Windows verwenden können. Diese Dateien können Sie die Eintragsseite Product Key-im Windows-Setup mithilfe einer Antwortdatei automatisieren. Wenn Sie eine Datei EI.cfg Volume License Media unterscheiden verwenden, jedoch nicht mit eine Datei PID.txt einschließen, erhält der Benutzer aufgefordert, einen Product Key mit Windows Setup fortfahren.

Sie können den Product Key in der Produkt-ID-Datei für mehrere Installationen wiederverwenden. Der Product Key in der Produkt-ID-Datei wird nur verwendet, um Windows zu installieren. Dieser Schlüssel wird nicht verwendet, um Windows zu aktivieren. Weitere Informationen finden Sie unter [Arbeiten mit Product Keys und Aktivierung](work-with-product-keys-and-activation-auth-phases.md).

## <a name="span-idusingeicfgandpidtxtspanspan-idusingeicfgandpidtxtspanspan-idusingeicfgandpidtxtspanusing-eicfg-and-pidtxt"></a><span id="Using_EI.cfg_and_PID.txt"></span><span id="using_ei.cfg_and_pid.txt"></span><span id="USING_EI.CFG_AND_PID.TXT"></span>Verwenden von EI.cfg und PID.txt


1.  Erstellen Sie diese Konfigurationsdateien in einem Text-Editor wie Editor.

2.  Speichern Sie die Dateien in die `\Sources` Ordner auf dem Installationsmedium. Windows-Setup wird diese Dateien automatisch während der Installation verwenden.

3.  Führen Sie Setup. Setup verwendet diese Dateien während der Konfiguration übergeben Sie Windows PE, sobald es gestartet wird.

**Hinweis**  
Eine Antwortdatei Vorrang vor diese Dateien. Wenn Sie eine Antwortdatei während der Installation verwenden, wird Windows Setup die Dateien EI.cfg und PID.txt ignoriert.

 

## <a name="span-ideicfgformatspanspan-ideicfgformatspaneicfg-format"></a><span id="ei.cfg_format"></span><span id="EI.CFG_FORMAT"></span>EI.cfg Format


Die Datei EI.cfg gibt die Werte für die Edition-ID, den DDE-Kanal und der Volumenlizenz.

Die Datei EI.cfg weist Folgendes Format:

``` syntax
[EditionID]
{Edition ID}
[Channel]
{Channel Type}
[VL]
{Volume License}
```

*{Edition-ID}* muss eine gültige Windows Edition ID, beispielsweise "Enterprise". Um die aktuelle EditionID erhalten möchten, verwenden Sie den Befehl **Dism /Get-ImageInfo** oder den Befehl **Dism/Get-CurrentEdition** . Weitere Informationen finden Sie unter [Nehmen Inventar eines Bilds oder einer Komponente mithilfe von DISM](take-inventory-of-an-image-or-component-using-dism.md) und [DISM Windows Edition – Wartung Command-Line Options](dism-windows-edition-servicing-command-line-options.md).

*{DDE-Kanaltyp}* muss "OEM" oder "Retail"

*{Volume License}* muss entweder 1 aus, wenn dies einer Volumenlizenz oder 0 ist, ist dies keiner Volumenlizenz. Beispiel:

``` syntax
[EditionID]
Enterprise
[Channel]
OEM
[VL]
0
```

## <a name="span-idpidtxtformatspanspan-idpidtxtformatspanpidtxt-format"></a><span id="pid.txt_format"></span><span id="PID.TXT_FORMAT"></span>PID.txt Format


Die PID.txt-Datei enthält den Product Key für die Edition von Windows, die Sie installieren.

Die Datei PID.txt weist Folgendes Format:

``` syntax
[PID]
Value=XXXXX-XXXXX-XXXXX-XXXXX-XXXXX
```

Dabei ist *XXXXX-XXXXX-XXXXX-XXXXX-XXXXX* den Product Key.

## <a name="span-idtroubleshootingspanspan-idtroubleshootingspanspan-idtroubleshootingspantroubleshooting"></a><span id="Troubleshooting"></span><span id="troubleshooting"></span><span id="TROUBLESHOOTING"></span>Problembehandlung


**"Der eingegebene Product Key stimmt nicht überein Windows Bilder für die Installation verfügbar. Geben Sie einen anderen Product Key."**: Möglicherweise müssen Sie eine eigene Version des Windows herunterladen. OEM-Versionen stehen nur für OEMs und Volume-Lizenzen sind nur für MSDN-Abonnenten verfügbar.

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Arbeiten Sie mit Product Keys und Aktivierung](work-with-product-keys-and-activation-auth-phases.md)

[Windows Setup-Befehlszeilenoptionen](windows-setup-command-line-options.md)

[Windows-Setup-Status](windows-setup-states.md)

 

 






