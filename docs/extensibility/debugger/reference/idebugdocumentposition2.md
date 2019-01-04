---
title: IDebugDocumentPosition2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugDocumentPosition2
helpviewer_keywords:
- IDebugDocumentPosition2 interface
ms.assetid: 0e838ced-12bb-4efc-b811-2b7c034b77b0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4327d1350c6d0487f9ee8fb89f03ad24b0e085a8
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53907759"
---
# <a name="idebugdocumentposition2"></a>IDebugDocumentPosition2
Cette interface représente une position abstraite dans un fichier source.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugDocumentPosition2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs  
 En général, Visual Studio implémente cette interface. Un moteur de débogage (dé) serait également implémenter cette interface si elle doit fournir son propre code source (comme lorsque le D’implémente le [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) interface).  
  
## <a name="notes-for-callers"></a>Notes de publication pour les appelants  
 Cette interface est transmise comme argument à [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md). Il est également fourni dans le cadre d’un [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) union (plus précisément, un [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md) structure) qui est à son tour de partie de la [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) structure, qui est utilisé dans la création d’un point d’arrêt en attente.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IDebugDocumentPosition2`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetFileName](../../../extensibility/debugger/reference/idebugdocumentposition2-getfilename.md)|Obtient le nom de fichier du fichier source qui contient la position de ce document.|  
|[GetDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-getdocument.md)|Obtient le document conteneur.|  
|[IsPositionInDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-ispositionindocument.md)|Détermine si cette position est contenue dans le document donné.|  
|[GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)|Obtient la plage de cette position du document.|  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md)