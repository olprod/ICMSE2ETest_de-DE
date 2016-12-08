---
title: Feature-Manifestdatei Inhalt
description: Feature-Manifestdatei (FM) Dateien dienen zum bestimmte Typen von Bild Builds definieren, die unterschiedliche optionale Pakete enthalten. In diesem Thema werden die erforderlichen und optionalen Elemente in einer FM-Datei.
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: ffed39b7-4dd0-48f6-b284-ddaf897beade
ms.openlocfilehash: bdeff28ab8111ceb9b7150002dc2f0be009caf92
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="feature-manifest-file-contents"></a>Feature-Manifestdatei Inhalt


*Feature Manifestdateien (FM)* werden verwendet, um bestimmte Typen von Bild Builds definieren, die unterschiedliche optionale Pakete enthalten. In diesem Thema werden die erforderlichen und optionalen Elemente in einer FM-Datei. Weitere Informationen zur Verwendung von FM-Dateien beim Generieren von Bildern finden Sie unter [Erstellen eines Phone Abbilds ImgGen.cmd verwenden](building-a-phone-image-using-imggencmd.md).

**Hinweis**  
Die meisten Elemente in einer FM-Datei enthalten einen Pfad zu einem Paket. Wenn das Paket unter dem Stammverzeichnis für Microsoft-Pakete ist (WPDKCONTENTROOT %\\MSPackages), diesem Pfad können Sie das Makro $(mspackageroot) in der Name des Pfads. Wenn das Paket in einem anderen Speicherort befindet, können Sie mithilfe einer Umgebungsvariablen, wie etwa Oempackageroot %, und legen diese Umgebungsvariable im Befehlszeilenfenster.

 

## <a name="example-fm-file"></a>FM-Beispieldatei


Das folgende Beispiel zeigt eine Beispieldatei OEM FM.

``` syntax
<?xml version="1.0" encoding="utf-8"?>
<FeatureManifest xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
  xmlns:xsd="http://www.w3.org/2001/XMLSchema" 
  xmlns="http://schemas.microsoft.com/embedded/2004/10/ImageUpdate">
  <BasePackages>
    <PackageFile Path="%oempackageroot%\common\" 
      Name="Contoso.Phone.Test.BaseOs.EnvPath.spkg" />
  </BasePackages>
  <Features>
    <OEM>
     <PackageFile Path="%oempackageroot%\test\" 
      Name="Contoso.Test.MinTE.spkg">
        <FeatureIDs>
          <FeatureID>TEST_FEATURE1</FeatureID>
        </FeatureIDs>
      </PackageFile>
   </OEM>
</Features>
  <ReleasePackages> 
    <PackageFile FeatureIdentifierPackage="true" Name="Contoso.BaseOS.BootApplications_Test.spkg" 
Path="%oempackageroot%\test" ReleaseType="Test"/> 
  </ReleasePackages> 
  <PrereleasePackages>
    <PackageFile ID="Contoso.MainOS.Protected_Replacement_Production" FeatureIdentifierPackage="true" 
Name="Contoso.MainOS.Protected_Replacement_Production.spkg" Path="%oempackageroot%\Merged\" Resolution="*" Type="replacement" Language="*"/>
  </PrereleasePackages>
<OEMDevicePlatformPackages>
    <PackageFile Name="SoCVendor.DCD6000.OEMDevicePlatform.spkg" Path="%oempackageroot%\DCD6000\" Device="DCD6000"/>  
</OEMDevicePlatformPackages>
</FeatureManifest>
```

Sie möchten die MSOptionalFeaturesFM.xml untersuchen, die mit der MobileOS Packagesunder % WPDKCONTENTROOT enthalten ist\\FMFiles zusätzliche FM-XML-Dateien angezeigt.

## <a name="elements-in-a-fm-file"></a>Elemente in einer Datei FM


In den folgenden Abschnitten werden die unterstützten Elemente in einer FM Datei beschrieben.

### <a name="featuremanifest"></a>FeatureManifest

**FeatureManifest** -Element ist das Stammelement des XML in der Datei FM. Dieses Element ist das grundlegende Container-Element für alle anderen Elemente in der Datei. Es muss nur einmal vorkommen.

### <a name="basepackages"></a>BasePackages

Das **BasePackages** -Element gibt Pakete, die immer im Bild enthalten sind, wenn die Datei FM im **AdditionalFMs** -Element der OEMInput-XML-Datei verwiesen wird. Das **BasePackages** -Element hat keine unterstützte Attribute.

In der folgenden Tabelle werden die untergeordneten Elemente des **BasePackages** -Elements beschrieben.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Element</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>PackageFile</strong></p></td>
<td><p>Optional Dieses Element beschreibt ein Paket, das im Bild eingeschlossen werden sollen. Dieses Element unterstützt die folgenden Attribute:</p>
<ul>
<li><p><strong>Pfad</strong> – erforderlich. Der Pfad für das Paket.</p></li>
<li><p><strong>Namen</strong> – erforderlich. Der Dateiname des Pakets.</p></li>
<li><p><strong>Lösung</strong> – Optional. Eine Zeichenfolge, die Auflösung durch das Paket unterstützt enthält. Dieses Attribut kann mit den folgenden Werten angegeben werden:</p>
<ul>
<li><p>&quot;*&quot;: Der &quot; * &quot; Zeichen bedeutet, dass das Paket jede Lösung unterstützt.</p></li>
<li><p>&quot;(720 x 1280; 768 1280 x) &quot;: Mit dieser Syntax gibt den Satz von Lösungen, die das Paket unterstützt. Das Paket ist nur in Bilder enthalten, die für eine der Lösungen in dieser Liste integriert sind.</p></li>
<li><p>&quot;! (720 x 1280; 768 1280 x) &quot;: A '!' vor die Auflösung Liste gibt an, dass das Paket alle Lösungen mit Ausnahme der in der Liste unterstützt. Das Paket ist nur in Bilder enthalten, die für eine der Lösungen in dieser Liste nicht erstellt werden.</p></li>
</ul></li>
<li><p><strong>Sprache</strong> – Optional. Eine Zeichenfolge, die die Anzeige Sprachcodes unterstützt durch das Paket enthält. Dieses Attribut kann mit den folgenden Werten angegeben werden:</p>
<ul>
<li><p>&quot;*&quot;: Der &quot; * &quot; Zeichen bedeutet, dass das Paket jede Sprache unterstützt.</p></li>
<li><p>&quot;(En-US; Zh-CN) &quot;: Mit dieser Syntax gibt den Satz von Sprachen, die das Paket unterstützt. Das Paket ist nur in Bilder enthalten, die einer der Anzeigesprachen in dieser Liste enthalten.</p></li>
<li><p>&quot;! (En-US; Zh-CN) &quot;: A "!" vor der Sprache Liste gibt an, dass das Paket alle Sprachen außer oder in der Liste unterstützt. Das Paket ist nur in Bilder enthalten, die nicht der Anzeigesprachen in der Liste enthalten.</p></li>
</ul></li>
<li><p><strong>Partition</strong> – Optional. Eine Zeichenfolge, die Zielpartition für das Paket angibt. Standardmäßig werden Pakete auf die MainOS Partition installiert, wenn eine andere explizit angegeben wird.</p></li>
</ul>
<p>Diese Elemente sind für Microsoft nur zur internen Verwendung.</p>
<ul>
<li><p><strong>ID</strong> – Optional. String-Wert. Die ID ist der Paketname. Dieses Attribut sollte nicht von OEMs verwendet werden.</p></li>
<li><p><strong>NoBasePackage</strong> – Optional. Boolean-Wert. Legen Sie auf Lösung Pakete true für Sprache sperren, die Basis-Pakete nicht enthalten. Dieses Attribut sollte nicht von OEMs verwendet werden.</p></li>
<li><p><strong>FeatureIdentifierPackage</strong> – Optional. Boolean-Wert. Dieses Attribut sollte nicht von OEMs verwendet werden.</p></li>
</ul></td>
</tr>
</tbody>
</table>

 

