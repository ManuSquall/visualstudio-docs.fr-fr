---
title: IDebugDocumentText2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugDocumentText2
helpviewer_keywords:
- IDebugDocumentText2 interface
ms.assetid: e85f50a3-211c-4220-a9f4-789950ba2782
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e0dc8344e19f422e65439aae6bafe12e3f62bee4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31107827"
---
# <a name="idebugdocumenttext2"></a>IDebugDocumentText2
Cette interface représente un document texte.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugDocumentText2 : IDebugDocument2  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 Un moteur de débogage (DE) implémente cette interface lorsque le code source, qu'il doit fournir est sous forme de texte. Étant donné que c’est le cas en règle générale, si un D’implémente la [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md) interface, elle doit également implémenter le `IDebugDocumentText2` interface.  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 Utilisez le `QueryInterface` méthode pour obtenir cette interface dans un `IDebugDocument2` interface.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Outre les méthodes sur le `IDebugDocument2` interface, cette interface implémente les méthodes suivantes :  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetSize](../../../extensibility/debugger/reference/idebugdocumenttext2-getsize.md)|Récupère la taille du texte à cette position dans le document.|  
|[GetText](../../../extensibility/debugger/reference/idebugdocumenttext2-gettext.md)|Récupère le texte de la position spécifiée dans le document.|  
  
## <a name="remarks"></a>Notes  
 Un objet qui implémente cette interface doit également implémenter le <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> de l’interface, qui fournit le <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> de l’interface pour un [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md) objet.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)   
 [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)