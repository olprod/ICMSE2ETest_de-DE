---
title: ICSPNodeTransactioning
description: ICSPNodeTransactioning
MSHAttr:
- PreferredSiteName:MSDN
- PreferredLib:/library/windows/hardware
ms.assetid: 24dc518a-4a8d-41fe-9bc6-217bbbdf6a3f
ms.openlocfilehash: 65e0d6cbb324039364f0208c66565fdb3fdc41b9
ms.sourcegitcommit: d33e870dc4850bf0ea47fdae0d163b04c1c90f15
translationtype: MT
---
# <a name="icspnodetransactioning"></a>ICSPNodeTransactioning

Dies ist eine optionale Schnittstelle, die einen Konfigurationsdienstanbieter so definieren Sie eine eigene Transactioning Schema (interne Transactioning) für einen einzelnen Knoten ermöglicht. Transactioning unterstützt die Möglichkeit, einen Rollback vorherige Aktionen auf einem Knoten. Die meisten Knoten verwenden externe Transactioning an, der automatisch behandelt wird, und müssen nicht auf diese Schnittstelle implementieren. Weitere Informationen zu internen und externen Transactioning, einschließlich der Behandlung von der `RollbackAction` Funktionen finden Sie unter "Determine Knotenvorgänge" in [einer benutzerdefinierten Konfigurationsdienstanbieter entwerfen](design-a-custom-windows-csp.md).

``` syntax
interface ICSPNodeTransactioning : IUnknown
{
    HRESULT PersistRollbackAddState([in] IConfigManager2URI* puriChild, 
                                    [in] CFG_DATATYPE DataType, 
                                    [in] VARIANT varValue, 
                                    [in] ISequentialStream* pRollbackStream, 
                                    [in] ISequentialStream* pUninstallStream);
    HRESULT PersistRollbackCopyState([in] IConfigManager2URI* puriDestination, 
                                     [in] ISequentialStream* pRollbackStream, 
                                     [in] ISequentialStream* pUninstallStream);
    HRESULT PersistRollbackDeleteChildState([in] IConfigManager2URI* puriChild, 
                                            [in] ISequentialStream* pRollbackStream, 
                                            [in] ISequentialStream* pUninstallStream);
    HRESULT PersistRollbackClearState([in] ISequentialStream* pRollbackStream, 
                                      [in] ISequentialStream* pUninstallStream);
    HRESULT PersistRollbackExecuteState([in] VARIANT varUserData, 
                                        [in] ISequentialStream* pRollbackStream, 
                                        [in] ISequentialStream* pUninstallStream);
    HRESULT PersistRollbackMoveState([in] IConfigManager2URI* puriDestination, 
                                     [in] ISequentialStream* pRollbackStream, 
                                     [in] ISequentialStream* pUninstallStream);
    HRESULT PersistRollbackSetValueState([in] VARIANT varValue, 
                                         [in] ISequentialStream* pRollbackStream, 
                                         [in] ISequentialStream* pUninstallStream);
    HRESULT PersistRollbackSetPropertyState([in] REFGUID guidProperty, 
                                            [in] VARIANT varValue, 
                                            [in] ISequentialStream* pRollbackStream, 
                                            [in] ISequentialStream* pUninstallStream); 
    HRESULT PersistRollbackDeletePropertyState([in] REFGUID guidProperty, 
                                               [in] ISequentialStream* pRollbackStream, 
                                               [in] ISequentialStream* pUninstallStream);
    HRESULT RollbackAdd([in] ISequentialStream* pUndoStream, 
                        [in] BOOL fRecoveryRollback);
    HRESULT RollbackCopy([in] ISequentialStream* pUndoStream, 
                         [in] BOOL fRecoveryRollback);
    HRESULT RollbackDeleteChild([in] ISequentialStream* pUndoStream, 
                                [in] BOOL fRecoveryRollback);
    HRESULT RollbackClear([in] ISequentialStream* pUndoStream, 
                          [in] BOOL fRecoveryRollback);
    HRESULT RollbackExecute([in] ISequentialStream* pUndoStream, 
                            [in] BOOL fRecoveryRollback);
    HRESULT RollbackMove([in] ISequentialStream* pUndoStream, 
                         [in] BOOL fRecoveryRollback);
    HRESULT RollbackSetValue([in] ISequentialStream* pUndoStream, 
                             [in] BOOL fRecoveryRollback);
    HRESULT RollbackSetProperty([in] ISequentialStream* pUndoStream, 
                                [in] BOOL fRecoveryRollback);
    HRESULT RollbackDeleteProperty([in] ISequentialStream* pUndoStream, 
                                   [in] BOOL fRecoveryRollback);

    HRESULT Commit();
};
```

## <a name="related-topics"></a>Verwandte Themen

[Erstellen eines benutzerdefinierten Konfiguration-Dienstanbieters](create-a-custom-configuration-service-provider.md)

 





