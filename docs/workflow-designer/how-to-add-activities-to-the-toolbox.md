---
title: "Proc&#233;dure&#160;: ajouter des activit&#233;s &#224; la bo&#238;te &#224; outils | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: b3a8a785-5928-457a-8a50-30267e29503d
caps.latest.revision: 16
caps.handback.revision: 16
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Proc&#233;dure&#160;: ajouter des activit&#233;s &#224; la bo&#238;te &#224; outils
Il existe différentes façons d'ajouter des activités à la **Boîte à outils**.Vous pouvez les ajouter à partir de votre projet en cours, les référencer à partir d'un autre projet ou les référencer à partir d'un autre assembly.  
  
### Pour ajouter une activité à partir de votre projet en cours  
  
1.  Ajoutez une nouvelle activité personnalisée à votre projet de workflow actif.[!INCLUDE[crabout](../test/includes/crabout_md.md)] l'ajout d'une nouvelle activité personnalisée à votre projet, consultez [Comment : ajouter un nouvel élément à un projet de workflow](../Topic/How%20to:%20Add%20a%20New%20Item%20to%20a%20Workflow%20Project.md).  
  
2.  Ajoutez une logique personnalisée à votre activité.  
  
3.  Générez le projet.Si la build est réussie, une nouvelle catégorie, nommée « \<*project name*\> » s'affiche dans la **Boîte à outils** avec l'activité personnalisée incluse dans cette catégorie.  
  
    > [!NOTE]
    >  Si la boîte à outils est réinitialisée, des activités personnalisées sont supprimées, même si la solution est générée à nouveau.Pour remplir de nouveau la boîte à outils avec des activités personnalisées, redémarrez [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] après que la boîte à outils a été réinitialisée.  
  
    > [!NOTE]
    >  La boîte à outils ne peut afficher qu'une activité d'un nom donné.Si deux activités de différents assemblys ont le même nom de classe, une seule s'affiche.  
  
    > [!NOTE]
    >  Le domaine d'application est partagé entre des instances de l'éditeur ; si des variables statiques sont utilisée, elles sont également partagées par les instances de l'éditeur.S'il ne s'agit pas du comportement souhaité, un service doit être utilisé pour assurer le suivi des instances variables.Consultez [Utilisation du contexte d'édition ModelItem](../Topic/Using%20the%20ModelItem%20Editing%20Context.md) pour plus d'informations sur l'utilisation des services dans le concepteur.  
  
### Pour ajouter une activité à partir d'un autre projet  
  
1.  Ouvrez une solution qui contient au moins un projet de workflow, ainsi qu'un projet de bibliothèque d'activités personnalisées ou un autre projet de workflow qui définit une activité personnalisée.  
  
2.  Générez les deux projets.Si la build est réussie, une nouvelle catégorie, nommée « \<*project name*\> » s'affiche dans la **Boîte à outils** avec l'activité personnalisée incluse dans cette catégorie.  
  
### Pour ajouter une activité à la boîte à outils à partir d'un assembly  
  
1.  Ouvrez une solution de workflow.  
  
2.  Dans le menu **Outils**, sélectionnez **Choisir des éléments de boîte à outils**.  
  
3.  Dans la boîte de dialogue **Choisir des éléments de boîte à outils**, sélectionnez l'onglet **Composants System.Activities**, puis cliquez sur **Parcourir** pour naviguer jusqu'à l'assembly qui contient l'activité personnalisée à ajouter.  
  
4.  Sélectionnez l'assembly, puis cliquez sur **OK**.Le composant d'activité personnalisée est ajouté à la liste de composants et est automatiquement sélectionné.  
  
    1.  Cliquez sur **OK** pour fermer la boîte de dialogue.  
  
5.  Pour afficher la boîte à outils, sélectionnez **Boîte à outils** dans le menu **Affichage**.  
  
6.  L'activité personnalisée s'affiche dans la **Boîte à outils** sous la catégorie qui avait le focus avant l'ajout de l'élément.Par exemple, si la catégorie **Général** était sélectionnée dans la **Boîte à outils** avant l'ajout de l'élément de boîte à outils, l'activité apparaît sous la catégorie **Général**.  
  
## Voir aussi  
 [Utilisation de Workflow Designer](../workflow-designer/using-the-workflow-designer.md)