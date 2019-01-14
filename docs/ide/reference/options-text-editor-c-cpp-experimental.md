---
title: Options, Éditeur de texte, C/C++, Expérimental
ms.date: 08/02/2017
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C/C++.Experimental
- VS.ToolsOptionsPages.Text_Editor.C%2FC%2B%2B.Experimental
- VS.ToolsOptionsPages.Text_Editor.C\C++.Experimental
author: mikeblome
ms.author: mblome
manager: wpickett
ms.prod: visual-studio-dev15
ms.workload:
- cplusplus
ms.openlocfilehash: 13bcc65b3d8ffe4872c8b7d5f18b1bbf13bc67c5
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53893326"
---
# <a name="options-text-editor-cc-experimental"></a>Options, Éditeur de texte, C/C++, Expérimental

En modifiant ces options, vous pouvez changer le comportement lié à IntelliSense et la base de données de navigation quand vous programmez en C ou C++. Ces fonctionnalités sont véritablement expérimentales et peuvent être modifiées ou supprimées de Visual Studio dans une version ultérieure. Cette rubrique décrit les options disponibles dans Visual Studio 2017. Pour Visual Studio 2015, sélectionnez **2015** dans le sélecteur au-dessus de la table des matières.

Pour accéder à cette page de propriétés, appuyez sur **Ctrl+Q** afin d’activer `Quick Launch`, puis tapez « expérimental ». Lancement rapide trouve la page une fois que vous avez tapé les premières lettres. Vous pouvez également y accéder en choisissant **Outils | Options** et en développant **Éditeur de texte** et **C/C++**, puis en choisissant **Expérimental**.

Ces fonctionnalités sont disponibles dans une installation de Visual Studio 2017.

> [!NOTE]
> Il est possible que pour certains des éléments de l’interface utilisateur de Visual Studio, votre ordinateur affiche des noms ou des emplacements différents de ceux indiqués dans les instructions suivantes. L’édition de Visual Studio dont vous disposez et les paramètres que vous utilisez déterminent ces éléments. Consultez [Personnaliser l’IDE Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="enable-predictive-intellisense"></a>Activer la fonctionnalité IntelliSense prédictive

La fonctionnalité IntelliSense prédictive limite le nombre de résultats affichés dans la liste déroulante IntelliSense afin que vous ne voyiez que les résultats qui sont pertinents dans le contexte. Par exemple, si vous tapez <code>int x =</code> et appelez la liste déroulante IntelliSense, vous voyez uniquement des entiers ou des fonctions qui retournent des entiers. La fonctionnalité IntelliSense prédictive est désactivée par défaut.

## <a name="enable-faster-project-load"></a>Activer le chargement accéléré de projet

**Visual Studio 2017 15.3 et versions ultérieures :** cette fonctionnalité se nomme désormais **Activer la mise en cache du projet** et elle a été déplacée dans la page de propriétés [Paramètres de projet VC ++](vcpp-project-settings-projects-and-solutions-options-dialog-box.md).
Cette option permet à Visual Studio de mettre en cache des données de projet pour que, lors de la prochaine ouverture du projet, il puisse charger ces données mises en cache au lieu de les recalculer à partir des fichiers projet. L’utilisation de données mises en cache peut accélérer considérablement la vitesse de chargement du projet.

## <a name="additional-features-in-the-visual-studio-marketplace"></a>Autres fonctionnalités dans Visual Studio Marketplace

Vous pouvez parcourir d’autres fonctionnalités de l’éditeur de texte dans la [Place de marché Visual Studio](https://marketplace.visualstudio.com/search?target=VS&category=Tools&vsVersion=&subCategory=All&sortBy=Downloads). Par exemple, les [Corrections rapides C++](https://marketplace.visualstudio.com/items?itemName=VisualCppDevLabs.CQuickFixes2017)prennent en charge les éléments suivants :

- **Ajouter un #include manquant** : propose des éléments #include pertinents pour les symboles inconnus dans votre code

- **Ajouter l’espace de noms using/Symbole qualifié complet** : comme l’élément précédent, mais pour les espaces de noms

- **Ajouter un point-virgule manquant**

- **Aide en ligne** : recherchez vos messages d’erreur dans l’aide en ligne

- Et plus encore...

## <a name="see-also"></a>Voir aussi

- [Définition d’options d’éditeur spécifiques du langage](../../ide/reference/setting-language-specific-editor-options.md)
- [Refactorisation en C++ (blog VC)](https://blogs.msdn.microsoft.com/vcblog/2014/11/14/all-about-c-refactoring-in-visual-studio-2015-preview/)