### <a name="features"></a>Features

Es werden **Microsoft** und **OEM** -Elementen, von die jedes **Features**enthalten kann. OEM sollten nur ihre Features zum Hinzufügen der ** &lt;OEM&gt; ** Element. Dies bietet mehrere Vorteile, einschließlich der erleichtert die Integration von neueren Versionen der Dateien OEMInput.xml in der OEM Buildsystem.

Das **Features** -Element definiert einen oder mehrere optionale Features, die auf Sie verwiesen werden können im **Features** -Element in der Datei OEMInput optionale Pakete im Bild eingeschlossen. **Features** -Element hat keine unterstützte Attribute.

Die folgende Tabelle beschreibt die untergeordneten Elemente des Elements **Features** .

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Element</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>PackageFile</strong></p></td>
<td><p>Optional Dieses Element beschreibt ein Paket, das im Bild eingeschlossen werden sollen, wenn die Datei OEMInput dieses Feature verweist.</p>
<p>Dieses Element unterstützt die folgenden Attribute:</p>
<ul>
<li><p><strong>Pfad</strong> – benötigt. Der Pfad für das Paket.</p></li>
<li><p><strong>Namen</strong> – erforderlich. Der Dateiname des Pakets.</p></li>
<li><p><strong>Lösung</strong> – Optional. Eine Zeichenfolge, die vom Paket unterstützte Auflösung enthält. Dieses Attribut kann mit den folgenden Werten angegeben werden:</p>
<ul>
<li><p>&quot;*&quot;: Der &quot; * &quot; Zeichen bedeutet, dass das Paket jede Lösung unterstützt.</p></li>
<li><p>&quot;(720 x 1280; 768 1280 x) &quot;: Mit dieser Syntax gibt den Satz von Lösungen, die das Paket unterstützt. Das Paket ist nur in Bilder enthalten, die für eine der Lösungen in dieser Liste integriert sind.</p></li>
<li><p>&quot;! (720 x 1280; 768 1280 x) &quot;: A '!' vor die Auflösung Liste gibt an, dass das Paket alle Lösungen mit Ausnahme der in der Liste unterstützt. Das Paket ist nur in Bilder enthalten, die für eine der Lösungen in dieser Liste nicht erstellt werden.</p></li>
</ul></li>
<li><p><strong>Sprache</strong> – Optional. Eine Zeichenfolge, die die Anzeige Sprachcodes unterstützt durch das Paket enthält. Dieses Attribut kann mit den folgenden Werten angegeben werden:</p>
<ul>
<li><p>&quot;*&quot;: Der &quot; * &quot; Zeichen bedeutet, dass das Paket jede Sprache unterstützt.</p></li>
<li><p>&quot;(En-US; Zh-CN) &quot;: Mit dieser Syntax gibt den Satz von Sprachen, die das Paket unterstützt. Das Paket ist nur in Bilder enthalten, die eine der in dieser Liste Anzeigesprachen enthalten.</p></li>
<li><p>&quot;! (En-US; Zh-CN) &quot;: A "!" vor der Sprache Liste gibt an, dass das Paket alle Sprachen außer denen in der Liste unterstützt. Das Paket ist nur in Bilder enthalten, die nicht der Anzeigesprachen in dieser Liste enthalten.</p></li>
</ul></li>
<li><p><strong>Partition</strong> – Optional. Eine Zeichenfolge, die Zielpartition für das Paket angibt. Standardmäßig werden Pakete auf die MainOS Partition installiert, wenn eine andere explizit angegeben wird.</p></li>
</ul>
<p>Dieses Element unterstützt die folgenden untergeordneten Elemente:</p>
<ul>
<li><p><strong>FeatureIDs</strong> – erforderlich. Ein oder mehrere <strong>FeatureID</strong> Elemente enthält. Jedes <strong>FeatureID</strong> -Element enthält einen String-Wert, der den Namen eines Features angibt, die mit dem angegebenen vom übergeordneten Element <strong>PackageFile</strong> Paket zugeordnet werden sollen.</p></li>
</ul>
<p>Diese Elemente sind für Microsoft nur zur internen Verwendung.</p>
<ul>
<li><p><strong>CPUType</strong> – erforderlich. String-Wert. Legt den CPU-Typ. Kann auf <em>X86</em> oder <em>Arm</em>festgelegt werden. Dieses Attribut sollte nicht von OEMs verwendet werden.</p></li>
<li><p><strong>ID</strong> – Optional. String-Wert. Die ID ist der Paketname. Dieses Attribut sollte nicht von OEMs verwendet werden.</p></li>
<li><p><strong>NoBasePackage</strong> – Optional. Boolean-Wert. Legen Sie auf Lösung Pakete true für Sprache sperren, die Basis-Pakete nicht enthalten. Dieses Attribut sollte nicht von OEMs verwendet werden.</p></li>
<li><p><strong>FeatureIdentifierPackage</strong> – Optional. Boolean-Wert. Dieses Attribut sollte nicht von OEMs verwendet werden.</p></li>
</ul></td>
</tr>
</tbody>
</table>

 

### <a name="feature-groupings-and-constraints"></a>Gruppierung von Features und Einschränkungen

Gruppierung von Features und Einschränkungen können zum Verwalten von Features verwendet werden. Weitere Informationen finden Sie unter [Feature Gruppen und Einschränkungen](feature-groupings-and-constraints.md) .

