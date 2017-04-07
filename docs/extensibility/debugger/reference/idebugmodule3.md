---
title: IDebugModule3 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugModule3
helpviewer_keywords:
- IDebugModule3 interface
ms.assetid: 44f8e96e-9c59-4ffc-9a08-9c908a0e4de7
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: ca7c86466fa23fb21a932f26dc24e37c71cf29b4
ms.openlocfilehash: 8d06621cc46499d763fd16797813d9dd71e9fdfb
ms.lasthandoff: 04/05/2017

---
# <a name="idebugmodule3"></a>IDebugModule3
Cette interface représente un module qui prend en charge d’autres emplacements de symboles et des États de JustMyCode.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugModule3 : IDebugModule2  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 Le moteur de débogage (DE) implémente cette interface pour prendre en charge d’autres emplacements de symboles et pour travailler avec les États JustMyCode (consultez la [glossaire de débogueur Visual Studio](../../../extensibility/debugger/reference/visual-studio-debugger-glossary.md) pour une définition de « JustMyCode »).  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 Un appel à [GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md) retourne cette interface. L’envoie DE la [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) de l’interface pour le Gestionnaire de débogage de session (SDM) à l’aide de la [événement](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) (méthode). En outre, un appel à [QueryInterface](/cpp/atl/queryinterface) sur une [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) interface retourne cette interface.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Outre les méthodes sur le [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) interface, cette interface implémente les méthodes suivantes :  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)|Retourne une liste de chemins de recherche pour les symboles et les résultats de recherche dans chaque chemin d’accès.|  
|[LoadSymbols](../../../extensibility/debugger/reference/idebugmodule3-loadsymbols.md)|Charge et initialise les symboles du module en cours.|  
|[IsUserCode](../../../extensibility/debugger/reference/idebugmodule3-isusercode.md)|Indicateur retourne en spécifiant si le module représente le code utilisateur.|  
|[SetJustMyCodeState](../../../extensibility/debugger/reference/idebugmodule3-setjustmycodestate.md)|Indique si le module doit être considérée comme code utilisateur, ou non.|  
  
## <a name="remarks"></a>Notes  
 Visual Studio est le consommateur classique de cette interface.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)   
 [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)   
 [GetSymbolSearchInfo](../../../extensibility/debugger/reference/idebugsymbolsearchevent2-getsymbolsearchinfo.md)
