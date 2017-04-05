---
title: "Options, Éditeur de texte, C/C++, Expérimental │ Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C/C++.Experimental
- VS.ToolsOptionsPages.Text_Editor.C%2FC%2B%2B.Experimental
- VS.ToolsOptionsPages.Text_Editor.C\C++.Experimental
ms.assetid: b9e9dda2-350c-460d-b368-37d6c5342eee
caps.latest.revision: 10
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: e9a05d008f671fb79d6813a14c594b82f27697e3
ms.openlocfilehash: 780c643c25f0d43ec0564e43bc50d2f36f1aee79
ms.lasthandoff: 03/27/2017

---
# <a name="options-text-editor-cc-experimental"></a>Options, Éditeur de texte, C/C++, Expérimental
En modifiant ces options, vous pouvez changer le comportement lié à IntelliSense et la base de données de navigation quand vous programmez en C ou C++. Ces fonctionnalités sont véritablement expérimentales et peuvent être modifiées ou supprimées de Visual Studio dans une version ultérieure.  
  
 Pour accéder à cette page, dans la boîte de dialogue **Options** , dans le volet gauche, développez **Éditeur de texte**, **C/C++**, puis choisissez **Expérimental**.  

 Ces fonctionnalités sont disponibles dans une installation de Visual Studio 2017.  
  
> [!NOTE]
>  Il est possible que pour certains des éléments de l'interface utilisateur de Visual Studio, votre ordinateur affiche des noms ou des emplacements différents de ceux indiqués dans les instructions suivantes. L’édition de Visual Studio dont vous disposez et les paramètres que vous utilisez déterminent ces éléments. Consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="enable-predictive-intellisense"></a>Activer la fonctionnalité IntelliSense prédictive
La fonctionnalité IntelliSense prédictive limite le nombre de résultats affichés dans la liste déroulante IntelliSense afin que vous ne voyiez que les résultats qui sont pertinents dans le contexte. Par exemple, si vous tapez <code>int x =</code> et appelez la liste déroulante IntelliSense, vous voyez uniquement des entiers ou des fonctions qui retournent des entiers. La fonctionnalité IntelliSense prédictive est désactivée par défaut.

## <a name="enable-faster-project-load"></a>Activer le chargement accéléré du projet
Cette option active la fonctionnalité appelée « chargement de solution allégé ». Quand le chargement de solution allégé est activé, Visual Studio ne charge pas entièrement les projets tant que vous n’en avez pas réellement besoin. De nombreuses tâches courantes, telles que la navigation dans un code base, la modification de code et la création de projets, ne nécessitent pas le chargement du projet. Quand cette option est activée, vous pouvez démarrer plus rapidement ces tâches courantes sans avoir à attendre le chargement du projet.  

## <a name="additional-features-in-the-visual-studio-gallery"></a>Autres fonctionnalités dans la galerie Visual Studio
Pour obtenir d’autres fonctionnalités de l’éditeur de texte dans la galerie Visual Studio, consultez la liste [ici](http://go.microsoft.com/fwlink/?LinkId=692016). Par exemple, les [Corrections rapides C++](https://visualstudiogallery.msdn.microsoft.com/be91feef-8dc3-4f7a-ac9f-f34e7ca5918f)prennent en charge les éléments suivants :  
  
-   **Ajouter un #include manquant** : propose des éléments #include pertinents pour les symboles inconnus dans votre code  
  
-   **Ajouter l’espace de noms using/Symbole qualifié complet** : comme l’élément précédent, mais pour les espaces de noms  
  
-   **Ajouter un point-virgule manquant**  
  
-   **Aide MSDN** : rechercher les messages d’erreur sur MSDN  
  
 Vous pouvez soit pointer sur un tilde pour obtenir une ampoule, soit utiliser le raccourci clavier par défaut Ctrl+point [Ctrl+.]. Notez que, pour le raccourci clavier, votre signe d’insertion ne doit pas être positionné sur le jeton ou l’erreur spécifique ; vous pouvez tout simplement vous placer sur la même ligne que l’erreur pour appeler des suggestions pour tout élément sur cette ligne.  
  
## <a name="see-also"></a>Voir aussi  
 [Définition d’options d’éditeur spécifiques du langage](../../ide/reference/setting-language-specific-editor-options.md)   
 [Refactoring in C++ (blog VC)](http://blogs.msdn.com/b/vcblog/archive/2014/11/14/all-about-c-refactoring-in-visual-studio-2015-preview.aspx) (Refactorisation en C++ (blog VC)