### <a name="releasepackages"></a>ReleasePackages

Das **ReleasePackages** -Element gibt Pakete, die in Bildern eines bestimmten Version Typs, gemäß dem **ReleaseType** -Element in der Datei OEMInput enthalten sind. Das Element **ReleasePackages** keine unterstützte Attribute aufweisen.

In der folgenden Tabelle werden die untergeordneten Elemente des **ReleasePackages** -Elements beschrieben.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Element</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>PackageFile</strong></p></td>
<td><p>Optional Dieses Element beschreibt ein Paket.</p>
<p>Dieses Element unterstützt die folgenden Attribute:</p>
<ul>
<li><p><strong>ReleaseType</strong> – benötigt. Der Typ des durch das Paket, <strong>Produktion</strong> oder <strong>Test</strong>unterstützte Version. Das Paket wird nur in Bildern, der den Versionstyp des angegebenen enthalten sein.</p></li>
<li><p><strong>Pfad</strong> – erforderlich. Der Pfad für das Paket.</p></li>
<li><p><strong>Namen</strong> – erforderlich. Der Dateiname des Pakets.</p></li>
<li><p><strong>Lösung</strong> – Optional. Eine Zeichenfolge, die Auflösung durch das Paket unterstützt enthält. Dieses Attribut kann mit den folgenden Werten angegeben werden:</p>
<ul>
<li><p>&quot;*&quot;: Der &quot; * &quot; Zeichen bedeutet, dass das Paket jede Lösung unterstützt.</p></li>
<li><p>&quot;(720 x 1280; 768 1280 x) &quot;: Mit dieser Syntax gibt den Satz von Lösungen, die das Paket unterstützt. Das Paket ist nur in Bilder enthalten, die für eine der Lösungen in dieser Liste integriert sind.</p></li>
<li><p>&quot;! (720 x 1280; 768 1280 x) &quot;: A '!' vor die Auflösung Liste gibt an, dass das Paket alle Lösungen mit Ausnahme der in der Liste unterstützt. Das Paket ist nur in Bilder enthalten, die für eine der Lösungen in dieser Liste nicht erstellt werden.</p></li>
</ul></li>
<li><p><strong>Sprache</strong> – Optional. Eine Zeichenfolge, die die Anzeige Sprachcodes unterstützt durch das Paket enthält. Dieses Attribut kann mit den folgenden Werten angegeben werden:</p>
<ul>
<li><p>&quot;*&quot;: Der &quot; * &quot; Zeichen bedeutet, dass das Paket jede Sprache unterstützt.</p></li>
<li><p>&quot;(En-US; Zh-CN) &quot;: Mit dieser Syntax gibt den Satz von Sprachen, die das Paket unterstützt. Das Paket ist nur in Bilder enthalten, die einer der Anzeigesprachen in dieser Liste enthalten.</p></li>
<li><p>&quot;! (En-US; Zh-CN) &quot;: A "!" vor der Sprache Liste gibt an, dass das Paket mit Ausnahme der in der Liste alle Sprachen unterstützt. Das Paket ist nur in Bilder enthalten, die nicht der Anzeigesprachen in der Liste enthalten.</p></li>
</ul></li>
<li><p><strong>Partition</strong> – Optional. Eine Zeichenfolge, die Zielpartition für das Paket angibt. Standardmäßig werden Pakete auf die MainOS Partition installiert, wenn eine andere explizit angegeben wird.</p></li>
</ul>
<p>Diese Elemente sind für Microsoft nur zur internen Verwendung.</p>
<ul>
<li><p><strong>ID</strong> – Optional. String-Wert. Die ID ist der Paketname. Dieses Attribut sollte nicht von OEMs verwendet werden.</p></li>
<li><p><strong>NoBasePackage</strong> – Optional. Boolean-Wert. Legen Sie auf Lösung Pakete true für Sprache sperren, die Basis-Pakete nicht enthalten. Dieses Attribut sollte nicht von OEMs verwendet werden.</p></li>
<li><p><strong>FeatureIdentifierPackage</strong> – Optional. Boolean-Wert. Dieses Attribut sollte nicht von OEMs verwendet werden.</p></li>
</ul></td>
</tr>
</tbody>
</table>

 

### <a name="prereleasepackages"></a>PrereleasePackages

Beschreibt die Pakete, die mithilfe des **ExcludePrereleaseFeatures** -Elements in der Datei OEMInput ausgeschlossen werden können. Weitere Informationen finden Sie unter [OEMInput Inhalt](oeminput-file-contents.md).

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Element</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>PackageFile</strong></p></td>
<td><p>Optional Dieses Element beschreibt ein prelease Paket.</p>
<p>Dieses Element unterstützt die folgenden Attribute:</p>
<ul>
<li><p><strong>Typ</strong> – erforderlich. <strong>Geschützte</strong> oder <strong>Ersatz</strong>möglich.</p>
<p>Die Pakete <strong>geschützt</strong> werden ausgeschlossen beim <code>ExcludePrereleaseFeatures</code> ist festgelegt auf <strong>Ja</strong> und die Ersetzung Pakete, stattdessen werden eingeschlossen. Beispielsweise kann ein Replacement-Feature vom OEM Szenarien wie Mobilfunkbetreiber testen, während der Verteilung von Builds nicht mit vertraulichen Funktionalität unterstützen erstellt werden. Dieser Ansatz ist eine von vielen, und ist nicht erforderlich, jedoch ist eine Möglichkeit zum Verwalten der Veröffentlichung von Feature berücksichtigt. Weitere Informationen finden Sie unter <a href="oeminput-file-contents.md">OEMInput Dateiinhalten</a>.</p>
<div class="alert">
<strong>Wichtige</strong>  
<p>Keine Pakete Replacement sollte im Einzelhandel-Abbild enthalten sein.</p>
</div>
<div>
 
