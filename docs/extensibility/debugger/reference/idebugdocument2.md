---
title: IDebugDocument2 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugDocument2
helpviewer_keywords:
- IDebugDocument2 interface
ms.assetid: 1bc58426-dbf5-4471-9aad-9d66cd80eef0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 36ac127e6cd6e25fd42c4859e723c883ecaffa82
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31109153"
---
# <a name="idebugdocument2"></a>IDebugDocument2
Cette interface représente un document source.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugDocument2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] en général implémente cette interface. Un moteur de débogage (DE) peut également implémenter cette interface lorsqu’il a besoin fournir le code source et de la source n’existe pas sur le disque.  Dans ce cas, le D’implémente également [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) et [IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md) interfaces, ainsi que des méthodes supplémentaires sur le [ IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) et [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md) interfaces.  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 Les méthodes sur le `IDebugDocumentContext2`, `IDebugDisassemblyStream2`, `IDebugDocumentPosition2`, et `IDebugActivateDocumentEvent2` interfaces retournent cette interface.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IDebugDocument2`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)|Obtient le nom du document dans un des différents formulaires.|  
|[GetDocumentClassID](../../../extensibility/debugger/reference/idebugdocument2-getdocumentclassid.md)|Obtient l’identificateur de classe du document.|  
  
## <a name="remarks"></a>Notes  
 Cette interface est implémentée uniquement lorsque le DE fournit le code source. Par exemple, lorsque vous déboguez un script sur une page HTML, le DE fournit le code source, car la source est téléchargée ou générée dynamiquement et n’existe pas comme un fichier de disque. Lors du débogage de langages traditionnels, tels que C++, cette interface n’a pas besoin être implémentée.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [IsPositionInDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-ispositionindocument.md)   
 [GetDocument](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocument.md)   
 [GetDocument](../../../extensibility/debugger/reference/idebugdocumentcontext2-getdocument.md)   
 [GetDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-getdocument.md)   
 [GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)