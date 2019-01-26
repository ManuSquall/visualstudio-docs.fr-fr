---
title: IDebugPort2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugPort2
helpviewer_keywords:
- IDebugPort2 interface
ms.assetid: 8fd87f05-a950-4d14-b925-98be29d4facc
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 06026276b6f9b37f005ee296d56ee17df5c75ca8
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54962746"
---
# <a name="idebugport2"></a>IDebugPort2
Cette interface représente un port de débogage sur un ordinateur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugPort2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs  
 Un fournisseur de port personnalisé implémente cette interface pour représenter un port de débogage sur un ordinateur.  
  
 Si le port prend en charge l’envoi des événements de port, il doit également implémenter le <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> interface pour prendre en charge un <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> interface qui fournit à son tour le [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) interface.  
  
## <a name="notes-for-callers"></a>Notes de publication pour les appelants  
 Les appels à [GetPort](../../../extensibility/debugger/reference/idebugportsupplier2-getport.md) ou [ajouter un port](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) retourner cette interface, qui représente le port demandé.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IDebugPort2`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetPortName](../../../extensibility/debugger/reference/idebugport2-getportname.md)|Retourne le nom de port.|  
|[GetPortId](../../../extensibility/debugger/reference/idebugport2-getportid.md)|Retourne l’identificateur du port.|  
|[GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)|Retourne la requête utilisée pour créer un port (si disponible).|  
|[GetPortSupplier](../../../extensibility/debugger/reference/idebugport2-getportsupplier.md)|Retourne le fournisseur de port pour ce port.|  
|[GetProcess](../../../extensibility/debugger/reference/idebugport2-getprocess.md)|Retourne une interface pour le processus étant donné les identificateur du processus.|  
|[EnumProcesses](../../../extensibility/debugger/reference/idebugport2-enumprocesses.md)|Énumère tous les processus en cours d’exécution sur un port.|  
  
## <a name="remarks"></a>Notes  
 Le port local fournit l’accès à tous les processus et les programmes en cours d’exécution sur l’ordinateur local. Autres ports peuvent représenter une connexion de câble série à un périphérique Windows CE, ou une connexion réseau à un ordinateur non-DCOM. Le `IDebugPort2` interface est utilisée pour rechercher le nom et l’identificateur d’un port et énumérer tous les processus en cours d’exécution sur le port. Installations pour lancer et arrêter les processus sur le port sont implémentées dans le `IDebugPortEx2` interface.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces principales](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)