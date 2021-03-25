---
description: Représente un fournisseur de symboles COM+ avec des méthodes qui sont spécifiques au code managé et étendent le IDebugComPlusSymbolProvider.
title: IDebugComPlusSymbolProvider2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugComPlusSymbolProvider2 interface
ms.assetid: fa2f9b49-03ad-43c7-92d6-6dcb9c3d0531
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 975dc6df875866a16fffc5d044ae82c996b84e35
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105077965"
---
# <a name="idebugcomplussymbolprovider2"></a>IDebugComPlusSymbolProvider2
Représente un fournisseur de symboles COM+ avec des méthodes qui sont spécifiques au code managé et étendent le [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) **IDebugComPlusSymbolProvider**.

## <a name="syntax"></a>Syntaxe

```
IDebugComPlusSymbolProvider2 : IDebugComPlusSymbolProvider
```

## <a name="methods"></a>Méthodes
 Outre les méthodes sur l’interface [IDebugComPlusSymbolProvider](../../../extensibility/debugger/reference/idebugcomplussymbolprovider.md) , cette interface implémente les méthodes suivantes :

|Méthode|Description|
|------------|-----------------|
|[FunctionHasLineInfo](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-functionhaslineinfo.md)|Détermine si la méthode spécifiée a des informations de ligne.|
|[GetTypesByName](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-gettypesbyname.md)|Récupère un type en fonction de son nom.|
|[GetTypeFromToken](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-gettypefromtoken.md)|Récupère un type en fonction de son jeton.|
|[IsAddressSequencePoint](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-isaddresssequencepoint.md)|Détermine si l’adresse de débogage spécifiée est un point de séquence.|
|[LoadSymbolsFromCallback](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-loadsymbolsfromcallback.md)|Charge les symboles de débogage à l’aide de la méthode de rappel spécifiée.|
|[LoadSymbolsFromStreamWithCorModule](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-loadsymbolsfromstreamwithcormodule.md)|Charger les symboles de débogage à partir d’un flux de données en fonction de l’objet **ICorDebugModule** .|
|[LoadSymbolsWithCorModule](../../../extensibility/debugger/reference/idebugcomplussymbolprovider2-loadsymbolswithcormodule.md)|Charge les symboles de débogage en fonction de l’objet **ICorDebugModule** .|

## <a name="requirements"></a>Spécifications
 En-tête : SH. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll
