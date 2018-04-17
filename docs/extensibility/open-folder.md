---
title: Vue d’ensemble de Visual Studio ouvrir le dossier d’extensibilité | Documents Microsoft
ms.custom: ''
ms.date: 02/21/2018
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: 94c3f8bf-1de3-40ea-aded-7f40c4b314c7
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: d916ea30dd9b72a2d8bd59e8d3d34f9e73c74877
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="open-folder-extensibility"></a>Ouvrez l’extensibilité du dossier

Le [ouvrir le dossier](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) fonctionnalité permet aux utilisateurs d’ouvrir une base de code dans Visual Studio sans avoir besoin pour les fichiers projet ou solution. Ouvrir le dossier fournit que les fonctionnalités que les utilisateurs attendent à partir de Visual Studio telles que :

* Recherche et l’intégration de l’Explorateur de solutions
* Colorisation de l’éditeur
* Aller à la navigation
* Rechercher dans la recherche de fichiers

Lorsqu’il est utilisé avec les charges de travail telles que le développement .NET et C++, les utilisateurs obtiennent également :

* Riches Intellisense
* Fonctionnalités spécifiques au langage

Avec ouvrir le dossier, les auteurs d’extensions peuvent créer des fonctionnalités évoluées pour n’importe quel langage. Il existe des API pour prendre en charge de génération, de débogage et de la recherche des symboles pour le code de base de n’importe quel fichier dans un utilisateur. Extendeurs actuels peuvent mettre à jour leurs fonctionnalités existantes de Visual Studio pour comprendre le code sans de projets ou d’une solution de sauvegarde.

## <a name="an-api-without-project-systems"></a>Une API sans les systèmes de projet

Historiquement, Visual Studio compris uniquement les fichiers dans une solution et ses projets à l’aide de systèmes de projet. Un système de projet est chargé des interactions utilisateur et les fonctionnalités d’un projet chargé. Il prend en charge les fichiers son projet contient, la représentation visuelle du contenu du projet, les dépendances sur d’autres projets, et le fichier de projet de modification de l’objet sous-jacent. Il s’agit de ces fonctions que les autres composants ne fonctionnent pas pour le compte de l’utilisateur et de hiérarchies. Pas toutes les bases de code sont également représentées dans une structure de projet et de solution. Langages de script et le code open source écrit en C++ pour Linux sont de bons exemples. Ouvrir le dossier, Visual Studio fournit aux utilisateurs une nouvelle façon d’interagir avec leur code source.

L’API de dossier ouvertes sont sous la `Microsoft.VisualStudio.Workspace.*` espace de noms et sont disponibles pour les extendeurs produire et consommer des données ou des actions au sein d’ouvrir le dossier des fichiers. Extensions peuvent utiliser ces API pour fournir des fonctionnalités de nombreux domaines, notamment :

- [Espaces de travail](workspaces.md) - l’extensibilité de point d’ouvrir le dossier de démarrage est l’espace de travail et ses API.
- [Les contextes et des actions de fichier](workspace-file-contexts.md) -intelligence de code spécifiques fournie par le biais des contextes de fichier du fichier.
- [L’indexation](workspace-indexing.md) - recueillir et conserver les données sur les espaces de travail ouvrir le dossier.
- [Les services de langage](workspace-language-services.md) -intégrer des services de langage dans les espaces de travail ouvrir le dossier.
- [Build](workspace-build.md) -prise en charge des espaces de travail ouvrir le dossier de génération.

Vous devrez à adopter les nouvelles API pour prendre en charge d’ouvrir le dossier fonctionnalités qui utilisent les types suivants :

- `IVsHierarchy`
- `IVsProject`
- `DTE`

## <a name="feedback-comments-issues"></a>Commentaires, les commentaires, les problèmes

Ouvrez le dossier et le `Microsoft.VisualStudio.Workspace.*` API sont en cours de développement actif. Si vous voyez un comportement inattendu, puis consultez les problèmes connus de la version d’intérêt. La Communauté des développeurs est l’emplacement recommandé de voter et de créer des problèmes. Pour chaque évaluation, nous vous recommandons une description détaillée de votre problème. Inclure la version de Visual Studio que vous développez pour, les API que vous utilisez (ce que vous avez implémenté et vous interagissez avec), le résultat attendu et le résultat réel. Si possible, inclure une image du processus devenv.exe. Utiliser le suivi de GitHub de commentaires sur ce et la documentation associée.

## <a name="next-steps"></a>Étapes suivantes

* [Espaces de travail](workspaces.md) -en savoir plus sur l’API d’espace de travail ouvrir le dossier.