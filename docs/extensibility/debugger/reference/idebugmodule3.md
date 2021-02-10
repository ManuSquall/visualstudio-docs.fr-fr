---
title: IDebugModule3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule3
helpviewer_keywords:
- IDebugModule3 interface
ms.assetid: 44f8e96e-9c59-4ffc-9a08-9c908a0e4de7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: fa655c03665c9eed54feabc5af679765b09ac0a6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99955518"
---
# <a name="idebugmodule3"></a>IDebugModule3
Cette interface représente un module qui prend en charge d’autres emplacements de symboles et d’États JustMyCode.

## <a name="syntax"></a>Syntaxe

```
IDebugModule3 : IDebugModule2
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Le moteur de débogage (DE) implémente cette interface pour prendre en charge d’autres emplacements de symboles et pour utiliser les États JustMyCode (consultez le [Glossaire du débogueur Visual Studio](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md) pour obtenir une définition de « JustMyCode »).

## <a name="notes-for-callers"></a>Notes pour les appelants
 Un appel à [GetSymbolSearchInfo,](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md) retourne cette interface. Le DE envoie l’interface [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) au gestionnaire de débogage de session (SDM) à l’aide de la méthode d' [événement](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) . En outre, un appel à [QueryInterface](/cpp/atl/queryinterface) sur une interface [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) retourne cette interface.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Outre les méthodes sur l’interface [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) , cette interface implémente les méthodes suivantes :

|Méthode|Description|
|------------|-----------------|
|[GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)|Retourne une liste de chemins d’accès pour rechercher des symboles et les résultats de la recherche de chaque chemin d’accès.|
|[LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md)|Charge et initialise les symboles pour le module en cours.|
|[IsUserCode](../../../extensibility/debugger/reference/idebugmodule3-isusercode.md)|Retourne un indicateur spécifiant si le module représente le code utilisateur.|
|[SetJustMyCodeState](../../../extensibility/debugger/reference/idebugmodule3-setjustmycodestate.md)|Spécifie si le module doit être considéré comme du code utilisateur.|

## <a name="remarks"></a>Notes
 Visual Studio est l’utilisateur classique de cette interface.

## <a name="requirements"></a>Configuration requise
 En-tête : msdbg. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
- [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)
- [GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md)
