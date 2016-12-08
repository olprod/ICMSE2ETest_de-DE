---
author: Justinha
Description: DISM Windows Edition zum Warten von Befehlszeilenoptionen
ms.assetid: e7faf4eb-7de8-49f7-9d42-caededf1b289
MSHAttr: PreferredLib:/library/windows/hardware
title: DISM Windows Edition zum Warten von Befehlszeilenoptionen
ms.openlocfilehash: ed1a129352f38303a6b8671cd56eeebf3d0f1efe
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="dism-windows-edition-servicing-command-line-options"></a>DISM Windows Edition zum Warten von Befehlszeilenoptionen


Die Windows® Edition – Wartung Befehle können Sie eine Version von Windows 8 auf eine höhere Version der gleichen Edition Familie ändern. Die Editionspakete für jede mögliche Zieledition sind in einem Windows-Abbild bereitgestellt. Dies wird als Bild Edition-Familie bezeichnet. Da die Ziel-Versionen bereitgestellt werden, können Sie ein einzelnes Bild service, und die Updates werden entsprechend auf jede Edition im Bild angewendet. Damit können Sie die Anzahl der Bilder reduzieren, die Sie verwalten möglicherweise muss, aber die Factory oder Endbenutzer Zeit, die im Durchgang Konfiguration **specialize** aufgewendet werden muss.

Offline ändert erfordern keinen Product Key. Wenn Sie eine höhere Version unter Verwendung von – Wartung offline ändern, können Sie den Product Key mit einer der folgenden Methoden hinzufügen:

-   Geben Sie den Product Key während der Out-of-Box-Experience (OOBE).

-   Verwenden Sie eine Antwortdatei, um den Product Key eingeben, der in der Phase der **specialize** Konfiguration.

-   Verwenden Sie Deployment Image Servicing und Management (DISM) und die Windows zum Warten von Editionen Befehlszeilenoption **/set-productkey/Set-ProductKey** nach dem Festlegen der Edition offline.

In diesem Thema:

