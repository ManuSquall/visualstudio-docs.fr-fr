---
title: Nœuds du programme (en anglais seulement) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- program nodes, debugging context
- debugging [Debugging SDK], program nodes
- program nodes, adding
- program nodes, superceding
ms.assetid: 1c5a5c13-c14d-42c3-af11-4c63f1032c8d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2943f74c7316495be93c2f5c20998ffa685f5d01
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738217"
---
# <a name="program-nodes"></a>Nœuds de programme
Dans l’architecture de débbugger, un *nœud de programme*:

- Est une description légère d’un programme.

- Peut s’identifier et le processus dans lequel il est en cours d’exécution. Un nœud de programme peut être attaché à, être détaché de, et décrire le moteur de débogé (DE) qui l’a créé, le cas échéant.

- Est représenté par une interface [IDebugProgramNode2,](../../extensibility/debugger/reference/idebugprogramnode2.md) généralement créée par un DE ou un port. Les nœuds du programme sont ajoutés à un port en appelant [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). Lorsqu’un nœud de programme est ajouté à un port, il est ajouté au processus contenant le programme que représente ce nœud de programme.

  Quelque temps après le début d’une séance de débogé, selon la mise en œuvre du paquet de débog, les nœuds du programme sont utilisés pour créer des programmes correspondants. Lorsqu’un processus est demandé pour ses programmes, les programmes sont énumérés, un pour chaque nœud de programme.

  Avant qu’un programme ne soit rattaché, l’IDE n’a besoin que d’une description légère du programme. Ces renseignements peuvent être obtenus à partir du nœud du programme. Une fois le programme rattaché, l’IDE affiche des informations plus détaillées, telles qu’une liste de tous les threads en cours d’exécution dans le programme. Cette information provient du programme lui-même.

## <a name="see-also"></a>Voir aussi
- [Programmes](../../extensibility/debugger/programs.md)
- [Processus](../../extensibility/debugger/processes.md)
- [Moteur Debug](../../extensibility/debugger/debug-engine.md)
- [Concepts Debugger](../../extensibility/debugger/debugger-concepts.md)
- [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)
- [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)
