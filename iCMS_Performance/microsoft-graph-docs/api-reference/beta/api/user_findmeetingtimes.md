# <a name="user-findmeetingtimes"></a>Benutzer: FindMeetingTimes
Hier finden Sie Besprechungstermin basierend auf Organisator und Teilnehmer Verfügbarkeit, und die Uhrzeit oder Speicherort Einschränkungen, die als Parameter angegeben.

Wenn **FindMeetingTimes** Besprechungsvorschläge zurückgeben kann, würde die Antwort einen Grund in der **EmptySuggestionsHint** -Eigenschaft angeben. Anhand dieses Werts, können Sie besser passen Sie die Parameter und erneut **FindMeetingTimes** aufrufen.

**Hinweis**

Derzeit **FindMeetingTimes** wird Folgendes vorausgesetzt:

- Alle [Teilnehmer](../resources/attendee.md) , die eine (im Gegensatz zu einer Ressource Person) ist ein Erforderlicher Teilnehmer. Geben Sie also `required` einer Person und `resource` für eine Ressource in der entsprechenden **Typ** -Eigenschaft im Rahmen des Parameters-Auflistung **Teilnehmer** .
- Alle besprechungsvorschlag tritt auf, während nur den Arbeitsstunden der Organisator oder einem Teilnehmer. Sie können ignorieren, die **ActivityDomain** -Eigenschaft des einer [TimeConstraint](../resources/timeConstraint.md)angeben. 


## <a name="prerequisites"></a>Voraussetzungen
Die folgenden **Bereiche** sind erforderlich, um diese API ausführen: *Calendars.Read*
## <a name="http-request"></a>HTTP-Anforderung
<!-- { "blockType": "ignored" } -->
```http
POST /me/findMeetingTimes
POST /users/<id|userPrincipalName>/findMeetingTimes
```
## <a name="request-headers"></a>Anforderungsheader
| Name       | Wert|
|:---------------|:----------|
| Autorisierung  | Bearer<code>|
| Lieber: outlook.timezone | Eine Zeichenfolge zur Darstellung einer bestimmten Zeitzone für die Antwort ein, beispielsweise "Pazifik Normalzeit". |


## <a name="request-body"></a>Anforderungstext
Alle unterstützten Parameter sind wie folgt: Geben Sie je nach Szenario ein JSON-Objekt für jeden erforderlichen Parameter im Textkörper Anforderung. Auf Grundlage der angegebenen Parameter, überprüft**FindMeetingTimes** den Status Frei/Gebucht-Informationen in der primären Kalender der Organisator und Teilnehmer. Die Aktion berechnet die bestmögliche Besprechungszeiten und Besprechungsvorschläge zurück.


