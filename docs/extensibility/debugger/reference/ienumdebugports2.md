---
title: IEnumDebugPorts2 - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugPorts2
helpviewer_keywords:
- IEnumDebugPorts2
ms.assetid: 1754eef3-cf62-42e0-b218-1911acba77d4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f3cc46ef8abb6ef1fbb8f072d97b0fc4a537af1a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80716102"
---
# <a name="ienumdebugports2"></a>IEnumDebugPorts2
Cette interface énumère les ports d’une machine ou d’un fournisseur de port.

## <a name="syntax"></a>Syntaxe

```
IEnumDebugPorts2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Un fournisseur de port personnalisé implémente cette interface pour représenter une liste de ports créés par le fournisseur. Visual Studio implémente cette interface à l’appui de son propre fournisseur de ports.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Appelez [EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md) pour obtenir cette interface représentant une liste de ports créés par le fournisseur portuaire. Appelez [EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md) pour obtenir cette interface représentant une liste de ports qui ont été enregistrés sur disque.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant montre `IEnumDebugPorts2`les méthodes de .

|Méthode|Description|
|------------|-----------------|
|[Suivant](../../../extensibility/debugger/reference/ienumdebugports2-next.md)|Récupère un nombre précis de ports dans une séquence de recensement.|
|[Ignorer](../../../extensibility/debugger/reference/ienumdebugports2-skip.md)|Passe un nombre précis de ports dans une séquence de recensement.|
|[Réinitialiser](../../../extensibility/debugger/reference/ienumdebugports2-reset.md)|Réinitialise une séquence d'énumération.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugports2-clone.md)|Crée un enumérateur qui contient le même état de recensement que l’enumérateur actuel.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugports2-getcount.md)|Obtient le nombre de ports dans un enumérateur.|

## <a name="remarks"></a>Notes
 Visual Studio utilise cette interface pour aider à remplir une liste de ports utilisés pour s’attacher aux processus.

 Un moteur de débogé ne fonctionne généralement pas à cette interface.

## <a name="requirements"></a>Spécifications
 En-tête: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumPorts](../../../extensibility/debugger/reference/idebugcoreserver2-enumports.md)
- [EnumPorts](../../../extensibility/debugger/reference/idebugportsupplier2-enumports.md)
