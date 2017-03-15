---
title: "IDebugPortPicker::DisplayPortPicker | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "DisplayPortPicker"
  - "IDebugPortPicker::DisplayPortPicker"
ms.assetid: 08511ef5-be64-4069-b169-a569cc94bc64
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugPortPicker::DisplayPortPicker
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Affiche la boîte de dialogue spécifiée qui permet à l'utilisateur de sélectionner un port.  
  
## Syntaxe  
  
```cpp#  
HRESULT DisplayPortPicker(  
   HWND hwndParentDialog,  
   BSTR* pbstrPortId  
);  
```  
  
```c#  
public int DisplayPortPicker(  
   int hwndParentDialog,  
   out string pbstrPortId  
);  
```  
  
#### Paramètres  
 `hwndParentDialog`  
 \[in\]  Handle de la boîte de dialogue parente.  
  
 `pbstrPortId`  
 \[out\]  Chaîne d'identificateur de port.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  Une valeur de retour d' `S_FALSE` \(ou une valeur de retour d' `S_OK` avec `BSTR` défini à `NULL`\) indique que l'utilisateur a cliqué **Annuler**.  
  
## Voir aussi  
 [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)