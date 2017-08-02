---
title: R Tools pour Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 6/29/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-r
ms.devlang: r
ms.tgt_pltfrm: 
ms.topic: hero-article
ms.assetid: 11324501-ceb6-47a2-ae13-e9e992d3603e
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 712cc780388acc5e373f71d51fc8f1f42adb5bed
ms.openlocfilehash: 80a10c710aac8413bd59b53bb61de7a982c09952
ms.contentlocale: fr-fr
ms.lasthandoff: 07/12/2017

---

# <a name="working-with-r-in-visual-studio"></a>Utilisation de R dans Visual Studio

R est un langage très extensible et un environnement pour le calcul de statistiques et les graphiques. Il est distribué gratuitement sous la licence GNU GPL, bénéficie d’un large support de la Communauté et est connu pour sa capacité à générer des graphiques prêts pour la publication qui incluent des formules et des symboles mathématiques. Pour en savoir plus sur R, consultez [r-project.org](https://www.r-project.org/about.html) et [An Introduction to R](https://cran.r-project.org/doc/manuals/r-release/R-intro.html).

R Tools pour Visual Studio (RTVS) est une extension [open-source](https://github.com/microsoft/RTVS) gratuite pour Visual Studio 2017 et Visual Studio 2015 Update 3 (ou supérieur), publiée sous la licence MIT. (Un second composant open source appelé [RHost](https://github.com/microsoft/R-Host), qui lie les binaires de l’interpréteur R, est publié sous la licence publique GNU V2.)

Pour utiliser R dans Visual Studio :

- [Installez R Tools](installation.md).
- Suivez le guide [Bien démarrer](getting-started-with-r.md), ainsi que les rubriques [Exemples](getting-started-samples.md) et [Obtention d’aide](getting-started-help.md).

Suivez ensuite les liens pour en savoir plus sur les fonctionnalités de R, ainsi que sur les fonctionnalités générales de Visual Studio.

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

La vidéo suivante présente aussi brièvement (5m 48s) les fonctionnalités de R Tools :

> [!VIDEO https://www.youtube.com/embed/RcSDEfMgUvU]

## <a name="frequently-asked-questions"></a>Questions fréquemment posées

**Q. RTVS fonctionne-t-il avec les éditions Visual Studio Express ?**

R. Non.

**Q. Avec quels interpréteurs R fonctionne RTVS ?**

R. [CRAN R](https://cran.r-project.org/), [Microsoft R Client et Microsoft R Server](https://msdn.microsoft.com/microsoft-r/)

**Q. Où puis-je télécharger ces interpréteurs ?**

R. Consultez [Installation](installation.md).

**Q. Puis-je utiliser des extensions Visual Studio avec RTVS ?**

R. Absolument. Voici quelques exemples que les utilisateurs de R utilisent couramment.

- [VsVim pour les combinaisons de touches vim](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim)
- [Github](https://marketplace.visualstudio.com/items?itemName=GitHub.GitHubExtensionforVisualStudio)
- [Éditeur Markdown avec aperçu instantané](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.MarkdownEditor)

Pour en savoir plus, consultez [Visual Studio Marketplace](https://marketplace.visualstudio.com/).

**Q. Étant donné que RTVS se trouve dans Visual Studio, R peut-il être facilement utilisé avec C#, C++ et d’autres langages Microsoft ?**

R. Non. RTVS est un outil de développement de code R qui utilise les interpréteurs R natifs standard. Aucune interopérabilité entre R et d’autres langages n’est prise en charge actuellement.

**Q. La fonctionnalité X n’existe pas ? Si, dans RStudio !**

R. RStudio est un IDE fantastique et abouti pour R qui est resté en phase de développement pendant de nombreuses années. Le but de RTVS est d’avoir toutes les fonctionnalités essentielles dont vous avez besoin pour réussir. Aidez-nous à définir les priorités de nos prochains travaux en répondant à l’[enquête RTVS](https://www.surveymonkey.com/r/RTVS1).

**Q. RTVS fonctionne-t-il sur OS X ou Linux ?**

R. Non, RTVS repose sur Visual Studio, qui est une implémentation Windows uniquement. Ceci dit, Microsoft cherche à créer un nouvel ensemble d’outils basés sur [Visual Studio Code](https://code.visualstudio.com/), l’éditeur multiplateforme connu de Microsoft.

**Q. Puis-je contribuer à RTVS ?**

R. Absolument ! Le code source se trouve sur [Github](https://github.com/microsoft/RTVS). Utilisez le suivi des problèmes pour envoyer des bogues et des commentaires sur ces fichiers.

Vous êtes également invité à contribuer à cette documentation&mdash; sélectionnez simplement la commande **Modifier** en haut à droite de chaque page. Vos commentaires sur la documentation sont également bienvenus. Vous pouvez en ajouter en bas de chaque page.

**Q. RTVS fonctionne-t-il avec mon système de gestion de code source ?**

R. Oui, vous pouvez utiliser n’importe quel système de gestion de code source intégré à Visual Studio.

**Q. RTVS fonctionne-t-il avec des paramètres régionaux non anglais ?**

R. La version 1.0 de RTVS est en anglais uniquement. La version 1.1 sera localisée dans les mêmes langues que celles de Visual Studio. En attendant, utilisez le [module linguistique en anglais de Visual Studio 2015](https://www.microsoft.com/download/details.aspx?id=48157) ou dans Visual Studio 2017, exécutez le programme d’installation et sélectionnez Anglais dans l’onglet **Modules linguistiques**.

![Paramètres internationaux de Visual Studio 2017](~/docs/rtvs/media/FAQ-international-settings.png)

**Q. RTVS fonctionne-t-il avec les éditions 32 bits de R ?**

R. Non, RTVS prend uniquement en charge les éditions 64 bits de R exécutées sur les éditions 64 bits de Windows.

**Q. J’aime vraiment mes paramètres Visual Studio actuels, mais je veux tester les nouveaux paramètres de science des données. Que dois-je faire ?**

R. Enregistrez vos paramètres Visual Studio actuels en accédant à **Outils > Importer et exporter les paramètres...**, puis remplacez-les par les paramètres de science des données. Pour restaurer les paramètres enregistrés, utilisez à nouveau la commande **Importer et exporter les paramètres...**.

**Q. Quels sont les paramètres `.gitignore` recommandés pour un projet RTVS ?**

R. Github conserve un dépôt principal des fichiers `.gitignore` recommandés. Vous le trouverez ici : [R .gitignore](https://github.com/github/gitignore/blob/master/R.gitignore)

**Q. Puis-je stocker mon projet Visual Studio sur un partage réseau ?**

R. Non, Visual Studio ne prend pas en charge le chargement des projets à partir d’un partage réseau.

## <a name="send-us-your-feedback"></a>Envoyez-nous vos commentaires !

1. **Problèmes Github** : la meilleure façon de contacter l’équipe RTVS est de [signaler un problème sur GitHub](https://github.com/Microsoft/RTVS/issues) ou d’utiliser le menu **R Tools > Commentaires**.

1. **Envoyer un sourire / smiley mécontent** : le menu **R Tools > Commentaires** est un moyen rapide d’envoyer des commentaires et de joindre des fichiers journaux RTVS pour faciliter le diagnostic de votre problème. (Les journaux sont écrits dans `%temp%/RTVSlogs.zip` au cas où vous souhaitez les envoyer séparément.) La journalisation est désactivée si vous avez refusé la télémétrie de Visual Studio via la commande de menu **Aide > Commentaires > Paramètres** ou lors de l’installation.

1. **E-mail** : vous pouvez envoyer des commentaires directement à l’équipe *rtvsuserfeedback (at) microsoft.com*.

