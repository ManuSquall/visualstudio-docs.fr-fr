---
title: Responsable Debug session (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- session debug manager, unifying session views
- session debug manager, broadcasting
- debugging [Debugging SDK], session debug manager
- session debug manager
- session debug manager, debug engine multiplexing
- session debug manager, delegating
ms.assetid: fbb1928d-dddc-43d1-98a4-e23b0ecbae09
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 953b4e948ef5e21531a3e73bceed3a363ed3cec5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712882"
---
# <a name="session-debug-manager"></a>Gestionnaire de débogé de session
Le gestionnaire de déboguer la session (SDM) gère un certain nombre de moteurs de déboguer (DE) qui déboient un certain nombre de programmes dans plusieurs processus à travers un certain nombre de machines. En plus d’être un multiplexer moteur de débogé, le SDM fournit une vue unifiée de la session de débog à l’IDE.

## <a name="session-debug-manager-operation"></a>Opération de gestionnaire de débogue de session
 Le gestionnaire de débogé de session (SDM) gère le DE. Il peut y avoir plus d’un moteur de déboguer en cours d’exécution sur une machine en même temps. Pour multiplexer les DE, le SDM enveloppe un certain nombre d’interfaces des DE et les expose à l’IDE comme une seule interface.

 Pour augmenter les performances, certaines interfaces ne sont pas multiplexées. Au lieu de cela, ils sont utilisés directement à partir de la DE, et les appels à ces interfaces ne passent pas par le SDM. Par exemple, les interfaces utilisées avec la mémoire, le code et les contextes de documents ne sont pas multiplexées, car elles se réfèrent à une instruction, une mémoire ou un document spécifiques dans un programme spécifique débogé par un DE spécifique. Aucun autre DE n’a besoin d’être impliqué dans ce niveau de communication.

 Ce n’est pas le cas de tous les contextes. Les appels à l’interface contextuelle d’expression passent par le SDM. Pendant l’évaluation d’expression, le SDM enveloppe [l’interface IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) qu’elle donne à l’IDE parce que lorsque cette expression est évaluée, elle peut impliquer plusieurs DE qui sont des programmes de débogage dans le même processus qui pourraient être en cours d’exécution sur le même thread.

 Le SDM agit généralement comme un mécanisme de délégation, mais il peut agir comme un mécanisme de radiodiffusion. Par exemple, lors de l’évaluation de l’expression, le SDM agit comme un mécanisme de diffusion pour aviser tous les DE qu’ils peuvent exécuter du code sur un thread spécifié. De même, lorsque le SDM reçoit un événement d’arrêt, il diffuse aux émissions qu’ils devraient cesser de courir. Lorsqu’une étape est déclenchée, le SDM diffuse aux émissions qu’ils peuvent continuer à exécuter. Les points d’arrêt sont également diffusés à chaque DE.

 Le SDM ne suit pas le programme actuel, le thread ou le cadre de pile. Les informations sur le processus, le programme et le fil sont envoyées au SDM en conjonction avec des événements spécifiques de débogage.

## <a name="see-also"></a>Voir aussi
- [Moteur Debug](../../extensibility/debugger/debug-engine.md)
- [Composants Debugger](../../extensibility/debugger/debugger-components.md)
- [Contextes Debugger](../../extensibility/debugger/debugger-contexts.md)
