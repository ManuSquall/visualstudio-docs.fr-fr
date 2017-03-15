---
title: "IDebugEnumField::GetValueFromString | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEnumField::GetValueFromString"
helpviewer_keywords: 
  - "IDebugEnumField::GetValueFromString (méthode)"
ms.assetid: 1ef8ac5e-a3e0-4078-b876-7f5615aedcbb
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# IDebugEnumField::GetValueFromString
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette méthode retourne la valeur associée au nom d'une constante d'énumération.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetValueFromString(  
   LPCOLESTR  pszValue,  
   ULONGLONG* pvalue  
);  
```  
  
```c#  
int GetValueFromString(  
   string    pszValue,  
   out ulong pValue  
);  
```  
  
#### Paramètres  
 `pszValue`  
 \[in\]  Chaîne spécifiant le nom pour lequel obtenir la valeur.  Notez que pour C\+\+, cela est une chaîne à caractères larges.  
  
 `pValue`  
 \[out\]  Retourne la valeur numérique associée.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne `S_FALSE`, si le nom n'est pas partie de l'énumération, ou un code d'erreur.  
  
## Notes  
 Cette méthode respecte la casse.  Si une recherche respectant la casse est nécessaire \(par exemple, dans un langage tel que Visual Basic où les noms ne tiennent pas compte de la casse\), utilisez [GetValueFromStringCaseInsensitive](../Topic/IDebugEnumField::GetValueFromStringCaseInsensitive.md).  
  
## Voir aussi  
 [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)   
 [GetValueFromStringCaseInsensitive](../Topic/IDebugEnumField::GetValueFromStringCaseInsensitive.md)