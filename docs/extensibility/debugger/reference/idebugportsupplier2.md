---
title: IDebugPortSupplier2 - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2
helpviewer_keywords:
- IDebugPortSupplier2 interface
ms.assetid: 37067324-2ea6-4a01-8829-a6e9c7a70068
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ddce454e6634d8cc177019e9d30b0ffcc7e7f1cc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724476"
---
# <a name="idebugportsupplier2"></a>IDebugPortSupplier2
Cette interface fournit des ports au gestionnaire de débogé de session (SDM).

## <a name="syntax"></a>Syntaxe

```
IDebugPortSupplier2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
Un fournisseur de port personnalisé implémente cette interface pour représenter un fournisseur de port.

## <a name="notes-for-callers"></a>Notes pour les appelants
Un appel `CoCreateInstance` avec un fournisseur `GUID` de port renvoie cette interface (c’est la façon typique d’obtenir cette interface). Par exemple :

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

Un appel à [GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md) renvoie cette interface, [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]représentant le fournisseur portuaire actuel utilisé par .

- [GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md) renvoie cette interface, représentant le fournisseur de port qui a créé le port.

- [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md) représente une `IDebugPortSupplier` liste d’interfaces (l’interface `IEnumDebugPortSuppliers` est obtenue auprès d’EnumPortSuppliers , représentant tous les fournisseurs [portuaires](../../../extensibility/debugger/reference/idebugcoreserver2-enumportsuppliers.md)enregistrés auprès [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]).

Un moteur de débogé n’interagit généralement pas avec un fournisseur de port.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
Le tableau suivant montre `IDebugPortSupplier2`les méthodes de .

|Méthode|Description|
|------------|-----------------|
|[GetPortSupplierName](../../../extensibility/debugger/reference/idebugportsupplier2-getportsuppliername.md)|Obtient le nom du fournisseur de port.|
|[GetPortSupplierId](../../../extensibility/debugger/reference/idebugportsupplier2-getportsupplierid.md)|Obtient l’identifiant de fournisseur de port.|
|[GetPort](../../../extensibility/debugger/reference/idebugportsupplier2-getport.md)|Obtient un port d’un fournisseur de port.|
|[EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)|Énumère les ports qui existent déjà.|
|[CanAddPort](../../../extensibility/debugger/reference/idebugportsupplier2-canaddport.md)|Vérifie qu’un fournisseur portuaire prend en charge l’ajout de nouveaux ports.|
|[AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)|Ajoute un port.|
|[RemovePort](../../../extensibility/debugger/reference/idebugportsupplier2-removeport.md)|Enlève un port.|

## <a name="remarks"></a>Notes
Un fournisseur portuaire peut s’identifier par son nom et par son identité, ajouter et supprimer les ports et énumérer tous les ports que le fournisseur du port fournit.

## <a name="requirements"></a>Spécifications
En-tête: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md)
- [GetPortSupplier](../../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)
- [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)
