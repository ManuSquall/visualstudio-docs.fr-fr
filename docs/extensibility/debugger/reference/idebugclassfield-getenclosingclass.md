---
title: "IDebugClassField::GetEnclosingClass | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugClassField::GetEnclosingClass"
helpviewer_keywords: 
  - "IDebugClassField::GetEnclosingClass (méthode)"
ms.assetid: a0c12e3c-9ea0-4dfb-9e45-8cea18725022
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugClassField::GetEnclosingClass
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtient la classe qui attache cette classe.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetEnclosingClass(   
   IDebugClassField** ppClassField  
);  
```  
  
```c#  
int GetEnclosingClass(  
   out IDebugClassField ppClassField  
);  
```  
  
#### Paramètres  
 `ppClassField`  
 \[out\]  Retourne un objet d' [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) représentant la classe englobante.  Retourne une valeur NULL s'il n'y a aucune classe englobante.  
  
## Valeur de retour  
 En cas de réussite, retourne S\_OK ; sinon, retourne un code d'erreur.  
  
## Notes  
 Si la classe représentée par cet objet d' [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) est une classe imbriquée, le paramètre d' `ppClassField` retourne un objet d' `IDebugClassField` représentant la classe englobante.  Par exemple, si cette définition de classe :  
  
```  
class RootClass {  
   class NestedClass { }  
};  
```  
  
 Appelant la méthode d' `GetEnclosingClass` sur l'objet d' `IDebugClassField` qui représente la classe d' `NestedClass` retourne un objet d' `IDebugClassField` qui représente la classe `RootClass`.  
  
## Voir aussi  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)