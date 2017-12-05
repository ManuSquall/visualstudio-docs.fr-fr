---
title: R Tools pour Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 11/13/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-r
ms.devlang: r
ms.tgt_pltfrm: 
ms.topic: hero-article
caps.latest.revision: "1"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.openlocfilehash: 1ff32914b523b2b515a3d4175e4b3f76ad7ecefd
ms.sourcegitcommit: ae9450e81c4167b3fbc9ee5d1992fc693628eafa
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/04/2017
---
# <a name="working-with-r-in-visual-studio"></a>Utilisation de R dans Visual Studio

R est un langage très extensible et un environnement pour le calcul de statistiques et les graphiques. Il est distribué gratuitement sous la licence GNU GPL, bénéficie d’un large support de la Communauté et est connu pour sa capacité à générer des graphiques prêts pour la publication qui incluent des formules et des symboles mathématiques. Pour en savoir plus sur R, consultez [r-project.org](https://www.r-project.org/about.html) et [An Introduction to R](https://cran.r-project.org/doc/manuals/r-release/R-intro.html).

R Tools pour Visual Studio (RTVS) est une extension [open-source](https://github.com/microsoft/RTVS) gratuite pour Visual Studio 2017 et Visual Studio 2015 Update 3 (ou supérieur), publiée sous la licence MIT. (Un second composant open source appelé [RHost](https://github.com/microsoft/R-Host), qui lie les binaires de l’interpréteur R, est publié sous la licence publique GNU V2.)

> [!Note]
> Pour le moment, RTVS n’est pris en charge que dans Visual Studio sous Windows, et non Visual Studio pour Mac.

Pour utiliser R dans Visual Studio :

- [Installez R Tools](installation.md).
- Suivez le guide [Bien démarrer](getting-started-with-r.md), ainsi que les rubriques [Exemples](getting-started-samples.md) et [Obtention d’aide](getting-started-help.md).

Suivez ensuite les liens ci-dessous pour en savoir plus sur les fonctionnalités de R, ainsi que sur les fonctionnalités générales de Visual Studio.

| Fonctionnalité | Description | Documentation générale de Visual Studio | 
| --- | --- | --- |
| [Système de projet Visual Studio](projects.md) | Organisez et gérez des fichiers connexes dans une structure pratique, et aidez-vous de modèles utiles dans le code R, la documentation de R, R Markdown, les requêtes SQL et les procédures stockées. Profitez également du [Gestionnaire de package](package-manager.md) et de l’[intégration de SQL Server](sql-server.md).  | [Solutions et projets dans Visual Studio](../ide/solutions-and-projects-in-visual-studio.md) |
| [Espace de travail](workspaces.md) | Vous pouvez lier RTVS aux espaces de travail locaux et distants, ce qui vous permet de développer du code R localement à l’aide de petits jeux de données, puis de l’exécuter facilement sur des ordinateurs cloud plus puissants avec des jeux de données beaucoup plus grands. | N/A |
| [Options de R Tools](options.md) | Contrôlez divers aspects de RTVS. | [Boîte de dialogue Options](../ide/reference/options-dialog-box-visual-studio.md) |
| [Édition avancée, IntelliSense et extraits de code](code-editing.md) | Inclut la coloration syntaxique, [IntelliSense](code-intellisense.md) dans l’ensemble du code et des bibliothèques, la mise en forme du code, une assistance pour la signature, les fonctions Atteindre la définition et Rechercher toutes les références, des [extraits de code](code-snippets.md) et plus encore. | [Écriture de code dans l’éditeur de code et de texte](../ide/writing-code-in-the-code-and-text-editor.md) |
| [R Markdown](rmarkdown.md) | Les documents R Markdown vous aident à partager vos résultats de données grâce à l’intégration du code R dans les blocs de code Markdown. | N/A |
| [Fenêtre interactive](interactive-repl.md) | Fournit une expérience REPL complète de R vous permettant d’exécuter facilement du code dans un fichier source de la fenêtre interactive. | N/A |
| [Visualisation des données](visualizing-data.md) | La création de graphiques est une partie intégrante de l’expérience de R, c’est pourquoi RTVS prend en charge plusieurs fenêtres de graphique indépendantes, chacune avec son propre historique et la possibilité de déplacer les graphiques d’une fenêtre à une autre. Vous pouvez enregistrer les graphiques dans des fichiers bitmap et PDF ou les copier dans le Presse-papiers comme bitmap ou métafichier.  | N/A |
| [Explorateur de variables](variable-explorer.md) | Examinez les variables d’une étendue globale ou d’une étendue spécifique à un package, avec la possibilité d’afficher des tableaux que vous pouvez trier et exporter au format CSV. | N/A |
| [Débogage complet](debugging.md) | Inclut l’intégration dans la fenêtre interactive. | [Débogage dans Visual Studio](../debugger/debugging-in-visual-studio.md) |

Voir aussi la [Foire aux questions](faq.md).

La vidéo suivante présente aussi brièvement (5m 48s) les fonctionnalités de R Tools :

> [!VIDEO https://www.youtube.com/embed/RcSDEfMgUvU]

## <a name="send-us-your-feedback"></a>Envoyez-nous vos commentaires !

1. **Problèmes Github** : la meilleure façon de contacter l’équipe RTVS est de [signaler un problème sur GitHub](https://github.com/Microsoft/RTVS/issues) ou d’utiliser le menu **R Tools > Commentaires**.

1. **Envoyer un sourire / smiley mécontent** : le menu **R Tools > Commentaires** est un moyen rapide d’envoyer des commentaires et de joindre des fichiers journaux RTVS pour faciliter le diagnostic de votre problème. (Les journaux sont écrits dans `%temp%/RTVSlogs.zip` au cas où vous souhaitez les envoyer séparément.) La journalisation est désactivée si vous avez refusé la télémétrie de Visual Studio via la commande de menu **Aide > Commentaires > Paramètres** ou lors de l’installation.

1. **E-mail** : vous pouvez envoyer des commentaires directement à l’équipe *rtvsuserfeedback (at) microsoft.com*.
