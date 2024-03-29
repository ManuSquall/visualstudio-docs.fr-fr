---
description: Cette interface représente une position abstraite dans un fichier source.
title: IDebugDocumentPosition2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentPosition2
helpviewer_keywords:
- IDebugDocumentPosition2 interface
ms.assetid: 0e838ced-12bb-4efc-b811-2b7c034b77b0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8b7c4c8e469dff76e2af631c4943305b0e3ee8e7
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105066397"
---
# <a name="idebugdocumentposition2"></a>IDebugDocumentPosition2
Cette interface représente une position abstraite dans un fichier source.

## <a name="syntax"></a>Syntaxe

```
IDebugDocumentPosition2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Visual Studio implémente généralement cette interface. Un moteur DE débogage (DE) implémenterait également cette interface s’il doit fournir son propre code source (comme lorsque le moteur DE BASE DE code implémente l’interface [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) ).

## <a name="notes-for-callers"></a>Notes pour les appelants
 Cette interface est transmise en tant qu’argument à [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md). Elle est également fournie dans le cadre d’une [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) Union (plus précisément, une structure [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md) ) qui fait partie intégrante de la structure [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) , utilisée pour la création d’un point d’arrêt en attente.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant présente les méthodes de `IDebugDocumentPosition2` .

|Méthode|Description|
|------------|-----------------|
|[GetFileName](../../../extensibility/debugger/reference/idebugdocumentposition2-getfilename.md)|Obtient le nom de fichier du fichier source qui contient la position de ce document.|
|[GetDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-getdocument.md)|Obtient le document conteneur.|
|[IsPositionInDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-ispositionindocument.md)|Détermine si cette position est contenue dans le document donné.|
|[GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)|Obtient la plage de la position de ce document.|

## <a name="requirements"></a>Spécifications
 En-tête : msdbg. h

 Espace de noms : Microsoft. VisualStudio. Debugger. Interop

 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md)
