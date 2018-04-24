---
title: Gestion des propriétés des projets et des solutions | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2a68cc558a52f7c8d66f76600cd68309ad67769c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="managing-project-and-solution-properties"></a>Gestion des propriétés des projets et des solutions

Les projets ont des propriétés qui régissent de nombreux aspects de la compilation, du débogage, du test et du déploiement. Certaines propriétés sont communes à tous les types de projets, et certaines sont particulières à des langages ou des plateformes spécifiques. Vous accédez aux propriétés d’un projet en cliquant avec le bouton droit sur le nœud du projet dans l’Explorateur de solutions et en sélectionnant **Propriétés**, ou en tapant « propriétés » dans la zone de recherche **Lancement rapide** dans la barre de menus.

![Menu contextuel du projet](../ide/media/vs2015_proj_prop_menu.gif "vs2015_proj_prop_menu")

Les projets .NET peuvent également avoir un nœud Propriétés dans l’arborescence-même du projet.

![Nœud Propriétés dans l’arborescence de l’Explorateur de solutions](../ide/media/vs2015_props_se.png "VS2015_Props_SE")

## <a name="project-properties"></a>Propriétés de projet

Les propriétés de projet sont organisées en groupes, et chaque groupe a sa propre page de propriétés. Les pages peuvent être différentes pour différents langages et types de projets.

### <a name="c-visual-basic-and-f-projects"></a>Projets C#, Visual Basic et F#

Dans les projets C#, Visual Basic et F#, les propriétés sont exposées dans le **Concepteur de projet**. L'illustration suivante montre la page de propriétés Build d'un projet WPF en C# :

![Concepteur de projets Visual Studio](../ide/media/vs2015_proppage_build.png "VS2015_PropPage_Build")

Pour plus d’informations sur chacune des pages de propriétés dans le Concepteur de projets, consultez [Informations de référence sur les propriétés d’un projet](../ide/reference/project-properties-reference.md).

> [!TIP]
> Les solutions ont quelques propriétés, de même que les éléments des projets. Ces propriétés sont accessibles dans la [fenêtre Propriétés](../ide/reference/properties-window.md) et non pas dans le **Concepteur de projets**.

### <a name="c-and-javascript-projects"></a>Projets C++ et JavaScript

Les projets C++ et JavaScript ont une interface utilisateur différente pour la gestion des propriétés des projets. Cette illustration montre une page de propriétés d'un projet C++ (les pages pour JavaScript sont similaires) :

![Propriétés de projet Visual C&#43;&#43;](../ide/media/vs2015_projprops_cpp.png "VS2015_ProjProps_cpp")

Pour plus d’informations sur les propriétés des projets C++, consultez [Utilisation des propriétés des projets (C++)](/cpp/ide/working-with-project-properties). Pour plus d’informations sur les propriétés JavaScript, consultez [Pages de propriétés, JavaScript](../ide/reference/property-pages-javascript.md).

## <a name="solution-properties"></a>Propriétés de la solution

Pour accéder aux propriétés sur la solution, cliquez avec le bouton droit sur le nœud de la solution dans l’**Explorateur de solutions** et choisissez **Propriétés**. Dans la boîte de dialogue, vous pouvez définir des configurations de projet pour les builds Debug ou Release, choisir les projets qui doivent être le projet de démarrage quand vous appuyez sur F5 et définir les options d’analyse du code.

## <a name="see-also"></a>Voir aussi

[Solutions et projets dans Visual Studio](../ide/solutions-and-projects-in-visual-studio.md)
