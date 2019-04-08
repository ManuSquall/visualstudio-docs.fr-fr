---
title: Concepteur de flux de travail - Concepteur d’activités Interop
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Interop.UI
ms.assetid: 800a3403-ba86-41c4-8de1-c4fee9703eb1
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e020e2f4e1ffae9c0e979f2230ff845b1cda203e
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55942698"
---
# <a name="interop-activity-designer"></a>Concepteur d'activités Interop

Le **Interop** ActivityDesigner est utilisé pour créer et configurer un <xref:System.Activities.Statements.Interop> activité.

## <a name="the-interop-activity"></a>Activité Interop

L'activité <xref:System.Activities.Statements.Interop> gère l'exécution des types qui dérivent de <xref:System.Workflow.ComponentModel.Activity?displayProperty=fullName> dans un workflow.

### <a name="use-the-interop-activity-designer"></a>Utiliser le Concepteur d’activités Interop

Le **Interop** Concepteur d’activités peut être trouvé dans le **Migration** catégorie de la **boîte à outils**, qui est accessible en cliquant sur le **boîte à outils**onglet. Vous pouvez également sélectionner **boîte à outils** à partir de la **vue** menu, ou appuyez sur **Ctrl**+**Alt** + **X**.

Le [Migration](../workflow-designer/migration-activity-designers.md) catégorie qui contient le <xref:System.Activities.Statements.Interop> activité ne s’affiche dans **boîte à outils** si votre projet cible le .NET Framework 4 complet.

Pour les projets C#, vous pouvez recibler le projet pour utiliser le .NET Framework 4 complet en double-cliquant sur le projet dans **l’Explorateur de solutions** et en sélectionnant **propriétés**. Sur le **Application** onglet, sélectionnez le **NET Framework 4** option dans le **framework cible**. Sélectionnez **Oui** confirmer cette modification.

Pour les projets Visual Basic, vous pouvez recibler le projet pour utiliser le .NET Framework 4 complet en cliquant sur le projet dans **l’Explorateur de solutions** et en sélectionnant **propriétés**. Sur le **compiler** , cliquez sur le **Options avancées de compilation** bouton. Sélectionnez **.Net Framework 4** à partir de la **liste de framework cible**, puis cliquez sur **OK**. Sélectionnez **Oui** confirmer cette modification.

Le **Interop** Concepteur d’activités peut être déplacé de **boîte à outils** et déposé sur l’aire du Concepteur de flux de travail chaque fois que les activités sont généralement placées, par exemple dans un <xref:System.Activities.Statements.Sequence>. Suppression de la **Interop** Concepteur d’activités crée un <xref:System.Activities.Statements.Interop> activité avec une valeur par défaut **DisplayName** Interop. Vous pouvez modifier le <xref:System.Activities.Activity.DisplayName%2A> dans l’en-tête de la **Interop** Concepteur d’activités, ou dans le **DisplayName** case de la grille des propriétés.

Cliquez sur le **cliquez ici pour parcourir** texte dans le **ActivityType** zone, soit sur le **Interop** activité concepteur ou dans la grille des propriétés pour ouvrir le **Parcourir et Sélectionnez un .net Type** boîte de dialogue. Seuls les types de workflow 3.0 ou d’activités de workflow 3.5 sont affichés. Autrement dit, seuls les types dérivés de <xref:System.Workflow.ComponentModel.Activity> sont affichés. Pour plus d’informations sur l’utilisation de cette zone pour spécifier un type, consultez [Parcourir et sélectionner un Type .NET, boîte de dialogue](../workflow-designer/browse-and-select-a-dotnet-type-dialog-box.md).

### <a name="the-interop-properties"></a>Propriétés d'Interop

Le tableau suivant présente le <xref:System.Activities.Statements.Interop> propriétés et décrit comment elles sont utilisées dans le concepteur. Ces propriétés peuvent être modifiées dans la grille des propriétés ou sur l’aire du Concepteur de flux de travail.

|Nom de la propriété|Obligatoire|Utilisation|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|Nom convivial de l'activité <xref:System.Activities.Statements.Interop>. La valeur par défaut est **Interop**. Le nom d’affichage n’est pas obligatoire, il est recommandé d’en fournir un.|
|<xref:System.Activities.Statements.Interop.ActivityType%2A>|True|Spécifie le type de l'activité contenue par l'activité <xref:System.Activities.Statements.Interop>. Le type spécifié doit dériver d'<xref:System.Workflow.ComponentModel.Activity>.|

## <a name="see-also"></a>Voir aussi

- [Migration](../workflow-designer/migration-activity-designers.md)