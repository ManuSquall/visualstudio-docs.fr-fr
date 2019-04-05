---
title: IEnumDebugFrameInfo2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugFrameInfo2
helpviewer_keywords:
- IEnumDebugFrameInfo2
ms.assetid: 994e30ad-435a-4f9e-9272-d96d9e01099c
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6cc6a0ff332fd6feac72ce4abf38b5319e63c913
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58938592"
---
# <a name="ienumdebugframeinfo2"></a>IEnumDebugFrameInfo2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Cette interface énumère [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) structures.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IEnumDebugFrameInfo2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs  
 Le moteur de débogage (dé) implémente cette interface pour fournir une liste de structures qui décrit la pile des appels actuelle.  
  
## <a name="notes-for-callers"></a>Notes de publication pour les appelants  
 Les appels de Visual Studio [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) pour obtenir cette interface chaque fois qu’un point d’arrêt, une exception ou arrêt se produit dans un programme en cours de débogage.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IEnumDebugFrameInfo2`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[Next](../../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md)|Récupère un nombre spécifié de [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) structures dans une séquence d’énumération.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugframeinfo2-skip.md)|Ignore un nombre spécifié de [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) structures dans une séquence d’énumération.|  
|[Reset](../../../extensibility/debugger/reference/ienumdebugframeinfo2-reset.md)|Réinitialise une séquence d’énumération au début.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugframeinfo2-clone.md)|Crée un énumérateur qui contient le même état d’énumération que l’énumérateur en cours.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugframeinfo2-getcount.md)|Obtient le nombre de [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) structures dans un énumérateur.|  
  
## <a name="remarks"></a>Notes  
 Visual Studio obtient cette interface en tant que la première étape à la gestion d’un point d’arrêt, une exception ou généré par l’utilisateur de pause sur le programme en cours de débogage. La liste des [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) structures représente la pile des appels actuelle, avec l’appel de fonction en cours au début de la liste et la plus ancienne fonction appeler à la fin de la liste. Chaque `FRAMEINFO` représente un frame de pile, un contexte dans lequel les expressions peuvent être évaluées et examiné des variables locales.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg.h  
  
 Espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces principales](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)
