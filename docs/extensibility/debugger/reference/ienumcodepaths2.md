---
title: IEnumCodePaths2 - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumCodePaths2
helpviewer_keywords:
- IEnumCodePaths2 interface
ms.assetid: 17ec9f9e-dc06-4532-b5db-da52efcc8630
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 89c8cac9a7c2baa020002fe852330639d7081982
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717718"
---
# <a name="ienumcodepaths2"></a>IEnumCodePaths2
Cette interface représente une liste de chemins de code.

## <a name="syntax"></a>Syntaxe

```
IEnumCodePaths2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Le moteur de débogé (DE) implémente cette interface pour représenter une liste de chemins de code.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Appelez [EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md) pour obtenir cette interface.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant montre `IEnumCodePaths2`les méthodes de .

|Méthode|Description|
|------------|-----------------|
|[Suivant](../../../extensibility/debugger/reference/ienumcodepaths2-next.md)|Récupère un nombre précis de chemins de code dans une séquence de recensement.|
|[Ignorer](../../../extensibility/debugger/reference/ienumcodepaths2-skip.md)|Passe un nombre spécifié de chemins de code dans une séquence de recensement.|
|[Réinitialiser](../../../extensibility/debugger/reference/ienumcodepaths2-reset.md)|Réinitialise une séquence d'énumération.|
|[Clone](../../../extensibility/debugger/reference/ienumcodepaths2-clone.md)|Crée un enumérateur qui contient le même état de recensement que l’enumérateur actuel.|
|[GetCount](../../../extensibility/debugger/reference/ienumcodepaths2-getcount.md)|Obtient le nombre de chemins de code dans un enumérateur.|

## <a name="remarks"></a>Notes
 Un chemin de code représente un point de branche ou un appel de fonction dans un programme. Une liste de chemins de code représente le chemin parcouru par l’exécution du code.

## <a name="requirements"></a>Spécifications
 En-tête: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
