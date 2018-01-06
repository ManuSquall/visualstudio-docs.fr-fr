---
title: IDebugPortRequest2 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugPortRequest2
helpviewer_keywords: IDebugPortRequest2 interface
ms.assetid: 556e610d-7c4b-44a8-965a-76a9d02b601a
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 5b47a9bde47049c957af9f60e1d09d03b55c2359
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugportrequest2"></a>IDebugPortRequest2
Cette interface décrit un port. Cette description est utilisée pour ajouter le port à un fournisseur de port.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugPortRequest2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 En général, Visual Studio implémente cette interface en cours de mise en route d’un port de débogage à partir d’un fournisseur de port.  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 Cette interface est passée à [ajouter un port](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) pour créer un port de débogage. Un appel à [GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md) retourne cette interface, qui représente la demande permet de créer le port en premier lieu.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IDebugPortRequest2`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetPortName](../../../extensibility/debugger/reference/idebugportrequest2-getportname.md)|Obtient le nom du port à créer.|  
  
## <a name="remarks"></a>Notes  
 En général, un moteur de débogage n’interagit pas avec un fournisseur de port et n’en aurez aucune utilisation de cette interface.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [Ajouter un port](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)   
 [GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)