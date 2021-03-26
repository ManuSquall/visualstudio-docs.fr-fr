---
description: Cette interface fournit des ports au gestionnaire de débogage de session (SDM).
title: IDebugPortSupplier2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2
helpviewer_keywords:
- IDebugPortSupplier2 interface
ms.assetid: 37067324-2ea6-4a01-8829-a6e9c7a70068
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: bd28e261c9c74601bd88f2d84e1296a1ed508f37
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105072024"
---
# <a name="idebugportsupplier2"></a>IDebugPortSupplier2
Cette interface fournit des ports au gestionnaire de débogage de session (SDM).

## <a name="syntax"></a>Syntaxe

```
IDebugPortSupplier2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
Un fournisseur de port personnalisé implémente cette interface pour représenter un fournisseur de ports.

## <a name="notes-for-callers"></a>Notes pour les appelants
Un appel à `CoCreateInstance` avec le fournisseur de port `GUID` retourne cette interface (il s’agit de la méthode habituelle pour obtenir cette interface). Par exemple :

```cpp
IDebugPortSupplier2 *GetPortSupplier(GUID *pPortSupplierGuid)
{
    IDebugPortSupplier2 *pPS = NULL;
    if (pPortSupplierGuid != NULL) {
        CComPtr<IDebugPortSupplier2> spPortSupplier;
        spPortSupplier.CoCreateInstance(*pPortSupplierGuid);
        if (spPortSupplier != NULL) {
            pPS = spPortSupplier.Detach();
        }
    }
    return (pPS);
}
```

Un appel à [GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md) retourne cette interface, représentant le fournisseur de port actuel utilisé par [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] .

- [GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md) retourne cette interface, qui représente le fournisseur de port qui a créé le port.

- [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md) représente une liste d' `IDebugPortSupplier` interfaces (l' `IEnumDebugPortSuppliers` interface est obtenue à partir de [EnumPortSuppliers](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md), représentant tous les fournisseurs de port inscrits auprès de [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] ).

En général, un moteur de débogage n’interagit pas avec un fournisseur de ports.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
Le tableau suivant présente les méthodes de `IDebugPortSupplier2` .

|Méthode|Description|
|------------|-----------------|
|[GetPortSupplierName](../../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md)|Obtient le nom du fournisseur de port.|
|[GetPortSupplierId](../../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md)|Obtient l’identificateur du fournisseur de port.|
|[GetPort](../../../extensibility/debugger/reference/idebugportsupplier2-getport.md)|Obtient un port à partir d’un fournisseur de ports.|
|[EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)|Énumère les ports qui existent déjà.|
|[CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md)|Vérifie qu’un fournisseur de ports prend en charge l’ajout de nouveaux ports.|
|[AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)|Ajoute un port.|
|[RemovePort](../../../extensibility/debugger/reference/idebugportsupplier2-removeport.md)|Supprime un port.|

## <a name="remarks"></a>Notes
Un fournisseur de ports peut s’identifier à l’aide d’un nom et d’un ID, ajouter et supprimer des ports et énumérer tous les ports fournis par le fournisseur de port.

## <a name="requirements"></a>Spécifications
En-tête : msdbg. h

Espace de noms : Microsoft. VisualStudio. Debugger. Interop

Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md)
- [GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)
- [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)
