---
title: IEnumCodePaths2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumCodePaths2
helpviewer_keywords:
- IEnumCodePaths2 interface
ms.assetid: 17ec9f9e-dc06-4532-b5db-da52efcc8630
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 577b2691ed67751407621d5000ee9a8abec318df
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68192015"
---
# <a name="ienumcodepaths2"></a>IEnumCodePaths2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Cette interface représente une liste de chemins de code.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IEnumCodePaths2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 Le moteur de débogage (DE) implémente cette interface pour représenter une liste de chemins de code.  
  
## <a name="notes-for-callers"></a>Notes pour les appelants  
 Appelez [EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md) pour obtenir cette interface.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Le tableau suivant présente les méthodes de `IEnumCodePaths2` .  
  
|Méthode|Description|  
|------------|-----------------|  
|[Next](../../../extensibility/debugger/reference/ienumcodepaths2-next.md)|Récupère un nombre spécifié de chemins de code dans une séquence d’énumération.|  
|[Skip](../../../extensibility/debugger/reference/ienumcodepaths2-skip.md)|Ignore un nombre spécifié de chemins de code dans une séquence d’énumération.|  
|[Réinitialiser](../../../extensibility/debugger/reference/ienumcodepaths2-reset.md)|Réinitialise une séquence d'énumération.|  
|[Clone](../../../extensibility/debugger/reference/ienumcodepaths2-clone.md)|Crée un énumérateur qui contient le même état d’énumération que l’énumérateur actuel.|  
|[GetCount](../../../extensibility/debugger/reference/ienumcodepaths2-getcount.md)|Obtient le nombre de chemins de code dans un énumérateur.|  
  
## <a name="remarks"></a>Notes  
 Un chemin d’accès de code représente un point de branche ou un appel de fonction dans un programme. Une liste de chemins de code représente le chemin d’accès utilisé par l’exécution du code.  
  
## <a name="requirements"></a>Configuration requise  
 En-tête : msdbg. h  
  
 Espace de noms : Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)
