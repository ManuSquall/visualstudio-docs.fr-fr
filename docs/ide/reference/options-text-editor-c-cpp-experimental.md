---
title: "Options, Éditeur de texte, C/C++, Expérimental │ Microsoft Docs"
ms.custom: 
ms.date: 08/02/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C/C++.Experimental
- VS.ToolsOptionsPages.Text_Editor.C%2FC%2B%2B.Experimental
- VS.ToolsOptionsPages.Text_Editor.C\C++.Experimental
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-general
ms.openlocfilehash: 5ef21632d4d1de211aeb84c00adc0f852d4ebae9
ms.sourcegitcommit: eb954434c34b4df6fd2264266381b23ce9e6204a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2017
---
# <a name="options-text-editor-cc-experimental"></a>Options, Éditeur de texte, C/C++, Expérimental

En modifiant ces options, vous pouvez changer le comportement lié à IntelliSense et la base de données de navigation quand vous programmez en C ou C++. Ces fonctionnalités sont véritablement expérimentales et peuvent être modifiées ou supprimées de Visual Studio dans une version ultérieure. Cette rubrique décrit les options disponibles dans Visual Studio 2017. Pour Visual Studio 2015, consultez [Options, Éditeur de texte, C/C++, Expérimental](https://msdn.microsoft.com/library/mt591979.aspx)

Pour accéder à cette page de propriétés, appuyez sur **Ctrl+Q** afin d’activer `Quick Launch`, puis tapez « expérimental ». Lancement rapide trouve la page une fois que vous avez tapé les premières lettres. Vous pouvez également y accéder en choisissant **Outils | Options** et en développant **Éditeur de texte** et **C/C++**, puis en choisissant **Expérimental**.

Ces fonctionnalités sont disponibles dans une installation de Visual Studio 2017.

> [!NOTE]
> Il est possible que pour certains des éléments de l'interface utilisateur de Visual Studio, votre ordinateur affiche des noms ou des emplacements différents de ceux indiqués dans les instructions suivantes. L'édition de Visual Studio dont vous disposez et les paramètres que vous utilisez déterminent ces éléments. Consultez [Personnaliser l’IDE Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="enable-predictive-intellisense"></a>Activer la fonctionnalité IntelliSense prédictive

La fonctionnalité IntelliSense prédictive limite le nombre de résultats affichés dans la liste déroulante IntelliSense afin que vous ne voyiez que les résultats qui sont pertinents dans le contexte. Par exemple, si vous tapez <code>int x =</code> et appelez la liste déroulante IntelliSense, vous voyez uniquement des entiers ou des fonctions qui retournent des entiers. La fonctionnalité IntelliSense prédictive est désactivée par défaut.

## <a name="enable-faster-project-load"></a>Activer le chargement accéléré du projet

**Visual Studio 2017 versions 15.3 et ultérieures** : cette fonctionnalité est désormais appelée **Activer la mise en cache du projet** et a été déplacée dans la page de propriétés [Paramètres de projet VC ++](vcpp-project-settings-projects-and-solutions-options-dialog-box.md).
Cette option permet à Visual Studio de mettre en cache des données de projet pour que, lors de la prochaine ouverture du projet, il puisse charger ces données mises en cache au lieu de les recalculer à partir des fichiers projet. L’utilisation de données mises en cache peut accélérer considérablement la vitesse de chargement du projet.

## <a name="additional-features-in-the-visual-studio-marketplace"></a>Autres fonctionnalités dans la Place de marché Visual Studio

Vous pouvez parcourir d’autres fonctionnalités de l’éditeur de texte dans la [Place de marché Visual Studio](https://marketplace.visualstudio.com/search?target=VS&category=Tools&vsVersion=&subCategory=All&sortBy=Downloads). Par exemple, les [Corrections rapides C++](https://marketplace.visualstudio.com/items?itemName=VisualCPPTeam.CQuickFixes2017)prennent en charge les éléments suivants :

- **Ajouter un #include manquant** : propose des éléments #include pertinents pour les symboles inconnus dans votre code

- **Ajouter l’espace de noms using/Symbole qualifié complet** : comme l’élément précédent, mais pour les espaces de noms

- **Ajouter un point-virgule manquant**

- **Aide en ligne** : recherchez vos messages d’erreur dans l’aide en ligne

- Et plus encore...

## <a name="see-also"></a>Voir aussi

[Définition d’options d’éditeur spécifiques du langage](../../ide/reference/setting-language-specific-editor-options.md)  
[Refactorisation en C++ (blog VC)](http://blogs.msdn.com/b/vcblog/archive/2014/11/14/all-about-c-refactoring-in-visual-studio-2015-preview.aspx)
