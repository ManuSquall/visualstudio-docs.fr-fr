---
title: Vue d’ensemble de l’extensibilité des dossiers ouverts Visual Studio | Microsoft Docs
ms.date: 02/21/2018
ms.topic: overview
ms.assetid: 94c3f8bf-1de3-40ea-aded-7f40c4b314c7
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: d213a7add358c46f7088f504d8c54352cda44a1c
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85905967"
---
# <a name="open-folder-extensibility"></a>Ouvrir l’extensibilité des dossiers

La fonctionnalité [ouvrir le dossier](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) permet aux utilisateurs d’ouvrir n’importe quel code base dans Visual Studio sans avoir besoin de fichiers projet ou solution. Ouvrir un dossier fournit les fonctionnalités que les utilisateurs attendent de Visual Studio, par exemple :

* Intégration et recherche de Explorateur de solutions
* Colorisation de l’éditeur
* Accéder à la navigation
* Rechercher dans la recherche de fichiers

Lorsqu’ils sont utilisés avec des charges de travail telles que pour le développement .NET et C++, les utilisateurs obtiennent également :

* IntelliSense enrichi
* Fonctionnalités spécifiques au langage

Avec un dossier ouvert, les créateurs d’extensions peuvent créer des fonctionnalités riches pour n’importe quel langage. Il existe des API pour prendre en charge la génération, le débogage et la recherche de symbole pour tout fichier dans le code base d’un utilisateur. Les extendeurs actuels peuvent mettre à jour leurs fonctionnalités Visual Studio existantes pour comprendre le code sans la sauvegarde de projets ou d’une solution.

## <a name="an-api-without-project-systems"></a>API sans système de projet

Historiquement, Visual Studio ne comprisa que les fichiers d’une solution et ses projets utilisant des systèmes de projet. Un système de projet est responsable de la fonctionnalité et des interactions utilisateur d’un projet chargé. Il comprend les fichiers qu’il contient, la représentation visuelle du contenu du projet, les dépendances sur d’autres projets et la modification du fichier projet sous-jacent. C’est à travers ces hiérarchies et fonctionnalités que les autres composants fonctionnent pour le compte de l’utilisateur. Toutes les bases de code ne sont pas bien représentées dans une structure de projet et de solution. Les langages de script et le code open source écrits en C++ pour Linux sont de bons exemples. Avec un dossier ouvert, Visual Studio offre aux utilisateurs une nouvelle façon d’interagir avec leur code source.

Les API des dossiers ouverts se trouvent sous l' `Microsoft.VisualStudio.Workspace.*` espace de noms et sont disponibles pour les extendeurs pour produire et consommer des données ou des actions autour des fichiers dans un dossier ouvert. Les extensions peuvent utiliser ces API pour fournir des fonctionnalités pour de nombreuses zones, notamment :

- [Espaces de travail](workspaces.md) : le point de départ de l’extensibilité des dossiers ouverts est l’espace de travail et ses API.
- [Contextes de fichier et actions](workspace-file-contexts.md) : informations de code spécifiques aux fichiers fournies par le biais de contextes de fichier.
- [Indexation](workspace-indexing.md) : collecte et conserve les données sur les espaces de travail de dossier ouverts.
- [Services de langage](workspace-language-services.md) : intégrez les services de langage dans les espaces de travail de dossier ouverts.
- [Build](workspace-build.md) -générer la prise en charge des espaces de travail de dossier ouverts.

Les fonctionnalités qui utilisent les types suivants devront adopter de nouvelles API pour prendre en charge l’ouverture de dossier :

- `IVsHierarchy`
- `IVsProject`
- `DTE`

## <a name="feedback-comments-issues"></a>Commentaires, commentaires, problèmes

Ouvrez le dossier et les API sont en cours de `Microsoft.VisualStudio.Workspace.*` développement. Si vous constatez un comportement inattendu, consultez les problèmes connus pour la publication d’intérêt. La [communauté des développeurs](https://developercommunity.visualstudio.com) est l’endroit recommandé pour voter et créer des problèmes. Pour chaque commentaire, nous vous recommandons vivement de fournir une description détaillée de votre problème. Incluez la version de Visual Studio pour laquelle vous développez, les API que vous utilisez (ce que vous avez implémenté et ce que vous utilisez), le résultat attendu et le résultat réel. Si possible, incluez un vidage du processus de devenv.exe. Utilisez le suivi des problèmes de GitHub pour fournir des commentaires sur ce et la documentation associée.

## <a name="next-steps"></a>Étapes suivantes

* [Espaces de travail](workspaces.md) : en savoir plus sur l’API ouvrir un dossier d’espace de travail.