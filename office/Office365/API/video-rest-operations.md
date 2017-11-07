---
ms.Toctitle: Video REST API reference
title: Video REST-API-Referenz
description: "Gewusst wie: Verwenden der Video REST-API zum Ermitteln von und interagieren mit Informationen zu Videos und Kanäle in Office 365 Video Service in SharePoint Online abgerufen verweisen."
ms.ContentId: 4202e210-44be-4289-808d-3b7358181cc0
ms.date: November 17, 2015
ms.openlocfilehash: a4194467f28959785912432fe0e6350aab895bcb
ms.sourcegitcommit: 4648ef0fb81b465cef7e8ccad197fe9b9edabc33
translationtype: MT
---
# <a name="video-rest-api-reference"></a>Video-REST-API-Referenz


 _**Gilt für:** SharePoint Online | Office 365_

Die REST-API Video können Sie ermitteln und interagieren mit Videos im Office 365-Video-Dienst in SharePoint Online. Sie können Abrufen von Informationen zu Videos und Kanäle, neue Videos hochladen und Abrufen von Informationen Videostreams.

<a name="Overview"> </a>
## <a name="using-the-video-rest-api"></a>Verwenden das Video REST-API

Es gibt zwei Arten von Objekten, die mit der REST-API Video interagiert: Videos und Kanäle.

Zur Interaktion mit der REST-API Video, senden Sie HTTP-Anfragen, die eine unterstützte Methode zu verwenden: erhalten MÖCHTEN, VERÖFFENTLICHEN, ZUSAMMENFÜHREN oder LÖSCHEN.

Alle API-Video-Anforderungen verwenden die Stamm-URL aus der Discovery-Dienst abgerufen, wie im Abschnitt "Vorgänge Video Portal" erläutert.

Der Pfad URL Ressourcennamen und Abfrageparameter Groß-und Kleinschreibung. Werte, die Sie zuweisen, Entity-IDs und anderen base64-codierte Werte sind jedoch Groß-/Kleinschreibung beachtet.