</div></li>
<li><p><strong>Pfad</strong> – erforderlich. Der Pfad für das Paket.</p></li>
<li><p><strong>Namen</strong> – erforderlich. Der Dateiname des Pakets.</p></li>
<li><p><strong>Lösung</strong> – Optional. Eine Zeichenfolge, die Auflösung durch das Paket unterstützt enthält. Dieses Attribut kann mit den folgenden Werten angegeben werden:</p>
<ul>
<li><p>&quot;*&quot;: Der &quot; * &quot; Zeichen bedeutet, dass das Paket jede Lösung unterstützt.</p></li>
<li><p>&quot;(720 x 1280; 768 1280 x) &quot;: Mit dieser Syntax gibt den Satz von Lösungen, die das Paket unterstützt. Das Paket ist nur in Bilder enthalten, die für eine der Lösungen in dieser Liste integriert sind.</p></li>
<li><p>&quot;! (720 x 1280; 768 1280 x) &quot;: A '!' vor die Auflösung Liste gibt an, dass das Paket alle Lösungen mit Ausnahme der in der Liste unterstützt. Das Paket ist nur in Bilder enthalten, die für eine der Lösungen in dieser Liste nicht erstellt werden.</p></li>
</ul></li>
<li><p><strong>Sprache</strong> – Optional. Eine Zeichenfolge, die die Anzeige Sprachcodes unterstützt durch das Paket enthält. Dieses Attribut kann mit den folgenden Werten angegeben werden:</p>
<ul>
<li><p>&quot;*&quot;: Der &quot; * &quot; Zeichen bedeutet, dass das Paket jede Sprache unterstützt.</p></li>
<li><p>&quot;(En-US; Zh-CN) &quot;: Mit dieser Syntax gibt den Satz von Sprachen, die das Paket unterstützt. Das Paket ist nur in Bilder enthalten, die einer der Anzeigesprachen in dieser Liste enthalten.</p></li>
<li><p>&quot;! (En-US; Zh-CN) &quot;: A "!" vor der Sprache Liste gibt an, dass das Paket alle Sprachen außer denen in der Liste unterstützt. Das Paket ist nur in Bilder enthalten, die nicht der Anzeigesprachen in der Liste enthalten.</p></li>
</ul></li>
<li><p><strong>Partition</strong> – Optional. Eine Zeichenfolge, die Zielpartition für das Paket angibt. Standardmäßig werden Pakete auf die MainOS Partition installiert, wenn eine andere explizit angegeben wird.</p></li>
</ul>
<p>Diese Elemente sind für Microsoft nur zur internen Verwendung.</p>
<ul>
<li><p><strong>ID</strong> – Optional. String-Wert. Die ID ist der Paketname. Dieses Attribut sollte nicht von OEMs verwendet werden.</p></li>
<li><p><strong>NoBasePackage</strong> – Optional. Boolean-Wert. Legen Sie auf Lösung Pakete true für Sprache sperren, die Basis-Pakete nicht enthalten. Dieses Attribut sollte nicht von OEMs verwendet werden.</p></li>
<li><p><strong>FeatureIdentifierPackage</strong> – Optional. Boolean-Wert. Dieses Attribut sollte nicht von OEMs verwendet werden.</p></li>
</ul></td>
</tr>
</tbody>
</table>

 

### <a name="socpackages"></a>SOCPackages

Das **SOCPackages** -Element gibt Pakete, die in Bilder enthalten sind, die für eine bestimmte SoC, gemäß dem **SOC** -Element in der Datei OEMInput generiert werden. Das **SOCPackages** -Element hat keine unterstützte Attribute.

In der folgenden Tabelle werden die untergeordneten Elemente des **SOCPackages** -Elements beschrieben.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Element</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>PackageFile</strong></p></td>
<td><p>Optional Dieses Element beschreibt ein Paket.</p>
<p>Dieses Element unterstützt die folgenden Attribute:</p>
<ul>
<li><p><strong>SOC</strong> – erforderlich. Der Typ des durch das Paket unterstützt SoC. Eine Liste der unterstützten Werte finden Sie unter der Beschreibung des Elements <strong>SOC</strong> in [Dateiinhalten OEMInput](oeminput-file-contents.md). Das Paket wird nur in Bilder für die angegebene SoC. generierte enthalten sein</p></li>
<li><p><strong>Pfad</strong> – erforderlich. Der Pfad für das Paket.</p></li>
<li><p><strong>Namen</strong> – erforderlich. Der Dateiname des Pakets.</p></li>
<li><p><strong>Lösung</strong> – Optional. Eine Zeichenfolge, die Auflösung durch das Paket unterstützt enthält. Dieses Attribut kann mit den folgenden Werten angegeben werden:</p>
<ul>
<li><p>&quot;*&quot;: Der &quot; * &quot; Zeichen bedeutet, dass das Paket jede Lösung unterstützt.</p></li>
<li><p>&quot;(720 x 1280; 768 1280 x) &quot;: Mit dieser Syntax gibt den Satz von Lösungen, die das Paket unterstützt. Das Paket ist nur in Bilder enthalten, die für eine der Lösungen in dieser Liste integriert sind.</p></li>
<li><p>&quot;! (720 x 1280; 768 1280 x) &quot;: A '!' vor die Auflösung Liste gibt an, dass das Paket alle Lösungen mit Ausnahme der in der Liste unterstützt. Das Paket ist nur in Bilder enthalten, die für eine der Lösungen in dieser Liste nicht erstellt werden.</p></li>
</ul></li>
<li><p><strong>Sprache</strong> – Optional. Eine Zeichenfolge, die die Anzeige Sprachcodes unterstützt durch das Paket enthält. Dieses Attribut kann mit den folgenden Werten angegeben werden:</p>
<ul>
<li><p>&quot;*&quot;: Der &quot; * &quot; Zeichen bedeutet, dass das Paket jede Sprache unterstützt.</p></li>
<li><p>&quot;(En-US; Zh-CN) &quot;: Mit dieser Syntax gibt den Satz von Sprachen, die das Paket unterstützt. Das Paket ist nur in Bilder enthalten, die einer der Anzeigesprachen in dieser Liste enthalten.</p></li>
<li><p>&quot;! (En-US; Zh-CN) &quot;: A "!" vor der Sprache Liste gibt an, dass das Paket mit Ausnahme der in der Liste alle Sprachen unterstützt. Das Paket ist nur in Bilder enthalten, die nicht der Anzeigesprachen in der Liste enthalten.</p></li>
</ul></li>
<li><p><strong>Partition</strong> – Optional. Eine Zeichenfolge, die Zielpartition für das Paket angibt. Standardmäßig werden Pakete auf die MainOS Partition installiert, wenn eine andere explizit angegeben wird.</p></li>
</ul>
<p>Diese Elemente sind für Microsoft nur zur internen Verwendung.</p>
<ul>
<li><p><strong>CPUType</strong>– erforderlich. String-Wert. Legt den CPU-Typ. Kann auf <em>X86</em> oder <em>Arm</em>festgelegt werden. Dieses Attribut sollte nicht von OEMs verwendet werden. Dieses Attribut sollte nicht von OEMs verwendet werden.</p></li>
<li><p><strong>ID</strong> – Optional. String-Wert. Die ID ist der Paketname. Dieses Attribut sollte nicht von OEMs verwendet werden.</p></li>
<li><p><strong>NoBasePackage</strong> – Optional. Boolean-Wert. Legen Sie auf Lösung Pakete true für Sprache sperren, die Basis-Pakete nicht enthalten. Dieses Attribut sollte nicht von OEMs verwendet werden.</p></li>
<li><p><strong>FeatureIdentifierPackage</strong> – Optional. Boolean-Wert. Dieses Attribut sollte nicht von OEMs verwendet werden.</p></li>
</ul></td>
</tr>
</tbody>
</table>

 

