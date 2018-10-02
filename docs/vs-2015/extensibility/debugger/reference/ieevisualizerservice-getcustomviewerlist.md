---
title: IEEVisualizerService::GetCustomViewerList | Microsoft Docs
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
- IEEVisualizerService::GetCustomViewerList
helpviewer_keywords:
- IEEVisualizerService::GetCustomViewerList method
ms.assetid: 249d26ca-914f-43af-a400-8162477223f4
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e037ac728c47b2b4610d866b2ba3868dc44b4eb0
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47492787"
---
# <a name="ieevisualizerservicegetcustomviewerlist"></a>IEEVisualizerService::GetCustomViewerList
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [IEEVisualizerService::GetCustomViewerList](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist).  
  
Cette méthode retourne une liste de visualiseurs de type que ce service connaît.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetCustomViewerList(  
   ULONG                celtSkip,  
   ULONG                celtRequested,  
   DEBUG_CUSTOM_VIEWER* rgViewers,  
   ULONG*               pceltFetched  
);  
```  
  
```csharp  
int GetCustomViewerList(  
   uint                  celtSkip,  
   uint                  celtRequested,  
   DEBUG_CUSTOM_VIEWER[] rgViewers,  
   out uint              pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `celtSkip`  
 [in] Nombre de visualiseurs à ignorer.  
  
 `celRequested`  
 [in] Nombre de visualiseurs pour récupérer (spécifie également la taille de la `rgViewers` tableau).  
  
 `rgViewers`  
 [in, out] Tableau de [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) structures doit être renseigné.  
  
 `pceltFetched`  
 [out] Nombre de visualiseurs réellement récupérées.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d’erreur.  
  
## <a name="remarks"></a>Notes  
 [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) transmet la demande à cette méthode dans le cadre de sa prise en charge pour les visualiseurs de type. Si l’évaluateur d’expression fournit également des visionneuses personnalisées pour le même type, il peut ajouter correctement rempli [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) structures pour ces visionneuses personnalisées pour la liste. Assurez-vous que l’option [GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) reflète ces visionneuses supplémentaires.  
  
 Consultez [visualiseur de Type et Visionneuse de personnalisé](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md) pour plus d’informations sur les différences entre les visualiseurs et les visionneuses.  
  
## <a name="see-also"></a>Voir aussi  
 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md)   
 [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)   
 [GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md)   
 [Visualiseur de type et visionneuse personnalisée](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)

