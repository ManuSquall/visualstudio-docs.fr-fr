---
title: IDebugProperty3 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProperty3
helpviewer_keywords: IDebugProperty3 interface
ms.assetid: 8f9be68d-4490-4eca-8f6b-8a10ed77e226
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 091ebddc0c3424bdbf8126257fe56e6959bc28c8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugproperty3"></a>IDebugProperty3
Cette interface prend en charge :  
  
-   Récupération d’une chaîne de longueur arbitraire associée à la propriété.  
  
-   Association d’un ID unique à la propriété.  
  
-   Récupération d’une liste des visionneuses personnalisées pour la propriété.  
  
-   La valeur d’une propriété avec la capacité à signaler les erreurs rencontrées  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugProperty3 : IDebugProperty2  
```  
  
## <a name="notes-for-implementers"></a>Notes pour les implémenteurs  
 Le moteur de débogage (DE) implémente cette interface sur le même objet qui implémente [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) pour prendre en charge des chaînes longues, les identificateurs de propriété et les visionneuses personnalisées.  
  
## <a name="notes-for-callers"></a>Remarques pour les appelants  
 Appelez [QueryInterface](/cpp/atl/queryinterface) sur une `IDebugProperty2` interface pour obtenir cette interface.  
  
## <a name="methods-in-vtable-order"></a>Méthodes dans l'ordre Vtable  
 Outre les méthodes héritées de `IDebugProperty2`, le `IDebugProperty3` interface expose les méthodes suivantes.  
  
|Méthode|Description|  
|------------|-----------------|  
|[GetStringCharLength](../../../extensibility/debugger/reference/idebugproperty3-getstringcharlength.md)|Retourne la longueur de la chaîne associée à la propriété.|  
|[GetStringChars](../../../extensibility/debugger/reference/idebugproperty3-getstringchars.md)|Retourne la chaîne dans une mémoire tampon fournie par l’utilisateur.|  
|[CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)|Crée un ID unique pour cette propriété.|  
|[DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)|Détruit l’ID unique pour cette propriété.|  
|[GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md)|Retourne le nombre de visionneuses personnalisées pour cette propriété peut être affichée avec.|  
|[GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)|Retourne la liste des visionneuses personnalisées pour cette propriété peut être affichée avec.|  
|[SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)|Définit la valeur de cette propriété, en retournant un message d’erreur si tout est survenu.|  
  
## <a name="remarks"></a>Remarques  
 [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md) est recommandée pour le Gestionnaire de session de débogage (SDM) pour définir une valeur de propriété.  
  
## <a name="requirements"></a>Spécifications  
 En-tête : msdbg.h  
  
 Namespace : Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly : Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)