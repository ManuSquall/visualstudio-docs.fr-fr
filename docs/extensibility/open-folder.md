---
title: Présentation de l’extensibilité Visual Studio ouvrir le dossier | Microsoft Docs
ms.date: 02/21/2018
ms.topic: conceptual
ms.assetid: 94c3f8bf-1de3-40ea-aded-7f40c4b314c7
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 2bb74703f639848d643f536edf620e30b1836310
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62806451"
---
# <a name="open-folder-extensibility"></a>Extensibilité de dossier ouverte

Le [ouvrir le dossier](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) fonctionnalité permet aux utilisateurs d’ouvrir une base de code dans Visual Studio sans la nécessité pour les fichiers projet ou solution. Ouvrir le dossier fournit que les fonctionnalités que les utilisateurs attendent à partir de Visual Studio, telles que :

* Recherche et intégration de l’Explorateur de solutions
* Colorisation de l’éditeur
* Aller à la navigation
* Rechercher dans la recherche de fichiers

Lorsqu’il est utilisé avec les charges de travail par exemple, pour le développement .NET et C++, les utilisateurs obtiennent également :

* Rich Intellisense
* Fonctionnalités spécifiques au langage

Avec ouvrir le dossier, les auteurs d’extension peuvent créer des fonctionnalités riches pour n’importe quel langage. Il existe des API pour la prise en charge de génération, de débogage et de recherche de symbole de code de base de n’importe quel fichier dans un utilisateur. Les extendeurs actuels peuvent mettre à jour leurs fonctionnalités existantes de Visual Studio pour comprendre le code sans le soutien de projets ou d’une solution.

## <a name="an-api-without-project-systems"></a>Une API sans les systèmes de projet

Historiquement, Visual Studio compris uniquement les fichiers dans une solution et ses projets à l’aide de systèmes de projet. Un système de projet est chargé pour les interactions utilisateur et les fonctionnalités d’un projet chargé. Il sait quels fichiers son projet contient, la représentation visuelle du contenu du projet, les dépendances sur d’autres projets, et le fichier de projet de modification de l’objet sous-jacent. Il s’effectue via ces hiérarchies et les fonctionnalités autres composants ne fonctionnent pas pour le compte de l’utilisateur. Pas tous les codes base sont également représentées dans une structure de projet et solution. Langages de script et le code open source écrit en C++ pour Linux sont de bons exemples. Ouvrir le dossier, Visual Studio fournit aux utilisateurs une nouvelle façon d’interagir avec leur code source.

Les API de dossier ouvert sont sous la `Microsoft.VisualStudio.Workspace.*` espace de noms et sont disponibles pour les extendeurs produire et consommer des données ou des actions au sein d’ouvrir le dossier des fichiers. Extensions peuvent utiliser ces API pour fournir des fonctionnalités pour plusieurs domaines, notamment :

- [Espaces de travail](workspaces.md) - l’extensibilité de point d’ouvrir le dossier de démarrage est l’espace de travail et ses API.
- [Fichier de contextes et les actions](workspace-file-contexts.md) -fichier intelligence de code spécifiques fournie par le biais des contextes de fichier.
- [L’indexation](workspace-indexing.md) : collecter et conserver les données sur les espaces de travail d’ouvrir le dossier.
- [Services de langage](workspace-language-services.md) -intégrer des services de langage dans les espaces de travail d’ouvrir le dossier.
- [Build](workspace-build.md) -prise en charge des espaces de travail d’ouvrir le dossier de Build.

Fonctionnalités qui utilisent les types suivants devront adopter les nouvelles API pour prendre en charge d’ouvrir le dossier :

- `IVsHierarchy`
- `IVsProject`
- `DTE`

## <a name="feedback-comments-issues"></a>Commentaires, les commentaires, les problèmes

Ouvrez le dossier et le `Microsoft.VisualStudio.Workspace.*` API sont en cours de développement. Si vous voyez un comportement inattendu, puis consultez les problèmes connus pour la version d’intérêt. [Communauté de développeurs](https://developercommunity.visualstudio.com) est l’emplacement recommandé pour voter et de créer des problèmes. Pour chaque évaluation, nous vous recommandons une description détaillée de votre problème. Inclure la version de Visual Studio que vous développez, les API que vous utilisez (ce que vous avez implémenté et ce que vous interagissez avec), le résultat attendu et le résultat réel. Si possible, inclure une image du processus devenv.exe. Utiliser pour fournir des commentaires sur ce de suivi des problèmes de GitHub et de la documentation connexe.

## <a name="next-steps"></a>Étapes suivantes

* [Espaces de travail](workspaces.md) -en savoir plus sur l’espace de travail du dossier Open API.