---
title: Le Concepteur de flux de travail - Parcourir et sélectionnez une boîte de dialogue du Type .NET (hérité)
ms.date: 11/04/2016
ms.topic: reference
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
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
ms.openlocfilehash: 23e311aa8e87fe799bc8ea22a22ffd8e789b3dcd
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31969356"
---
# <a name="browse-and-select-a-net-type-dialog-box-legacy"></a>Rechercher et sélectionner un type .NET, boîte de dialogue (héritée)

Cette rubrique décrit comment utiliser le **rechercher et sélectionner un Type .NET** boîte de dialogue dans le Concepteur de flux de travail Windows hérité. Utilisez le Concepteur de flux de travail hérité lorsque vous avez besoin cibler le .NET Framework version 3.5 ou du WinFX.

 Dans le **propriétés** fenêtre, lorsque vous sélectionnez des propriétés qui acceptent un type .NET Framework dans un assembly référencé, les points de suspension **[...]**  apparaît à la fin de la zone de texte de la propriété. En cliquant sur le **[...]**  ouvre le **rechercher et sélectionner un Type .NET** boîte de dialogue. Dans cette boîte de dialogue, vous pouvez choisir un type dans l’arborescence des assemblys référencés. Par exemple, lorsque vous utilisez le Concepteur d’activités, dans le **propriétés** fenêtre, cliquez sur le **une classe de Base** points de suspension **[...]**  pour sélectionner une autre classe de base pour une activité à partir de l’arborescence des assemblys référencés.

 Le tableau suivant décrit les éléments d’interface utilisateur utilisateur de la **rechercher et sélectionner un Type .NET** boîte de dialogue.

|Élément d'interface utilisateur|Description|
|----------------|-----------------|
|**Nom du type :**|Nom du type actuellement sélectionné.|
|**Type**|Le volet de gauche affiche l’arborescence des assemblys référencés. Le volet de droite affiche les types disponibles pour l'assembly référencé sélectionné dans le volet de gauche.|

## <a name="see-also"></a>Voir aussi

- [Utilisation du concepteur d’activités hérité](../workflow-designer/using-the-legacy-activity-designer.md)