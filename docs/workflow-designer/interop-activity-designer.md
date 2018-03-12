---
title: "Concepteur d’activités Interop | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Interop.UI
ms.assetid: 800a3403-ba86-41c4-8de1-c4fee9703eb1
caps.latest.revision: 
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload:
- multiple
ms.openlocfilehash: 726bc2fa995d819b0e554e11439c85f9fdf19243
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="interop-activity-designer"></a>Concepteur d'activités Interop
Le **Interop** ActivityDesigner est utilisé pour créer et configurer un <xref:System.Activities.Statements.Interop> activité.  
  
## <a name="the-interop-activity"></a>Activité Interop  
 L'activité <xref:System.Activities.Statements.Interop> gère l'exécution des types qui dérivent de <xref:System.Workflow.ComponentModel.Activity?displayProperty=fullName> dans un workflow.  
  
### <a name="using-the-interop-activity-designer"></a>Utilisation du Concepteur d'activités Interop  
 Le **Interop** Concepteur d’activités peut être trouvé dans le **Migration** catégorie de la **boîte à outils**, qui est accessible en cliquant sur les **boîte à outils**onglet (ou bien, sélectionnez **boîte à outils** à partir de la **vue** menu ou CTRL + ALT + X.)  
  
 Le [Migration](../workflow-designer/migration-activity-designers.md) catégorie contenant le <xref:System.Activities.Statements.Interop> activité s’affiche uniquement dans le **boîte à outils** si votre projet cible la version complète [!INCLUDE[netfx40_long](../workflow-designer/includes/netfx40_long_md.md)].  
  
 Pour les projets c#, vous pouvez recibler le projet pour utiliser la version complète [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] en double-cliquant sur le projet dans le **l’Explorateur de solutions** et en sélectionnant **propriétés**. Sur le **Application** onglet, sélectionnez le **NET Framework 4** option dans le **framework cible**. Sélectionnez le **Oui** situé dans le **modification du Framework cible** dialogue qui s’affiche vous invitant à confirmer cette modification.  
  
 Pour les projets Visual Basic, vous pouvez recibler le projet pour utiliser la version complète [!INCLUDE[netfx40_short](../workflow-designer/includes/netfx40_short_md.md)] en cliquant sur le projet dans le **l’Explorateur de solutions** et en sélectionnant **propriétés**. Sur le **compiler** , cliquez sur le **Options avancées de compilation** bouton. Sélectionnez **.Net Framework 4** à partir de la **liste de framework cible** puis cliquez sur **OK**. Cliquez sur le **Oui** situé dans le **modification du Framework cible** dialogue qui s’affiche vous invitant à confirmer cette modification.  
  
 Le **Interop** Concepteur d’activités peut être déplacé de la **boîte à outils** et déposé dans le [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] surface, là où les activités sont généralement placées, par exemple dans un <xref:System.Activities.Statements.Sequence>. Cette opération crée un <xref:System.Activities.Statements.Interop> activité avec une valeur par défaut **DisplayName** d’interopérabilité. Le <xref:System.Activities.Activity.DisplayName%2A> peuvent être modifiées dans l’en-tête de la **Interop** Concepteur d’activités ou dans le **DisplayName** zone de la grille des propriétés.  
  
 Cliquez sur le **cliquez pour parcourir...**  texte dans le **ActivityType** zone, soit sur le **Interop** activité concepteur ou dans la grille des propriétés, pour afficher le **rechercher et sélectionner un .net Type** boîte de dialogue. Seuls les types d'activités de workflow 3.0 ou 3.5 sont affichés (autrement dit, les types dérivés de <xref:System.Workflow.ComponentModel.Activity>). [!INCLUDE[crabout](../test/includes/crabout_md.md)]à l’aide de cette case pour spécifier un type, consultez la [rechercher et sélectionner un Type .NET, boîte de dialogue](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box.md) rubrique.  
  
### <a name="the-interop-properties"></a>Propriétés d'Interop  
 Le tableau suivant présente les propriétés de <xref:System.Activities.Statements.Interop> et décrit comment elles sont utilisées dans le concepteur. Ces propriétés peuvent être modifiées dans la grille des propriétés ou dans l'aire de conception [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)].  
  
|Nom de la propriété|Obligatoire|Utilisation|  
|-------------------|--------------|-----------|  
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nom convivial de l'activité <xref:System.Activities.Statements.Interop>. La valeur par défaut est Interop. Bien que le nom complet ne soit pas strictement obligatoire, la meilleure pratique consiste à l'utiliser.|  
|<xref:System.Activities.Statements.Interop.ActivityType%2A>|True|Spécifie le type de l'activité contenue par l'activité <xref:System.Activities.Statements.Interop>. Le type spécifié doit dériver d'<xref:System.Workflow.ComponentModel.Activity>.|  
  
## <a name="see-also"></a>Voir aussi  
 [Migration](../workflow-designer/migration-activity-designers.md)