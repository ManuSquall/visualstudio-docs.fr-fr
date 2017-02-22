---
title: "IDebugClassField::EnumNestedClasses | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugClassField::EnumNestedClasses"
helpviewer_keywords: 
  - "IDebugClassField::EnumNestedClasses (méthode)"
ms.assetid: 2ba5ef0c-395e-4006-9e3c-9b06e1d711d0
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugClassField::EnumNestedClasses
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

crée un énumérateur pour les classes imbriquées dans cette classe.  
  
## Syntaxe  
  
```cpp#  
HRESULT EnumNestedClasses(   
   IEnumDebugFields** ppEnum  
);  
```  
  
```c#  
int EnumNestedClasses(  
   out IEnumDebugFields ppEnum  
);  
```  
  
#### Paramètres  
 `ppEnum`  
 \[out\]  Retourne un objet d' [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) représentant la liste des classes imbriquées.  Retourne une valeur NULL s'il n'y a aucune classe imbriquée.  
  
## Valeur de retour  
 En cas de réussite, retourne S\_OK ou retourne S\_FALSE s'il n'y a aucune classe imbriquée.  Sinon, retourne un code d'erreur.  
  
## Notes  
 chaque élément de l'énumération est un objet d' [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) décrivant une classe imbriquée.  
  
 Une classe imbriquée est une classe définie à l'intérieur d'une autre classe.  Par exemple :  
  
```  
class RootClass {  
   class NestedClass { }  
};  
```  
  
 L'énumération d' [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) correspondrait un objet qui représente la classe d' `NestedClass` .  
  
## Voir aussi  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)