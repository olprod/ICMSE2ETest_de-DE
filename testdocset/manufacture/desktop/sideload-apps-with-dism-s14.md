---
author: Justinha
Description: Sideload-Apps mit DISM
ms.assetid: ce95f34a-b9a4-4130-89ed-b7a7126fe21b
MSHAttr: PreferredLib:/library/windows/hardware
title: Sideload-Apps mit DISM
ms.openlocfilehash: 97e89dc47c6304aad9cfc32012155a628d8bdfd4
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="sideload-apps-with-dism"></a>Sideload-Apps mit DISM


Sie können mithilfe von PowerShell oder Abbildern Bereitstellung und Verwaltung (DISM) Sideload Line-of-Business (LOB) Windows apps auf einem Windows-10. Windows-apps enthalten:

-   Universelle Windows apps-Geräten: apps für Windows universellen Windows-app-Plattform-Gerätefamilie der universellen Zielgruppenadressierung aufgebaut.
-   Universelle Windows 8-apps: Windows-apps, die auf Windows abzielen 8.x.

Windows-apps sind in der Regel nur über die Windows Store verfügbar. Übermitteln von apps im Windows Store LOB Windows und außerhalb Ihres Unternehmens zur Verfügung stellen können. Sie können auch Entwickeln von apps für Windows für die Verwendung nur innerhalb Ihres Unternehmens und diese hinzufügen auf Windows-Geräte, die Sie über einen Prozess verwalten wir *Sideloading*aufrufen. Sideloaded-apps müssen nicht von zertifiziert oder über den Windows Store installiert sein.

