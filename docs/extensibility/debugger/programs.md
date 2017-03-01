---
title: Programmes | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], programs
- programs, debugging
ms.assetid: e1f955d8-95da-493b-837e-e97741a26d7e
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 982d966208433905115e76a36d358c656005e3d3
ms.lasthandoff: 02/22/2017

---
# <a name="programs"></a>Programs
En termes de l’architecture du débogueur, une **programme**:  
  
-   Est un conteneur pour un ensemble de threads et un ensemble de modules. Un programme n’a aucun analogie unique dans le système d’exploitation Windows.  
  
     Un programme est un genre de sous-processus. Par exemple, lorsque vous déboguez un site Web, un script peut être considéré comme un programme. Pendant un script s’exécute dans le processus du moteur de script, indépendamment des autres scripts, il a également son propre ensemble de threads. Un moteur de débogage (DE) joint à un programme et pas à un processus ou un thread.  
  
-   Peut identifier lui-même et le processus est en cours d’exécution ; elle peut être attaché pour détacher et décrire le DE qui l’a créé, le cas échéant. Un programme peut exécuter, arrêter, continuer et se terminer.  
  
-   Peut énumérer tous ses threads. Un programme peut également fournir son propre flux de code machine et peut énumérer tous les contextes de code d’une position de document donné.  
  
-   Est représenté par une [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) interface créée avant que le programme est attaché, ou dans le cadre du processus d’attachement, selon l’implémentation. Lorsqu’un port énumère les programmes d’un processus, chaque programme est créé conformément à un correspondant [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) interface est passée comme argument à [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). Alors que les moteurs de débogage également créer `IDebugProgram2` interfaces pour représenter, ces programmes ne sont pas créés conformément à un nœud du programme. Le `IDebugProgramNode2` créés par un des interfaces sont utilisées pour le débogage réel, tandis que ceux créés par un port sont uniquement utilisées pour détecter les programmes qui sont exécutent dans un processus.  
  
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
