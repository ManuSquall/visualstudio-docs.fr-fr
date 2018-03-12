---
title: "Comment : ajouter des activités à la boîte à outils (hérité) | Documents Microsoft"
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Toolbox, adding activities
- activities, adding to Toolbox
ms.assetid: b66ea29c-120b-40ba-8a61-c1c8240850fa
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 1d6d7e817ae34b3e39d617ad5d12802cabd5cedc
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2018
---
# <a name="how-to-add-activities-to-the-toolbox-legacy"></a>Procédure : ajouter des activités à la boîte à outils (héritée)
Lors de la création d’une solution de flux de travail avec le Concepteur de flux de travail Windows hérité qui cible le [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)], des activités personnalisées peuvent être ajoutées au projet de workflow et leurs concepteurs placés dans le **boîte à outils** pour accès facile. Vous pouvez également ajouter des activités directement à la **boîte à outils** à partir d’une bibliothèque de liens dynamiques (DLL).

### <a name="to-add-an-activity-to-the-toolbox-from-a-dll"></a>Pour ajouter une activité à la boîte à outils à partir d'une DLL

1.  Avec le bouton droit de la surface de la fenêtre Boîte à outils sous **Windows Workflow**, puis cliquez sur **choisir des éléments de**.

2.  Dans le **choisir des éléments de boîte à outils** boîte de dialogue, cliquez sur le **System.Activities Components** onglet, puis cliquez sur **Parcourir** à partir de l’angle inférieur droit de la fenêtre.

3.  Sélectionnez la DLL dans le répertoire de fichier qui contient l’implémentation de l’activité personnalisée à ajouter à la **boîte à outils**, puis cliquez sur **ouvrir**.

4.  Cliquez sur **OK** pour terminer l’ajout de l’activité à la boîte à outils.

## <a name="see-also"></a>Voir aussi

- [Utilisation du concepteur d’activités hérité](../workflow-designer/using-the-legacy-activity-designer.md)
- [Activités de flux de travail héritées](../workflow-designer/legacy-workflow-activities.md)