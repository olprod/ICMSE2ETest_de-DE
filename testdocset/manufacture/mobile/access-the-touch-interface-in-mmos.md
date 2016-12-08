---
author: kpacquer
Description: Zugriff auf die Touch-Schnittstelle in MMOS
ms.assetid: 4455627d-ba59-48f1-9327-c9e2c30509da
MSHAttr: PreferredLib:/library/windows/hardware
title: Zugriff auf die Touch-Schnittstelle in MMOS
ms.openlocfilehash: b73d8a7b7901b0005ada895989fbba057c448b2b
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="access-the-touch-interface-in-mmos"></a>Zugriff auf die Touch-Schnittstelle in MMOS


Die Fingereingabe Controller Ausgabe kann erfasst und MMOS mit richtigen Touch Treibersupport verwendet werden. Das Touch-Schnittstelle-Beispiel wird veranschaulicht, wie Sammeln von Touch Koordinaten in MMOS Fertigung Tests zu implementieren.

## <a name="span-idtouchsamplerequirementsspanspan-idtouchsamplerequirementsspanspan-idtouchsamplerequirementsspantouch-sample-requirements"></a><span id="Touch_sample_requirements"></span><span id="touch_sample_requirements"></span><span id="TOUCH_SAMPLE_REQUIREMENTS"></span>Tippen Sie auf Beispiel Anforderungen


Der Beispielcode erfordert, dass die Microsoft.Input.TchHID.spkg zu packen, um im Bild (der Main-Betriebssystem oder MMOS) eingeschlossen werden. Das Microsoft.Input.TchHID.spkg-Paket enthält tchhid.sys, die die **CreateFile** und **Readfile** -Funktionen, die vom Beispielcode verwendet implementiert.

## <a name="span-idtouchsamplecodespanspan-idtouchsamplecodespanspan-idtouchsamplecodespantouch-sample-code"></a><span id="Touch_sample_code"></span><span id="touch_sample_code"></span><span id="TOUCH_SAMPLE_CODE"></span>Tippen Sie auf Beispielcode (engl.)


In diesem Beispiel im Benutzermodus für zeigt die Touch-Koordinaten, die vom Treiber Bildschirm Touch empfangen wurden.

Die Beispiel-app verwendet **CreateFile** -Funktion, um eine exklusive Handle für das Gerät zum Empfangen unformatierte Touch-Beispiele zu öffnen. Der Gerätename, die "TouchRaw0" von tchhid.sys verfügbar gemacht wird, die beim COMPUTERAKTIVIERUNGSVERSUCH touch Klassen-Treiber von Microsoft bereitgestellten und in Microsoft.Input.TchHID.spkg enthalten.

``` syntax
#define TOUCH_RAW_SAMPLES_DEVICE_NAME L"\\\\.\\TouchRaw0"
```

Nachdem das Handle erfolgreich geöffnet wird, durchlaufen die Anwendung, bis eine Fingereingabe Stelle in der Nähe der oberen linken Ecke des Bildschirms empfangen wird. Die Anwendung liest und zeigt die Koordinaten und die zugehörigen Fingereingabe Kontakt-ID

``` syntax
#include "sample.h"
#include <cfgmgr32.h>
#include <strsafe.h>

int main()
{
    HANDLE testDriver = INVALID_HANDLE_VALUE;
    BOOL exit = FALSE;
    INT32 i;
    TouchInfo touchInfo = {0};

    //
    // Open an exclusive handle to the device to get raw samples
    //
    testDriver = CreateFile(
        L"\\\\.\\TouchRaw0",
        GENERIC_READ,
        0,
        NULL,
        OPEN_EXISTING,
        0,
        NULL);


    if (INVALID_HANDLE_VALUE == testDriver)
    {
        goto exit;
    }

    //
    // Loop, printing touches to the debugger.
    // Release in upper-left corner ends the test.
    //
    while (!exit)
    {
        DWORD touchInfoBytesRead = 0;

        //
        // Wait for data
        //
        if (!ReadFile(
            testDriver,
            &touchInfo,
            sizeof(TouchInfo),
            &touchInfoBytesRead,
            NULL))
        {
            goto exit;
        }

        if (touchInfoBytesRead == 0)
        {
            goto exit;
        }

        //
        // Print to debugger
        //
        for (i=0; i<touchInfo.ContactCount; i++)
        {
            WCHAR infoString[MAX_PATH] = {0};

            StringCchPrintf(
                infoString,
                MAX_PATH,
                L"%d: Contact ID %d, at (%d,%d) is %s\r\n",
                GetTickCount(),
                touchInfo.ContactArray[i].ContactID,
                touchInfo.ContactArray[i].ScreenX,
                touchInfo.ContactArray[i].ScreenY,
                FLAGS_TO_STRING(touchInfo.ContactArray[i].Flags));
                
            OutputDebugString(infoString);
        }

        //
        // Look for program exit
        //
        for (i=0; i<touchInfo.ContactCount; i++)
        {
            if ((touchInfo.ContactArray[i].ScreenX < 50) &&
                (touchInfo.ContactArray[i].ScreenY < 50) &&
                (touchInfo.ContactArray[i].Flags & InputEventFlag_Up))
            {
                OutputDebugString(L"Touch below (50,50), quitting!\r\n");
                exit = TRUE;
            }
        }
    }

exit:
    if (testDriver != INVALID_HANDLE_VALUE)
    {
        CloseHandle(testDriver);
    }

    return 0;
}
```

