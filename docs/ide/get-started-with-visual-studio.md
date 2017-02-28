---
title: "Bien démarrer avec Visual Studio | Microsoft Docs"
description: "Découvrez comment bien démarrer avec Visual Studio."
ms.custom: 
ms.date: 12/05/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio, getting started
ms.assetid: 38e90339-1da5-410c-8ba4-437fc556cba7
caps.latest.revision: 65
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
ms.sourcegitcommit: 27493b53229d9ceb6bc215fcf3d57a60fe4358b0
ms.openlocfilehash: 452f8dbd2c7eb4bcc2f0310da1f04c6dd031f629
ms.lasthandoff: 02/22/2017

---
# <a name="get-started-with-visual-studio"></a>Bien démarrer avec Visual Studio

Visual Studio est un outil puissant pour développer vos applications. Si ce n’est déjà fait, téléchargez et installez [Visual Studio](https://aka.ms/vs/15/preview/vs_enterprise). Regardez la vidéo sur le [démarrage de Visual Studio et la configuration de votre IDE](https://www.youtube.com/watch?v=xLCedknQkN0&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK&index=1) pour plus d’informations sur le téléchargement et la configuration de Visual Studio.

## <a name="visual-studio-tour"></a>Visite guidée de Visual Studio
Visual Studio comporte un groupe de fenêtres d’outils, de menus et de barres d’outils collectivement appelés « environnement de développement intégré » ou IDE. L’IDE Visual Studio vous permet d’accomplir vos tâches de développement. Voici un aperçu des éléments de l’IDE que vous utiliserez probablement le plus souvent.

### <a name="code-editor"></a>Éditeur de code
L’une des fenêtres d’outils les plus utilisées dans Visual Studio. C’est là que vous écrivez, affichez et parcourez votre code.

![Éditeur de code](../ide/media/VSIDE_CodeWindow.png)

L’éditeur de code permet d’accélérer l’écriture du code grâce à des fonctionnalités telles que la saisie semi-automatique des instructions, la coloration syntaxique, le mode de mappage et plus encore. Pour plus d’informations, regardez la vidéo sur le [démarrage de Visual Studio et sur la modification et la navigation dans votre code](https://www.youtube.com/watch?v=4glwwioCVjA&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK&index=5).

Certains types de solutions peuvent inclure des formulaires, tels que WPF ou Windows Forms. Dans ces cas-là, vous verrez également un concepteur visuel dans cet espace, qui vous permet d’ajouter visuellement des contrôles au formulaire, tels que des boutons et des zones de liste.

### <a name="solution-explorer"></a>Explorateur de solutions

Une fenêtre d’outils appelée **Explorateur de solutions** répertorie tous les fichiers de votre code. L’Explorateur de solutions peut vous aider à organiser votre code en regroupant ses fichiers dans des projets et des solutions. Le projet en gras est appelé projet de démarrage. C’est le premier code qui s’exécute quand vous démarrez votre solution. Vous pouvez modifier le projet de démarrage. Pour plus d’informations, regardez la vidéo sur le [démarrage de Visual Studio et les composantes de l’IDE)](https://www.youtube.com/watch?v=JHc3_gsCmZg&index=2&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK).

![Nœuds réduits dans l’Explorateur de solutions](../ide/media/VSIDE_SolutionExplorer2_callouts.png)

 En plus des projets et des solutions, l’Explorateur de solutions répertorie tous les fichiers de chaque projet quand vous développez le nœud du projet. Chaque projet contient un ou plusieurs fichiers, tels que les fichiers de code source et les fichiers de ressources comme les images ou les bibliothèques.

![Explorateur de solutions](../ide/media/VSIDE_SolutionExplorer3.png)

Pour afficher les propriétés des fichiers, projets et solutions, choisissez la commande **Propriétés** dans le menu contextuel (clic droit), ou choisissez **Affichage, Fenêtre Propriétés** dans le menu.

![Fenêtre Propriétés](../ide/media/VSIDE_SolutionExplorer4.png)

Vous n’êtes toutefois pas obligé de créer une solution ou un projet pour commencer le code. Vous pouvez simplement ouvrir des fichiers de code dans Visual Studio, tels que des fichiers clonés à partir d’un dépôt Git, et commencer à les modifier immédiatement. Les fichiers s’affichent dans l’Explorateur de solutions et vous donnent accès à la coloration syntaxique, la saisie semi-automatique des instructions de base et bien plus encore, tout comme avec les solutions traditionnelles. Pour plus d’informations, consultez [Open Any Folder (Ouvrir un dossier quelconque)](https://blogs.msdn.microsoft.com/visualstudio/2016/04/12/open-any-folder-with-visual-studio-15-preview/).

### <a name="toolbar-and-menus"></a>Barre d’outils et menus
Pour exécuter votre projet, créer des solutions, enregistrer des fichiers et bien plus encore, utilisez les commandes de menu et de barre d’outils de Visual Studio. Par exemple, une fois que votre code est prêt à s’exécuter pour le débogage, vous pouvez choisir le bouton **Démarrer** dans la barre d’outils, ou choisir **Déboguer, Démarrer le débogage** dans le menu. Pour créer une solution, choisissez le bouton **Nouveau projet**, ou choisissez **Fichier, Nouveau, Projet** dans le menu, et ainsi de suite.

![Barre d’outils de Visual Studio](../ide/media/VSIDE_SolutionExplorer5_callouts.png)

Notez que les commandes de menu et les icônes de barre d’outils peuvent changer en fonction du contexte (c’est-à-dire de l’élément actuellement sélectionné).

### <a name="team-explorer"></a>Team Explorer
**Team Explorer** vous permet de vous connecter à des outils de contrôle de code source tels que [Git](https://git-scm.com/) et [Team Foundation Version Control (TFVC)](https://www.visualstudio.com/en-us/docs/tfvc/overview) pour stocker votre code localement ou le partager avec d’autres utilisateurs sur un service hébergé. Vous pouvez également l’utiliser pour effectuer le suivi des tâches et bien plus encore.

Pour plus d’informations, regardez les vidéos sur le [démarrage de Visual Studio et les composantes de l’IDE](https://www.youtube.com/watch?v=JHc3_gsCmZg&index=2&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK) et sur le [démarrage de Visual Studio et l’ouverture d’un projet à partir du contrôle de code Source](https://www.youtube.com/watch?v=pc9vX_4RGV4&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK&index=3).

![Team Explorer](../ide/media/TeamExplorer.png)

### <a name="output-window"></a>Fenêtre Sortie
La fenêtre **Sortie** est l’emplacement où Visual Studio envoie ses notifications, telles que les messages d’erreur et de débogage, les avertissements du compilateur, les messages d’état de publication, et ainsi de suite. Chaque type de message a son propre onglet.

![Fenêtre Sortie](../ide/media/VSIDE_OutputWindow.png)

Pour en savoir plus sur l’utilisation de la fenêtre de sortie pour le débogage, consultez [Fenêtre Sortie pendant le débogage avec Visual Studio](https://blogs.msdn.microsoft.com/visualstudioalm/2015/02/09/the-output-window-while-debugging-with-visual-studio/).

## <a name="first-steps"></a>Premières étapes
- **Installation** - Pour en savoir plus sur le téléchargement et l’installation de Visual Studio, consultez [Setup & Installation](https://go.microsoft.com/fwlink/?linkid=833223).
- **Notions de base** - Pour en savoir plus sur le fonctionnement de Visual Studio, consultez [Bien démarrer avec le développement dans Visual Studio](../ide/get-started-developing-with-visual-studio.md).
- **Paramètres** - Personnalisez Visual Studio à votre goût. Consultez [Personnalisation de l’IDE de Visual Studio](https://msdn.microsoft.com/en-us/library/mt269425.aspx).
- **Didacticiels** - Pour plus d’informations sur le développement de code dans Visual Studio, suivez un didacticiel, tel que [Mises en route de Visual Basic et Visual C#](https://msdn.microsoft.com/en-us/library/dd492171.aspx) ou [Mise en route de C++ dans Visual Studio](https://msdn.microsoft.com/en-us/library/jj620919.aspx).
- **Vidéos** - Pour plus d’informations sur d’autres fonctionnalités et aspects de Visual Studio, regardez les vidéos sur le [canal de Microsoft Visual Studio](https://www.youtube.com/user/VisualStudio/videos) sur YouTube ou les vidéos Visual Studio sur [Channel 9](https://channel9.msdn.com/Tags/visual+studio).

## <a name="access-cloud-based-resources"></a>Accéder aux ressources cloud

Si vous souhaitez utiliser des ressources cloud dans votre application ou votre jeu, vous pouvez inclure des [services Azure](https://azure.microsoft.com/en-us/services/). Vous pouvez obtenir le kit SDK Azure pour .NET en installant le contenu d’Azure à l’aide du nouveau programme d’installation de Visual Studio. Les packages installés sont au même niveau de fonctionnalité que la version 2.9.5 du kit SDK. Pour cette version de Visual Studio et toutes les versions futures, le kit SDK Azure pour .NET est seulement disponible à partir du programme d’installation de Visual Studio.

Une fois que vous avez installé le kit SDK Azure pour .NET, une nouvelle fenêtre d’outils appelée **Cloud Explorer** est disponible dans Visual Studio. Cloud Explorer vous permet de parcourir et de gérer vos ressources Azure à partir de Visual Studio. Si une opération particulière nécessite le portail Azure, Cloud Explorer fournit des liens vers l’emplacement du portail Azure auquel vous devez accéder.

![Cloud Explorer](../ide/media/VSIDE_CloudExplorer.png)

Pour en savoir plus sur l’utilisation de Cloud Explorer, consultez [Gestion des ressources Azure avec Cloud Explorer](https://azure.microsoft.com/en-us/documentation/articles/vs-azure-tools-resources-managing-with-cloud-explorer/).
L’installation du kit SDK Azure vous donne également accès à [Visual Studio Tools pour Azure](https://www.visualstudio.com/vs/azure-tools/) et à d’autres outils.

## <a name="tips-and-tricks"></a>Conseils et astuces
Pour obtenir des raccourcis et des conseils et astuces pratiques qui vous permettront de tirer le meilleur parti de Visual Studio, consultez les rubriques suivantes.
- [Getting Started with Visual Studio - Tips & Tricks (Bien démarrer avec Visual Studio - Conseils et astuces)](https://www.youtube.com/watch?v=vmXqGwn1Glk&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK&index=4)
- [Conseils de productivité pour Visual Studio](https://msdn.microsoft.com/en-us/library/jj153218.aspx)
- [Visual Studio Tips and Tricks (Conseils et astuces Visual Studio)](https://channel9.msdn.com/events/TechEd/2013/DEV-B353)
- [C++ Debugging Tips and Tricks (Conseils et astuces pour le débogage C++)](https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/C-Plus-Plus-Debugging-Tips-and-Tricks)
- [Getting Started with Visual Studio - Installing Visual Studio extensions (Bien démarrer avec Visual Studio - Installation des extensions Visual Studio)](https://www.youtube.com/watch?v=MWLLQaknRZY&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK&index=7)