### <a name="svpackages"></a>SVPackages

Das **SVPackages** -Element gibt Pakete, die in Bilder enthalten sind, die für einen bestimmten SoC Hersteller gemäß dem **PA** -Element in der Datei OEMInput generiert werden. Das **SVPackages** -Element hat keine unterstützte Attribute.

In der folgenden Tabelle werden die untergeordneten Elemente des **SVPackages** -Elements beschrieben.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Element</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>PackageFile</strong></p></td>
<td><p>Optional Dieses Element beschreibt ein Paket.</p>
<p>Dieses Element unterstützt die folgenden Attribute:</p>
<ul>
<li><p><strong>PA</strong> – erforderlich. Der Hersteller für die SoC, die durch das Paket unterstützt wird. Das Paket wird nur in Bilder für die angegebene SoC Anbieter generierte einbezogen werden.</p></li>
<li><p><strong>Pfad</strong> – erforderlich. Der Pfad für das Paket.</p></li>
<li><p><strong>Namen</strong> – Optional.</p></li>
<li><p><strong>Lösung</strong> – Optional. Eine Zeichenfolge, die Auflösung durch das Paket unterstützt enthält. Dieses Attribut kann mit den folgenden Werten angegeben werden:</p>
<ul>
<li><p>&quot;*&quot;: Der &quot; * &quot; Zeichen bedeutet, dass das Paket jede Lösung unterstützt.</p></li>
<li><p>&quot;(720 x 1280; 768 1280 x) &quot;: Mit dieser Syntax gibt den Satz von Lösungen, die das Paket unterstützt. Das Paket ist nur in Bilder enthalten, die für eine der Lösungen in dieser Liste integriert sind.</p></li>
<li><p>&quot;! (720 x 1280; 768 1280 x) &quot;: A '!' vor die Auflösung Liste gibt an, dass das Paket alle Lösungen mit Ausnahme der in der Liste unterstützt. Das Paket ist nur in Bilder enthalten, die für eine der Lösungen in dieser Liste nicht erstellt werden.</p></li>
</ul></li>
<li><p><strong>Sprache</strong> – Optional. Eine Zeichenfolge, die die Anzeige Sprachcodes unterstützt durch das Paket enthält. Dieses Attribut kann mit den folgenden Werten angegeben werden:</p>
<ul>
<li><p>&quot;*&quot;: Der &quot; * &quot; Zeichen bedeutet, dass das Paket jede Sprache unterstützt.</p></li>
<li><p>&quot;(En-US; Zh-CN) &quot;: Mit dieser Syntax gibt den Satz von Sprachen, die das Paket unterstützt. Das Paket ist nur in Bilder enthalten, die einer der Anzeigesprachen in dieser Liste enthalten.</p></li>
<li><p>&quot;! (En-US; Zh-CN) &quot;: A "!" vor der Sprache Liste gibt an, dass das Paket mit Ausnahme der in der Liste alle Sprachen unterstützt. Das Paket ist nur in Bilder enthalten, die nicht der Anzeigesprachen in der Liste enthalten.</p></li>
</ul></li>
<li><p><strong>Partition</strong> – Optional. Eine Zeichenfolge, die Zielpartition für das Paket angibt. Standardmäßig werden Pakete auf die MainOS Partition installiert, wenn eine andere explizit angegeben wird.</p></li>
</ul>
<p>Diese Elemente sind für Microsoft nur zur internen Verwendung.</p>
<ul>
<li><p><strong>CPUType</strong>– erforderlich. String-Wert. Legt den CPU-Typ. Kann auf <em>X86</em> oder <em>Arm</em>festgelegt werden. Dieses Attribut sollte nicht von OEMs verwendet werden. Dieses Attribut sollte nicht von OEMs verwendet werden.</p></li>
<li><p><strong>ID</strong> – Optional. String-Wert. Die ID ist der Paketname. Dieses Attribut sollte nicht von OEMs verwendet werden.</p></li>
<li><p><strong>NoBasePackage</strong> – Optional. Boolean-Wert. Legen Sie auf Lösung Pakete true für Sprache sperren, die Basis-Pakete nicht enthalten. Dieses Attribut sollte nicht von OEMs verwendet werden.</p></li>
<li><p><strong>FeatureIdentifierPackage</strong> – Optional. Boolean-Wert. Dieses Attribut sollte nicht von OEMs verwendet werden.</p></li>
</ul></td>
</tr>
</tbody>
</table>

 

### <a name="oemdeviceplatformpackages"></a>OEMDevicePlatformPackages

Das **OEMDevicePlatformPackages** -Element gibt das Gerät Plattform Paket in ein Bild für ein bestimmtes Gerätetyp werden soll. OEMs müssen das Gerät Plattform-Paket angeben, durch die Verwendung dieses Elements in einer FM-Datei. Weitere Informationen zu Gerät Plattform-Paketen finden Sie unter [Festlegen von Geräteinformationen Plattform](set-device-platform-information.md). Das **OEMDevicePlatformPackages** -Element hat keine unterstützte Attribute.

In der folgenden Tabelle werden die untergeordneten Elemente des **OEMDevicePlatformPackages** -Elements beschrieben.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Element</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>PackageFile</strong></p></td>
<td><p>Optional Dieses Element beschreibt ein Gerät Plattform Paket zum Einschließen in das Bild für ein bestimmtes Gerät.</p>
<p>Dieses Element unterstützt die folgenden Attribute:</p>
<ul>
<li><p><strong>Gerät</strong> – erforderlich. Der Gerätetyp, der durch das Gerät-Paket-Plattform unterstützt wird. Das Paket wird nur in Bilder für die angegebene Gerätetyp generierte einbezogen werden.</p></li>
<li><p><strong>Pfad</strong> – erforderlich. Der Pfad für das Paket.</p></li>
<li><p><strong>Namen</strong> – erforderlich. Der Dateiname des Pakets.</p></li>
</ul>
<p>Diese Elemente sind für Microsoft nur zur internen Verwendung.</p>
<ul>
<li><p><strong>CPUType</strong>– erforderlich. String-Wert. Legt den CPU-Typ. Kann auf <em>X86</em> oder <em>Arm</em>festgelegt werden. Dieses Attribut sollte nicht von OEMs verwendet werden.</p></li>
<li><p><strong>ID</strong> – Optional. String-Wert. Die ID ist der Paketname. Dieses Attribut sollte nicht von OEMs verwendet werden.</p></li>
<li><p><strong>NoBasePackage</strong> – Optional. Boolean-Wert. Legen Sie auf Lösung Pakete true für Sprache sperren, die Basis-Pakete nicht enthalten. Dieses Attribut sollte nicht von OEMs verwendet werden.</p></li>
<li><p><strong>FeatureIdentifierPackage</strong> – Optional. Boolean-Wert. Dieses Attribut sollte nicht von OEMs verwendet werden.</p></li>
</ul></td>
</tr>
</tbody>
</table>

 

