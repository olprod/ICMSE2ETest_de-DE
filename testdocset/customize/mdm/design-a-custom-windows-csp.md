---
title: Entwerfen eines benutzerdefinierten Konfiguration-Dienstanbieters
description: Entwerfen eines benutzerdefinierten Konfiguration-Dienstanbieters
MS-HAID:
- p\_phDeviceMgmt.designing\_a\_custom\_configuration\_service\_provider
- p\_phDeviceMgmt.design\_a\_custom\_windows\_csp
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 0fff9516-a71a-4036-a57b-503ef1a81a37
ms.openlocfilehash: 2e4473541cfe15923f5cdb3f04f4abf1b0f7d315
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="design-a-custom-configuration-service-provider"></a>Entwerfen eines benutzerdefinierten Konfiguration-Dienstanbieters

Um eine benutzerdefinierte Konfiguration-Dienstanbieter zu entwerfen, muss der OEM die folgenden Schritte ausführen:

1.  Einrichten von Knoten Semantik
2.  Die Konfiguration des Dienstanbieters Unterstruktur Shape
3.  Wählen Sie ein Transactioning-Schema für jeden Knoten
4.  Bestimmen der Knotenvorgänge

Weitere Informationen zu größeren Prozesses einen neuen Konfiguration-Dienstanbieter zu schreiben finden Sie unter [Erstellen einer benutzerdefinierten Konfiguration-Dienstanbieter](create-a-custom-configuration-service-provider.md).

## <a name="establish-node-semantics"></a>Einrichten von Knoten Semantik

Ermitteln Sie zunächst, basiert die Menschen, mit denen Knoten hinsichtlich des Typs der Daten in der Registrierung gespeichert werden.

Knoten können nichts von abstrakte Konzepte oder Sammlungen (wie e-Mail-Konten oder Verbindungseinstellungen) auf mehr als eine konkrete Objekte (beispielsweise Registrierungsschlüssel und Werte, Verzeichnisse und Dateien) dargestellt.

### <a name="example"></a>Beispiel

Angenommen, haben ein Dienstanbieter der hypothetischer e-Mail-Konfiguration dieser Knoten:

-   Konto: Den Namen des e-Mail-Kontos (beispielsweise "Hotmail")

-   Benutzername: Den Benutzer oder e-Mail-Adresse("exampleAccount@hotmail.com")

-   Kennwort: Das Kennwort des Benutzers

-   Server: DNS-Adresse des Servers ("e-Mail-serv1-example.mail.hotmail.com")

Die `Account`, `Username`, und `Server` Knoten textbasierten Informationen zu dem e-Mail-Konto, die e-Mail-Adresse des Benutzers und die Adresse des Servers mit diesem Konto verknüpften halten würde. Die `Password` Knoten, möglicherweise jedoch einen binären Hash das Kennwort des Benutzers enthalten.

## <a name="shape-the-configuration-service-providers-subtree"></a>Die Konfiguration des Dienstanbieters Unterstruktur Shape

Entscheiden Sie nach dem bestimmen, was die Knoten darstellen, wobei jeder Knoten in der Hierarchie Einstellungen passt.

Der Stammknoten der Unterstruktur einer Konfiguration des Dienstanbieters muss der Name des Dienstanbieters Konfiguration sein. In diesem Beispiel wird der Stammknoten `Email`.

Alle Knoten im vorherigen Schritt definierten muss unter Stammknoten der Konfigurationsdienstanbieter befinden. Endknoten zum Speichern von Daten verwendet werden soll, und innere Knoten zum Gruppieren der Daten in logische Gruppen verwendet werden sollte. Knoten-URIs muss eindeutig sein. Anders ausgedrückt, können keine zwei Knoten derselben übergeordneten und denselben Namen aufweisen.

Es gibt drei Standardszenarien für gruppieren und Strukturieren von Knoten:

-   Wenn alle Daten auf dieselbe Komponente gehört, und keine weiteren kategorisieren oder Gruppierung erforderlich ist, können Sie eine flache Struktur erstellen, in der alle Werte, die direkt unter dem Stammknoten gespeichert sind. Beispiele für dieses Design finden Sie unter [DevInfo Konfigurationsdienstanbieter](devinfo-csp.md) [HotSpot Konfigurationsdienstanbieter](hotspot-csp.md)und [w4 APPLICATION Configuration-Dienstanbieter](w4-application-csp.md).

