---
title: Nœuds de programme | Microsoft Docs
description: Cet article décrit la définition et le rôle d’un nœud de programme dans l’architecture du débogueur dans Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- program nodes, debugging context
- debugging [Debugging SDK], program nodes
- program nodes, adding
- program nodes, superceding
ms.assetid: 1c5a5c13-c14d-42c3-af11-4c63f1032c8d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 4c26fa95a5fedf325591ce517e7c12ecebcd705c
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899080"
---
# <a name="program-nodes"></a>Nœuds de programme
Dans l’architecture du débogueur, un *nœud de programme*:

- Est une description légère d’un programme.

- Peut s’identifier et le processus dans lequel il s’exécute. Un nœud de programme peut être attaché à, être détaché de et décrire le moteur DE débogage (DE) qui l’a créé, le cas échéant.

- Est représenté par une interface [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) , généralement créée par un port de ou. Les nœuds de programme sont ajoutés à un port en appelant [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). Lorsqu’un nœud de programme est ajouté à un port, il est ajouté au processus contenant le programme que ce nœud de programme représente.

  Quelque temps après le démarrage d’une session de débogage, en fonction de l’implémentation du package de débogage, les nœuds de programme sont utilisés pour créer les programmes correspondants. Lorsqu’un processus est interrogé pour ses programmes, les programmes sont énumérés, un pour chaque nœud de programme.

  Avant qu’un programme ne soit attaché à, l’IDE n’a besoin que d’une description légère du programme. Ces informations peuvent être obtenues à partir du nœud du programme. Une fois le programme attaché, l’IDE affiche des informations plus détaillées, telles qu’une liste de tous les threads exécutés dans le programme. Ces informations sont obtenues à partir du programme lui-même.

## <a name="see-also"></a>Voir aussi
- [Programmes](../../extensibility/debugger/programs.md)
- [Processus](../../extensibility/debugger/processes.md)
- [Moteur de débogage](../../extensibility/debugger/debug-engine.md)
- [Concepts du débogueur](../../extensibility/debugger/debugger-concepts.md)
- [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)
- [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)
