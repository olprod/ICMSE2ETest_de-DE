---
author: kpacquer
Description: Ein Update genehmigen
ms.assetid: 766c5961-4291-4547-a3a4-8ce98d3525e5
MSHAttr: PreferredLib:/library/windows/hardware
title: Ein Update genehmigen
ms.openlocfilehash: e32f78ce6ca1236c7a9ab29915c5eea27a761740
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="approve-an-update"></a>Ein Update genehmigen


Nachdem Sie ein Update übermittelt, die OEM und Mobile Operator (MO) genehmigen oder abzubrechen.

## <a name="span-idprerequisitestoapproveanupdatespanspan-idprerequisitestoapproveanupdatespanspan-idprerequisitestoapproveanupdatespanprerequisites-to-approve-an-update"></a><span id="Prerequisites_to_approve_an_update"></span><span id="prerequisites_to_approve_an_update"></span><span id="PREREQUISITES_TO_APPROVE_AN_UPDATE"></span>Erforderlichen Komponenten auf ein Update genehmigen


Finden Sie unter [Senden einer Aktualisierung](submit-an-update.md).

## <a name="span-idapprovingrfusspanspan-idapprovingrfusspanspan-idapprovingrfusspanapproving-rfus"></a><span id="Approving_RFUs"></span><span id="approving_rfus"></span><span id="APPROVING_RFUS"></span>Genehmigen von RFUs


Öffnen Sie ein Team Foundation Server (TFS) updateanforderung.

Open separate TFS Update Anfragen für Updates von Windows Phone 8.0 auf Windows Phone 8.1 und von Windows Phone 8.1 auf Windows Phone 8.1.

1.  Hinzufügen eines Titels, mit dem Format: "RFU Genehmigungen &lt;MOID oder mehreren&gt; &lt;DeviceName oder mehreren&gt;&lt;Apollo Blau oder Blau-Blau&gt;".

2.  Führen Sie den anderen TFS-Felder entsprechend.

3.  Fügen Sie eine Excel-Arbeitsmappe (XLS) mit der Liste der Geräte, einschließlich der folgenden Informationen:

    1.  RFU\#

    2.  RFU Ticket-Nummer (nicht Code signieren TKT)

    3.  PhoneManufacturerModelName (keine angezeigten oder Codename)

    4.  Telefon Mobilfunkbetreiber Name (MOId)

    5.  Quelle Firmwareversion

    6.  Ziel-Firmwareversion

    Beispiel:

    <table>
    <colgroup>
    <col width="12%" />
    <col width="12%" />
    <col width="12%" />
    <col width="12%" />
    <col width="12%" />
    <col width="12%" />
    <col width="12%" />
    <col width="12%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th align="left">RFU#</th>
    <th align="left">RFU Ticket-Nummer</th>
    <th align="left">PhoneManufacturerModelName</th>
    <th align="left">MOId</th>
    <th align="left">Quelle Firmware</th>
    <th align="left">Ziel Firmware</th>
    <th align="left">Version des Betriebssystems vor der Aktualisierung</th>
    <th align="left">Version des Betriebssystems nach Aktualisierung</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td align="left"><p>12345</p></td>
    <td align="left"><p>TKT-RFU-"BEMERKUNGEN"-ABC3DEF-2</p></td>
    <td align="left"><p>OEMDeviceName</p></td>
    <td align="left"><p>000-33</p></td>
    <td align="left"><p>1.2.3.4</p></td>
    <td align="left"><p>1.2.3.5</p></td>
    <td align="left"><p>10521</p></td>
    <td align="left"><p>12397</p></td>
    </tr>
    </tbody>
    </table>

     

## <a name="span-idapprovingadaptationkitakreleasesnofirmwareupdatespanspan-idapprovingadaptationkitakreleasesnofirmwareupdatespanspan-idapprovingadaptationkitakreleasesnofirmwareupdatespanapproving-adaptation-kit-ak-releases-no-firmware-update"></a><span id="Approving_Adaptation_Kit__AK__Releases__no_firmware_update_"></span><span id="approving_adaptation_kit__ak__releases__no_firmware_update_"></span><span id="APPROVING_ADAPTATION_KIT__AK__RELEASES__NO_FIRMWARE_UPDATE_"></span>Genehmigen von Anpassung Kit (AK)-Versionen (keine Firmware-Aktualisierung)


Die OEM und MO können einreichen und genehmigen die Version von einer Anpassung Kit (AK) ohne eine zugehörige RFU. Das reinen AK Bundle wird für die Vorschau vorbereitet werden, und freizugeben, wenn der OEM eine reine AK Anforderung durch Erfassung Tools übermittelt. Sobald genehmigt, kann das Update für die Produktion freigegeben. Wenn die Absicht, wechseln zur Produktion, sollten diese Updates für den Einzelhandel – Wartung Preview Ziel sein.