Die Anwendung verwendet die Datenstrukturen TouchInfo und TouchContact, die in WPDKCONTENTROOT % definiert sind\\umfassen\\um\\WinPhoneInput.h. Der Header-Code wird hier gezeigt.

``` syntax
#pragma once

#include <windows.h>
#include <initguid.h>
#include <devguid.h>

//
// This device name is used to access raw touch samples from user mode.
//

#define TOUCH_RAW_SAMPLES_DEVICE_NAME L"\\\\.\\TouchRaw0"

enum InputEventFlag
{
    InputEventFlag_None     = 0x0000,
    
    InputEventFlag_Down     = 0x0001,
    InputEventFlag_Move     = 0x0002,
    InputEventFlag_Hold     = 0x0002,
    InputEventFlag_Up       = 0x0004,
    
    InputEventFlag_Empty    = 0x1000,
    InputEventFlag_Invalid  = 0x2000,
    
    InputEventFlag_TestSync = 0x8000
};

typedef struct _TouchContact
{
    UINT16         ContactID;
    UINT16         Flags;            // See InputEventFlag_*
    INT16          ScreenX;          // Screen Space X-Position
    INT16          ScreenY;          // Screen Space Y-Position
    INT16          WindowX;          // Ignore
    INT16          WindowY;          // Ignore
} TouchContact;

typedef struct _TouchInfo
{
    UINT16         Size;             // Size, in bytes, of this structure (includes n contacts)
    UINT16         Flags;            // Ignore
    UINT32         TimeStamp;        // Driver timestamp
    HANDLE         Source;           // Ignore
    UINT32         SessionID;        // Ignore
    INT32          ContactCount;     // Count of touch contact data points
    TouchContact   ContactArray[10]; // Collection of contacts
} TouchInfo;

#define FLAGS_TO_STRING(x) \
    (x & InputEventFlag_Down) ? L"Down" : \
    (x & InputEventFlag_Move) ? L"Move" : \
    (x & InputEventFlag_Up)   ? L"Up"   : \
    L"Unknown"
```

## <a name="span-idbuildinganddeployingthesampleapplicationspanspan-idbuildinganddeployingthesampleapplicationspanspan-idbuildinganddeployingthesampleapplicationspanbuilding-and-deploying-the-sample-application"></a><span id="Building_and_deploying_the_sample_application"></span><span id="building_and_deploying_the_sample_application"></span><span id="BUILDING_AND_DEPLOYING_THE_SAMPLE_APPLICATION"></span>Erstellen und Bereitstellen der beispielanwendung


Gehen Sie folgendermaßen vor, um die Anwendung im Benutzermodus Test zu erstellen.

1.  Erstellen Sie ein neues Benutzermodus-Anwendung-Projekt in Visual Studio. Weitere Informationen finden Sie unter [entwickeln MMOS Applikationen testen](develop-mmos-test-applications.md)

2.  Fügen Sie den Beispielcode und die Headerdatei zum Projekt hinzu.

3.  Erstellen Sie die Projektmappe, um sicherzustellen, dass es erfolgreich generiert wurde.

4.  Deaktivieren Sie Integrität des Codes in MMOS oder melden Sie die ausführbare Testdatei. Weitere Informationen finden Sie unter "Sicherheit in MMOS" in [Entwickeln MMOS Applikationen zu testen](develop-mmos-test-applications.md).

5.  Stellen Sie die ausführbare Datei für das Gerät, und führen Sie die Anwendung. Weitere Informationen finden Sie unter [Bereitstellen und Testen einer Benutzermodus - testanwendung in MMOS](deploy-and-test-a-user-mode-test-application-in-mmos.md).

 

 





