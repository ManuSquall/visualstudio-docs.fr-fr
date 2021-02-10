---
title: Concepts du débogueur | Microsoft Docs
description: Découvrez les concepts architecturaux utilisés lors de la conception du package de débogage Visual Studio pour vous aider à créer ce package.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK]
ms.assetid: 2d371d38-f1a0-4a9a-8ea3-100e8c0149b7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5202ebdb621121e63adbdf5118cb0848689adde6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99952406"
---
# <a name="debugger-concepts"></a>Concepts du débogueur
Pour générer le package de débogage Visual Studio, vous devez connaître les concepts architecturaux utilisés lors de la conception du package.

## <a name="in-this-section"></a>Dans cette section
 [Session de débogage](../../extensibility/debugger/debug-session.md) Explique le rôle d’une session dans l’architecture de débogage.

 [Serveurs](../../extensibility/debugger/servers-visual-studio-sdk.md) Définit ce qu’un serveur est en termes d’architecture de débogage, en termes abstraits et physiques.

 [Fournisseurs de port](../../extensibility/debugger/port-suppliers.md) Définit ce qu’un fournisseur de ports est en termes d’architecture de débogage.

 [Ports](../../extensibility/debugger/ports.md) Définit ce qu’un port est en termes d’architecture de débogage.

 [Processus](../../extensibility/debugger/processes.md) Définit ce qu’un processus est en termes d’architecture de débogage.

 [Nœuds de programme](../../extensibility/debugger/program-nodes.md) Définit un nœud de programme en termes d’architecture de débogage, notamment la façon dont il peut s’identifier et le processus dans lequel il s’exécute.

 [Programmes](../../extensibility/debugger/programs.md) Définit un programme en termes d’architecture de débogage.

 [Threads](../../extensibility/debugger/threads.md) Définit les caractéristiques des threads en termes d’architecture de débogage.

 [Frames de pile](../../extensibility/debugger/stack-frames.md) Définit un frame de pile en termes d’architecture de débogage. Un frame de pile est une abstraction d’une pile qui fournit le contexte d’exécution d’un thread.

 [Modules](../../extensibility/debugger/modules.md) Définit un module, en termes d’architecture de débogage, comme un conteneur physique de code, tel qu’un fichier exécutable ou une DLL.

 [Points d’arrêt](../../extensibility/debugger/breakpoints-visual-studio-sdk.md) Définit les trois types de points d’arrêt (en attente, liés et erreur) en termes d’architecture de débogage.

## <a name="related-sections"></a>Sections connexes
 [Contextes du débogueur](../../extensibility/debugger/debugger-contexts.md) Explique comment le moteur DE débogage fonctionne simultanément dans le code, la documentation et les contextes d’évaluation des expressions. Décrit, pour chacun des trois contextes, l’emplacement, la position ou l’évaluation qui s’y rapporte.

 [Composants du débogueur](../../extensibility/debugger/debugger-components.md) Fournit une vue d’ensemble des composants de débogage de Visual Studio, notamment le moteur DE débogage (DE), l’évaluateur d’expression (EE) et le gestionnaire de symboles (SH).

 [Tâches de débogage](../../extensibility/debugger/debugging-tasks.md) Contient des liens vers différentes tâches de débogage, telles que le lancement d’un programme et l’évaluation d’expressions.