| Parameter    | Typ   |Beschreibung|
|:---------------|:--------|:----------|
|Teilnehmer|[AttendeeBase](../resources/attendeebase.md) -Auflistung|Eine Auflistung von Teilnehmern oder Ressourcen für die Besprechung. Eine leere Auflistung bewirkt, dass **FindMeetingTimes** kostenlos Zeitfenster nur den Organisator gesucht.|
|locationConstraint|[locationConstraint](../resources/locationconstraint.md)|Der Organisator Anforderungen über den Speicherort für die Besprechung, z. B., ob Vorschläge für einen Besprechungsort ist erforderlich, oder es sind bestimmte Speicherorte nur, in dem die Besprechung stattfinden kann.|
|timeConstraint|[timeConstraint](../resources/timeconstraint.md)|Die Start- und Endzeit Zeitraum in dem Besprechung werden sollen. Sie können eine Zeitzone als Teil der **start** und **End** -Eigenschaften für diesen Parameter angeben. Diese Zeitzone betrifft jedoch nur den Parameter **TimeConstraint** . die Zeitwerte in der Antwort zurückgegeben werden, noch in UTC standardmäßig. Sie können die `Prefer: outlook.timezone` Anforderungsheader an einer bestimmten Zeitzone für die Zeitwerte in der Antwort. |
|meetingDuration|Edm.Duration|Die Länge der Besprechung im Format [ISO8601](http://www.iso.org/iso/iso8601) gekennzeichnet. 1 Stunde wird beispielsweise als "PT1H", wobei "P" der Dauer Kennzeichner ist, gekennzeichnet ' t ' wird der Kennzeichner Zeit "H" wird die Stunde-Kennzeichner verwendet werden. Wenn keine Besprechungsdauer angegeben wird, wird **FindMeetingTimes** 30 Minuten wird den Standardwert verwendet. |
|maxCandidates|Edm.Int32|Die maximale Anzahl der Besprechung Zeit Vorschläge zurückgegeben werden soll.|
|isOrganizerOptional|Edm.Boolean|`True`Wenn der Organisator Anwesenheit nicht notwendig ist, `false` andernfalls.|
|returnSuggestionHints|Edm.Boolean|`True`Um einen Grund für jeden besprechungsvorschlag in der **SuggestionHint** -Eigenschaft zurückzugeben. Der Standardwert ist `false` diese Eigenschaft nicht zurückgegeben.|

## <a name="response"></a>Antwort
Wenn der Vorgang erfolgreich war, gibt diese Methode `200, OK` Antwortcode und eine [MeetingTimeCandidatesResult](../resources/meetingtimecandidatesresult.md) im Antworttext. 

Ein **MeetingTimeCandidatesResult** enthält eine Auflistung von Besprechungsvorschläge und eine **EmptySuggestionsHint** -Eigenschaft. Jeder Vorschlag ist definiert als eine [MeetingTimeCandidate](../resources/meetingtimecandidate.md)mit Teilnehmern, da auf den Mittelwert einer Confidence Level der Möglichkeit von 50 % oder höher für die Teilnahme an. 

Standardmäßig wird jedes Mal Besprechung Vorschlag in UTC zurückgegeben. 

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird gezeigt, wie Zeit zum erfüllen an einem vordefinierten Speicherort, und fordern Sie einen Grund für jeden einzelnen Vorschlag durch angeben die folgenden Parameter im Anforderungstext suchen:

- **Teilnehmer**
- **locationConstraint**
- **timeConstraint**
- **meetingDuration**
- **returnSuggestionHints**

Durch Festlegen des Parameters **ReturnSuggestionHints** , erhalten Sie auch eine Erläuterung der **SuggestionHint** -Eigenschaft für jeden einzelnen Vorschlag **FindMeetingTimes** Vorschläge zurück.

Beachten Sie, dass die Anforderung Zeit in die PST-Zeitzone und die Antwort gibt Besprechungstermin in UTC, standardmäßig angibt. Sie können die `Prefer: outlook.timezone` Anforderungsheader PST-Datei als auch für die Zeitwerte in der Antwort angeben.

##### <a name="request"></a>Anforderung
Nachfolgend finden Sie die beispielanforderung.
<!-- {
  "blockType": "request",
  "name": "user_findmeetingtimes"
}-->
```http
POST https://graph.microsoft.com/beta/me/findMeetingTimes


{ 
  "attendees": [ 
    { 
      "type": "required",  
      "emailAddress": { 
        "address": "alexd@contoso.onmicrosoft.com" 
      } 
    } 
  ],  
  "locationConstraint": { 
    "isRequired": "false",  
    "suggestLocation": "false",  
    "locations": [ 
      { 
        "displayName": "Conf room Hood" 
      } 
    ] 
  },  
  "timeConstraint": { 
    "timeslots": [ 
      { 
        "start": { 
          "date": "2016-06-20",  
          "time": "7:00:00",  
          "timeZone": "Pacific Standard Time" 
        },  
        "end": { 
          "date": "2016-06-20",  
          "time": "17:00:00",  
          "timeZone": "Pacific Standard Time" 
        } 
      } 
    ] 
  },  
  "meetingDuration": "PT2H",
  "returnSuggestionHints": "true"
}
```

##### <a name="response"></a>Antwort
Es folgt eine Beispielantwort. Hinweis: Das hier gezeigte Response-Objekt der Kürze halber werden möglicherweise abgeschnitten. Alle Eigenschaften werden aus einem tatsächlichen Aufruf zurückgegeben.
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.meetingTimeCandidatesResult",
  "isCollection": false
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json


{
   "@odata.context":"https://graph.microsoft.com/beta/$metadata#microsoft.graph.meetingTimeCandidatesResult",
   "meetingTimeSlots":[
      {
         "meetingTimeSlot":{
            "start":{
               "date":"2016-06-20",
               "time":"15:00:00.0000000",
               "timeZone":"UTC"
            },
            "end":{
               "date":"2016-06-20",
               "time":"17:00:00.0000000",
               "timeZone":"UTC"
            }
         },
         "confidence":100,
         "organizerAvailability":"free",
         "attendeeAvailability":[
            {
               "attendee":{
                  "type":"required",
                  "emailAddress":{
                     "address":"alexd@contoso.onmicrosoft.com"
                  }
               },
               "availability":"free"
            }
         ],
         "locations":[
            {
               "displayName":"Conf room Hood"
            }
         ],
         "suggestionHint":"Suggested because it is one of the nearest times when all attendees are available."
      },
      {
         "meetingTimeSlot":{
            "start":{
               "date":"2016-06-20",
               "time":"17:00:00.0000000",
               "timeZone":"UTC"
            },
            "end":{
               "date":"2016-06-20",
               "time":"19:00:00.0000000",
               "timeZone":"UTC"
            }
         },
         "confidence":100,
         "organizerAvailability":"free",
         "attendeeAvailability":[
            {
               "attendee":{
                  "type":"required",
                  "emailAddress":{
                     "address":"alexd@contoso.onmicrosoft.com"
                  }
               },
               "availability":"free"
            }
         ],
         "locations":[
            {
               "displayName":"Conf room Hood"
            }
         ],
         "suggestionHint":"Suggested because it is one of the nearest times when all attendees are available."
      }
   ],
   "emptySuggestionsHint":""
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "user: findMeetingTimes",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->