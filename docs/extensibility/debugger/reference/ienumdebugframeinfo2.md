---
title: IEnumDebugFrameInfo2 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumDebugFrameInfo2
helpviewer_keywords:
- IEnumDebugFrameInfo2
ms.assetid: 994e30ad-435a-4f9e-9272-d96d9e01099c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 858250c3c951880cf905ea6ee150f1ff61008204
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31123916"
---
# <a name="ienumdebugframeinfo2"></a>IEnumDebugFrameInfo2
Cette interface énumère [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) structures.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IEnumDebugFrameInfo2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 Le moteur de débogage (DE) implémente cette interface pour fournir une liste de structures qui décrit la pile des appels actuelle.  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 Appels de Visual Studio [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) pour obtenir cette interface chaque fois qu’un point d’arrêt, une exception ou arrêt se produit dans un programme en cours de débogage.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IEnumDebugFrameInfo2`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[Next](../../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md)|Récupère un nombre spécifié de [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) structures dans une séquence d’énumération.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugframeinfo2-skip.md)|Ignore un nombre spécifié de [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) structures dans une séquence d’énumération.|  
|[Réinitialiser](../../../extensibility/debugger/reference/ienumdebugframeinfo2-reset.md)|Réinitialise la séquence d’énumération au début.|  
|[Clone](../../../extensibility/debugger/reference/ienumdebugframeinfo2-clone.md)|Crée un énumérateur qui contient le même état d’énumération que l’énumérateur actuel.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugframeinfo2-getcount.md)|Obtient le nombre de [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) structures dans un énumérateur.|  
  
## <a name="remarks"></a>Notes  
 Visual Studio obtient cette interface en tant que la première étape à la gestion d’un point d’arrêt, une exception ou généré par l’utilisateur de pause sur le programme en cours de débogage. La liste des [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) structures représente la pile des appels actuelle, avec l’appel de fonction en cours au début de la liste et la fonction la plus ancienne des appels à la fin de la liste. Chaque `FRAMEINFO` représente un frame de pile, un contexte dans lequel les expressions peuvent être évaluées et variables locales est examiné.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)