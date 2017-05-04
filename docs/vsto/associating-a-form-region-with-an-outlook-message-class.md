---
title: "Association d&#39;une zone de formulaire &#224; une classe de message Outlook | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VSTO.NewFormRegionWizard.InvalidMessageClassName"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "zones de formulaire (développement Office dans Visual Studio), classes de message"
  - "FormRegionMessageClassAttribute"
ms.assetid: e2db8d61-fd5f-4059-beec-33b66970f520
caps.latest.revision: 43
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 42
---
# Association d&#39;une zone de formulaire &#224; une classe de message Outlook
  Vous pouvez spécifier quels éléments de Microsoft Office Outlook affichent une zone de formulaire en associant la zone à la classe de message de chaque élément.  Par exemple, si vous souhaitez ajouter une zone de formulaire au bas d'un élément de messagerie, vous pouvez associer la zone à la classe de message IPM.Note.  
  
 Pour associer une zone de formulaire à une classe de message, spécifiez le nom de classe dans l'Assistant **Nouvelle zone de formulaire Outlook** ou appliquez un attribut à la classe de fabrique de zones de formulaire.  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## Fonctionnement des classes de message Outlook  
 Une classe de message Outlook identifie un type d'élément Outlook.  Le tableau suivant répertorie les huit types d'éléments standard et les noms de classe de message correspondants.  
  
|Type d'élément Outlook|Nom de classe de message|  
|----------------------------|------------------------------|  
|AppointmentItem|IPM.Appointment|  
|ContactItem|IPM.Contact|  
|DistListItem|IPM.DistList|  
|JournalItem|IPM.Activity|  
|MailItem|IPM.Note|  
|PostItem|IPM.Post ou IPM.Post.RSS|  
|TaskItem|IPM.Task|  
  
 Vous pouvez également spécifier les noms de classes de message personnalisées.  Les classes de message personnalisées identifient des formulaires personnalisés que vous définissez dans Outlook.  
  
> [!NOTE]  
>  Pour les zones de formulaire de remplacement et de remplacement global, vous pouvez spécifier un nouveau nom de classe de message personnalisée.  Il n'est pas nécessaire d'utiliser le nom de classe de message d'un formulaire personnalisé existant.  Le nom de la classe de message personnalisée doit être unique.  Pour vous assurer que le nom est unique, vous pouvez utiliser une convention d'affectation de noms respectant le schéma suivant : \<*NomClasseMessageStandard*\>.\<*Société*\>.\<*NomClasseMessage*\> \(par exemple: IPM.Note.Contoso.MyMessageClass\).  
  
## Association d'une zone de formulaire à une classe de message Outlook  
 Il existe deux moyens d'associer une zone de formulaire à une classe de message :  
  
-   À l'aide de l'Assistant **Nouvelle zone de formulaire Outlook**.  
  
-   En appliquant des attributs de classe.  
  
### Utilisation de l'Assistant Nouvelle zone de formulaire Outlook  
 Sur la dernière page de l'Assistant **Nouvelle zone de formulaire Outlook**, vous pouvez sélectionner des classes de message standard et saisir les noms de classes de message personnalisées à associer à la zone de formulaire.  
  
 Les classes de message standard ne sont pas disponibles si la zone de formulaire est destinée à remplacer l'ensemble du formulaire ou la page par défaut d'un formulaire.  Vous pouvez spécifier des noms de classe de message standard uniquement pour les formulaires qui ajoutent une nouvelle page à un formulaire ou qui sont ajoutés à la fin d'un formulaire.  Pour plus d’informations, consultez [Comment : ajouter une zone de formulaire à un projet de complément Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).  
  
 Pour inclure une ou plusieurs classes de message personnalisées, saisissez leur nom dans la zone **Quelles classes de message personnalisées afficheront cette zone de formulaire ?**  
  
 Les noms saisis doivent respecter les recommandations suivantes :  
  
