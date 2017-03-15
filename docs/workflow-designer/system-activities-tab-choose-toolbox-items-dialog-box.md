---
title: "Onglet System.Activities de la bo&#238;te de dialogue Choisir des &#233;l&#233;ments de bo&#238;te &#224; outils | Microsoft Docs"
ms.custom: ""
ms.date: "09/02/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "VS.CHOOSEITEMS.SYSTEM.ACTIVITIES_COMPONENTS"
  - "VS.CHOOSEITEMS.SYSTEM.ACTIVITIES COMPONENTS"
ms.assetid: cef390cd-eeda-42e6-9d2e-18c8325a4f06
caps.latest.revision: 5
caps.handback.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Onglet System.Activities de la bo&#238;te de dialogue Choisir des &#233;l&#233;ments de bo&#238;te &#224; outils
Cet onglet de la boîte de dialogue **Choisir des éléments de boîte à outils** affiche une liste d'activités, de modèles et d'éléments [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] disponibles.Pour afficher la liste, sélectionnez **Choisir des éléments de boîte à outils** dans le menu **Outils** ou cliquez avec le bouton droit sur la **boîte à outils** et sélectionnez **Choisir les éléments** pour afficher la boîte de dialogue **Choisir des éléments de boîte à outils**, puis sélectionnez l'onglet **System.Activities**.La liste affiche automatiquement les activités de workflow des assemblys System.Activities, System.ServiceModel.Activities et System.Activities.Core.Presentation ; toutefois, seules les activités fournies par le système indiquées et les activités ajoutées via d'autres assemblys affichés dans la **boîte à outils** sont sélectionnées par défaut.Les activités récemment ajoutées sont sélectionnées automatiquement et figurent dans la **boîte à outils** lorsque vous cliquez sur **OK** dans la boîte de dialogue.De plus, ces éléments s'affichent dans la **boîte à outils** sous une nouvelle catégorie qui correspond à l'espace de noms dans lequel réside l'activité\/l'élément\/le modèle.  
  
> [!WARNING]
>  Si vous essayez d'ajouter un assembly qui ne contient pas d'activités de workflow, un boîte de dialogue d'erreur s'affiche pour expliquer que l'assembly ne contient pas d'activités.  
  
 Étant donné que cette boîte de dialogue ne dépend pas du projet, l'onglet **System.Activities** continue de s'afficher dans le type XAML autonome ou dans un type de projet autre qu'un workflow.  
  
 Le filtrage s'effectue sous chaque onglet.Autrement dit, il n'est pas possible d'ajouter des activités de workflow via l'onglet **Composant .NET**.Les activités doivent être ajoutées via l'onglet **System.Activities** lui\-même.  
  
 Vous pouvez désactiver tous les éléments que vous ne souhaitez pas afficher dans la **boîte à outils** en utilisant l'onglet de cette boîte de dialogue, ou bien en sélectionnant l'option **Supprimer** dans le menu contextuel de la **boîte à outils**. Notez que la suppression de la référence à un assembly ne supprime pas l'élément de la **boîte à outils**.  
  
 L'instanciation de l'activité, en la faisant glisser vers le concepteur, ajoute automatiquement l'assembly qui contient l'élément à la liste des assemblys référencés.Par ailleurs, si l'activité fait référence à un assembly C, elle n'ajoute pas C à la liste des assemblys référencés.L'assembly C doit se trouver dans le GAC ou le même répertoire que l'activité B.Dans le cas autonome, l'assembly doit figurer dans le GAC ou dans les chemins d'accès d'exploration de Visual Studio.Vous ne pouvez faire glisser l'activité sur l'aire du concepteur de workflow qu'à ce moment\-là.  
  
 Les paramètres de la **boîte à outils** sont enregistrés par défaut en tant qu'options utilisateur. Par conséquent, lors de sa prochaine ouverture, la **boîte à outils** affichera votre liste personnalisée d'activités de workflow.L'opération présente l'effet secondaire suivant : si vous avez ajouté vos éléments de domaine spécifiques à la **boîte à outils** par le biais de la boîte de dialogue **Choisir des éléments de boîte à outils**, ces éléments continuent de s'afficher lorsque vous utilisez une application console de workflow.Si vous ne souhaitez pas les afficher, supprimez\-les à l'aide du menu contextuel ou désactivez\-les via la boîte de dialogue **Choisir des éléments de boîte à outils** comme indiqué précédemment.  
  
 Les colonnes dans cette boîte de dialogue contiennent les informations suivantes :  
  
 Nom  
 Répertorie les noms des activités de workflow enregistrées actuellement sur votre ordinateur local.  
  
 Espace de noms  
 Affiche la hiérarchie de l'espace de noms de la bibliothèque de classes .NET Framework qui définit la structure de l'activité.  
  
 Nom de l'assembly  
 Affiche le nom et la version de l'assembly .NET Framework qui contient l'activité.  
  
 Répertoire  
 Affiche l'emplacement de l'assembly .NET Framework qui contient les activités de workflow.L'emplacement par défaut de tous les assemblys est le Global Assembly Cache.  
  
 Pour trier la liste des composants, cliquez sur un en\-tête de colonne.