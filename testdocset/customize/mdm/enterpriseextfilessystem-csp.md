---
title: EnterpriseExtFileSystem CSP
description: EnterpriseExtFileSystem CSP
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: F773AD72-A800-481A-A9E2-899BA56F4426
ms.openlocfilehash: 83f586543e6a923a9367f6bff9f49d28e740486a
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="enterpriseextfilesystem-csp"></a>EnterpriseExtFileSystem CSP


Im EnterpriseExtFileSystem Konfiguration-Dienstanbieter (CSP) kann IT-Administratoren hinzufügen, Abrufen oder Ändern von Dateien im Dateisystem über den Dienst Mobile Device Management (MDM). Beispielsweise können Sie mit der eine XML-Bereitstellungsdatei oder eine neue Sperre Bildschirm Hintergrund Abbilddatei zu einem Gerät über den Dienst MDM push dieses Dienstanbieters Konfiguration und Protokolle auch vom Gerät in der Enterprise-Umgebung abrufen.

> **Hinweis**  EnterpriseExtFileSystem CSP ist nur in Windows 10 Mobile unterstützt.

 

Inhalt der Datei werden direkt in der Nachricht SyncML eingebettet, damit es besteht ein Grenzwert zu der Größe der Datei, die vom Gerät abgerufen werden kann. Die Standardgrenze liegt bei 0 x 100000 (1 MB). Sie können diese Grenze konfigurieren, indem Sie mit dem folgenden Registrierungsschlüssel: **Software\\Microsoft\\Provisioning\\Kryptografiedienstanbieter\\.\\ Hersteller\\MSFT\\EnterpriseExtFileSystem\\MaxFileReadSize**.

Das folgende Diagramm zeigt den EnterpriseExtFileSystem Konfigurationsdienstanbieter im Strukturformat von Open Mobile Allianz (OMA) Gerät Management (DM) verwendet.

![Enterpriseextfilesystem csp](images/provisioning-csp-enterpriseextfilesystem.png)

Die folgende Liste beschreibt die Merkmale und Parameter.

<a href="" id="--vendor-msft-enterpriseextfilesystem"></a>**./Vendor/MSFT/EnterpriseExtFileSystem**  
<p style="margin-left: 25px">Der für den EnterpriseExtFileSystem Konfigurationsdienstanbieter Stammknoten. Unterstützte Vorgänge sind Add und abrufen.</p>

<a href="" id="persistent"></a>**Persistent**  
<p style="margin-left: 25px">EnterpriseExtFileSystem CSP ermöglicht es Unternehmen, lesen, schreiben, löschen und Auflisten von Dateien in diesem Ordner. Wenn eine app Daten zum permanenten Ordner schreibt, greift diese Daten aus der EnterpriseExtFileSystem auf\\Persistent Knoten. Dateien in den Ordner Persistent geschrieben über normale Power Zyklen weiterhin auftritt.</p>

> **Wichtige**  Es besteht ein Grenzwert der Menge der Daten, die beibehalten werden können, die variiert je nach wie viel Speicherplatz auf eine Partition verfügbar ist. Diese Daten Cap Betrag (das beibehalten werden kann) variiert je nach Hersteller.

 

> **Hinweis**   Wenn der IT-Administrator eine **DoWipePersistProvisionedData** -Aktion mit [RemoteWipe CSP](remotewipe-csp.md)ausgelöst wird, werden Elemente im Ordner Persistent gespeichert über Remotegerätzurücksetzung beibehalten und wiederhergestellt, wenn das Gerät erneut gestartet wird. Die Inhalte werden nicht beibehalten, wenn eine Aktion **DoWipe** ausgelöst wird.

 

<a href="" id="nonpersistent"></a>**Denen nicht beständige**  
<p style="margin-left: 25px">EnterpriseExtFileSystem CSP ermöglicht es Unternehmen, lesen, schreiben, löschen und Auflisten von Dateien in diesem Ordner. Wenn eine app schreibt Daten in den Ordner nicht Persistent es greift auf die Daten aus der EnterpriseExtFileSystem\\nicht beständige Knoten. Dateien in den Ordner nicht beständige geschrieben werden über normale Power Zyklen beibehalten.</p>  

