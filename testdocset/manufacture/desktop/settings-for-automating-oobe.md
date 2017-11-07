---
author: Justinha
Description: "Einstellungen für die Automatisierung von OOBE"
ms.assetid: b7d71c0e-6e91-4409-a184-d76d744b386b
MSHAttr: PreferredLib:/library/windows/hardware
title: "Einstellungen für die Automatisierung von OOBE"
ms.openlocfilehash: 8cb684b15d627fc0f931d59b0d00a878689631b0
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="settings-for-automating-oobe"></a>Einstellungen für die Automatisierung von OOBE


Sie können einige oder alle Seiten der Benutzeroberfläche (UI) verhindert in Windows Out of Box-Experience (OOBE).

## <a name="span-idautomatingoobespanspan-idautomatingoobespanspan-idautomatingoobespanautomating-oobe"></a><span id="Automating_OOBE"></span><span id="automating_oobe"></span><span id="AUTOMATING_OOBE"></span>Automatisieren der OOBE


Wenn OOBE automatisieren möchten, Ihre Antwortdatei fügen Sie die folgenden Einstellungen hinzu:

<table>
<colgroup>
<col width="25%" />
<col width="25%" />
<col width="25%" />
<col width="25%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Einstellung</th>
<th align="left">Konfigurationsphasen</th>
<th align="left">Beschreibung</th>
<th align="left">Gilt für</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p>Microsoft-Windows-International-Core-Einstellungen: [InputLocale](http://go.microsoft.com/fwlink/?LinkId=224435), [SystemLocale](http://go.microsoft.com/fwlink/?LinkId=224436), [UILanguage](http://go.microsoft.com/fwlink/?LinkId=224437)und [UserLocale](http://go.microsoft.com/fwlink/?LinkId=224438).</p></td>
<td align="left"><p><strong>oobeSystem</strong></p></td>
<td align="left"><p>Gibt die Standardwerte regionsspezifische der Windows-Installation.</p></td>
<td align="left"><p>Windows-10 für desktop-Editionen (Start, Pro, Enterprise und Bildungseinrichtungen) und Windows Server 2016 – Technische Vorschau </p></td>
</tr>
<tr class="even">
<td align="left"><p>Microsoft-Windows-Shell-Setup | [ComputerName](http://go.microsoft.com/fwlink/p/?linkid=224440)</p></td>
<td align="left"><p><strong>specialize</strong></p></td>
<td align="left"><p>Gibt den Namen des Computers auf die Windows-Installation anwenden.</p>
<p>ComputerName auf ein Sternchen (*) festgelegt ist, oder eine leere Zeichenfolge ist, wird ein zufälliger Computername generiert.</p></td>
<td align="left"><p>Windows-10 für desktop-Editionen und Windows Server 2016 – Technische Vorschau </p></td>
</tr>
<tr class="odd">
<td align="left"><p>Microsoft-Windows-Shell-Setup | [UserAccounts](http://go.microsoft.com/fwlink/?LinkId=224439): Fügen Sie ein Konto und ein Kennwort.</p></td>
<td align="left"><p><strong>oobeSystem</strong></p></td>
<td align="left"><p>Gibt die Benutzerkonten auf die Windows-Installation erstellen.</p>
<p>Das Konto kann ein Benutzerkonto, das standardmäßige Administratorkonto oder ein Domänenkonto sein.</p>
<p>Obwohl Sie kein Kennwort eingeben müssen, kann das Kennwort leer sein. Geben ein Kennwort in Windows SIM, mit der rechten Maustaste <strong>Wert</strong>ein, und wählen <strong>Leere Zeichenfolge schreiben</strong>.</p></td>
<td align="left"><p>Windows-10 für desktop-Editionen und Windows Server 2016 – Technische Vorschau </p></td>
</tr>
<tr class="even">
<td align="left"><p>Microsoft-Windows-Shell-Setup | OOBE | ([HideEULAPage](http://go.microsoft.com/fwlink/?LinkId=224445), [HideOEMRegistrationScreen](http://go.microsoft.com/fwlink/?LinkId=252784), [HideOnlineAccountScreens](http://go.microsoft.com/fwlink/?LinkId=252785)und [HideWirelessSetupInOOBE](http://go.microsoft.com/fwlink/?LinkId=252786))</p></td>
<td align="left"><p><strong>oobeSystem</strong></p></td>
<td align="left"><p>Gibt das Verhalten von einigen OOBE Bildschirmen.</p></td>
<td align="left"><p>Windows-10 für desktop-Editionen und Windows Server 2016 – Technische Vorschau </p></td>
</tr>
<tr class="odd">
<td align="left"><p>Microsoft-Windows-Shell-Setup | OOBE | [HideLocalAccountScreen](http://go.microsoft.com/fwlink/?LinkId=252787)</p></td>
<td align="left"><p><strong>oobeSystem</strong></p></td>
<td align="left"><p>Gibt an, ob Endbenutzer der Administrator Kennwortbildschirm festlegen müssen, die während der OOBE angezeigt wird.</p></td>
<td align="left"><p>Windows Server 2016 – Technische Vorschau nur</p></td>
</tr>
<tr class="even">
<td align="left"><p>Microsoft-Windows-Shell-Setup | OOBE | [ProtectYourPC](http://go.microsoft.com/fwlink/?LinkId=224441)</p></td>
<td align="left"><p><strong>oobeSystem</strong></p></td>
<td align="left"><p>Gibt an, ob das Gerät mit Express-Einstellungen, wie Daten an Microsoft gesendet, Navigate Windows- und apps Lokalisierung des Benutzers anfordern und einschalten Schutz vor böswilligen Webinhalte konfiguriert ist.</p></td>
<td align="left"><p>Windows-10 für desktop-Editionen und Windows Server 2016 – Technische Vorschau </p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Automatisieren der Windows-Setup](automate-windows-setup.md)

 

 






