---
title: IDebugPortSupplierEx2 | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugPortSupplierEx2 interface
ms.assetid: dae0050a-a50a-4f35-bfbd-e538f537b20f
caps.latest.revision: 5
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 594bb0625036cb42e18c63e4b836df732e39a17e
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49193990"
---
# <a name="idebugportsupplierex2"></a>IDebugPortSupplierEx2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Prend en charge pour un fournisseur de port sélectionner et d’interagir avec un serveur de base.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugPortSupplierEx2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs  
 Un fournisseur de port personnalisé implémente cette interface afin qu’elle peut sélectionner le serveur de base à utiliser.  
  
## <a name="methods"></a>Méthodes  
 Le tableau suivant présente les méthodes de **IDebugPortSupplierEx2**.  
  
|Méthode|Description|  
|------------|-----------------|  
|[SetServer](../../../extensibility/debugger/reference/idebugportsupplierex2-setserver.md)|Définit le serveur de base pour le fournisseur de port.|  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : Portpriv.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces principales](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)

