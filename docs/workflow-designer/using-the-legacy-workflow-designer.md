---
title: Utilisation du Concepteur de Workflow hérité
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- Visual Studio 2005 Extensions for Windows Workflow Foundation, about
ms.assetid: 7af53077-afd7-465f-9c1d-b387e9d4f216
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 794b52c918eb727fe67d24af209d21403da18475
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31975466"
---
# <a name="using-the-legacy-workflow-designer"></a>Utilisation du Concepteur de Workflow hérité

Hérité Concepteur de flux de travail fourni par Visual Studio 2010 peut servir pour cibler le .NET Framework version 3.5 ou le WinFX.

Il est accessible en sélectionnant le le **.NET Framework 3.0** option ou **.NET Framework 3.5** option dans la liste déroulante située en haut de la **nouveau projet** fenêtre. L’option par défaut dans Visual Studio 2010 est **.NET Framework 4** qui sert à créer des applications Windows Workflow Foundation (WF) qui ciblent le .NET Framework 4.

Le Concepteur de flux de travail vous permet de créer graphiquement des applications de Windows Workflow Foundation (WF) à l’aide de l’interface utilisateur de Visual Studio familière. Les applications Windows Workflow Foundation (WF) sont composées d’étapes du processus de workflow appelées activités. Pour créer un workflow, composez des activités sur l’aire de conception en faisant glisser leurs concepteurs d’activités respectifs de **boîte à outils** sur l’aire de conception.

Le tableau suivant répertorie les principales fonctionnalités de Visual Studio pour Windows Workflow Foundation.

|Fonctionnalité|Description|
|-------------|-----------------|
|Activité de glisser-déposer|Faites glisser les activités à partir de la **boîte à outils** sur l’aire de conception pour créer un flux de travail.|
|Explorateur de propriétés|La norme **propriétés** fenêtre dans Visual Studio est utilisé pour configurer les propriétés d’une activité.|
|Zoom|Les jumelles **le niveau de Zoom** située sous la barre de défilement verticale sur le côté droit de l’aire de conception. Cliquez sur les jumelles et sélectionnez un pourcentage de zoom pour effectuer un zoom avant ou arrière du graphique de workflow. Vous pouvez également utiliser le **panoramique** options de curseur icône en forme de loupe pour effectuer un zoom avant et arrière.|
|Panoramique|Le **panoramique** , un cercle contenant quatre flèches qui pointent dans quatre directions, est située sous la barre de défilement verticale sur le côté droit de l’aire de conception juste en dessous de l’icône de zoom (jumelles). Si vous cliquez sur l'icône de panoramique, un menu contextuel affiche les options de curseur suivantes :<br /><br /> -La **zoom avant** curseur de loupe vous permet de faire un zoom en cliquant sur l’aire de conception.<br />-La **Zoom arrière** curseur de loupe vous permet d’effectuer un zoom arrière en cliquant sur l’aire de conception.<br />-La **outil de Navigation** main vous permet de « saisissez » et déplacez la vue d’un flux de travail dans l’aire de conception.<br />-La **par défaut** pointeur vous permet de basculer d’autres curseurs vers le pointeur par défaut.|
|Défilement automatique|En cas de workflow de grande taille, vous pouvez placer une activité au delà de l'affichage visible de la zone d'aire de conception. Visual Studio vous permet de faire glisser une activité vers le bord de l’aire de conception, le plus proche dans laquelle vous souhaitez placer l’activité. La vue de l'aire de conception défile automatiquement dans cette direction.|
|Balises actives|Les activités qui ne sont pas configurées complètement ou correctement sont signalées par une icône en forme de point d'exclamation. Vous pouvez cliquer sur l’icône afin d’afficher la liste déroulante des besoins de configuration répertoriés pour cette activité. Vous pouvez ensuite utiliser le **propriétés** fenêtre Configurer l’activité de manière appropriée. Une fois que toutes les propriétés sont valides pour l'activité, l'icône de point d'exclamation disparaît.|

## <a name="see-also"></a>Voir aussi

- [Développement de flux de travail](http://go.microsoft.com/fwlink?LinkID=65010)