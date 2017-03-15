---
title: "IDebugProgramPublisher2::UnpublishProgramNode | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramPublisher2::UnpublishProgramNode"
helpviewer_keywords: 
  - "IDebugProgramPublisher2::UnpublishProgramNode"
ms.assetid: 57c7e6e1-b84e-4e14-ad83-cbbb64e2f526
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugProgramPublisher2::UnpublishProgramNode
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Supprime un nœud spécifié du programme de la disponibilité les moteurs de \(DEs\) débogage et au gestionnaire de débogage de session \(SDM\).  
  
## Syntaxe  
  
```cpp  
HRESULT UnpublishProgramNode(  
   IDebugProgramNode2* pProgramNode  
);  
```  
  
```c#  
int UnpublishProgramNode(  
   IDebugProgramNode2 pProgramNode  
);  
```  
  
#### Paramètres  
 `pProgramNode`  
 \[in\]  Un objet d' [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) représentant le nœud de programme en cours de suppression.  
  
## Valeur de retour  
 En cas de réussite, retourne `S_OK`; sinon, retourne un code d'erreur.  
  
## Notes  
 Une fois que supprimé, le nœud de votre programme n'est plus disponible pour interroger pour obtenir des informations de programme.  
  
 Pour rendre un nœud de programme disponible, appelez la méthode d' [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md) .  
  
## Voir aussi  
 [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)