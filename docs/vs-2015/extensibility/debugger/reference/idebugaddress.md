---
title: IDebugAddress | Microsoft Docs
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
- IDebugAddress
helpviewer_keywords:
- IDebugAddress interface
ms.assetid: bc709ff7-4966-4f36-9af2-690efe2cea1d
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 75a5b1ab9979d7d071282ab4d807d89b5e7abb2b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47507785"
---
# <a name="idebugaddress"></a>IDebugAddress
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [IDebugAddress](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugaddress).  
  
Cette interface représente l’adresse d’un élément. Elle est retournée par le Gestionnaire de symboles.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugAddress : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs  
 Un fournisseur de symboles implémente cette interface pour représenter une adresse d’un objet.  
  
## <a name="notes-for-callers"></a>Notes de publication pour les appelants  
 De nombreuses méthodes sur le nombre d’interfaces retournent cette interface.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Cette interface implémente la méthode suivante :  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)|Récupère un [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) structure qui décrit un objet et son emplacement.|  
  
## <a name="remarks"></a>Notes  
 Le fournisseur de symboles retourne cette interface pour représenter un objet et son emplacement au sein d’une étendue particulière (par exemple, fonction, méthode ou classe). Cette interface est retournée à partir d’et passée à différentes méthodes de fournisseur de symboles et de l’expression évaluateur. Normalement, le fournisseur de symboles est la seule entité qui a besoin d’interpréter le contenu de cette interface.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : sh.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de fournisseur de symboles](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)

