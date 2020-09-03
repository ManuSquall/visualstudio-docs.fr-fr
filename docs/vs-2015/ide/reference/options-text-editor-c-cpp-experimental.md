---
title: Options, Éditeur de texte, C-C++, Expérimental │ Microsoft Docs
ms.date: 11/15/2016
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C/C++.Experimental
- VS.ToolsOptionsPages.Text_Editor.C%2FC%2B%2B.Experimental
- VS.ToolsOptionsPages.Text_Editor.C\C++.Experimental
ms.assetid: b9e9dda2-350c-460d-b368-37d6c5342eee
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6e4f239c5be290f6d79f52f55dbcb6da60d10785
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75851701"
---
# <a name="options-text-editor-cc-experimental"></a>Options, Éditeur de texte, C/C++, Expérimental
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

En modifiant ces options, vous pouvez changer le comportement lié à IntelliSense et la base de données de navigation quand vous programmez en C ou C++.

 Pour accéder à cette page, dans la boîte de dialogue **Options** , dans le volet gauche, développez **Éditeur de texte**, **C/C++**, puis choisissez **Expérimental**.

 Ces fonctionnalités sont disponibles dans une installation de Visual Studio 2015 Update 1 RC.

> [!NOTE]
> Il est possible que pour certains des éléments de l'interface utilisateur de Visual Studio, votre ordinateur affiche des noms ou des emplacements différents de ceux indiqués dans les instructions suivantes. L'édition de Visual Studio dont vous disposez et les paramètres que vous utilisez déterminent ces éléments. Consultez [Personnalisation des paramètres de développement dans Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="browsingnavigation"></a>Navigation de fichiers/répertoires
 **Activer les nouvelles moteur de base de données** Cela doit automatiquement accélérer le remplissage de la base de données et rendre toutes les opérations de base de données plus rapides (sans perte de précision) pour les opérations telles que **atteindre la définition** et **Rechercher toutes les références**. (Il vous suffit de fermer et rouvrir votre solution pour appliquer les modifications ; vous n’êtes pas obligé de redémarrer Visual Studio.)

## <a name="intellisense"></a>IntelliSense
 **Liste des membres point par flèche** Remplace « . » par « -> » le cas échéant pour la liste des membres.

## <a name="refactoring"></a>Refactorisation
 **Activer l’extraction de fonction** Extrayez le code sélectionné dans sa propre fonction et remplacez le code par un appel à la nouvelle fonction. Pour accéder à cette fonctionnalité, cliquez avec le bouton droit sur le code sélectionné et sélectionnez **Actions rapides**, ou appuyez simplement sur le raccourci par défaut Ctrl+point [Ctrl+.].

 **Activer la signature de modification** Ajoutez, réorganisez et supprimez les paramètres d’une fonction et Propagez les modifications à tous les sites d’appel. Pour accéder à cette fonctionnalité, cliquez avec le bouton droit sur toute utilisation de la fonction et sélectionnez **Actions rapides**, ou appuyez simplement sur le raccourci par défaut Ctrl+point [Ctrl+.].

## <a name="text-editor"></a>Éditeur de texte
 **Activer développer les étendues** Si cette option est activée, vous pouvez entourer le texte sélectionné d’accolades en tapant « { » dans l’éditeur de texte.

 **Activer développer la précédence** Si cette option est activée, vous pouvez entourer le texte sélectionné de parenthèses en tapant « ( » dans l’éditeur de texte.

 Pour obtenir d’autres fonctionnalités de l’éditeur de texte dans la galerie Visual Studio, consultez la liste [ici](https://marketplace.visualstudio.com/). Par exemple, les [Corrections rapides C++](https://visualstudiogallery.msdn.microsoft.com/be91feef-8dc3-4f7a-ac9f-f34e7ca5918f)prennent en charge les éléments suivants :

- **Ajouter un #include manquant** : propose des éléments #include pertinents pour les symboles inconnus dans votre code

- **Ajouter l’espace de noms using/Symbole qualifié complet** : comme l’élément précédent, mais pour les espaces de noms

- **Ajouter un point-virgule manquant**

- **Aide MSDN** : rechercher les messages d’erreur sur MSDN

  Vous pouvez soit pointer sur un tilde pour obtenir une ampoule, soit utiliser le raccourci clavier par défaut Ctrl+point [Ctrl+.]. Notez que, pour le raccourci clavier, votre signe d’insertion ne doit pas être positionné sur le jeton ou l’erreur spécifique ; vous pouvez tout simplement vous placer sur la même ligne que l’erreur pour appeler des suggestions pour tout élément sur cette ligne.

## <a name="see-also"></a>Voir aussi
 [Définition des options de l’éditeur spécifiques](../../ide/reference/setting-language-specific-editor-options.md) à la langue [refactorisation en C++ (blog VC)](https://devblogs.microsoft.com/cppblog/all-about-c-refactoring-in-visual-studio-2015-preview/)
