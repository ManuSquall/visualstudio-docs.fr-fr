---
title: "IDebugProgramEngines2::EnumPossibleEngines | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramEngines2::EnumPossibleEngines"
helpviewer_keywords: 
  - "IDebugProgramEngines2::EnumPossibleEngines"
ms.assetid: 993d70a4-f6a5-4e47-a603-0b162b9fde00
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProgramEngines2::EnumPossibleEngines
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Retourne le GUID pour tous les moteurs de débogage possibles \(DE\) qui peuvent mettre ce programme.  
  
## Syntaxe  
  
```cpp#  
HRESULT EnumPossibleEngines(   
   DWORD  celtBuffer,  
   GUID*  rgguidEngines,  
   DWORD* pceltEngines  
);  
```  
  
```c#  
int EnumPossibleEngines(   
   uint      celtBuffer,  
   GUID[]    rgguidEngines,  
   ref DWORD pceltEngines  
);  
```  
  
#### Paramètres  
 `celtBuffer`  
 \[in\]  Le nombre de GUID à retourner.  Cela spécifie également la taille maximale du tableau d' `rgguidEngines` .  
  
 `rgguidEngines`  
 \[in, out\]  Un tableau de GUID à accomplir.  
  
 `pceltEngines`  
 \[out\]  Retourne le nombre réel de GUID retournés.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  Retourne \[C\+\+\] `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` ou \[c\#\] 0x8007007A si la mémoire tampon n'est pas suffisamment grande.  
  
## Notes  
 Pour déterminer le nombre de moteurs sont présents, appellent cette méthode une fois avec le jeu de paramètres d' `celtBuffer` à 0 et le jeu de paramètres d' `rgguidEngines` à une valeur NULL.  Retourne `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` \(0x8007007A pour c\#\), et le paramètre d' `pceltEngines` retourne la taille nécessaire de la mémoire tampon.  
  
## Voir aussi  
 [IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)