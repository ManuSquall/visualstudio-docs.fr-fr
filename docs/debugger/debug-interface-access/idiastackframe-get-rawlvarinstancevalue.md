---
title: "IDiaStackFrame::get_rawLVarInstanceValue | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaStackFrame::get_rawLVarInstanceValue (méthode)"
ms.assetid: ce526259-85a6-475b-9274-0b3a21d95db2
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IDiaStackFrame::get_rawLVarInstanceValue
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Cette méthode récupère la valeur de la variable locale spécifiée en tant qu'octets bruts.  
  
## Syntaxe  
  
```cpp#  
HRESULT get_rawLVarInstanceValue(  
   IDiaLVarInstance* pInstance,  
   DWORD             cbDataMax,  
   DWORD*            pcbData,  
   BYTE*             pbData  
);  
```  
  
#### Paramètres  
 `pInstance`  
 \[in\]  un objet d' `IDiaLVarInstance` représentant une instance de variable locale pour obtenir la valeur pour.  
  
 `cbDataMax`  
 \[in\]  Le nombre maximal d'octets en mémoire tampon indiquée par `pbData`.  Cela peut être un maximum de 8 octets \(`sizeof(ULONGLONG)`\).  
  
 `pcbData`  
 \[out\]  Retourne le nombre d'octets réel stockés en mémoire tampon.  
  
 `pbData`  
 \[out\]  Une mémoire tampon à remplir avec des données.  Il ne peut pas s'agir de la valeur `NULL`.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)