### <a name="devicespecificpackages"></a>DeviceSpecificPackages

Das **DeviceSpecificPackages** -Element gibt Pakete zum Einschließen in Bilder, die für einen bestimmten Gerätetyp gemäß dem **Gerät** -Element in der Datei OEMInput generiert werden. Das **DeviceSpecificPackages** -Element hat keine unterstützte Attribute.

Die folgende Tabelle beschreibt die untergeordneten Elemente des **DeviceSpecificPackages** -Elements.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Element</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>PackageFile</strong></p></td>
<td><p>Optional Dieses Element beschreibt ein Paket zum Einschließen in das Bild für ein bestimmtes Gerät.</p>
<p>Dieses Element unterstützt die folgenden Attribute:</p>
<ul>
<li><p><strong>Gerät</strong> – benötigt. Der Gerätetyp, der durch das Gerät-Paket-Plattform unterstützt wird. Das Paket wird nur in Bilder für die angegebene Gerätetyp generierte einbezogen werden.</p></li>
<li><p><strong>Pfad</strong> – erforderlich. Der Pfad für das Paket.</p></li>
<li><p><strong>Namen</strong> – erforderlich. Der Dateiname des Pakets.</p></li>
<li><p><strong>Lösung</strong> – Optional. Eine Zeichenfolge, die Auflösung durch das Paket unterstützt enthält. Dieses Attribut kann mit den folgenden Werten angegeben werden:</p>
<ul>
<li><p>&quot;*&quot;: Der &quot; * &quot; Zeichen bedeutet, dass das Paket jede Lösung unterstützt.</p></li>
<li><p>&quot;(720 x 1280; 768 1280 x) &quot;: Mit dieser Syntax gibt den Satz von Lösungen, die das Paket unterstützt. Das Paket ist nur in Bilder enthalten, die für eine der Lösungen in dieser Liste integriert sind.</p></li>
<li><p>&quot;! (720 x 1280; 768 1280 x) &quot;: A '!' vor die Auflösung Liste gibt an, dass das Paket alle Lösungen mit Ausnahme der in der Liste unterstützt. Das Paket ist nur in Bilder enthalten, die für eine der Lösungen in dieser Liste nicht erstellt werden.</p></li>
</ul></li>
<li><p><strong>Sprache</strong> – Optional. Eine Zeichenfolge, die die Anzeige Sprachcodes unterstützt durch das Paket enthält. Dieses Attribut kann mit den folgenden Werten angegeben werden:</p>
<ul>
<li><p>&quot;*&quot;: Der &quot; * &quot; Zeichen bedeutet, dass das Paket jede Sprache unterstützt.</p></li>
<li><p>&quot;(En-US; Zh-CN) &quot;: Mit dieser Syntax gibt den Satz von Sprachen, die das Paket unterstützt. Das Paket ist nur in Bilder enthalten, die einer der Anzeigesprachen in dieser Liste enthalten.</p></li>
<li><p>&quot;! (En-US; Zh-CN) &quot;: A "!" vor der Sprache Liste gibt an, dass das Paket mit Ausnahme der in der Liste alle Sprachen unterstützt. Das Paket ist nur in Bilder enthalten, die nicht der Anzeigesprachen in der Liste enthalten.</p></li>
</ul></li>
<li><p><strong>Partition</strong> – Optional. Eine Zeichenfolge, die Zielpartition für das Paket angibt. Standardmäßig werden Pakete auf die MainOS Partition installiert, wenn eine andere explizit angegeben wird.</p></li>
</ul>
<p>Diese Elemente sind für Microsoft nur zur internen Verwendung.</p>
<ul>
<li><p><strong>CPUType</strong>– erforderlich. String-Wert. Legt den CPU-Typ. Kann auf <em>X86</em> oder <em>Arm</em>festgelegt werden. Dieses Attribut sollte nicht von OEMs verwendet werden.</p></li>
<li><p><strong>ID</strong> – Optional. String-Wert. Die ID ist der Paketname, die dieses Attribut nicht von OEMs verwendet werden soll.</p></li>
<li><p><strong>NoBasePackage</strong> – Optional. Boolean-Wert. Legen Sie auf Lösung Pakete true für Sprache sperren, die Basis-Pakete nicht enthalten. Dieses Attribut sollte nicht von OEMs verwendet werden.</p></li>
<li><p><strong>FeatureIdentifierPackage</strong> – Optional. Boolean-Wert. Dieses Attribut sollte nicht von OEMs verwendet werden.</p></li>
</ul></td>
</tr>
</tbody>
</table>

 

## <a name="microsoft-internal-use-only"></a>Microsoft nur zur internen Verwendung


Die folgenden Komponenten sind für die Microsoft nur interne Verwendung reserviert, jedoch werden hier der Vollständigkeit dokumentiert.

### <a name="cpupackages"></a>CPUPackages

