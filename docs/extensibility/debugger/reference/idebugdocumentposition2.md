---
title: IDebugDocumentPosition2 - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentPosition2
helpviewer_keywords:
- IDebugDocumentPosition2 interface
ms.assetid: 0e838ced-12bb-4efc-b811-2b7c034b77b0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 63742f220d5a776fca180a3f9f7fe9c15e04c66a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731637"
---
# <a name="idebugdocumentposition2"></a>IDebugDocumentPosition2
Cette interface représente une position abstraite dans un fichier source.

## <a name="syntax"></a>Syntaxe

```
IDebugDocumentPosition2 : IUnknown
```

## <a name="notes-for-implementers"></a>Notes pour les implémenteurs
 Visual Studio implémente généralement cette interface. Un moteur de débogé (DE) implémenterait également cette interface s’il doit fournir son propre code source (comme lorsque le DE implémente [l’interface IDebugDocument2).](../../../extensibility/debugger/reference/idebugdocument2.md)

## <a name="notes-for-callers"></a>Notes pour les appelants
 Cette interface est transmise comme un argument à [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md). Il est également fourni dans le cadre d’un syndicat [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) (en particulier, une structure [BP_LOCATION_CODE_FILE_LINE)](../../../extensibility/debugger/reference/bp-location-code-file-line.md) qui fait à son tour partie de la structure [BP_REQUEST_INFO,](../../../extensibility/debugger/reference/bp-request-info.md) qui est utilisé dans la création d’un point d’arrêt en attente.

## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable
 Le tableau suivant montre `IDebugDocumentPosition2`les méthodes de .

|Méthode|Description|
|------------|-----------------|
|[GetFileName](../../../extensibility/debugger/reference/idebugdocumentposition2-getfilename.md)|Obtient le nom de fichier du fichier source qui contient cette position de document.|
|[GetDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-getdocument.md)|Obtient le document contenant.|
|[IsPositionInDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-ispositionindocument.md)|Détermine si cette position est contenue dans le document donné.|
|[GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)|Obtient la plage pour cette position de document.|

## <a name="requirements"></a>Spécifications
 En-tête: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assemblage: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Voir aussi
- [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md)
