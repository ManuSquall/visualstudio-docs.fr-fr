---
title: IEnumDebugPrograms2 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IEnumDebugPrograms2
helpviewer_keywords:
- IEnumDebugPrograms2
ms.assetid: 7fbb8fb7-db64-4546-a364-dc668430c8af
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
ms.openlocfilehash: af46d12f546c2b8e53510ca1b3cd28b634909ea7
ms.lasthandoff: 04/05/2017

---
# <a name="ienumdebugprograms2"></a>IEnumDebugPrograms2
Cette interface énumère les programmes en cours d’exécution dans la session de débogage en cours.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IEnumDebugPrograms2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 Le moteur de débogage (DE) implémente cette interface pour fournir une liste des programmes en cours de débogage par le DE.  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 Appels de Visual Studio [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) pour obtenir cette interface. [EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md) n’est pas utilisé par Visual Studio.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IEnumDebugPrograms2`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[Suivant](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)|Récupère un nombre spécifié de programmes dans une séquence d’énumération.|  
|[Ignorer](../../../extensibility/debugger/reference/ienumdebugprograms2-skip.md)|Ignore un nombre spécifié de programmes dans une séquence d’énumération.|  
|[Réinitialiser](../../../extensibility/debugger/reference/ienumdebugprograms2-reset.md)|Réinitialise la séquence d’énumération au début.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugprograms2-clone.md)|Crée un énumérateur qui contient le même état d’énumération que l’énumérateur actuel.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugprograms2-getcount.md)|Obtient le nombre de programmes dans un énumérateur.|  
  
## <a name="remarks"></a>Notes  
 Visual Studio utilise cette interface pour :  
  
-   Remplir le **Modules** fenêtre (en appelant [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) , puis en appelant [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) sur chaque programme).  
  
-   Remplir le **attacher au processus** liste (en appelant `IDebugProcess2::EnumPrograms` , puis en appelant [QueryInterface](/cpp/atl/queryinterface) sur chaque [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) interface pour obtenir un [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md) interface).  
  
-   Générer une liste DEs, qui peut être débogué chaque programme dans le processus (à l’aide de [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)).  
  
-   Appliquer des mises à jour de modifier & Continuer (ENC) pour chaque programme (en appelant IDebugProcess2::EnumPrograms, puis [GetENCUpdate](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md)).  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)   
 [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)
