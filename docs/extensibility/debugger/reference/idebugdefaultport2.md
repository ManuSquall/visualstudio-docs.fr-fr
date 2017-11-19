---
title: IDebugDefaultPort2 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugDefaultPort2
helpviewer_keywords: IDebugDefaultPort2 interface
ms.assetid: 7b3452af-9a96-4c4c-9946-4339b72d3d7b
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a733ff466a8c0e8ad62e1d633054d0631024b9ac
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugdefaultport2"></a>IDebugDefaultPort2
Cette interface fournit plusieurs méthodes pour accéder à serveur d’un port et des fonctionnalités de notification.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugDefaultPort2 : IDebugPort2  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 Visual Studio implémente cette interface pour représenter le port de débogage pour l’accès à des programmes. Un fournisseur de port personnalisé peut également implémenter cette interface si elle gère le débogage distant.  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 Un argument de méthodes sur le [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md) interface fournit cette interface. Appel de [QueryInterface](/cpp/atl/queryinterface) sur une [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) interface peut également obtenir cette interface.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l’ordre Vtable  
 Outre les méthodes définies dans [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md), cette interface implémente les méthodes suivantes :  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetPortNotify](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md)|Obtient l’interface de notification de port à partir de ce port.|  
|[GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)|Obtient l’interface pour le serveur qui héberge ce port.|  
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugdefaultport2-queryislocal.md)|Détermine si ce port est en cours d’exécution sur l’ordinateur local.|  
  
## <a name="remarks"></a>Remarques  
 Le nom «`IDebugDefaultPort2`» est un peu trompeur, car il ne représente pas un port par défaut. Il peut être appelée « IDebugPort3 ».  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)