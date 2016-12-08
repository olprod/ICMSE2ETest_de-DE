---
author: Justinha
Description: ".NET Framework 3.5 Bereitstellungsfehler und Lösungsschritte"
ms.assetid: 1320d926-3ff7-4deb-b7b8-17190028dd97
MSHAttr: PreferredLib:/library/windows/hardware
title: ".NET Framework 3.5 Bereitstellungsfehler und Lösungsschritte"
ms.openlocfilehash: 57c5bcaa7afbfc249000af5cc8db3df71363ae94
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="net-framework-35-deployment-errors-and-resolution-steps"></a>.NET Framework 3.5 Bereitstellungsfehler und Lösungsschritte


In diesem Thema werden häufig auftretende Fehler auftreten können, wenn Sie Features bei Bedarf verwenden, aktivieren oder Bereitstellen von .NET Framework 3.5 und empfohlene Schritte aus, um die Probleme zu beheben.

**Tabelle 1-Funktionen zu Fehlercodes bei Bedarf**

<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Fehlercode</th>
<th align="left">Name</th>
<th align="left">Beschreibung</th>
<th align="left">Lösungsschritte</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>0x800F081F</p></td>
<td align="left"><p>CBS_E_SOURCE_MISSING</p></td>
<td align="left"><p>Die Quelldateien konnte nicht gefunden werden. Verwenden Sie die Option <strong>Quelle</strong> , um den Speicherort der Dateien anzugeben, die erforderlich sind, um das Feature wiederherstellen. Weitere Informationen zum Angeben eines Speicherorts Quelle finden Sie unter [Konfigurieren einer Windows-Quelle reparieren](http://go.microsoft.com/fwlink/?LinkId=243077).</p></td>
<td align="left"><p>Stellen Sie sicher, dass die angegebene Quelle die erforderlichen Dateien verfügt. Das Argument Source sollten <strong>\sources\sxs Ordner</strong> auf dem Installationsmedium oder die Windows-Ordner für eine bereitgestellte Abbild (beispielsweise <strong>c:\mount\windows</strong> für ein Bild zu <strong>c:\mount</strong>bereitgestellt) verweisen.</p></td>
</tr>
<tr class="even">
<td align="left"><p>0x800F0906</p></td>
<td align="left"><p>CBS_E_DOWNLOAD_FAILURE</p></td>
<td align="left"><p>Die Quelldateien konnte nicht heruntergeladen werden. Verwenden Sie die Option <strong>Quelle</strong> , um den Speicherort der Dateien anzugeben, die erforderlich sind, um das Feature wiederherzustellen. Weitere Informationen zum Angeben eines Speicherorts Quelle finden Sie unter [Konfigurieren einer Windows-Quelle reparieren](http://go.microsoft.com/fwlink/?LinkId=243077).</p>
<p>Windows konnte nicht mit dem Internet zum Herunterladen der erforderlichen Dateien verbinden. Stellen Sie sicher, dass das System mit dem Internet verbunden ist, und klicken Sie auf <strong>Wiederholen</strong>.</p></td>
<td align="left"><p>Stellen Sie sicher, dass die Computer oder Server mit Windows Update verbunden ist und Sie so Navigieren zur <strong>http://update.microsoft.com</strong>können. Wenn WSUS zum Verwalten von Updates für diesen Computer verwendet wird, stellen Sie sicher, dass der Gruppenrichtlinieneinstellung <strong>Kontakt Windows Update direkt an die zum Herunterladen von Inhalten der Reparatur anstelle von Windows Server Update Services (WSUS)</strong> aktiviert ist.</p></td>
</tr>
<tr class="odd">
<td align="left"><p>0x800F0907</p></td>
<td align="left"><p>CBS_E_GROUPPOLICY_DISALLOWED</p></td>
<td align="left"><p>DISM ist fehlgeschlagen. Es wurde kein Vorgang ausgeführt. Weitere Informationen finden Sie unter <strong>%WINDIR%\logs\DISM\dism.log</strong>die Protokolldatei.</p>
<p>Aufgrund von Netzwerkrichtlinien konnte nicht mit dem Internet zum Herunterladen von Dateien erforderlich, um den angeforderten Änderungen auszuführen Windows verbinden.</p></td>
<td align="left"><p>Fordern Sie die gruppenrichtlinieneinstellung <strong>Angeben von Einstellungen für optionale Komponenteninstallation und Komponente reparieren</strong> einer direkten Unterstützung mit Ihrem Netzwerkadministrator erhalten haben.</p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Bereitstellungsaspekte für Microsoft .NET Framework 3.5](microsoft-net-framework-35-deployment-considerations.md)

 

 






