---
title: "Rechercher et s&#233;lectionner un type .NET, bo&#238;te de dialogue | Microsoft Docs"
ms.custom: ""
ms.date: "09/02/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "TypeBrowser.UI"
  - "ActivityTypeResolver.UI"
ms.assetid: 864b60b6-a070-4e5c-aa5b-a25341b57ea6
caps.latest.revision: 13
caps.handback.revision: 13
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
---
# Rechercher et s&#233;lectionner un type .NET, bo&#238;te de dialogue
Dans la fenêtre **Propriétés**, les boîtes de dialogue ou les concepteurs, tels que le concepteur de variables, lorsque vous sélectionnez **Rechercher des types** dans une liste de types de données, la boîte de dialogue **Parcourir et sélectionner un type .NET** \(appelée sous forme abrégée « Explorateur de types »\) s'affiche.Cette boîte de dialogue vous permet de choisir un type dans une arborescence d'assemblys et de projets.  
  
 Elle est employée dans plusieurs scénarios utilisateur, notamment les suivants :  
  
-   lors de la définition du type d'une variable ou d'argument ;  
  
-   lors de la sélection d'un type pour une activité générique ;  
  
-   lors de l'ajout d'un catch sur l'activité <xref:System.Activities.Statements.TryCatch>.  
  
> [!NOTE]
>  L'explorateur de types peut afficher des types de tableau en escalier Visual Basic, mais pas des types de tableau multidimensionnel.Consultez [Tableaux en escalier](http://go.microsoft.com/fwlink/?LinkId=195226) et [Tableaux multidimensionnels](http://go.microsoft.com/fwlink/?LinkId=195227) pour plus de détails.  
  
## Sélection d'un type valeur ou référence dans l'Explorateur de types  
  
#### Pour sélectionner un type valeur ou référence dans l'Explorateur de types  
  
1.  Dans la zone **Nom de type**, entrez le nom du type à utiliser.  
  
2.  Effectuez l'une des opérations suivantes :  
  
    -   Une fois que le nom du type que vous souhaitez utiliser s'affiche dans l'arborescence, dans la zone **Nom de type**, double\-cliquez sur le type pour le sélectionner.  
  
    -   Tapez un nombre de caractères suffisant dans la zone **Nom de type** afin d'identifier de manière unique le type à utiliser, puis appuyez sur Entrée pour sélectionner le type.  
  
#### Pour sélectionner un type générique dans l'Explorateur de types  
  
1.  Dans la zone **Nom de type**, tapez le nom du type à utiliser.  
  
2.  Une fois que le nom du type que vous souhaitez utiliser s'affiche dans l'arborescence, dans la zone **Nom de type**, cliquez sur le type pour le sélectionner et faire apparaître des zones de liste déroulante.  
  
     Sélectionnez le type souhaité pour fermer le type générique dans les zones de liste déroulante, puis cliquez sur **OK**.  
  
## Types affichés dans l'Explorateur de types  
 Les types affichés dans l'Explorateur de types peuvent varier selon le mode de lancement de l'Explorateur de types.Si l'Explorateur de types a été lancé à partir d'un projet de flux de travail dans **vs2010**, par défaut, tous les types dans les assemblys et les projets référencés sont affichés.Si l'Explorateur de types a été lancé en dehors d'un système de projet **vs2010** \(tel que dans une application de flux de travail réhébergée ou dans un fichier de flux de travail autonome\), les types de tous les assemblys chargés dans le domaine d'application sont affichés par défaut.  
  
 Les types dans l'Explorateur de types peuvent être filtrés par développeurs de concepteurs d'activités.Pour une activité donnée, seul un sous\-ensemble des types peut s'afficher.Par exemple, dans l'activité <xref:System.Activities.Statements.TryCatch>, seuls les types dérivés de <xref:System.Exception> sont affichés dans l'Explorateur de types.  
  
## Filtrage des résultats de la recherche dans l'Explorateur de types  
 Plus vous tapez de caractères pour rechercher une correspondance, plus la liste des types dans la zone **Nom de type** se raccourcit.Seuls les types dont le nom complet ou le nom court commence par la chaîne tapée s'affichent dans la liste filtrée.  
  
 Par exemple :  
  
1.  Taper **Operation** permet de trouver <xref:System.OperationCanceledException> mais pas <xref:System.InvalidOperationException>.Pour trouver <xref:System.InvalidOperationException>, commencez par taper System.I ou Invalid.  
  
2.  Taper **Generic** permet de trouver <xref:System.GenericUriParser>, mais pas les types dans l'espace de noms <xref:System.Collections.Generic>.Pour rechercher les types dans l'espace de noms <xref:System.Collections.Generic>, tapez le nom complet de l'espace de noms.  
  
## Sélectionner un contrat de service à l'aide de la boîte de dialogue de l'Explorateur de types  
 Lorsque vous sélectionnez un type de contrat de service, l'Explorateur de types affiche uniquement les types possédant l'attribut <xref:System.ServiceModel.ServiceContractAttribute>.  
  
## Voir aussi  
 [Utilisation des concepteurs d'activités](../workflow-designer/using-the-activity-designers.md)