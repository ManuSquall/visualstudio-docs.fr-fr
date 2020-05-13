---
title: IEnumDebugCodeContexts2 - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugCodeContexts2
helpviewer_keywords:
- IEnumDebugCodeContexts2
ms.assetid: 72915146-215f-4c99-a034-131b2b474e0e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6917c44bb3ddc80513e7c45a6aa4ea0207fd46c9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717272"
---
# <a name="ienumdebugcodecontexts2"></a>IEnumDebugCodeContexts2
Cette interface énumère les contextes de code associés à la session de débogé, ou avec un programme ou un document particulier.

## <a name="syntax"></a>Syntaxe

```
IEnumDebugCodeContexts2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Le moteur de débopathie (DE) implémente cette interface pour représenter une liste de contextes de code pour une position de texte particulière dans un programme, ou une liste de contextes de code pour un contexte de document particulier.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Appelez [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md) pour obtenir cette interface représentant une liste de contextes de code pour une position de texte spécifique dans le document source d’un programme.

 Appelez [EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md) pour obtenir cette interface représentant une liste de tous les contextes de code dans un document source particulier.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant montre `IEnumDebugCodeContexts2`les méthodes de .

|Méthode|Description|
|------------|-----------------|
|[Suivant](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)|Récupère un nombre précis de contextes de code dans une séquence de recensement.|
|[Ignorer](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-skip.md)|Passe un certain nombre de contextes de code dans une séquence de recensement.|
|[Réinitialiser](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-reset.md)|Réinitialise une séquence d'énumération.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-clone.md)|Crée un enumérateur qui contient le même état de recensement que l’enumérateur actuel.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-getcount.md)|Obtient le nombre de contextes de code dans un enumérateur.|

## <a name="remarks"></a>Notes
 Visual Studio appelle [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md) pour remplir une liste de contextes de code que l’utilisateur peut choisir lors de la définition de la prochaine instruction ou de l’affichage du démontage pour un fichier source. Plusieurs contextes de code peuvent se produire, par exemple, lorsqu’il existe plusieurs exemples d’un modèle de style C.

## <a name="requirements"></a>Spécifications
 En-tête: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)
- [EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md)
