---
title: IDebugDynamicField | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugDynamicField
helpviewer_keywords:
- IDebugDynamicField interface
ms.assetid: caffbd95-7596-4714-84b1-b964e89a78bb
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7e975940947b68fdce34bd7d1e2e289c85914c44
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47508308"
---
# <a name="idebugdynamicfield"></a>IDebugDynamicField
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [IDebugDynamicField](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugdynamicfield).  
  
Cette interface représente un type d’une variable.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugDynamicField : IDebugField  
```  
  
## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs  
 Cette interface est implémentée par les fournisseurs de symbole comme classe de base pour tout type qui peut être déterminée au moment de l’exécution. Il s’agit uniquement du code managé.  
  
## <a name="notes-for-callers"></a>Notes de publication pour les appelants  
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

