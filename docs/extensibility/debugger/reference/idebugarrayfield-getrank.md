---
title: "IDebugArrayField::GetRank | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugArrayField::GetRank"
helpviewer_keywords: 
  - "IDebugArrayField::GetRank (méthode)"
ms.assetid: 2364b876-5be1-4bab-9b8f-3b6121da35c6
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugArrayField::GetRank
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtient le rang ou le nombre de dimensions du tableau.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetRank(   
   DWORD* pdwRank  
);  
```  
  
```c#  
int GetRank(  
   out uint pdwRank  
);  
```  
  
#### Paramètres  
 `pdwRank`  
 \[out\]  Retourne le classement.  
  
## Valeur de retour  
 En cas de réussite, retourne S\_OK ; sinon, retourne un code d'erreur.  
  
## Notes  
 Le rang d'un tableau correspond au nombre de dimensions.  En C\+\+ et c\#, les tableaux multidimensionnels sont véritablement des tableaux de tableaux et peut donc être considérés comme un tableau unidimensionnel \(et la méthode d' `GetRank` retourne toujours 1\).  Dans [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)], en revanche, les tableaux multidimensionnels sont gérés différemment et le rang d'une telle tableau reflète le nombre de dimensions \(et de la méthode d' `GetRank` retourne toujours le nombre de dimensions\).  
  
## Voir aussi  
 [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)