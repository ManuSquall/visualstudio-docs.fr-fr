---
title: "IDebugCodeContext2::GetLanguageInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCodeContext2::GetLanguageInfo"
helpviewer_keywords: 
  - "IDebugCodeContext2::GetLanguageInfo"
ms.assetid: 03002ef1-9fe6-44b6-b23b-ef7b86b2b21b
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugCodeContext2::GetLanguageInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtient les informations de langage dans ce contexte de code.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetLanguageInfo(   
   BSTR* pbstrLanguage,  
   GUID* pguidLanguage  
);  
```  
  
```c#  
int GetLanguageInfo(   
   ref string pbstrLanguage,  
   ref Guid pguidLanguage  
);  
```  
  
#### Paramètres  
 `pbstrLanguage`  
 \[in, out\]  Retourne une chaîne contenant le nom du langage, tel que « C\+\+ ».  
  
 `pguidLanguage`  
 \[in, out\]  Retourne le GUID pour le langage du contexte de code, par exemple, `guidCPPLang`.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Au moins l'un des paramètres doit retourner une valeur non null.  
  
## Voir aussi  
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)