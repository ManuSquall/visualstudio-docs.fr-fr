---
title: "IDebugMethodField::EnumParameters | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugMethodField::EnumParameters"
helpviewer_keywords: 
  - "IDebugMethodField::EnumParameters (méthode)"
ms.assetid: d77b1197-deb6-4144-8d1b-8b09949ccfac
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugMethodField::EnumParameters
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

crée un énumérateur pour les paramètres de la méthode.  
  
## Syntaxe  
  
```cpp#  
HRESULT EnumParameters(   
   IEnumDebugFields** ppParams  
);  
```  
  
```c#  
int EnumParameters(  
   out IEnumDebugFields ppParams  
);  
```  
  
#### Paramètres  
 `ppParams`  
 \[out\]  Retourne un objet d' [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) représentant la liste de paramètres à la méthode ; sinon, retourne une valeur NULL s'il n'y a pas de paramètre.  
  
## Valeur de retour  
 En cas de réussite, retourne S\_OK ou retourne S\_FALSE s'il n'y a pas de paramètre.  Sinon, retourne un code d'erreur.  
  
## Notes  
 chaque élément est un objet d' [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) représentant différents types de paramètres.  Appelez la méthode d' [GetKind](../Topic/IDebugField::GetKind.md) sur chaque objet pour déterminer exactement ce que représente un type de paramètre l'objet.  
  
 Un paramètre inclut son nom de variable et son type.  Le premier paramètre à une méthode de classe est en général le pointeur « this ».  
  
 Si seuls les types des paramètres est nécessaire, appelez la méthode d' [EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) .  
  
## Voir aussi  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)