---
title: "IDebugMethodField::EnumArguments | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugMethodField::EnumArguments"
helpviewer_keywords: 
  - "IDebugMethodField::EnumArguments (méthode)"
ms.assetid: 3ab55488-2437-4ff6-a9ae-78ea6d7b23a8
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugMethodField::EnumArguments
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

crée un énumérateur pour le type de chaque argument requis pour appeler la méthode.  
  
## Syntaxe  
  
```cpp#  
HRESULT EnumArguments(   
   IEnumDebugFields** ppParams  
);  
```  
  
```c#  
int EnumArguments(  
   out IEnumDebugFields ppParams  
);  
```  
  
#### Paramètres  
 `ppParams`  
 \[out\]  Retourne un objet d' [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) représentant la liste de types d'argument.  Retourne une valeur NULL si aucun argument n'est spécifié.  
  
## Valeur de retour  
 En cas de réussite, retourne S\_OK ou retourne S\_FALSE si aucun argument n'est spécifié.  Sinon, retourne un code d'erreur.  
  
## Notes  
 chaque élément est un objet d' [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) représentant les types de chaque paramètre.  Appelez la méthode d' [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) pour récupérer des informations sur le type de chaque paramètre.  
  
 Si le nom du paramètre est nécessaire avec le type, puis appelez la méthode d' [EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md) .  
  
## Voir aussi  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md)