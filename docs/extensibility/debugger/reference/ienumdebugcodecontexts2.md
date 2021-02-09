---
title: IEnumDebugCodeContexts2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugCodeContexts2
helpviewer_keywords:
- IEnumDebugCodeContexts2
ms.assetid: 72915146-215f-4c99-a034-131b2b474e0e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7dee04516d8bc8d72859509a9f721455d858a433
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99929392"
---
# <a name="ienumdebugcodecontexts2"></a>IEnumDebugCodeContexts2
Cette interface énumère les contextes de code associés à la session de débogage, ou à un programme ou un document particulier.

## <a name="syntax"></a>Syntaxe

```
IEnumDebugCodeContexts2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Le moteur de débogage (DE) implémente cette interface pour représenter une liste de contextes de code pour une position de texte particulière dans un programme, ou une liste de contextes de code pour un contexte de document particulier.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Appelez [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md) pour obtenir cette interface représentant une liste de contextes de code pour une position de texte spécifique dans le document source d’un programme.

 Appelez [EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md) pour obtenir cette interface représentant une liste de tous les contextes de code dans un document source particulier.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant présente les méthodes de `IEnumDebugCodeContexts2` .

|Méthode|Description|
|------------|-----------------|
|[Next](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)|Récupère un nombre spécifié de contextes de code dans une séquence d’énumération.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-skip.md)|Ignore un nombre spécifié de contextes de code dans une séquence d’énumération.|
|[Réinitialiser](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-reset.md)|Réinitialise une séquence d'énumération.|
|[Répliqué](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-clone.md)|Crée un énumérateur qui contient le même état d’énumération que l’énumérateur actuel.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-getcount.md)|Obtient le nombre de contextes de code dans un énumérateur.|

## <a name="remarks"></a>Notes
 Visual Studio appelle [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md) pour remplir une liste de contextes de code que l’utilisateur peut choisir lors de la définition de l’instruction suivante ou de l’indication du code machine pour un fichier source. Plusieurs contextes de code peuvent se produire, par exemple, lorsqu’il existe plusieurs instances d’un modèle de style C++.

## <a name="requirements"></a>Configuration requise
 En-tête : msdbg. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)
- [EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md)