<p style="margin-left: 25px">Wenn das Gerät bereinigt ist, werden im Ordner nicht beständige gespeicherten Daten gelöscht.</p>

<a href="" id="oemprofile"></a>**OemProfile**  
<p style="margin-left: 25px">In Windows 10, Version 1511 hinzugefügt. EnterpriseExtFileSystem CSP ermöglicht es Unternehmen, die ein OEM-Profil auf dem Gerät wie ein Barcode Scanner Profil bereitstellen, und klicken Sie dann von der OEM Barcode-Scanner-Treiber verwendet werden können. Die Datei befindet sich in der \\Daten\\Shareddata\\oem\\öffentlichen\\Profil\\ Ordner des Geräts.</p>

<a href="" id="directory"></a>***Verzeichnis***  
<p style="margin-left: 25px">Der Name eines Verzeichnisses im Gerätedateisystem. Jeder Knoten *Directory* kann Verzeichnisse und Dateien als untergeordnete Knoten besitzen.</p>

<p style="margin-left: 25px">Verwenden Sie den Befehl hinzufügen, um ein neues Verzeichnis zu erstellen. Sie können sie ein neues Verzeichnis unter einem Dateisystem-Root hinzuzufügen.</p>

<p style="margin-left: 25px">Verwenden Sie den Befehl Get, um die Liste der Namen der untergeordneten Knoten unter *Verzeichnis*zurückzugeben.</p>

<p style="margin-left: 25px">Verwenden Sie den Befehl Get mit ?List = Struct rekursiv Rückgabe aller untergeordneten Knotennamen, einschließlich der Namen der Unterverzeichnisse *im Verzeichnis*.</p>

<a href="" id="filename"></a>***Dateiname***  
<p style="margin-left: 25px">Der Name einer Datei im Gerätedateisystem.</p>

Unterstützte Vorgänge ist Get.

## <a name="oma-dm-examples"></a>Beispiele für OMA DM


Im folgenden Beispiel wird eine Datei vom Gerät abrufen veranschaulicht.

``` syntax
<Get>
    <CmdID>2</CmdID>
    <Item>
        <Target>
            <LocURI>./Vendor/MSFT/EnterpriseExtFileSystem/Persistent/file.txt</LocURI>
        </Target>
    </Item>
</Get>
```

Im folgende Beispiel zeigt den Dateinamen, der im Textkörper der SyncML Antwortcodes zurückgegeben wird. In diesem Beispiel wird der vollständige Pfad der Datei auf dem Gerät C:/data/test/bin/filename.txt.

``` syntax
<Results>
    <CmdID>3</CmdID>
    <MsgRef>1</MsgRef>
    <CmdRef>2</CmdRef>
    <Item>
        <Source>
            <LocURI>./Vendor/MSFT/EnterpriseExtFileSystem/Persistent/filename.txt</LocURI>
        </Source>
        <Meta>
            <Format xmlns="syncml:metinf">b64</Format>
            <Type xmlns="syncml:metinf">application/octet-stream</Type>
        </Meta>
        <Data>aGVsbG8gd29ybGQ=</Data>
    </Item>
</Results>
```

Im folgenden Beispiel wird eine Datei mit dem Gerät push veranschaulicht.

``` syntax
<Add>
   <CmdID>2</CmdID>
   <Item>
      <Target>
         <LocURI>./Vendor/MSFT/EnterpriseExtFileSystem/Persistent/new.txt</LocURI>
      </Target>
      <Meta>
          <Format xmlns="syncml:metinf">b64</Format>
          <Type xmlns="syncml:metinf">application/octet-stream</Type>
      </Meta>
      <Data>aGVsbG8gd29ybGQ=</Data>
   </Item>
</Add>
```

 

 






