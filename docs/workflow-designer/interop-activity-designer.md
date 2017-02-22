---
title: "Concepteur d&#39;activit&#233;s Interop | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "System.Activities.Statements.Interop.UI"
ms.assetid: 800a3403-ba86-41c4-8de1-c4fee9703eb1
caps.latest.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# Concepteur d&#39;activit&#233;s Interop
Le concepteur d'activités **Interop** permet de créer et configurer une activité <xref:System.Activities.Statements.Interop>.  
  
## Activité Interop  
 L'activité <xref:System.Activities.Statements.Interop> gère l'exécution des types qui dérivent de <xref:System.Workflow.ComponentModel.Activity?displayProperty=fullName> dans un workflow.  
  
### Utilisation du Concepteur d'activités Interop  
 Le concepteur d'activités **Interop** se trouve dans la catégorie **Migration** de la **Boîte à outils**, accessible en cliquant sur l'onglet **Boîte à outils** \(ou en sélectionnant **Barre d'outils** dans le menu **Affichage**, ou encore en appuyant sur CTRL\+ALT\+X\).  
  
 La catégorie [Migration](../workflow-designer/migration-activity-designers.md) qui contient l'activité <xref:System.Activities.Statements.Interop> ne s'affiche dans la **Boîte à outils** que si votre projet cible le [!INCLUDE[netfx40_long](../workflow-designer/includes/netfx40_long_md.md)] complet.  
  
 Pour les projets C\#, vous pouvez recibler le projet pour utiliser le [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] complet en cliquant avec le bouton droit sur le projet dans l'**Explorateur de solutions** et en sélectionnant **Propriétés**.Sous l'onglet **Application**, sélectionnez l'option **.NET Framework 4** dans **Framework cible**.Sélectionnez le bouton **Oui** dans la boîte de dialogue **Modification du Framework cible** qui s'affiche, vous demandant de confirmer cette modification.  
  
 Pour les projets VB, vous pouvez recibler le projet pour utiliser le [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] complet en cliquant avec le bouton droit sur le projet dans l'**Explorateur de solutions** et en sélectionnant **Propriétés**.Sous l'onglet **Compiler**, cliquez sur le bouton **Options avancées de compilation**.Sélectionnez **.Net Framework 4** dans la liste **Framework cible**, puis cliquez sur **OK**.Cliquez sur le bouton **Oui** dans la boîte de dialogue **Modification du Framework cible** qui s'affiche, vous demandant de confirmer cette modification.  
  
 Le concepteur d'activités **Interop** peut être déplacé de la **Boîte à outils** et déposé dans l'aire de conception [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], là où les activités sont généralement placées, par exemple dans un objet <xref:System.Activities.Statements.Sequence>.Cette action crée une activité <xref:System.Activities.Statements.Interop> avec Interop comme **DisplayName** par défaut.La propriété <xref:System.Activities.Activity.DisplayName%2A> peut être modifiée dans l'en\-tête du concepteur d'activités **Interop** ou dans la zone **DisplayName** de la grille des propriétés.  
  
 Cliquez sur le texte **Cliquer pour parcourir** dans la zone **ActivityType**, sur le concepteur d'activités **Interop** ou dans la grille des propriétés, pour afficher la boîte de dialogue **Rechercher et sélectionner un type .Net**.Seuls les types d'activités de workflow 3.0 ou 3.5 sont affichés \(autrement dit, les types dérivés de <xref:System.Workflow.ComponentModel.Activity>\).[!INCLUDE[crabout](../test/includes/crabout_md.md)] l'utilisation de cette zone pour spécifier un type, consultez la rubrique [Rechercher et sélectionner un type .NET, boîte de dialogue](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box.md).  
  
### Propriétés d'Interop  
 Le tableau suivant présente les propriétés de <xref:System.Activities.Statements.Interop> et décrit comment elles sont utilisées dans le concepteur.Ces propriétés peuvent être modifiées dans la grille des propriétés ou dans l'aire de conception [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].  
  
|Nom de la propriété|Valeur requise|Utilisation|  
|-------------------------|--------------------|-----------------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nom convivial de l'activité <xref:System.Activities.Statements.Interop>.La valeur par défaut est Interop.Bien que le nom complet ne soit pas strictement obligatoire, la meilleure pratique consiste à l'utiliser.|  
|<xref:System.Activities.Statements.Interop.ActivityType%2A>|True|Spécifie le type de l'activité contenue par l'activité <xref:System.Activities.Statements.Interop>.Le type spécifié doit dériver d'<xref:System.Workflow.ComponentModel.Activity>.|  
  
## Voir aussi  
 [Migration](../workflow-designer/migration-activity-designers.md)