---
author: justinha
Description: FFU Bildformat
ms.assetid: 6847ef65-becf-4a96-a4e0-6cef27dcabf7
MSHAttr: PreferredLib:/library/windows/hardware
title: FFU Bildformat
ms.openlocfilehash: 4fd07947af6c4aaac25ab73117b83ffe0cfc52bd
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="ffu-image-format"></a>FFU Bildformat


Das folgende Diagramm zeigt V1 und V2 FFU Format. Eine Hauptversion geändert eingeführt in V2 FFU Format ist die Unterstützung für mehrere Datenspeicher – jeder Informationsspeicher enthält Sektor basierende Daten für eine eindeutige physischen Partition.

![Vergleich der FFU Formate. Abschnitte für beide enthalten: Sicherheit Header, Bildheader, Store Header und Abstände. Für FFU V2 können mehrere Speicher Kopf- und Nutzlast Datenabschnitte vorhanden sein.](images/oem-ffuv2-image-format.png)

## <a name="span-idsecurityheaderregionspanspan-idsecurityheaderregionspanspan-idsecurityheaderregionspansecurity-header-region"></a><span id="Security_header_region"></span><span id="security_header_region"></span><span id="SECURITY_HEADER_REGION"></span>Bereich Sicherheit


<span id="cbSize"></span><span id="cbsize"></span><span id="CBSIZE"></span>cbSize  
Die Größe der SICHERHEIT\_HEADER Struktur. Zusammen mit der Signaturzeichenfolge verwendet zum Identifizieren des FFU Security-Headers.

<span id="Signature_string"></span><span id="signature_string"></span><span id="SIGNATURE_STRING"></span>Signaturzeichenfolge  
Eine hartcodierte ASCII-Zeichenfolge "SignedImage", die dieses Bild als sichere FFU Bild identifiziert.

<span id="Chunk_size_in_KB"></span><span id="chunk_size_in_kb"></span><span id="CHUNK_SIZE_IN_KB"></span>Segmentgröße in KB  
Die Größe der Abschnitte, die zum Generieren der Hashtabelle verwendet haben. Verwendet, um das Bild in hashable Segmente für Einträge in der Hash-Validierung aufteilen und stellen Sie sicher, dass das Bild nicht nach der Erstellung manipuliert wurde.

<span id="Hash_algorithm_ID"></span><span id="hash_algorithm_id"></span><span id="HASH_ALGORITHM_ID"></span>Hashalgorithmus-ID  
Definiert, welcher Hashalgorithmus zum Generieren der Hashtabelle verwendet wurde.

<span id="Catalog_size"></span><span id="catalog_size"></span><span id="CATALOG_SIZE"></span>Catalog-Größe  
Die Größe in Bytes des Katalogs nach dem Sicherheitsheader.

<span id="Hash_table_size"></span><span id="hash_table_size"></span><span id="HASH_TABLE_SIZE"></span>Größe der Hash-Tabelle  
Die Größe des nach der Security-Header und der Katalog der Hashtabelle in Bytes.

**Security-Header**, Byteanzahl: CbSize

``` syntax
#define SECURITY_SIGNATURE "SignedImage "

typedef struct _SECURITY_HEADER
{
    UINT32 cbSize;            // size of struct, overall
    BYTE   signature[12];     // "SignedImage "
    UINT32 dwChunkSizeInKb;   // size of a hashed chunk within the image
    UINT32 dwAlgId;           // algorithm used to hash
    UINT32 dwCatalogSize;     // size of catalog to validate
    UINT32 dwHashTableSize;   // size of hash table
} SECURITY_HEADER;
```

**Katalog signiert**, Byteanzahl: DwCatalogSize

Eine Katalogdatei mit den Hash der Blob der Hash-Tabelle, das signiert wird und muss eines der Zertifikate auf dem Gerät übereinstimmen. Dieser Ansatz ermöglicht eine Signatur vorab ohne das vollständige Bild auf das Gerät vor dem blinken gesucht. Streaming von Daten wird überprüft, empfangenes gegen die Einträge der Hash-Tabelle.

