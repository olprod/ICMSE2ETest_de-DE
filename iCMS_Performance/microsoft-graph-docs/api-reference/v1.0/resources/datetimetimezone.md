# <a name="datetimetimezone-resource-type"></a>Ressourcentyp dateTimeTimeZone

Beschreibt das Datum, Uhrzeit und Zeitzone eines Punkts in der Zeit.

## <a name="properties"></a>Eigenschaften
| Eigenschaft     | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|DateTime|String|Eine zentrale Stelle Zeit in eine kombinierte Datums- und zeitdarstellung (`<date>T<time>`).|
|Zeitzone|String|Einer der folgenden Zeitzone Namen.|


Die _TimeZone_ -Eigenschaft kann eine der von Windows als auch die folgenden Namen von Zeitzonen unterstützt Zeitzonen festgelegt werden.

Etc/GMT + 12

Etc/GMT + 11

Pacific/Honolulu

America/Verankerung

America/Santa_Isabel

America/Los_Angeles

America/Phoenix

America/Chihuahua

America/Denver

America/Guatemala

America/Chicago

America/Mexiko

America/Regina

America/Bogotá

America/New_York

America/Indiana/Indianapolis

America/Caracas

America/Asuncion

America/Halifax

America/Cuiaba

America/La_Paz

America/Santiago

America/St_Johns

America/Sao_Paulo

America/Argentinien/Buenos_Aires

America/Cayenne

America/Godthab

America/Montevideo

America/Bahia

Etc/GMT + 2

Atlantic/Azoren

Atlantic/Cape_Verde

Afrika/Casablanca

Etc/GMT

Europa/London

Atlantic/Reykjavik

Europa/Berlin

Europa/Budapest

Europa/Paris

Europa/Warschau

Afrika/Lagos

Afrika/Windhuk

Europa/Bukarest

Asien/Beirut

Afrika/Kairo

Asien/Damaskus

Afrika/dezentral eingesetzt.

Europa/Kiew

Europa/Istanbul

Asien/Jerusalem

Asien/Amman

Asien/Bagdad

Europa/Kaliningrad

Asien/Riad

Afrika/Nairobi

Asien/Teheran

Asien/Dubai

Asien/Baku

Europa/Moskau

Indisch/Mauritius

Asien/Tiflis

Asien/Eriwan

Asien/Kabul

Asien/Karatschi

Asien/Taschkent

Asien/Kolkata

Asien/Colombo

Asien/Katmandu

Asien/Almaty

Asien/Dakka

Asien/Jekaterinburg

Asien/Rangun

Asien/Bangkok

Asien/Nowosibirsk

Asien/Shanghai

Asien/Krasnojarsk

Asien/Singapur

Australien/Perth

Asien/Taipeh

Asien/Ulan-Bator

Asien/Irkutsk

Asien/Tokio

Asien/Seoul

Australien/Adelaide

Australien/Darwin

Australien/Brisbane

Australien/australische

Pacific/Port_Moresby

Australien/Hobart

Asien/Jakutsk

Pacific/Guadalcanal

Asien/Wladiwostok

Pacific/Auckland

Etc/GMT-12

Pacific/Fidschi

Asien/Magadan

Pacific/Tongatapu

Pacific/Apia

Pacific/Kiritimati

## <a name="json-representation"></a>JSON-Darstellung

Es folgt eine JSON-Darstellung der Ressource

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.dateTimeTimeZone"
}-->

```json
{
  "dateTime": "string",
  "timeZone": "string"
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "dateTimeTimeZone resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
