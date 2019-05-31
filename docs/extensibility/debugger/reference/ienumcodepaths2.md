---
title: IEnumCodePaths2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumCodePaths2
helpviewer_keywords:
- IEnumCodePaths2 interface
ms.assetid: 17ec9f9e-dc06-4532-b5db-da52efcc8630
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d5ad1f7a3f954116350e8accbdc9db02d0ac920d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66319594"
---
# <a name="ienumcodepaths2"></a>IEnumCodePaths2
Cette interface représente une liste de chemins d’accès du code.

## <a name="syntax"></a>Syntaxe

```
IEnumCodePaths2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs
 Le moteur de débogage (dé) implémente cette interface pour représenter une liste de chemins d’accès du code.

## <a name="notes-for-callers"></a>Notes de publication pour les appelants
 Appelez [EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md) pour obtenir cette interface.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant présente les méthodes de `IEnumCodePaths2`.

|Méthode|Description|
|------------|-----------------|
|[Next](../../../extensibility/debugger/reference/ienumcodepaths2-next.md)|Récupère un nombre spécifié de chemins d’accès du code dans une séquence d’énumération.|
|[Skip](../../../extensibility/debugger/reference/ienumcodepaths2-skip.md)|Ignore un nombre spécifié de chemins d’accès du code dans une séquence d’énumération.|
|[Reset](../../../extensibility/debugger/reference/ienumcodepaths2-reset.md)|Réinitialise une séquence d’énumération au début.|
|[Clone](../../../extensibility/debugger/reference/ienumcodepaths2-clone.md)|Crée un énumérateur qui contient le même état d’énumération que l’énumérateur en cours.|
|[GetCount](../../../extensibility/debugger/reference/ienumcodepaths2-getcount.md)|Obtient le nombre de chemins d’accès du code dans un énumérateur.|

## <a name="remarks"></a>Notes
 Un chemin d’accès du code représente un appel de fonction ou de point de branche dans un programme. Une liste de chemins d’accès du code représente le chemin d’accès par le biais duquel l’exécution du code a pris.

## <a name="requirements"></a>Configuration requise
 En-tête : msdbg.h

 Espace de noms : Microsoft.VisualStudio.Debugger.Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)