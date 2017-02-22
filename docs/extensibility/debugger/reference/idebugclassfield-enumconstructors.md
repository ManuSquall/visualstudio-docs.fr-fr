---
title: "IDebugClassField::EnumConstructors | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugClassField::EnumConstructors"
helpviewer_keywords: 
  - "IDebugClassField::EnumConstructors (méthode)"
ms.assetid: 66a250b2-75a0-45aa-8d58-40f91cc4bf7b
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugClassField::EnumConstructors
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Crée un énumérateur pour les constructeurs de cette classe.  
  
## Syntaxe  
  
```cpp#  
HRESULT EnumConstructors(   
   CONSTRUCTOR_ENUM   cMatch,  
   IEnumDebugFields** ppEnum  
);  
```  
  
```c#  
int EnumConstructors(  
   CONSTRUCTOR_ENUM     cMatch,   
   out IEnumDebugFields ppEnum  
);  
```  
  
#### Paramètres  
 `cMatch`  
 \[in\]  une valeur de l'énumération de [CONSTRUCTOR\_ENUM](../../../extensibility/debugger/reference/constructor-enum.md) qui spécifie le type de constructeurs à l'énumération.  
  
 `ppEnum`  
 \[out\]  Retourne un objet d' [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) représentant la liste de constructeurs.  Retourne une valeur NULL s'il n'y a pas de constructeur.  
  
## Valeur de retour  
 En cas de réussite, retourne S\_OK ou retourne S\_FALSE s'il n'y a pas de constructeur.  Sinon, retourne un code d'erreur.  
  
## Notes  
 chaque élément de l'énumération est un objet d' [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) décrivant une méthode de constructeur.  
  
 La liste des constructeurs en général n'inclut pas de constructeur par défaut fournis par un compilateur.  
  
## Voir aussi  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [CONSTRUCTOR\_ENUM](../../../extensibility/debugger/reference/constructor-enum.md)