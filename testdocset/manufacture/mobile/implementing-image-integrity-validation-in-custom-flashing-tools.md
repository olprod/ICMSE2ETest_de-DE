---
author: kpacquer
Description: "Implementieren von Bild Integrität Überprüfung in benutzerdefinierten blinkende tools"
ms.assetid: 0885d221-e9c6-4fe1-987b-34781546ba07
MSHAttr: PreferredLib:/library/windows/hardware
title: "Implementieren von Bild Integrität Überprüfung in benutzerdefinierten blinkende tools"
ms.openlocfilehash: 26468abb000faef1515759fe38463a6bd56ff170
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="implementing-image-integrity-validation-in-custom-flashing-tools"></a>Implementieren von Bild Integrität Überprüfung in benutzerdefinierten blinkende tools


Das Bild FFU enthält eine signierte Katalogdatei, ein Hash in den Katalog und des weiteren jeder Ausschnitt des Bilds für eine Tabelle. Der Inhalt der Hash-Tabelle sind mit den sicheren Hashalgorithmus SHA256 generiert. Bevor Sie das Bild aktualisiert wird, müssen drei überprüft ausgeführt werden:

-   **Überprüfung der Katalog Signatur** - Überprüfen der Signatur der signierten Katalogdatei trägt dazu bei, um sicherzustellen, dass das Bild von einer vertrauenswürdigen Quelle stammt.

-   **Der Tabelle der Überprüfung Hashes Hash** - überprüfen den Hash der Tabelle des weiteren in der Tabelle stellt sicher, dass das Bild nicht manipuliert wurde.

-   **Daten aufteilen Validierung mithilfe der Einträge in der Hash** - der FFU Anwendung muss jeder Ausschnitt gegen die entsprechenden Chunk Hash überprüfen, bevor das Bild des Geräts blinken.

## <a name="span-idcheckingthesignatureonthecatalogandcheckingthehashofthetableofhashesspanspan-idcheckingthesignatureonthecatalogandcheckingthehashofthetableofhashesspanspan-idcheckingthesignatureonthecatalogandcheckingthehashofthetableofhashesspanchecking-the-signature-on-the-catalog-and-checking-the-hash-of-the-table-of-hashes"></a><span id="Checking_the_signature_on_the_catalog_and_checking_the_hash_of_the_table_of_hashes"></span><span id="checking_the_signature_on_the_catalog_and_checking_the_hash_of_the_table_of_hashes"></span><span id="CHECKING_THE_SIGNATURE_ON_THE_CATALOG_AND_CHECKING_THE_HASH_OF_THE_TABLE_OF_HASHES"></span>Überprüfen die Signatur im Katalog sowie zum Überprüfen von des Hashs der Tabelle des weiteren


Das Ziel bei der Überprüfung der Signatur ist dafür sorgen, dass die Signatur im Katalog mit dem PK Zertifikat auf dem Telefon übereinstimmt. Dieser Ansatz ermöglicht eine Signatur vorab ohne das vollständige Bild auf das Gerät vor dem blinken gesucht. Das Signatur Kontrollkästchen wird vorausgesetzt, dass dieser Katalog Hashfunktion SHA1 enthält.

