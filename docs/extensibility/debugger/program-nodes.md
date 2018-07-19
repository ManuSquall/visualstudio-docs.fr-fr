---
title: Programmer des nœuds | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- program nodes, debugging context
- debugging [Debugging SDK], program nodes
- program nodes, adding
- program nodes, superceding
ms.assetid: 1c5a5c13-c14d-42c3-af11-4c63f1032c8d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 50ab93c31a340bf8a2f4e2deb5f202707d7826b8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31099601"
---
# <a name="program-nodes"></a>Nœuds de programme
En termes de l’architecture du débogueur, une **nœud du programme**:  
  
-   Est une description léger d’un programme.  
  
-   Peut identifier lui-même et le processus est en cours d’exécution, elle puisse être joint à être détaché et décrivent le moteur de débogage (DE) qui l’a créé, le cas échéant.  
  
-   Est représenté par un [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) interface, généralement créé par un port ou DE. Les nœuds de programme sont ajoutées à un port en appelant [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). Lorsqu’un nœud de programme est ajouté à un port, il est ajouté au processus contenant le programme qui représente ce nœud du programme.  
  
 Un certain temps après qu’une session de débogage est démarrée, en fonction de l’implémentation du package de débogage, les nœuds de programme sont utilisés pour créer des programmes correspondants. Lorsqu’un processus est interrogé sur ses programmes, les programmes sont énumérées, une pour chaque nœud du programme.  
  
 Avant d’un programme est attaché à, l’IDE doit seulement une légère description du programme. Ces informations peuvent être obtenues à partir du nœud du programme. Une fois que le programme est attaché à, l’IDE doit afficher des informations plus détaillées, telles qu’une liste de tous les threads en cours d’exécution dans le programme. Ces informations sont obtenues à partir du programme lui-même.  
  
## <a name="see-also"></a>Voir aussi  
 [Programmes](../../extensibility/debugger/programs.md)   
 [Processus](../../extensibility/debugger/processes.md)   
 [Moteur de débogage](../../extensibility/debugger/debug-engine.md)   
 [Concepts du débogueur](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)