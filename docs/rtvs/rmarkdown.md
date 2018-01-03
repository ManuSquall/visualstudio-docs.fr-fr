---
title: R Markdown avec les Outils R pour Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 11/16/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-r
ms.devlang: r
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: "1"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload: data-science
ms.openlocfilehash: 340ab0b55de1bb6c5889bb15560065d71e438ca6
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="creating-r-markdown-documents"></a>Création de documents R Markdown

[R Markdown](https://rmarkdown.rstudio.com/) est un format de document qui convertit l’analyse dans R en documents, rapports, présentations et tableaux de bord de haute qualité.

Les outils R pour Visual Studio (RTVS) fournissent un modèle d’élément R Markdown, la prise en charge d’éditeur (notamment IntelliSense pour le code R dans l’éditeur), des fonctionnalités de génération de fichier et un aperçu instantané.

## <a name="using-r-markdown"></a>Utilisation de R Markdown

1. Fermez Visual Studio.
1. (Une seule fois) Installez `pandoc` à partir de [pandoc.org](http://pandoc.org/installing.html).
1. Redémarrez Visual Studio. L’installation de pandoc doit être détectée.
1. Installez les packages `knitr` et `rmarkdown`, ce que vous pouvez faire à partir de la [Fenêtre interactive](interactive-repl.md) :

    ```R
    install.packages("knitr")
    install.packages("rmarkdown")

    ```
1. Créez un fichier R Markdown à l’aide de la commande de menu **Fichier > Nouveau > Fichier** et en sélectionnant **R > R Markdown** dans la liste. Dans le contexte d’un projet, cliquez avec le bouton droit sur le projet dans l’Explorateur de solutions et sélectionnez **Ajouter R Markdown** (ou **Ajouter > Nouvel élément...**  et sélectionnez **R Markdown** dans la liste).

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

## <a name="previews"></a>Versions d'évaluation

Visual Studio 2017 versions 15.5 et ultérieures fournissent automatiquement un aperçu instantané pour R Markdown. Pour activer la synchronisation automatique entre l’éditeur et l’aperçu, sélectionnez **Outils R > Markdown > Synchronisation automatique** (Ctrl+Maj+Y). Si vous n’utilisez pas la synchronisation automatique, vous pouvez actualiser l’aperçu en utilisant **Outils R > Markdown > Recharger l’aperçu R Markdown**.

Vous pouvez également afficher un aperçu du fichier au format HTML, PDF et Microsoft Word en cliquant avec le bouton droit dans l’éditeur et en sélectionnant une des commandes **Aperçu**. Les mêmes commandes sont également disponibles dans le menu **Outils R > Markdown**. (Dans les versions antérieures de Visual Studio, ces commandes se trouvent dans le menu **Outils R > Publier**.)

![Aperçu instantané R Markdown et autres commandes de menu d’aperçu](media/rmarkdown-live-preview.png)
