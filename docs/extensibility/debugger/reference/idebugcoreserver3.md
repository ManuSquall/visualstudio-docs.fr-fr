---
title: IDebugCoreServer3 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugCoreServer3
helpviewer_keywords: IDebugCoreServer3 interface
ms.assetid: 51f5f41b-a5a4-4df0-a703-41f3d1811d7f
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 66b543735a48364429eec02d23df0bd08c987035
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugcoreserver3"></a>IDebugCoreServer3
Cette interface permet d’accéder à plus d’informations sur le serveur, dans que le processus est en cours d’exécution.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugCoreServer3 : IDebugCoreServer2  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 Visual Studio implémente cette interface.  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 Utilisez [QueryInterface](/cpp/atl/queryinterface) pour obtenir cette interface dans un [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) interface. Un appel à [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md) peut également retourner cette interface. Cette interface est utilisée plus souvent par un fournisseur de port personnalisé pour lancer des programmes sur un serveur (local ou distant).  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Outre les méthodes sur le [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) interface, cette interface implémente les méthodes suivantes :  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetServerName](../../../extensibility/debugger/reference/idebugcoreserver3-getservername.md)|Récupère le nom du serveur.|  
|[GetServerFriendlyName](../../../extensibility/debugger/reference/idebugcoreserver3-getserverfriendlyname.md)|Récupère une version conviviale du nom du serveur|  
|[EnableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-enableautoattach.md)|Indique les moteurs de débogage spécifiques attachement automatique au processus de démarrage de ces processus.|  
|[DiagnoseWebDebuggingError](../../../extensibility/debugger/reference/idebugcoreserver3-diagnosewebdebuggingerror.md)|Récupère un code d’erreur spécifique lors de l’échec de l’attachement automatique.|  
|[CreateInstanceInServer](../../../extensibility/debugger/reference/idebugcoreserver3-createinstanceinserver.md)|Crée une instance d’un moteur de débogage sur le serveur.|  
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugcoreserver3-queryislocal.md)|Récupère un indicateur qui indique si le serveur est sur le même ordinateur que l’appelant.|  
|[GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)|Récupère une valeur qui indique le protocole utilisé pour communiquer avec le serveur.|  
|[DisableAutoAttach](../../../extensibility/debugger/reference/idebugcoreserver3-disableautoattach.md)|Désactive tous les attacher automatiquement les paramètres pour tous les moteurs de débogage que ce serveur connaît.|  
  
## <a name="remarks"></a>Remarques  
 Un fournisseur de port personnalisé reçoit le [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) interface sur un appel à [événement](../../../extensibility/debugger/reference/idebugportevents2-event.md). Le `IDebugCoreServer3` interface peut être obtenue à partir de cette interface.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)   
 [GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)