Für die interne Verwendung durch Microsoft reserviert. Dieses Element sollte nicht von OEMs verwendet werden.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Element</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>PackageFile</strong></p></td>
<td><p>Optional Dieses Element beschreibt ein Paket.</p>
<p>Dieses Element unterstützt die folgenden Attribute:</p>
<ul>
<li><p><strong>CPUType</strong> – erforderlich. String-Wert. Legt den CPU-Typ. Kann auf <em>X86</em> oder <em>Arm</em>festgelegt werden. Dieses Attribut sollte nicht von OEMs verwendet werden.</p></li>
<li><p><strong>Pfad</strong> – erforderlich. Der Pfad für das Paket.</p></li>
<li><p><strong>Namen</strong> – erforderlich. Der Dateiname des Pakets.</p></li>
<li><p><strong>ID</strong>– Optional. String-Wert. Die ID ist der Paketname. Dieses Attribut sollte nicht von OEMs verwendet werden.</p></li>
<li><p><strong>NoBasePackage</strong> – Optional. Boolean-Wert. Legen Sie auf Lösung Pakete true für Sprache sperren, die Basis-Pakete nicht enthalten. Dieses Attribut sollte nicht von OEMs verwendet werden.</p></li>
<li><p><strong>FeatureIdentifierPackage</strong> – Optional. Boolean-Wert. Dieses Attribut sollte nicht von OEMs verwendet werden.</p></li>
<li><p><strong>Lösung</strong> – Optional. Eine Zeichenfolge, die Auflösung durch das Paket unterstützt enthält. Dieses Attribut kann mit den folgenden Werten angegeben werden:</p>
<ul>
<li><p>&quot;*&quot;: Der &quot; * &quot; Zeichen bedeutet, dass das Paket jede Lösung unterstützt.</p></li>
<li><p>&quot;(720 x 1280; 768 1280 x) &quot;: Mit dieser Syntax gibt den Satz von Lösungen, die das Paket unterstützt. Das Paket ist nur in Bilder enthalten, die für eine der Lösungen in dieser Liste integriert sind.</p></li>
<li><p>&quot;! (720 x 1280; 768 1280 x) &quot;: A '!' vor die Auflösung Liste gibt an, dass das Paket alle Lösungen mit Ausnahme der in der Liste unterstützt. Das Paket ist nur in Bilder enthalten, die für eine der Lösungen in dieser Liste nicht erstellt werden.</p></li>
</ul></li>
<li><p><strong>Sprache</strong> – Optional. Eine Zeichenfolge, die die Anzeige Sprachcodes unterstützt durch das Paket enthält. Dieses Attribut kann mit den folgenden Werten angegeben werden:</p>
<ul>
<li><p>&quot;*&quot;: Der &quot; * &quot; Zeichen bedeutet, dass das Paket jede Sprache unterstützt.</p></li>
<li><p>&quot;(En-US; Zh-CN) &quot;: Mit dieser Syntax gibt den Satz von Sprachen, die das Paket unterstützt. Das Paket ist nur in Bilder enthalten, die einer der Anzeigesprachen in dieser Liste enthalten.</p></li>
<li><p>&quot;! (En-US; Zh-CN) &quot;: A "!" vor der Sprache Liste gibt an, dass das Paket alle Sprachen außer denen in der Liste unterstützt. Das Paket ist nur in Bilder enthalten, die nicht der Anzeigesprachen in der Liste enthalten.</p></li>
</ul></li>
<li><p><strong>Partition</strong> – Optional. Eine Zeichenfolge, die Zielpartition für das Paket angibt.</p></li>
</ul></td>
</tr>
</tbody>
</table>

 

### <a name="bootuilanguagepackagefile"></a>BootUILanguagePackageFile

Für die interne Verwendung durch Microsoft reserviert. Dieses Element sollte nicht von OEMs verwendet werden.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Element</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>BootUILanguagePackageFile</strong></p></td>
<td><p>Optional Dieses Element unterstützt die folgenden Attribute:</p>
<ul>
<li><p><strong>Pfad</strong> – erforderlich. Der Pfad für das Paket.</p></li>
<li><p><strong>Namen</strong> – erforderlich. Der Dateiname des Pakets.</p></li>
<li><p><strong>ID</strong> – Optional. String-Wert. Die ID ist der Paketname. Dieses Attribut sollte nicht von OEMs verwendet werden.</p></li>
<li><p><strong>NoBasePackage</strong> – Optional. Boolean-Wert. Legen Sie auf Lösung Pakete true für Sprache sperren, die Basis-Pakete nicht enthalten. Dieses Attribut sollte nicht von OEMs verwendet werden.</p></li>
<li><p><strong>FeatureIdentifierPackage</strong> – Optional. Boolean-Wert. Dieses Attribut sollte nicht von OEMs verwendet werden.</p></li>
<li><p><strong>Partition</strong> – Optional. Eine Zeichenfolge, die Zielpartition für das Paket angibt.</p></li>
</ul></td>
</tr>
</tbody>
</table>

 

### <a name="bootlocalepackagefile"></a>BootLocalePackageFile

Für die interne Verwendung durch Microsoft reserviert. Dieses Element sollte nicht von OEMs verwendet werden.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Element</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>BootLocalePackageFile</strong></p></td>
<td><p>Optional Dieses Element unterstützt die folgenden Attribute:</p>
<ul>
<li><p><strong>Pfad</strong> – erforderlich. Der Pfad für das Paket.</p></li>
<li><p><strong>Namen</strong> – erforderlich. Der Dateiname des Pakets.</p></li>
<li><p><strong>ID</strong> – Optional. String-Wert. Die ID ist der Paketname. Dieses Attribut sollte nicht von OEMs verwendet werden.</p></li>
<li><p><strong>NoBasePackage</strong> – Optional. Boolean-Wert. Legen Sie auf Lösung Pakete true für Sprache sperren, die Basis-Pakete nicht enthalten. Dieses Attribut sollte nicht von OEMs verwendet werden.</p></li>
<li><p><strong>FeatureIdentifierPackage</strong> – Optional. Boolean-Wert. Dieses Attribut sollte nicht von OEMs verwendet werden.</p></li>
<li><p><strong>Partition</strong> – Optional. Eine Zeichenfolge, die Zielpartition für das Paket angibt.</p></li>
</ul></td>
</tr>
</tbody>
</table>

 

### <a name="devicelayoutpackages"></a>DeviceLayoutPackages

Für die interne Verwendung durch Microsoft reserviert. Dieses Element sollte nicht von OEMs verwendet werden.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Element</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>PackageFile</strong></p></td>
<td><p>Optional Dieses Element beschreibt ein Paket.</p>
<p>Dieses Element unterstützt die folgenden Attribute:</p>
<ul>
<li><p><strong>SOC</strong> – erforderlich.</p></li>
<li><p><strong>Pfad</strong> – erforderlich. Der Pfad für das Paket.</p></li>
<li><p><strong>Namen</strong> – erforderlich. Der Dateiname des Pakets.</p></li>
<li><p><strong>Partition</strong> – Optional. Eine Zeichenfolge, die Zielpartition für das Paket angibt. Standardmäßig werden Pakete auf die MainOS Partition installiert, wenn eine andere explizit angegeben wird.</p></li>
<li><p><strong>ID</strong>– Optional. String-Wert. Die ID ist der Paketname. Dieses Attribut sollte nicht von OEMs verwendet werden.</p></li>
<li><p><strong>NoBasePackage</strong> – Optional. Boolean-Wert. Legen Sie auf Lösung Pakete true für Sprache sperren, die Basis-Pakete nicht enthalten. Dieses Attribut sollte nicht von OEMs verwendet werden.</p></li>
<li><p><strong>FeatureIdentifierPackage</strong> – Optional. Boolean-Wert. Dieses Attribut sollte nicht von OEMs verwendet werden.</p></li>
<li><p><strong>CPUType</strong>– erforderlich. String-Wert. Legt den CPU-Typ. Kann auf <em>X86</em> oder <em>Arm</em>festgelegt werden. Dieses Attribut sollte nicht von OEMs verwendet werden. Dieses Attribut sollte nicht von OEMs verwendet werden.</p></li>
<li><p><strong>Partition</strong> – Optional. Eine Zeichenfolge, die Zielpartition für das Paket angibt.</p></li>
</ul></td>
</tr>
</tbody>
</table>

 

