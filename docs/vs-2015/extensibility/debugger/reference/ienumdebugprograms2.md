---
title: IEnumDebugPrograms2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugPrograms2
helpviewer_keywords:
- IEnumDebugPrograms2
ms.assetid: 7fbb8fb7-db64-4546-a364-dc668430c8af
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8d9d1030616fa8d7f3a1bfc6b533c4ed8433ea89
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65703906"
---
# <a name="ienumdebugprograms2"></a>IEnumDebugPrograms2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Cette interface énumère les programmes en cours d’exécution dans la session de débogage en cours.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IEnumDebugPrograms2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 Le moteur de débogage (DE) implémente cette interface pour fournir une liste de programmes débogués par le DE.  
  
## <a name="notes-for-callers"></a>Notes pour les appelants  
 Visual Studio appelle [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) pour obtenir cette interface. [EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md) n’est pas utilisé par Visual Studio.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IEnumDebugPrograms2` .  
  
|Méthode|Description|  
|------------|-----------------|  
|[Next](../../../extensibility/debugger/reference/ienumdebugprograms2-next.md)|Récupère un nombre spécifié de programmes dans une séquence d’énumération.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugprograms2-skip.md)|Ignore un nombre spécifié de programmes dans une séquence d’énumération.|  
|[Réinitialiser](../../../extensibility/debugger/reference/ienumdebugprograms2-reset.md)|Réinitialise une séquence d'énumération.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugprograms2-clone.md)|Crée un énumérateur qui contient le même état d’énumération que l’énumérateur actuel.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugprograms2-getcount.md)|Obtient le nombre de programmes dans un énumérateur.|  
  
## <a name="remarks"></a>Notes  
 Visual Studio utilise cette interface pour :  
  
- Remplissez la fenêtre **modules** (en appelant [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md) , puis en appelant [EnumModules](../../../extensibility/debugger/reference/idebugprogram2-enummodules.md) sur chaque programme).  
  
- Remplissez la liste **attacher au processus** (en appelant `IDebugProcess2::EnumPrograms` , puis en appelant [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) sur chaque interface [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) pour obtenir une interface [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md) ).  
  
- Générez une liste des qui peuvent déboguer chaque programme dans le processus (à l’aide de [GetEngineInfo](../../../extensibility/debugger/reference/idebugprogram2-getengineinfo.md)).  
  
- Appliquez les mises à jour de modifier & Continuer (ENC) à chaque programme (en appelant IDebugProcess2 :: EnumPrograms, puis en appelant [GetENCUpdate](../../../extensibility/debugger/reference/idebugprogram2-getencupdate.md)).  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg. h  
  
 Espace de noms : Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces principales](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumPrograms](../../../extensibility/debugger/reference/idebugengine2-enumprograms.md)   
 [EnumPrograms](../../../extensibility/debugger/reference/idebugprocess2-enumprograms.md)
