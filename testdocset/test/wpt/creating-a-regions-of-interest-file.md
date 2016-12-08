---
title: Erstellen einer Bereiche der Zinsen-Datei
description: Erstellen einer Bereiche der Zinsen-Datei
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: e8818fd2-3536-4b02-840d-f7d2eb4fbd91
ms.prod: W10
ms.mktglfcycl: operate
ms.sitesec: msdn
ms.openlocfilehash: 929a65a01f45c2b4de4d1f1d4140f92c80c7a5f5
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="creating-a-regions-of-interest-file"></a>Erstellen einer Bereiche der Zinsen-Datei


Eine Datei Regionen von Interesse ist eine gültige XML-Datei mit den folgenden Knoten:

-   **InstrumentationManifest**

-   **Instrumentation**

-   **Formularbereichen (engl.)**

-   **RegionsRoot**, ein Container für alle definierten Bereiche

-   Eine oder mehrere **Region** -Knoten

**Hinweis**  
Definition einer Region, die *Version* -Attribut in der XML-Deklaration wie `version='1.0'`, ist optional.

 

Im folgende Beispiel wird eine vollständige Regionen interessante-Datei, die einen einfachen Bereich definiert. Erläutern der Attribute und Knoten innerhalb der **Region** werden nach dem Beispiel beschrieben.

``` syntax
<?xml version='1.0' encoding='utf-8' standalone='yes'?>
<?Copyright (c) Microsoft Corporation. All rights reserved.?>
<InstrumentationManifest>
   <Instrumentation>
      <Regions>
         <RegionRoot Guid="{EFA7A927-BAE3-48F6-92E1-000000000000}"
                     Name="Sample Region File Root"
                     FriendlyName="Root">
            <Region Guid="{d8d639a0-cf4c-45fb-976a-000111000100}"
                    Name="FastStartup-Suspend-UserSession-Shutdown"
                    FriendlyName="User Session Shutdown">
               <Start>
                  <Event Provider="{dbe9b383-7cf3-4331-91cc-a3cb16a3b538}" Id="301" Version="0" />
               </Start>
               <Stop>
                  <Event Provider="{331c3b3a-2005-44c2-ac5e-77220c37d6b4}" Id="22" Version="0" />
               </Stop>
            </Region>
         </RegionRoot>
      </Regions>
   </Instrumentation>
</InstrumentationManifest>
```

In diesem Thema hat den folgenden Inhalt:

