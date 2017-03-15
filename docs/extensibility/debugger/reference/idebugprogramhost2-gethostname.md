---
title: "IDebugProgramHost2::GetHostName | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramHost2::GetHostName"
helpviewer_keywords: 
  - "IDebugProgramHost2::GetHostName"
ms.assetid: 48bbb089-e59a-471a-9965-24b42a8dabf3
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProgramHost2::GetHostName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

obtient le titre, le nom convivial, ou le nom de fichier du processus d'hébergement de ce programme.  
  
## Syntaxe  
  
```cpp#  
HRESULT GetHostName(   
   DWORD dwType,  
   BSTR* pbstrHostName  
);  
```  
  
```c#  
int GetHostName(   
   uint dwType,  
   out string pbstrHostName  
);  
```  
  
#### Paramètres  
 `dwType`  
 \[in\]  une valeur de l'énumération de [GETHOSTNAME\_TYPE](../../../extensibility/debugger/reference/gethostname-type.md) .  
  
 `pbstrHostName`  
 \[out\]  Retourne le nom demandé du processus d'hébergement.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Dans une implémentation de cette méthode, le paramètre d' `dwType` est ignoré et un nom convivial de l'ordinateur \- hôte est retourné.  Une autre implémentation possible consiste à passer le paramètre d' `dwType` à un appel à la méthode d' [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md) pour obtenir le nom.  
  
## Voir aussi  
 [IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)   
 [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)