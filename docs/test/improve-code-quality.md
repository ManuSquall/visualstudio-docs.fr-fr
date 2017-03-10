---
title: "Améliorer la qualité du code"
ms.custom: na
ms.date: 10/14/2016
ms.reviewer: na
ms.suite: na
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: na
ms.topic: article
helpviewer_keywords:
- Visual Studio ALM
- team-based development
ms.assetid: 73baa961-c21f-43fe-bb92-3f59ae9b5945
caps.latest.revision: 39
ms.author: mlearned
manager: douge
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
ms.sourcegitcommit: 93f70de0acfa8b5efcfe141a1f8060061a4ba15d
ms.openlocfilehash: 0c439304b8a23166293fc4cc6d984947fd51f133
ms.lasthandoff: 02/22/2017

---
# <a name="improve-code-quality"></a>Améliorer la qualité du code
Qu'est-ce que la qualité du code ? Pour que le code que vous créez soit de qualité, il faut qu'il soit correct, facile à maintenir et même élégant. Quelle que soit la façon dont vous le définissez, les outils de test de Visual Studio peuvent vous aider vous et votre équipe à développer et à maintenir des normes élevées d’excellence du code.  
  
 **Requirements**  
  
-   Certains outils et fonctionnalités décrits dans cette section sont uniquement disponibles dans des éditions spécifiques de Visual Studio. Ils ne sont pas universellement disponibles dans Visual Studio. Les spécifications propres à chaque édition sont répertoriées dans la documentation de ces outils et fonctionnalités.  
  
## <a name="in-this-section"></a>Dans cette section  
 Le tableau ci-dessous contient les descriptions des tâches courantes ainsi que des liens pointant vers des informations supplémentaires sur la façon dont vous pouvez mener à bien ces tâches.  
  
|||  
|-|-|  
|[Tests unitaires sur votre code](../test/unit-test-your-code.md)|L'Explorateur de tests facilite l'intégration des tests unitaires dans votre pratique de développement. Vous pouvez utiliser l'infrastructure de test unitaire Microsoft ou une des infrastructures tierces et ouvertes.|  
|[Analyse de la qualité des applications](../code-quality/analyzing-application-quality-by-using-code-analysis-tools.md)|Les outils d'analyse du code statique recherchent la conception, l'utilisation, la maintenabilité, et les problèmes de style en C++ et code managé. Bon nombre de ces problèmes peuvent provoquer des bogues difficiles à reproduire dans l'environnement de test standard.|  
|[Mesures de la complexité et de la facilité de maintenance du code managé](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)|La métrique du code est un jeu de mesures de logiciel qui fournit aux développeurs plus de détails sur le code qu'ils développent. La métrique inclut un index de maintenabilité des fonctions et des classes, la complexité cyclomatique des fonctions, la profondeur d'héritage des classes et la quantité de couplage entre les classes.|  
|[PreEmptive Analytics pour Team Foundation Server](http://msdn.microsoft.com/library/hh973124.aspx)|PreEmptive Analytics pour TFS CE vous permet d'intégrer des processus de développement pilotés par commentaires à votre flux de travail de développement. Vos applications renvoient automatiquement des données de rapport d'exception au service PreEmptive Analytics dès que des erreurs se produisent au cours de leur exécution. Ensuite, le service crée ou met à jour les éléments de travail dans Microsoft Team Foundation Server en fonction des règles et des seuils que vous définissez.|  
|[PreEmptive Dotfuscator and Analytics CE](assetId:///25d195d4-9f76-4dcc-9fbb-eeb9bdca9a3f)|PreEmptive Dotfuscator est un logiciel d'obfuscation et de compactage d'applications .NET. Il aide à protéger les programmes de toute ingénierie à rebours tout en contribuant à les rendre moins volumineux et plus efficaces.|  
  
## <a name="related-scenarios"></a>Scénarios connexes  
 [Adoption de Visual Studio et Team Foundation Server pour Application Lifecycle Management](assetId:///7ae9182f-4762-4bd3-b238-39ce987932e5)  
 Si Visual Studio Team Foundation ne vous est pas familier, vous pouvez apprendre à l’utiliser dans un environnement de développement en équipe pour améliorer la productivité et réduire les risques associés au développement d’applications.  
  
 [Analyse et modélisation de l’architecture](../modeling/analyze-and-model-your-architecture.md)  
 Vous pouvez utiliser [!INCLUDE[vsPreExt](../test/includes/vspreext_md.md)] afin de faire face aux difficultés et à la complexité de la conception de logiciel. [!INCLUDE[vsPreShort](../test/includes/vspreshort_md.md)] vous permet de modéliser visuellement votre application, telle qu'elle existe actuellement et comme vous souhaitez qu'elle existe ultérieurement. Vous pouvez créer et tenir à jour des diagrammes pour vous aider à visualiser en même temps les modèles logiques de votre application et les modèles physiques ; cela vous permet de modifier, valider et analyser le logiciel « en cours de conception ».  
  
 [Test de l’application](https://www.visualstudio.com/docs/test/overview)  
 Vous pouvez utiliser [!INCLUDE[vsPreShort](../test/includes/vspreshort_md.md)] et [!INCLUDE[vsUltShort](../test/includes/vsultshort_md.md)] pour être plus productif durant le cycle de vie de test. [!INCLUDE[vsPreShort](../test/includes/vspreshort_md.md)] ou [!INCLUDE[vsUltShort](../test/includes/vsultshort_md.md)] vous permet de planifier votre effort de test. Vous pouvez créer, gérer, modifier et effectuer à la fois des tests manuels et automatisés. Vous pouvez aussi passer en revue la progression de vos tests en fonction de votre plan.  
  
 [Générer l’application](https://www.visualstudio.com/docs/build/overview)  
 Vous pouvez utiliser [!INCLUDE[esprbuild](../test/includes/esprbuild_md.md)] pour créer et gérer des générations automatisées pour votre code. [!INCLUDE[esprbuild](../test/includes/esprbuild_md.md)] vous permet de créer des serveurs de déplacement pour déployer des builds. En outre, vous pouvez analyser des tendances de génération.  
  
 [Effectuer le suivi d’un travail à l’aide de Visual Studio Online ou Team Foundation Server](https://www.visualstudio.com/docs/work/overview)  
 Vous pouvez utiliser [!INCLUDE[vstsTfsLong](../test/includes/vststfslong_md.md)] pour planifier et effectuer le suivi de vos projets, que vous utilisiez le processus agile, le processus formel ou une variante de ces processus. En planifiant vos projets, en suivant votre progression par rapport au plan et en faisant les réglages nécessaires, vous pouvez réduire les risques, évitez les surprises désagréables et gérez le coût de vos projets.