Öffnen einer TFS aktualisieren Anforderung:

1.  Geben Sie einen Titel mit dem Format: "Genehmigung für AK Version nur &lt;MOID oder mehreren&gt; &lt;DeviceName oder mehreren&gt;&lt;Version, z. B. GDR2QFE1&gt;".

2.  Führen Sie die anderen TFS-Felder entsprechend.

3.  Fügen Sie eine Excel-Arbeitsmappe (XLS) mit der Liste der Geräte, einschließlich der folgenden Informationen ein. Geben Sie eine Erläuterung zum Anfordern eines manuellen Abbruchs der Updates.

    1.  RFU\#. Beachten Sie, dass es sein, dass nur AK fasst eine TFS-ID zugeordnet.

        Nicht Mischen AK nur mit normaler RFU Genehmigungen in einer TFS-Anforderung, die sie separat verwaltet werden.

    2.  PhoneManufacturerModelName

    3.  Telefon Mobilfunkbetreiber Name (MOId)

    4.  Version des Betriebssystems vor der Aktualisierung

    5.  Version des Betriebssystems nach Aktualisierung

    Beispiel:

    <table>
    <colgroup>
    <col width="20%" />
    <col width="20%" />
    <col width="20%" />
    <col width="20%" />
    <col width="20%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th align="left">RFU#</th>
    <th align="left">PhoneManufacturerModelName</th>
    <th align="left">MOId</th>
    <th align="left">Version des Betriebssystems vor der Aktualisierung</th>
    <th align="left">Version des Betriebssystems nach Aktualisierung</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td align="left"><p>12345</p></td>
    <td align="left"><p>OEMDeviceName</p></td>
    <td align="left"><p>000-33</p></td>
    <td align="left"><p>10327</p></td>
    <td align="left"><p>10501</p></td>
    </tr>
    </tbody>
    </table>

     

## <a name="span-idcancellingrfusspanspan-idcancellingrfusspanspan-idcancellingrfusspancancelling-rfus"></a><span id="Cancelling_RFUs"></span><span id="cancelling_rfus"></span><span id="CANCELLING_RFUS"></span>RFUs wird abgebrochen.


In der Vorschau RFUs müssen nicht manuell abgebrochen werden, wenn mit demselben Baseline ersetzen. Automatische Erfassung wird die 'ersetzte' RFU für einzelne Best-Effort Abbrechen, wenn der neuen Firmware-Updates in der Vorschau live geschaltet wird. Verwenden Sie für das Abbrechen RFUs, die in der Vorschau aktiv sind das [Cmdlet Anforderung UpdateCancellation](request-updatecancellation.md). Für das Abbrechen RFUs, die bereits in der Produktion live sind:

Öffnen einer TFS aktualisieren Anforderung:

1.  Geben Sie einen Titel mit dem Format: "&lt;OEM&gt;für den Abbruch anfordern: &lt;DeviceName&gt;&lt;MOId&gt; &lt;Erklärung&gt;".

2.  Führen Sie die anderen TFS-Felder entsprechend.

3.  Fügen Sie eine Excel-Arbeitsmappe (XLS) mit der Liste der Geräte, einschließlich der folgenden Informationen ein. Geben Sie eine Erläuterung zum Anfordern eines manuellen Abbruchs der Updates.

    1.  RFU\#

    2.  PhoneManufacturerModelName

    3.  Telefon Mobilfunkbetreiber Name (MOId)

    4.  Version des Betriebssystems vor der Aktualisierung

    5.  Version des Betriebssystems nach Aktualisierung

    Beispiel:

    <table>
    <colgroup>
    <col width="20%" />
    <col width="20%" />
    <col width="20%" />
    <col width="20%" />
    <col width="20%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th align="left">RFU#</th>
    <th align="left">PhoneManufacturerModelName</th>
    <th align="left">MOId</th>
    <th align="left">Version des Betriebssystems vor der Aktualisierung</th>
    <th align="left">Version des Betriebssystems nach Aktualisierung</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td align="left"><p>765432</p></td>
    <td align="left"><p>OEMDeviceName</p></td>
    <td align="left"><p>000-33</p></td>
    <td align="left"><p>12345</p></td>
    <td align="left"><p>12346</p></td>
    </tr>
    </tbody>
    </table>

     

## <a name="span-idaftertheupdatespanspan-idaftertheupdatespanspan-idaftertheupdatespanafter-the-update"></a><span id="After_the_update"></span><span id="after_the_update"></span><span id="AFTER_THE_UPDATE"></span>Nach der Aktualisierung


Das Update wird auf Produktionsserver Update von Microsoft veröffentlicht, auf dem Telefone des Kunden das Update herunterladen und installieren es mit ihr Einverständnis.

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Update](index.md)

[Senden Sie ein update](submit-an-update.md)

 

 