-   [Definieren einer region](#defining-a-region)
-   [Region-Typen](#region-types)
-   [Verwenden von Nutzlast Feldern zur Identifizierung von Ereignissen](#using-payload-fields-to-identify-events)
-   [Entsprechende Ereignisse für Regionen](#matching-events-for-regions)
-   [Filtern einer Region auf der Grundlage einer Bedingung](#filtering-a-region-based-on-a-condition)
-   [Über-und untergeordneten Elementen](#parent-child-relationships)
-   [Self Schachtelung von Regionen](#self-nesting-regions)
-   [Instanznamen](#instance-names)
-   [Metadaten](#metadata)

### <a name="defining-a-region"></a>Definieren einer region

Eine Definition Region enthält die folgenden Attribute im Knoten **Region** :

-   *GUID* (erforderlich), eine GUID für den Bereich.

-   *Name* (erforderlich), einen eindeutigen Namen für die Region. Ist ein vorgeschlagener Format für *Name* `Root-GrandparentName-ParentName-RegionName`.

-   *FriendlyName* (optional), einen alternativen Namen für die Region.

### <a name="region-types"></a>Region-Typen

Sie können die folgenden Arten von Bereiche auf Grundlage von starten und beenden Sie erstellen:

-   [Bereiche auf Grundlage von Ereignissen](#regions-based-on-events)
-   [Bereiche auf Grundlage der Dauer](#regions-based-on-duration)
-   [Bereiche auf Grundlage von anderen Regionen](#regions-based-on-other-regions)
-   [Bereiche, die von anderen Regionen Container sind](#regions-within-regions)

### <a name="regions-based-on-events"></a>Bereiche auf Grundlage von Ereignissen

Der am häufigsten verwendete Typ des Bereichs ist durch Ereignisse, deren starten und Beenden von Punkte definiert sind.

Um ein Ereignis als die Anfangs- oder Endpunkt angeben, müssen Sie die folgenden Attribute enthalten:

-   *Anbieter*, eine GUID, die Provider-ID für das Ereignis angibt.

-   *Id*, eine nicht signierte kurze, der die ID des Ereignisses angibt.

-   *Version*, einer ohne Vorzeichen, der die Version des Ereignisses angibt.

Darüber hinaus können Sie die Definition durch Hinzufügen von einem oder mehreren **PayloadIdentifier** Knoten weiter optimieren. Diese Tags enthalten zwei Zeichenfolgenattribute, *FieldName* und *FieldValue*, die ein Feld angeben, die das Ereignis enthalten muss. **PayloadIdentifier** Tags werden weiter unten in **Using Nutzlast Felder zur Identifizierung von Ereignissen**beschrieben werden.

### <a name="examples"></a>Beispiele

Es folgt ein einfaches Beispiel für diese Art von Region:

``` syntax
<Region Guid="{d8d639a0-cf4c-45fb-976a-000111000100}"
        Name="FastStartup-Suspend-UserSession-Shutdown"
        FriendlyName="User Session Shutdown">
   <Start>
      <Event Provider="{dbe9b383-7cf3-4331-91cc-a3cb16a3b538}" Id="301" Version="0" />
   </Start>
   <Stop>
      <Event Provider="{331c3b3a-2005-44c2-ac5e-77220c37d6b4}" Id="22" Version="0" />
   </Stop>
</Region>
```

Im folgenden Beispiel wird die Region endet nur, wenn das angegebene Ereignis ein Feld namens enthält `StartOrStop` mit dem Wert `Stop`:

``` syntax
<Region Guid="{d8d639a0-cf4c-45fb-976a-000111000100}"
        Name="FastStartup-Suspend-UserSession-Shutdown"
        FriendlyName="User Session Shutdown">
   <Start>
      <Event Provider="{dbe9b383-7cf3-4331-91cc-a3cb16a3b538}" Id="301" Version="0" />
   </Start>
   <Stop>
      <Event Provider="{331c3b3a-2005-44c2-ac5e-77220c37d6b4}" Id="22" Version="0" />
      <PayloadIdentifier FieldName="StartOrStop" FieldValue="Stop" />
   </Stop>
</Region>
```

### <a name="regions-based-on-duration"></a>Bereiche auf Grundlage der Dauer

Viele ETW-Ereignisse werden als ein einzelnes Stop-Ereignis mit einer Dauer Nutzlastfeld definiert. Wir können den Anfangspunkt berechnen, indem subtrahiert die Dauer von Zeit für das Stop-Ereignis.

Das Tag **Dauer** kann in einem Tag **Starten** oder **Beenden** eines Felds Nutzlast aus dem Code Dauerinformationen an verwendet werden. Wenn Sie eine Dauer für den Anfangspunkt definieren, wird die Dauer von den Punkt subtrahiert. Wenn Sie eine Dauer für den Punkt definieren, wird die Dauer zum Startpunkt hinzugefügt.

Der **Dauer** Knoten kann die folgenden Attribute aufweisen:

-   *Anbieter*, eine GUID, die die Provider-ID für das Ereignis angibt, das das Nutzlastfeld enthält.

-   *Id*, eine nicht signierte kurze, die die ID des Ereignisses angibt, das das Nutzlastfeld enthält.

-   *Version*, einer ohne Vorzeichen, die die Version des Ereignisses angibt, das das Nutzlastfeld enthält.

-   *Dauer*, eine Zeichenfolge, die den Namen des Felds Nutzlast angibt.

-   *Multiplikator*. WPA erfordert die Dauer in Nanosekunden sein. Verwenden Sie dieses Attribut, um die Dauer in Nanosekunden zu konvertieren, bei Bedarf. Verwenden Sie beispielsweise 1000000 ein (1 Mio.), um Millisekunden Nanosekunden zu konvertieren.

Wenn Sie eine Dauer für den Anfangspunkt definieren, wird die Dauer von den Punkt subtrahiert. Wenn Sie eine Dauer für den Punkt definieren, wird die Dauer zum Startpunkt hinzugefügt.

### <a name="example"></a>Beispiel

Im folgende Beispiel definiert einen Bereich, der beim Start von einer anderen Region beendet. Um den Anfangspunkt zu berechnen, subtrahieren wir eine Dauer von Kontaktpunkt Öffnungsvorgangs. Die Dauer wird im Feld Nutzlast HiberHiberFileTime gefunden. Klicken Sie dann Multiplizieren wir die Dauer von 1.000.000 Nanosekunden zu konvertieren und den Punkt subtrahiert.

``` syntax
<Region Guid="{7D6BA3F6-BC04-4776-8A7F-93CF7F4E2B6D}"
   Name="FastStartup-Suspend-WriteHiberFile"
   FriendlyName="Subscribers for Create Session">
   <Region Guid="{93783B2C-A67F-49cb-89BC-BF305D7E2CEA}"
         Name="FastStartup-Suspend-Winlogon-CreateSession-Subscribers-Child"
         FriendlyName="Hiberfile Write">
      <Start>
         <Duration Provider="{331c3b3a-2005-44c2-ac53-77220c37d6b4}" 
                   Id="117"
                   Version="0"
                   Duration="HiberHiberFileTime"
                   Multiplier="1000000" />
      </Start>
      <Stop>
         <Region RegionGuid="{EC1BB2D9-4AA8-4d82-84AA-6042FF4CFBE3}" />
      </Stop>
   </Region>
</Region>
```

### <a name="regions-based-on-other-regions"></a>Bereiche auf Grundlage von anderen Regionen

Sie können einen Bereich definieren, dessen Punkt starten und Anhalten von anderen Regionen definiert werden, mithilfe einer **Region** Knoten innerhalb der **Starten** oder **Beenden** . Dieser Region Knoten verfügt über ein Attribut obligatorisch, *RegionGuid*, der die GUID des den Zielbereich angibt.

Standardmäßig wird bei die ersten Punkt Region beendet ein Bereich, dessen Anfangspunkt auf einer anderen Region basiert, gestartet. Entsprechend wird eine Region, deren Punkt auf einer anderen Region basiert, beenden, wenn die Region des Öffnungsvorgangs Punkt beginnt. Sie können dieses Standardverhalten außer Kraft setzen, durch ein optionales Attribut, *Endpunkt*, an den Knoten Region hinzufügen. *Endpunkt* kann der Wert haben `Start` oder `Stop` und gibt den Endpunkt des Bereichs, der für das Starten oder Beenden-Ereignis verwenden.

### <a name="example"></a>Beispiel

Die folgende Region Definition enthält starten und Beenden von Punkten, die durch andere Bereiche definiert sind:

``` syntax
<Region Guid="{93783B2C-A67F-49cb-89BC-BF305D7E2CEA}"
        Name="FastStartup-Suspend-HiberInitTime"
        FriendlyName="Hiberfile Initialization">
   <Start>
      <Region RegionGuid="{5E81D74C-0CCC-43f9-8119-953F827BCD12}" />
   </Start>
   <Stop>
      <Region RegionGuid="{7D6BA3F6-BC04-4776-8A7F-93CF7F4E2B6D}" />
   </Stop>
</Region>
```

### <a name="a-href-idregions-within-regionsaregions-that-are-containers-of-other-regions"></a><a href="" id="regions-within-regions"></a>Bereiche, die von anderen Regionen Container sind

Bereiche, die anderen Regionen enthalten sind *Container*aufgerufen. Container starten, wenn die erste Instanz von einer enthaltenen Region wird gestartet, und sie beenden, wenn die letzte Instanz beendet. Diese Bereiche müssen keine anderen Attribute.

**RegionRoot** ist ein Container für alle Bereiche, die Sie definieren. Folglich beginnt **RegionRoot** auf, wenn die erste Instanz von einer Region wird gestartet, und es wird beendet, wenn die letzte Instanz einen Bereich beendet.

Um einen Containerbereich zu definieren, definieren Sie einfach einen Bereich ohne einen Ausgangspunkt oder einen Punkt.

### <a name="example"></a>Beispiel

Im folgenden Beispiel ist *Abonnenten für Create Session* ein Container für *Untergeordnete des Abonnenten des Sitzung erstellen*. Beachten Sie, dass *Abonnenten für Create Session* Ausgangspunkt oder einen Punkt nicht vorhanden ist. Gestartet, wenn die erste Instanz von einem untergeordneten Bereich beginnt wird und beendet, wenn die letzte Instanz eines Bereichs untergeordneter beendet.

``` syntax
<Region Guid="{A75D8F5D-E8F8-40b8-B453-5CC70DEAC06F}"
   Name="FastStartup-Suspend-Winlogon-CreateSession-Subscribers"
   FriendlyName="Subscribers for Create Session">
   <Region Guid="{93783B2C-A67F-49cb-89BC-BF305D7E2CEA}"
           Name="FastStartup-Suspend-Winlogon-CreateSession-Subscribers-Child"
           FriendlyName="Child of Subscribers for Create Session">
      <Start>
         <Region RegionGuid="{5E81D74C-0CCC-43f9-8119-953F827BCD12}" />
      </Start>
      <Stop>
         <Region RegionGuid="{7D6BA3F6-BC04-4776-8A7F-93CF7F4E2B6D}" 
                 Endpoint="Stop" />
      </Stop>
   </Region>
</Region>
```

### <a name="using-payload-fields-to-identify-events"></a>Verwenden von Nutzlast Feldern zur Identifizierung von Ereignissen

Oft sind die Eigenschaften von Ereignis-ID (Prozess-ID, Thread-ID und Aktivitäts-ID) nicht ausreicht, um bestimmte Szenarien zu identifizieren. Beispielsweise wenn ein Dienst gestartet wird, wird ein generisches Ereignis ausgelöst, möglicherweise nicht identifizieren welcher Dienst gestartet. In diesem Fall müssen Sie auf *Nutzlast Felder* für zusätzliche Informationen zurückgreifen. In diesem Fall sollte eine zusätzliche Felder den Namen enthalten. Diese Informationen können Sie weitere Region starten und Beenden von Punkt anzugeben.

Um Nutzlast Felder als zusätzliche Ereignis-IDs zu verwenden, fügen Sie einen oder mehrere **PayloadIdentifier** Knoten an einen Knoten **Starten** oder **Beenden** .

Der Knoten **PayloadIdentifier** hat die folgenden Attribute:

-   *FieldName* (erforderlich), den Namen des Felds Nutzlast.

-   *FieldValue* (erforderlich), den Wert der Nutzlast.

-   *FieldValueRelationship* (optional). Verwenden Sie **IsEqual** um anzugeben, dass das Ereignis den Nutzlast Wert enthalten muss. Verwenden Sie **DoesNotContain** , um anzugeben, dass das Ereignis nicht den Nutzlast Wert enthalten muss. Wenn dieses Attribut nicht angegeben wird, ist der Standardwert **IsEqual**.

**Hinweis**  
Nutzlast Felder Groß-/Kleinschreibung beachtet, und die XML-Definition muss vollständig den Nutzlast Wert entsprechen. Beispielsweise, wenn ein Nutzlastfeld Wert hat `00000`, muss auch die Region Definition angeben `00000` als Nutzlast Wert.

 

### <a name="example"></a>Beispiel

Das folgende Beispiel enthält **PayloadIdentifier** Knoten für den Ausgangspunkt und den Punkt:

``` syntax
<Region Guid="{AB719FB1-D863-4305-AE8E-F21281899A85}"
        Name="FastStartup-ConsoleSessionDisconnect"
        FriendlyName="Console Session Disconnect">
   <Start>
      <Event Provider="{dbe9b383-7cf3-4331-91cc-a3cb16a3b538}" Id="801" Version="0" />
      <PayloadIdentifier FieldName="Event" FieldValue="8" />
      <PayloadIdentifier FieldName="Key" FieldValue="00000" />
   </Start>
   <Stop>
      <Event Provider="{dbe9b383-7cf3-4331-91cc-a3cb16a3b538}" Id="802" Version="0" />
      <PayloadIdentifier FieldName="Event"
                         FieldValue="20"
                         FieldValueRelationship="DoesNotContain" />
   </Stop>
</Region>
```

### <a name="matching-events-for-regions"></a>Entsprechende Ereignisse für Regionen

WPA ermittelt Start-Ereignisse mit dem Beenden der Ereignisse von Formularbereichen in einem Prozess *übereinstimmenden Ereignis*aufgerufen. WPA versucht, auf der Ebene des Ereignisses eine einzelne starten oder Beenden-Ereignis basierend auf der Provider-ID, Ereignis-ID, Version des Ereignisses und alle zusätzlichen angegebenen Nutzlast Felder übereinstimmen.

Abgleich kann auch auf Regionsebene Kriterien angegeben erweitert werden, die von der starten und beenden Punkt erfüllt sein müssen. Ebene der Region können Sie festlegen, dass beide Punkte passenden Thread-IDs, -IDs und Aktivitäts-IDs zu verarbeiten. Darüber hinaus können Sie auch Nutzlast Kriterien auf der Regionsebene definieren.

Sie können die Region auf Dokumentebene Abgleich werden durch einen Knoten **Übereinstimmung** innerhalb der **Region** Knoten einschließlich verwenden. Der **Übereinstimmung** -Knoten enthält einen untergeordneten Knoten **Ereignis**, das eine beliebige Kombination der folgenden Attribute haben kann:

-   `TID="true"`– erfordern übereinstimmenden Thread-IDs

-   `PID="true"`– erfordern übereinstimmenden Prozess-IDs

-   `AID="true"`– Vergleich Aktivität IDs erfordern

Der Knoten **Ereignis** kann es sich um einen optionalen **Nutzlast** untergeordneten Knoten aufweisen, der ein *FieldName* -Attribut enthält. Dieser Knoten erfordert, dass sowohl das Starten und Beenden von Knoten für die angegebene *FieldName*übereinstimmenden Nutzlast Werte enthalten.

Alternativ kann der **Nutzlast** Knoten auch ein optionales Attribut, *TargetFieldName*enthalten. Wenn dieses Attribut angegeben ist, klicken Sie dann entspricht *FieldName* an ein Nutzlastfeld nur in den Startknoten, während *TargetFieldName* an ein Nutzlastfeld im Knoten Öffnungsvorgangs entspricht.

### <a name="example"></a>Beispiel

Im folgenden Beispiel wird forms eine Region, wenn das Startdatum-Ereignis ein Felds Nutzlast, *folgende*, enthält, deren Wert, der im Knoten Öffnungsvorgangs die Nutzlast-Felds- *Client entspricht*. Die Ereignisse starten und anhalten müssen außerdem übereinstimmenden Thread-IDs.

``` syntax
<Region Guid="{A75D8F5D-E8F8-40b8-B453-5CCC70DEAC06F}"
        Name="FastStartup-Suspend-Winlogon-CreateSession-Subscribers"
        FriendlyName="Subscribers for Create Session">
   <Start>
      <Event Provider="{dbe9b383-7cf3-4331-91cc-a3cb16a3b538}" Id="805" Version="0" />
      <PayloadIdentifier FieldName="Event" FieldValue="0" />
   </Start>
   <Stop>
      <Event Provider="{dbe9b383-7cf3-4331-91cc-a3cb16a3b538}" Id="806" Version="0" />
      <PayloadIdentifier FieldName="Event" FieldValue="0" />
   </Stop>
   <Match>
      <Event TID="true">
         <Payload FieldName="SubscriberName" TargetFieldName="Client" />
      </Event>
   </Match>
</Region>
```

### <a name="filtering-a-region-based-on-a-condition"></a>Filtern einer Region auf der Grundlage einer Bedingung

WPA kann ein- oder ausschließen eine Region basierend auf einer Bedingung oder *Trigger*, was kann ein Ereignis oder eine andere Region. Der Trigger in einem **Filter** -Element angegeben ist, und die Region, die **Filter** enthält, ist das *Ziel*.

Wenn der Trigger eine *Region*ist, muss **Filter** die Bereichs-ID enthalten

Wenn Sie der Auslöser ist ein *Ereignis*, und klicken Sie dann **Filter** muss ein **Ereignis** Element mit der *ProviderId* ETW-Anbieter und einem oder mehreren der folgenden Attribute enthalten: *Id*, *Version*, *OpCode*und *Typ*.

*-ID* und *Versionsnummer* werden weiter oben in der [Region-Typen](#region-types)beschrieben. *OpCode* ist zugewiesene Wert, die Sie auswählen. *Typ* gibt den Modus der Filterung von der gewünschten Region, ein- oder Ausschließen von basierend auf die Bedingungen in der folgenden Tabelle beschrieben.

| Typ des Filters | Beschreibung                                                                                          |
|----------------|------------------------------------------------------------------------------------------------------|
| Aus            | Schließen Sie den Zielbereich ein, wenn Sie auslösenden Ereignis oder Region gefunden wird.                              |
| OutPost        | Schließen Sie den Zielbereich ein, wenn Sie das Ziel nach der letzten auslösende Ereignis oder einer Region aufgetreten ist. |
| OutPrev        | Schließen Sie den Zielbereich, wenn das Ziel des Vorgangs vor dem ersten auslösende Ereignis oder eine Region ist aufgetreten.    |
| In             | Enthalten Sie den Zielbereich nur, wenn das auslösende Ereignis oder Region gefunden wird.                         |
| InPost         | Enthalten Sie den Zielbereich nur, wenn sie nach dem letzten auslösende Ereignis oder eine Region ist aufgetreten.    |
| InPrev         | Enthalten Sie den Zielbereich nur, wenn sie vor der ersten auslösende Ereignis oder einer Region aufgetreten ist.       |


### <a name="parent-child-relationships"></a>Über-und untergeordneten Elementen

Sie können eine Region in einer anderen So erstellen Sie eine hierarchische Beziehung definieren. Für eine Region für eine übergeordnete sein benötigen sie eine Startzeit, die einer älteren Version als oder gleich dem Anfangszeitpunkt der untergeordneten Region ist. Es muss auch eine Endzeit verfügen, liegen oder Endzeit der untergeordneten Region gleich ist. Diese Bedingung nicht erfüllt sind, kann keine hierarchische Beziehung gebildet werden.

Verwenden Sie zum Angeben von zusätzlicher Kriterien für einen übergeordneten Bereich den **übergeordneten** Knoten in einem **Übereinstimmung** -Knoten. Der **übergeordnete** Knoten hat die gleichen Attribute und untergeordneten Knoten als **Ereignis** Knoten in Region auf Dokumentebene übereinstimmenden verwendet. Sie können angeben, dass die übergeordnete und untergeordnete Regionen die gleichen Thread-ID, die Prozess-ID, Aktivitäts-ID und eine beliebige Anzahl von übereinstimmenden Nutzlast Felder sein müssen.

Wenn Nutzlast Feldern verwenden Sie nur das *FieldName* -Attribut angeben, müssen die über- und untergeordnete Regionen übereinstimmende Werte für dieses Feld Nutzlast verfügen. Wenn Sie auch das *TargetFieldName* -Attribut angeben, gilt das Attribut *TargetFieldName* auf das übergeordnete Element als auch das untergeordnete Element, was bedeutet, dass die untergeordneten Region einen Nutzlast-Wert für das Feld *FieldName* sein muss, die mit den Nutzlast Wert für das Feld *TargetFieldName* im übergeordneten Element übereinstimmt.

Wenn ein untergeordnetes Element mehr als eine potenzielle übergeordnetes Objekt ist, wird das übergeordnete Element mit der frühesten Startzeit ausgewählt.

### <a name="example"></a>Beispiel

Das folgende Beispiel definiert die Kriterien für ein übergeordnetes Element. Übergeordneten benötigen eine übereinstimmenden Thread-ID und einen Wert Nutzlast für die `SubscriberName` Feld in der untergeordneten muss einen Wert für entsprechen der `Client` das übergeordnete Feld.

``` syntax
<Region Guid="{A75D8F5D-E8F8-40b8-B453-5CC70DEAC06F}"
        Name="FastStartup-Suspend-Winlogon-CreateSession-Subscribers"
        FriendlyName="Subscribers for Create Session">
   <Start>
      <Event Provider="{dbe9b383-7cf3-4331-91cc-a3cb16a3b538}" Id="805" Version="0" />
      <PayloadIdentifier FieldName="Event" FieldValue="0" />
   </Start>
   <Stop>
      <Event Provider="{dbe9b383-7cf3-4331-91cc-a3cb16a3b538}" Id="806" Version="0" />
      <PayloadIdentifier FieldName="Event" FieldValue="0" />
   </Stop>
   <Match>
      <Event TID="true">
         <Payload FieldName="SubscriberName" TargetFieldName="Client" />
      </Event>
      <Parent TID="true">
         <Payload FieldName="SubscriberName" TargetFieldName="Client" />
      </Parent>
   </Match>
</Region>
```

### <a name="self-nesting-regions"></a>Self Schachtelung von Regionen

*Schachtelung von sich selbst* ist eine optionale Funktion, die über-und untergeordneten Elementen optimiert.

Ist eine *Self schachteln Region* , deren Dauer vollständig in die Dauer einer Region gleichgeordneten Knoten enthalten ist. Diese Region wird effektiv ein untergeordnetes Element seines länger dauerhaften nebengeordneten.

Nehmen wir beispielsweise an, dass für die folgenden Bereiche Self schachteln aktiviert ist:

-   Das übergeordnete Region A

-   Untergeordnete Bereich B1, dem Zeitpunkt 0 startet und beendet Zeitpunkt 6

-   Untergeordnete Region B2, dem Zeitpunkt 2 startet und beendet Zeitpunkt 5

-   Untergeordnete Region B3, dem Zeitpunkt 3 startet und beendet Zeitpunkt 4

In diesem Beispiel B2 wird einen untergeordneten Bereich B1 und B3 wird einen untergeordneten Bereich B2. Wenn Sie diese Art von übergeordneten und untergeordneten Beziehung erstellen, wird das übergeordnete Element mit der Startzeit die Startzeit des untergeordneten am nächsten ausgewählt.

Zum Aktivieren von Self schachteln fügen Sie **SelfNest** Knoten innerhalb der **Übereinstimmung** Knoten hinzu.

Der Knoten **SelfNest** hat keine erforderlichen Parameter. Jedoch dieselbe übereinstimmende Parameter können, die zum Erstellen der normalen über-und untergeordneten Elementen verwendet werden. Weitere Informationen finden Sie weiter oben in diesem Thema **über-und untergeordneten Elementen** .

### <a name="examples"></a>Beispiele

Das folgende Beispiel definiert einen **Übereinstimmung** -Tag, der einfach Self schachteln aufruft:

``` syntax
<Match>
   <SelfNest />
</Match>
```

Das folgende Beispiel definiert eine komplexere Self schachteln Szenarios, in dem erfordert passenden Thread-IDs und Nutzlast Felder:

``` syntax
<Match>
   <SelfNest TID="true">
      <Payload FieldName="SubscriberName" />
   </SelfNest>
</Match>
```

### <a name="instance-names"></a>Instanznamen

Sie können einen eindeutigen Namen für jede Instanz einer übereinstimmenden Region mithilfe des Knotens **Naming** zuweisen. Benennung ist nützlich, wenn Sie eine große Anzahl von Instanzen des gleichen Bereichs oder Regionen auf Grundlage anderer Kriterien kategorisiert werden sollen. Instanznamen können entweder Nutzlast Feld oder auf Beziehungen mit anderen Regionen basieren.

Instanzen können heißen basierend auf Nutzlast Werte mithilfe des **PayloadBased** -Knotens in einem **Naming** -Knoten. Den **PayloadBased** -Knoten ist ein erforderliches Attribut, *Feld*, die das Nutzlastfeld gibt an, deren Werte, die Sie als Instanznamen verwenden möchten. Diese Felder Nutzlast können in Start- oder Endpunkt für den Bereich sein.

Es folgt ein Beispiel einer Region mit einem Nutzlast basierenden **Naming** Knoten:

``` syntax
<Region Guid="{9261872F-D3A7-4d80-BDE3-8479CC920639}"
        Name="FastStartup-Suspend-Winlogon-EndShell-CallSubscriber"
        FriendlyName="Call Subscriber for End Shell">
   <Start>
      <Event Provider="{dbe9b383-7cf3-4331-91cc-a3cb16a3b538}" Id="811" Version="0" />
      <PayloadIdentifier FieldName="Event" FieldValue="13" />
   </Start>
   <Stop>
      <Event Provider="{dbe9b383-7cf3-4331-91cc-a3cb16a3b538}" Id="812" Version="0" />
      <PayloadIdentifier FieldName="Event" FieldValue="13" />
   </Stop>
   <Match>
      <Event PID="true" />
      <Parent PID="true" />
   </Match>
   <Naming>
      <PayloadBased NameField="SubscriberName" />
   </Naming>
</Region>
```

Im vorstehenden Beispiel gibt der Knoten **Naming** an, dass das Starten oder Beenden-Ereignis ein Nutzlastfeld Namens enthält `SubscriberName`. Für jede Instanz der Region, die erstellt wird, ist der Name der Instanz der zugeordneten Nutzlast Wert.

**Hinweis**  
Beim Benennen von Instanzen Region überprüft WPA zuerst das Start--Ereignis für das entsprechende Nutzlastfeld. Wenn eine nicht gefunden wird, wird WPA klicken Sie dann auf Beenden-Ereignis für das Nutzlastfeld gesucht. Wenn eine Übereinstimmung in jedem Fall nicht gefunden wird, wird ein Fehler in der Konsole gedruckt.

 

Manchmal ist die Informationen in der Nutzlast nicht nur wir die gewünschten Informationen. Wenn die Informationen in der Nutzlast enthaltenen Geräte-ID ist, können wir diese Informationen wieder dem Gerät Beschreibung und Namen zuzuordnen. Unterstützte *Typ* Attribute sind:

-   `Device`, ordnet einen Namen und eine Beschreibung

-   `GUID`, ordnet die GUID der Region

-   `CLSID`, ordnet einen Klassennamen, um die Klassen-ID

-   `PID`, die Region ordnet den Namen des Prozesses

``` syntax
<Naming>
   <PayloadBased NameField="SubscriberName" Type="Device" />
</Naming>
```

Wenn es für den Wert Nutzlast im Rahmen sowohl das Starten und Beenden von Punkten möglich ist, können Sie das optionale *InstanceEndpoint* -Attribut verwenden, an denen zeigen Sie auf verwenden. Mögliche Werte für *InstanceEndpoint* `Start` und `Stop`.

``` syntax
<Naming>
   <PayloadBased NameField="SubscriberName" InstanceEndpoint="Start" />
</Naming>
```

Sie können auch eine Region basierend auf Beziehungen mit anderen Regionen Namen. Um eine andere Region zuzuordnen, fügen Sie einen Knoten **RegionBased** eine **Naming** Knoten hinzu. Der Knoten **RegionBased** besteht aus vier erforderlichen Attribute:

-   *RegionGuid*, die GUID der der jeweiligen Region.

-   *Relation*, ein bedingter Wert, der beschreibt die Beziehung zwischen der Region, die Sie definieren und die Region, die Sie zuordnen möchten. Derzeit ist die einzige unterstützte Beziehung `IsPresent`, was bedeutet, dass die bedingte ist True, wenn die jeweiligen Region an einer beliebigen Stelle in der Verfolgung gefunden wird.

-   *IfRelationTrue*, String-Wert, der als den Namen der Instanz verwendet wird, wenn die Beziehung von *Relation* beschrieben auf true festgelegt ist.

-   *IfRelationFalse*, String-Wert, der als den Namen der Instanz verwendet wird, wenn die Beziehung von *Relation* beschriebenen false ist.

Das folgende Beispiel definiert einen Bereich, der Benennung bereichsspezifische hat. Wenn eine Region mit einer übereinstimmenden GUID irgendwo in die Ablaufverfolgung, und klicken Sie dann auf jede Instanz von gefunden wird `Launch` heißt `Warm`. Andernfalls wird jede Instanz namens `Cold`.

``` syntax
<Region Guid="{C99EFA90-F645-4A24-9576-740351171BD0}"
        Name="WinStoreAppActivationDuration"
        FriendlyName="Launch">
   <Start>
      <Event Provider="{315a8872-923e-4ea2-9889-33cd4754bf64}" Id="5901" Version="0" />
      <PayloadIdentifier FieldName="SqmableContractID" FieldValue="Windows.Launch" />
   </Start>
   <Stop>
      <Event Provider="{315a8872-923e-43a2-9889-33cd4754bf64}" Id="5902" Version="0" />
      <PayloadIdentifier FieldName="SqmableContractID" FieldValue="Windows.Launch" />
   </Stop>
   <Match>
      <Event PID="true" />
   </Match>
   <Naming>
      <RegionBased RegionGuid="{1539A93E-129C-4602-A011-431E7F73A353}" Relation="IsPresent" IfRelationTrue="Warm" IfRelationFalse="Cold" />
   </Naming>
</Region>
```

**Hinweis**  
Sie können in WPA Instanznamen durch Bewegen der Maus über eine Region-Instanz im Diagramm Regionen von Interesse sehen.

 

### <a name="metadata"></a>Metadaten

Sie können zusätzliche Informationen zur Definition einer Region in Form von *Metadaten*, innerhalb einer **Metadaten** -Knoten hinzufügen. Beispielsweise können Sie Informationen in den Metadaten einschließen, die die Kriterien für die Region, damit ein anderer Benutzer den Zweck des Bereichs leichter verstehen, welche erklärt. Metadaten ist einfach zusätzliche Daten – es hat keinen Einfluss auf die Verarbeitung von Regionen.

WPA fügt diese Metadaten für jede Region-Instanz in der Diagrammansicht des Diagramms Regionen von Interesse. Zum Anzeigen von Metadaten für übereinstimmenden Ereignisse in WPA, erweitern Sie den Bereich in die Diagrammansicht und einfach auf die gewünschte Metadaten. WPA weist eine eindeutige Nummer auf die Metadaten und der Namen des Knotens als die Spalteninformationen angezeigt wird.

### <a name="example"></a>Beispiel

Das folgende Beispiel enthält einen **Metadaten** -Knoten in der Definition der Region:

``` syntax
<Region Guid="{F466EE67-192C-4772-B13D-052CCD2D70B3}"
        Name="FastStartup-Suspend-Winlogon-Logoff-Subscribers"
        FriendlyName="Subscribers for Logoff">
   <Start>
      <Event Provider="{dbe9b383-7cf3-4331-91cc-a3cb16a3b538}" Id="805" Version="0" />
      <PayloadIdentifier FieldName="Event" FieldValue="3" />
   </Start>
   <Stop>
      <Event Provider="{db39b383-7cf3-4331-91cc-a3cb16a3b538}" Id="806" Version="0" />
      <PayloadIdentifier FieldName="Event" FieldValue="3" />
   </Stop>
   <Match>
      <Event>
         <Payload FieldName="Event" />
      </Event>
   </Match>
   <Naming>
      <PayloadBased NameField="SubscriberName" />
   </Naming>
   <Metadata>
      <FAS.TestNode>yes</FAS.TestNode>
   </Metadata>
</Region>
```

## <a name="related-topics"></a>Verwandte Themen


[Interessante Bereiche](regions-of-interest.md)

[WPA-Features](wpa-features.md)

 

 







