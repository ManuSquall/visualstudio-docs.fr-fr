---
title: "IDebugProgramProvider2::SetLocale | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramProvider2::SetLocale"
helpviewer_keywords: 
  - "IDebugProgramProvider2::SetLocale"
ms.assetid: b41d20a7-ba40-4c42-a450-16f413d6a04f
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugProgramProvider2::SetLocale
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Génère des paramètres régionaux à utiliser pour toutes les ressources spécifiques aux paramètres régionaux.  
  
## Syntaxe  
  
```cpp  
HRESULT SetLocale(  
   WORD wLangID  
);  
```  
  
```c#  
int SetLocale(  
   ushort wLangID  
);  
```  
  
#### Paramètres  
 `wLangID`  
 \[in\]  ID de langue à générer.  par exemple, 1033 pour l'anglais.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Voir aussi  
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)