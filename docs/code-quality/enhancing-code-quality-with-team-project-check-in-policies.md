---
title: "Amélioration de la qualité du Code avec les stratégies d’archivage du projet d’équipe | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code quality, using check-in policies
- team-based development, enhancing code quality
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: c82bc929fa7633719c06569cb3dded5df651a349
ms.sourcegitcommit: d6327b978661c0a745bf4b59f32d8171607803a3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2018
---
# <a name="enhancing-code-quality-with-team-project-check-in-policies"></a>Amélioration de la qualité du code avec des stratégies d’archivage de projet d’équipe

Quand vous utilisez le contrôle de version Team Foundation, vous pouvez créer des stratégies d’archivage pour vos projets d’équipe afin d’appliquer des pratiques permettant d’améliorer le développement de code et d’optimiser le travail en groupe. Les stratégies d’archivage sont des règles établies au niveau du projet d’équipe et appliquées sur les ordinateurs des développeurs avant que le code ne soit autorisé à être archivé.

Vous pouvez spécifier les stratégies d’archivage de projet d’équipe suivantes :

- **Générations**: exigent que les arrêts de génération créés pendant une génération soient résolus avant un nouvel archivage.

- **Commentaires sur un ensemble de modifications**: exigent que les utilisateurs fassent des commentaires en cas de modification d’un archivage.

- **Analyse du code**: exige que l’analyse du code soit exécutée avant l’archivage.

- **Éléments de travail**: exige qu’un ou plusieurs éléments de travail soient associés à l’archivage.

> [!IMPORTANT]
> Pour utiliser les stratégies d’archivage, vous devez être connecté à [!INCLUDE[vststfsLong](../code-quality/includes/vststfslong_md.md)].

## <a name="common-tasks"></a>Tâches courantes

|Tâche|Contenu de support|
|----------|------------------------|
|**Créer et utiliser des stratégies d’archivage d’analyse du code :** vous pouvez soit sélectionner des stratégies parmi un jeu standard de règles d’analyse du code, soit créer un jeu personnalisé.|[Création et utilisation de stratégies d’archivage de l’analyse du code](../code-quality/creating-and-using-code-analysis-check-in-policies.md)|

## <a name="related-tasks"></a>Tâches connexes

|Tâche|Contenu de support|
|----------|------------------------|
|**Utiliser l’analyse du code dans le processus de développement :** les membres de l’équipe effectuent une analyse du code sur leurs ordinateurs dédiés au développement. Dans Visual Studio, les développeurs configurent et exécutent des opérations d’analyse du code pour des projets de code individuels, consultent et analysent les problèmes rencontrés dans les opérations et créent des éléments de travail pour les avertissements.|[Analyse de la qualité des applications](../code-quality/analyzing-application-quality-by-using-code-analysis-tools.md)|
|**Créer et exécuter des tests unitaires :** tests unitaires offrent aux développeurs et aux testeurs une méthode rapide pour rechercher des erreurs de logique dans les méthodes des classes dans les projets c#, Visual Basic et C++. Un test unitaire peut être créé une fois et exécuté à chaque modification du code source pour s’assurer qu’aucun bogue n’a été introduit.|[Tests unitaires sur votre code](../test/unit-test-your-code.md)|
|**Suivre des éléments de travail et des défauts :** vous pouvez utiliser des éléments de travail pour suivre et gérer à la fois votre travail et les informations concernant votre projet d’équipe. Un élément de travail est un enregistrement de base de données que [!INCLUDE[esprfound](../code-quality/includes/esprfound_md.md)] utilise pour effectuer le suivi de l’assignation et de la progression d’un travail. Vous pouvez utiliser différents types d’éléments de travail pour effectuer le suivi de différents types de travaux, par exemple les spécifications du client, les bogues de produits et les tâches de développement.|[Éléments de travail (VSTS)](/vsts/work/work-items/index)|

## <a name="external-resources"></a>Ressources externes

[Test de la livraison continue avec Visual Studio 2012 - Chapitre 2 : Tests unitaires : tester l’intérieur](http://go.microsoft.com/fwlink/?LinkID=255188)