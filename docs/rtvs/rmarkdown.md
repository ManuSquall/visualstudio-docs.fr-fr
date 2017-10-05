---
title: R Markdown avec les Outils R pour Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 6/29/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.devlang: r
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3ac955b2-b6e1-4d32-b1a4-2882c93311fc
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 712cc780388acc5e373f71d51fc8f1f42adb5bed
ms.openlocfilehash: b29ae0240a29616edcdf2ae0dced7a9fca0f9584
ms.contentlocale: fr-fr
ms.lasthandoff: 07/12/2017

---

# <a name="creating-r-markdown-documents"></a>Création de documents R Markdown

[R Markdown](https://rmarkdown.rstudio.com/) est un format de document qui convertit l’analyse dans R en documents, rapports, présentations et tableaux de bord de haute qualité.

Les outils R pour Visual Studio (RTVS) fournissent un modèle d’élément R Markdown, la prise en charge d’éditeur (notamment IntelliSense pour le code R dans l’éditeur) et des fonctionnalités de génération de fichier.

Pour utiliser R Markdown

1. Fermez Visual Studio.
1. (Une seule fois) Installez `pandoc` à partir de [pandoc.org](http://pandoc.org/installing.html).
1. Redémarrez Visual Studio. L’installation de pandoc doit être détectée.
1. Installez les packages `knitr` et `rmarkdown`, ce que vous pouvez faire à partir de la [Fenêtre interactive](interactive-repl.md) :

    ```R
    install.packages("knitr")
    install.packages("rmarkdown")

    ```
1. Créez un fichier R Markdown en utilisant la commande de menu **Fichier > Nouveau** et en sélectionnant **R Markdown** dans la liste, ou en double-cliquant sur votre projet dans l’Explorateur de solutions et en sélectionnant **Ajouter un fichier Markdown R** (ou **Ajouter > Nouvel élément** et **R Markdown** dans la liste).

1. Le contenu par défaut du nouveau fichier est le suivant :

    ~~~markdown
    ---
    title: "Untitled"
    output: html_document
    ---
    
    This is an R Markdown document. Markdown is a simple formatting syntax for authoring HTML, PDF, and Microsoft Word documents. For more details on using R Markdown see <http://rmarkdown.rstudio.com>.
    
    When you click the **R Tools | Publish | Preview** button a document will be generated that includes both content as well as the output of any embedded R code chunks within the document. You can embed an R code chunk like this:
    
    ```{r}
    summary(cars)
    ```
    
    You can also embed plots, for example:
    
    ```{r, echo=FALSE}
    plot(cars)
    ```
    
    Note that the `echo = FALSE` parameter was added to the code chunk to prevent printing of the R code that generated the plot.
    
    ~~~

1. À tout moment lors de l’édition, cliquez avec le bouton droit dans l’éditeur, puis sélectionnez **Aperçu** pour afficher des options pour HTML, PDF et Microsoft Word. À partir de cet aperçu, vous pouvez enregistrer le fichier au format de votre choix.

