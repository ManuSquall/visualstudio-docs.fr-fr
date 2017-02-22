---
title: "IDebugCustomViewer::DisplayValue | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCustomViewer::DisplayValue"
helpviewer_keywords: 
  - "IDebugCustomViewer::DisplayValue"
ms.assetid: 7a538248-5ced-450e-97cd-13fabe35fb1c
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugCustomViewer::DisplayValue
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

cette méthode est appelée pour afficher la valeur spécifiée.  
  
## Syntaxe  
  
```cpp#  
HRESULT DisplayValue(  
   HWND             hwnd,  
   DWORD            dwID,  
   IUnknown *       pHostServices,  
   IDebugProperty3* pDebugProperty);  
);  
```  
  
```c#  
int DisplayValue(  
   IntPtr          hwnd,   
   uint            dwID,   
   object          pHostServices,   
   IDebugProperty3 pDebugProperty  
);  
```  
  
#### Paramètres  
 `hwnd`  
 \[in\]  fenêtre parente  
  
 `dwID`  
 \[in\]  ID pour les visionneuses personnalisées qui prennent en charge plusieurs types.  
  
 `pHostServices`  
 \[in\] Réservé.  toujours défini pour annuler.  
  
 `pDebugProperty`  
 \[in\]  Interface qui peut être utilisé pour récupérer la valeur à afficher.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon retourne un code d'erreur.  
  
## Notes  
 L'affichage est « modale » dans la mesure où cette méthode crée la fenêtre nécessaire, affiche la valeur, attend que l'entrée, et ferme la fenêtre, tous avant de retourner à l'appelant.  Cela signifie que la méthode doit gérer tous les aspects du rendu la valeur de propriété, de créer une fenêtre pour la sortie, à l'entrée d'utilisateur en attente, à détruire la fenêtre.  
  
 Pour prendre en charge modifier la valeur de l'objet donné d' [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) , vous pouvez utiliser la méthode d' [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md) \- si la valeur peut être exprimée sous forme de chaîne.  Sinon, il est nécessaire de créer une interface\-exclusivité personnalisée à l'évaluateur d'expression en implémentant cet `DisplayValue` méthode\-sur le même objet qui implémente l'interface d' `IDebugProperty3` .  Cette interface personnalisée fournit des méthodes pour modifier les données d'une taille ou d'une complexité arbitraire.  
  
## Voir aussi  
 [IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)