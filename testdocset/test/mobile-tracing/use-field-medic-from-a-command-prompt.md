---
title: "Feld Sanitäter über eine Befehlszeile verwenden"
description: "Feld Sanitäter über eine Befehlszeile verwenden"
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: CFC32516-C794-40D8-BFED-6C607E85E6CD
ms.openlocfilehash: 248222851a3e1e5c1f40a7cf66a4c68b33ac3d01
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="use-field-medic-from-a-command-prompt"></a>Feld Sanitäter über eine Befehlszeile verwenden


Wenn Feld Sanitäter über eine Befehlszeile (Feld Sanitäter Helper) verwenden möchten, können Sie das Paket Microsoft.Phone.Test.Tools.FieldMedicHelper installieren.

Sie müssen IUTool verwenden, auf dem Gerät zu installieren.

``` syntax
%WPDKCONTENTROOT%\tools\bin\i386\IUTool.exe -p Microsoft.Phone.Test.Tools.FieldMedicHelper.spkg
```

Feld Sanitäter Helper besteht aus den folgenden Modulen:

-   **FileMedicHelper.exe** das Feld Sanitäter Helper ausführbare Datei

-   **DiagnosticSvcRPC.dll** Diagnosedienst RPC-wrapper

-   **DICData.dll** Gerät Informationsbibliothek

## <a name="syntax"></a>Syntax


``` syntax
FieldMedicHelper parameter <options>
```

## <a name="parameters"></a>Parameter


<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Parameter</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Netlog-</p></td>
<td><p><strong>Starten Sie</strong>  - NETLOG starten Protokollierung.</p>
<p><strong>Beenden Sie</strong>  - Protokollierung beenden NETLOG.</p></td>
</tr>
<tr class="even">
<td><p>-qxdm</p></td>
<td><p><strong>Starten Sie</strong>  - QXDM starten Protokollierung.</p>
<p><strong>Beenden Sie</strong>  - Protokollierung beenden QXDM.</p></td>
</tr>
<tr class="odd">
<td><p>Etw-</p></td>
<td><p><strong>Starten Sie</strong>  - Protokollierung ETW starten.</p>
<p><strong>Beenden Sie</strong>  - beenden ETW-Protokollierung.</p></td>
</tr>
<tr class="even">
<td><p>-userdump</p></td>
<td><p>Starten Sie einen Dump Benutzermodus.</p></td>
</tr>
<tr class="odd">
<td><p>-kerneldump</p></td>
<td><p>Starten Sie ein Abbild im Kernelmodus.</p></td>
</tr>
</tbody>
</table>

 

## <a name="options"></a>Options


Die folgenden Optionen können mit den Parametern verwendet werden:

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Option</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>-Modus</p></td>
<td><p>Dump-Modus für Benutzermodus oder Kernelmodus Modus Dump.</p>
<p><strong>Standardmäßige</strong> verwendet den Standardmodus Dump.</p>
<p><strong>Vollständige</strong> verwenden Sie den vollständigen Dump-Modus.</p></td>
</tr>
<tr class="even">
<td><p>-Speicher</p></td>
<td><p>Der Speichertyp. Dies kann nicht mit dem Pfadparameter verwendet werden.</p>
<p><strong>SD</strong> SD-Karte für die Speicherung verwenden.</p>
<p><strong>Telefon</strong> Se das Gerät zum Speicher. Standardwert.</p></td>
</tr>
<tr class="odd">
<td><p>-Pfad</p></td>
<td><p>Der MTP Pfad zum Speichern des Berichts. Dies kann nicht mit dem Parameter Speicher verwendet werden.</p></td>
</tr>
<tr class="even">
<td><p>Timeoutduration-</p></td>
<td><p>Die Dauer, die die Protokollierung in Stunden ausgeführt werden soll. Standardmäßig ist dies 48 Stunden.</p>
<div class="alert">
<strong>Vorsicht</strong>  
<p>Wenn Sie einen Wert größer als 48 Stunden angeben, stellen Sie sicher, dass Sie genügend Puffer Reservierung und Speicher verfügen.</p>
</div>
<div>
 
</div></td>
</tr>
<tr class="odd">
<td><p>-dmcinputpath</p></td>
<td><p>Pfad der benutzerdefinierten DMCFile für QXDM.</p></td>
</tr>
<tr class="even">
<td><p>-custominputpath</p></td>
<td><p>Pfad zur XML-Datei für benutzerdefinierte Profile für ETW oder QXDM.</p></td>
</tr>
</tbody>
</table>

 

## <a name="examples"></a>Beispiele


Verwenden Sie in den folgenden Beispielen Feld Sanitäter Helper über eine Befehlszeile ausführen. Sie sollten Cmd-Gerät in TShell verwenden, um diese Befehle von einem PC auszuführen.

Starten Sie QXDM, speichern Sie das Protokoll auf die SD-Karte und nach 48 Stunden zu beenden:

``` syntax
FieldMedicHelper -qxdm start -storage SD -timeoutduration 48
```

QXDM zu starten, und speichern Sie das Protokoll in C:\\Daten\\testen\\Bin\\Protokolle:

``` syntax
FieldMedicHelper -qxdm start -path C:\data\test\bin\logs
```

Beenden Sie QXDM:

``` syntax
FieldMediaHelper -qxdm stop
```

Starten Sie Netlog, speichern Sie das Protokoll auf SD-Karte und nach 10 Stunden zu beenden:

``` syntax
FieldMedicHelper -netlog start -storage SD -timeoutduration 10
```

Starten Sie Netlog mit Standardwerten:

``` syntax
FieldMedicHelper -netlog start
```

Starten Sie Netlog, speichern Sie das Protokoll auf dem Gerät und nach 10 Stunden beenden:

``` syntax
FieldMedicHelper -netlog start -timeoutduration 10
```

oder

``` syntax
FieldMedicHelper -netlog start -storage Phone -timeoutduration 10
```

Beenden Sie Netlog:

``` syntax
FieldMedicHelper -netlog stop
```

So starten Sie ETW mit einen benutzerdefinierten Anbieter:

``` syntax
FieldMedicHelper -etw start -custominputpath c:\data\test\bin\FieldMedicHelper\mycustomprofile.xml
```

So starten Sie QXDM mit einen benutzerdefinierten Anbieter in einem benutzerdefinierten Pfad:

``` syntax
FieldMedicHelper -qxdm start -dmcinputpath c:\data\test\MyDMCFile.dmc -custominputpath c:\data\test\mycustomprofile.xml -path C:\data\test\bin\logs
```

 

 






