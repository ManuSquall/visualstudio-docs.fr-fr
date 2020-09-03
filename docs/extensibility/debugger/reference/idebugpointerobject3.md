---
title: IDebugPointerObject3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPointerObject3 interface
ms.assetid: 11d26af4-1079-435e-96fa-d5269cbea8eb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8605f1cdd50b6e98d6e30a7b550cce1d22543ff9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80725465"
---
# <a name="idebugpointerobject3"></a>IDebugPointerObject3
> [!IMPORTANT]
> Dans Visual Studio 2015, cette façon d’implémenter les évaluateurs d’expression est déconseillée. Pour plus d’informations sur l’implémentation des évaluateurs d’expression CLR, consultez [évaluateur d’expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [exemple évaluateur d’expression managée](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Représente un pointeur dans une arborescence d’analyse et étend l’interface **IDebugPointerObject** .

## <a name="syntax"></a>Syntaxe

```
IDebugPointerObject3 : IDebugPointerObject
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Un évaluateur d’expression (EE) implémente cette interface.

## <a name="methods"></a>Méthodes
 Outre les méthodes sur l’interface [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md) , cette interface implémente les méthodes suivantes :

|Méthode|Description|
|------------|-----------------|
|[GetPointerAddress](../../../extensibility/debugger/reference/idebugpointerobject3-getpointeraddress.md)|Récupère l’adresse du pointeur.|

## <a name="requirements"></a>Configuration requise
 En-tête : EE. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll
