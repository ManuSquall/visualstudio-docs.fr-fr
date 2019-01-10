---
title: Concepts MSBuild | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, concepts
ms.assetid: 083b8ba3-e4ad-45af-bb5d-3bc81d406131
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1aaaf8dfae7ed0fd3626779fa1ba33e795d9f1d8
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53913502"
---
# <a name="msbuild-concepts"></a>Concepts MSBuild
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] fournit un schéma XML de base qui vous permet de contrôler la manière dont la plateforme de génération génère les logiciels. Pour spécifier les composants de la génération et comment ils doivent être générés, utilisez ces quatre parties de MSBuild : propriétés, éléments, tâches et cibles.  

## <a name="related-topics"></a>Rubriques connexes  

| Titre | Description |
| - | - |
| [Propriétés MSBuild](../msbuild/msbuild-properties.md) | Présente les propriétés et les collections de propriétés. Les propriétés sont des paires clé/valeur qui vous permettent de configurer les générations. |
| [MSBuild, éléments](../msbuild/msbuild-items.md) | Présente les éléments et les collections d’éléments. Les éléments sont des entrées du système de génération qui représentent généralement des fichiers. |
| [Cibles de MSBuild](../msbuild/msbuild-targets.md) | Explique comment grouper les tâches dans un ordre particulier et autoriser des sections du processus de génération à être appelées sur la ligne de commande. |
| [MSBuild, tâches](../msbuild/msbuild-tasks.md) | Indique comment créer une unité de code exécutable qui peut être utilisée par [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] afin d'exécuter des opérations de génération atomiques. |
| [Comparaison des propriétés et des éléments](../msbuild/comparing-properties-and-items.md) | Compare les propriétés et les éléments MSBuild. Les deux permettent de transmettre des informations aux tâches, d’évaluer des conditions et de stocker les valeurs qui peuvent être référencées dans le fichier projet. |
| [Caractères spéciaux MSBuild](../msbuild/msbuild-special-characters.md) | Explique comment insérer certains caractères dans des séquences d’échappement que [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] réserve pour une utilisation particulière dans des contextes spécifiques. |
| [Procédure pas à pas : Créer un fichier projet MSBuild à partir de zéro](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md) | Indique comment créer de façon incrémentielle un fichier projet de base, en utilisant uniquement un éditeur de texte. |
| [Procédure pas à pas : Utiliser MSBuild](../msbuild/walkthrough-using-msbuild.md) | Présente les blocs de construction de MSBuild et indique comment écrire, manipuler et déboguer des projets MSBuild sans fermer l’environnement de développement intégré (IDE) de Visual Studio. |
| [Informations de référence sur MSBuild](../msbuild/msbuild-reference.md) | Renvoie aux documents contenant les informations de référence. |
| [MSBuild](../msbuild/msbuild.md) | Présente une vue d’ensemble du schéma XML d’un fichier projet et montre comment il contrôle les processus qui génèrent les logiciels. |
