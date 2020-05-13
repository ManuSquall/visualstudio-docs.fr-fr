---
title: IDebugModule3 - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule3
helpviewer_keywords:
- IDebugModule3 interface
ms.assetid: 44f8e96e-9c59-4ffc-9a08-9c908a0e4de7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 84db1b672a9460ef3809162a2a1433f269796046
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726740"
---
# <a name="idebugmodule3"></a>IDebugModule3
Cette interface représente un module qui prend en charge d’autres emplacements de symboles et d’états JustMyCode.

## <a name="syntax"></a>Syntaxe

```
IDebugModule3 : IDebugModule2
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Le moteur de débogé (DE) implémente cette interface pour prendre en charge d’autres emplacements de symboles et pour travailler avec les états JustMyCode (voir le [Visual Studio Debugger Glossary](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md) pour une définition de "JustMyCode").

## <a name="notes-for-callers"></a>Notes pour les appelants
 Un appel à [GetSymbolSearchInfo renvoie](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md) cette interface. Le DE envoie [l’interface IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) au gestionnaire de débogé de session (SDM) en utilisant la méthode [Event.](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) En outre, un appel à [QueryInterface](/cpp/atl/queryinterface) sur une interface [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) renvoie cette interface.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 En plus des méthodes de l’interface [IDebugModule2,](../../../extensibility/debugger/reference/idebugmodule2.md) cette interface met en œuvre les méthodes suivantes :

|Méthode|Description|
|------------|-----------------|
|[GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)|Retourne une liste de chemins recherchés pour les symboles et les résultats de la recherche de chaque chemin.|
|[LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md)|Charge et initialise les symboles du module actuel.|
|[IsUserCode](../../../extensibility/debugger/reference/idebugmodule3-isusercode.md)|Retourne le drapeau en précisant si le module représente le code utilisateur.|
|[SetJustMyCodeState](../../../extensibility/debugger/reference/idebugmodule3-setjustmycodestate.md)|Précise si le module doit être considéré comme un code utilisateur ou non.|

## <a name="remarks"></a>Notes
 Visual Studio est le consommateur typique de cette interface.

## <a name="requirements"></a>Spécifications
 En-tête: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)
- [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)
- [GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md)
