---
title: Concepteur de flux de travail - Concepteur d’activités Interop
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
f1_keywords:
- System.Activities.Statements.Interop.UI
ms.assetid: 800a3403-ba86-41c4-8de1-c4fee9703eb1
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bb9eb5e8b2dbca57d28f9d350b769b5eaa90e2b2
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31979072"
---
# <a name="interop-activity-designer"></a>Concepteur d'activités Interop

Le **Interop** ActivityDesigner est utilisé pour créer et configurer un <xref:System.Activities.Statements.Interop> activité.

## <a name="the-interop-activity"></a>Activité Interop
 L'activité <xref:System.Activities.Statements.Interop> gère l'exécution des types qui dérivent de <xref:System.Workflow.ComponentModel.Activity?displayProperty=fullName> dans un workflow.

### <a name="using-the-interop-activity-designer"></a>Utilisation du Concepteur d'activités Interop
 Le **Interop** Concepteur d’activités peut être trouvé dans le **Migration** catégorie de la **boîte à outils**, qui est accessible en cliquant sur les **boîte à outils**onglet (ou bien, sélectionnez **boîte à outils** à partir de la **vue** menu ou CTRL + ALT + X.)

 Le [Migration](../workflow-designer/migration-activity-designers.md) catégorie contenant le <xref:System.Activities.Statements.Interop> activité s’affiche uniquement dans le **boîte à outils** si votre projet cible le .NET Framework 4 complet.

 Pour les projets c#, vous pouvez recibler le projet pour utiliser le .NET Framework 4 complet en cliquant sur le projet dans le **l’Explorateur de solutions** et en sélectionnant **propriétés**. Sur le **Application** onglet, sélectionnez le **NET Framework 4** option dans le **framework cible**. Sélectionnez le **Oui** situé dans le **modification du Framework cible** dialogue qui s’affiche vous invitant à confirmer cette modification.

 Pour les projets VB, vous pouvez recibler le projet pour utiliser le .NET Framework 4 complet en cliquant sur le projet dans le **l’Explorateur de solutions** et en sélectionnant **propriétés**. Sur le **compiler** , cliquez sur le **Options avancées de compilation** bouton. Sélectionnez **.Net Framework 4** à partir de la **liste de framework cible** puis cliquez sur **OK**. Cliquez sur le **Oui** situé dans le **modification du Framework cible** dialogue qui s’affiche vous invitant à confirmer cette modification.

 Le **Interop** Concepteur d’activités peut être déplacé de la **boîte à outils** et déposés dans l’aire du Concepteur de flux de travail où les activités sont généralement placées, par exemple dans un <xref:System.Activities.Statements.Sequence>. Cette opération crée un <xref:System.Activities.Statements.Interop> activité avec une valeur par défaut **DisplayName** d’interopérabilité. Le <xref:System.Activities.Activity.DisplayName%2A> peuvent être modifiées dans l’en-tête de la **Interop** Concepteur d’activités ou dans le **DisplayName** zone de la grille des propriétés.

 Cliquez sur le **cliquez pour parcourir...**  texte dans le **ActivityType** zone, soit sur le **Interop** activité concepteur ou dans la grille des propriétés, pour afficher le **rechercher et sélectionner un .net Type** boîte de dialogue. Seuls les types d'activités de workflow 3.0 ou 3.5 sont affichés (autrement dit, les types dérivés de <xref:System.Workflow.ComponentModel.Activity>). Pour plus d’informations sur l’utilisation de cette zone pour spécifier un type, consultez la [rechercher et sélectionner un Type .NET, boîte de dialogue](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box.md) rubrique.

### <a name="the-interop-properties"></a>Propriétés d'Interop
 Le tableau suivant présente les propriétés de <xref:System.Activities.Statements.Interop> et décrit comment elles sont utilisées dans le concepteur. Ces propriétés peuvent être modifiées dans la grille des propriétés ou sur l’aire du Concepteur de flux de travail.

|Nom de la propriété|Obligatoire|Utilisation|
|-------------------|--------------|-----------|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nom convivial de l'activité <xref:System.Activities.Statements.Interop>. La valeur par défaut est Interop. Bien que le nom complet ne soit pas strictement obligatoire, la meilleure pratique consiste à l'utiliser.|
|<xref:System.Activities.Statements.Interop.ActivityType%2A>|True|Spécifie le type de l'activité contenue par l'activité <xref:System.Activities.Statements.Interop>. Le type spécifié doit dériver d'<xref:System.Workflow.ComponentModel.Activity>.|

## <a name="see-also"></a>Voir aussi

- [Migration](../workflow-designer/migration-activity-designers.md)