-   Wenn die Konfiguration des Dienstanbieters Knoten einer bereits vorhandenen Entitäten darstellen, deren Struktur (wie Verzeichnisse und Dateien) klar definiert ist, können die Konfiguration des Dienstanbieters Knoten die vorhandene Struktur einfach spiegeln.

-   Wenn die Daten vom Typ oder eine Komponente gruppiert werden müssen, ist eine komplexere Struktur erforderlich. Dies gilt insbesondere dann, wenn mehrere Instanzen des Datasets auf dem Gerät vorhanden sein können, und jeder Gruppe mit einer ID, Kontonamen oder Kontotyp indiziert. In diesem Fall müssen Sie eine komplexere Struktur erstellen. Beispiele finden Sie unter [ActiveSync Konfiguration-Dienstanbieter](activesync-csp.md), [CertificateStore Konfiguration-Dienstanbieter](certificatestore-csp.md)und [CMPolicy Konfiguration-Dienstanbieter](cmpolicy-csp.md).

### <a name="example"></a>Beispiel

Die folgende Abbildung zeigt eine falsche Möglichkeit zum Strukturieren der hypothetische `Email` Konfiguration-Dienstanbieter. Das innere `Account` Knoten die Datengruppe Konto (Servername, Benutzername und Kennwort).

![Bereitstellung\-Customcsp\-Beispiel 1](images/provisioning-customcsp-example1.png)

Die Konto-Knoten in diesem Design sind jedoch nicht eindeutig. Obwohl die Knoten sinnvolle gruppiert sind, ist der Pfad für die einzelnen Endknoten mehrdeutige. Es ist nicht möglich, die beiden eindeutig `Username` Knoten, beispielsweise oder auf zuverlässig demselben Knoten mit demselben Pfad. Diese Struktur ist nicht funktionsfähig. Die einfachste Lösung für dieses Problem ist in der Regel einen interior-Knoten (den Knoten Gruppierung) durch Ersetzen:

1.  Fördern der Verwendung von untergeordneten Knoten.

2.  Verwenden den Wert des Knotens als den Namen des neuen Knotens interior.

Folgende Entwurfsziele übermittelt die gleichen Maßes an Informationen als die erste entwerfen, aber alle Knoten haben einen eindeutigen Pfad, und daher es funktionieren.

![Bereitstellung\-Customcsp\-Beispiel 2](images/provisioning-customcsp-example2.png)

In diesem Fall die `Server` Knoten haben ersetzen eine Ebene nach oben heraufgestuft wurde die `Account` Knoten und deren Werte sind jetzt als den Namen der Knoten verwendet. Beispielsweise konnten Sie zwei andere e-Mail-Konten auf dem Telefon, mit dem Server Namen "www.hotmail.com" und "exchange.microsoft.com", von denen jeder einen Benutzernamen und ein Kennwort gespeichert haben.

Beachten Sie, dass der Vorgang der Konfiguration des Dienstanbieters Unterstruktur shaping Wahl des Schemas für jeden Knoten Transactioning beeinflusst. Wenn möglich, sollten Peerknoten keine Abhängigkeiten voneinander enthalten. Symbol Abhängigkeiten als über-/untergeordnete Beziehungen erstellen obligatorische Gruppen von Standardeinstellungen, durch die Konfiguration Service Provider Entwicklung erschwert.

## <a name="choose-a-transactioning-scheme-for-each-node"></a>Wählen Sie ein Transactioning-Schema für jeden Knoten

Entscheiden Sie für jeden Knoten, ob *externe Transactioning* oder *interne Transactioning* verwenden, um die Transaktion Phasen (Rollback Persistenz, Rollback und Engagement) für den Knoten zu verwalten.

Externe Transactioning ist die einfachste Möglichkeit, weil sie ConfigManager2 zur automatischen Verarbeitung des Knotens Transactioning ermöglicht.

