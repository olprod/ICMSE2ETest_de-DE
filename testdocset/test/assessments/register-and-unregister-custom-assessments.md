---
title: Registrieren des benutzerdefinierten Bewertung
description: Registrieren des benutzerdefinierten Bewertung
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: b86c6b47-08d0-441a-ba92-3a7be65ebe16
ms.prod: W10
ms.mktglfcycl: plan
ms.sitesec: msdn
ms.openlocfilehash: 61074264ffadfd99ba25fce37cf3cda7a51da44a
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="register-custom-assessments"></a>Registrieren des benutzerdefinierten Bewertung


Die Analysen, die zusammen mit dem Windows Assessment Toolkit installiert werden werden automatisch registriert, wenn sie installiert sind. Allerdings bei der Entwicklung Ihrer eigenen Einschätzung mithilfe der Bewertung Platform-APIs müssen Sie manuell die Bewertung registrieren, damit sie in der Windows-Assessment-Konsole und die Windows-Assessment-Services - Client (Windows ASC) angezeigt werden.

**Hinweis**  
Eine Reihe von öffentlichen APIs können zum Erstellen und Erweitern von Analysen, die für die Bewertung Plattform kompatibel sind. Weitere Informationen finden Sie unter [MSDN: Assessment Execution Engine](http://go.microsoft.com/fwlink/?LinkId=236367).

 

Sie können die folgenden Befehlszeilenoptionen verwenden, registrieren oder Aufheben der Registrierung individuelle Beurteilung.

So registrieren Sie eine Bewertung

**Regasmt***&lt;Pfad\_des\_Bewertung&gt;*

Eine Bewertung aufgehoben werden:

**Regasmt/u***&lt;Pfad der Bewertung&gt;*

**Hinweis**  
**Regasmt.exe** wird standardmäßig installiert, wenn das Windows Assessment Toolkit installiert ist. In der Standardeinstellung **Regasmt.exe** installiert ist, unter ProgramFiles%\\Windows Kits\\10\\Assessment and Deployment Kit\\Windows Assessment Toolkit\\X86. Es ist keine X64 Version.

Sie benötigen Administratorrechte, um diese Befehle auszuführen.

 

**Registrieren Sie eine Bewertung**

1.  Geben Sie an einer Eingabeaufforderung mit erhöhten Rechten Folgendes aus:

    ``` syntax
    regasmt C:\MyAssessments\example.asmtmanifest.asmtx
    ```

    Wobei C:\\MyAssessments\\example.asmtmanifest ist der Pfad der Bewertung. Relative Pfade werden unterstützt.

2.  Zum Registrieren von mehr als eine Bewertung Auflisten der Bewertungsfragen. Beispiel:

    ``` syntax
    regasmt C:\MyAssessments\example.asmtmanifest.asmtx example2.asmtmanifest.asmtx
    ```

**Aufheben der Registrierung eine Bewertung**

-   Geben Sie an einer Eingabeaufforderung mit erhöhten Rechten Folgendes aus:

    ``` syntax
    regasmt /u C:\MyAssessments\example.asmtmanifest.asmtx
    ```

    **Hinweis**  
    Aufheben der Registrierung einer Bewertung wird nicht deinstalliert. Sie können mehrere Bewertung zu einem Zeitpunkt aufgehoben.

     

## <a name="related-topics"></a>Verwandte Themen


[Windows-Assessment-Toolkit](windows-assessment-toolkit-technical-reference.md)

[Häufige Szenarien Windows Assessment-Konsole](windows-assessment-console-common-scenarios.md)

 

 







