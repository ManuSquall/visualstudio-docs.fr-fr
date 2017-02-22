---
title: "IDebugMethodField::GetThis | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugMethodField::GetThis"
helpviewer_keywords: 
  - "IDebugMethodField::GetThis (méthode)"
ms.assetid: cc235bea-e909-4d8c-ab54-936736c803fc
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugMethodField::GetThis
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

obtient le pointeur d' `this` \(`Me` dans [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)]\) de l'objet contenant la méthode.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetThis(   
   IDebugClassField** ppClass  
);  
```  
  
```c#  
int GetThis(  
   out IDebugClassField ppClass  
);  
```  
  
#### Paramètres  
 `ppClass`  
 \[out\]  Retourne un objet d' [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) représentant le pointeur « this ».  
  
## Valeur de retour  
 En cas de réussite, retourne S\_OK ; sinon, retourne un code d'erreur.  
  
## Notes  
 Dans les langages orientés objet, il y a généralement un pointeur implicite à l'instanciation actuelle d'une classe.  Il s'agit `this` dans C\#\/C\+\+ et comme `Me` dans [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)].  
  
## Voir aussi  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)