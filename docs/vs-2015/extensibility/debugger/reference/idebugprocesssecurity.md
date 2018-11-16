---
title: IDebugProcessSecurity | Microsoft Docs
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
- IDebugProcessSecurity interface
ms.assetid: 8a52ddca-bd99-49c0-9778-469dce7abd44
caps.latest.revision: 5
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 69efa5cf6f9a71e4d66ef03907645644a644413c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51735768"
---
# <a name="idebugprocesssecurity"></a>IDebugProcessSecurity
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

`IDebugProcessSecurity` est implémentée par un fournisseur de port pour avertir l’utilisateur que l’attachement au processus unsafe.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugProcessSecurity : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IDebugProcessSecurity`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetUserName](../../../extensibility/debugger/reference/idebugprocesssecurity-getusername.md)|Obtient le nom d’utilisateur du fournisseur de port.|  
|[QueryCanSafelyAttach](../../../extensibility/debugger/reference/idebugprocesssecurity-querycansafelyattach.md)|Avertit un utilisateur que l’attachement au processus de débogage est unsafe.|  
  
## <a name="remarks"></a>Notes  
 Implémentez cette interface pour afficher un avertissement et autoriser l’utilisateur à annuler si le processus auquel vous joignez peuvent être considérées comme unsafe.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Ports](../../../extensibility/debugger/ports.md)   
 [Fournisseurs de port](../../../extensibility/debugger/port-suppliers.md)   
 [Interfaces principales](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)

