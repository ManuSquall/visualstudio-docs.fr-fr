---
title: 'Concepteur de flux de travail : Déboguer XAML'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d9305dbc-af62-4bdd-b03f-c54e3fe9ecc7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 0d22668089581dcf44609756a4e7f8f4527dd751
ms.sourcegitcommit: ba5e072c9fedeff625a1332f22dcf3644d019f51
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66431821"
---
# <a name="how-to-debug-xaml-with-the-workflow-designer"></a>Procédure : Déboguer du code XAML à l’aide du concepteur de workflow

Les workflows sont définis en code XAML. La représentation de l’interface utilisateur du workflow est construite sur l’arborescence XAML définissant le workflow. L’expérience de débogage est semblable au débogage de flux de travail dans le Concepteur de Workflow. Par exemple, pendant le débogage de XAML, les variables locales, Espion et threads windows fonctionnent la même façon comme ils le font dans le Concepteur de flux de travail de débogage. De plus, la vue de la pile des appels pendant le débogage de code XAML est une vue hiérarchique basée sur les lignes du flux d'exécution pour le workflow.

> [!NOTE]
> Si le code XAML pour un workflow se trouve dans le même assembly que les activités, la partie d'assembly des noms de classe n'est pas incluse. Sans cette partie des noms de classe (activité), le code XAML ne peut pas être chargé au moment de l'exécution. Il n'est pas recommandé de définir des activités dans le même espace de noms que le projet principal ; sinon, le code XAML doit être modifié manuellement après avoir été modifié dans le concepteur.

## <a name="to-debug-workflow-xaml"></a>Pour déboguer le code XAML du workflow

1. Dans Visual Studio, ouvrez un projet de flux de travail ou d’activité.

2. Définir un point d’arrêt sur l’activité ou les activités que vous souhaitez déboguer, comme décrit dans [Comment : Définir des points d’arrêt dans les Workflows](../workflow-designer/how-to-set-breakpoints-in-workflows.md).

3. Cliquez sur le fichier .xaml qui contient votre définition de flux de travail, puis sélectionnez **afficher le Code**. Vous verrez un point d'arrêt affiché sur la même ligne que la déclaration d'élément XAML de l'activité sur laquelle vous définissez le point d'arrêt en mode Design.

4. Appelez le débogueur, comme décrit dans [déboguer des workflows](debugging-workflows-with-the-workflow-designer.md).

5. Lorsque l'exécution du code atteint l'un de vos points d'arrêt, l'élément XAML associé à ce point d'arrêt est mis en surbrillance. Pour déplacer le point d’arrêt suivant, utilisez le **F10** ou **F11** clé.

## <a name="see-also"></a>Voir aussi

- [Guide pratique pour définir des points d’arrêt dans les workflows](../workflow-designer/how-to-set-breakpoints-in-workflows.md)
- [Déboguer des workflows](debugging-workflows-with-the-workflow-designer.md)