**Tabellendaten Hash**Byteanzahl: DwHashTableSize

Die tatsächlichen Hashes für jeden Datenblock des Basis Bilds. Chunk Validierung beginnt mit der Bild-Kopfzeile und am Ende der FFU endet.

**Padding** - nächste Abschnittswechsel auf einer Chunk-Grenze Byteanzahl: Variable

Wenn die Hashtabelle wurde Abstand (leere Zeichenfolge) hinzugefügt zum aktuellen Abschnitt ausfüllen. Dadurch wird sichergestellt, dass gesicherte Kopfzeile, Katalog und Hashtabelle am eine Grenze Chunk und die eigentliche Bild Kopfzeile endet und darüber hinaus Chunk ausgerichtet werden.

## <a name="span-idimageheaderregionspanspan-idimageheaderregionspanspan-idimageheaderregionspanimage-header-region"></a><span id="Image_header_region"></span><span id="image_header_region"></span><span id="IMAGE_HEADER_REGION"></span>Bild-Header region


<span id="cbSize"></span><span id="cbsize"></span><span id="CBSIZE"></span>cbSize  
Die Größe des der ImageHeader Struc in Bytes. Zusammen mit der Signaturzeichenfolge verwendet zum Identifizieren der FFU Headers.

<span id="Signature_string"></span><span id="signature_string"></span><span id="SIGNATURE_STRING"></span>Signaturzeichenfolge  
Eine hartcodierte Zeichenfolge "ImageFlash", die dieses Bild als Bild FFU identifiziert.

<span id="Manifest_Length"></span><span id="manifest_length"></span><span id="MANIFEST_LENGTH"></span>Manifest Länge  
Die Größe des Manifesten Daten unmittelbar nach der Bildheader in Bytes.

<span id="Chunk_size"></span><span id="chunk_size"></span><span id="CHUNK_SIZE"></span>Datenblockgröße  
Die Größe der Abschnitte, die zum Generieren der Hashtabelle verwendet haben. Verwendet, um das Bild in hashable Segmente für Einträge in der Hash-Validierung aufteilen und stellen Sie sicher, dass das Bild nicht nach der Erstellung manipuliert wurde. Dies sollte die Chunk-Size im sicheren Header übereinstimmen. Verwendet nur während der Überprüfung des Abbilds ausgeführt.

**Bild-Header**, Byteanzahl: CbSize

``` syntax
#define FFU_SIGNATURE "ImageFlash  "

typedef struct _IMAGE_HEADER
{
    DWORD  cbSize;           // sizeof(ImageHeader)
    BYTE   Signature[12];    // "ImageFlash  "
    DWORD  ManifestLength;   // in bytes
    DWORD  dwChunkSize;      // Used only during image generation.
} ImageHeader;
```

**Manifest Daten**, Byteanzahl: ManifestLength

Das Manifest enthält die Beschreibung der das Gerät Layout und Nutzlast in der FFU enthalten.

Byteanzahl **Abstand** : Variable

Nach das Manifest Abstand (leere Zeichenfolge) wird zum Ausfüllen zum aktuellen Abschnitt hinzugefügt. Dadurch wird sichergestellt, dass die Daten, die folgt auf einer Grenze Chunk beginnt.

## <a name="span-idstoreheaderregionspanspan-idstoreheaderregionspanspan-idstoreheaderregionspanstore-header-region"></a><span id="Store_header_region"></span><span id="store_header_region"></span><span id="STORE_HEADER_REGION"></span>Store-Header region


### <a name="span-idstoreheaderspanspan-idstoreheaderspanspan-idstoreheaderspanstore-header"></a><span id="Store_header"></span><span id="store_header"></span><span id="STORE_HEADER"></span>Speicher-header

<span id="Store_header__byte_count__STORE_HEADER_V1_0_SIZE__248_bytes_"></span><span id="store_header__byte_count__store_header_v1_0_size__248_bytes_"></span><span id="STORE_HEADER__BYTE_COUNT__STORE_HEADER_V1_0_SIZE__248_BYTES_"></span>**Store-Header**, Byteanzahl: STORE\_HEADER\_V1\_0\_(248 BYTE)  
Die Informationsspeicher Kopfzeile enthält die Metadaten, die Nutzlast beschreibt. Dazu gehören Updatetyp, Validierung Größe, Datengröße und Versioning. Einige Informationen redundant ist, aber aus praktischen Gründen enthalten ist.

