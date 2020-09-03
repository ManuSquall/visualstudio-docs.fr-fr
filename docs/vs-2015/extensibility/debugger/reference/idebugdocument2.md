---
title: IDebugDocument2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugDocument2
helpviewer_keywords:
- IDebugDocument2 interface
ms.assetid: 1bc58426-dbf5-4471-9aad-9d66cd80eef0
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2cd6afb417de4d8a362916f91593d0d0e67d307c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156501"
---
# <a name="idebugdocument2"></a>IDebugDocument2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Cette interface représente un document source.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugDocument2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] implémente généralement cette interface. Un moteur DE débogage (DE) peut également implémenter cette interface lorsqu’il doit fournir le code source et que la source n’existe pas sur le disque.  Dans ce cas, le DE implémenterait également des interfaces [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) et [IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md) , ainsi que des méthodes supplémentaires sur les interfaces [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) et [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md) .  
  
## <a name="notes-for-callers"></a>Notes pour les appelants  
 Les méthodes sur `IDebugDocumentContext2` les `IDebugDisassemblyStream2` interfaces,, `IDebugDocumentPosition2` et `IDebugActivateDocumentEvent2` retournent cette interface.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IDebugDocument2` .  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)|Obtient le nom du document dans l’un des plusieurs formulaires.|  
|[GetDocumentClassID](../../../extensibility/debugger/reference/idebugdocument2-getdocumentclassid.md)|Obtient l’identificateur de classe du document.|  
  
## <a name="remarks"></a>Notes  
 Cette interface est implémentée uniquement lorsque le DE fournit le code source. Par exemple, lorsque vous déboguez un script sur une page HTML, le DE fournit le code source, car la source est téléchargée ou générée dynamiquement et n’existe pas en tant que fichier disque. Lors du débogage de langages traditionnels, tels que C++, il n’est pas nécessaire d’implémenter cette interface.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg. h  
  
 Espace de noms : Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [IsPositionInDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-ispositionindocument.md)   
 [GetDocument](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocument.md)   
 [GetDocument](../../../extensibility/debugger/reference/idebugdocumentcontext2-getdocument.md)   
 [GetDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-getdocument.md)   
 [GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)
