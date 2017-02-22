---
title: "IDebugProgramPublisher2::PublishProgramNode | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramPublisher2::PublishProgramNode"
helpviewer_keywords: 
  - "IDebugProgramPublisher2::PublishProgramNode"
ms.assetid: d4b72e04-f726-46cf-8e56-5203ff205b12
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugProgramPublisher2::PublishProgramNode
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Rend un nœud de programme disponible pour une utilisation par les moteurs \(DEs\) de débogage et du gestionnaire de débogage de \(SDM\) session.  
  
## Syntaxe  
  
```cpp  
HRESULT PublishProgramNode(  
   IDebugProgramNode2 *pProgramNode  
);  
```  
  
```c#  
int PublishProgramNode(  
   IDebugProgramNode2 pProgramNode  
);  
```  
  
#### Paramètres  
 `pProgramNode`  
 \[in\]  Un objet d' [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) qui représente le nœud de programme pour rendre disponible.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Cette méthode permet des programmes à interroger des informations avant de les sélectionner et lancer pour le débogage.  
  
 Pour supprimer un nœud de programme de disponibilité, appelez la méthode d' [UnpublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogramnode.md) .  
  
## Voir aussi  
 [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [UnpublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogramnode.md)