Der Store-Header enthält DWORD-WERT Count/Länge Felder, die die Überprüfung beschreiben & Deskriptor Abschnitte zu schreiben.  Diese Abschnitte heraus kopiert und später verarbeitet werden können.

In V1 FFU-Format sollte nur eine Store Kopfzeile angezeigt werden. V2 FFU-Format zu erwarten, dass eine Anzahl von Store Kopfzeilen, abhängig vom Wert von NumOfStores Struktur definierten finden Sie unter.

<span id="Validation_descriptor_region"></span><span id="validation_descriptor_region"></span><span id="VALIDATION_DESCRIPTOR_REGION"></span>Validierung Deskriptor region  
Die Überprüfung Deskriptor Region ist eine Auflistung von VALIDIERUNG\_Strukturen EINTRAG.  DwValidateDescriptorCount davon vorhanden sind, und die allgemeine Byteanzahl des Bereichs ist DwValidateDescriptorLength aus.

<span id="Write_descriptor_region"></span><span id="write_descriptor_region"></span><span id="WRITE_DESCRIPTOR_REGION"></span>Schreiben von Deskriptor region  
Die Write Deskriptor Region ist eine Auflistung von BLOCK\_DATEN\_EINTRAG Strukturen.  DwWriteDescriptorCount davon vorhanden sind, und die Gesamtgröße in Bytes des Bereichs ist DwWriteDescriptorLength.

<span id="MajorVersion__MinorVersion"></span><span id="majorversion__minorversion"></span><span id="MAJORVERSION__MINORVERSION"></span>Hauptversion, MinorVersion  
Haupt- und Nebenversionen des Store-Headers.

<span id="FullFlashMajorVersion__FullFlashMinorVersion_"></span><span id="fullflashmajorversion__fullflashminorversion_"></span><span id="FULLFLASHMAJORVERSION__FULLFLASHMINORVERSION_"></span>FullFlashMajorVersion FullFlashMinorVersion   
Haupt- und Nebenversionen des Dateiformats vollständige flash-Update.

In der folgenden Tabelle sind die Versionswerte für V1 und V2 Ffu Bildformate.

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<tbody>
<tr class="odd">
<td align="left"></td>
<td align="left">V1</td>
<td align="left">V2</td>
</tr>
<tr class="even">
<td align="left"><p>Hauptversion</p></td>
<td align="left"><p>1</p></td>
<td align="left"><p>2</p></td>
</tr>
<tr class="odd">
<td align="left"><p>MinorVersion</p></td>
<td align="left"><p>0</p></td>
<td align="left"><p>0</p></td>
</tr>
<tr class="even">
<td align="left"><p>FullFlashMajorVersion</p></td>
<td align="left"><p>2</p></td>
<td align="left"><p>2</p></td>
</tr>
<tr class="odd">
<td align="left"><p>FullFlashMinorVersion</p></td>
<td align="left"><p>0</p></td>
<td align="left"><p>0</p></td>
</tr>
</tbody>
</table>

 

**Hinweis**  
-   OEM sollte nicht das Bild auf das Gerät flash, es sei denn, die Version des Bilds diese Werte entspricht.

 

<span id="NumOfStores__V2_only_"></span><span id="numofstores__v2_only_"></span><span id="NUMOFSTORES__V2_ONLY_"></span>NumOfStores (nur Version 2)  
Anzahl von Speicher und ihre Nutzlast in dieser FFU.

<span id="StoreIndex__V2_only_"></span><span id="storeindex__v2_only_"></span><span id="STOREINDEX__V2_ONLY_"></span>StoreIndex (nur Version 2)  
Aktuelle Store Index, beginnend bei 1.

