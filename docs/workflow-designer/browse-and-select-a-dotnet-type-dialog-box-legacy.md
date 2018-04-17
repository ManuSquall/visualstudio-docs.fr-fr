---
title: Rechercher et sélectionner une boîte de dialogue du Type .NET (hérité) | Documents Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Workflow.ComponentModel.Design.TypeBrowserDialog.UI
helpviewer_keywords:
- Browse and Select a .NET Type dialog box
ms.assetid: 1e66c9bc-94b2-46e2-bedf-871752e5f917
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: a283caa664bb208613a695cb4afb8873caba3645
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="browse-and-select-a-net-type-dialog-box-legacy"></a>Rechercher et sélectionner un type .NET, boîte de dialogue (héritée)
Cette rubrique décrit comment utiliser le **rechercher et sélectionner un Type .NET** boîte de dialogue dans le Concepteur de flux de travail Windows hérité. Utilisez le [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] hérité lorsque vous devez cibler le [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou le [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].

 Dans le **propriétés** fenêtre, lorsque vous sélectionnez des propriétés qui acceptent un type .NET Framework dans un assembly référencé, les points de suspension **[...]**  apparaît à la fin de la zone de texte de la propriété. En cliquant sur le **[...]**  ouvre le **rechercher et sélectionner un Type .NET** boîte de dialogue. Dans cette boîte de dialogue, vous pouvez choisir un type dans l’arborescence des assemblys référencés. Par exemple, lorsque vous utilisez le Concepteur d’activités, dans le **propriétés** fenêtre, cliquez sur le **une classe de Base** points de suspension **[...]**  pour sélectionner une autre classe de base pour une activité à partir de l’arborescence des assemblys référencés.

 Le tableau suivant décrit les éléments d’interface utilisateur utilisateur de la **rechercher et sélectionner un Type .NET** boîte de dialogue.

|Élément d'interface utilisateur|Description|
|----------------|-----------------|
|**Nom du type :**|Nom du type actuellement sélectionné.|
|**Type**|Le volet de gauche affiche l’arborescence des assemblys référencés. Le volet de droite affiche les types disponibles pour l'assembly référencé sélectionné dans le volet de gauche.|

## <a name="see-also"></a>Voir aussi

- [Utilisation du concepteur d’activités hérité](../workflow-designer/using-the-legacy-activity-designer.md)