[Befehlszeilensyntax](#bkmk-syntax)

[Einschränkungen](#bkmk-limitations)

## <a name="span-idbkmksyntaxspanspan-idbkmksyntaxspanspan-idbkmksyntaxspancommand-line-syntax"></a><span id="BKMK_Syntax"></span><span id="bkmk_syntax"></span><span id="BKMK_SYNTAX"></span>Befehlszeilensyntax


Die grundlegende Syntax zum Warten eines Windows-Abbilds mithilfe von DISM lautet:

**DISM.exe** {**/Image:**&lt;*Pfad\_auf\_Bild\_Verzeichnis*&gt; | **/Online**} \[ **Dism\_globale\_Optionen** \] {**– Wartung\_Option**} \[ &lt; *– Wartung\_Argument*&gt;\]

Sie können die folgenden Edition – Wartung Optionen auf offline Schwelle Liste Editionen oder zum Ändern eines Windows-Abbilds auf eine höhere Version verwenden:

**DISM.exe/Image:**&lt;*Pfad\_auf\_Bild\_Verzeichnis* &gt; {**/ Get-CurrentEdition** | **/Get-TargetEditions** | **/Optimize-Image /WIMBoot** | **/Set-Edition** | **/Set-ProductKey**:&lt;*Produkt\_Schlüssel*&gt;}

Die folgenden Optionen zum Warten von Editionen stehen für ein Windows-Betriebssystem ausgeführt wird:

**DISM.exe / Online** {**/ Get-CurrentEdition** | **/Get-TargetEditions** | **/Set-ProductKey**:&lt;*Produkt\_Schlüssel*&gt; | **/Set-Edition**:&lt;*Ziel\_Edition* &gt; {**/GetEula**:&lt; *Pfad*&gt; | **/AcceptEula** **/productkey/ProductKey**:&lt;Produkt\_Schlüssel&gt;}}

Die folgende Tabelle enthält eine Beschreibung für die wie jede Option Edition – Wartung verwendet werden kann. Diese Optionen sind nicht Groß-/Kleinschreibung beachtet.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th align="left">Option</th>
<th align="left">Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><p><strong>/ Get-Help</strong></p>
<p><strong>/?</strong></p></td>
<td align="left"><p>Wenn sofort nach einer Befehlszeilenoption zum Warten von Editionen verwendet, werden Informationen über die Option und die Argumente angezeigt. Zusätzliche Hilfethemen möglicherweise verfügbar, wenn ein Bild angegeben wird.</p>
<p>Beispiele:</p>
<p><strong>DISM /Image:C:\test\offline/Get-CurrentEdition /?</strong></p>
<p><strong>DISM / Online/Get-CurrentEdition /?</strong></p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>/ Get-CurrentEdition</strong></p></td>
<td align="left"><p>Zeigt die Version des angegebenen Bilds.</p>
<p>Beispiele:</p>
<p><strong>DISM /Image:C:\test\offline/Get-CurrentEdition</strong></p>
<p><strong>DISM / Online/Get-CurrentEdition</strong></p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>/ Get-TargetEditions</strong></p></td>
<td align="left"><p>Zeigt eine Liste der Windows-Editionen, denen ein Bild in geändert werden kann.</p>
<p>Beispiele:</p>
<p><strong>DISM /Image:C:\test\offline/Get-TargetEditions</strong></p>
<p><strong>DISM / Online/Get-TargetEditions</strong></p></td>
</tr>
<tr class="even">
<td align="left"><p><strong>/ Set-Edition</strong>:&lt;<em>Target_edition_ID</em> &gt; [{<strong>/GetEula</strong>:&lt;<em>Pfad</em> | <strong>/AcceptEula</strong> <strong>/productkey/ProductKey</strong>:&lt;<em>Product_key</em>&gt;}]</p></td>
<td align="left"><p>Verwenden der <strong>Option/Set-Edition</strong> ohne Argumente ein offline-Windows-Abbild auf eine höhere Edition zu ändern.</p>
<p>Um ein online Windows Server-Betriebssystem auf eine höhere Version zu ändern, müssen Sie die <strong>Option/Set-Edition</strong> mit den Argumenten <strong>/AcceptEula</strong> <strong>und/ProductKey</strong> verwenden.</p>
<div class="alert">
<strong>Wichtige</strong>  
<p>Sie sollten nicht die <strong>Option/Set-Edition</strong> eines Abbilds verwenden, die bereits in eine höhere Edition geändert wurde. Es wird empfohlen, dass Sie diese Option für die niedrigste Edition in der Produktfamilie Edition verfügbar verwenden.</p>
</div>
<div>
 
</div>
<p>Verwenden Sie <strong>/GetEula</strong> auf online Schwelle zum Kopieren des Endbenutzer-Lizenzvertrag auf einem angegebenen Pfad.</p>
<p>Das Argument <strong>/AcceptEula</strong> den Endbenutzer-Lizenzvertrag akzeptiert und ist erforderlich, um die Windows-Edition auf Schwelle online zu ändern.</p>
<p>Beispiel:</p>
<p><strong>DISM /Image:C:\test\offline/Set-Edition:</strong><em>&lt;Edition Name&gt;</em></p>
<p>Klicken Sie auf eine ausgeführte Betriebssystem Windows Server nur:</p>
<p><strong>DISM / online/Set-Edition:</strong><em>&lt;Edition Name&gt;</em> <strong>/GetEula:c:\eulapathDism / online/Set-Edition:</strong><em>&lt;Edition Name&gt;</em><strong>/AcceptEula /ProductKey:12345-67890-12345-67890-12345</strong></p>
<p>Dabei <em> &lt;Edition Name&gt; </em> ist die höhere Version, die Sie ändern möchten.</p></td>
</tr>
<tr class="odd">
<td align="left"><p><strong>/ Set-ProductKey</strong>:&lt;<em>ProductKey</em>&gt;</p></td>
<td align="left"><p>Die <strong>Option/Set-ProductKey</strong> kann nur verwendet werden, geben Sie den Product Key für die aktuelle Version in einem offline-Windows-Bild nach dem Ändern eines offline Windows-Abbilds auf eine höhere Version mit der <strong>Option/Set-Edition</strong> .</p>
<p>Beispiel:</p>
<p><strong>DISM /Image:C:\test\offline /Set-ProductKey:12345-67890-12345-67890-12345</strong></p></td>
</tr>
</tbody>
</table>

 

## <a name="span-idbkmklimitationsspanspan-idbkmklimitationsspanspan-idbkmklimitationsspanlimitations"></a><span id="BKMK_Limitations"></span><span id="bkmk_limitations"></span><span id="BKMK_LIMITATIONS"></span>Einschränkungen


-   Wenn Sie beim Festlegen der Edition von offline-Abbild nicht den Product Key eingeben, müssen Sie den Product Key eingeben, während OOBE oder verwenden eine Antwortdatei während des **specialize** Konfiguration Schritts den Product Key eingeben.

-   Sie können nicht Edition – Wartung Befehle für ein Abbild Windows Vorinstallation Environment (Windows PE) verwenden.

-   Um die Edition-spezifische Anpassungen zu gewährleisten, sollten Sie nach dem Upgrade Edition Edition-spezifischen Antwortdateien anwenden.

-   Wenn Sie die **Option/Set-Edition** für eine 64-Bit-Bild mit mehr als 30 Language Packs ausführen möchten, müssen Sie es auf einem 64-Bit-Computer ausführen. Andernfalls erhalten Sie möglicherweise eine Fehlermeldung unzureichendem Speicherplatz. Diese Einschränkung ist nur vorhanden, wenn Sie ein 64-Bit-Bild aus einem 32-Bit-Computer bearbeiten. Diese Einschränkung ist nicht vorhanden, wenn Sie diese Option auf einem Computer ausführen, die mit die Architektur des Bilds übereinstimmt.

-   Ein Windows-Bild kann nicht auf eine niedrigere Edition festgelegt werden. Die niedrigste Edition wird nicht angezeigt, wenn Sie die **Option/Get-TargetEditions** ausführen.

-   Sie sollten nicht die **Option/Set-Edition** eines Abbilds verwenden, die bereits auf eine höhere Edition geändert wurde.

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Was ist DISM?](what-is-dism.md)

[DISM Bild Management-Befehlszeilenoptionen](dism-image-management-command-line-options-s14.md)

[Deployment Image Servicing and Management (DISM) Befehlszeilenoptionen](deployment-image-servicing-and-management--dism--command-line-options.md)

[Ändern Sie das Windows-Abbild auf eine höhere Edition mithilfe von DISM](change-the-windows-image-to-a-higher-edition-using-dism.md)

 

 






