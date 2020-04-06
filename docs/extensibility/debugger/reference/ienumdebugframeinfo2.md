---
title: IEnumDebugFrameInfo2 - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugFrameInfo2
helpviewer_keywords:
- IEnumDebugFrameInfo2
ms.assetid: 994e30ad-435a-4f9e-9272-d96d9e01099c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0aa67792ced94afd9c4439cbc6ea577e6b85f28b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80716613"
---
# <a name="ienumdebugframeinfo2"></a>IEnumDebugFrameInfo2
Cette interface énumère les structures [FRAMEINFO.](../../../extensibility/debugger/reference/frameinfo.md)

## <a name="syntax"></a>Syntaxe

```
IEnumDebugFrameInfo2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Le moteur de débogé (DE) implémente cette interface pour fournir une liste de structures qui décrit la pile d’appels actuelle.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Visual Studio appelle [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) pour obtenir cette interface chaque fois qu’un point d’arrêt, une exception ou un arrêt se produit dans un programme en cours de déboisation.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant montre `IEnumDebugFrameInfo2`les méthodes de .

|Méthode|Description|
|------------|-----------------|
|[Suivant](../../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md)|Récupère un nombre précis de structures [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) dans une séquence de recensement.|
|[Ignorer](../../../extensibility/debugger/reference/ienumdebugframeinfo2-skip.md)|Passe un nombre précis de structures [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) dans une séquence de recensement.|
|[Réinitialiser](../../../extensibility/debugger/reference/ienumdebugframeinfo2-reset.md)|Réinitialise une séquence d'énumération.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugframeinfo2-clone.md)|Crée un enumérateur qui contient le même état de recensement que l’enumérateur actuel.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugframeinfo2-getcount.md)|Obtient le nombre de structures [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) dans un enumérateur.|

## <a name="remarks"></a>Notes
 Visual Studio obtient cette interface comme première étape pour gérer un point d’arrêt, une exception ou une pause générée par l’utilisateur sur le programme étant débogé. La liste des structures [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) représente la pile d’appels actuelle, avec l’appel de fonction en cours au début de la liste et le plus ancien appel de fonction à la fin de la liste. Chacun `FRAMEINFO` représente un cadre de pile, un contexte dans lequel les expressions peuvent être évaluées et les variables locales examinées.

## <a name="requirements"></a>Spécifications
 En-tête: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)
- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
