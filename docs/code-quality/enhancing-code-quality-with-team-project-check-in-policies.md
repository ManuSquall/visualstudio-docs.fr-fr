---
title: "Am&#233;lioration de la qualit&#233; du code avec des strat&#233;gies d’archivage de projet d’&#233;quipe | Microsoft Docs"
ms.custom: ""
ms.date: "12/12/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "qualité du code, utiliser des stratégies d’archivage"
  - "développement en équipe, améliorer la qualité du code"
ms.assetid: 0ab72c33-148a-4a8a-a7bf-046995514c84
caps.latest.revision: 25
caps.handback.revision: 25
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Am&#233;lioration de la qualit&#233; du code avec des strat&#233;gies d’archivage de projet d’&#233;quipe
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Quand vous utilisez le contrôle de version Team Foundation, vous pouvez créer des stratégies d’archivage pour vos projets d’équipe afin d’appliquer des pratiques permettant d’améliorer le développement de code et d’optimiser le travail en groupe. Les stratégies d’archivage sont des règles établies au niveau du projet d’équipe et appliquées sur les ordinateurs des développeurs avant que le code ne soit autorisé à être archivé.  
  
 Vous pouvez spécifier les stratégies d’archivage de projet d’équipe suivantes :  
  
-   **Générations** : exigent que les arrêts de génération créés pendant une génération soient résolus avant un nouvel archivage.  
  
-   **Commentaires sur un ensemble de modifications** : exigent que les utilisateurs fassent des commentaires en cas de modification d’un archivage.  
  
-   **Analyse du code** : exige que l’analyse du code soit exécutée avant l’archivage.  
  
-   **Éléments de travail** : exige qu’un ou plusieurs éléments de travail soient associés à l’archivage.  
  
> [!IMPORTANT]
>  Pour utiliser les stratégies d’archivage, vous devez être connecté à [!INCLUDE[vststfsLong](../code-quality/includes/vststfslong_md.md)].  
  
## Tâches courantes  
  
|Tâche|Contenu de support|  
|-----------|------------------------|  
|**Créer et utiliser des stratégies d’archivage :** vous créez des stratégies d’archivage à l’aide des paramètres Projet d’équipe du [!INCLUDE[esprscc](../code-quality/includes/esprscc_md.md)].|[Définir et appliquer des critères de qualité](../Topic/Set%20and%20Enforce%20Quality%20Gates.md)|  
|**Créer et utiliser des stratégies d’archivage d’analyse du code :** vous pouvez soit sélectionner des stratégies parmi un jeu standard de règles d’analyse du code, soit créer un jeu personnalisé.|[Création et utilisation de stratégies d'archivage de l'analyse du code](../code-quality/creating-and-using-code-analysis-check-in-policies.md)|  
  
## Tâches connexes  
  
|Tâche|Contenu de support|  
|-----------|------------------------|  
|**Installer votre environnement de développement :** avant de pouvoir créer ou modifier du code, vous devez installer vos environnements de test et développement à l’aide du code source approprié. Si vous utilisez des bases de données, vous devez aussi avoir accès à leur représentation hors connexion.|[Installation d’environnements de développement](http://msdn.microsoft.com/fr-fr/7b686610-d379-4ca0-9608-73ef0e576e3a)|  
|**Utiliser l’analyse du code dans le processus de développement :** les membres de l’équipe effectuent une analyse du code sur leurs ordinateurs dédiés au développement. Dans Visual Studio, les développeurs configurent et exécutent des opérations d’analyse du code pour des projets de code individuels, consultent et analysent les problèmes rencontrés dans les opérations et créent des éléments de travail pour les avertissements.|[Analyse de la qualité des applications](../code-quality/analyzing-application-quality-by-using-code-analysis-tools.md)|  
|**Créer et exécuter des tests unitaires** : les tests unitaires constituent, pour les développeurs et les testeurs, un moyen simple de rechercher des erreurs de logique dans les méthodes de classes, pour des projets C\#, Visual Basic .NET et C\+\+. Un test unitaire peut être créé une fois et exécuté à chaque modification du code source pour s’assurer qu’aucun bogue n’a été introduit.|[Tests unitaires sur votre code](../test/unit-test-your-code.md)|  
|**Suivre des éléments de travail et des défauts :** vous pouvez utiliser des éléments de travail pour suivre et gérer à la fois votre travail et les informations concernant votre projet d’équipe. Un élément de travail est un enregistrement de base de données que [!INCLUDE[esprfound](../code-quality/includes/esprfound_md.md)] utilise pour effectuer le suivi de l’assignation et de la progression d’un travail. Vous pouvez utiliser différents types d’éléments de travail pour effectuer le suivi de différents types de travaux, par exemple les spécifications du client, les bogues de produits et les tâches de développement.|[Assurer le suivi du travail et gérer le flux de travail &#91;redirection&#93;](http://msdn.microsoft.com/fr-fr/d2d8637d-0ef8-4ca3-874e-a04713344032)|  
  
## Ressources externes  
  
### Conseils  
 [Tester la livraison continue avec Visual Studio 2012 \- Chapitre 2 : Tests unitaires : tester l’intérieur](http://go.microsoft.com/fwlink/?LinkID=255188)