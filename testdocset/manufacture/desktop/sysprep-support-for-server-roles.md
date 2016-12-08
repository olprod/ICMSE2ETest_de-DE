---
author: Justinha
Description: "Sysprep-Unterstützung für Serverrollen"
ms.assetid: ed484189-a2a7-423e-b191-202559efa81f
MSHAttr: PreferredLib:/library/windows/hardware
title: "Sysprep-Unterstützung für Serverrollen"
ms.openlocfilehash: 046db4b422e7e0a39a086772294160d4cefe1fa1
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="sysprep-support-for-server-roles"></a>Sysprep-Unterstützung für Serverrollen


Viele allgemeine Serverrollen unterstützen das Systemvorbereitungstool (Sysprep). Jedoch, wenn Sie den Befehl **Sysprep** zusammen mit der Option **/ verallgemeinern** für eine Installation von einem Server ausführen, und Sie eine nicht unterstützte Serverrolle verwenden, diese Rollen funktionieren möglicherweise nicht nach Abschluss des Vorgangs Imaging und Bereitstellung. Aus diesem Grund müssen Sie aktivieren und konfigurieren alle Serverrollen, die keine Sysprep unterstützen, nachdem Sie die Imaging und Bereitstellungsprozess ausgeführt haben.

In der folgenden Tabelle werden die Serverrollen aufgelistet und gibt an, ob die Rollen Sysprep unterstützt.

