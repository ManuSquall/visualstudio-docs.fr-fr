---
title: IDebugPortSupplier3 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugPortSupplier3
helpviewer_keywords: IDebugPortSupplier3 interface
ms.assetid: e458cd02-2370-4435-8953-17d7a60ce152
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f0e1c5c252e0674ee3de8371080e298f42de2112
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugportsupplier3"></a>IDebugPortSupplier3
Cette interface permet à un appelant déterminer si un fournisseur de port peut conserver des ports (en les écrivant sur le disque) entre les appels du débogueur, puis d’obtenir une liste de ces ports sont conservés.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugPortSupplier3 : IDebugPortSupplier2  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 Un fournisseur de port personnalisé implémente cette interface pour prendre en charge la persistance ou de l’enregistrement des informations sur le port sur le disque. Cette interface doit être implémentée sur le même objet que le [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) interface.  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 Appelez [QueryInterface](/cpp/atl/queryinterface) sur la `IDebugPortSupplier2` interface pour obtenir cette interface.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l’ordre Vtable  
 Outre les méthodes héritées de la [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) interface, cette interface prend en charge les éléments suivants :  
  
|Méthode|Description|  
|------------|-----------------|  
|[CanPersistPorts](../../../extensibility/debugger/reference/idebugportsupplier3-canpersistports.md)|Retourne si le fournisseur de port peut être rendue persistante ports (en les écrivant sur le disque) entre les appels du débogueur.|  
|[EnumPersistedPorts](../../../extensibility/debugger/reference/idebugportsupplier3-enumpersistedports.md)|Retourne un objet qui peut être utilisé pour énumérer par tous les ports qui ont été écrites sur le disque par le fournisseur de ce port.|  
  
## <a name="remarks"></a>Notes  
 Si un fournisseur de port peut être persistante ports en plusieurs endroits, il doit implémenter cette interface. Ports doivent être chargées lorsque le fournisseur de port est instancié et écrit sur le disque lorsque le fournisseur de port est détruit.  
  
 En général, un moteur de débogage n’interagit pas avec un fournisseur de port et n’en aurez aucune utilisation de cette interface.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)