<span id="StorePayloadSize__V2_only_"></span><span id="storepayloadsize__v2_only_"></span><span id="STOREPAYLOADSIZE__V2_ONLY_"></span>StorePayloadSize (nur Version 2)  
Größe der Nutzlast Store in Bytes ohne Auffüllung.

<span id="DevicePathLength__V2_only_"></span><span id="devicepathlength__v2_only_"></span><span id="DEVICEPATHLENGTH__V2_ONLY_"></span>DevicePathLength (nur Version 2)  
Die Größe des Geräts Pfads, der, in Zeichen, bildet, ohne das abschließende Null-Zeichen.

<span id="DevicePath__V2_only_"></span><span id="devicepath__v2_only_"></span><span id="DEVICEPATH__V2_ONLY_"></span>DevicePath (nur Version 2)  
Tatsächliche Gerätepfad, die der Speicher für gerichtet ist. Dies sollte das Gerätepfad aus UEFI Protokoll abgerufene identisch sein: GERÄT\_PFAD\_AN\_TEXT\_PROTOKOLL. ConvertDevicePathToText()

<pre><code>
typedef struct _STORE_HEADER
{
    UINT32 dwUpdateType; // indicates partial or full flash
    UINT16 MajorVersion, MinorVersion; // used to validate struct
    UINT16 FullFlashMajorVersion, FullFlashMinorVersion; // FFU version, i.e. the image format
    char szPlatformId[192]; // string which indicates what device this FFU is intended to be written to
    UINT32 dwBlockSizeInBytes; // size of an image block in bytes – the device’s actual sector size may differ
    UINT32 dwWriteDescriptorCount; // number of write descriptors to iterate through
    UINT32 dwWriteDescriptorLength; // total size of all the write descriptors, in bytes (included so they can be read out up front and interpreted later)
    UINT32 dwValidateDescriptorCount; // number of validation descriptors to check
    UINT32 dwValidateDescriptorLength; // total size of all the validation descriptors, in bytes
    UINT32 dwInitialTableIndex; // block index in the payload of the initial (invalid) GPT
    UINT32 dwInitialTableCount; // count of blocks for the initial GPT, i.e. the GPT spans blockArray[idx..(idx + count -1)]
    UINT32 dwFlashOnlyTableIndex; // first block index in the payload of the flash-only GPT (included so safe flashing can be accomplished)
    UINT32 dwFlashOnlyTableCount; // count of blocks in the flash-only GPT
    UINT32 dwFinalTableIndex; // index in the table of the real GPT
    UINT32 dwFinalTableCount; // number of blocks in the real GPT
    <b>UINT16 NumOfStores; // Total number of stores (V2 only)</b>
    <b>UINT16 StoreIndex; // Current store index, 1-based (V2 only)</b>
    <b>UINT64 StorePayloadSize; // Payload data only, excludes padding (V2 only)</b>
    <b>UINT16 DevicePathLength; // Length of the device path (V2 only)</b>
    <b>CHAR16 DevicePath[1]; // Device path has no NUL at then end (V2 only)</b>
} STORE_HEADER;
</code></pre>

### <a name="span-idvalidationentriesspanspan-idvalidationentriesspanspan-idvalidationentriesspanvalidation-entries"></a><span id="Validation_Entries"></span><span id="validation_entries"></span><span id="VALIDATION_ENTRIES"></span>Validation-Einträge

**Validation-Einträge**, Elementanzahl: DwValidateDescriptorCount Byteanzahl: DwValidateDescriptorLength

Der Abschnitt Überprüfung wird nur für partielle Updates verwendet. Es enthält einen Satz von GÜLTIGKEITSPRÜFUNGSREGELN\_EINTRAG Strukturen. Jeder Validierung Eintrag enthält ein Byte-Array und einen Bereich auf der Festplatte, verglichen werden soll. Wenn die Daten in den Eintrag für die Validierung die Daten auf dem Datenträger übereinstimmt, wird dieser Eintrag Validierung bestätigt. Wenn alle Einträge der Überprüfung bestätigt werden, wird das partielle Update sicher für das Gerät zu übernehmen.

**Validation-Eintrag**, Byteanzahl: Variable

