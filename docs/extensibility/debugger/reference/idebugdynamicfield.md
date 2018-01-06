---
title: IDebugDynamicField | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugDynamicField
helpviewer_keywords: IDebugDynamicField interface
ms.assetid: caffbd95-7596-4714-84b1-b964e89a78bb
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: d1fdd5e0eeb7aeb88b999e72dac875a41c0e0b03
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="idebugdynamicfield"></a>IDebugDynamicField
Cette interface représente un type d’une variable.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugDynamicField : IDebugField  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 Cette interface est implémentée par les fournisseurs de symboles en tant que classe de base pour n’importe quel type peut être déterminée au moment de l’exécution. Il s’agit uniquement du code managé.  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 Cette interface représente une classe de base à partir de laquelle des interfaces plus spécialisées peuvent être dérivées.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l’ordre Vtable  
 Cette interface ne fournit pas toutes les méthodes autres que celles héritées de `IDebugField`.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : sh.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de fournisseur de symboles](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)