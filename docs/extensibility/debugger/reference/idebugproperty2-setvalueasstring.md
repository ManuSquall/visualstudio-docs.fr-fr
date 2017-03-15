---
title: "IDebugProperty2::SetValueAsString | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProperty2::SetValueAsString"
helpviewer_keywords: 
  - "IDebugProperty2::SetValueAsString"
ms.assetid: 9e6a5054-41b7-4223-b509-b93689d366a5
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProperty2::SetValueAsString
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

définit la valeur d'une propriété d'une chaîne donnée.  
  
## Syntaxe  
  
```cpp#  
HRESULT SetValueAsString (   
   LPCOLESTR pszValue,  
   UINT      nRadix,  
   DWORD     dwTimeout  
);  
```  
  
```c#  
int SetValueAsString (   
   string pszValue,  
   uint   nRadix,  
   uint   dwTimeout  
);  
```  
  
#### Paramètres  
 `pszValue`  
 \[in\]  Chaîne contenant la valeur à définir.  
  
 `nRadix`  
 \[in\]  Une base à utiliser lors de l'interprétation des informations numériques.  Cela peut être composé de 0 à tenter de déterminer la base automatiquement.  
  
 `dwTimeout`  
 \[in\]  Spécifie le temps maximum, en millisecondes, d'attendre avant le retour de cette méthode.  Utilisation `INFINITE` d'attente dure indéfiniment.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon retourne un code d'erreur.  Le tableau suivant montre les autres valeurs possibles.  
  
|Valeur|Description|  
|------------|-----------------|  
|`E_SETVALUE_VALUE_CANNOT_BE_SET`|La chaîne ne peut pas être convertie en une valeur de propriété, ou la valeur de propriété ne peut pas être définie.|  
|`E_SETVALUE_VALUE_IS_READONLY`|La propriété est en lecture seule.|  
  
## Voir aussi  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)