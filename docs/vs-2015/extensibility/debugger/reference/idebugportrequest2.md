---
title: IDebugPortRequest2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPortRequest2
helpviewer_keywords:
- IDebugPortRequest2 interface
ms.assetid: 556e610d-7c4b-44a8-965a-76a9d02b601a
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fa72ae9d2cfbe399c3507406875e9c692d18b678
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68188339"
---
# <a name="idebugportrequest2"></a>IDebugPortRequest2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Cette interface décrit un port. Cette description est utilisée pour ajouter le port à un fournisseur de port.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugPortRequest2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 Visual Studio implémente généralement cette interface dans le processus d’obtention d’un port de débogage à partir d’un fournisseur de ports.  
  
## <a name="notes-for-callers"></a>Notes pour les appelants  
 Cette interface est transmise à [addport](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) pour créer un port de débogage. Un appel à [GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md) retourne cette interface, représentant la requête utilisée pour créer le port en premier lieu.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IDebugPortRequest2` .  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetPortName](../../../extensibility/debugger/reference/idebugportrequest2-getportname.md)|Obtient le nom du port à créer.|  
  
## <a name="remarks"></a>Notes  
 En général, un moteur de débogage n’interagit pas avec un fournisseur de port et n’a pas d’utilisation pour cette interface.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg. h  
  
 Espace de noms : Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces principales](../../../extensibility/debugger/reference/core-interfaces.md)   
 [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)   
 [GetPortRequest](../../../extensibility/debugger/reference/idebugport2-getportrequest.md)
