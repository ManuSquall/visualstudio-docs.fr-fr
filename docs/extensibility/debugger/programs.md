---
title: Programmes Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], programs
- programs, debugging
ms.assetid: e1f955d8-95da-493b-837e-e97741a26d7e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d3fd1db5add74d2d94467e1f369916feb5f30d4a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738211"
---
# <a name="programs"></a>Programmes
Dans l’architecture débbugger, un *programme*:

- Est un conteneur pour un ensemble de fils et un ensemble de modules. Un programme n’a pas une seule analogie dans le système d’exploitation Windows.

     Un programme est une sorte de sous-traitement. Par exemple, lorsque vous débogagez un site Web, un script peut être considéré comme un programme. Alors qu’un script s’exécute dans le processus du moteur de script, indépendamment d’autres scripts, il a également son propre ensemble de fils. Un moteur de débogé (DE) se fixe à un programme, et non à un processus ou à un thread.

- Peut s’identifier et le processus dans lequel il est en cours d’exécution. Un programme peut être attaché à, être détaché de, et décrire le DE qui l’a créé, le cas échéant. Un programme peut également exécuter, arrêter, continuer et être terminé.

- Peut énumérer tous ses fils. Un programme peut également fournir son propre flux de démontage, et peut énumérer tous les contextes de code d’une position de document donnée.

- Est représenté par une interface [IDebugProgram2,](../../extensibility/debugger/reference/idebugprogram2.md) créée avant l’attachement du programme, ou dans le cadre du processus de joint, selon la mise en œuvre. Lorsqu’un port énumère les programmes d’un processus, chaque programme est créé conformément à une interface [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) correspondante adoptée comme argument à [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). Bien que les moteurs `IDebugProgram2` de débogé créent également des interfaces pour représenter les programmes, ces programmes ne sont pas créés conformément à un nœud de programme. Les `IDebugProgramNode2` interfaces créées par un DE sont utilisées pour le débogage réel, tandis que celles créées par un port ne sont utilisées que pour découvrir quels programmes sont en cours d’exécution dans un processus.

## <a name="see-also"></a>Voir aussi
- [Processus](../../extensibility/debugger/processes.md)
- [Nœuds de programme](../../extensibility/debugger/program-nodes.md)
- [Modules](../../extensibility/debugger/modules.md)
- [Concepts Debugger](../../extensibility/debugger/debugger-concepts.md)
- [Moteur Debug](../../extensibility/debugger/debug-engine.md)
- [Position du document](../../extensibility/debugger/document-position.md)
- [Contexte du code](../../extensibility/debugger/code-context.md)
- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)
- [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)
