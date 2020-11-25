---
title: Options, Éditeur de texte, C/C++, Expérimental
description: Découvrez comment utiliser la page expérimental dans la section C/C++ pour modifier les comportements expérimentaux liés à IntelliSense et à la base de données de navigation.
ms.custom: SEO-VS-2020
ms.date: 08/02/2017
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C/C++.Experimental
- VS.ToolsOptionsPages.Text_Editor.C%2FC%2B%2B.Experimental
- VS.ToolsOptionsPages.Text_Editor.C\C++.Experimental
author: corob-msft
ms.author: corob
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: e35bdb8c6a56ef3174277836769201cd00e47dad
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96040301"
---
# <a name="options-text-editor-cc-experimental"></a>Options, Éditeur de texte, C/C++, Expérimental

En modifiant ces options, vous pouvez changer le comportement lié à IntelliSense et la base de données de navigation quand vous programmez en C ou C++. Ces fonctionnalités sont véritablement expérimentales et peuvent être modifiées ou supprimées de Visual Studio dans une version ultérieure.

::: moniker range="vs-2017"

Cet article décrit les options disponibles dans Visual Studio 2017. Pour Visual Studio 2015, sélectionnez **2015** dans le sélecteur au-dessus de la table des matières.

::: moniker-end

Pour accéder à cette page de propriétés, appuyez sur **CTRL** + **Q** pour activer la zone de recherche, puis tapez **expérimental**. La recherche trouve la page dès les premières lettres saisies. Vous pouvez également y accéder en choisissant **Outils**  >  **options** et en développant **éditeur de texte**, puis **C/C++**, puis en choisissant **expérimental**.

Ces fonctionnalités sont disponibles dans une installation de Visual Studio.

> [!NOTE]
> Il est possible que pour certains des éléments de l'interface utilisateur de Visual Studio, votre ordinateur affiche des noms ou des emplacements différents de ceux indiqués dans les instructions suivantes. L'édition de Visual Studio dont vous disposez et les paramètres que vous utilisez déterminent ces éléments. Consultez [Personnaliser l’IDE Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="enable-predictive-intellisense"></a>Activer la fonctionnalité IntelliSense prédictive

La fonctionnalité IntelliSense prédictive limite le nombre de résultats affichés dans la liste déroulante IntelliSense afin que vous ne voyiez que les résultats qui sont pertinents dans le contexte. Par exemple, si vous tapez `int x =` et appelez la liste déroulante IntelliSense, vous voyez uniquement des entiers ou des fonctions qui retournent des entiers. La fonctionnalité IntelliSense prédictive est désactivée par défaut.

::: moniker range="vs-2017"

## <a name="enable-faster-project-load"></a>Activer le chargement accéléré de projet

À compter de Visual Studio 2017 version 15.3, cette fonctionnalité est appelée [Activer la mise en cache du projet](vcpp-project-settings-projects-and-solutions-options-dialog-box.md) et a été déplacée dans la page de propriétés **Paramètres de projet VC++**.

Cette option permet à Visual Studio de mettre en cache des données de projet pour que, lors de la prochaine ouverture du projet, il puisse charger ces données mises en cache au lieu de les recalculer à partir des fichiers projet. L’utilisation de données mises en cache peut accélérer considérablement la vitesse de chargement du projet.

::: moniker-end

## <a name="additional-features-in-the-visual-studio-marketplace"></a>Autres fonctionnalités dans Visual Studio Marketplace

Vous pouvez parcourir d’autres fonctionnalités de l’éditeur de texte dans la [Place de marché Visual Studio](https://marketplace.visualstudio.com/search?target=VS&category=Tools&vsVersion=&subCategory=All&sortBy=Downloads). Par exemple, les [Corrections rapides C++](https://marketplace.visualstudio.com/items?itemName=VisualCppDevLabs.CQuickFixes2017)prennent en charge les éléments suivants :

- **Ajouter un #include manquant** : propose des éléments #include pertinents pour les symboles inconnus dans votre code

- **Ajouter l’espace de noms using/Symbole qualifié complet** : comme l’élément précédent, mais pour les espaces de noms

- **Ajouter un point-virgule manquant**

- **Aide en ligne** : recherchez vos messages d’erreur dans l’aide en ligne

- Et bien plus...

## <a name="see-also"></a>Voir aussi

- [Définition des options de l’éditeur de Language-Specific](../../ide/reference/setting-language-specific-editor-options.md)
- [Refactorisation en C++ (blog VC)](https://devblogs.microsoft.com/cppblog/all-about-c-refactoring-in-visual-studio-2015-preview/
)