<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Serverrolle</th>
<th align="left">Sysprep-Unterstützung in Windows Server 2008</th>
<th align="left">Sysprep-Unterstützung in Windows Server 2008 R2</th>
<th align="left">Sysprep-Unterstützung in Windows Server® 2012</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>Active Directory-Zertifikatdienste (AD CS)</p></td>
<td align="left"><p>Nein</p></td>
<td align="left"><p>Nein</p></td>
<td align="left"><p>Nein</p></td>
</tr>
<tr class="even">
<td align="left"><p>Active Directory-Domänendienste (AD DS)</p></td>
<td align="left"><p>Nein</p></td>
<td align="left"><p>Nein</p></td>
<td align="left"><p>Nein</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Active Directory-Verbunddienste (AD FS)</p></td>
<td align="left"><p>Nein</p></td>
<td align="left"><p>Nein</p></td>
<td align="left"><p>Nein</p></td>
</tr>
<tr class="even">
<td align="left"><p>Active Directory Lightweight Directory Services (AD LDS)</p></td>
<td align="left"><p>Nein</p></td>
<td align="left"><p>Nein</p></td>
<td align="left"><p>Nein</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Active Directory-Rechteverwaltungsdienste (AD RMS)</p></td>
<td align="left"><p>Nein</p></td>
<td align="left"><p>Nein</p></td>
<td align="left"><p>Nein</p></td>
</tr>
<tr class="even">
<td align="left"><p>Anwendungsserver</p></td>
<td align="left"><p>Ja</p></td>
<td align="left"><p>Ja</p></td>
<td align="left"><p>Ja</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Server für Dynamic Host Configuration Protocol (DHCP)</p></td>
<td align="left"><p>Ja</p></td>
<td align="left"><p>Nein</p></td>
<td align="left"><p>Nein</p></td>
</tr>
<tr class="even">
<td align="left"><p>Server für Domain Name System (DNS)</p></td>
<td align="left"><p>Nicht zutreffend</p></td>
<td align="left"><p>Nicht zutreffend</p></td>
<td align="left"><p>Nicht zutreffend</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Faxserver</p></td>
<td align="left"><p>Nein</p></td>
<td align="left"><p>Nein</p></td>
<td align="left"><p>Nein</p></td>
</tr>
<tr class="even">
<td align="left"><p>Datei- und Speicher-Services</p></td>
<td align="left"><p>Nein</p></td>
<td align="left"><p>Ja</p></td>
<td align="left"><p>Ja</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Hyper-V™</p></td>
<td align="left"><p>Nicht zutreffend</p></td>
<td align="left"><p>Ja</p>
<p>Für ein virtuelles Netzwerk auf Hyper-V™ unterstützt nicht. Sie müssen alle virtuelle Netzwerke vor dem Ausführen des Tools Sysprep löschen.</p></td>
<td align="left"><p>Ja</p>
<p>Für ein virtuelles Netzwerk auf Hyper-V™ unterstützt nicht. Sie müssen alle virtuelle Netzwerke vor dem Ausführen des Tools Sysprep löschen.</p></td>
</tr>
<tr class="even">
<td align="left"><p>Netzwerkrichtlinie und Zugriffsdienste (NPAS) ¹</p></td>
<td align="left"><p>Nein</p></td>
<td align="left"><p>Nein</p></td>
<td align="left"><p>Nein</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Netzwerkrichtlinien-Routing und RAS-Services</p></td>
<td align="left"><p>Ja</p></td>
<td align="left"><p>Nicht zutreffend</p></td>
<td align="left"><p>Nicht zutreffend</p></td>
</tr>
<tr class="even">
<td align="left"><p>Drucken und Dokumentieren Sie Services (Druckdienste) ²</p></td>
<td align="left"><p>Nein</p></td>
<td align="left"><p>Ja</p></td>
<td align="left"><p>Ja</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Remotedesktopdienste ³</p></td>
<td align="left"><p>Ja</p></td>
<td align="left"><p>Ja</p></td>
<td align="left"><p>Ja</p></td>
</tr>
<tr class="even">
<td align="left"><p>Streaming Media-Services (als Download verfügbar)</p></td>
<td align="left"><p>Nicht zutreffend</p></td>
<td align="left"><p>Nicht zutreffend</p></td>
<td align="left"><p>Nicht zutreffend</p></td>
</tr>
<tr class="odd">
<td align="left"><p>UDDI-Dienste ⁴</p></td>
<td align="left"><p>Nein</p></td>
<td align="left"><p>Nicht zutreffend</p></td>
<td align="left"><p>Nicht zutreffend</p></td>
</tr>
<tr class="even">
<td align="left"><p>Volume Activation Services ⁵</p></td>
<td align="left"><p>Nicht zutreffend</p></td>
<td align="left"><p>Nicht zutreffend</p></td>
<td align="left"><p>Nicht zutreffend</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Webserver (Internet Information Services)</p></td>
<td align="left"><p>Ja</p>
<p>Mit verschlüsselten Anmeldeinformationen in der Datei "applicationHost.config" unterstützt nicht.</p></td>
<td align="left"><p>Ja</p>
<p>Mit verschlüsselten Anmeldeinformationen in der Datei "applicationHost.config" unterstützt nicht.</p></td>
<td align="left"><p>Ja</p>
<p>Mit verschlüsselten Anmeldeinformationen in der Datei "applicationHost.config" unterstützt nicht.</p></td>
</tr>
<tr class="even">
<td align="left"><p>Windows-Bereitstellungsdienste</p></td>
<td align="left"><p>Nein</p></td>
<td align="left"><p>Nein</p></td>
<td align="left"><p>Ja</p>
<p>Nicht unterstützt, wenn Windows-Bereitstellungsdienste initialisiert wird. ⁶</p></td>
</tr>
<tr class="odd">
<td align="left"><p>Windows Server Update Services (WSUS)</p></td>
<td align="left"><p>Nein</p></td>
<td align="left"><p>Nein</p></td>
<td align="left"><p>Nein</p></td>
</tr>
</tbody>
</table>

 

⁽¹⁾ NPAS enthält (Health Registration Authority, HRA), Network Policy Server (NPS) und Host Credential Authorization-Protokoll (HCAP).

⁽²⁾ in Windows Server 2008 R2, Druckdienste wurde umbenannte drucken und Document Services.

⁽³⁾ in Windows Server 2008 R2, Terminal Services umbenannt wurde Remote Desktop Services, die auch bekannt als Remotedesktop-Sitzungshost wird.

⁽⁴⁾ UDDI-Diensten wurde nicht in Windows Server 2008 R2 enthalten.

⁽⁵⁾ Volume Activation Services ist neu in Windows Server 2012.

Sie müssen den Server initialisieren, der die Windows-Bereitstellungsdienste Funktion vor dem Ausführen von Sysprep installiert ⁽⁶⁾. Sie können einen Server mithilfe des Befehls **Wdsutil /uninitialize-server** initialisieren.

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Übersicht über die Sysprep (Vorbereitung System)](sysprep--system-preparation--overview.md)

[Übersicht über den Sysprep Upgradeprozess](sysprep-process-overview.md)

[Sysprep-Befehlszeilenoptionen](sysprep-command-line-options.md)

[Sysprep (verallgemeinern) einer Windows-installation](sysprep--generalize--a-windows-installation.md)

 

 






