---
Description: "Windows 10 Mobile bringt die Features in Windows 10 für mobile Geräte verfügbar."
ms.assetid: 8ee995d9-420d-4bba-9ab0-decf4b3dc39b
MSHAttr: PreferredLib:/library
title: Mobile Bereitstellung und imaging
author: CelesteDG
ms.openlocfilehash: 59eab072c3b7fc19a5a6434f23b3d09d658a9e86
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="mobile-deployment-and-imaging"></a>Mobile Bereitstellung und imaging


Windows 10 Mobile bringt die Features in Windows 10 für mobile Geräte verfügbar. Auf Geräten, die die erforderliche Hardware-Komponenten zu erfüllen, fügt Windows 10 Mobile darüber hinaus auch Features wie kontinuierliche für Telefone, die Benutzer ihre Windows Phone, einen Monitor und sogar ein mithilfe von Maus und Tastatur verbinden, wie bei einem Desktop funktioniert Telefon tätigen.

## <a name="span-idintendedaudiencespanspan-idintendedaudiencespanspan-idintendedaudiencespanintended-audience"></a><span id="Intended_audience"></span><span id="intended_audience"></span><span id="INTENDED_AUDIENCE"></span>Zielgruppe


Die Gesamtheit oder Abschnitten dieser exemplarischen Vorgehensweise ist für die Verwendung durch vorgesehen:

-   Neue oder erfahrene Windows OEMs und ODMs zum Erstellen und Bereitstellen einer angepassten Abbilds Windows 10 Mobile wünschen.

-   Mobilfunkbetreiber, wer den Prozess der erstellen und Bereitstellen einer angepassten Abbilds mobilen ermitteln möchten.

## <a name="span-idoverviewspanspan-idoverviewspanspan-idoverviewspanoverview"></a><span id="Overview"></span><span id="overview"></span><span id="OVERVIEW"></span>Übersicht über


Diese mobilen Bereitstellung und imaging Handbuch wird basierend auf den zwei Methoden, um Sie anpassen und erstellen können, um ein Windows-Abbild auf einem mobilen Gerät flash aufgebaut:

**Schritt 1:** [Vorbereiten für Windows mobile Entwicklung](preparing-for-windows-mobile-development.md) bietet Informationen zu der Preprequisites Tools und wie Sie Ihre Entwicklungsumgebung einrichten.

**Schritt 2:** [Erstellen von mobilen Paketen](creating-mobile-packages.md) bietet schrittweise Informationen zum Erstellen einer mobilen Paket mit einer Beispieltreiber und beim Deklarieren einer MCSF Einstellung mithilfe des MCSF Settings Schemas innerhalb einer. pkg.xml.

**Schritt 3:** [Konfigurieren des Layouts Start](configure-the-start-layout.md) zeigt zum Anpassen des Layouts Start auf mobilen Geräten Einbeziehung Web, Hyperlinks, sekundäre Kacheln, Ordner und usw.. Start-Layout verwendet ein neues einheitliches Schema in Win\_Schwellenwert, damit es nicht wichtig ist, wenn Sie die Einstellungen MCSF starten oder der Einstellungen für die Bereitstellung von Windows starten verwenden, um das Layout für das Abbild hinzufügen. Beachten Sie außerdem, dass das Standardlayout auf mobilen Geräten nur im Rahmen des imaging-Prozesses angepasst werden kann.

**Schritt 4:** Nachdem Sie alle vorbereitenden Schritte durchgeführt haben, können Sie anpassen und erstellen Ihr Bild zu starten. Es wird empfohlen, zuerst den klassischen mobilen Bereitstellungsprozess erlernen, da MCSF weiterhin eine robustere Reihe von Anpassungen bereitstellt, die für ihre Bild OEMs und ODMs konfigurieren können. Jedoch bietet Windows Provisioning viele Unternehmensrichtlinien, Registrierung und Enterprise-Einstellungen über MCSF nicht verfügbar, sodass es wird empfohlen, vertraut mit der Bereitstellung von Windows-Bereitstellungsprozess zu.

-   [Teil 1: Classic mobilen Bereitstellung](lab-1--classic-mobile-deployment.md)

    Konfigurieren Anpassungen, die sind nur verfügbar über die verwaltete zentralisierte Einstellungen Framework (MCSF), und verwenden die klassische Windows mobile-Befehlszeilentools-Paketen und einer angepassten Abbilds erstellen, und klicken Sie dann flash das Bild zu einem Gerät.

-   [Teil 2: Mobile Bereitstellung mithilfe von Windows-Bereitstellung](lab-2--mobile-deployment-using-windows-provisioning.md)

    Verwenden der Windows-Bereitstellung Antwortdatei (WPAF) Anpassung Einstellungen konfigurieren, die nur über die Bereitstellung von Windows-Framework zur Verfügung stehen an. Verwenden Sie der WPAF mit einer MCSF CAF als Eingaben in der Befehlszeilenschnittstelle Windows Imaging und Konfiguration Designer (ICD) zum Erstellen eines benutzerdefinierten mobilen Abbilds.

 

 



