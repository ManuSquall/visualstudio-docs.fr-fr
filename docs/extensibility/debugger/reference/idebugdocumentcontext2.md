---
title: IDebugDocumentContext2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugDocumentContext2
helpviewer_keywords:
- IDebugDocumentContext2
ms.assetid: 2a446c71-8100-4c09-a1cc-fd446bd74030
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: dca62a511cd247f3344e319a7c3b4946b848103f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53909696"
---
# <a name="idebugdocumentcontext2"></a>IDebugDocumentContext2
Cette interface représente une position dans un document de fichier source.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugDocumentContext2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs  
 Le moteur de débogage (dé) implémente cette interface dans le cadre de sa prise en charge pour le débogage au niveau du code source. En plus d’une position dans le code source, cette interface fournit des méthodes pour la comparaison des contextes et de naviguer dans un document de code source.  
  
## <a name="notes-for-callers"></a>Notes de publication pour les appelants  
 Les méthodes sur plusieurs interfaces, généralement le [GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) et [GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md) interfaces, retourner cette interface.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IDebugDocumentContext2`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetDocument](../../../extensibility/debugger/reference/idebugdocumentcontext2-getdocument.md)|Obtient le document qui contient le contexte de ce document.|  
|[GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)|Obtient le nom affichable du document qui contient le contexte de ce document.|  
|[EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md)|Récupère une liste de tous les contextes de code associé à ce contexte de document.|  
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugdocumentcontext2-getlanguageinfo.md)|Obtient la langue associée à ce contexte de document.|  
|[GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)|Obtient la plage d’instruction de fichier de ce contexte de document.|  
|[GetSourceRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getsourcerange.md)|Obtient la plage de source de fichier de ce contexte de document.|  
|[Compare](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)|Compare ce contexte de document dans un tableau des contextes de document donné.|  
|[Seek](../../../extensibility/debugger/reference/idebugdocumentcontext2-seek.md)|Déplace le contexte de document en un nombre donné d’instructions ou des lignes.|  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)   
 [GetDocumentContext](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocumentcontext.md)   
 [GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)   
 [GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)