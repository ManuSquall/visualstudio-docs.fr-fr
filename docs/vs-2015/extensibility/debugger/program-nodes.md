---
title: Nœuds de programme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- program nodes, debugging context
- debugging [Debugging SDK], program nodes
- program nodes, adding
- program nodes, superceding
ms.assetid: 1c5a5c13-c14d-42c3-af11-4c63f1032c8d
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3a06be4ef0a69ec173f171ba202f1f479448b1ca
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153659"
---
# <a name="program-nodes"></a>Nœuds de programme
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

En termes d’architecture du débogueur, un **nœud de programme**:  
  
- Est une description légère d’un programme.  
  
- Peut s’identifier et le processus dans lequel il s’exécute, et peut être attaché à, être détaché de et décrire le moteur DE débogage (DE) qui l’a créé, le cas échéant.  
  
- Est représenté par une interface [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) , généralement créée par un port de ou. Les nœuds de programme sont ajoutés à un port en appelant [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). Lorsqu’un nœud de programme est ajouté à un port, il est ajouté au processus contenant le programme que ce nœud de programme représente.  
  
  Quelque temps après le démarrage d’une session de débogage, en fonction de l’implémentation du package de débogage, les nœuds de programme sont utilisés pour créer les programmes correspondants. Lorsqu’un processus est interrogé pour ses programmes, les programmes sont énumérés, un pour chaque nœud de programme.  
  
  Avant qu’un programme ne soit attaché à, l’IDE n’a besoin que d’une description légère du programme. Ces informations peuvent être obtenues à partir du nœud du programme. Une fois le programme attaché, l’IDE doit afficher des informations plus détaillées, telles qu’une liste de tous les threads exécutés dans le programme. Ces informations sont obtenues à partir du programme lui-même.  
  
## <a name="see-also"></a>Voir aussi  
 [Installés](../../extensibility/debugger/programs.md)   
 [Processus](../../extensibility/debugger/processes.md)   
 [Moteur de débogage](../../extensibility/debugger/debug-engine.md)   
 [Concepts du débogueur](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)
