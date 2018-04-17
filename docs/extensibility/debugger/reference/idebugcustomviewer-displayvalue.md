---
title: IDebugCustomViewer::DisplayValue | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugCustomViewer::DisplayValue
helpviewer_keywords:
- IDebugCustomViewer::DisplayValue
ms.assetid: 7a538248-5ced-450e-97cd-13fabe35fb1c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 017e1e7a27839dae91559468c62be353bbd43b4e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
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
  
## <a name="remarks"></a>Notes  
 L’affichage est « modale » dans la mesure où cette méthode crée la fenêtre nécessaire, afficher la valeur, attendez d’entrée et fermer la fenêtre, tous les avant de retourner à l’appelant. Cela signifie que la méthode doit gérer tous les aspects de l’affichage de la valeur de propriété, à partir de la création d’une fenêtre pour la sortie, au lieu d’attendre pour l’entrée d’utilisateur, de la destruction de la fenêtre.  
  
 Pour prendre en charge la modification de la valeur de la donnée [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) de l’objet, vous pouvez utiliser la [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md) (méthode), si la valeur peut être exprimée sous forme de chaîne. Sinon, il est nécessaire de créer une interface personnalisée : exclusifs à l’évaluateur d’expression que l’implémentation de cela `DisplayValue` (méthode), sur le même objet qui implémente le `IDebugProperty3` interface. Cette interface personnalisée fournirait des méthodes de modification des données d’une taille arbitraire ou de la complexité.  
  
## <a name="see-also"></a>Voir aussi  
 [IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)