---
title: IDebugCustomViewer::DisplayValue | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugCustomViewer::DisplayValue
helpviewer_keywords: IDebugCustomViewer::DisplayValue
ms.assetid: 7a538248-5ced-450e-97cd-13fabe35fb1c
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 701c5e33273dc6d00156e554e1abaa9a003568eb
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="idebugcustomviewerdisplayvalue"></a>IDebugCustomViewer::DisplayValue
Cette méthode est appelée pour afficher la valeur spécifiée.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT DisplayValue(  
   HWND             hwnd,  
   DWORD            dwID,  
   IUnknown *       pHostServices,  
   IDebugProperty3* pDebugProperty);  
);  
```  
  
```csharp  
int DisplayValue(  
   IntPtr          hwnd,   
   uint            dwID,   
   object          pHostServices,   
   IDebugProperty3 pDebugProperty  
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 `hwnd`  
 [in] Fenêtre parente  
  
 `dwID`  
 [in] ID de visionneuses personnalisées qui prennent en charge plusieurs types.  
  
 `pHostServices`  
 [in] Réservé. Toujours la valeur null.  
  
 `pDebugProperty`  
 [in] Interface qui peut être utilisé pour récupérer la valeur à afficher.  
  
## <a name="return-value"></a>Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon retourne le code d’erreur.  
  
## <a name="remarks"></a>Remarques  
 L’affichage est « modale » dans la mesure où cette méthode crée la fenêtre nécessaire, afficher la valeur, attendez d’entrée et fermer la fenêtre, tous les avant de retourner à l’appelant. Cela signifie que la méthode doit gérer tous les aspects de l’affichage de la valeur de propriété, à partir de la création d’une fenêtre pour la sortie, au lieu d’attendre pour l’entrée d’utilisateur, de la destruction de la fenêtre.  
  
 Pour prendre en charge la modification de la valeur de la donnée [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) de l’objet, vous pouvez utiliser la [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md) (méthode), si la valeur peut être exprimée sous forme de chaîne. Sinon, il est nécessaire de créer une interface personnalisée : exclusifs à l’évaluateur d’expression que l’implémentation de cela `DisplayValue` (méthode), sur le même objet qui implémente le `IDebugProperty3` interface. Cette interface personnalisée fournirait des méthodes de modification des données d’une taille arbitraire ou de la complexité.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)