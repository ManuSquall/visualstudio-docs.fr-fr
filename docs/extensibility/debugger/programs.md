---
title: Programmes | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], programs
- programs, debugging
ms.assetid: e1f955d8-95da-493b-837e-e97741a26d7e
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e34dbcf9c19b5e8e7a16d2f409159597670cb8cc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="programs"></a>Programs
En termes de l’architecture du débogueur, une **programme**:  
  
-   Est un conteneur pour un ensemble de threads et un ensemble de modules. Un programme n’a aucune analogie unique dans le système d’exploitation Windows.  
  
     Un programme est une sorte de sous-processus. Par exemple, lorsque vous déboguez un site Web, un script peut être considéré comme un programme. Même si un script s’exécute dans le processus du moteur de script, indépendamment des autres scripts, il possède aussi son propre ensemble de threads. Un moteur de débogage (DE) joint à un programme et non à un processus ou un thread.  
  
-   Peut identifier lui-même et le processus est en cours d’exécution, elle puisse être joint à être détaché et décrivent le DE qui l’a créé, le cas échéant. Un programme peut s’exécuter, arrêter, continuer et se terminer.  
  
-   Peut énumérer tous les threads. Un programme peut également fournir son propre flux de code machine et peut énumérer tous les contextes de code d’une position de document donné.  
  
-   Est représenté par un [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) interface, créé avant que le programme est attaché, ou dans le cadre du processus d’attachement, selon l’implémentation. Lorsqu’un port énumère les programmes d’un processus, chaque programme est créé conformément à correspondante [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) interface est passée comme argument à [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). Alors que les moteurs de débogage également créer `IDebugProgram2` interfaces pour représenter, ces programmes ne sont pas créés en fonction d’un nœud de programme. Le `IDebugProgramNode2` interfaces créés par un DE sont utilisés pour le débogage réel, tandis que ceux créés par un port sont utilisées uniquement pour la découverte les programmes qui sont exécutent dans un processus.  
  
## <a name="see-also"></a>Voir aussi  
 [Processus](../../extensibility/debugger/processes.md)   
 [Nœuds de programme](../../extensibility/debugger/program-nodes.md)   
 [Modules](../../extensibility/debugger/modules.md)   
 [Concepts du débogueur](../../extensibility/debugger/debugger-concepts.md)   
 [Moteur de débogage](../../extensibility/debugger/debug-engine.md)   
 [Position du document](../../extensibility/debugger/document-position.md)   
 [Contexte de code](../../extensibility/debugger/code-context.md)   
 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)