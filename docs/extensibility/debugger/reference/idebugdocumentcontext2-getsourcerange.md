---
title: "IDebugDocumentContext2::GetSourceRange | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDocumentContext2::GetSourceRange"
helpviewer_keywords: 
  - "IDebugDocumentContext2::GetSourceRange"
ms.assetid: 5903c75e-5390-4d13-9314-1ee276255313
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugDocumentContext2::GetSourceRange
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

obtient la plage de code source de ce contexte de document.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetSourceRange(   
   TEXT_POSITION* pBegPosition,  
   TEXT_POSITION* pEndPosition  
);  
```  
  
```c#  
int GetSourceRange(   
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
 Une plage source est la plage complète de code source, de l'instruction en cours de nouveau à juste après l'instruction précédente que le code fourni.  La plage source est généralement utilisée pour associer des instructions de source, y compris les commentaires, au code de la fenêtre Code machine.  
  
 Pour obtenir la plage uniquement pour les instructions de code contenues dans ce contexte de document, appelez la méthode d' [GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md) .  
  
## Voir aussi  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)   
 [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md)