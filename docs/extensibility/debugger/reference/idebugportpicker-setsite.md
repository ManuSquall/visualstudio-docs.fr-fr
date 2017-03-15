---
title: "IDebugPortPicker::SetSite | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugPortPicker::SetSite"
ms.assetid: 7319e187-adfe-4b3f-aec9-521356fb5a8a
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# IDebugPortPicker::SetSite
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

définit le fournisseur de services.  
  
## Syntaxe  
  
```cpp#  
HRESULT SetSite(  
   IServiceProvider * pSP  
);  
```  
  
```c#  
public int SetSite(  
   IServiceProvider pSP  
);  
```  
  
#### Paramètres  
 `pSP`  
 \[in\]  référence à l'interface du fournisseur de services.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Cette méthode sera appelée avant que toutes les autres méthodes sont appelées.  
  
## Voir aussi  
 [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)