### <a name="keyboardpackages"></a>KeyboardPackages

Für die interne Verwendung durch Microsoft reserviert. Dieses Element sollte nicht von OEMs verwendet werden.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Element</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>PackageFile</strong></p></td>
<td><p>Optional Dieses Element beschreibt ein Paket.</p>
<p>Dieses Element unterstützt die folgenden Attribute:</p>
<ul>
<li><p><strong>Pfad</strong> – erforderlich. Der Pfad für das Paket.</p></li>
<li><p><strong>Namen</strong> – erforderlich. Der Dateiname des Pakets.</p></li>
<li><p><strong>ID</strong>– Optional. String-Wert. Die ID ist der Paketname. Dieses Attribut sollte nicht von OEMs verwendet werden.</p></li>
<li><p><strong>NoBasePackage</strong> – Optional. Boolean-Wert. Legen Sie auf Lösung Pakete true für Sprache sperren, die Basis-Pakete nicht enthalten. Dieses Attribut sollte nicht von OEMs verwendet werden.</p></li>
<li><p><strong>FeatureIdentifierPackage</strong> – Optional. Boolean-Wert. Dieses Attribut sollte nicht von OEMs verwendet werden.</p></li>
<li><p><strong>Sprache</strong> – Optional. Eine Zeichenfolge, die die Anzeige Sprachcodes unterstützt durch das Paket enthält. Dieses Attribut kann mit den folgenden Werten angegeben werden:</p>
<ul>
<li><p>&quot;*&quot;: Der &quot; * &quot; Zeichen bedeutet, dass das Paket jede Sprache unterstützt.</p></li>
<li><p>&quot;(En-US; Zh-CN) &quot;: Mit dieser Syntax gibt den Satz von Sprachen, die das Paket unterstützt. Das Paket ist nur in Bilder enthalten, die einer der Anzeigesprachen in dieser Liste enthalten.</p></li>
<li><p>&quot;! (En-US; Zh-CN) &quot;: A "!" vor der Sprache Liste gibt an, dass das Paket mit Ausnahme der in der Liste alle Sprachen unterstützt. Das Paket ist nur in Bilder enthalten, die nicht der Anzeigesprachen in der Liste enthalten.</p></li>
</ul></li>
<li><p><strong>Partition</strong> – Optional. Eine Zeichenfolge, die Zielpartition für das Paket angibt. Standardmäßig werden Pakete auf die MainOS Partition installiert, wenn eine andere explizit angegeben wird.</p></li>
</ul></td>
</tr>
</tbody>
</table>

 

### <a name="speechpackages"></a>SpeechPackages

Für die interne Verwendung durch Microsoft reserviert. Dieses Element sollte nicht von OEMs verwendet werden.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Element</th>
<th>Beschreibung</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>PackageFile</strong></p></td>
<td><p>Optional Dieses Element beschreibt ein Paket.</p>
<p>Dieses Element unterstützt die folgenden Attribute:</p>
<ul>
<li><p><strong>Pfad</strong> – erforderlich. Der Pfad für das Paket.</p></li>
<li><p><strong>Namen</strong> – erforderlich. Der Dateiname des Pakets.</p></li>
<li><p><strong>ID</strong>– Optional. String-Wert. Die ID ist der Paketname. Dieses Attribut sollte nicht von OEMs verwendet werden.</p></li>
<li><p><strong>NoBasePackage</strong> – Optional. Boolean-Wert. Legen Sie auf Lösung Pakete true für Sprache sperren, die Basis-Pakete nicht enthalten. Dieses Attribut sollte nicht von OEMs verwendet werden.</p></li>
<li><p><strong>FeatureIdentifierPackage</strong> – Optional. Boolean-Wert. Dieses Attribut sollte nicht von OEMs verwendet werden.</p></li>
<li><p><strong>Sprache</strong> – Optional. Eine Zeichenfolge, die die Anzeige Sprachcodes unterstützt durch das Paket enthält. Dieses Attribut kann mit den folgenden Werten angegeben werden:</p>
<ul>
<li><p>&quot;*&quot;: Der &quot; * &quot; Zeichen bedeutet, dass das Paket jede Sprache unterstützt.</p></li>
<li><p>&quot;(En-US; Zh-CN) &quot;: Mit dieser Syntax gibt den Satz von Sprachen, die das Paket unterstützt. Das Paket ist nur in Bilder enthalten, die einer der Anzeigesprachen in dieser Liste enthalten.</p></li>
<li><p>&quot;! (En-US; Zh-CN) &quot;: A "!" vor der Sprache Liste gibt an, dass das Paket mit Ausnahme der in der Liste alle Sprachen unterstützt. Das Paket ist nur in Bilder enthalten, die nicht der Anzeigesprachen in der Liste enthalten.</p></li>
</ul></li>
<li><p><strong>Partition</strong> – Optional. Eine Zeichenfolge, die Zielpartition für das Paket angibt. Standardmäßig werden Pakete auf die MainOS Partition installiert, wenn eine andere explizit angegeben wird.</p></li>
</ul></td>
</tr>
</tbody>
</table>

 

## <a name="related-topics"></a>Verwandte Themen


[Erstellen von ein Telefon Bild mit ImgGen.cmd](building-a-phone-image-using-imggencmd.md)

 

 

[Senden Sie Kommentare zu diesem Thema an Microsoft] (mailto:wsddocfb@microsoft.com?subject=Documentation%20feedback%20%5Bp_phFlashing\p_phFlashing%5D:%20Feature%20manifest%20file%20contents%20%20RELEASE:%20%2810/4/2016%29&body=%0A%0APRIVACY%20STATEMENT%0A%0AWe%20use%20your%20feedback%20to%20improve%20the%20documentation.%20We%20don't%20use%20your%20email%20address%20for%20any%20other%20purpose,%20and%20we'll%20remove%20your%20email%20address%20from%20our%20system%20after%20the%20issue%20that%20you're%20reporting%20is%20fixed.%20While%20we're%20working%20to%20fix%20this%20issue,%20we%20might%20send%20you%20an%20email%20message%20to%20ask%20for%20more%20info.%20Later,%20we%20might%20also%20send%20you%20an%20email%20message%20to%20let%20you%20know%20that%20we've%20addressed%20your%20feedback.%0A%0AFor%20more%20info%20about%20Microsoft's%20privacy%20policy,%20see%20http://privacy.microsoft.com/default.aspx. "Senden Sie Kommentare zu diesem Thema an Microsoft")





