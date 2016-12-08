---
author: Justinha
Description: "PAE/n x/SSE2-Support-Anforderung Guide für Windows 8"
ms.assetid: 2100166b-fcd7-46af-953e-846e70090fae
MSHAttr: PreferredLib:/library/windows/hardware
title: "PAE/n x/SSE2-Support-Anforderung Guide für Windows 8"
ms.openlocfilehash: 107141b0003af94ee5cf5848252fae143a82889f
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="paenxsse2-support-requirement-guide-for-windows-8"></a>PAE/n x/SSE2-Support-Anforderung Guide für Windows 8


In diesem Thema wird beschrieben, Prozessor-Unterstützung für die Anforderung PAE/n x/SSE2 in Windows 8 und Fehlersituationen und Szenarios, in denen Kunden auftreten können, wenn Computer nicht die Anforderung erfüllen.

Dieser Inhalt gilt für Windows 8 und Windows Server® 2012.

**In diesem Thema:**

-   [Übersicht über die](#overview)

-   [Bereich der Auswirkungen](#scope)

-   [Support-Anforderungen](#support)

-   [Häufig gestellte Fragen](#faq)

## <a name="span-idoverviewspanspan-idoverviewspanoverview"></a><span id="overview"></span><span id="OVERVIEW"></span>Übersicht über die


### <a name="span-idno-executenxspanspan-idno-executenxspanspan-idno-executenxspanno-execute-nx"></a><span id="No-eXecute__NX_"></span><span id="no-execute__nx_"></span><span id="NO-EXECUTE__NX_"></span>No eXecute (n x)

No eXecute (n x) ist ein Prozessorfeature, mit der Seiten im Arbeitsspeicher als nicht ausführbar markiert werden kann. Das Feature ermöglicht die CPU zum Schutz des Systems vor Angriffen durch Schadsoftware. Das Feature n x verhindert, dass Schadsoftware ausführbaren Code zugegriffen werden Regionen Arbeitsspeicher abgelegt. Windows 8 erfordert, dass Systeme Prozessoren verfügen, die n x unterstützen und n x muss aktiviert werden, für wichtige Sicherheitsvorkehrungen effektive und potenzielle Sicherheitsrisiken zu vermeiden.

In diesem Thema definiert *n x* speziell für den n x-Prozessor, d. h. bit bezieht sich der Begriff von AMD oder die entsprechende XD Bit-Prozessor, die zur featureunterstützung von (Data Execution Prevention, DEP) in Microsoft Windows durch Intel definiert ist.

Datenausführungsverhinderung hilft beim bösartigen Code-Ausführung von Datenseiten zu verhindern. Die 32-Bit-Version von Windows verwendet eine der folgenden Features für die Datenausführungsverhinderung Unterstützung:

-   Protection-Prozessorfeature Seite der AMD-defined No eXecute (n x)

-   Intel definierte eXecute deaktivieren (XD)-Bit-Funktion

Verwendung dieser Prozessorfeatures, der X86 (32-Bit) Prozessor muss im physischen Extension (PAE) Modus ausgeführt werden. Die 64-Bit-Version von Windows verwendet das n x Prozessor-Feature auf 64-Bit-Erweiterungen und bestimmte Werte aus dem Feld Access Rechte Seite Tabelle Eintrag (PTE) Prozessoren mit Intel Itanium Prozessor Familie (IPF).

Zusätzlich zur Datenausführungsverhinderung verschiebt Address Space Layout zufällige (ASLR) ausführbare Bilder in zufällige Positionen Wenn ein System startet, wodurch er nach Betrieb vorhersehbar bösartigem Code schwieriger. ASLR und DEP sind effektive nur, wenn sie gemeinsam verwendet werden. N x muss für diese zwei wichtigen Windows-Sicherheitsvorkehrungen effektiven bleiben aktiviert sein. Weitere Informationen finden Sie unter [Windows ISV Software Sicherheitsmaßnahmen kombiniert](http://go.microsoft.com/fwlink/p/?LinkId=698535).

### <a name="span-idphysicaladdressextensionpaespanspan-idphysicaladdressextensionpaespanspan-idphysicaladdressextensionpaespanphysical-address-extension-pae"></a><span id="Physical_Address_Extension__PAE_"></span><span id="physical_address_extension__pae_"></span><span id="PHYSICAL_ADDRESS_EXTENSION__PAE_"></span>Physische Adresse-Erweiterung (PAE)

Im Modus das n x Prozessor-Feature verwenden Physical Address Extension (PAE) muss der Prozessor ausgeführt werden. PAE ist ein Prozessor, ermöglicht X86 Prozessoren für den Zugriff auf mehr als 4 GB des physischen Arbeitsspeichers auf fähig Versionen von Windows-Features. Der Intel Itanium und X64 Prozessorarchitekturen können mehr als 4 GB des physischen Arbeitsspeichers systemintern zugreifen, und das Äquivalent von PAE nicht bereitstellen. PAE wird von 32-Bit-Versionen von Windows auf nur X86-basierte Systeme unterstützt.

Wenn DEP auf einem System mit einem Prozessor, der das Feature n x unterstützt aktiviert ist, ist PAE automatisch aktiviert.

### <a name="span-idstreamingsimdextensions2sse2spanspan-idstreamingsimdextensions2sse2spanspan-idstreamingsimdextensions2sse2spanstreaming-simd-extensions-2-sse2"></a><span id="Streaming_SIMD_Extensions_2__SSE2_"></span><span id="streaming_simd_extensions_2__sse2_"></span><span id="STREAMING_SIMD_EXTENSIONS_2__SSE2_"></span>Streaming SIMD Extensions (SSE2) 2

Alle Prozessoren, die n x unterstützen unterstützen auch Streaming SIMD Extensions 2 (SSE2). SSE2 Inseln-Befehlssatz ein Intel einzelnen Anweisung mehrere Daten (SIMD) Prozessor zusätzliche AMD umfasst auch SSE2-Unterstützung mit Opteron und Athlon 64 Bereichen der AMD64-Prozessoren. Alle Prozessoren, die n x unterstützen unterstützen auch SSE2. Viele Windows 8-Clientanwendungen müssen Codepfade, die die SSE2-Anweisung festgelegt haben. SSE2 ist eine Voraussetzung für Windows 8.

## <a name="span-idscopespanspan-idscopespanscope-of-implications"></a><span id="scope"></span><span id="SCOPE"></span>Bereich der Auswirkungen


Alle moderne Prozessoren unterstützen n x. N x kann im BIOS deaktiviert werden. Basierend auf verfügbaren Telemetriedaten, 1 Prozent der Systeme, das Windows® 7 ausführen, wird n x aufgrund eines Konfigurationsfehlers in der BIOS-Einstellung deaktiviert haben.

N x erfordert PAE-fähigen Prozessoren auf 32-Bit-Version von Windows. Alle 64-Bit-Prozessoren n x unterstützen, da sie Address Windowing Extensions (AWE) sind-beachten. Aus diesem Grund hat das Problem der älteren 32-Bit-Prozessoren, die nicht PAE-fähig sind keine Auswirkungen auf WOA Auswirkungen auf Windows Server (Windows Server 2012 64-Bit-nur ist). Die Prozessor-Anforderung wird nicht die Kunden auf moderne Systeme beeinträchtigen oder diese Systeme haben auf Systemen, die Anforderungen an das Logo für Windows 7, da erfüllen PAE-fähige 32-Bit-Prozessoren, die n x unterstützen und Aktivieren von n x aktiviert werden. Nur eine kleine Gruppe von Kunden mit einer sehr alten 32-Bit-Prozessoren ohne PAE/n x Unterstützung unter Windows 7 betroffen sind.

Windows 8 und Windows Server 2012 ist PAE erforderlich. Dies wirkt sich auf eine kleine Anzahl von Kunden, die älteren Hardware verfügen, der PAE nicht unterstützt. Auftreten von Fehlern bei der Installation von Windows 8 auf falsch konfigurierter virtuellen Computern (VMs). Windows Setup die Installation mit Fehler 0xc0000260 fehlschlägt und ein Rollback auf Windows 7.

Visual Studio gibt standardmäßig SSE2-Anweisungen aus. Anwendungen, die diese Anweisungen Absturz auf Systemen wenden Sie sich an, die ältere Prozessoren, die keine für SSE2 Unterstützung, wie beschrieben in [SSE2-Anweisungen generiert, wenn neben angegeben ist](http://connect.microsoft.com/VisualStudio/feedback/details/565959).

## <a name="span-idsupportspanspan-idsupportspansupport-requirements"></a><span id="support"></span><span id="SUPPORT"></span>Support-Anforderungen


Dieser Abschnitt beschreibt Maßnahmen, mit die sichergestellt, dass Prozessoren auf Systeme, die Windows 8 ausgeführt werden PAE, n x und SSE2-Support-Anforderungen erfüllen.

### <a name="span-idwindows8logorequirementspanspan-idwindows8logorequirementspanspan-idwindows8logorequirementspanwindows-8-logo-requirement"></a><span id="Windows_8_Logo_requirement"></span><span id="windows_8_logo_requirement"></span><span id="WINDOWS_8_LOGO_REQUIREMENT"></span>Windows 8-Logo-Anforderung

Windows 8-Zertifizierung Hardwareanforderung erfordert, dass alle Treiber zusammen mit Ausführungsschutz, um sicherzustellen, dass ordnungsgemäße Gerät und Treiber Systemverhalten normal ausgeführt werden müssen. Treiber müssen Code aus der Stack, ausgelagerte Pool- und Sitzungspool nicht ausgeführt werden. Treiber müssen nicht nicht geladen werden, wenn PAE-Modus aktiviert ist. System-Firmware benötigen n x auf und die Datenausführungsverhinderung Richtlinie muss nicht **Immer**OFF festgelegt werden. Ein Test Zertifizierung ist eingeschlossen, um zu bestätigen, dass ein System diese n x Support Anforderung erfüllt.

Weitere Informationen finden Sie unter [Windows-Zertifizierungsstelle Hardwareanforderungen](http://go.microsoft.com/fwlink/p/?linkid=329939).

### <a name="span-idhardwarecompatibilitycheckinwindowssetupspanspan-idhardwarecompatibilitycheckinwindowssetupspanspan-idhardwarecompatibilitycheckinwindowssetupspanhardware-compatibility-check-in-windows-setup"></a><span id="Hardware_compatibility_check_in_Windows_Setup"></span><span id="hardware_compatibility_check_in_windows_setup"></span><span id="HARDWARE_COMPATIBILITY_CHECK_IN_WINDOWS_SETUP"></span>Hardwarekomponenten Kompatibilität überprüfen Sie im Windows-Setup

Windows-Setup hat einen Hardware Kompatibilitätstest für PAE, n x und SSE2-Unterstützung auf dem System installieren. Systeme, die die Unterstützung von Prozessoren für PAE, n x und SSE2-Anforderung fehlschlagen werden als hard Blöcke für Windows 8 im Bericht Kompatibilität Problem gemeldet und Anzeigen der Nachricht: **Ihren PC CPU ist nicht kompatibel mit Windows 8**.

![PC kann nicht Windows 8 ausgeführt werden.](images/pccantrunwin8.jpg)

**Abbildung 1 CPU Inkompatibilität-Fehlermeldung**

**Hinweis**  
Diese Unterstützung Anforderung Überprüfung ist nur im neuen Windows-Setup und Upgrade Assistant verfügbar. Windows 8 enthält eine alternative Version des Windows-Setup im Ordner "Sources" des Installationsmediums, die dieses Kontrollkästchen nicht enthalten ist. Kunden, die versuchen, diese alternative Version von Windows-Setup auf einem System zu verwenden, die nicht PAE/n x/SSE2 erfüllt unterstützen Anforderungen treffen ein Fehler während des Installationsvorgangs und Rollback auf vorherige Betriebssystem.

Tritt auf in einen Neustart von Medium oder eines Netzwerkinstallationspfads wie Windows Deployment Services (WDS) während der Installation von Windows, keine Kompatibilität zu überprüfen. Für diese Szenarien ein System ohne n x oder SSE2-Unterstützung in einem schwerwiegenden Fehler führt (, der im folgenden Abschnitt **Kernel-Erweiterung** beschrieben) beim Setup versucht, starten Sie Windows.

 

### <a name="span-idkernelenhancementspanspan-idkernelenhancementspanspan-idkernelenhancementspankernel-enhancement"></a><span id="Kernel_enhancement"></span><span id="kernel_enhancement"></span><span id="KERNEL_ENHANCEMENT"></span>Kernel-Erweiterung

Um die Windows 8-Anforderung von n x erfüllen unterstützen Feature und SSE2-Anweisungen, der Windows 8-Kernel für diese Funktionen während der Initialisierung überprüft. Systeme, die keine n x oder SSE2 unterstützen können einen Windows 8-Kernel nicht initialisieren. Systeme, die in der Firmware n x deaktivieren können, haben die Option außer Kraft gesetzt; falsch konfigurierter Firmware bewirkt daher nicht zu einem Fehler beim Starten. Ein Versuch, ein System zu starten, die keine n x oder SSE2-Support-Suchergebnissen in einem schwerwiegenden Fehler vorhanden ist. Benutzer erhalten die nicht UNTERSTÜTZT\_PROZESSOR (0x0000005D) Fehler; zusammen mit vier Zeilen mit Informationen auf einem 32-Bit-System code:

-   Zeile 1 – ein Code, der angibt, dass ein Feature nicht vorhanden ist und eine Kennung für die CPU

-   Zeilen 2 bis 4 – Herstellerklassen-ID-Zeichenfolgen

Auf einem 64-Bit-System der Fehlercode Zeigt die gleichen nicht UNTERSTÜTZT\_PROZESSOR Code als auf einem 32-Bit-System, zusammen mit den folgenden vier Zeilen der Informationen:

-   Zeile 1 – den Inhalt des Registers Standardfeatures

-   Zeile 2 – der Inhalt der erweiterten Features registrieren

-   Zeilen 3 bis 4 – beide 0

## <a name="span-idfaqspanspan-idfaqspanfaqs"></a><span id="faq"></span><span id="FAQ"></span>Häufig gestellte Fragen


### <a name="span-idsupportnxspanspan-idsupportnxspanhow-do-i-know-if-my-system-supports-nx-or-sse2"></a><span id="supportnx"></span><span id="SUPPORTNX"></span>Wie weiß ich, wenn mein System n x oder SSE2 unterstützt?

Sie können das Befehlszeilendienstprogramm [Coreinfo](http://go.microsoft.com/fwlink/p/?linkid=246771) zum Abrufen einer Systeminformationen Prozessor und überprüfen Sie PAE, n x und SSE2-Einträge in der Ausgabeliste verwenden. Ein **\*** Zeichen zeigt neben dem Namen einer unterstützte Funktion an. Eine **-** Zeichen angezeigt, wenn das Feature nicht unterstützt wird. Beispiel:

``` syntax
Coreinfo v3.04 - Dump information on system CPU and memory topology
Copyright (C) 2008-2012 Mark Russinovich
Sysinternals - www.sysinternals.com

AMD Athlon(tm) 64 X2 Dual Core Processor 4600+
x86 Family 15 Model 75 Stepping 2, AuthenticAMD
HTT*       Hyperthreading enabled
HYPERVISOR      -       Hypervisor is present
VMX             -       Supports Intel hardware-assisted virtualization
SVM             *       Supports AMD hardware-assisted virtualization
EM64T           *       Supports 64-bit mode

SMX             -       Supports Intel trusted execution
SKINIT          -       Supports AMD SKINIT
EIST            -       Supports Enhanced Intel Speedstep

NX              *       Supports no-execute page protection
PAGE1GB         -       Supports 1 GB large pages
PAE             *       Supports > 32-bit physical addresses
PAT             *       Supports Page Attribute Table
PSE             *       Supports 4 MB pages
PSE36           *       Supports > 32-bit address 4 MB pages
PGE             *       Supports global bit in page tables
SS              -       Supports bus snooping for cache operations
VME             *       Supports Virtual-8086 mode

FPU             *       Implements i387 floating point instructions
MMX             *       Supports MMX instruction set
MMXEXT          *       Implements AMD MMX extensions
3DNOW           *       Supports 3DNow! instructions
3DNOWEXT        *       Supports 3DNow! extension instructions
SSE             *       Supports Streaming SIMD Extensions
SSE2            *       Supports Streaming SIMD Extensions 2
SSE3            *       Supports Streaming SIMD Extensions 3
SSSE3           -       Supports Supplemental SIMD Extensions 3
SSE4.1          -       Supports Streaming SIMD Extensions 4.1
SSE4.2          -       Supports Streaming SIMD Extensions 4.2
……..
……..
```

Wenn PAE als nicht unterstützte in Coreinfo Ausgabe angezeigt wird, bedeutet dies, dass das System einen Prozessor verfügt, der nicht PAE-fähige und n x unterstützt keine. Wenn PAE gezeigt wird, wie unterstützt, aber n x wird nicht angezeigt, die in Coreinfo Ausgabe unterstützt werden:

-   Wenden Sie sich an die Featuregruppe, die vom Hersteller CPU zu ermitteln, ob n x vom Prozessor auf dem System unterstützt wird veröffentlicht wird.

-   Weist der Prozessor n x Support, möglicherweise das System eine falsch konfigurierter BIOS-Einstellung für n x Option unterstützen.

### <a name="span-idturnonnxspanspan-idturnonnxspanif-nx-is-supported-on-my-system-how-do-i-turn-on-nx"></a><span id="turnonnx"></span><span id="TURNONNX"></span>Aktivieren Wenn n x auf meinem System unterstützt wird, wie kann ich n x?

Auf einem System, das die n x unterstützt, finden Sie unter Hersteller des Systems Leitfaden zum Wechseln in die Option BIOS-Einstellungen, und suchen Sie nach dem n x oder XD Einstellungen unter der Registerkarte **Sicherheit** , um die Unterstützung von n x zu aktivieren. Wenn die BIOS-Einstellung für die Unterstützung von n x nicht im System verfügbar ist, müssen Sie möglicherweise wenden Sie sich an den Hersteller, um die Aktualisierung des BIOS.

**Hinweis**  
Auf einem 64-Bit-System Wenn n x vom System unterstützt wird die Konfiguration Systemeinstellungen nicht Einstellung DEP-Richtlinie auf **Always Off**festgelegt werden zulassen. Weitere Informationen über eine systemweite Konfiguration der Datenausführungsverhinderung finden Sie [eine detaillierte Beschreibung des Features in Windows XP Service Pack 2, Windows XP Tablet PC Edition 2005 und Windows Server 2003 (Data Execution Prevention, DEP)](http://support.microsoft.com/kb/875352).

 

Windows 8 müssen auf einem System Prozessoren n x und SSE2 für das System erfolgreich gestartet unterstützen. Wenn ein System die Unterstützung, aber die Einstellungen sind falsch konfiguriert, werden die Optionen überschrieben, bevor das System der Kernel startet.

### <a name="span-idwhatshouldidowhenwindows8failedtoinstallonavmwitherror0x0000260spanspan-idwhatshouldidowhenwindows8failedtoinstallonavmwitherror0x0000260spanspan-idwhatshouldidowhenwindows8failedtoinstallonavmwitherror0x0000260spanwhat-should-i-do-when-windows-8-failed-to-install-on-a-vm-with-error-0x0000260"></a><span id="What_should_I_do_when_Windows_8_failed_to_install_on_a_VM_with_error_0x0000260_"></span><span id="what_should_i_do_when_windows_8_failed_to_install_on_a_vm_with_error_0x0000260_"></span><span id="WHAT_SHOULD_I_DO_WHEN_WINDOWS_8_FAILED_TO_INSTALL_ON_A_VM_WITH_ERROR_0X0000260_"></span>Was soll ich tun, wenn Windows 8 konnte nicht auf einen virtuellen Computer mit Fehler 0x0000260 installiert?

Wenn ein virtueller Computer auf einem System, die n x unterstützt gehostet wird, müssen Sie beim Einrichten der Windows 8-VM PAE/n x im Konfigurations-Manager oder VM-Einstellungen aktivieren. Finden der Virtualisierung – Produkthandbuch Installation Anweisungen zum PAE/n x für den virtuellen Computer zu aktivieren.

**Hinweis**  
Wenn Sie haben versucht, Windows 8 auf einem virtuellen Computer installieren, die auf einem System gehostet wird, der eine Version von Windows ausgeführt wird, die n x deaktiviert wurde, müssen Sie die Anweisungen in befolgen [Wie finde ich heraus, ob mein System n x oder SSE2 unterstützt?](#supportnx) und [Wenn n x auf meinem System unterstützt wird, wie aktiviere ich auf n x?](#turnonnx) um n x bevor PAE/n x für den virtuellen Computer aktiviert werden kann auf dem System zu aktivieren.

 

 

 





