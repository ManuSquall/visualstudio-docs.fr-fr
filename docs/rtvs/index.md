---
title: Outils R pour Visual Studio
description: Les Outils R pour Visual Studio 2017 (RTVS) sont une extension gratuite open source qui fournit de nombreuses fonctionnalités de langage, notamment IntelliSense, le débogage et les espaces de travail à distance.
ms.date: 11/13/2017
ms.topic: overview
author: kraigb
ms.author: kraigb
manager: jmartens
ms.workload:
- data-science
ms.openlocfilehash: 76230555defd9367800f6c3c4e5ea0fe24a5195d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99946343"
---
# <a name="work-with-r-in-visual-studio"></a>Utiliser R dans Visual Studio

R est un langage très extensible et un environnement pour le calcul de statistiques et les graphiques. Il est distribué gratuitement sous la licence GNU GPL, bénéficie d’un large support de la Communauté et est connu pour sa capacité à générer des graphiques prêts pour la publication qui incluent des formules et des symboles mathématiques. Pour en savoir plus sur R, consultez [r-project.org](https://www.r-project.org/about.html) et [An Introduction to R](https://cran.r-project.org/doc/manuals/r-release/R-intro.html).

R Tools pour Visual Studio (RTVS) est une extension [open-source](https://github.com/microsoft/RTVS) gratuite pour Visual Studio 2017 et Visual Studio 2015 Update 3 (ou supérieur), publiée sous la licence MIT. (Un second composant open source appelé [RHost](https://github.com/microsoft/R-Host), qui lie les binaires de l’interpréteur R, est publié sous la licence publique GNU V2.)

> [!Note]
> Pour le moment, RTVS n’est pris en charge que dans Visual Studio 2017 sur Windows (pas dans Visual Studio pour Mac). Il n’est pas disponible pour Visual Studio 2019.

Pour utiliser R dans Visual Studio :

- [Installez R Tools](installing-r-tools-for-visual-studio.md).
- Suivez le guide [Bien démarrer](getting-started-with-r.md), ainsi que les articles [Exemples](getting-started-samples.md) et [Obtention d’aide](getting-started-help.md).

Suivez ensuite les liens ci-dessous pour en savoir plus sur les fonctionnalités de R, ainsi que sur les fonctionnalités générales de Visual Studio.

| Fonctionnalité | Description | Documentation générale de Visual Studio |
| --- | --- | --- |
| [Système de projet Visual Studio](r-projects-in-visual-studio.md) | Organisez et gérez des fichiers connexes dans une structure pratique, et aidez-vous de modèles utiles dans le code R, la documentation de R, R Markdown, les requêtes SQL et les procédures stockées. Profitez également du [Gestionnaire de package](r-package-manager-in-visual-studio.md) et de l’[intégration de SQL Server](integrating-sql-server-with-r.md).  | [Solutions et projets dans Visual Studio](../ide/solutions-and-projects-in-visual-studio.md) |
| [Espace de travail](r-workspaces-in-visual-studio.md) | Vous pouvez lier RTVS aux espaces de travail locaux et distants, ce qui vous permet de développer du code R localement à l’aide de petits jeux de données, puis de l’exécuter facilement sur des ordinateurs cloud plus puissants avec des jeux de données beaucoup plus grands. | n/a |
| [Options de R Tools](options-for-r-tools-in-visual-studio.md) | Contrôlez divers aspects de RTVS. | [Options (boîte de dialogue)](../ide/reference/options-dialog-box-visual-studio.md) |
| [Édition avancée, IntelliSense et extraits de code](editing-r-code-in-visual-studio.md) | Inclut la coloration syntaxique, [IntelliSense](r-intellisense.md) dans l’ensemble du code et des bibliothèques, la mise en forme du code, une assistance pour la signature, les fonctions Atteindre la définition et Rechercher toutes les références, des [extraits de code](code-snippets-for-r.md) et plus encore. | [Fonctionnalités de l’éditeur de code](../ide/writing-code-in-the-code-and-text-editor.md) |
| [R Markdown](rmarkdown-with-r-in-visual-studio.md) | Les documents R Markdown vous aident à partager vos résultats de données grâce à l’intégration du code R dans les blocs de code Markdown. | n/a |
| [Fenêtre interactive](interactive-repl-for-r-in-visual-studio.md) | Fournit une expérience REPL complète de R vous permettant d’exécuter facilement du code dans un fichier source de la fenêtre interactive. | n/a |
| [Visualisation des données](visualizing-data-with-r-in-visual-studio.md) | La création de graphiques est une partie intégrante de l’expérience de R, c’est pourquoi RTVS prend en charge plusieurs fenêtres de graphique indépendantes, chacune avec son propre historique et la possibilité de déplacer les graphiques d’une fenêtre à une autre. Vous pouvez enregistrer les graphiques dans des fichiers bitmap et PDF ou les copier dans le Presse-papiers comme bitmap ou métafichier.  | n/a |
| [Explorateur de variables](variable-explorer.md) | Examinez les variables d’une étendue globale ou d’une étendue spécifique à un package, avec la possibilité d’afficher des tableaux que vous pouvez trier et exporter au format CSV. | n/a |
| [Débogage complet](debugging-r-in-visual-studio.md) | Inclut l’intégration dans la fenêtre interactive. | [Débogage dans Visual Studio](../debugger/debugger-feature-tour.md) |

Voir aussi la [Foire aux questions](faq.md).

![icône de caméra pour la vidéo](../install/media/video-icon.png "Regarder une vidéo") [Regardez une vidéo (youtube.com)](https://www.youtube.com/watch?v=dll3IS1bfWQ) pour une vue d’ensemble des Outils R pour Visual Studio (12m 36s). Regardez également [d’autres vidéos sur les Outils R](https://www.youtube.com/results?search_query=R+Tools+for+visual+studio).

## <a name="send-us-your-feedback"></a>Envoyez-nous vos commentaires !

1. **Problèmes GitHub** : la meilleure façon de contacter l’équipe RTVS est de [signaler un problème sur GitHub](https://github.com/Microsoft/RTVS/issues) ou d’utiliser le menu **R Tools** > **Commentaires**.

1. **Envoyer un sourire / smiley mécontent** : le menu **R Tools** > **Commentaires** est un moyen rapide d’envoyer des commentaires et de joindre des fichiers journaux RTVS pour faciliter le diagnostic de votre problème. (Les journaux sont écrits dans *%temp%/RTVSlogs.zip* au cas où vous souhaitez les envoyer séparément.) La journalisation est désactivée si vous avez refusé la télémétrie de Visual Studio via la commande de menu **Aide** > **Commentaires** > **Paramètres** ou lors de l’installation.

1. **E-mail** : vous pouvez envoyer des commentaires directement à l’équipe *rtvsuserfeedback (at) microsoft.com*.