-   Utilisez le nom de classe de message qualifié complet \(par exemple, « IPM.Note.Contoso »\).  
  
-   Séparez les noms de classe de message par des points\-virgules.  
  
-   N'incluez pas de classes de message Outlook standard, telles que « IPM.Note » ou « IPM.Contact ».  Vous pouvez uniquement inclure des classes de message personnalisées telles que « IPM.Note.Contoso ».  
  
-   Ne spécifiez pas la classe de message de base seule \(par exemple : « IPM »\).  
  
-   Les noms de classe de message ne doivent pas dépasser 256 caractères.  
  
 L'Assistant **Nouvelle zone de formulaire Outlook** valide le format de votre saisie lorsque vous cliquez sur **Terminer**.  
  
> [!NOTE]  
>  L'Assistant **Nouvelle zone de formulaire Outlook** ne vérifie pas que les noms de classe de message fournis sont corrects ou valides.  
  
 Lorsque vous avez terminé, l'Assistant **Nouvelle zone de formulaire Outlook** applique à la classe de zone du formulaire des attributs qui contiennent les noms de classe de message spécifiés.  Vous pouvez également appliquer ces attributs manuellement.  
  
### Application d'attributs de classe  
 Vous pouvez associer une zone de formulaire à une classe de message Outlook après avoir exécuté l'Assistant **Nouvelle zone de formulaire Outlook**.  Pour cela, appliquez des attributs à la classe de fabrique de zones de formulaire.  
  
 L'exemple suivant affiche deux attributs <xref:Microsoft.Office.Tools.Outlook.FormRegionMessageClassAttribute> appliqués à une classe de fabrique de zones de formulaire nommée `myFormRegion`.  Le premier attribut associe la zone de formulaire à une classe de message standard pour un formulaire de message électronique.  Le deuxième associe la zone de formulaire à une classe de message personnalisée nommée `IPM.Task.Contoso`.  
  
 [!code-csharp[Trin_Outlook_FR_Attributes#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Outlook_FR_Attributes/CS/FormRegion1.cs#1)]
 [!code-vb[Trin_Outlook_FR_Attributes#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Outlook_FR_Attributes/VB/FormRegion1.vb#1)]  
  
 Les attributs doivent respecter les recommandations suivantes :  
  
-   Pour les classes de message personnalisées, utilisez le nom de classe de message qualifié complet \(par exemple, « IPM.Note.Contoso »\).  
  
-   Ne spécifiez pas la classe de message de base seule \(par exemple : « IPM »\).  
  
-   Les noms de classe de message ne doivent pas dépasser 256 caractères.  
  
-   N'incluez pas les noms de classes de message standard si la zone de formulaire remplace l'ensemble du formulaire ou la page par défaut d'un formulaire.  Vous pouvez spécifier des noms de classe de message standard uniquement pour les formulaires qui ajoutent une nouvelle page à un formulaire ou qui sont ajoutés à la fin d'un formulaire.  Pour plus d’informations, consultez [Comment : ajouter une zone de formulaire à un projet de complément Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).  
  
 Visual Studio valide le format des noms de classes de message lorsque vous générez le projet.  
  
> [!NOTE]  
>  Visual Studio ne vérifie pas que les noms de classes de message que vous fournissez sont corrects ou valides.  
  
## Voir aussi  
 [Accès à une zone de formulaire au moment de l'exécution](../vsto/accessing-a-form-region-at-run-time.md)   
 [Création de zones de formulaire Outlook](../vsto/creating-outlook-form-regions.md)   
 [Procédure pas à pas : conception d'une zone de formulaire Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Directives pour la création de zones de formulaire Outlook](../vsto/guidelines-for-creating-outlook-form-regions.md)   
 [Sur le nom et la classe de message de formulaire](HV01044315)   
 [comment les formulaires Outlook et les éléments fonctionnent ensemble](HV01044298)  
  
  