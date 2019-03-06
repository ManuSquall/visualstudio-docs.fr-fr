---
title: Gestion des propriétés des projets et des solutions | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: d727efc0-1096-4ede-84b6-31a65da22ac0
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f3e9ff4acbfd6df1980a3882311b3d3c4611e064
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2019
ms.locfileid: "54758119"
---
# <a name="managing-project-and-solution-properties"></a>Gestion des propriétés des projets et des solutions
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Les projets ont des propriétés qui régissent de nombreux aspects de la compilation, du débogage, du test et du déploiement. Certaines propriétés sont communes à tous les types de projets, et certaines sont particulières à des langages ou des plateformes spécifiques. Vous accédez aux propriétés d’un projet en cliquant avec le bouton droit sur le nœud du projet dans l’Explorateur de solutions et en sélectionnant Propriétés, ou en tapant le nom des propriétés dans la zone de recherche **Lancement rapide** dans la barre de menus.  
  
 ![Menu contextuel du projet](../ide/media/vs2015-proj-prop-menu.gif "vs2015_proj_prop_menu")  
  
 Les projets .NET ont également un nœud Propriétés dans l’arborescence du projet.  
  
 ![Nœud Propriétés dans l’arborescence de l’Explorateur de solutions](../ide/media/vs2015-props-se.png "VS2015_Props_SE")  
  
> [!TIP]
>  Les solutions ont quelques propriétés, de même que les éléments des projets. Ces propriétés sont accessibles dans la [fenêtre Propriétés](../ide/reference/properties-window.md) et non pas dans le **Concepteur de projets**.  
  
## <a name="project-properties"></a>Propriétés du projet  
 Les propriétés du projet sont organisées en groupes, chaque groupe ayant sa propre page de propriétés. Les pages peuvent être différentes pour les différents langages et types de projets.  
  
### <a name="c-and-visual-basic-projects"></a>Projets C# et Visual Basic  
 Dans les projets C# et Visual Basic, les propriétés sont exposées dans le **Concepteur de projets**. L'illustration suivante montre la page de propriétés Build d'un projet WPF en C# :  
  
 ![Concepteur de projets Visual Studio](../ide/media/vs2015-proppage-build.png "VS2015_PropPage_Build")  
  
 Pour plus d’informations sur chacune des pages de propriétés dans le Concepteur de projets, consultez [Informations de référence sur les propriétés d’un projet](../ide/reference/project-properties-reference.md).  
  
### <a name="c-and-javascript-projects"></a>Projets C++ et JavaScript  
 Les projets C++ et JavaScript ont une interface utilisateur différente pour la gestion des propriétés des projets. Cette illustration montre une page de propriétés d'un projet C++ (les pages pour JavaScript sont similaires) :  
  
 ![Propriétés de projet Visual C&#43;&#43;](../ide/media/vs2015-projprops-cpp.png "VS2015_ProjProps_cpp")  
  
 Pour plus d’informations sur les propriétés des projets C++, consultez [Utilisation des propriétés des projets](http://msdn.microsoft.com/library/9b0d6f8b-7d4e-4e61-aa75-7d14944816cd). Pour plus d’informations sur les propriétés JavaScript, consultez [Pages de propriétés, JavaScript](../ide/reference/property-pages-javascript.md).  
  
## <a name="solution-properties"></a>Propriétés de la solution  
 Pour accéder aux propriétés sur la solution, cliquez avec le bouton droit sur le nœud de la solution dans l’**Explorateur de solutions** et choisissez **Propriétés**. Dans la boîte de dialogue, vous pouvez définir des configurations de projet pour les builds Debug ou Release, choisir le ou les projets qui doivent être le projet de démarrage quand vous appuyez sur F5, et définir les options d’analyse du code.  
  
## <a name="see-also"></a>Voir aussi  
 [Solutions et projets dans Visual Studio](../ide/solutions-and-projects-in-visual-studio.md)
