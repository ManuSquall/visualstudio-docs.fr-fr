---
title: "IDebugDocumentContext2::GetStatementRange | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDocumentContext2::GetStatementRange"
helpviewer_keywords: 
  - "IDebugDocumentContext2::GetStatementRange"
ms.assetid: bc94851a-0ec4-47ea-99c7-0a585e54e726
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugDocumentContext2::GetStatementRange
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtient la plage d'instructions de fichier du contexte de document.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetStatementRange(   
   TEXT_POSITION* pBegPosition,  
   TEXT_POSITION* pEndPosition  
);  
```  
  
```c#  
int GetStatementRange(   
   TEXT_POSITION[] pBegPosition,  
   TEXT_POSITION[] pEndPosition  
);  
```  
  
#### Paramètres  
 `pBegPosition`  
 \[in, out\]  Une structure de [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md) qui est terminée avec la position de départ.  Affectez à cet argument à une valeur NULL si ces informations ne sont pas nécessaires.  
  
 `pEndPosition`  
 \[in, out\]  Une structure de [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md) qui est terminée avec la position de fin.  Affectez à cet argument à une valeur NULL si ces informations ne sont pas nécessaires.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Une plage d'instructions est la plage des lignes qui a fourni le code auquel ce contexte de document fait référence.  
  
 Pour obtenir la plage de code source \(commentaires\) dans ce contexte de document, appelez la méthode d' [GetSourceRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getsourcerange.md) .  
  
## Exemple  
 L'exemple suivant indique comment appliquer cette méthode d'un objet simple d' `CDebugContext` qui expose l'interface d' [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) .  Cet exemple complète la position de fin uniquement si la position de début n'est pas une valeur NULL.  
  
```cpp#  
HRESULT CDebugContext::GetStatementRange(TEXT_POSITION* pBegPosition,  
                                         TEXT_POSITION* pEndPosition)    
{    
   HRESULT hr;    
  
   // Check for a valid beginning position argument pointer.    
   if (pBegPosition)    
   {    
      // Copy the member TEXT_POSITION into the local pBegPosition.    
      memcpy(pBegPosition, &m_pos, sizeof (TEXT_POSITION));    
  
      // Check for a valid ending position argument pointer.   
     if (pEndPosition)    
      {    
         // Copy the member TEXT_POSITION into the local pEndPosition.    
         memcpy(pEndPosition, &m_pos, sizeof (TEXT_POSITION));    
      }    
      hr = S_OK;    
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
 [GetSourceRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getsourcerange.md)   
 [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md)