---
title: IDebugProperty3 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProperty3
helpviewer_keywords:
- IDebugProperty3 interface
ms.assetid: 8f9be68d-4490-4eca-8f6b-8a10ed77e226
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ad01cf848d90a421f36aba65876afdd94ac9649c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55002663"
---
# <a name="idebugproperty3"></a>IDebugProperty3
Cette interface prend en charge :  
  
-   Récupération d’une chaîne de longueur arbitraire associée à la propriété.  
  
-   Association d’un ID unique à la propriété.  
  
-   Récupération d’une liste des visionneuses personnalisées pour la propriété.  
  
-   Définition de la valeur d’une propriété avec la capacité à signaler les erreurs résultantes  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugProperty3 : IDebugProperty2  
```  
  
## <a name="notes-for-implementers"></a>Notes de publication pour les implémenteurs  
 Le moteur de débogage (dé) implémente cette interface sur le même objet qui implémente [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) pour prendre en charge pour les chaînes longues, les ID de propriété et les visionneuses personnalisées.  
  
## <a name="notes-for-callers"></a>Notes de publication pour les appelants  
 Appelez [QueryInterface](/cpp/atl/queryinterface) sur un `IDebugProperty2` interface pour obtenir cette interface.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Outre les méthodes héritées de `IDebugProperty2`, le `IDebugProperty3` interface expose les méthodes suivantes.  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetStringCharLength](../../../extensibility/debugger/reference/idebugproperty3-getstringcharlength.md)|Retourne la longueur de la chaîne associée à la propriété.|  
|[GetStringChars](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md)|Retourne la chaîne dans une mémoire tampon fournie par l’utilisateur.|  
|[CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)|Crée un ID unique pour cette propriété.|  
|[DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)|Détruit l’ID unique pour cette propriété.|  
|[GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md)|Retourne le nombre de visionneuses personnalisées, cette propriété peut être consultée avec.|  
|[GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)|Retourne la liste des visionneuses personnalisées, cette propriété peut être consultée avec.|  
|[SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)|Définit la valeur de cette propriété, qui retourne un message d’erreur si quelque chose tournait mal.|  
  
## <a name="remarks"></a>Notes  
 [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md) est la meilleure méthode pour le Gestionnaire de session de débogage (SDM) pour définir la valeur d’une propriété.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Espace de noms : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces principales](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)