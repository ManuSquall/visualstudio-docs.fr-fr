---
title: "IEnumDebugCustomAttributes::Reset | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumCustomAttributes::Reset"
helpviewer_keywords: 
  - "IEnumDebugCustomAttributes::Reset"
ms.assetid: e0db6518-5a71-4adb-a407-4d2ac7a3e369
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumDebugCustomAttributes::Reset
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Remet au début la séquence d'énumération.  
  
## Syntaxe  
  
```cpp#  
HRESULT Reset(void);  
```  
  
```c#  
int Reset();  
```  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Une fois que cette méthode soit appelée, l'appel suivant à la méthode d' [Suivant](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md) retourne le premier élément de l'énumération.  
  
## Voir aussi  
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)   
 [Suivant](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md)