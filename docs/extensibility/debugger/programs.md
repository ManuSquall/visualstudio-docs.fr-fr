---
title: Programmes | Microsoft Docs
description: Cet article décrit la définition et le rôle d’un programme dans l’architecture du débogueur dans Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], programs
- programs, debugging
ms.assetid: e1f955d8-95da-493b-837e-e97741a26d7e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5205dba6cddf104d0cb05f01acbc43f6927acaaf
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948424"
---
# <a name="programs"></a>Programmes
Dans l’architecture du débogueur, un *programme*:

- Est un conteneur pour un ensemble de threads et un ensemble de modules. Un programme n’a pas d’analogie unique dans le système d’exploitation Windows.

     Un programme est un type de sous-processus. Par exemple, lorsque vous déboguez un site Web, un script peut être considéré comme un programme. Tandis qu’un script s’exécute dans le processus du moteur de script, indépendamment des autres scripts, il possède également son propre ensemble de threads. Un moteur DE débogage (DE) est attaché à un programme, et non à un processus ou à un thread.

- Peut s’identifier et le processus dans lequel il s’exécute. Un programme peut être attaché à, être détaché de et décrire le DE qui l’a créé, le cas échéant. Un programme peut également s’exécuter, s’arrêter, continuer et être arrêté.

- Peut énumérer tous ses threads. Un programme peut également fournir son propre flux de code de désassemblage et peut énumérer tous les contextes de code d’une position de document donnée.

- Est représenté par une interface [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) , créée avant l’attachement du programme ou dans le cadre du processus d’attachement, en fonction de l’implémentation. Lorsqu’un port énumère les programmes d’un processus, chaque programme est créé conformément à une interface [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) correspondante transmise en tant qu’argument à [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). Alors que les moteurs de débogage créent également des `IDebugProgram2` interfaces pour représenter des programmes, ces programmes ne sont pas créés conformément à un nœud de programme. Les `IDebugProgramNode2` interfaces créées par un de sont utilisées pour le débogage réel, tandis que celles créées par un port sont utilisées uniquement pour détecter les programmes en cours d’exécution dans un processus.

## <a name="see-also"></a>Voir aussi
- [Processus](../../extensibility/debugger/processes.md)
- [Nœuds de programme](../../extensibility/debugger/program-nodes.md)
- [Modules](../../extensibility/debugger/modules.md)
- [Concepts du débogueur](../../extensibility/debugger/debugger-concepts.md)
- [Moteur de débogage](../../extensibility/debugger/debug-engine.md)
- [Position du document](../../extensibility/debugger/document-position.md)
- [Contexte de code](../../extensibility/debugger/code-context.md)
- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)
- [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)
