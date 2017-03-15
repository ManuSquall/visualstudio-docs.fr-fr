---
title: "IDebugProgram2::WriteDump | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgram2::WriteDump"
helpviewer_keywords: 
  - "IDebugProgram2::WriteDump"
ms.assetid: 375afb8c-882d-44db-bfa7-e2c9eb555122
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugProgram2::WriteDump
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

écrit un dump à un fichier.  
  
## Syntaxe  
  
```cpp#  
HRESULT WriteDump(   
   DUMPTYPE  DumpType,  
   LPCOLESTR pszDumpUrl  
);  
```  
  
```c#  
int WriteDump(   
   enum_DUMPTYPE  DumpType,  
   string         pszDumpUrl  
);  
```  
  
#### Paramètres  
 `DumpType`  
 \[in\]  une valeur de l'énumération de [DUMPTYPE](../../../extensibility/debugger/reference/dumptype.md) qui spécifie le type de dump, par exemple, court ou longtemps.  
  
 `pszDumpUrl`  
 \[in\]  L'URL pour écrire le dump à.  En général, cela se présente sous la forme d' `file://c : le chemin d'accès \ \ filename.ext`, mais peut être une URL valide.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Un dump de programme inclut généralement le frame de pile actuel, la pile elle\-même, une liste des threads exécutant dans le programme, et éventuellement toute mémoire que le programme possède.  
  
## Voir aussi  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)