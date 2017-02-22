---
title: "IDebugAlias::GetICorDebugValue | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugAlias::GetICorDebugValue"
helpviewer_keywords: 
  - "IDebugAlias::GetICorDebugValue (méthode)"
ms.assetid: b9eb39ee-84af-4ace-9cfe-236b3d48aff5
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugAlias::GetICorDebugValue
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Récupère une interface en code managé qui représente la valeur associée à cet alias.  
  
## Syntaxe  
  
```cpp  
HRESULT GetICorDebugValue(  
   IUnknown** ppUnk  
);  
```  
  
```c#  
int GetICorDebugValue(  
   out object ppUnk  
);  
```  
  
#### Paramètres  
 `ppUnk`  
 \[out\] `IUnknown` interface qui représente la valeur associée à cet alias. Cette interface peut être interrogée pour le `ICorDebugValue` interface.  
  
## Valeur de retour  
 En cas de réussite, retourne S\_OK ; Sinon, retourne un code d'erreur.  
  
## Notes  
 Cette méthode s'applique uniquement aux valeurs gérés \(les `ICorDebugValue` une interface n'est disponible dans le [!INCLUDE[dnprdnshort](../../../code-quality/includes/dnprdnshort_md.md)] et est défini dans le [!INCLUDE[dnprdnshort](../../../code-quality/includes/dnprdnshort_md.md)] SDK dans le fichier cordebug.idl\).  
  
## Voir aussi  
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)