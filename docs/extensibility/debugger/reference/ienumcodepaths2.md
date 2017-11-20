---
title: IEnumCodePaths2 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEnumCodePaths2
helpviewer_keywords: IEnumCodePaths2 interface
ms.assetid: 17ec9f9e-dc06-4532-b5db-da52efcc8630
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a9c27084032e0492b1110b1a085ded4f8e556433
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="ienumcodepaths2"></a>IEnumCodePaths2
Cette interface représente une liste de chemins d’accès du code.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IEnumCodePaths2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 Le moteur de débogage (DE) implémente cette interface pour représenter une liste de chemins d’accès du code.  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 Appelez [EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md) pour obtenir cette interface.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IEnumCodePaths2`.  
  
|Méthode|Description|  
|------------|-----------------|  
|[Next](../../../extensibility/debugger/reference/ienumcodepaths2-next.md)|Récupère un nombre spécifié de chemins d’accès du code dans une séquence d’énumération.|  
|[Skip](../../../extensibility/debugger/reference/ienumcodepaths2-skip.md)|Ignore un nombre spécifié de chemins d’accès du code dans une séquence d’énumération.|  
|[Réinitialiser](../../../extensibility/debugger/reference/ienumcodepaths2-reset.md)|Réinitialise la séquence d’énumération au début.|  
|[Clone](../../../extensibility/debugger/reference/ienumcodepaths2-clone.md)|Crée un énumérateur qui contient le même état d’énumération que l’énumérateur actuel.|  
|[GetCount](../../../extensibility/debugger/reference/ienumcodepaths2-getcount.md)|Obtient le nombre de chemins d’accès du code dans un énumérateur.|  
  
## <a name="remarks"></a>Remarques  
 Un chemin d’accès du code représente un appel de fonction ou de point de branche dans un programme. Une liste de chemins d’accès du code représente le chemin d’accès qui a pris l’exécution du code.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)