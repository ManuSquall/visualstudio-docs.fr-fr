---
title: "IDebugClassField::EnumNestedEnums | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugClassField::EnumNestedEnums"
helpviewer_keywords: 
  - "IDebugClassField::EnumNestedEnums (méthode)"
ms.assetid: 90fd0cef-9145-4de6-91d4-6c881df39d6e
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugClassField::EnumNestedEnums
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

crée un énumérateur pour les énumérateurs imbriqués de cette classe.  
  
## Syntaxe  
  
```cpp#  
HRESULT EnumNestedEnums(   
   IEnumDebugFields** ppEnum  
);  
```  
  
```c#  
int EnumNestedEnums(  
   out IEnumDebugFields ppEnum  
);  
```  
  
#### Paramètres  
 `ppEnum`  
 \[out\]  Retourne un objet d' [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) représentant la liste d'énumérations imbriquées.  Retourne une valeur NULL s'il n'y a aucune énumération imbriquée.  
  
## Valeur de retour  
 En cas de réussite, retourne S\_OK ou retourne S\_FALSE s'il n'y a aucun énumérateur imbriqué.  Sinon, retourne un code d'erreur.  
  
## Notes  
 chaque élément de l'énumération est un objet d' [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md) décrivant une énumération imbriquée.  
  
 Une énumération déclarée à l'intérieur d'une classe est considérée comme une énumération imbriquée.  Supposons, par exemple :  
  
```  
class RootClass {  
   enum NestedEnum { EnumValue = 0 }  
};  
```  
  
 La méthode d' `EnumNestedEnums` retourne un objet d' [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) qui contient un objet d' [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md) qui représente l'énumération d' `NestedEnum` .  
  
## Voir aussi  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)