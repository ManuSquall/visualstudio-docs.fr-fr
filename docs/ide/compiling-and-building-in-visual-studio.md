---
title: "Compilation et génération dans Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 7/14/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- builds [Visual Studio], about building in Visual Studio
- custom build steps, types of builds
ms.assetid: c7958821-285f-4e28-9e7a-b5d8b40336a1
caps.latest.revision: 28
author: gewarren
ms.author: gewarren
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: e2b7ff9126e1cc38ac2e58d6be339b656a024e7f
ms.openlocfilehash: 1a2db8a10664e1d4b38b1d6867c5a3bad1532b39
ms.contentlocale: fr-fr
ms.lasthandoff: 08/10/2017

---

# <a name="compiling-and-building-in-visual-studio"></a>Compilation et génération dans Visual Studio

L’exécution d’une génération crée des assemblys et des applications exécutables à partir de votre code source à n’importe quel moment de votre cycle de développement. D’une façon générale, le processus de génération est très similaire entre de nombreux types différents de projets, comme Windows, ASP.NET, des applications mobiles, etc. Le processus de génération est également très similaire entre les langages de programmation, comme C#, Visual Basic, C++ et F#. 

En générant souvent une build à partir de votre code, vous pouvez identifier rapidement les erreurs de compilation, comme une syntaxe incorrecte, des mots clés mal orthographiés et des incompatibilités de types. Vous pouvez aussi détecter et corriger les erreurs d’exécution, comme les erreurs de logique et les erreurs sémantiques, en générant et en exécutant souvent des versions Debug du code.  

Une build réussie est essentiellement une validation que le code source de l’application contient une syntaxe correcte et que toutes les références statiques à des bibliothèques, des assemblys et à d’autres composants ont été résolues. Le résultat est une application exécutable dont le fonctionnement correct peut ensuite être testé à la fois dans un [environnement de débogage](../debugger/index.md) et par différents tests manuels et automatisés pour [vérifier la qualité du code](../test/improve-code-quality.md). Une fois que l’application a été entièrement testée, vous pouvez alors compiler une version Release à déployer auprès de vos clients. Pour une présentation de cette procédure, consultez [Procédure pas à pas : génération d’une application](../ide/walkthrough-building-an-application.md).  

Dans la famille de produits Visual Studio, vous pouvez utiliser trois méthodes pour générer une application : l’IDE de Visual Studio, les outils en ligne de commande MSBuild et Team Foundation Build sur Visual Studio Team Services :
 
| Méthode de génération | Avantages | 
| --- |--- | --- |  
| IDE |- Créer des builds immédiatement et les tester dans un débogueur.<br />- Exécuter des builds multiprocesseurs pour des projets C++ et C#.<br />- Personnaliser différents aspects du système de génération. |
| Ligne de commande MSBuild| - Générer des projets sans installer Visual Studio.<br />- Exécuter des builds multiprocesseurs pour tous les types de projets.<br />- Personnaliser la plupart des éléments du système de génération.|
| Team Foundation Build | - Automatiser votre processus de génération dans un pipeline d’intégration continue/de livraison continue.<br />- Appliquer des tests automatisés avec chaque build.<br />- Utiliser des ressources cloud virtuellement illimitées pour les processus de génération.<br />- Modifier le flux de travail de la génération et créer des activités de génération pour effectuer des tâches fortement personnalisées.|  

La documentation de cette section contient plus de détails sur le processus de génération avec l’IDE. Pour plus d’informations sur les autres méthodes, consultez [MSBuild](../msbuild/msbuild.md) et [Intégration et déploiement continus](https://www.visualstudio.com/docs/build/overview), respectivement.

## <a name="overview-of-building-from-the-ide"></a>Vue d’ensemble de la génération à partir de l’IDE  

Quand vous créez un projet, Visual Studio crée des configurations de build par défaut pour le projet et la solution qui contient le projet.  Ces configurations définissent comment les solutions et les projets sont générés et déployés. En particulier, les configurations de projet sont uniques pour une plateforme cible (comme Windows ou Linux) et un type de build (comme Debug ou Release). Vous pouvez modifier ces configurations comme vous le souhaitez et aussi créer vos propres configurations selon vos besoins.

Pour une première présentation de la génération dans l’IDE, consultez [Procédure pas à pas : génération d’une application](walkthrough-building-an-application.md).  

Consultez ensuite [Génération et nettoyage des solutions et de projets dans Visual Studio](building-and-cleaning-projects-and-solutions-in-visual-studio.md) pour en savoir plus sur les personnalisations des différents aspects que vous pouvez apporter au processus. Les personnalisations portent notamment sur le [changement des répertoires de sortie](how-to-change-the-build-output-directory.md), la [spécification d’événements de build personnalisés](specifying-custom-build-events-in-visual-studio.md), la [gestion des dépendances du projet](how-to-create-and-remove-project-dependencies.md), la [gestion des fichiers journaux de génération](how-to-view-save-and-configure-build-log-files.md) et la [suppression des avertissements du compilateur](how-to-suppress-compiler-warnings.md).

À partir de là, vous pouvez explorer différentes autres tâches :
- [Présentation des configurations de build](understanding-build-configurations.md)
- [Présentation des plateformes de génération](understanding-build-platforms.md)
- [Gestion des propriétés des projets et des solutions](managing-project-and-solution-properties.md).  
- Spécification des événements de build dans [C#](how-to-specify-build-events-csharp.md) et [Visual Basic](how-to-specify-build-events-visual-basic.md). 
- [Définition des options de génération](reference/options-dialog-box-projects-and-solutions-build-and-run.md)
- [Génération parallèle de plusieurs projets](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md).  
  
## <a name="see-also"></a>Voir aussi  

- [Génération (compilation) de projets de site web](http://msdn.microsoft.com/Library/a9cbb88c-8fff-4c67-848b-98fbfd823193)   

