---
title: 'Comment : ajouter des activités à la boîte à outils (héritée) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- Toolbox, adding activities
- activities, adding to Toolbox
ms.assetid: b66ea29c-120b-40ba-8a61-c1c8240850fa
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f3f982372f0189871c4f3d294c07a9e3cfc44391
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656618"
---
# <a name="how-to-add-activities-to-the-toolbox-legacy"></a>Procédure : ajouter des activités à la boîte à outils (héritée)
Lors de la génération d’une solution de flux de travail avec le hérité [!INCLUDE[wfd1](../includes/wfd1-md.md)] qui cible le [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] ou le [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] , les activités personnalisées peuvent être ajoutées au projet de workflow et à leurs concepteurs dans la **boîte à outils** pour y accéder facilement. Vous pouvez également ajouter directement des activités à la **boîte à outils** à partir d’une bibliothèque de liens dynamiques (dll).

### <a name="to-add-an-activity-to-the-toolbox-from-a-dll"></a>Pour ajouter une activité à la boîte à outils à partir d'une DLL

1. Cliquez avec le bouton droit sur la surface de la fenêtre boîte à outils sous **Windows Workflow**, puis cliquez sur **choisir les éléments**.

2. Dans la boîte de dialogue **choisir des éléments de boîte à outils** , cliquez sur l’onglet **composants System. Activities** , puis cliquez sur **Parcourir** dans la partie inférieure droite de la fenêtre.

3. Sélectionnez la DLL dans le répertoire de fichiers qui contient l’implémentation de l’activité personnalisée à ajouter à la **boîte à outils**, puis cliquez sur **ouvrir**.

4. Cliquez sur **OK** pour terminer l’ajout de l’activité à la boîte à outils.

## <a name="see-also"></a>Voir aussi
 Utilisation des [activités de flux de travail héritées](../workflow-designer/legacy-workflow-activities.md) [du concepteur d’activités héritées](../workflow-designer/using-the-legacy-activity-designer.md)