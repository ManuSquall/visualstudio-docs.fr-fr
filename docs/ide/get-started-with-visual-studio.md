---
redirect_url: ../ide/visual-studio-ide
ms.openlocfilehash: a615a3a6da289f265e350d529349f1fb6ba6865f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2017
---
# <a name="get-started-with-visual-studio"></a>Bien démarrer avec Visual Studio
Visual Studio est un outil puissant pour développer vos applications. Si ce n’est déjà fait, téléchargez et installez [Visual Studio](https://www.visualstudio.com/vs/). Regardez la vidéo sur la [mise en route de Visual Studio et la configuration de votre environnement de développement intégré](https://www.youtube.com/watch?v=xLCedknQkN0&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK&index=1) pour plus d’informations sur le téléchargement et la configuration de Visual Studio.

## <a name="visual-studio-tour"></a>Visite guidée de Visual Studio
Visual Studio comporte un groupe de fenêtres d’outils, de menus et de barres d’outils collectivement appelés « environnement de développement intégré » ou IDE. L’IDE Visual Studio vous permet d’accomplir vos tâches de développement. Voici un aperçu des éléments de l’IDE que vous utiliserez probablement le plus souvent.

### <a name="code-editor"></a>Éditeur de code
L’une des fenêtres d’outils les plus utilisées dans Visual Studio. C’est là que vous écrivez, affichez et parcourez votre code.

![Éditeur de code](../ide/media/VSIDE_CodeWindow.png)

L’éditeur de code permet d’accélérer l’écriture du code grâce à des fonctionnalités telles que la saisie semi-automatique des instructions, la coloration syntaxique, le mode de mappage et plus encore. Pour plus d’informations, regardez la vidéo sur le [démarrage de Visual Studio et sur la modification et la navigation dans votre code](https://www.youtube.com/watch?v=4glwwioCVjA&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK&index=5).

Certains types de solutions peuvent inclure des fenêtres appelées *formulaires*, comme, par exemple, des formulaires Windows Presentation Foundation (WPF), des formulaires Windows, des formulaires Extensible Application Markup Language (XAML). Dans ces cas-là, vous verrez également un concepteur visuel dans cet espace, qui vous permet de glisser et déposer des contrôles, tels que des boutons et des zones de liste vers le formulaire avec lequel les utilisateurs interagissent lorsqu’ils exécutent votre application.

### <a name="solution-explorer"></a>Explorateur de solutions
Une fenêtre d’outils appelée **Explorateur de solutions** répertorie tous les fichiers de votre code. L’Explorateur de solutions peut vous aider à organiser votre code en regroupant ses fichiers dans des projets et des solutions. Le projet en gras est appelé *projet de démarrage*. Il s’agit du premier code qui s’exécute quand vous démarrez votre solution. Vous pouvez modifier le projet de démarrage. Pour plus d’informations, regardez la vidéo sur la [mise en route de Visual Studio et les composantes de l’environnement de développement intégré](https://www.youtube.com/watch?v=JHc3_gsCmZg&index=2&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK).

![Nœuds réduits dans l’Explorateur de solutions](../ide/media/VSIDE_SolutionExplorer2_callouts.png)

 En plus des projets et des solutions, l’Explorateur de solutions répertorie tous les fichiers de chaque projet quand vous développez le nœud du projet. Chaque projet contient un ou plusieurs fichiers, tels que les fichiers de code source et les fichiers de ressources comme les images ou les bibliothèques.

![Explorateur de solutions](../ide/media/VSIDE_SolutionExplorer3.png)

Pour afficher les propriétés des fichiers, projets et solutions, choisissez la commande **Propriétés** dans le menu contextuel (clic droit), ou choisissez **Affichage, Fenêtre Propriétés** dans le menu.

![Fenêtre Propriétés](../ide/media/VSIDE_SolutionExplorer4.png)

Vous n’êtes toutefois pas obligé de créer une solution ou un projet pour commencer le code. Vous pouvez simplement ouvrir des fichiers de code dans Visual Studio, tels que des fichiers clonés à partir d’un dépôt Git, et commencer à les modifier immédiatement. Les fichiers s’affichent dans l’Explorateur de solutions et vous donnent accès à la coloration syntaxique, la saisie semi-automatique des instructions de base et bien plus encore, tout comme avec les solutions traditionnelles. Consultez [Développer du code dans Visual Studio sans projets ni solutions](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) pour obtenir plus d’informations.

### <a name="toolbar-and-menus"></a>Barre d’outils et menus
Pour exécuter votre projet, créer des solutions, enregistrer des fichiers et bien plus encore, utilisez les commandes de menu et de barre d’outils de Visual Studio. Par exemple, une fois que votre code est prêt à s’exécuter pour le débogage, vous pouvez choisir le bouton **Démarrer** dans la barre d’outils, ou choisir **Déboguer, Démarrer le débogage** dans le menu. Pour créer une solution, choisissez le bouton **Nouveau projet**, ou choisissez **Fichier, Nouveau, Projet** dans le menu, et ainsi de suite.

![Barre d’outils de Visual Studio](../ide/media/VSIDE_SolutionExplorer5_callouts.png)

Notez que les commandes de menu et les icônes de barre d’outils peuvent changer en fonction du contexte (c’est-à-dire de l’élément actuellement sélectionné). Quasiment toutes les commandes sont accessibles via le clavier ou la souris.

### <a name="team-explorer"></a>Team Explorer
**Team Explorer** vous permet de vous connecter à des outils de contrôle de code source tels que [Git](https://git-scm.com/) et [Team Foundation Version Control (TFVC)](https://www.visualstudio.com/en-us/docs/tfvc/overview) pour stocker votre code localement ou le partager avec d’autres utilisateurs sur un service hébergé. Vous pouvez également l’utiliser pour effectuer le suivi des tâches et bien plus encore.

Pour plus d’informations, regardez les vidéos sur la [mise en route de Visual Studio et les composantes de l’environnement de développement intégré](https://www.youtube.com/watch?v=JHc3_gsCmZg&index=2&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK) et sur la [mise en route de Visual Studio et l’ouverture d’un projet à partir du contrôle de code source](https://www.youtube.com/watch?v=pc9vX_4RGV4&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK&index=3).

![Team Explorer](../ide/media/TeamExplorer.png)

### <a name="output-window"></a>Fenêtre Sortie
La fenêtre **Sortie** est l’emplacement où Visual Studio envoie ses notifications, telles que les messages d’erreur et de débogage, les avertissements du compilateur, les messages d’état de publication, et ainsi de suite. Chaque type de message a son propre onglet.

![Fenêtre Sortie](../ide/media/VSIDE_OutputWindow.png)

Pour en savoir plus sur l’utilisation de la fenêtre de sortie pour le débogage, consultez [Fenêtre Sortie pendant le débogage avec Visual Studio](https://blogs.msdn.microsoft.com/visualstudioalm/2015/02/09/the-output-window-while-debugging-with-visual-studio/).

## <a name="first-steps"></a>Premières étapes
- **Vue d’ensemble** - Effectuez une visite guidée pour obtenir une vue d’ensemble de la plupart des principales fonctionnalités de Visual Studio ! Consultez [Visite guidée des fonctionnalités de l’IDE Visual Studio](../ide/visual-studio-ide.md).
- **Installation** - Pour en savoir plus sur le téléchargement et l’installation de Visual Studio, consultez [Visual Studio 2017](../install/install-visual-studio.md).
- **Notions de base** - Pour en savoir plus sur le fonctionnement de Visual Studio, consultez [Bien démarrer avec le développement dans Visual Studio](../ide/get-started-developing-with-visual-studio.md).
- **Paramètres** - Pour apprendre à personnaliser Visual Studio de manière à ce qu’il s’adapte à votre façon de travailler. Consultez [Personnalisation de l’IDE de Visual Studio](../ide/personalizing-the-visual-studio-ide.md).
- **Didacticiels** - Pour plus d’informations sur le développement de code dans Visual Studio, suivez un didacticiel, tel que [Mises en route de Visual Basic et Visual C#](../ide/getting-started-with-visual-csharp-and-visual-basic.md) ou [Mise en route de C++ dans Visual Studio](../ide/getting-started-with-cpp-in-visual-studio.md).
- **Vidéos** - Pour plus d’informations sur les autres fonctionnalités et aspects de Visual Studio, regardez les vidéos sur le [canal de Microsoft Visual Studio](https://www.youtube.com/user/VisualStudio/videos) sur YouTube ou les vidéos Visual Studio sur [Channel 9](https://channel9.msdn.com/Tags/visual+studio) ou sur la [Microsoft Virtual Academy](https://mva.microsoft.com/product-training/visual-studio-courses#!jobf=Developer).

## <a name="access-cloud-based-resources"></a>Accéder aux ressources cloud
Si vous souhaitez utiliser des ressources cloud dans votre application ou votre jeu, vous pouvez inclure des [services Azure](https://azure.microsoft.com/en-us/services/). Vous pouvez obtenir le kit de développement logiciel SDK Azure pour .NET en installant la charge de travail de **développement Azure** à l’aide du nouveau programme d’installation de Visual Studio. Les packages installés sont au même niveau de fonctionnalité que la version 2.9.5 du kit SDK. Pour cette version de Visual Studio et toutes les versions futures, le kit SDK Azure pour .NET est seulement disponible à partir du programme d’installation de Visual Studio.

Une fois la charge de travail de développement Azure installée, une nouvelle fenêtre d’outils appelée **Cloud Explorer** devient disponible dans Visual Studio. Cloud Explorer vous permet de parcourir et de gérer vos ressources Azure à partir de Visual Studio. Si une opération particulière nécessite le portail Azure, Cloud Explorer fournit des liens vers l’emplacement du portail Azure auquel vous devez accéder.

![Cloud Explorer](../ide/media/VSIDE_CloudExplorer.png)

Pour en savoir plus sur l’utilisation de Cloud Explorer, consultez [Gestion des ressources Azure avec Cloud Explorer](https://azure.microsoft.com/en-us/documentation/articles/vs-azure-tools-resources-managing-with-cloud-explorer/).
L’installation de la charge de travail de développement Azure vous donne également accès à [Visual Studio Tools pour Azure](https://www.visualstudio.com/vs/azure-tools/) et à d’autres outils associés.

## <a name="tips-and-tricks"></a>Conseils et astuces
Pour obtenir des raccourcis et des conseils et astuces pratiques qui vous permettront de tirer le meilleur parti de Visual Studio, consultez les rubriques suivantes.
- [Getting Started with Visual Studio - Tips & Tricks (Bien démarrer avec Visual Studio - Conseils et astuces)](https://www.youtube.com/watch?v=vmXqGwn1Glk&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK&index=4)
- [Conseils de productivité pour Visual Studio](../ide/productivity-tips-for-visual-studio.md)
- [Visual Studio Tips and Tricks (Conseils et astuces Visual Studio)](https://channel9.msdn.com/events/TechEd/2013/DEV-B353)
- [C++ Debugging Tips and Tricks (Conseils et astuces pour le débogage C++)](https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/C-Plus-Plus-Debugging-Tips-and-Tricks)
- [Visual Studio’s most useful (and underused) tips (Conseils les plus utiles relatifs à Visual Studio) [Blog de Scott Hanselman]](https://www.hanselman.com/blog/VisualStudiosMostUsefulAndUnderusedTips.aspx)
- [Getting Started with Visual Studio - Installing Visual Studio extensions (Bien démarrer avec Visual Studio - Installation des extensions Visual Studio)](https://www.youtube.com/watch?v=MWLLQaknRZY&list=PLReL099Y5nRfw6VNvzMkv0sabT2crbSpK&index=7)
