---
title: "IDebugProcessEx2::AddImplicitProgramNodes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcessEx2::AddImplicitProgramNodes"
helpviewer_keywords: 
  - "IDebugProcessEx2::AddImplicitProgramNodes (méthode)"
ms.assetid: 8b491b00-f9e7-45b3-9115-fe58c3464289
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProcessEx2::AddImplicitProgramNodes
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Cette méthode ajoute un nœud de programme pour chaque moteur de débogage \(DE\) spécifié.  
  
## Syntaxe  
  
```cpp#  
HRESULT AddImplicitProgramNodes(  
   REFGUID guidLaunchingEngine,  
   GUID*   rgguidSpecificEngines,  
   DWORD   celtSpecificEngines  
);  
```  
  
```c#  
int AddImplicitProgramNodes(  
   ref Guid guidLaunchingEngine,  
   Guid[]   rgguidSpecificEngines,  
   uint     celtSpecificEngines  
);  
```  
  
#### Paramètres  
 `guidLaunchingEngine`  
 \[in\]  `GUID` d'un De devant être utilisé pour exécuter les programmes \(et est supposé pour ajouter ses propres nœuds de programme\).  
  
 `rgguidSpecificEngines`  
 \[in\]  Tableau d' `GUID`s de les pour lequel des nœuds de programme seront ajoutés.  
  
 `celtSpecificEngines`  
 \[in\]  Le numéro d' `GUID`s dans le tableau d' `rgguidSpecificEngines` .  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 [Nœuds de programme](../../../extensibility/debugger/program-nodes.md) sera ajouté pour chaque De répertorié dans `rgguidSpecificEngines`\- exclusion du moteur lancement \(comme indiqué dans `guidLaunchingEngine`\), il est supposé que qui ajoute son propre nœud de programme lorsqu'il exécute un programme.  
  
## Voir aussi  
 [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)   
 [Nœuds de programme](../../../extensibility/debugger/program-nodes.md)