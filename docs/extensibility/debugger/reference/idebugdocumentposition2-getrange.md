---
title: "IDebugDocumentPosition2::GetRange | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDocumentPosition2::GetRange"
helpviewer_keywords: 
  - "IDebugDocumentPosition2::GetRange"
ms.assetid: 91a06ee7-253a-4215-be22-04bf57305aa8
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugDocumentPosition2::GetRange
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

obtient la plage pour cette position de document.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetRange(   
   TEXT_POSITION* pBegPosition,  
   TEXT_POSITION* pEndPosition  
);  
```  
  
```c#  
int GetRange(   
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
 La plage spécifiée en position de le document pour un point d'arrêt d'emplacement est utilisée par le moteur de \(DE\) débogage pour rechercher vers l'avant une instruction qui offre réellement code.  Considérons par exemple le code suivant :  
  
```  
Line 5: // comment  
Line 6: x = 1;  
```  
  
 La ligne 5 ne fournit aucun code au programme en cours de débogage.  Si le débogueur qui définit le point d'arrêt sur la ligne 5 souhaite le De pour rechercher vers l'avant une certaine quantité de la première ligne qui fournit le code, le débogueur assigne une plage qui comprend des lignes supplémentaires candidat où un point d'arrêt peut être correctement placé.  Le De rechercherait ensuite en accédant à avant lignes jusqu'à ce qu'il a trouvé une ligne qui peut accepter un point d'arrêt.  
  
## Voir aussi  
 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)   
 [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md)