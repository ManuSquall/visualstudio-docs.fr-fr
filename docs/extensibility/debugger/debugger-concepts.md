---
title: Debugger Concepts - France Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK]
ms.assetid: 2d371d38-f1a0-4a9a-8ea3-100e8c0149b7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9ad8a450f9e79c1d44b8e098c8a00bb4b816e1af
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738980"
---
# <a name="debugger-concepts"></a>Concepts Debugger
Pour construire sur le paquet de débbug Visual Studio, vous devez être familier avec les concepts architecturaux utilisés dans la conception de l’emballage.

## <a name="in-this-section"></a>Contenu de cette section
 [Séance Debug](../../extensibility/debugger/debug-session.md) Explique le rôle d’une session dans l’architecture de débogage.

 [Serveurs](../../extensibility/debugger/servers-visual-studio-sdk.md) Définit ce qu’est un serveur en termes de débogage de l’architecture, en termes abstraits et physiques.

 [Fournisseurs portuaires](../../extensibility/debugger/port-suppliers.md) Définit ce qu’est un fournisseur de port en termes de débogage de l’architecture.

 [Ports](../../extensibility/debugger/ports.md) Définit ce qu’est un port en termes de débogage de l’architecture.

 [Processus](../../extensibility/debugger/processes.md) Définit ce qu’est un processus en termes de débogage de l’architecture.

 [Nœuds de programme](../../extensibility/debugger/program-nodes.md) Définit un nœud de programme en termes de débogage de l’architecture, y compris la façon dont il peut s’identifier et le processus dans lequel il est en cours d’exécution.

 [Programmes](../../extensibility/debugger/programs.md) Définit un programme en termes de débogage de l’architecture.

 [Les fils](../../extensibility/debugger/threads.md) Définit les caractéristiques des threads en termes de débogage de l’architecture.

 [Piles de cadres](../../extensibility/debugger/stack-frames.md) Définit un cadre de pile en termes de débogage de l’architecture. Un cadre de pile est une abstraction d’une pile qui fournit le contexte d’exécution d’un thread.

 [Modules](../../extensibility/debugger/modules.md) Définit un module, en termes de débogage de l’architecture, comme un conteneur physique de code, comme un fichier exécutable ou un DLL.

 [Points d’arrêt](../../extensibility/debugger/breakpoints-visual-studio-sdk.md) Définit les trois types de points d’arrêt — en attente, liés et erreurs — en termes de débogage de l’architecture.

## <a name="related-sections"></a>Sections connexes
 [Contextes Debugger](../../extensibility/debugger/debugger-contexts.md) Explique comment le moteur de débogé (DE) fonctionne simultanément dans les contextes de code, de documentation et d’évaluation de l’expression. Décrit, pour chacun des trois contextes, l’emplacement, le poste ou l’évaluation qui lui est pertinent.

 [Composants Debugger](../../extensibility/debugger/debugger-components.md) Fournit un aperçu des composants Visual Studio Debugging, qui comprennent le moteur de débogage (DE), l’évaluateur d’expression (EE) et le gestionnaire de symboles (SH).

 [Tâches de débogé](../../extensibility/debugger/debugging-tasks.md) Contient des liens vers diverses tâches de débogage, telles que le lancement d’un programme et l’évaluation des expressions.