Jede VALIDIERUNG\_EINTRAG Struct beschreibt einen Speicherort auf dem Datenträger, die, deren Daten sollten entsprechen das Byte-array in diesen Eintrag.

``` syntax
typedef struct _VALIDATION_ENTRY
{
    UINT32 dwSectorIndex;
    UINT32 dwSectorOffset;
    UINT32 dwByteCount;
    BYTE rgCompareData[1]; // size is dwByteCount
} VALIDATION_ENTRY;
```

### <a name="span-idblockdataentriesspanspan-idblockdataentriesspanspan-idblockdataentriesspanblock-data-entries"></a><span id="Block_data_entries"></span><span id="block_data_entries"></span><span id="BLOCK_DATA_ENTRIES"></span>Dateneinträge blockieren

**Dateneinträge blockieren**, Elementanzahl: DwWriteDescriptorCount Byteanzahl: DwWriteDescriptorLength

Die Dateneinträge Block wird beschrieben, wie die Daten auf den Datenträger geschrieben. Es ist möglich, einen einzelnen Bereich des Datenträgers nur einmal schreiben oder zum Schreiben der gleichen Daten an mehreren Stellen auf dem Datenträger, eine komprimierte Nutzlast zulassen. Besteht aus die Schreibzugriff Deskriptor Region BLOCK\_DATEN\_EINTRAG Strukturen. Jeder Eintrag hat eine Größe und ein Bytearray und ein Array von Speicherorten zum Schreiben auf Datenträger.

Die Felder **DwFlashOnlyTableIndex** und **DwFlashOnlyTableCount** dienen den letzten Eintrag Block zu ermitteln, der für alle Partitionen erforderlich, um das Gerät erneut flash-Layout erforderlich ist. Wenn alle Blöcke bis und einschließlich dieser Block auf das Gerät aktualisiert werden, kann das Gerät erneut Flash ohne alle Halbleiterhersteller oder OEM-Code.

**Dateneingabe blockieren**, Byteanzahl: Variable

Jeden Block Dateneingabe beschreibt einen Block von Daten im Abschnitt Data Store. Jeder Eintrag beschreibt die Anzahl der Datenblöcke und die Speicherorte, die sie geschrieben werden, auf dem Datenträger. Die AccessMethod ist wie der AccessMethod in Zeigers an, was bedeutet, dass Bedeutung für die BlockIndex ermöglicht es verwendet.

``` syntax
enum DISK_ACCESS_METHOD
{
    DISK_BEGIN  = 0,
    DISK_END    = 2
};

typedef struct _DISK_LOCATION
{
    UINT32 dwDiskAccessMethod;
    UINT32 dwBlockIndex;
} DISK_LOCATION; 

typedef struct _BLOCK_DATA_ENTRY
{
    UINT32 dwLocationCount;
    UINT32 dwBlockCount;
    DISK_LOCATION rgDiskLocations[1];
} BLOCK_DATA_ENTRY;
```

### <a name="span-idpaddingspanspan-idpaddingspanspan-idpaddingspanpadding"></a><span id="Padding"></span><span id="padding"></span><span id="PADDING"></span>Abstand

**Abstand** – zum nächsten Abschnitt, um an einer Blockgrenze Byteanzahl starten zulassen: Variable

## <a name="span-idimagepayloadregionspanspan-idimagepayloadregionspanspan-idimagepayloadregionspanimage-payload-region"></a><span id="Image_payload_region"></span><span id="image_payload_region"></span><span id="IMAGE_PAYLOAD_REGION"></span>Bild Nutzlast region


Nutzlast Blockdaten geschrieben werden, auf dem Datenträger Byteanzahl: Variable.

Dies ist ein Array von Datenblöcke. Jeder Datenblock besteht aus **BytesPerBlock** Bytes, wobei **BytesPerBlock** im Store Header definiert ist.

In V1 FFU Format sollte nur ein Bild Nutzlast Region angezeigt werden. V2 FFU-Format zu erwarten, dass eine Reihe von Bild Nutzlast Regionen abhängig vom Wert von Struct NumOfStores definierten finden Sie unter.

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Blinken tools](flashing-tools.md)

 

 






