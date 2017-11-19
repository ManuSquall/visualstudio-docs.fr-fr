---
title: IDebugCodeContext2 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugCodeContext2
helpviewer_keywords: IDebugCodeContext2 interface
ms.assetid: 3670439e-2171-405d-9d77-dedb0f1cba93
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e9e003372e390d7e807f314555310c167bf011a8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugcodecontext2"></a>IDebugCodeContext2
Cette interface représente la position de départ d’une instruction de code. Pour la plupart des architectures d’exécution aujourd'hui, un contexte de code peut être considéré comme une adresse dans le flux de l’exécution d’un programme.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugCodeContext2 : IDebugMemoryContext2  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 Le moteur de débogage implémente cette interface pour associer la position d’une instruction de code vers un emplacement de document.  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 Méthodes de nombreuses interfaces retournent cette interface, plus généralement, [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md). Il est aussi largement utilisé avec le [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) interface ainsi que dans les informations de résolution de point d’arrêt.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Outre les méthodes sur le [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) interface, cette interface implémente les méthodes suivantes :  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)|Obtient le contexte de document correspondant au contexte de code actif.|  
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugcodecontext2-getlanguageinfo.md)|Obtient les informations de langue pour ce contexte de code.|  
  
## <a name="remarks"></a>Remarques  
 La principale différence entre une `IDebugCodeContext2` interface et un [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) interface est une `IDebugCodeContext2` est toujours instruction aligné. Cela signifie qu’une `IDebugCodeContext2` pointe toujours vers le début d’une instruction, tandis qu’un `IDebugMemoryContext2` peut pointer vers les octets de mémoire de l’architecture de l’exécution. `IDebugCodeContext2`est incrémenté par les instructions plutôt que par la taille de stockage de base (généralement octets).  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)   
 [CanSetNextStatement](../../../extensibility/debugger/reference/idebugthread2-cansetnextstatement.md)   
 [SetNextStatement](../../../extensibility/debugger/reference/idebugthread2-setnextstatement.md)   
 [GetCodeContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getcodecontext.md)   
 [GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)   
 [Suivant](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)