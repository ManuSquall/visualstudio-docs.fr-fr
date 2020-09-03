---
title: Rechercher et sélectionner un type .NET, boîte de dialogue (héritée) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Workflow.ComponentModel.Design.TypeBrowserDialog.UI
helpviewer_keywords:
- Browse and Select a .NET Type dialog box
ms.assetid: 1e66c9bc-94b2-46e2-bedf-871752e5f917
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1e5045a62d0a654af968d50e0c309bcf8104b5cc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72668984"
---
# <a name="browse-and-select-a-net-type-dialog-box-legacy"></a>Rechercher et sélectionner un type .NET, boîte de dialogue (héritée)
Cette rubrique décrit comment utiliser la boîte de dialogue **Parcourir et sélectionner un type .net** dans le hérité [!INCLUDE[wfd1](../includes/wfd1-md.md)] . Utilisez le [!INCLUDE[wfd2](../includes/wfd2-md.md)] hérité lorsque vous devez cibler le [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] ou le [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 Dans la fenêtre **Propriétés** , lorsque vous sélectionnez des propriétés qui acceptent un type de .NET Framework dans un assembly référencé, un Ellipse **[...]** apparaît à la fin de la zone de texte de la propriété. Cliquez sur **[...]** pour ouvrir la boîte de dialogue **Parcourir et sélectionner un type .net** . Dans cette boîte de dialogue, vous pouvez choisir un type dans l’arborescence des assemblys référencés. Par exemple, lorsque vous utilisez le concepteur d’activités, dans la fenêtre **Propriétés** , cliquez sur les ellipses de la **classe de base** **[...]** pour sélectionner une autre classe de base pour une activité à partir de l’arborescence des assemblys référencés.

 Le tableau suivant décrit les éléments d’interface utilisateur de la boîte de dialogue **Parcourir et sélectionner un type .net** .

|Élément de l’interface utilisateur|Description|
|----------------|-----------------|
|**Nom du type :**|Nom du type actuellement sélectionné.|
|**Type**|Le volet de gauche affiche l'arborescence des assemblys référencés. Le volet de droite affiche les types disponibles pour l'assembly référencé sélectionné dans le volet de gauche.|

## <a name="see-also"></a>Voir aussi
 [Utilisation du concepteur d'activités hérité](../workflow-designer/using-the-legacy-activity-designer.md)