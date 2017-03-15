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
ms.sourcegitcommit: a1edc88394193474b273968d8435e8df06415044
ms.openlocfilehash: a3fcafe5c191987668dc6e0dce8835d748742ed7
ms.lasthandoff: 02/22/2017

---
# <a name="options-text-editor-cc-experimental"></a>Options, Éditeur de texte, C/C++, Expérimental
En modifiant ces options, vous pouvez changer le comportement lié à IntelliSense et la base de données de navigation quand vous programmez en C ou C++.  
  
 Pour accéder à cette page, dans la boîte de dialogue **Options** , dans le volet gauche, développez **Éditeur de texte**, **C/C++**, puis choisissez **Expérimental**.  
  
 Ces fonctionnalités sont disponibles dans une installation de Visual Studio 2015 Update 1 RC.  
  
> [!NOTE]
>  Il est possible que pour certains des éléments de l’interface utilisateur de Visual Studio, votre ordinateur affiche des noms ou des emplacements différents de ceux indiqués dans les instructions suivantes. L’édition de Visual Studio dont vous disposez et les paramètres que vous utilisez déterminent ces éléments. Consultez [Personnalisation des paramètres de développement dans Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="browsingnavigation"></a>Navigation de fichiers/répertoires  
 **Activer le nouveau moteur de base de données**  
 Cela doit automatiquement accélérer le remplissage de la base de données et toutes les opérations de base de données (sans perte de précision) pour les opérations comme **Atteindre la définition** et **Rechercher toutes les références**. (Il vous suffit de fermer et rouvrir votre solution pour appliquer les modifications ; vous n’êtes pas obligé de redémarrer Visual Studio.)  
  
## <a name="intellisense"></a>IntelliSense  
 **« Point par flèche » pour la liste des membres**  
 Remplace « . » par « -> » le cas échéant pour la liste des membres.  
  
## <a name="refactoring"></a>Refactorisation  
 **Activer Extraire la fonction**  
 Extrayez le code sélectionné dans sa propre fonction et remplacez le code par un appel à la nouvelle fonction. Pour accéder à cette fonctionnalité, cliquez avec le bouton droit sur le code sélectionné et sélectionnez **Actions rapides**, ou appuyez simplement sur le raccourci par défaut Ctrl+point [Ctrl+.].  
  
 **Activer Modifier la signature**  
 Ajoutez, réorganisez et supprimez les paramètres d’une fonction, et propagez les modifications à tous les sites d’appel. Pour accéder à cette fonctionnalité, cliquez avec le bouton droit sur toute utilisation de la fonction et sélectionnez **Actions rapides**, ou appuyez simplement sur le raccourci par défaut Ctrl+point [Ctrl+.].  
  
## <a name="text-editor"></a>Éditeur de texte  
 **Activer Développer la portée**  
 Si cette option est activée, vous pouvez entourer le texte sélectionné d’accolades en tapant « { » dans l’éditeur de texte.  
  
 **Activer Développer la priorité**  
 Si cette option est activée, vous pouvez entourer le texte sélectionné de parenthèses en tapant « ( » dans l’éditeur de texte.  
  
 Pour obtenir d’autres fonctionnalités de l’éditeur de texte dans la galerie Visual Studio, consultez la liste [ici](http://go.microsoft.com/fwlink/?LinkId=692016). Par exemple, les [Corrections rapides C++](https://visualstudiogallery.msdn.microsoft.com/be91feef-8dc3-4f7a-ac9f-f34e7ca5918f)prennent en charge les éléments suivants :  
  
-   **Ajouter un #include manquant** : propose des éléments #include pertinents pour les symboles inconnus dans votre code  
  
-   **Ajouter l’espace de noms using/Symbole qualifié complet** : comme l’élément précédent, mais pour les espaces de noms  
  
-   **Ajouter un point-virgule manquant**  
  
-   **Aide MSDN** : rechercher les messages d’erreur sur MSDN  
  
 Vous pouvez soit pointer sur un tilde pour obtenir une ampoule, soit utiliser le raccourci clavier par défaut Ctrl+point [Ctrl+.]. Notez que, pour le raccourci clavier, votre signe d’insertion ne doit pas être positionné sur le jeton ou l’erreur spécifique ; vous pouvez tout simplement vous placer sur la même ligne que l’erreur pour appeler des suggestions pour tout élément sur cette ligne.  
  
## <a name="see-also"></a>Voir aussi  
 [Définition d’options d’éditeur spécifiques du langage](../../ide/reference/setting-language-specific-editor-options.md)   
 [Refactoring in C++ (blog VC)](http://blogs.msdn.com/b/vcblog/archive/2014/11/14/all-about-c-refactoring-in-visual-studio-2015-preview.aspx) (Refactorisation en C++ (blog VC)