Microsoft bietet ein UEFI-Protokoll, das eine Funktion zu diesem Zweck EFI verfügbar macht\_ÜBERPRÜFEN\_SIG\_UND\_HASH. Weitere Informationen finden Sie unter [UEFI Protokoll Signatur überprüfen](https://msdn.microsoft.com/library/windows/hardware/dn772115). Diese Funktion überprüft auch den Hash der Tabelle des weiteren.

**Beispiel-Codefluss**

1.  Zeiger auf Daten im Katalog und Hash-Tabelle herstellen.

2.  Bestimmen Sie die Größe der Katalog und Hash Tabellendaten in Byte.

3.  EFI rufen Sie mithilfe der [UEFI überprüfen Signatur Protokoll](https://msdn.microsoft.com/library/windows/hardware/dn772115) \_ÜBERPRÜFEN\_SIG\_UND\_HASH die Zeiger und Daten Größen übergeben.

4.  Basierend auf der EFI-Rückgabecode fortzusetzen, um das Bild zu verarbeiten oder Buchen ein Wertpapiers Nachricht wie EFI\_SECURITY\_VERLETZUNG.

**Hinweis**  
Wenn auf dem Gerät nicht sicheren Boot aktiviert ist, wird ein Eincheckvorgang Signatur nicht ausgeführt.

 

## <a name="span-idcheckingthedataagainstthehashtableentriesspanspan-idcheckingthedataagainstthehashtableentriesspanspan-idcheckingthedataagainstthehashtableentriesspanchecking-the-data-against-the-hash-table-entries"></a><span id="Checking_the_data_against_the_hash_table_entries"></span><span id="checking_the_data_against_the_hash_table_entries"></span><span id="CHECKING_THE_DATA_AGAINST_THE_HASH_TABLE_ENTRIES"></span>Überprüfen die Daten mit den Einträgen der Hash-Tabelle


Das blinkende OEM-Tool muss die Daten vor dem Einträge in der Hash überprüfen. Informationen zum blinkende [Developing benutzerdefinierte OEM blinkende Tools](developing-custom-oem-flashing-tools.md)-Tool.

**Beispiel-Codefluss**

Eine Reihe von gültige Methoden kann verwendet werden. Ein Beispiel ist hier dienen als Ausgangspunkt Allgemeine Referenz bereitgestellt.

1.  Rufen Sie die neuen Hashdaten aus der Hashtabelle in der Kopfzeile des Bilds.

2.  Einrichten einer Schleife Datenblöcke im Bild zu verarbeiten.

3.  Ein Zeiger auf den Hash des aktuellen Abschnitts der Daten abgerufen.

4.  Vergleichen Sie den Hash der aktuellen Abschnitt gegen die Verwendung einer Funktion wie **Memcmp**Hash Tabellendaten ein.

5.  Wenn die beiden Hashs übereinstimmen, erhöhen Sie den Zeiger, und machen Sie sich bereit, um den nächsten Datenblock zu überprüfen.

6.  Wenn die beiden Hashs nicht übereinstimmen, können Sie eine Nachricht Sicherheit wie Veröffentlichen und beenden Sie alle Verarbeitung des Bilds **EFI\_SECURITY\_VERLETZUNG**.

7.  Die Verarbeitung, bis es keine weiteren Daten im Bild sind, um die Verarbeitung fort.

Info für die hier beschriebenen FFU Elemente finden Sie unter [FFU Bildformat](ffu-image-format.md).

## <a name="span-iderrorhandlingspanspan-iderrorhandlingspanspan-iderrorhandlingspanerror-handling"></a><span id="Error_handling"></span><span id="error_handling"></span><span id="ERROR_HANDLING"></span>Fehlerbehandlung


Standard-Fehlerbehandlung Codetechniken sollte verwendet werden. Einige allgemeine Situationen zu behandeln sind hier aufgeführt:

-   Fehlende Katalogdaten

-   Nicht genügend Ressourcen

-   Leeres Bild

## <a name="span-idcleanupandexitspanspan-idcleanupandexitspanspan-idcleanupandexitspanclean-up-and-exit"></a><span id="Clean_up_and_exit"></span><span id="clean_up_and_exit"></span><span id="CLEAN_UP_AND_EXIT"></span>Bereinigen und beenden


Führen Sie die standard-Methode und Bereinigung alle erstellten Sie Arrays oder sonstigen Objekte, vor dem Beenden des blinkenden Codes. Der Prozess beenden sollte die endgültige zurückgegeben **EFI\_STATUS** Wert. Angenommen, wenn das Bild gültig ist, Sie können einen Wert zurück `EFI_SUCCESS`.

## <a name="span-idencryptionlibraryspanspan-idencryptionlibraryspanspan-idencryptionlibraryspanencryption-library"></a><span id="Encryption_library"></span><span id="encryption_library"></span><span id="ENCRYPTION_LIBRARY"></span>Verschlüsselungsbibliothek


Suchen und eine entsprechende Verschlüsselung Clientbibliothek im Bild zur Unterstützung von Hashüberprüfung, wie etwa EFI miteinbeziehen\_HASH\_PROTOKOLL.

## <a name="span-idrelatedtopicsspanrelated-topics"></a><span id="related_topics"></span>Verwandte Themen


[Entwickeln von benutzerdefinierten OEM blinkendes tools](developing-custom-oem-flashing-tools.md)

 

 






