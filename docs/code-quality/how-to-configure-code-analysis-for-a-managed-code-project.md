---
title: "Comment : configurer l’analyse du Code pour un projet de Code managé | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.codeanalysis.propertypages.csvb
helpviewer_keywords:
- code analysis, selecting rule sets
- code analysis, rule sets
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: 575b81e9c213e4025cd38921ad467869686d867c
ms.sourcegitcommit: d6327b978661c0a745bf4b59f32d8171607803a3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2018
---
# <a name="how-to-configure-code-analysis-for-a-managed-code-project"></a>Procédure : configurer l’analyse du code pour un projet de code managé

Dans Visual Studio, vous pouvez choisir parmi une liste de l’analyse du code *ensembles de règles* à appliquer à un projet de code managé. L’ensemble de règles par défaut est de règles Microsoft minimales recommandées. Vous pouvez appliquer un autre ensemble de règles à un projet ou à tous les projets dans une solution.  
  
> [!NOTE]
> Pour plus d’informations sur la configuration d’un ensemble de règles pour les applications Web ASP.NET, consultez [Comment : configurer l’analyse du Code pour une Application Web ASP.NET](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md).  
  
## <a name="to-configure-a-rule-set-for-a-net-framework-project"></a>Pour configurer un ensemble de règles pour un projet .NET Framework  
  
1.  Dans **l’Explorateur de solutions**, cliquez sur le projet.  
  
2.  Sur le **analyser** menu, cliquez sur **configurer l’analyse du Code pour** *nom_projet*.  
  
3.  Dans le **Configuration** et **plateforme** listes, cliquez sur la build configuration et la plateforme cible.  
  
4.  Pour exécuter l’analyse du code chaque fois que le projet est généré à l’aide de la configuration sélectionnée, sélectionnez le **activer l’analyse du Code sur la Build** case à cocher. Vous pouvez également exécuter manuellement l’analyse du code en ouvrant le **analyser** menu et en choisissant ** Exécuter l’analyse du Code sur * *** ProjectName.  
  
5.  Par défaut, l'analyse du code ne signale pas d'avertissements pour le code généré automatiquement par les outils externes. Pour afficher les avertissements du code généré, désactivez le **supprimer les résultats du code généré** case à cocher.  
  
    > [!NOTE]
    > Cette option ne supprime pas les erreurs d'analyse du code et les avertissements du code généré qui apparaissent dans les formulaires et les modèles. Vous pouvez afficher et mettre à jour le code source pour un formulaire ou un modèle, sans que celle-ci n’est remplacé.
  
6.  Dans le **exécuter cet ensemble de règles** liste, effectuez l’une des opérations suivantes :  
  
    -   Cliquez sur l’ensemble de règles que vous souhaitez utiliser.  
  
    -   Cliquez sur  **\<Parcourir... >** pour spécifier une règle personnalisée existante du jeu qui n’est pas dans la liste.  
  
    -   Définissez un ensemble de règles personnalisé.  
  
         Pour plus d’informations, consultez [création d’ensembles de règles personnalisés](../code-quality/creating-custom-code-analysis-rule-sets.md).  
  
## <a name="see-also"></a>Voir aussi

[Procédure pas à pas : configuration et utilisation d’un ensemble de règles personnalisé](../code-quality/walkthrough-configuring-and-using-a-custom-rule-set.md)