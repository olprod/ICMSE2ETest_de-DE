---
author: Justinha
Description: Bereitstellen von .NET Framework 3.5 mithilfe von Richtlinienfeature Gruppe bei Bedarf-Einstellung
ms.assetid: 764f765d-cdc1-4638-9035-64f3d6a43b8d
MSHAttr: PreferredLib:/library/windows/hardware
title: Bereitstellen von .NET Framework 3.5 mithilfe von Richtlinienfeature Gruppe bei Bedarf-Einstellung
ms.openlocfilehash: c66f0a5062baba4983f5a017d24914e2c51f7276
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="deploy-net-framework-35-by-using-group-policy-feature-on-demand-setting"></a>Bereitstellen von .NET Framework 3.5 mithilfe von Richtlinienfeature Gruppe bei Bedarf-Einstellung


Für Umgebungen für die Active Directory und Gruppenrichtlinien verwenden, enthält das Feature bei Bedarf (Departements) Richtlinie festlegen Option Flexibilität bei der Installation von .NET Framework 3.5. Diese Einstellung Group Policy gibt den Netzwerkadressen verwenden, um die optionale Features zu aktivieren, die ihre Nutzlast Dateien entfernt wurden, und Reparieren Vorgänge von Updatefehlern Installationen für Dateidaten und Registrierung an. Wenn Sie diese Einstellung nicht konfigurieren oder deaktivieren oder wenn die erforderlichen Dateien an den Standorten gefunden werden können, die in diese Einstellung angegeben sind, werden die Dateien von Windows Update heruntergeladen (sofern dies durch die Richtlinieneinstellungen für den Computer zulässig ist). Die Einstellung **Einstellungen für die optionale Komponenteninstallation und Komponente reparieren angeben** Gruppenrichtlinie befindet sich unter **Computerkonfiguration\\Administrative Vorlagen\\System** in Gruppenrichtlinien-Editor.

## <a name="span-idrequirementsspanspan-idrequirementsspanspan-idrequirementsspanrequirements"></a><span id="Requirements"></span><span id="requirements"></span><span id="REQUIREMENTS"></span>Anforderungen


-   Active Directory-Domäne-Infrastruktur, Windows 8 und Windows Server® 2012 unterstützt

-   Durch den Zugriffsrechte zum Konfigurieren von Gruppenrichtlinien

-   Zielcomputern benötigen Zugriff auf das Netzwerk und Rechte zu alternativen Quellen oder eine Internet-Verbindung verwenden, um mithilfe von Windows Update

![Festlegen von Funktionen bei Bedarf Gruppenrichtlinien](images/gpsettingfeaturesondemand.jpg)

**Abbildung 1 "Gruppenrichtlinien"-Einstellung für Features bei Bedarf und Feature Store Reparatur**

Wenn diese Richtlinie aktiviert ist, kann ein Speicherort im Netzwerk (beispielsweise eines Dateiservers) für beide Reparieren des Dateispeichers Feature und zum Aktivieren von Features, die ihre Nutzlast entfernt haben angegeben werden. Der **Alternative Quelldateipfad** können zeigen Sie auf eine ** \\Quellen\\Sxs** Ordner oder eine WIM mit Windows-Abbilddatei (WIM): Präfix. Der Vorteil einer WIM-Datei ist, dass es mit Updates verwaltet werden können, und geben Sie eine aktuelle Quelle reparieren und .NET Framework 3.5-Binärdateien. Die Reparatur kann WIM anders als die anfängliche WIM-Datei sein, die für die Installation verwendet wird. Der Benutzer oder Prozess, der versucht, ein optionales Windows-Feature aktivieren erfordert entsprechende Zugriffsrechte für Dateifreigaben und/oder WIM-Dateien.

Wenn Sie **nie Versuch Nutzlast von Windows Update herunterladen**auswählen, wird Windows Update nicht während eines Vorgangs Installation oder Reparatur kontaktiert.

Wenn Sie **Kontakt Windows Update direkt reparieren Inhalt anstelle von Windows Server Update Services (WSUS) herunterladen**, jeder Versuch, Hinzufügen von Features (beispielsweise .NET Framework 3.5) oder reparieren den Feature-Dateispeicher auswählen wird Windows Update Herunterladen von Dateien verwendet. Ziel-Computern für diese Option Internet-und Windows Update erforderlich.

**Hinweis**  
Windows Server Update Services (WSUS) wird als Quelle für Departements oder ein Feature File Store Reparatur nicht unterstützt.

Windows 8 und Windows Server 2012 wird WSUS als Quelle für die Installation von Features (beispielsweise Hinzufügen von .NET Framework 3.5 Feature-Dateien) oder Feature Dateivorgänge Store Reparatur nicht unterstützt. WSUS-Hauptszenarien zählen zentralisierte Verwaltung und Patch-Management-Automatisierung, die kann Administratoren die Verteilung von Updates zu verwalten, die über Microsoft Update an Computer in ihrem Netzwerk veröffentlicht werden. Departements und Feature-Datei Store Reparatur basieren auf Download der einzelnen Dateien oder reparieren Vorgänge ausführen Update. Angenommen, wenn eine einzelne Datei beschädigt werden, wird dann nur diese Datei (die so klein wie ein paar Kilobyte werden kann) aus der Quelle reparieren heruntergeladen. Vollständige oder express-Dateien können WSUS Wartungsvorgängen Update ausführen. Diese Dateien sind jedoch nicht kompatibel mit Departements oder ein Feature Datei Store reparieren.

 

Wenn ein alternative Quellpfad zum Reparieren von Bildern verwendet wird, berücksichtigen Sie die folgenden Richtlinien:

-   **Wartung von updates**

    Halten Sie einer beliebigen Quelle reparieren mit den neuesten Dienstupdates. Wenn Sie ein Bild aus einer WIM-Datei für Departements verwenden, können Sie das Tool Abbildern Bereitstellung und Verwaltung (DISM) auf das Bild-service verwenden. Weitere Informationen finden Sie unter [Mount und ein Bild mithilfe von DISM ändern](http://go.microsoft.com/fwlink/p/?linkid=329973). Wenn Sie eine online Windows-Installation, die gemeinsam genutzt wird in Ihrem lokalen Netzwerk als Bild reparieren verwenden, stellen Sie sicher, dass der Computer Zugriff auf Windows Update ist.

-   **Mehrsprachige Abbilder**

    Sie müssen alle relevanten Sprachpakete bei Ihrer Reparatur Quelldateien für die Gebietsschemas enthalten, die das Bild unterstützt. Wenn Sie ein Feature, ohne alle Lokalisierungsdateien, die für dieses Feature die Windows-Installation erforderlich sind wiederherstellen, schlägt die Installation fehl. Sie können weitere Sprachpakete installieren, nachdem ein Feature wiederhergestellt wird.

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Bereitstellungsaspekte für Microsoft .NET Framework 3.5](microsoft-net-framework-35-deployment-considerations.md)

 

 






