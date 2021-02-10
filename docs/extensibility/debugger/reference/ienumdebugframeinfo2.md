---
title: IEnumDebugFrameInfo2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugFrameInfo2
helpviewer_keywords:
- IEnumDebugFrameInfo2
ms.assetid: 994e30ad-435a-4f9e-9272-d96d9e01099c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: fdc2006b45a664496615988251081f1000cdb428
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99956284"
---
# <a name="ienumdebugframeinfo2"></a>IEnumDebugFrameInfo2
Cette interface énumère les structures [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) .

## <a name="syntax"></a>Syntaxe

```
IEnumDebugFrameInfo2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Le moteur de débogage (DE) implémente cette interface pour fournir une liste de structures décrivant la pile des appels actuelle.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Visual Studio appelle [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) pour obtenir cette interface chaque fois qu’un point d’arrêt, une exception ou une interruption se produit dans un programme en cours de débogage.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant présente les méthodes de `IEnumDebugFrameInfo2` .

|Méthode|Description|
|------------|-----------------|
|[Next](../../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md)|Récupère un nombre spécifié de structures [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) dans une séquence d’énumération.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugframeinfo2-skip.md)|Ignore un nombre spécifié de structures [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) dans une séquence d’énumération.|
|[Réinitialiser](../../../extensibility/debugger/reference/ienumdebugframeinfo2-reset.md)|Réinitialise une séquence d'énumération.|
|[Répliqué](../../../extensibility/debugger/reference/ienumdebugframeinfo2-clone.md)|Crée un énumérateur qui contient le même état d’énumération que l’énumérateur actuel.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugframeinfo2-getcount.md)|Obtient le nombre de structures [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) dans un énumérateur.|

## <a name="remarks"></a>Notes
 Visual Studio obtient cette interface comme première étape pour la gestion d’un point d’arrêt, d’une exception ou d’une pause générée par l’utilisateur sur le programme en cours de débogage. La liste de structures [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) représente la pile des appels actuelle, avec l’appel de fonction actuel au début de la liste et l’appel de fonction le plus ancien à la fin de la liste. Chaque `FRAMEINFO` représente un frame de pile, un contexte dans lequel les expressions peuvent être évaluées et les variables locales examinées.

## <a name="requirements"></a>Configuration requise
 En-tête : msdbg. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
