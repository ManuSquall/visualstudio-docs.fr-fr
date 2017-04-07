---
title: "Compilation et génération dans Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
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
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 5581224b17a7b42f65b69f741f984a144d78fc26
ms.openlocfilehash: f4ae98f4e9b7dbf4b1066120316ee5a167ae78f2
ms.lasthandoff: 04/04/2017

---
# <a name="compiling-and-building-in-visual-studio"></a>Compilation et génération dans Visual Studio
Vous pouvez utiliser Visual Studio pour générer des applications et créer des assemblys et des programmes exécutables à intervalles fréquents pendant un cycle de développement. En générant souvent votre code, vous pouvez identifier plus tôt les erreurs de compilation, telles qu'une syntaxe incorrecte, des mots clés mal orthographiés et des incompatibilités de types. Vous pouvez également détecter et corriger les erreurs d'exécution, telles que les erreurs de logique et les erreurs sémantiques, en générant et en exécutant souvent les versions Debug du code.  
  
 Une fois qu'un projet ou une solution est entièrement développé et suffisamment débogué, il est possible de compiler ses composants dans une version Release. Par défaut, une version Release est optimisée et conçue pour être plus petite et s’exécuter plus rapidement qu’une version Debug. Pour plus d’informations, consultez [Procédure pas à pas : génération d’une application](../ide/walkthrough-building-an-application.md).  
  
## <a name="choosing-a-build-method"></a>Choix d'une méthode de génération  
 Vous pouvez générer une application à l'aide des options de build par défaut dans l'IDE, à l'invite de commandes ou à l'aide de Team Foundation Build. Chacune de ces options utilise MSBuild comme technologie sous-jacente, et chaque approche présente des avantages spécifiques, comme indiqué dans le tableau suivant.  
  
|Méthode de génération|Avantages|Pour plus d'informations|  
|------------------|--------------|--------------------------|  
|Utilisation de l'IDE|-   Vous pouvez créer plus facilement des builds et les exécuter immédiatement.<br />-   Vous pouvez exécuter des builds multiprocesseurs pour les projets C++ et C#.<br />-   Vous pouvez personnaliser certains aspects du système de génération.|[Génération et nettoyage de solutions et de projets dans Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)|  
|Exécution d'une ligne de commande MSBuild|-   Vous pouvez générer des projets sans installer Visual Studio.<br />-   Vous pouvez exécuter des builds multiprocesseurs pour tous les types de projets.<br />-   Vous pouvez personnaliser la plupart des zones du système de génération.|[MSBuild](../msbuild/msbuild.md)|  
|Utilisation de Team Foundation Build|-   Vous pouvez automatiser votre processus de génération. Par exemple, vous pouvez générer un ou plusieurs projets la nuit ou chaque fois le code est archivé. Vous pouvez également générer des projets sur les serveurs de build partagés plutôt que sur votre ordinateur de développement.<br />-   Vous pouvez spécifier rapidement le code que vous souhaitez générer, les tests à exécuter et d’autres options courantes.<br />-   Vous pouvez modifier le flux de travail de build et, si nécessaire, créer des activités de build pour effectuer des tâches profondément personnalisées.|[Générer l’application](http://msdn.microsoft.com/Library/a971b0f9-7c28-479d-a37b-8fd7e27ef692)|  
  
## <a name="building-from-the-ide"></a>Génération à partir de l'IDE  
 Lorsque vous créez un projet, les configurations de build par défaut sont définies pour ce projet, et une configuration de build de solution par défaut lui est assignée pour fournir un contexte aux builds. Les configurations de solution définissent comment les projets de la solution sont générés et déployés. Les configurations de projet sont un jeu de propriétés de projet qui sont uniques pour un type de plateforme et de build (par exemple, Release Win32). Vous pouvez modifier ces configurations par défaut, et créer vos propres configurations. Pour plus d’informations, consultez [Introduction au Concepteur de projets](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7) et [NIB Guide pratique pour modifier des propriétés de projet et des paramètres de configuration](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67).  
  
 Dans l’IDE, vous pouvez effectuer les tâches additionnelles suivantes :  
  
-   [Modifier le répertoire de sortie de génération](../ide/how-to-change-the-build-output-directory.md).  
  
-   [Identifier les projets qui dépendent de la sortie d’un autre projet pour effectuer une génération correcte](../ide/how-to-create-and-remove-project-dependencies.md).  
  
-   [Modifier la quantité d’informations contenues dans le journal de génération ou la fenêtre Sortie des builds](../ide/how-to-view-save-and-configure-build-log-files.md).  
  
-   [Masquer les avertissements spécifiques du compilateur pour Visual C#, Visual C++ ou Visual Basic](../ide/how-to-suppress-compiler-warnings.md).  
  
-   [Spécifier des actions de précompilation et de post-compilation personnalisées pour une build](../ide/specifying-custom-build-events-in-visual-studio.md).  
  
-   Améliorer les performances de génération en utilisant des builds parallèles. Pour plus d’informations, consultez [Génération parallèle de plusieurs projets](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md) ou le billet de blog [Réglage du parallélisme de génération C++](http://blogs.msdn.com/b/msbuild/archive/2010/03/08/tuning-c-build-parallelism-in-vs2010.aspx).  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure pas à pas : génération d’une application](../ide/walkthrough-building-an-application.md)   
 [Présentation des configurations de build](../ide/understanding-build-configurations.md)   
 [Présentation des plateformes de générations](../ide/understanding-build-platforms.md)   
 [Génération de sites web](http://msdn.microsoft.com/Library/a9cbb88c-8fff-4c67-848b-98fbfd823193)   
 [Guide pratique pour créer et supprimer les dépendances d’un projet](../ide/how-to-create-and-remove-project-dependencies.md)
