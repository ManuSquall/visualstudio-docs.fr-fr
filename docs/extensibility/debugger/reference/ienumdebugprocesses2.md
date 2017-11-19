---
title: IEnumDebugProcesses2 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEnumDebugProcesses2
helpviewer_keywords: IEnumDebugProcesses2
ms.assetid: 06a1368f-10f0-44eb-af61-e388c2327111
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6e5be156ec0a30f736b96cfe6451b893dfb8eacf
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="ienumdebugprocesses2"></a>IEnumDebugProcesses2
Cette interface énumère les processus en cours d’exécution sur un port de débogage.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IEnumDebugProcesses : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 Un fournisseur de port personnalisé implémente cette interface pour fournir une liste des processus en cours d’exécution sur un port.  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 Appels de Visual Studio [EnumProcesses](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md) pour obtenir cette interface.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IEnumDebugProcesses2`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[Next](../../../extensibility/debugger/reference/ienumdebugprocesses2-next.md)|Récupère un nombre spécifié de processus dans une séquence d’énumération.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugprocesses2-skip.md)|Ignore un nombre spécifié de processus dans une séquence d’énumération.|  
|[Réinitialiser](../../../extensibility/debugger/reference/ienumdebugprocesses2-reset.md)|Réinitialise la séquence d’énumération au début.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugprocesses2-clone.md)|Crée un énumérateur qui contient le même état d’énumération que l’énumérateur actuel.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugprocesses2-getcount.md)|Obtient le nombre de processus dans l’énumérateur.|  
  
## <a name="remarks"></a>Remarques  
 Visual Studio utilise cette interface pour remplir le **processus** fenêtre.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumProcesses](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md)