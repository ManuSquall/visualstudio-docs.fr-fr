---
title: IDebugPortSupplierEx2 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugPortSupplierEx2 interface
ms.assetid: dae0050a-a50a-4f35-bfbd-e538f537b20f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 78ba4b16837200f729ec4f8b9061dbb321ee58ae
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31115897"
---
# <a name="idebugportsupplierex2"></a>IDebugPortSupplierEx2
Fournit la prise en charge pour un fournisseur de port sélectionner et d’interagir avec un serveur de base.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugPortSupplierEx2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 Un fournisseur de port personnalisé implémente cette interface afin qu’elle peut sélectionner le serveur de base à utiliser.  
  
## <a name="methods"></a>Méthodes  
 Le tableau suivant présente les méthodes de **IDebugPortSupplierEx2**.  
  
|Méthode|Description|  
|------------|-----------------|  
|[SetServer](../../../extensibility/debugger/reference/idebugportsupplierex2-setserver.md)|Définit le serveur de base pour le fournisseur de port.|  
  
## <a name="requirements"></a>Spécifications  
 En-tête : Portpriv.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)