Die Office 365-APIs verwenden Microsoft Azure Active Directory (AD Azure) und OAuth zum [Authentifizieren der Anwendung Anfragen](..\howto\common-app-authentication-tasks.md)an.
Um die API Video von der Anwendung zuzugreifen, müssen Sie in Azure Active Directory mit [Berechtigungen auf den entsprechenden Bereich](..\howto\common-app-authentication-tasks.md#sectionSection0)registriert werden.
Der Office 365 Video REST-API unterstützt OData 4.0 Standards und apps Videodaten in Office 365 mithilfe von Rest-Schnittstellen interagieren können.

Berechtigungen sind in drei benutzerdefinierte Gruppen beschränkt:

 - Administratoren können ändern, DDE-Kanal und Videos zu bearbeiten.
 - Mitwirkende können erstellen, lesen, aktualisieren und löschen (CRUD) Videos.
 - Viewer können nur Videos anzeigen.

Der Besitzer des Kanals für jeden Kanal bestimmt, die in der Organisation in jede dieser Gruppen fällt. Darüber hinaus kann die SharePoint-Mandanten-Administrator die gleiche Bestimmung stellen.


**Hinweis** Finden Sie weitere Informationen finden Sie unter [Developing auf der Office 365-Plattform](..\howto\platform-development-overview.md).

<a name="VideoPortalOperations"> </a>
## <a name="video-portal-operations"></a>Video Portal-Vorgänge

Sie erhalten die Stamm-URL des video-Portals in allen anderen Video REST-API-Operationen verwendet, und Sie können erkennen, ob das video Portal eingerichtet und aktiviert ist.

****

<a name="GetPortalInformation"></a> 
 **Abrufen von Informationen zu den video Portal**

Verwenden Sie den O365- [Discovery-Dienst](..\api\discovery-service-rest-operations.md) auf die Stamm-URL für SharePoint, Site Collection (Stammwebsite), und rufen Sie dann VideoService.Discover aus, um die URL des video-Portals in SharePoint Online abzurufen, die Sie, klicken Sie dann in allen nachfolgenden Aufrufen verwenden-URL an. Ermitteln Sie, ob das video Portal eingerichtet und aktiviert ist.

**Hinweis** Um den Discovery-Dienst zugreifen zu können, müssen Sie für Ihr Unternehmen in der SharePoint Portal angemeldet sein.

In der Regel würde die Endpunkt-URL für die Stammwebsitesammlung für SharePoint (für das fiktive Unternehmen Contoso) etwa folgendermaßen aussehen:

https://contoso.SharePoint.com/

Die Endpunkt-URL für das video Portal für das gleiche Unternehmen den Discovery-Dienst zurückgegebene aussehen etwa folgendermaßen:

https://contoso.SharePoint.com/Portals/Hub

```no-highlight
GET {RootSite}/_api/VideoService.Discover
```

**Hinweis** Der Parameter *Workflowwebsite* ist eine Zeichenfolge, die Endpunkt-URL der Stammwebsitesammlung für SharePoint darstellt, aus der Discovery-Dienst abgerufen. |

 **Antworttyp**

- **IsVideoPortalEnabled** --True, wenn Portal aktiviert und Einrichten von, False Wenn Portal ist entweder nicht aktiviert oder nicht konfiguriert ist.
- **VideoPortalURL** – die Endpunkt-URL des video-Portals, wird in alle nachfolgenden Aufrufe verwendet.

**Hinweis** Es wird empfohlen, dass Sie definieren und eine Konstante für diese URL verwenden, damit Sie auf einfache Weise Versionsinformationen hinzufügen können, die verfügbar ist.

[!code-REST-i[Get_Portal_Info](./_data/video_api_get_portal_info.json)]


<a name="ChannelOperations"> </a>
## <a name="channel-operations"></a>Kanal-Vorgänge

Videos werden in Kanäle gespeichert. Sie erhalten eine Liste aller Kanäle an die Benutzer Videos hochladen können und eine Liste aller Kanäle, die ein Benutzer anzeigen kann.
Sie können auch Informationen zu einem bestimmten Kanal, einschließlich die ID eines Kanals, die Farbe eines Kanals, den Titel eines Kanals und eine Liste aller Videos, die ein Kanal enthält abrufen.

****

<a name="GetChannelsInfo"> </a>
### <a name="get-information-about-the-channels-the-user-can-view-or-upload-to"></a>Abrufen von Informationen über die Kanäle, die der Benutzer kann anzeigen oder auf Hochladen

<a name="GetUploadChannels"></a> 
 **Abrufen einer Liste der Kanäle auf dem der Benutzer Videos hochladen kann**

Rufen Sie die Liste der Kanäle auf denen ein Benutzer hochladen kann Videos. Dies sind die Kanäle für die sie den Besitzer oder Editor Berechtigungen besitzen.


```no-highlight
GET {VideoPortalURL}/_api/VideoService/CanEditChannels
```

**Hinweis** In diesem und allen nachfolgenden Aufrufen ist *VideoPortalURL* eine Zeichenfolge, die Endpunkt-URL des video-Portals darstellt, wie aus den Anruf VideoService.Discover abgerufen.


 **Antworttyp**

Gibt eine Liste mit Channel-Objekten.

**Hinweis** Wenn Ihr video Portal viele Kanäle verfügt, kann diese API zurückzugebenden sehr lange dauern.


****

<a name="GetViewChannels"></a> 
 **Abrufen einer Liste der Benutzer anzeigen kann Kanäle**


Ruft die Liste aller Kanäle aus, die ein Benutzer anzeigen kann. Dies sind die Kanäle für die sie Besitzers, Editor oder Viewer Berechtigungen besitzen.


```no-highlight
GET {VideoPortalURL}/_api/VideoService/Channels
```

 **Antworttyp**

Gibt eine Liste mit Channel-Objekten.

[!code-REST-i[Get_ChannelView_Info](./_data/video_api_get_channels_view.json)]


****

<a name="GetChannelInfo"> </a>
### <a name="get-information-about-a-particular-channel"></a>Abrufen von Informationen zu einem bestimmten Kanal

<a name="GetInfo"></a> 
 **Abzurufen, die DDE-Kanal-ID, die Farbe Channel und des Titels Kanal**

```no-highlight
GET {VideoPortalURL}/_api/VideoService/Channels('{channelId}')
```
**Anfordern von URL-Parameter**

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|channelId|string|Die ID des Kanals.|


 **Antworttyp**

Gibt die folgende Informationen über einen Kanal:
- -ID – Die ID des Kanals.
- TileHtmlColor – Die Farbe des Kanals.
- Titel – Der Titel des Kanals.

[!code-REST-i[Get_Channel_Info](./_data/video_api_get_channel_info.json)]



<a name="GetVideoList"></a> 
 **Abrufen einer Liste aller Videos in einem Kanal**

Ruft die Liste alle Videos auf einem bestimmten Kanal ab.

```no-highlight
GET {VideoPortalURL}/_api/VideoService/Channels('{channelId}')/Videos
```

**Anfordern von URL-Parameter**

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|channelId|string|Die ID des Kanals.|


 **Antworttyp**

Gibt eine Liste von Video-Objekten.

[!code-REST-i[Get_Video_List](./_data/video_api_get_video_list.json)]


****

<a name="GetPlayableVideos"></a> 
 **Abrufen einer Liste der neuesten wiedergegeben werden können Videos in einem Kanal**

Ruft eine sortierte Liste der am häufigsten kürzlich hochgeladenen Videos für einen Kanal und Filtern der alle Videos, die noch nicht wiedergegeben werden können, außer denen, die von Ihnen hochgeladen wurden.

Dadurch wird eine sortierte Liste mit allen Videos für den Kanal, in denen transcodieren abgeschlossen haben und zum Abspielen bereit sind zurückgegeben (VideoProcessingStatus = 2), zusammen mit Videos, die wiedergegeben werden soll, noch nicht möchten, wenn sie von den aktuell angemeldeten Benutzer hochgeladen wurden.  

```no-highlight
GET {VideoPortalURL}/_api/VideoService/Channels('{channelId}')/GetAllVideos
```

**Anfordern von URL-Parameter**

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|channelId|string|Die ID des Kanals.|


 **Antworttyp**

Gibt eine Liste von Video-Objekten

****

<a name="VideoOperations"> </a>
## <a name="video-operations"></a>Video-Vorgänge

Abrufen von Informationen zu einer bestimmten video aus einem Kanal, rufen Sie die Anzahl, wie oft das Video angezeigt wurden und Wiedergabeinformationen erhalten möchten. Darüber hinaus Hochladen von Videos zu einem Kanal, die Videos in einem Kanal aktualisieren und Löschen von Videos aus einem Kanal.
****


<a name="GetVideoInfo"> </a>
### <a name="get-information-about-a-video"></a>Abrufen von Informationen zu einem video

Abrufen von Informationen zu einer bestimmten Video, einschließlich des Datums, den sie erstellt wurde, den Titel, die Dauer, die URL der Miniaturansicht des Videos und deren Verarbeitungsstatus.

```no-highlight
GET {VideoPortalURL}/_api/VideoService/Channels('{channelId}')/Videos('{videoId}')
```

**Anfordern von URL-Parameter**

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|channelId|string|Die ID des Kanals.|
|videoId|string|Die ID des Videos.|

 **Antworttyp**

Gibt die folgende Informationen zurück:
- CreatedDate--Das Datum, das Video ursprünglich hochgeladen wurde.
- Titel – Der Titel des Videos.
- VideoDurationInSeconds – Die Dauer des Videos in Sekunden.
- ThumbnailURL--Die URL der Miniaturansicht des Videos.
- VideoProcessingStatus – Der Status der video Verarbeitung. Kann die folgenden Werte annehmen:
    - 0 – (Standard) – das Video wurde noch nicht für die Wiedergabe verarbeitet.
    - 1 – das Video aufgenommene wurden und verarbeitet wird.
    - 2--das Video ist bereit, die wiedergegeben werden sollen.
    - 3 – das Video ist ein Fehler aufgetreten, während es in Azure Media Services für die Verarbeitung hochgeladen wurde.
    - 4 – Fehler: Allgemeiner Fehler – nicht das Video für streaming verarbeiten.
    - 5 – Fehler - Timeoutfehler – kann nicht das Video für streaming verarbeitet werden.
    - 6--Fehler--nicht unterstütztes Format – Typ der Videodatei wird nicht unterstützt für Stream-Wiedergabe von Azure Media-Dienste.

[!code-REST-i[Get_Video_Info](./_data/video_api_get_video_info.json)]

****

<a name="GetViewCountInfo"></a> 
 **Rufen Sie eine Anzahl der wie oft ein Video angezeigt wurden**

Zählt Ansicht werden nur, wenn Sie das Video-Objekt von Search-Endpunkten, abrufen, da die Ansicht Anzahl von suchanalyse aggregiert werden zurückgegeben. Die ViewCount-Eigenschaft wird somit unrichtige Werte aufweisen, es sei denn, sie über die /Search Endpunkte der Hub oder einen Kanal abgerufen werden.
Um die Ansichtenanzahl für ein einzelnes Video anzuzeigen, führen Sie eine Suchabfrage mit video-ID.


```no-highlight
GET {VideoPortalURL}/_api/videoservice/Channels('{channelId}')/search/query('{videoId}')?$Select=ViewCount
```

**Anfordern von URL-Parameter**

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|channelId|string|Die ID des Kanals.|
|videoId|string|Die ID des Videos.|

**Abfrageparameter**

|Name|Typ|Beschreibung|
|:-----|:-----|:-----|
|Wählen Sie $ _ = ViewCount|string|Die Ansichtenanzahl in der Antwort enthalten.|

 **Antworttyp**

Gibt die Anzahl der Häufigkeit, die des Videos angezeigt wurde.

[!code-REST-i[Get_View_Count](./_data/video_api_get_view_count.json)]


****

<a name="GetPlaybackInfo"> </a>
### <a name="get-information-about-playing-a-video"></a>Abrufen von Informationen über die Wiedergabe eines Videos

<a name="GetVideoManifest"></a> 
 **URL Abrufen der Azure-Media-Dienste manifest ein Video**

Dies ruft die Manifestdatei Azure Media-Dienste-URL für das Video. Sie können dieses Manifest ein Player feed, die Unterstützung für die Wiedergabe von Azure Media Services Assets hat.

```no-highlight
GET {VideoPortalURL}/_api/VideoService/Channels('{channelId}')/Videos('{videoId}')/GetPlaybackUrl('{streamingFormatType}')
```

**Anfordern von URL-Parameter**

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|channelId|string|Die ID des Kanals.|
|videoId|string|Die ID des Videos.|
|streamingFormatType|numerische|Streaming Formattyp des Videos.|

Der Parameter *StreamingFormatType* kann die folgenden Werte annehmen:
- 1--Smooth Streaming oder MPEG-STRICH
- 0 – HLS Streaming

**Antworttyp**

Gibt die URL des Manifests für das Video.

[!code-REST-i[Get_Format_Info](./_data/video_api_get_streaming_format.json)]


****

<a name="GetDecryptionToken"></a> 
 **Bearer Token für den Zugriff auf das Video entschlüsseln abrufen**

Alle Office 365-Videos sind AES verschlüsselt. Wiedergabe Videos im MPEG-STRICH-Format oder Smooth Streaming müssen Sie zunächst den Zugriff auf den Inhalt zu entschlüsseln abzurufenden Bearer-Token abzurufen. Diese API gibt das Authentifizierungstoken, um den Player zum Entschlüsseln der Inhalte zu ermöglichen.

Jedoch für HLS streaming müssen nicht Sie das wichtigsten Zugriffstoken separat abrufen, da es bereits ist Teil der manifest-URL an, die Sie erhalten, wenn Sie das Format HLS des Manifests abrufen.


```no-highlight
GET {VideoPortalURL}/_api/VideoService/Channels('{channelId}')/Videos('{videoId}')/GetStreamingKeyAccessToken
```

**Anfordern von URL-Parameter**

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|channelId|string|Die ID des Kanals.|
|videoId|string|Die ID des Videos.|


 **Antworttyp**

Gibt das Authentifizierungstoken, um die Player Entschlüsseln der Inhalte zuzulassen.

[!code-REST-i[Get_Bearer_Token](./_data/video_api_get_bearer_token.json)]

****

<a name="UploadVideos"> </a>
### <a name="upload-videos-to-a-channel"></a>Hochladen von Videos in einem Kanal

Erstellen Sie ein leeres Videos Objekt fungiert als Platzhalter für, in dem Sie ein Video hochladen möchten.

Nach auf diese Weise können Sie ein einzelnes kleines Video durch Aufrufen von POST hochladen, oder ruft eine größere in Segmenten in mehrere Post-ANFORDERUNG.

<a name="CreateEmptyVideoObject"></a> 
 **Erstellen eines Platzhalters für, in dem Sie das Video hochladen möchten**


Erstellt ein leeres Videos-Objekt, das fungiert als Platzhalter für, in dem Sie das Video hochladen möchten.

```no-highlight
POST {VideoPortalURL}/_api/VideoService/Channels('{channelId}')/Videos
```

**Anfordern von URL-Parameter**

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|channelId|string|Die ID des Kanals.|


**Anforderungstext**

{'__metadata': {"Typ": "SP. Publishing.VideoItem'}; "Beschreibung": ' {         *Ihrer Beschreibungstext hier* 
 } ', 'Titel': ' {         *Ihr Titel des Videos hier* 
 } "}


|Name|Typ|Beschreibung|
|:-----|:-----|:-----|
|Metadaten|SP. Publishing.VideoItem|Der Typ des Objekts, die Sie aktualisieren|
|Beschreibung|string|Die Beschreibung des Videos.|
|Title|string|Der Titel des Videos.|
|FileName|string|Der Dateiname des Videos.|


**Antworttyp**

VideoObject – Das Objekt in das Hochladen des Videos. Verwenden Sie als video ID zurückgegebene ID starten in hochladen.

****

<a name="UploadSmallVideo"></a> 
 **Ein kleineres Video in einem einzelnen Beitrag**

Dient zum Hochladen einer einzelnen video klein genug in einem einzelnen Beitrag zu übermitteln.


```no-highlight
POST {VideoPortalURL}/_api/VideoService/Channels('{channelId}')/Videos('{videoId}')/GetFile()/SaveBinaryStream
```
[//]: # (just checking that the above empty parens for GetFile are intentional)

**Anfordern von URL-Parameter**

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|channelId|string|Die ID des Kanals.|
|videoId|string|Die ID des Videos.|

**Anforderungstext**

Der binäre Datei-Stream. 

**Antworttyp**

Gibt 200. Keine Antworttext.

****

<a name="UploadLargerVideoInChunks"> </a>
###<a name="upload-a-larger-video-in-chunks"></a>Ein größerer Video in Segmenten

Verwenden Sie die folgenden Aufrufe zum Hochladen eines Videos zu groß, damit in einem einzigen Aufruf POST passen oder einen aufgeteilten Upload abzubrechen.


<a name="StartUploading"></a> 
 **Hochladen in das zuvor erstellte Objekt mit video starten**

Starten Sie das Hochladen des aufgeteilte Videos.

```no-highlight
POST {VideoPortalURL}/_api/VideoService/Channels('{channelId}')/Videos('{videoId}')/GetFile()/StartUpload(uploadId=guid'{yourGeneratedGuid}')
```

**Anfordern von URL-Parameter**

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|channelId|string|Die ID des Kanals.|
|videoId|string|Die ID des Videos.|
|yourGeneratedGuid|GUID|Die GUID, die Sie für Ihre Sitzung Upload zu generieren.|


**Antworttyp**

Gibt 200. Keine Antworttext.

****

<a name="UploadEachChunk"></a> 
 **Jeder Abschnitt der Datei auf das video-Objekt zuvor erstellten hochladen**

Weiterhin der nächsten Abschnitt der Datei hochladen. Wiederholen Sie so oft wie nötig.

```no-highlight
POST {VideoPortalURL}/_api/VideoService/Channels('{channelId}')/Videos('{videoId}')/GetFile()/ContinueUpload(uploadId=guid'{yourGeneratedGuid}',fileOffset='{offsetSize}')
```

**Anfordern von URL-Parameter**

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|channelId|string|Die ID des Kanals.|
|videoId|string|Die ID des Videos.|
|yourGeneratedGuid|GUID|Die GUID, die Sie für die Sitzung Upload zu generieren.|
|offsetSize|integer|Der Wert der Bytes bereits hochgeladen.|

**Hinweis:** Angenommen, Sie müssten d.h. 8MB hochladen, der Offset für das erste Segment wäre 0 und der Offset für die zweite Chunk wäre 8 * 1024 = 8192.


**Anforderungstext**

Der binäre Dateistream des in diesem Abschnitt.

**Antworttyp**

Gibt 200. Keinen Antworttext.

****


<a name="FinishUploading"></a> 
 **Hochladen der letzte Abschnitt der Datei, die das zuvor erstellte Objekt mit video beenden**

Das Hochladen des Videos aufgeteilte endet.

```no-highlight
POST {VideoPortalURL}/_api/VideoService/Channels('{channelId}')/Videos('{videoId}')/GetFile()/FinishUpload(uploadId=guid'{yourGeneratedGuid}',fileOffset='{offsetSize}')
```

**Anfordern von URL-Parameter**

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|channelId|string|Die ID des Kanals.|
|videoId|string|Die ID des Videos.|
|yourGeneratedGuid|GUID|Die GUID, die Sie für die Sitzung Upload zu generieren.|
|offsetSize|integer|Der Wert der Bytes bereits hochgeladen.|

**Anforderungstext**

Die Datei binären Stream des letzten Abschnitts.

**Antworttyp**

Gibt 200. Keinen Antworttext.

****

<a name="CancelChunkedUploading"></a> 
 **Hochladen Abbrechen**

Hebt das Hochladen des aufgeteilte Videos.

```no-highlight
POST {VideoPortalURL}/_api/VideoService/Channels('{channelId}')/Videos('{videoId}')/GetFile()/CancelUpload(uploadId=guid'{yourGeneratedGuid}')
```

**Anfordern von URL-Parameter**

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|channelId|string|Die ID des Kanals.|
|videoId|string|Die ID des Videos.|
|yourGeneratedGuid|GUID|Die GUID, die Sie für die Sitzung Upload zu generieren.|

**Antworttyp**

Gibt 200. Keine Antworttext.

****


<a name="UpdateVideo"> </a>
###<a name="update-video-metadata"></a>Aktualisieren von video-Metadaten
**Aktualisieren Sie die Metadaten für eine vorhandene Video in einem Kanal**


Ändern Sie den Titel und die Beschreibung eines Videos.

```no-highlight
POST {VideoPortalURL}/_api/VideoService/Channels('{channelId}')/Videos('{videoId}')
```

**Anfordern von URL-Parameter**

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|channelId|string|Die ID des Kanals.|
|videoId|string|Die ID des Videos.|


**Anforderungsheader**

|Name|Typ|Beschreibung|
|:-----|:-----|:-----|
|X-HTTP-Methode|string|MERGE ist der Wert der Eigenschaft X-HTTP-Methode.|


**Anforderungstext**

{'__metadata': {"Typ": "SP. Publishing.VideoItem'},'Description': "{ *Ihre Beschreibungstext hier* }", "Title": "{ *Ihr Titel des Videos hier* }"}

|Name|Typ|Beschreibung|
|:-----|:-----|:-----|
|Metadaten|SP. Publishing.VideoItem|Der Typ des video-Objekts.|
|Beschreibung|string|Die Beschreibung des Videos.|
|Title|string|Der Titel des Videos.|

 **Antworttyp**

Gibt 200. Keine Antworttext.

****

<a name="DeleteVideos"> </a>
## <a name="delete-videos-from-a-channel"></a>Löschen von Videos aus einem Kanal



<a name="DeleteVideo"></a> 
 **Löschen eine vorhandene Videokonferenz aus einem Kanal**


```no-highlight
 POST {VideoPortalURL}/_api/VideoService/Channels('{channelId}')/Videos('{videoId}')
```

**Anfordern von URL-Parameter**

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|channelId|string|Die ID des Kanals.|
|videoId|string|Die ID des Videos.|


**Anforderungsheader**

|Name|Typ|Beschreibung|
|:-----|:-----|:-----|
|X-HTTP-Methode|string|DELETE-Anweisung ist der Wert der Eigenschaft X-HTTP-Methode.|

 **Antworttyp**

Gibt 200. Keine Antworttext.

****

<a name="EmbedVideo"> </a>
## <a name="embed-a-video-in-another-page"></a>Einbetten eines Videos in eine andere Seite

****

<a name="GetEmbedCodeConfigureParameters"></a> 
 **Einen, die Sie ein video-Element in einer anderen Webseite, Angeben von Parameterwerten einbetten kann, Code abrufen**

Dieses Anrufs können Sie Werte für die Parameter angeben, die Sie weitergeben, einschließlich der Breite und Höhe des eingebetteten Fenster, ob das Video automatisch beim Öffnen der Seite angezeigt wird und ob bestimmte Informationen im Videoplayer angezeigt wird, wenn das Video angehalten wird. Die Informationen enthält, den Titel des Videos, die Dauer, Anzahl wie oft wiedergegeben wurde. und den Namen des Kanals an. 

```no-highlight
GET {VideoPortalURL}/_api/VideoService/Channels('{channelId}')/Videos('{videoId}')/GetVideoEmbedCode?width={width}&height={height}&autoplay={true/false}&showinfo={true/false}
```

Wenn Sie Werte für die Parameter übergeben, wählt das Office 365 einige sinnvolle Standardwerte, wie 120 für Breite und Höhe 230 aus.

**Anfordern von URL-Parameter**

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|channelId|string|Die ID des Kanals.|
|videoId|string|Die ID des Videos.|
|width|numerische|Die Breite des Fensters eingebettete Videos.|
|height|numerische|Die Höhe des Fensters eingebettete Videos.|
|Automatische Wiedergabe|wahr/falsch|Gibt an, ob die eingebettete Videos automatisch gestartet wird.|
|ShowInfo|wahr/falsch|Gibt an, ob der Titel des Videos, Dauer, Anzahl angezeigt und ChannelName im Player angezeigt werden, wenn das Video angehalten ist.|


**Antworttyp**

Gibt den Einbettungscode zurück.

****

<a name="GetEmbedCodeDefaultValues"></a> 
 **Einen, die Sie ein video-Element in einer anderen Webseite mit Standardwerten einbetten kann, Code abrufen**

Dieses Anrufs können Sie eine Einbettungscode abrufen, die die Standardwerte für die eingebettete Videoplayer angibt.

```no-highlight
GET {VideoPortalURL}/_api/VideoService/Channels('{channelId}')/Videos('{videoId}')/?$Select=Title,DefaultEmbedCode
```

Die Eigenschaft "DefaultEmbedCode" wird nicht automatisch auf das Video-Objekt zurückgegeben. Sie die Option $select verwenden müssen "DefaultEmbedCode" abgerufen.

Die Option $select verwenden, können Sie Videoelement, video, einschließlich Titel und standardmäßige Eigenschaften Code einbetten zurückgegeben, siehe anfordern.

**Anfordern von URL-Parameter**

|**Erforderliche parameter**|**Typ**|**Beschreibung**|
|:-----|:-----|:-----|
|channelId|string|Die ID des Kanals.|
|videoId|string|Die ID des Videos.|


**Antworttyp**

Gibt zurück, dass keine Standardeigenschaften, den, die Sie mithilfe von $select, einschließlich der standardmäßigen anfordern, Code einbetten.

****

<a name="GetVideoItemFromPlayerPageURL"></a> 
 **Videoelement Informationen und die Standardeinstellung Einbettungscode aus der Player-Seiten-URL**

Dieses Anrufs verwenden, wenn Sie die URL der Seite ein Video O365 Video Portal Player kennen, können Sie die video ID, die DDE-Kanal-ID und andere Informationen zu den Video abrufen.

```no-highlight
POST {VideoPortalURL}/_api/VideoService/GetVideoByURL?$Select=Title,Description,CreatedDate,DefaultEmbedCode,VideoDurationInSeconds,ID,VideoProcessingStatus
```

Mithilfe der Option $select können Sie bitten, return Videoelement video Eigenschaften, einschließlich der Titel und die standardmäßige Code einbetten wie dargestellt.


**Anforderungsheader**

Akzeptieren Sie = Application/Json; Odata = verbose

Content-Type = Application/Json; Odata = verbose


**Anforderungstext**

{'VideoFileRelativeUrl':'Https: / /*Root_SharePoint_site*/portals/hub/_layouts/15/PointPublishing.aspx?app=video & p = p & chid = b74774cb-Faad-43a0-8de9-cb263e38d75d & Vid = e5b66725-9f87-4813-9b50-b24fe80c9c20 "}

Dabei ist **VideoFileRelativeURL** die relative oder absolute URL der Seite ein Video O365 Video Portal Player.

****

<a name="NextSteps"> </a>
## <a name="next-steps"></a>Nächste Schritte

Ob Sie bereit, zum Erstellen einer app starten oder einfach mehr erfahren möchten sind, haben wir Sie behandelte Problem zu.


- Sind Sie bereit für den Einstieg? Starten Sie, indem [das Einrichten Ihrer Umgebung](..\howto\setup-development-environment.md).

- Weitere praktische Erfahrung mit diesen APIs abrufen möchten? Durcharbeiten Sie diese [praktische Übung für Video-APIs](http://dev.office.com/hands-on-labs/4589).

Oder erfahren Sie mehr über die Verwendung der Office 365-Plattform:

- [Bei der Entwicklung mit der Office 365-Plattform](..\howto\platform-development-overview.md)

- [Office 365-app-Authentifizierung](..\howto\common-app-authentication-tasks.md)

- [Common consent – Office 365 apps manuell hinzufügen](..\howto\add-common-consent-manually.md)

- [Deaktivieren oder erneutes Aktivieren von Office 365-Videos](https://support.office.com/en-us/article/Manage-your-Office-365-Video-portal-c059465b-eba9-44e1-b8c7-8ff7793ff5da#BKMK_Disabling)

- [Kalender-REST-Vorgänge](..\api\calendar-rest-operations.md)

- [Kontakte-REST-Vorgänge](..\api\contacts-rest-operations.md)

- [OneDrive-API](https://dev.onedrive.com/)

- [Ermittlung REST Service-Vorgänge](..\api\discovery-service-rest-operations.md)

- [E-Mail-REST-Vorgänge](..\api\mail-rest-operations.md)

- [OneDrive-API](https://dev.onedrive.com/)
