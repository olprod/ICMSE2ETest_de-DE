# <a name="outlook-extended-properties-overview"></a>Outlook erweiterte Eigenschaften (Übersicht)

Erweiterte Eigenschaften können Speichern benutzerdefinierter Daten und insbesondere dienen als ein Sicherungsmechanismus für apps Zugriff auf benutzerdefinierte Daten für Outlook-MAPI-Eigenschaften beim diese Eigenschaften _in der Microsoft Graph-API-Metadaten noch nicht verfügbar gemacht_werden. Erweiterte Eigenschaften REST-API können Sie speichern oder eine solche benutzerdefinierten Daten in den folgenden Benutzerressourcen erhalten:

- [Nachricht](../resources/message.md)
- [mailFolder](../resources/mailfolder.md)
- [Ereignis](../resources/event.md)
- [Kalender](../resources/calendar.md)
- [Wenden Sie sich an](../resources/contact.md)
- [contactFolder](../resources/contactfolder.md) 

Oder in den folgenden Office 365 Gruppieren von Ressourcen:

- Gruppe- [Ereignis](../resources/event.md)
- Gruppe [Kalender](../resources/calendar.md)
- Gruppe [Buchen](../resources/post.md) 

## <a name="use-extended-properties-or-office-365-data-extensions"></a>Verwenden Sie erweiterte Eigenschaften oder Office 365 Daten Extensions?

In den häufigsten Szenarien sollten Sie möglicherweise Office 365 Daten Extensions (dargestellt durch [OpenTypeExtension](../resources/opentypeextension.md)) verwenden, um benutzerdefinierte Daten für die Ressourceninstanzen im Postfach des Benutzers. Verwenden Sie erweiterte Eigenschaften nur, wenn Sie benutzerdefinierte Daten für Outlook-MAPI-Eigenschaften zugreifen, die nicht bereits in den [Microsoft Graph-API-Metadaten](http://graph.microsoft.io/en-us/docs/overview/call_api)verfügbar gemacht werden müssen.

## <a name="types-of-extended-properties"></a>Typen von erweiterten Eigenschaften

Je nachdem, ob Sie eine einzelne oder mehrere Werte (des gleichen Typs) in einer erweiterten Eigenschaft speichern möchten können Sie eine erweiterte Eigenschaft als [SingleValueLegacyExtendedProperty](../resources/singleValueLegacyExtendedProperty.md)oder [MultiValueLegacyExtendedProperty](../resources/multiValueLegacyExtendedProperty.md)erstellen.

Jeder dieser Typen bezeichnet die Eigenschaft durch seine **Id** und speichert die Daten in **Wert**. 

**Id** können Sie eine bestimmte Ressource-Instanz zusammen mit erweiterten Eigenschaft erhalten möchten, oder auf einem erweiterten Eigenschaft, um alle Instanzen abzurufen, die diese Eigenschaft verfügen Single-Wert gefiltert. 

**Hinweis** Sie können nicht die REST-API verwenden, um die erweiterten Eigenschaften einer bestimmten Instanz durch Aufrufen abzurufen.
  

## <a name="id-formats"></a>ID-Formate

Wenn Sie eine erweiterte Eigenschaft einwertig oder mit mehreren Werte zu erstellen, können Sie **Id** in einem der folgenden beiden Formate, basierend auf einem Zeichenfolgennamens oder numerischen Bezeichner und dem tatsächlichen Typ eines Werte der Eigenschaft angeben. Da erweiterte Eigenschaften in den meisten Fällen Konfigurationsrichtlinien Betrieb mit definierten MAPI-Eigenschaften in der Microsoft Graph-API-Metadaten zur Vereinfachung nicht verfügbar gemacht werden sollte das Format aus, das Sie auswählen, ob die entsprechende MAPI-Eigenschaft Zeichenfolge oder eines numerischen Wert eines Zeichens in der [MAPI-Eigenschaftenbezeichner](https://msdn.microsoft.com/en-us/library/office/cc815528.aspx)verwendet widerspiegeln.

**Hinweis** Nachdem Sie ein Format für die **Id**ausgewählt haben, sollten Sie nur dieses Format erweiterte Eigenschaft zugreifen.


**Gültige Id Formate für Einzelwert-erweiterte Eigenschaften**

|**Format**|**Beispiel**|**Beschreibung**|
|:---------|:----------|:--------------|
| "*{_type_} {_guid_} **Name** {_name_}*" | ```"String {8ECCC264-6880-4EBE-992F-8888D2EEAA1D} Name TestProperty"``` | Identifiziert eine Eigenschaft durch den Namespace (die GUID), zu der sie gehört, und einen Namen.         |
| "*{_type_} {_guid_} **Id** {_id_}*"     | ```"Integer {8ECCC264-6880-4EBE-992F-8888D2EEAA1D} Id 0x8012"```        | Identifiziert eine Eigenschaft durch den Namespace (die GUID), zu der sie gehört, und ein Bezeichner.  |


**Gültige Id Formate für erweiterte Eigenschaften mit mehreren Werten**

|**Format**|**Beispiel**|**Beschreibung**|
|:---------|:----------|:--------------|
| "*{_type_} {_guid_} **Name** {_name_}*" | ```"StringArray {8ECCC264-6880-4EBE-992F-8888D2EEAA1D} Name TestProperty"``` | Identifiziert eine Eigenschaft Namespace (die GUID) und Name.         |
| "*{_type_} {_guid_} **Id** {_id_}*"     | ```"IntegerArray {8ECCC264-6880-4EBE-992F-8888D2EEAA1D} Id 0x8013"```        | Identifiziert eine Eigenschaft von Namespace (die GUID) und Bezeichner.   |


## <a name="rest-api-operations"></a>REST-API-Vorgänge
 
Single-Wert der erweiterten Eigenschaft Vorgänge:
- [Erstellen einer erweiterten Eigenschaft in einer Ressourceninstanz einer neuen oder vorhandenen](../api/singlevaluelegacyextendedproperty_post_singlevalueextendedproperties.md)
- [Rufen Sie eine oder eine Auflistung von Resource-Instanzen mit einer erweiterten Eigenschaft mit `$expand` oder`$filter`](../api/singlevaluelegacyextendedproperty_get.md)

Erweiterte Eigenschaft Mehrfachwert Vorgänge:
- [Erstellen einer erweiterten Eigenschaft in einer Ressourceninstanz einer neuen oder vorhandenen](../api/multivaluelegacyextendedproperty_post_multivalueextendedproperties.md)
- [Eine Ressourceninstanz mit einer erweiterten Eigenschaft abrufen`$expand`](../api/multivaluelegacyextendedproperty_get.md)

