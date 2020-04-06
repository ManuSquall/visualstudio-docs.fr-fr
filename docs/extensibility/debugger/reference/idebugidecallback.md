---
title: IDebugIDECallback - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugIDECallback interface
ms.assetid: 8d31adc0-1c44-4658-8d4f-f4b73e35f4a6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 585ff354cef9686097325ea4dea25cd08c4cbb1b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727826"
---
# <a name="idebugidecallback"></a>IDebugIDECallback
> [!IMPORTANT]
> Dans Visual Studio 2015, cette façon de mettre en œuvre les évaluateurs d’expression est dépréciée. Pour obtenir de l’information sur la mise en œuvre des évaluateurs de l’expression CLR, veuillez consulter [les évaluateurs de l’expression CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) et [l’échantillon d’évaluateur d’expression gérée.](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)

 Permet à un évaluateur d’expression (EE) d’afficher un message dans la fenêtre de sortie du débaugeant.

## <a name="syntax"></a>Syntaxe

```
IDebugIDECallback : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Ce rappel est implémenté par le moteur de débogé géré.

## <a name="notes-for-callers"></a>Notes pour les appelants
 Il peut être consommé par un évaluateur d’expression pour envoyer la sortie à la fenêtre de sortie du débaugeant.

## <a name="methods"></a>Méthodes
 Cette interface implémente la méthode suivante :

|Méthode|Description|
|------------|-----------------|
|[DisplayMessage (DisplayMessage)](../../../extensibility/debugger/reference/idebugidecallback-displaymessage.md)|Envoie la chaîne de message spécifiée à la fenêtre de sortie du débagé.|

## <a name="requirements"></a>Spécifications
 En-tête: Ee.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll
