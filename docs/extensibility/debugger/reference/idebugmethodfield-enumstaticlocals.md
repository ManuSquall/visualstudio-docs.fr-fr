---
title: "IDebugMethodField::EnumStaticLocals | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugMethodField::EnumStaticLocals"
helpviewer_keywords: 
  - "IDebugMethodField::EnumStaticLocals (méthode)"
ms.assetid: e0c522c4-f759-4c32-ae87-7abcb573e77d
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugMethodField::EnumStaticLocals
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Crée un énumérateur pour les variables locales statiques de la méthode.  
  
## Syntaxe  
  
```cpp#  
HRESULT EnumStaticLocals(   
   IEnumDebugFields** ppLocals  
);  
```  
  
```c#  
int EnumStaticLocals(  
   out IEnumDebugFields ppLocals  
);  
```  
  
#### Paramètres  
 `ppLocals`  
 \[out\]  Retourne un objet d' [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) représentant la liste de variables locales statiques.  Retourne une valeur NULL s'il n'y a aucun locale statique.  
  
## Valeur de retour  
 En cas de réussite, retourne S\_OK ou retourne S\_FALSE s'il n'y a aucun locale statique.  Sinon, retourne un code d'erreur.  
  
## Notes  
 Chaque élément est un objet d' [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) représentant différents types de comptes locaux statiques.  Appelez la méthode d' [GetKind](../Topic/IDebugField::GetKind.md) sur chaque objet pour déterminer exactement ce genre représentent les données locales statiques l'objet.  
  
## Voir aussi  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)