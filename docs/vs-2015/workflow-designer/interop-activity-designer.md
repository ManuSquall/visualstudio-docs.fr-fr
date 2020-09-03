---
title: Concepteur d’activités Interop | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Interop.UI
ms.assetid: 800a3403-ba86-41c4-8de1-c4fee9703eb1
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 994d7776ff7c32f8dd309e667597550637ef2b5a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72659037"
---
# <a name="interop-activity-designer"></a>Concepteur d'activités Interop
Le concepteur d’activités **Interop** est utilisé pour créer et configurer une <xref:System.Activities.Statements.Interop> activité.

## <a name="the-interop-activity"></a>Activité Interop
 L'activité <xref:System.Activities.Statements.Interop> gère l'exécution des types qui dérivent de <xref:System.Workflow.ComponentModel.Activity?displayProperty=fullName> dans un workflow.

### <a name="using-the-interop-activity-designer"></a>Utilisation du Concepteur d'activités Interop
 Le concepteur d’activités **Interop** se trouve dans la catégorie **migration** de la **boîte à outils**, accessible en cliquant sur l’onglet **boîte à outils** (ou en sélectionnant **boîte à outils** dans le menu **affichage** , ou encore en appuyant sur CTRL + ALT + X).

 La catégorie de [migration](../workflow-designer/migration-activity-designers.md) qui contient l' <xref:System.Activities.Statements.Interop> activité s’affiche uniquement dans la **boîte à outils** si votre projet cible le complet [!INCLUDE[netfx40_long](../includes/netfx40-long-md.md)] .

 Pour les projets C#, vous pouvez recibler le projet pour utiliser le complet [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] en cliquant avec le bouton droit sur le projet dans le **Explorateur de solutions** et en sélectionnant **Propriétés**. Sous l’onglet **application** , sélectionnez l’option **NET Framework 4** dans la version cible de **.NET Framework**. Sélectionnez le bouton **Oui** dans la boîte de dialogue de **modification du Framework cible** qui s’affiche, vous demandant de confirmer cette modification.

 Pour les projets VB, vous pouvez recibler le projet pour utiliser le complet [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] en cliquant avec le bouton droit sur le projet dans la **Explorateur de solutions** et en sélectionnant **Propriétés**. Sous l’onglet **compiler** , cliquez sur le bouton **Options avancées de compilation** . Sélectionnez **.NET Framework 4** dans la **liste Framework cible** , puis cliquez sur **OK**. Cliquez sur le bouton **Oui** dans la boîte de dialogue de **modification du Framework cible** qui s’affiche, vous demandant de confirmer cette modification.

 Le concepteur d’activités **Interop** peut être déplacé de la **boîte à outils** et déposé dans l’aire de conception [!INCLUDE[wfd2](../includes/wfd2-md.md)] , là où les activités sont généralement placées, par exemple dans un <xref:System.Activities.Statements.Sequence> . Cette opération crée une <xref:System.Activities.Statements.Interop> activité avec un **DisplayName** par défaut de l’interopérabilité. La <xref:System.Activities.Activity.DisplayName%2A> propriété peut être modifiée dans l’en-tête du concepteur d’activités **Interop** ou dans la zone **DisplayName** de la grille des propriétés.

 Cliquez sur le **bouton Cliquer pour parcourir..** . texte dans la zone **ActivityType** , sur le concepteur d’activités **Interop**  ou dans la grille des propriétés, pour afficher la boîte de dialogue **Parcourir et sélectionner un type .net** . Seuls les types d'activités de workflow 3.0 ou 3.5 sont affichés (autrement dit, les types dérivés de <xref:System.Workflow.ComponentModel.Activity>). [!INCLUDE[crabout](../includes/crabout-md.md)] l’utilisation de cette zone pour spécifier un type, consultez la rubrique [Parcourir et sélectionner un type .net de](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box.md) la boîte de dialogue.

### <a name="the-interop-properties"></a>Propriétés d'Interop
 Le tableau suivant présente les propriétés de <xref:System.Activities.Statements.Interop> et décrit comment elles sont utilisées dans le concepteur. Ces propriétés peuvent être modifiées dans la grille des propriétés ou dans l'aire de conception [!INCLUDE[wfd2](../includes/wfd2-md.md)].

|Nom de la propriété|Obligatoire|Usage|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|Faux|Nom convivial de l'activité <xref:System.Activities.Statements.Interop>. La valeur par défaut est Interop. Bien que le nom complet ne soit pas strictement obligatoire, la meilleure pratique consiste à l'utiliser.|
|<xref:System.Activities.Statements.Interop.ActivityType%2A>|Vrai|Spécifie le type de l'activité contenue par l'activité <xref:System.Activities.Statements.Interop>. Le type spécifié doit dériver d'<xref:System.Workflow.ComponentModel.Activity>.|

## <a name="see-also"></a>Voir aussi
 [Migration](../workflow-designer/migration-activity-designers.md)