Sie müssen jedoch interne Transactioning für die folgenden Typen von Knoten verwenden:

-   Ein Knoten, der die **Execute** -Methode unterstützt.

-   Ein Knoten mit vertraulichen Informationen (beispielsweise ein Kennwort), der nicht in nur-Text im Dokument Rollback ConfigManager2 gespeichert werden muss.

-   Ein Knoten, der eine Abhängigkeit auf einem anderen Knoten aufweist, die nicht übergeordnet ist. Beispielsweise ein übergeordneten Knoten besitzt zwei untergeordneten Elementen, die beide sind erforderlich, die Konfiguration Dienstanbieter konnte mithilfe des internen Transactioning verzögern das Konto bereitstellen, bis Sie beide Werte festgelegt sind.

Sie können auch Transactioning Modi, in Ihrer Konfigurationsdienstanbieter, mithilfe von internen Transactioning für einige Vorgänge, aber externe Transactioning für andere Benutzer zu kombinieren. Weitere Informationen über das Schreiben von einer intern ungeachtet Knoten finden Sie unter der [ICSPNodeTransactioning](icspnodetransactioning.md) -Schnittstelle.

## <a name="determine-node-operations"></a>Bestimmen der Knotenvorgänge

Die verfügbaren Vorgänge für jeden Knoten variiert je nach den Zweck des Dienstanbieters Konfiguration. Der Konfigurationsdienstanbieter werden einfacher zu nutzen, wenn die Vorgänge konsistent sind. Weitere Informationen über die unterstützten Vorgänge finden Sie unter der [ICSPNode](icspnode.md) -Schnittstelle.

Für extern ungeachtet Knoten muss eine Implementierung der Vorgang der contrary Vorgänge in der folgenden Tabelle dargestellt wird, um ein Rollback für den Vorgang zulassen enthalten.

Intern ungeachtet Knoten, für die Methode, die contrary Befehle für jeden Befehl implementiert empfohlen, aber nicht erforderlich.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th>Knoten-Vorgang</th>
<th>Contrary Knoten-Vorgang</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><strong>Add</strong></p></td>
<td><p><strong>Klar</strong> und <strong>DeleteChild</strong></p></td>
</tr>
<tr class="even">
<td><p><strong>Kopie</strong></p></td>
<td><p>Um auf einen neuen Knoten zu kopieren: <strong>Löschen</strong> und <strong>DeleteChild</strong></p>
<p>Zum Kopieren von einem vorhandenen Knoten: <strong>Hinzufügen</strong> und <strong>SetValue</strong></p></td>
</tr>
<tr class="odd">
<td><p><strong>Transparent</strong></p></td>
<td><p>Um den Status der dem gelöschten Knoten wiederherzustellen: <strong>SetzenWert</strong> und <strong>SetProperty</strong></p></td>
</tr>
<tr class="even">
<td><p><strong>DeleteChild</strong></p></td>
<td><p>So stellen Sie den alten Knoten wieder her: <strong>hinzufügen</strong></p></td>
</tr>
<tr class="odd">
<td><p><strong>DeleteProperty</strong></p></td>
<td><p>Die gelöschte Eigenschaft wiederherzustellen: <strong>SetProperty</strong></p></td>
</tr>
<tr class="even">
<td><p><strong>Execute</strong></p></td>
<td><p>Extern ungeachtet Knoten unterstützt den <strong>Execute</strong> -Befehl nicht.</p></td>
</tr>
<tr class="odd">
<td><p><strong>GetValue</strong></p></td>
<td><p>Keine</p></td>
</tr>
<tr class="even">
<td><p><strong>Move</strong></p></td>
<td><p>Wiederherstellen einen Quellknoten: <strong>verschieben</strong></p>
<p>Wiederherstellen ein Knotens überschrieben Ziel: <strong>Hinzufügen</strong> und <strong>SetValue</strong></p></td>
</tr>
<tr class="odd">
<td><p><strong>SetValue</strong></p></td>
<td><p>Um den vorherigen Wert wiederherzustellen: <strong>SetValue</strong></p></td>
</tr>
</tbody>
</table>

 

 





