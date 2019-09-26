---
title: 'Concepteur de flux de travail : XAML de débogage'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d9305dbc-af62-4bdd-b03f-c54e3fe9ecc7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: af5b7585ed5c0f34eeb44edba8c60ba0d5e14559
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71254775"
---
# <a name="how-to-debug-xaml-with-the-workflow-designer"></a>Procédure : Déboguer du code XAML à l’aide du concepteur de workflow

Les workflows sont définis en code XAML. La représentation de l’interface utilisateur du workflow est construite sur l’arborescence XAML définissant le workflow. L’expérience de débogage est semblable au débogage de flux de travail dans le Concepteur de flux de travail. Par exemple, lors du débogage XAML, les fenêtres variables locales, espion et threads fonctionnent de la même façon que dans Concepteur de flux de travail le débogage. De plus, la vue de la pile des appels pendant le débogage de code XAML est une vue hiérarchique basée sur les lignes du flux d'exécution pour le workflow.

> [!NOTE]
> Si le code XAML pour un workflow se trouve dans le même assembly que les activités, la partie d'assembly des noms de classe n'est pas incluse. Sans cette partie des noms de classe (activité), le code XAML ne peut pas être chargé au moment de l’exécution. Il n'est pas recommandé de définir des activités dans le même espace de noms que le projet principal ; sinon, le code XAML doit être modifié manuellement après avoir été modifié dans le concepteur.

## <a name="to-debug-workflow-xaml"></a>Pour déboguer le code XAML du workflow

1. Ouvrez un flux de travail ou un projet d’activité dans Visual Studio.

2. Définissez un point d’arrêt sur l’activité ou les activités que vous souhaitez déboguer, comme décrit dans [procédure : Définir des points d’arrêt](../workflow-designer/how-to-set-breakpoints-in-workflows.md)dans les workflows.

3. Cliquez avec le bouton droit sur le fichier. XAML qui contient votre définition de flux de travail, puis sélectionnez **afficher le code**. Vous verrez un point d'arrêt affiché sur la même ligne que la déclaration d'élément XAML de l'activité sur laquelle vous définissez le point d'arrêt en mode Design.

4. Appelez le débogueur comme décrit dans [déboguer les flux de travail](debugging-workflows-with-the-workflow-designer.md).

5. Lorsque l'exécution du code atteint l'un de vos points d'arrêt, l'élément XAML associé à ce point d'arrêt est mis en surbrillance. Pour passer au point d’arrêt suivant, utilisez la touche **F10** ou **F11** .

## <a name="see-also"></a>Voir aussi

- [Guide pratique pour définir des points d’arrêt dans les workflows](../workflow-designer/how-to-set-breakpoints-in-workflows.md)
- [Déboguer des flux de travail](debugging-workflows-with-the-workflow-designer.md)