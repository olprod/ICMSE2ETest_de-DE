---
title: Bereitstellen von Windows mithilfe von Windows Assessment Services
description: Bereitstellen von Windows mithilfe von Windows Assessment Services
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: e86b9140-36dc-4802-b672-ffe94f1eed6a
ms.prod: W10
ms.mktglfcycl: plan
ms.sitesec: msdn
ms.openlocfilehash: f507b2c69910cd201fda42f431a47118d2cb9bd6
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="deploy-windows-using-windows-assessment-services"></a>Bereitstellen von Windows mithilfe von Windows-Assessment-Services


Es gibt drei Möglichkeiten zum Festlegen up Aufträge und zugehörigen Ressourcen. Sie können einen Auftrag einrichten, um die folgenden Schritte aus:

-   Bewerten von Computern, die bereits unterstützte Betriebssystem ausführen.

-   Bereitstellen Sie ein unterstütztes Betriebssystem auf einem Computer mithilfe der Windows-Assessment-Dienste und dann bewerten Sie des Computers.

-   Verwenden Sie anderer Bereitstellungstools oder Methoden, um ein unterstütztes Betriebssystem auf einem Computer bereitstellen, und klicken Sie dann bewerten Sie des Computers.

In diesem Thema werden alle drei dieser Optionen zur Bereitstellung von.

**Anlagen eines Auftrags hinzufügen und Bereitstellen eines Abbilds**

1.  Erstellen Sie in der Windows-ASC oder öffnen Sie ein Projekt.

2.  Klicken Sie unter **Einstellungen eines Auftrags für** **Übersicht**auf und stellen Sie sicher, dass das Kontrollkästchen **Bild anwenden** aktiviert ist.

3.  Wenn Sie übereinstimmenden Plug & Play einschleusen Treiber aus einer dynamische Treiber Bereitstellung Treiber während der Bereitstellung von Bild speichern möchten, wählen Sie **Dynamische Treiber-Bereitstellung**.

4.  Klicken Sie unter **Einstellungen für** **Anlagen**auf und klicken Sie dann auf **Hinzufügen** , um die Computer auszuwählen, die auf den Auftrag ausgeführt werden soll.

5.  Wählen Sie im Fenster **Evaluation Objekte auswählen** die Computer, die Sie verwenden möchten, bewerten, klicken Sie auf **Weiter**und dann auf **Fertig stellen**.

6.  Die Computer auf der rechten Seite des Windows ASC unter **Evaluation Anlagen**angezeigt werden. Wählen Sie einen Computer, klicken Sie auf **Das Bild ändern**, wählen Sie das Bild, das Sie auf diesem Computer anwenden möchten, und klicken Sie dann auf **OK**.

    **Hinweis**  
    Der Computer und die Architektur Bild müssen übereinstimmen, außer dass Sie ein Bild X86 basierend auf einem X64-basierten Computer bereitstellen auswählen können.

     

**Eines Auftrags für Objekte hinzu, und verwenden Sie benutzerdefinierte Bereitstellung**

1.  Erstellen Sie in der Windows-ASC oder öffnen Sie ein Projekt.

2.  Klicken Sie unter **Einstellungen eines Auftrags für** **Übersicht**auf und stellen Sie sicher, dass das Kontrollkästchen **Bild anwenden** aktiviert ist.

3.  Deaktivieren Sie das Kontrollkästchen **Dynamische Treiber-Bereitstellung** .

4.  Klicken Sie unter **Einstellungen eines Auftrags für**klicken Sie auf **Objekte**, und klicken Sie dann auf **Hinzufügen** , um die Computer auszuwählen, die auf den Auftrag ausgeführt werden soll.

5.  Klicken Sie im Fenster **Wählen Evaluation Objekte** wählen Sie die Computer, die Sie bewerten möchten, und klicken Sie dann auf **Weiter**.

6.  Klicken Sie auf ** &lt;Predeployed Bild verwenden&gt;**, und klicken Sie dann auf **Fertig stellen**.

    **Hinweis**  
    Beim Planen eines Auftrags mithilfe von ** &lt;Predeployed Bild verwenden&gt;**, der Auftrag wird nicht gestartet werden, bis Sie Windows bereitstellen und ausführen ** \\ \\WASServer %\\entspannen\\Skripts\\Testmachine\\completedeployment.cmd AUTO** an einer Eingabeaufforderung mit erhöhten Rechten.

     

**So eines Auftrags für Objekte hinzu, ohne die Bereitstellung von einem Bild**

1.  Erstellen Sie in der Windows-ASC oder öffnen Sie ein Projekt.

2.  Klicken Sie unter **Einstellungen eines Auftrags für**auf **Übersicht**und deaktivieren Sie das Kontrollkästchen **Bild übernehmen** .

3.  Klicken Sie unter **Einstellungen für** **Anlagen**auf und klicken Sie dann auf **Hinzufügen** , um die Computer auszuwählen, die auf den Auftrag ausgeführt werden soll.

4.  Klicken Sie im Fenster **Wählen Sie Evaluation Assets** wählen Sie die Computer, die Sie ermitteln möchten, und klicken Sie dann auf **Fertig stellen**.

## <a name="related-topics"></a>Verwandte Themen


[Häufige Szenarien Windows Assessment Services](windows-assessment-services-how-to-topics--wastechref.md)

 

 







