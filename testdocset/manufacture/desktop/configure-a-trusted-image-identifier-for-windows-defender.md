---
author: Justinha
Description: "Konfigurieren Sie einen vertrauenswürdigen Bild Bezeichner für Windows Defender"
ms.assetid: b55f681f-94d7-4800-a927-ec186dc046e2
MSHAttr: PreferredLib:/library/windows/hardware
title: "Konfigurieren Sie einen vertrauenswürdigen Bild Bezeichner für Windows Defender"
ms.openlocfilehash: a8ef10dd1aff55c4243c85677aa18a9f62f77bb2
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="configure-a-trusted-image-identifier-for-windows-defender"></a>Konfigurieren Sie einen vertrauenswürdigen Bild Bezeichner für Windows Defender


Sie können die anfängliche Leistung des Computers für den Endbenutzer durch Hinzufügen einer vertrauenswürdigen Bild-ID zum Windows® Defender beschleunigen. Windows Defender ist eine Microsoft®-Anwendung, die dazu beitragen kann, zu verhindern, dass entfernen und Malware und Spyware isolieren.

Der Standardeinstellung führt Windows Defender eine Überprüfung der einzelnen Dateien auf dem Computer an, wenn der Computer die Datei zum ersten Mal zugreift. Dies ist ein Zugriffs-Scan genannt. Optimierung Mechanismen wie Zwischenspeichern verringern Sie unnötige Überprüfungen von Dateien, die bereits überprüft wurden. Wenn Windows Defender einen schnellen Scan oder einen vollständigen Scan (auch bekannt als Scans auf Anforderung) ausführt, wird die restlichen Dateien auf dem System als sicher gekennzeichnet.

**Hinweis**  
Wenn Sie bereits eine Reihe von Computern bereitgestellt haben und einem späteren Zeitpunkt feststellen, dass ein potenzielles Problem mit der Sicherheit des Bilds vorhanden ist, wenden Sie sich an Ihrem Tiefe Project Manager (PM) im Windows-Ökosystem Engagements Team. und geben Sie den eindeutigen Bezeichner des Bilds. Microsoft wird dieser eindeutigen Bezeichner in Windows Update hinzufügen. Nachdem ein Computer mit dieser eindeutige Kennung Updates von Windows Update erhält, führt Windows Defender Scans auf alle Dateien auf diesem Computer.

 

## <a name="span-idaddingatrustedimageidentifierspanspan-idaddingatrustedimageidentifierspanspan-idaddingatrustedimageidentifierspanadding-a-trusted-image-identifier"></a><span id="Adding_a_Trusted_Image_Identifier"></span><span id="adding_a_trusted_image_identifier"></span><span id="ADDING_A_TRUSTED_IMAGE_IDENTIFIER"></span>Hinzufügen einer vertrauenswürdigen Bild-ID


Für eine optimale Leistung wird empfohlen, dass Sie diese Einstellung hinzufügen, wenn Sie den Computer für die endgültige Bereitstellung vorzubereiten, nachdem Sie eine vollständige Überprüfung des endgültigen Bilds ausführen.

**So fügen Sie eine vertrauenswürdige Bild-ID hinzu**

1.  Erstellen eine Antwortdatei, die Sie mit Sysprep verwenden möchten, und fügen Sie die Sicherheit Schadsoftware Windows-Defender\\ `TrustedImageIdentifier` Einstellung. Weitere Informationen finden Sie unter [Verwendung von Antwortdateien mit Sysprep](use-answer-files-with-sysprep.md).

2.  Für den Wert der `TrustedImageIdentifier` festgelegt wird, geben Sie einen eindeutigen Bezeichner, beispielsweise eine GUID für das Bild.

3.  Installieren von Windows auf dem Referenzcomputer, und führen Sie alle Updates, die im Abschnitt "Häufige Sysprep-Szenarien" neben dem Thema [Übersicht über die Sysprep (System Preparation)](sysprep--system-preparation--overview.md) beschrieben werden.

4.  Ausführen einer Überprüfung des Bilds mithilfe von Windows Defender oder eine andere Scan Tool. Dies hilft sicherzustellen, dass das Bild sicher ist.

5.  Wenn Sie nach dem letzten Sysprep ausführen, verwenden Sie den Befehl Sysprep zusammen mit der/OOBE und / unbeaufsichtigten Optionen, wie folgt:

    ``` syntax
    Sysprep /oobe /shutdown /unattend:Unattend.xml
    ```

6.  Aufgaben Sie andere offline, wie beispielsweise offline – Wartung des Bilds. Erfassen Sie und liefern Sie den Computer dann an den Kunden wenden Sie das Abbild auf anderen Computern.

    Beim nächsten des Computers starten Windows identifiziert alle derzeit auf dem System-Dateien, und diese Dateien bei nachfolgenden Scans übersprungen.

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Übersicht über den Sysprep Upgradeprozess](sysprep-process-overview.md)

[Verwenden Sie Antwortdateien mit Sysprep](use-answer-files-with-sysprep.md#bkmk_1)

 

 






