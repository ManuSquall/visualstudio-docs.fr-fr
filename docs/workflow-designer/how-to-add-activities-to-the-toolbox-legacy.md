---
title: 'Le Concepteur de flux de travail - Comment : ajouter des activités à la boîte à outils (héritée)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- Toolbox, adding activities
- activities, adding to Toolbox
ms.assetid: b66ea29c-120b-40ba-8a61-c1c8240850fa
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 99a8e1cef2ff5ddd526133355c608fa5218573d1
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31969425"
---
# <a name="how-to-add-activities-to-the-toolbox-legacy"></a>Procédure : ajouter des activités à la boîte à outils (héritée)

Lorsque vous créez une solution de flux de travail avec le Concepteur de flux de travail Windows hérité qui cible le .NET Framework version 3.5 ou le WinFX, des activités personnalisées peuvent être ajoutées au projet de workflow et leurs concepteurs placés dans le **boîte à outils** pour accès facile. Vous pouvez également ajouter des activités directement à la **boîte à outils** à partir d’une bibliothèque de liens dynamiques (DLL).

## <a name="to-add-an-activity-to-the-toolbox-from-a-dll"></a>Pour ajouter une activité à la boîte à outils à partir d'une DLL

1.  Avec le bouton droit de la surface de la fenêtre Boîte à outils sous **Windows Workflow**, puis cliquez sur **choisir des éléments de**.

2.  Dans le **choisir des éléments de boîte à outils** boîte de dialogue, cliquez sur le **System.Activities Components** onglet, puis cliquez sur **Parcourir** à partir de l’angle inférieur droit de la fenêtre.

3.  Sélectionnez la DLL dans le répertoire de fichier qui contient l’implémentation de l’activité personnalisée à ajouter à la **boîte à outils**, puis cliquez sur **ouvrir**.

4.  Cliquez sur **OK** pour terminer l’ajout de l’activité à la boîte à outils.

## <a name="see-also"></a>Voir aussi

- [Utilisation du concepteur d’activités hérité](../workflow-designer/using-the-legacy-activity-designer.md)
- [Activités de flux de travail héritées](../workflow-designer/legacy-workflow-activities.md)