Nachfolgend finden Sie die erforderlichen zu Sideload apps wissen:

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">So wird es gemacht?</th>
<th align="left">Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>[Sideloading Konzepte verstehen](#understandingconcepts)</p></td>
<td align="left"><p>Einführung in einige grundlegende Konzepte, die Sie benötigen, Sideloading apps kennen.</p></td>
</tr>
<tr class="even">
<td align="left"><p>[Konfigurieren von PCs für Sideloading Anforderungen](#sideloadingrequirements)</p></td>
<td align="left"><p>Zeigt die Anforderungen in Reihenfolge Sideload Apps auf verschiedenen Editionen von Windows-Geräten erfüllt sein. Wie Sie mithilfe von Gruppenrichtlinien zum Konfigurieren von Ihrem Unternehmen PCs für Sideloading apps enthält.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>[Konfigurieren von PCs für die Entwicklung von Windows Store-Apps](#bkmk-developerlicense)</p></td>
<td align="left"><p>Zeigt, wie konfigurieren Sie den PC, um eine Entwicklerlizenz für haben, die nicht abläuft. Der PC-Option kann verwendet werden, zum Entwickeln von Windows Store-apps oder Enterprise-apps, die Ihre Enterprise-Geräte hinzugefügt werden soll.</p></td>
</tr>
<tr class="even">
<td align="left"><p>[Hinzufügen von Apps](#addapps)</p></td>
<td align="left"><p>Zeigt, wie Sie Sideload-apps, die Sie entwickeln.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>[Hinzufügen von mehreren Sprachen für Apps](#bkmk-mulitlang)</p></td>
<td align="left"><p>Zeigt, wie Vorbereiten eines mehrsprachigen Abbilds, melden Sie sich das Bild, installieren Sie alle gewünschten app Ressource Packs (einschließlich Language) und dann Profil kopieren zum Erfassen des Abbilds verwenden.</p></td>
</tr>
<tr class="even">
<td align="left"><p>[Inventar-Apps](#inventoryapps)</p></td>
<td align="left"><p>Veranschaulicht das Auflisten der LOB-apps, die auf den Geräten in Ihrem Unternehmen oder ein offline-Windows-Abbild installiert.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>[Entfernen von Apps](#removeapps)</p></td>
<td align="left"><p>Zeigt, wie einzelne Instanzen für eine app entfernen oder die Bereitstellung einer app-Einstellung entfernen.</p></td>
</tr>
</tbody>
</table>

 

## <span id="UnderstandingConcepts"></span><span id="understandingconcepts"></span><span id="UNDERSTANDINGCONCEPTS"></span>


**Sideloading Konzepte verstehen**

Apps für Windows unterscheiden sich von Windows in ihren Entwurf und Benutzern desktopanwendungen mit ihnen interagieren können. Weitere Informationen zum Windows-apps finden Sie unter [Neuigkeiten von einer Windows Store-App?](http://go.microsoft.com/fwlink/?LinkId=264710).

Sie können nicht Sideload eine app, die aus dem Windows Store heruntergeladen wurde. Zum Installieren von Windows-apps, die nicht Teil der Business-Leitung sind, müssen Sie den Windows Store verwenden. Weitere Informationen finden Sie unter [Verwalten des Clientzugriffs an den Windows Store](http://go.microsoft.com/fwlink/?LinkId=264712).

LOB Windows apps, die von der Windows Store nicht signiert werden können Sideloaded oder an einem Computer im Unternehmen mithilfe von Skripts zur Laufzeit auf jeden Benutzer einzeln hinzugefügt. Sie können auch in einem Bild vom Unternehmen eingerichtet werden, damit die app in jede neue Benutzerprofil registriert wird, die auf dem PC erstellt wird. Die Anforderungen für die app pro Benutzer Sideload oder in das Bild sind identisch, jedoch Windows PowerShell-Cmdlets, die Sie verwenden, um das Hinzufügen, abrufen und Entfernen von den apps sind unterschiedlich. In diesem Thema werden die Schritte bei der beiden Methoden.

Bevor Sie Sideload Windows LOB-apps, die von der Windows Store nicht signiert werden können, müssen Sie zum Konfigurieren des PCs-Option finden Sie unter [Konfigurieren von PCs Sideloading bezüglich](#sideloadingrequirements).

**Beim Entwickeln LOB apps für Windows für Ihr Unternehmen**

LOB-Windows-apps, die von Windows Store nicht signiert sein müssen kryptografisch signiert werden. Die apps können nur auf einem Computer installiert werden, die das Signaturzertifikat vertraut.

Weitere Informationen zum Signieren einer app und die Verwendung von Zertifikaten finden Sie unter [App Tools zum Packen](http://go.microsoft.com/fwlink/?LinkId=242873).

Eine Entwicklerlizenz für können Sie jedoch apps hinzufügen, die bei der Entwicklung mit dem PC sind. Weitere Informationen zum Testen von apps, die bei der Entwicklung sind, finden Sie unter [erhalten Sie eine Lizenz für Entwickler](http://go.microsoft.com/fwlink/?LinkId=241313).

Sie können auch Gruppenrichtlinien verwenden, so konfigurieren Sie Ihre Domäne PCs, um eine Entwicklerlizenz für haben, die nicht zur Unterstützung der app-Entwicklung abläuft. Sobald die PCs konfiguriert sind, müssen Sie nicht eine Verbindung mit dem Internet abrufen oder erneuern eine Lizenz. Weitere Informationen finden Sie unter [Konfigurieren von PCs für Windows Store-Apps entwickeln](#bkmk-developerlicense) .

## <a name="span-idsideloadingrequirementsspanspan-idsideloadingrequirementsspanspan-idsideloadingrequirementsspanconfigure-pcs-for-sideloading-requirements"></a><span id="SideloadingRequirements"></span><span id="sideloadingrequirements"></span><span id="SIDELOADINGREQUIREMENTS"></span>Konfigurieren von PCs für Sideloading Anforderungen


Bis das Gerät alle der Sideloading Anforderungen erfüllt, werden app Kacheln im Menü Start in der unteren rechten Ecke, um anzugeben, dass ein Problem Ausführung die app verhindert wird eine "X" angezeigt.

In einigen Fällen enthält Teil diese Anforderungen mit einem Sideloading Product Key. Dieser Schlüssel enthält Nutzungsrechte erforderlich, um Windows 8 oder Windows 8.1 apps direkt auf Geräten bereitstellen, ohne dass Sie diese über die öffentliche Windows Store installieren.

Bevor Sie hinzufügen und Ausführen von Sideloaded Windows LOB-apps, die nicht von der Windows Store signiert werden können müssen Sie Ihr Gerät basierend auf Folgendes konfigurieren:

1.  Für diese Geräte, die mit einer Arbeitsgruppe verbunden sind, müssen Sie folgende Aktionen ausführen:

    -   Aktivieren Sie den Sideloading Product Key auf dem Gerät.

    -   Und aktivieren Sie die Einstellung für **alle zu installierenden Anwendungen vertrauenswürdigen zulassen** von Gruppenrichtlinien. Finden Sie unter [Verwenden von Gruppenrichtlinien zum Konfigurieren Ihres Unternehmens-PCs für Sideloading apps](#usegp).

    Dies gilt für:

    -   Windows 10 Enterprise
    -   Windows 8.1 Enterprise
    -   Windows 8 Enterprise
    -   Windows 8.1 Branche Enterprise eingebettet
    -   Windows 8.1 Pro Update

2.  Für diese Geräte, die Active Directory-Domäne zugeordnet werden soll, müssen Sie folgende Aktionen ausführen:

    -   Das Gerät zu einer Active Directory-Domäne hinzufügen.

    -   Und aktivieren Sie die Einstellung für **alle zu installierenden Anwendungen vertrauenswürdigen zulassen** von Gruppenrichtlinien. Finden Sie unter [Verwenden von Gruppenrichtlinien zum Konfigurieren von Ihrem Unternehmen PCs für apps Sideloading](#usegp).

    Dies gilt für:

    -   Windows-10 Enterprise
    -   Windows 8.1 Enterprise
    -   Windows 8 Enterprise
    -   Windows 8.1 Branche Enterprise eingebettet
    -   Windows 8.1 Pro Update
    -   Windows Server 2016 – Technische Vorschau
    -   Update für Windows Server 2012 R2
    -   WindowsServer 2012

3.  Für diese Geräte, die einen Sideloading Product Key, gibt an, ob das Gerät wird in die Domäne eingebundener oder ein Mitglied einer Arbeitsgruppe erforderlich ist, müssen Sie folgende Aktionen ausführen:

    -   Aktivieren Sie den Sideloading Product Key auf dem Gerät.

    -   Und aktivieren Sie die Einstellung für **alle zu installierenden Anwendungen vertrauenswürdigen zulassen** von Gruppenrichtlinien. Finden Sie unter [Verwenden von Gruppenrichtlinien zum Konfigurieren von Ihrem Unternehmen PCs für apps Sideloading](#usegp).

    Dies gilt für:

    -   Windows 10 Pro
    -   Windows 8.1 RT
    -   Windows 8.1 Pro
    -   Windows RT
    -   Windows 8 Pro
    -   Windows 8.1 Branche eingebettet Pro

4.  Für bestimmte Embedded Windows 8-Branche-Geräten nicht mehr benötigt einen Sideloading Product Key, ob das Gerät Mitglied einer Domäne ist, oder ein Mitglied einer Arbeitsgruppe. In diesem Fall müssen Sie folgende:

    -   Aktivieren Sie die gruppenrichtlinieneinstellung **alle zu installierenden Anwendungen vertrauenswürdigen zulassen** auf dem Gerät.

    Weitere Informationen zu Sideloading Embedded Windows 8-Branche finden Sie unter [Enterprise-Anleitung zur Installation von universellen Windows 8-apps auf Windows Embedded 8-Branche](http://go.microsoft.com/fwlink/?LinkId=391812).

    Dies gilt für:

    -   Windows 8.1 Branche Pro Update eingebettet
    -   Windows 8.1 Branche Enterprise Update eingebettet

<span id="UseGP"></span><span id="usegp"></span><span id="USEGP"></span>
**Verwenden von Gruppenrichtlinien zum Konfigurieren von Ihrem Unternehmen PCs für Sideloading apps**

1.  Öffnen Sie den Gruppenrichtlinienverwaltungs-Editor für eine Domäne – basierte Gruppenrichtlinienobjekt (GPO), dem Sie werden der gruppenrichtlinieneinstellung als unten, um den ausgewählten PCs angegeben anwenden werden.

    **Hinweis**  
    Die Schritte in diesem Verfahren wird davon ausgegangen, dass Sie die Grundlagen der Gruppenrichtlinien-Design und Vorgänge verstehen. Domäne zu verwalten – Gruppenrichtlinien basierend auf einem Windows 8.1-PC, Sie müssen der Gruppenrichtlinien-Verwaltungskonsole installieren, die mit dem [Remote Server Administration Tools für Windows 8.1](http://go.microsoft.com/fwlink/?LinkId=299896)installiert wird. Weitere Informationen zu Gruppenrichtlinien finden Sie unter [Gruppenrichtlinie für Anfänger](http://go.microsoft.com/fwlink/?LinkId=330723) und im [TechCenter für Gruppenrichtlinien](http://go.microsoft.com/fwlink/?LinkId=330564).

     

2.  Erweitern Sie **Computerkonfiguration**, **Administrative Vorlagen**, **Windows-Komponenten**, und klicken Sie dann **App-Paket-Bereitstellung**klicken.

3.  Doppelklicken Sie auf die Einstellung **Alle vertrauenswürdigen apps So installieren Sie zulassen** .

4.  Klicken Sie auf **aktiviert** und dann auf **OK**, klicken Sie im Fenster **Alle vertrauenswürdigen apps installieren können** .

Festlegen der Gruppenrichtlinien zum Zulassen vertrauenswürdiger Anwendungen aktualisiert den folgenden Registrierungsschlüssel: **HKEY\_LOKALE\_COMPUTER\\Software\\Richtlinien\\Microsoft\\Windows\\Appx\\AllowAllTrustedApps = 1**

**Um einen Sideloading Product Key zu aktivieren.**

1.  Öffnen Sie eine Eingabeaufforderung mit Administratorrechten aus, und geben Sie Folgendes ein, um den Product Key Sideloading hinzufügen:

    ``` syntax
    Slmgr /ipk <sideloading product key>
    ```

    Wobei * &lt;Sideloading Produktschlüssel&gt; * ist der Schlüssel 25 Ziffer Sideloading auf dem Computer zu aktivieren.

2.  Aktivieren Sie den Schlüssel Sideloading durch eingeben:

    ``` syntax
    slmgr /ato ec67814b-30e6-4a50-bf7b-d55daf729d1e
    ```

    **Hinweis**  
    Die Aktivierung GUID ist nicht identisch mit den Sideloading Product Key. Die Aktivierung GUID werden immer ec67814b-30e6-4a50-bf7b-d55daf729d1e.

     

Weitere Informationen zu Product Keys für Sideloading finden Sie unter [Windows 8 Lizenzierungshandbuch (engl.)](http://go.microsoft.com/fwlink/?LinkId=267899).

## <a name="span-idbkmkdeveloperlicensespanspan-idbkmkdeveloperlicensespanspan-idbkmkdeveloperlicensespanconfigure-pcs-for-developing-windows-apps"></a><span id="BKMK_DeveloperLicense"></span><span id="bkmk_developerlicense"></span><span id="BKMK_DEVELOPERLICENSE"></span>Konfigurieren von PCs für die Entwicklung von apps für Windows


Sie können Konfigurieren Ihrer PCs, um eine Entwicklerlizenz für haben, die nicht abläuft. Sobald die PCs konfiguriert sind, müssen Sie nicht eine Verbindung mit dem Internet abrufen oder erneuern eine Lizenz. Ihren Computer muss ein Mitglied einer Domäne sein und eine der folgenden Betriebssysteme ausgeführt werden:

-   Windows 10 Enterprise
-   Windows 8.1 Enterprise
-   Windows 8 Pro

**Hinweis**  
Um Sideloading auf Windows 8 Pro Gerät zu aktivieren, müssen Sie einen Produktschlüssel Aktivierung Sideloading verwenden. Weitere Informationen finden Sie unter [Konfigurieren von PCs bezüglich Sideloading](#sideloadingrequirements)

 

**So konfigurieren Sie Ihr Unternehmen PCs mit einer Entwicklerlizenz für**

1.  Öffnen Sie den Gruppenrichtlinienverwaltungs-Editor für eine Domäne – basierte Gruppenrichtlinienobjekt (GPO), dem Sie werden von gruppenrichtlinieneinstellungen, wie unten für den ausgewählten PCs angegeben anwenden werden.

    **Hinweis**  
    Die Schritte in diesem Verfahren wird davon ausgegangen, dass Sie die Grundlagen der Gruppenrichtlinien-Design und Vorgänge verstehen. Domäne zu verwalten – Gruppenrichtlinien basierend auf einem Windows 8.1-PC, Sie müssen der Gruppenrichtlinien-Verwaltungskonsole installieren, die mit dem [Remote Server Administration Tools für Windows 8.1](http://go.microsoft.com/fwlink/?LinkId=299896)installiert wird. Weitere Informationen zu Gruppenrichtlinien finden Sie unter [Gruppenrichtlinie für Anfänger](http://go.microsoft.com/fwlink/?LinkId=330723) und im [TechCenter für Gruppenrichtlinien](http://go.microsoft.com/fwlink/?LinkId=330564).

     

2.  Erweitern Sie **Computerkonfiguration**, **Administrative Vorlagen**, **Windows-Komponenten**, und klicken Sie dann **App-Paket-Bereitstellung**klicken.

3.  Doppelklicken Sie auf die Einstellung **Zulassen Entwicklung von apps für Windows ohne eine Entwicklerlizenz für installieren** .

4.  Klicken Sie im Fenster **Zulassen Entwicklung von apps für Windows ohne eine Entwicklerlizenz für installieren** klicken Sie auf **aktiviert** , und klicken Sie dann auf **OK**.

5.  Doppelklicken Sie auf die Einstellung **Alle vertrauenswürdigen apps installieren können** .

6.  Klicken Sie auf **aktiviert** und dann auf **OK**, klicken Sie im Fenster **Alle vertrauenswürdigen apps installieren können** .

Festlegen von Gruppenrichtlinien dazu, die Entwicklung von apps für Windows ohne Installation von einem Entwickler Lizenz Updates zulassen den folgenden Registrierungsschlüssel: **HKEY\_LOKALE\_COMPUTER\\Software\\Richtlinien\\Microsoft\\Windows\\Appx\\AllowDevelopmentWithoutDevLicense = 1**

Festlegen der Gruppenrichtlinien zum Zulassen vertrauenswürdiger Anwendungen aktualisiert den folgenden Registrierungsschlüssel: **HKEY\_LOKALE\_COMPUTER\\Software\\Richtlinien\\Microsoft\\Windows\\Appx\\AllowAllTrustedApps = 1**

## <a name="span-idaddappsspanspan-idaddappsspanspan-idaddappsspanadd-apps"></a><span id="AddApps"></span><span id="addapps"></span><span id="ADDAPPS"></span>Hinzufügen von Apps


Es gibt zwei Methoden, um apps hinzufügen. Ein Benutzer kann ein app-Paket hinzufügen, die die app nur, die diesem Benutzer zur Verfügung stellen wird. Oder Installation der app im Windows-Abbild, wodurch die app verfügbar auf jeden Benutzer des Windows-Abbilds bei der ersten Anmeldung oder bei der nächsten Anmeldung wird, wenn das Benutzerkonto bereits erstellt wird. In diesem zweiten Fall wird als ein app-Paket provisioning bezeichnet.

**Fügen Sie ein App-Paket hinzu**

Sie können ein app-Paket (.appx oder .appxbundle) für jeden Benutzer einzeln mithilfe des *add-Appxpackage* PowerShell-Cmdlets installieren. Es gibt keine Beschränkung der Anzahl der LOB-apps, die Sie für jeden Benutzer hinzufügen können.

**Hinzufügen einer LOB-app auf ein Benutzerkonto**

-   Fügen Sie an der Windows PowerShell-Eingabeaufforderung auf einem Computer mit Windows 8 oder Windows Server 2012 einem .appx (oder .appxbundle) Datei-Paket hinzu. Enthalten Sie erforderliche Abhängigkeit app Pakete, wenn Sie die app hinzufügen. Geben Sie beispielsweise Folgendes ein:

    ``` syntax
    add-appxpackage C:\app1.appx -DependencyPath C:\winjs.appx
    ```

    Weitere Informationen finden Sie unter [App-Installations-Cmdlets in Windows PowerShell](http://go.microsoft.com/fwlink/?LinkId=393919).

**Hinzufügen einer bereitgestellten LOB-app zu einem Windows-Abbild**

Apps, die im Windows-Abbild installiert sind heißen apps *bereitgestellt* . Bereitgestellte apps werden im Bild bereitgestellt und installiert sein, damit alle Benutzer des Windows-Abbilds bei der ersten Anmeldung oder bei der nächsten Anmeldung, geplant werden, wenn das Benutzerkonto bereits erstellt wird.

Sie können diese apps auf einem Windows-Abbild hinzufügen, wenn Sie vor der Bereitstellung des Abbilds mithilfe der DISM app-Bereitstellung Befehle im Überwachungsmodus starten. Weitere Informationen zum Überwachungsmodus finden Sie unter [Überwachen Modus Overview](audit-mode-overview.md).

Bereitgestellte apps sind spezifisch für den PC und werden mit dem Benutzer kein Roaming. Sie können nur 24 bereitgestellte apps in einem Bild installieren.

Klicken Sie auf einem Windows-Abbild, die bereits bereitgestellt wurde, sollten Sie stattdessen das Cmdlet Add-AppxPackage in PowerShell verwenden. Wenn Sie die DISM app-Bereitstellung von Befehlen auf einer bereitgestellten Windows-Abbild mit aktiven Benutzern verwenden, sollten Sie alle Benutzer aus dem Bild protokollieren, damit Sie sind der einzige Benutzer angemeldet, bevor Sie den Befehl ausführen.

**Hinweis**  
Unter Windows 8 zum Aktualisieren einer app bereitgestellten, müssen Sie zuerst entfernen die bereitgestellte app und klicken Sie dann die neue Version der app bereitstellen. Das Update wird dann das nächste Mal angewendet werden, die einzelnen Benutzer anmeldet.

Auf Windows 8.1 und höher müssen Sie nicht mehr die bereitgestellte app vor der Bereitstellung der neuen Version der bereitgestellten app zu entfernen.

 

**Fügen Sie einer bereitgestellten LOB-app auf einem Windows-Abbild**

-   Verwenden Sie das Deployment Image Servicing and Management (DISM) Befehlszeilenprogramm oder PowerShell-Cmdlets, die LOB-Anwendung ohne Windows Store-Lizenz hinzuzufügen. Geben Sie beispielsweise an einer Eingabeaufforderung mit erhöhten Rechten:

    ``` syntax
    DISM /Online /Add-ProvisionedAppxPackage /PackagePath:C:\App1.appx /SkipLicense
    ```

    Oder geben Sie an einer Windows PowerShell-Eingabeaufforderung ein:

    ``` syntax
    Add-AppxProvisionedPackage -Online -FolderPath C:\Appx -SkipLicense
    ```

    Weitere Informationen finden Sie unter [DISM App-Paket (.appx oder .appxbundle) Befehlszeilenoptionen zum Warten](dism-app-package--appx-or-appxbundle--servicing-command-line-options.md) oder [DISM-Cmdlets](http://go.microsoft.com/fwlink/?LinkId=393917). Informationen zu DISM unterstützte Plattformen finden Sie unter [DISM unterstützte Plattformen](dism-supported-platforms.md).

**Hinweis**  
Der Computer hat nicht Mitglied einer Domäne sein oder einen aktivierten Sideloading Product Key vor der Installation von bereitgestellte LOB-apps. Apps werden jedoch nicht ausgeführt, bis der Computer diese Sideloading Anforderung erfüllt. Weitere Informationen finden Sie unter [Anpassen der Startseite](customize-the-start-screen.md).

 

**Aktualisieren einer bereitgestellten LOB-app sobald es ist wurde ein Windows-Abbild hinzugefügt**

Unter Windows 8 zum Aktualisieren einer app bereitgestellten, müssen Sie zuerst entfernen die bereitgestellte app und klicken Sie dann die neue Version der app bereitstellen. Das Update wird dann das nächste Mal angewendet werden, die einzelnen Benutzer anmeldet.

Auf Windows 8.1 und neuere benötigen Sie zum Aktualisieren einer bereitgestellten-app, die app für jeden Benutzer zu aktualisieren, bei denen der Windows-Bild mit der app bereitgestellt angemeldet hat:

**Aktualisieren einer bereitgestellten LOB-app auf einem Windows-Abbild**

1.  Verwenden Sie die PowerShell, um die LOB-Anwendung ohne Windows Store-Lizenz zu aktualisieren. Dies muss erfolgen für jeden Benutzer, die auf den PC angemeldet hat das Windows-Abbild ausgeführt. Wenn Sie die ursprüngliche Version der app, 1.0.0.0, installiert haben muss, die nun auf Version 1.0.0.1 aktualisiert werden, klicken Sie dann auf eine PowerShell-Sitzung, geben Sie beispielsweise:

    ``` syntax
    Add-AppxPackage -Path App1_1.0.0.2 -DependencyPath C:\appx\WinJS.appx
    ```

    Wobei `c:\appx\WinJS.appx` ist der Pfad zum Paket Abhängigkeit.

2.  Nachdem Sie Ihre app aktualisiert haben, können Sie die Version der aktualisierten app überprüfen. Geben Sie von einer PowerShell-Sitzung Folgendes ein:

    ``` syntax
    Get-AppxPackage | Out-GridView
    ```

## <a name="span-idbkmkmulitlangspanspan-idbkmkmulitlangspanspan-idbkmkmulitlangspanadd-multiple-languages-for-apps"></a><span id="BKMK_MulitLang"></span><span id="bkmk_mulitlang"></span><span id="BKMK_MULITLANG"></span>Hinzufügen von mehreren Sprachen für Apps


Zur Vorbereitung einer mehrsprachigen Bild, melden Sie sich das Bild installieren Sie alle gewünschten app Ressource Packs (einschließlich Language) und dann verwenden Sie Profil kopieren zum Erfassen des Abbilds.

**Vorbereiten eines mehrsprachigen Abbilds für eine app**

1.  Erstellen Sie eine unattend.xml durch den folgenden Inhalt zu c:\\unattend.xml:

    ``` syntax
    <?xml version="1.0" encoding="utf-8"?>
    <unattend xmlns="urn:schemas-microsoft-com:unattend">
        <settings pass="specialize">
            <component name="Microsoft-Windows-Shell-Setup" processorArchitecture="x86" publicKeyToken="31bf3856ad364e35" language="neutral" versionScope="nonSxS" xmlns:wcm="http://schemas.microsoft.com/WMIConfig/2002/State" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
                <CopyProfile>true</CopyProfile>
                <RegisteredOrganization />
                <RegisteredOwner />
            </component>
        </settings>
        <cpi:offlineImage cpi:source="catalog:d:/desktop/x86 clgs/install_windows vista ultimate.clg" xmlns:cpi="urn:schemas-microsoft-com:cpi" />
    </unattend>
    ```

    **Hinweis**  
    Informationen zum Festlegen der Sprache und Installieren von Updates aus dem Windows Store finden Sie unter [Ändern der Sprache, die in apps verwendet](http://go.microsoft.com/fwlink/?LinkId=389195) .

     

2.  Melden Sie sich ein lokaler Administrator-Benutzerkonto von OOBE clean Bild.

    **Wichtige**  
    Beim Hinzufügen von einer bestimmten Sprache zu einer Windows-app auch sollten zum [Hinzufügen von Language Packs Windows](add-language-packs-to-windows.md) für dieselben Sprachen Sie wie bei der Windows-app.

     

3.  Liste der bevorzugten Sprachen des aktuellen Benutzers die gewünschten Sprachen hinzugefügt.

4.  **Installieren Sie app-Updates, die mithilfe einer Windows Store-Konto (Account MSA)**

    1.  Melden Sie sich über ein Konto MSA den Speicher.

        **Hinweis**  
        Store. Konvertieren Sie nicht das lokale Konto zu MSA.

        Wenn Sie nicht über ein Konto MSA verfügen, können Sie apps ohne einer Windows Store-Konto aktualisieren.

         

    2.  Suchen Sie nach Updates und installieren Sie neue Ressource Sprachpakete.

    3.  Abmelden bei Windows Store, und entfernen Sie das Konto MSA.

5.  Öffnen Sie ein Eingabeaufforderungsfenster mit erhöhten Rechten und Typ:

    ``` syntax
    Sysprep.exe /generalize /oobe /reboot /unattend:C:\unattend.xml
    ```

    Klicken Sie dann drücken Sie die EINGABETASTE.

6.  Starten Sie den PC OOBE sollte angezeigt werden. An dieser Stelle sollten alle Sprachen, die Sie vor dem Profil kopieren hinzugefügt haben vorhanden sein.

**Installieren von app-Updates ohne Verwendung einer Windows Store-Konto (Account MSA)**

1.  Nach dem Installieren der PC abgeschlossen ist, öffnen Sie eines Eingabeaufforderungsfenster mit erhöhten Rechten.

2.  Typ **Starten ms-Windows-Store: Updates**

3.  Die Seite Aktualisierungen von Windows Store, werden angezeigt. Die ausstehende Updates angezeigt sollte angezeigt werden.

4.  Tippen Sie auf **Installieren** , um die Updates zu installieren.

## <a name="span-idinventoryappsspanspan-idinventoryappsspanspan-idinventoryappsspaninventory-apps"></a><span id="InventoryApps"></span><span id="inventoryapps"></span><span id="INVENTORYAPPS"></span>Inventar-Apps


Sie können Auflisten der LOB-apps in auf offline- oder Onlinemodus Windows-Abbild installiert und erhalten weitere Informationen zu den Paketen.

**Liste LOB Apps pro Benutzerkonto**

1.  Sie können eine Liste der für ein bestimmtes Benutzerkonto auf dem Computer installierten apps Windows abrufen. Öffnen Sie PowerShell mit Administratorrechten die Pakete für einen Benutzer als dem aktuellen Benutzer aufgelistet. Geben Sie beispielsweise an der Eingabeaufforderung PowerShell:

    ``` syntax
    Get-AppxPackage -AllUsers
    ```

2.  Sie erhalten eine Liste der Pakete, die für einen bestimmten Benutzer installiert. Öffnen Sie PowerShell mit Administratorrechten die Pakete für einen Benutzer als dem aktuellen Benutzer aufgelistet. Geben Sie beispielsweise an der Eingabeaufforderung PowerShell:

    ``` syntax
    Get-AppxPackage -Name Package1 -User domain\username
    ```

3.  Sie können auch das Manifest der ein app-Paket (.appx) abzurufen, die umfasst Informationen wie die Paket-ID. Geben Sie beispielsweise an der Eingabeaufforderung PowerShell:

    ``` syntax
    Get-AppxPackageManifest -Package Package1
    ```

4.  Die Pipeline können Sie das Manifest für ein app-Paket (.appx) erhalten, wenn Sie den vollständigen Namen des Pakets nicht kennen. Geben Sie beispielsweise an der Eingabeaufforderung PowerShell:

    ``` syntax
    (Get-AppxPackage -Name "*WinJS*" | Get-AppxPackageManifest).package.applications.application.id
    ```

**Liste LOB-apps, die in einem Windows-Abbild bereitgestellt werden**

-   Sie erhalten eine Liste der Pakete, die in einem Windows-Abbild bereitgestellt werden, die für jeden neuen Benutzer mit Dism.exe oder PowerShell installiert wird. Beispielsweise an einem PowerShell-Eingabeaufforderung, geben Sie Folgendes ein:

    ``` syntax
    Get-AppxProvisionedPackage -Path c:\offline
    ```

    Oder geben Sie an einer Eingabeaufforderung ein:

    ``` syntax
    DISM.exe /Image:C:\test\offline /Get-ProvisionedAppxPackages
    ```

Weitere Informationen finden Sie unter [Inventory eines Bilds oder einer Komponente mithilfe von DISM dauern](take-inventory-of-an-image-or-component-using-dism.md).

## <a name="span-idremoveappsspanspan-idremoveappsspanspan-idremoveappsspanremove-apps"></a><span id="RemoveApps"></span><span id="removeapps"></span><span id="REMOVEAPPS"></span>Entfernen von Apps


Sie können einzelne Instanzen für eine app entfernen, oder Sie können die Bereitstellung einer app-Einstellung entfernen.

**Entfernen von LOB-apps pro Benutzerkonto**

-   Sie können eine einzelne app nur für den aktuellen Benutzer entfernen. Beispielsweise an einer Eingabeaufforderung, geben Sie Folgendes ein:

    ``` syntax
    Remove-AppxPackage Package1
    ```

**Entfernen von bereitgestellten LOB-apps in einem Windows-Abbild**

-   Wenn Sie eine bereitgestellte app entfernen, wird die app für neue Benutzerkonten nicht installiert. Für den aktuell angemeldeten Benutzer und anderen Benutzerkonten, die auf dem Computer aktiv sind, wird die app nicht von den Konten, entfernt werden. Die app müssen für die vorhandenen apps deinstalliert werden.

    Beispielsweise zum Entfernen einer bereitgestellten LOB-app, MyAppxPkg; aus einem Windows-Abbild an ein PowerShell-Eingabeaufforderung mit erhöhten Rechten, geben Sie Folgendes ein:

    ``` syntax
    Remove-AppxProvisionedPackage -Online -PackageName MyAppxPkg
    ```

    Oder geben Sie an einer Eingabeaufforderung ein:

    ``` syntax
    DISM.exe /Online /Remove-ProvisionedAppxPackage /PackageName:microsoft.app1_1.0.0.0_neutral_en-us_ac4zc6fex2zjp
    ```

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[App-Installations-Cmdlets in Windows PowerShell](http://go.microsoft.com/fwlink/?LinkId=243074)

[DISM App-Paket (.appx oder .appxbundle) Befehlszeilenoptionen zum Warten](dism-app-package--appx-or-appxbundle--servicing-command-line-options.md)

[Tools zum Packen App](http://go.microsoft.com/fwlink/?LinkId=242873)

[Modul AppX Cmdlets](http://go.microsoft.com/fwlink/?LinkId=393919)

[Ändern der Sprache in apps](http://go.microsoft.com/fwlink/?LinkId=389195)

[DISM Cmdlets](http://go.microsoft.com/fwlink/?LinkId=393917)

[DISM unterstützte Plattformen](dism-supported-platforms.md)

[Enterprise-Handbuch für die Installation von universellen Windows 8-apps auf Windows Embedded 8 aus dem Gesundheitswesen](http://go.microsoft.com/fwlink/?LinkId=391812)

[Erhalten Sie eine Entwicklerlizenz für](http://go.microsoft.com/fwlink/?LinkId=241313)

[Gruppenrichtlinien für Anfänger](http://go.microsoft.com/fwlink/?LinkId=330723)

[TechCenter für Gruppenrichtlinien](http://go.microsoft.com/fwlink/?LinkId=330564)

[Anpassen der Startseite](customize-the-start-screen.md)

[Verwalten des Clientzugriffs an den Windows Store](http://go.microsoft.com/fwlink/?LinkId=264712)

[Microsoft-Volumenlizenzierung](http://go.microsoft.com/fwlink/?LinkId=264711)

[Remoteserver-Verwaltungstools für Windows 8.1](http://go.microsoft.com/fwlink/?LinkId=299896)

[Was ist eine Windows Store-App?](http://go.microsoft.com/fwlink/?LinkId=264710)

[Windows 8-Lizenzierungshandbuch (engl.)](http://go.microsoft.com/fwlink/?LinkId=267899)

 

 






