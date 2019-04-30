---
title: Concepts du débogueur | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK]
ms.assetid: 2d371d38-f1a0-4a9a-8ea3-100e8c0149b7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7e3a9043215c5242246e54dc3e1eb2e85cd26c91
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62925891"
---
# <a name="debugger-concepts"></a>Concepts du débogueur
Pour générer sur le package de débogage de Visual Studio, vous devez être familiarisé avec les concepts architectures utilisés lors de la conception du package.

## <a name="in-this-section"></a>Dans cette section
 [La session de débogage](../../extensibility/debugger/debug-session.md) explique le rôle d’une session de l’architecture du débogage.

 [Serveurs](../../extensibility/debugger/servers-visual-studio-sdk.md) définit un serveur est en termes d’architecture, le débogage en termes d’aussi bien abstraits que physiques.

 [Fournisseurs de port](../../extensibility/debugger/port-suppliers.md) définit quelles un fournisseur de port est en termes d’architecture de débogage.

 [Ports](../../extensibility/debugger/ports.md) définit un port est en termes d’architecture de débogage.

 [Processus](../../extensibility/debugger/processes.md) définit un processus est en termes d’architecture de débogage.

 [Programmer des nœuds](../../extensibility/debugger/program-nodes.md) définit un nœud de programme en termes d’architecture, notamment comment il peut identifier lui-même et le processus, il est en cours d’exécution dans le débogage.

 [Programmes](../../extensibility/debugger/programs.md) définit un programme en termes d’architecture de débogage.

 [Threads](../../extensibility/debugger/threads.md) définit les caractéristiques de threads en termes d’architecture de débogage.

 [Frames de pile](../../extensibility/debugger/stack-frames.md) définit un frame de pile en termes d’architecture de débogage. Un frame de pile est une abstraction d’une pile qui fournit le contexte d’exécution d’un thread.

 [Modules](../../extensibility/debugger/modules.md) définit un module, en termes d’architecture, de débogage comme un conteneur physique de code, comme un fichier exécutable ou une DLL.

 [Points d’arrêt](../../extensibility/debugger/breakpoints-visual-studio-sdk.md) définit les trois types de points d’arrêt, en attente, la limite et d’erreur, en termes d’architecture de débogage.

## <a name="related-sections"></a>Rubriques connexes
 [Contextes du débogueur](../../extensibility/debugger/debugger-contexts.md) explique comment le moteur de débogage (dé) fonctionne simultanément dans des contextes d’évaluation code, documentation et expression. Décrit, pour chacun des trois contextes, emplacement, position ou d’évaluation pertinente à ce dernier.

 [Composants du débogueur](../../extensibility/debugger/debugger-components.md) fournit une vue d’ensemble des composants de débogage de Visual Studio, qui incluent le moteur de débogage (DE), évaluateur d’expression (EE) et le Gestionnaire de symboles (SH).

 [Déboguer des tâches](../../extensibility/debugger/debugging-tasks.md) contient des liens vers diverses tâches de débogage, telles que lancement d’un programme et l’évaluation des expressions.