---
title: Compilation et génération
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- builds [Visual Studio], about building in Visual Studio
- custom build steps, types of builds
ms.assetid: c7958821-285f-4e28-9e7a-b5d8b40336a1
caps.latest.revision: 30
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 04d67f90006d4e11b2cbe16f6dacd3ba02cde7a6
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54779447"
---
# <a name="compiling-and-building-in-visual-studio"></a>Compilation et génération dans Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez utiliser Visual Studio pour générer des applications et créer des assemblys et des programmes exécutables à intervalles fréquents pendant un cycle de développement. En générant souvent votre code, vous pouvez identifier plus tôt les erreurs de compilation, telles qu'une syntaxe incorrecte, des mots clés mal orthographiés et des incompatibilités de types. Vous pouvez également détecter et corriger les erreurs d'exécution, telles que les erreurs de logique et les erreurs sémantiques, en générant et en exécutant souvent les versions Debug du code.

 Une fois qu'un projet ou une solution est entièrement développé et suffisamment débogué, il est possible de compiler ses composants dans une version Release. Par défaut, une version Release est optimisée et conçue pour être plus petite et s’exécuter plus rapidement qu’une version Debug. Pour plus d’informations, consultez [Procédure pas à pas : Génération d’une application](../ide/walkthrough-building-an-application.md).

## <a name="choosing-a-build-method"></a>Choix d'une méthode de génération
 Vous pouvez générer une application à l'aide des options de build par défaut dans l'IDE, à l'invite de commandes ou à l'aide de Team Foundation Build. Chacune de ces options utilise MSBuild comme technologie sous-jacente, et chaque approche présente des avantages spécifiques, comme indiqué dans le tableau suivant.

|Méthode de génération|Avantages|Pour plus d'informations|
|------------------|--------------|--------------------------|
|Utilisation de l'IDE|-   Vous pouvez créer plus facilement des builds et les exécuter immédiatement.<br />-   Vous pouvez exécuter des builds multiprocesseurs pour les projets C++ et C#.<br />-   Vous pouvez personnaliser certains aspects du système de génération.|[Génération et nettoyage de solutions et de projets dans Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)|
|Exécution d'une ligne de commande MSBuild|-   Vous pouvez générer des projets sans installer Visual Studio.<br />-   Vous pouvez exécuter des builds multiprocesseurs pour tous les types de projets.<br />-   Vous pouvez personnaliser la plupart des zones du système de génération.|[MSBuild](../msbuild/msbuild.md)|
|Utilisation de Team Foundation Build|-   Vous pouvez automatiser votre processus de génération. Par exemple, vous pouvez générer un ou plusieurs projets la nuit ou chaque fois le code est archivé. Vous pouvez également générer des projets sur les serveurs de build partagés plutôt que sur votre ordinateur de développement.<br />-   Vous pouvez spécifier rapidement le code que vous souhaitez générer, les tests à exécuter et d’autres options courantes.<br />-   Vous pouvez modifier le flux de travail de build et, si nécessaire, créer des activités de build pour effectuer des tâches profondément personnalisées.|[Générer l’application](http://msdn.microsoft.com/library/a971b0f9-7c28-479d-a37b-8fd7e27ef692)|

## <a name="building-from-the-ide"></a>Génération à partir de l'IDE
 Lorsque vous créez un projet, les configurations de build par défaut sont définies pour ce projet, et une configuration de build de solution par défaut lui est assignée pour fournir un contexte aux builds. Les configurations de solution définissent comment les projets de la solution sont générés et déployés. Les configurations de projet sont un jeu de propriétés de projet qui sont uniques pour un type de plateforme et de build (par exemple, Release Win32). Vous pouvez modifier ces configurations par défaut, et créer vos propres configurations. Pour plus d’informations, consultez [Introduction au Concepteur de projet](http://msdn.microsoft.com/898dd854-c98d-430c-ba1b-a913ce3c73d7) et [NIB Comment : Modifier les propriétés du projet et les paramètres de Configuration](http://msdn.microsoft.com/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67).

 Dans l’IDE, vous pouvez effectuer les tâches additionnelles suivantes :

-   [Modifier le répertoire de sortie de génération](../ide/how-to-change-the-build-output-directory.md).

-   [Identifier les projets qui dépendent de la sortie d’un autre projet pour effectuer une génération correcte](../ide/how-to-create-and-remove-project-dependencies.md).

-   [Modifier la quantité d’informations contenues dans le journal de génération ou la fenêtre Sortie des builds](../ide/how-to-view-save-and-configure-build-log-files.md).

-   [Masquer les avertissements spécifiques du compilateur pour Visual C#, Visual C++ ou Visual Basic](../ide/how-to-suppress-compiler-warnings.md).

-   [Spécifier des actions de précompilation et de post-compilation personnalisées pour une build](../ide/specifying-custom-build-events-in-visual-studio.md).

-   Améliorer les performances de génération en utilisant des builds parallèles. Pour plus d’informations, consultez [Génération parallèle de plusieurs projets](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md) ou le billet de blog [Réglage du parallélisme de génération C++](http://blogs.msdn.com/b/msbuild/archive/2010/03/08/tuning-c-build-parallelism-in-vs2010.aspx).

## <a name="see-also"></a>Voir aussi
 [Procédure pas à pas : Création d’une Application](../ide/walkthrough-building-an-application.md) [présentation des Configurations de Build](../ide/understanding-build-configurations.md) [présentation des plateformes de générations](../ide/understanding-build-platforms.md) [génération (compilation) de projets de Site Web](http://msdn.microsoft.com/library/a9cbb88c-8fff-4c67-848b-98fbfd823193) [ Comment : Créer et supprimer les dépendances d’un projet](../ide/how-to-create-and-remove-project-dependencies.md)
