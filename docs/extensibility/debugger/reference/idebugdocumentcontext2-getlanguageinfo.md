---
title: "IDebugDocumentContext2::GetLanguageInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDocumentContext2::GetLanguageInfo"
helpviewer_keywords: 
  - "IDebugDocumentContext2::GetLanguageInfo"
ms.assetid: 6a212ee5-414c-4eb5-ab11-19db1786943d
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugDocumentContext2::GetLanguageInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtient la langue associé à ce contexte de document.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetLanguageInfo(   
   BSTR* pbstrLanguage,  
   GUID* pguidLanguage  
);  
```  
  
```c#  
int GetLanguageInfo(   
   out string pbstrLanguage,  
   out Guid   pguidLanguage  
);  
```  
  
#### Paramètres  
 `pbstrLanguage`  
 \[out\]  Retourne le nom de la langue qui implémente le code à ce contexte de document.  
  
 `pguidLanguage`  
 \[out\]  Retourne le GUID du langage qui implémente le code à ce contexte de document.  Par exemple, `guidVBScriptLang` ou `guidCPPLang`.  Ce GUID n'est pas limitée aux langages fournis par [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)].  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Exemple  
 L'exemple de code suivant montre comment appliquer cette méthode d'un objet simple d' `CDebugContext` qui expose l'interface d' [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) .  
  
```cpp#  
HRESULT CDebugContext::GetLanguageInfo(BSTR* pbstrLanguage, GUID* pguidLanguage)    
{    
   HRESULT hr;    
  
   // Check for a valid language argument pointers.    
   if (pbstrLanguage && pguidLanguage)    
   {    
      *pguidLanguage = GUID_NULL;    
      *pbstrLanguage = SysAllocString(L"Batch File");    
      if (*pbstrLanguage)    
      {    
         *pguidLanguage = guidBatLang;    
         hr = S_OK;    
      }    
      else    
      {    
         hr = E_OUTOFMEMORY;    
      }    
   }    
   else    
   {    
      hr = E_INVALIDARG;    
   }    
  
   return hr;    
}    
```  
  
## Voir aussi  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)