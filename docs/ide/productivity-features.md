---
title: Guide de productivité
description: Découvrez les raccourcis clavier et les fonctionnalités de productivité de Visual Studio qui peuvent vous aider à écrire efficacement du code, à déboguer le code et à gérer les erreurs.
ms.custom: SEO-VS-2020
ms.date: 4/29/2020
ms.topic: conceptual
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 181ce2071d780c9ef481d281f543c49d65262078
ms.sourcegitcommit: 6d88913a8b5a9e5eda01d3f95205b4d138f440f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/13/2021
ms.locfileid: "107296779"
---
# <a name="productivity-guide-for-visual-studio"></a>Guide de productivité pour Visual Studio

Si vous souhaitez gagner du temps pendant que vous écrivez du code, vous êtes au bon endroit. Ce guide de productivité comprend des conseils qui peuvent vous aider à prendre en main Visual Studio, à écrire du code, à déboguer du code, à gérer les erreurs et à utiliser les raccourcis clavier &mdash; sur une seule page.

Pour plus d’informations sur les raccourcis clavier utiles, consultez [Raccourcis de productivité](../ide/productivity-shortcuts.md). Pour obtenir la liste complète des raccourcis de commande, consultez [Raccourcis clavier par défaut](../ide/default-keyboard-shortcuts-in-visual-studio.md).

## <a name="get-started"></a>Bien démarrer

Gagnez du temps dans l’exploration des menus en recherchant rapidement les éléments dont vous avez besoin, notamment les commandes, les paramètres, la documentation et les options d’installation. Consultez Raccourcis clavier pour les commandes dans les résultats de la recherche dans Visual Studio afin de pouvoir les mémoriser plus facilement. 

- **Code factice utilisant la liste des tâches**. Si vous n’avez pas suffisamment de spécifications pour terminer un morceau de code, utilisez Liste des tâches pour suivre les commentaires de code qui utilisent des jetons tels que `TODO` et `HACK` , ou des jetons personnalisés, et pour gérer les raccourcis qui vous permettent d’accéder directement à un emplacement prédéfini dans le code. Pour plus d’informations, consultez [utiliser l’liste des tâches](../ide/using-the-task-list.md).

- **Utilisez Explorateur de solutions des raccourcis**. Si vous ne connaissez pas Visual Studio, ces raccourcis vous seront utiles et vous permettront de gagner du temps lorsque vous serez à la vitesse d’une nouvelle base de code. Pour obtenir la liste complète des raccourcis, consultez [raccourcis clavier par défaut dans Visual Studio](../ide/default-keyboard-shortcuts-in-visual-studio.md#bkmk_solutionexplorerGLOBAL).

- **[Identifiez et personnalisez les raccourcis clavier dans Visual Studio](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)**. Vous pouvez identifier les raccourcis clavier pour les commandes Visual Studio, personnaliser ces raccourcis, et les exporter afin que d'autres utilisateurs puissent les utiliser. Vous pouvez toujours Rechercher et modifier un raccourci clavier dans la boîte de dialogue Options.

- **Rendez Visual Studio plus accessible**. Visual Studio inclut des fonctionnalités d’accessibilité intégrées qui sont compatibles avec les lecteurs d’écran et d’autres appareils de technologie d’assistance. Pour obtenir la liste complète des fonctionnalités disponibles [, consultez conseils et astuces d’accessibilité pour Visual Studio](../ide/reference/accessibility-tips-and-tricks.md) . 

- Découvrez **le cycle de vie et la maintenance du produit Visual Studio**. Pour plus d’informations sur la façon d’obtenir des mises à jour pour Visual Studio, des options de support pour les clients professionnels et professionnels, la prise en charge des versions antérieures de Visual Studio et les composants non couverts par la maintenance de Visual Studio, consultez [cycle de vie et maintenance du produit Visual Studio](/visualstudio/releases/2019/servicing). 

- **Installer et gérer des packages NuGet dans Visual Studio**. L’interface utilisateur du gestionnaire de package NuGet dans Visual Studio facilite l’installation, la désinstallation et la mise à jour des packages NuGet dans les projets et solutions. Pour plus d’informations, consultez [installer et gérer des packages dans Visual Studio à l’aide du gestionnaire de package NuGet](/nuget/consume-packages/install-use-packages-visual-studio).

## <a name="write-code"></a>Écrire du code

Écrivez le code plus rapidement à l’aide des fonctionnalités suivantes.

- **Utilisez des commandes pratiques**. Visual Studio propose différentes commandes pour vous aider à accomplir plus rapidement des tâches d’édition. Par exemple, vous pouvez choisir une commande pour dupliquer facilement une ligne de code sans avoir à la copier, à repositionner le curseur, puis à coller la ligne. Choisissez **modifier** le  >  **doublon** ou appuyez sur **CTRL** + **E**,**V**. Vous pouvez également développer ou réduire rapidement une sélection de texte en choisissant **modifier** le  >    >  **développement** avancé ou **modifier** la sélection de  >    >  **contrat** avancée, ou en appuyant sur **MAJ** + **ALT** + **=** ou **MAJ** + **ALT** + **-** .

- **Utilisez IntelliSense**. Lorsque vous écrivez du code dans l'éditeur, les informations IntelliSense, telles que Liste des membres, Informations sur les paramètres, Info express, l'assistance de signature et Compléter le mot, s'affichent. Ces fonctionnalités prennent en charge la correspondance approximative de texte. par exemple, les listes de résultats pour les membres de liste incluent non seulement les entrées qui commencent par les caractères que vous avez entrés, mais également celles qui contiennent la combinaison de caractères n’importe où dans leurs noms. Pour plus d’informations, consultez [Utiliser IntelliSense](../ide/using-intellisense.md).

- **Modifier l’insertion automatique des options IntelliSense quand vous entrez du code**. En basculant IntelliSense en mode suggestion, vous pouvez spécifier que les options IntelliSense ne sont insérées que si vous les choisissez explicitement.

     Pour activer le mode de suggestion, appuyez sur les touches **CTRL** + **ALT** + **espace** ou, dans la barre de menus, choisissez **modifier** le mode de  >    >  **saisie semi-automatique** IntelliSense.

- **Utilisez des extraits de code**. Vous pouvez utiliser des extraits de code intégrés ou créer les vôtres.

     Pour insérer un extrait de code, dans la barre de menus, choisissez **modifier**  >  **IntelliSense**  >  **Insérer un extrait** ou **entourer** de, ou ouvrez le menu contextuel dans un fichier et choisissez **extrait**  >  **Insérer un extrait** ou **entourer de**. Pour plus d’informations, consultez [Extraits de code](../ide/code-snippets.md).

- **Corriger les erreurs de code inline**. Les actions rapides vous permettent de refactoriser, générer ou modifier facilement le code en une seule action. Ces actions peuvent être appliquées à l’aide des icônes de l’icône du tournevis-feu ![ ](media/screwdriver-icon.png) ou de l’ampoule ![ ](media/light-bulb-icon.png) , ou en appuyant sur **ALT** + **entrée** ou **CTRL** + **.** quand votre curseur se trouve sur la ligne de code appropriée. Pour plus d’informations, consultez [Actions rapides](quick-actions.md).

- **Afficher et modifier la définition d’un élément de code**. Vous pouvez afficher et modifier rapidement le module dans lequel un élément de code, tel qu'un membre, une variable ou une variable locale, est défini.

    Pour ouvrir une définition dans une fenêtre indépendante, mettez l’élément en surbrillance, puis appuyez sur les touches **ALT** + **F12** , ou ouvrez le menu contextuel de l’élément et choisissez Aperçu de la **définition**. Pour ouvrir une définition dans une nouvelle fenêtre de code, ouvrez le menu contextuel de l’élément de code, puis choisissez **Atteindre la définition**.

- **Utiliser des exemples d’applications**. Vous pouvez accélérer le développement d'applications en téléchargeant et en installant des exemples d'applications à partir de [Microsoft Developer Network](https://code.msdn.microsoft.com/). Vous pouvez également apprendre une technologie ou un concept de programmation spécifiques en téléchargeant et en explorant un exemple de pack pour cette zone.

- **Modifier la mise en forme des accolades avec la mise en forme/nouvelles lignes**. Utilisez la page Options de **mise en forme**  pour définir les options de mise en forme du code dans l’éditeur de code, y compris les nouvelles lignes. Pour plus d’informations sur l’utilisation de ce paramètre en C#, consultez [boîte de dialogue Options : éditeur de texte > C# > style de Code > mise en forme](../ide/reference/options-text-editor-csharp-formatting.md). Pour C++, consultez [définir vos préférences de codage C++ dans Visual Studio](/cpp/ide/how-to-set-preferences). Pour Python, consultez [formater le code python](../python/formatting-python-code.md).

- **Modifiez votre mise en retrait à l’aide des onglets**. Utilisez les paramètres personnalisés de l’éditeur, adaptés à chaque code base, pour appliquer des styles de codage cohérents pour plusieurs développeurs qui travaillent sur le même projet dans différents éditeurs et IDE. Assurez-vous que toute votre équipe respecte les mêmes conventions de langage, conventions de nommage et règles de mise en forme. Étant donné que ces paramètres personnalisés sont portables et voyagent avec votre code, vous pouvez appliquer des styles de codage même en dehors de Visual Studio. Pour plus d’informations, consultez [options, éditeur de texte, tous les langages, onglets](../ide/reference/options-text-editor-all-languages-tabs.md#tabs).

## <a name="navigate-within-your-code-and-the-ide"></a>Naviguer dans votre code et dans l’IDE

Vous pouvez utiliser différentes techniques pour rechercher et vous déplacer plus rapidement vers des emplacements spécifiques de votre code. Vous pouvez également modifier la disposition de vos fenêtres Visual Studio en fonction de vos préférences. 

- **Insérer un signet sur les lignes de code**. Vous pouvez utiliser des signets pour naviguer rapidement vers les lignes de code spécifiques d'un fichier.

    Pour définir un signet, dans la barre de menus, choisissez **modifier** les  >  **signets**,  >  **activer/désactiver le signet**. Vous pouvez afficher tous les signets d’une solution dans la fenêtre **Signets**. Pour plus d’informations, consultez [Définir des signets dans le code](../ide/setting-bookmarks-in-code.md).

- **Rechercher des définitions de symbole dans un fichier**. Vous pouvez faire une recherche dans une solution pour trouver des définitions de symbole et des noms de fichiers, mais les résultats de la recherche ne comportent pas d’espaces de noms ni de variables locales.

   Pour accéder à cette fonctionnalité, dans la barre de menus, choisissez **modifier**  >  **naviguer vers**.

- **Parcourir la structure globale de votre code**. Dans l’**Explorateur de solutions**, vous pouvez rechercher et parcourir des classes, ainsi que leurs types et membres dans vos projets. Vous pouvez également rechercher des symboles, afficher la hiérarchie d’appels d’une méthode, rechercher des références de symboles et effectuer d’autres tâches. Si vous sélectionnez un élément de code dans l’**Explorateur de solutions**, le fichier associé s’ouvre dans un onglet **Aperçu** et le curseur se déplace vers l’élément dans le fichier. Pour plus d’informations, consultez [Afficher la structure du code](../ide/viewing-the-structure-of-code.md).

- **Accède à un emplacement dans un fichier avec le mode carte**. Le mode carte affiche des lignes de code, en miniature, sur la barre de défilement. Pour plus d’informations sur ce mode d’affichage, consultez [Comment : personnaliser la barre de défilement](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md#map-mode).

- **Comprenez votre structure de code avec la carte de code**. Les cartes de code peuvent vous aider à visualiser les dépendances dans votre code et à voir comment elles s’adaptent sans lire les fichiers et les lignes de code. Pour plus d’informations, consultez [Mapper les dépendances avec des cartes de code](../modeling/map-dependencies-across-your-solutions.md).

- **Consultez fichiers fréquemment utilisés avec modifier/atteindre le fichier récent**. Utilisez les commandes atteindre dans Visual Studio pour effectuer une recherche ciblée sur votre code pour vous aider à trouver rapidement les éléments spécifiés. Pour obtenir des instructions détaillées, consultez [Rechercher du code à l’aide des commandes atteindre](../ide/go-to.md).

- **Déplacez le [fenêtre Propriétés](../ide/reference/properties-window.md) vers la partie droite**. Si vous avez besoin d’une disposition de fenêtres plus familière, vous pouvez déplacer les Fenêtre Propriétés dans Visual Studio en appuyant sur **F4**.

## <a name="find-items-faster"></a>Rechercher des éléments plus rapidement

Vous pouvez rechercher des commandes, des fichiers et des options dans l’IDE en plus de filtrer le contenu des fenêtres Outil pour afficher uniquement les informations importantes pour votre tâche actuelle.

- **Filtrer le contenu des fenêtres d’outils**. Vous pouvez faire une recherche dans le contenu de nombreuses fenêtres d’outils, telles que la **Boîte à outils**, la fenêtre **Propriétés** et l’**Explorateur de solutions**, mais afficher uniquement les éléments dont les noms contiennent les caractères que vous spécifiez.

- **Afficher uniquement les erreurs que vous souhaitez traiter**. Si vous sélectionnez le bouton **Filtre** dans la barre d’outils **Liste d’erreurs**, vous pouvez réduire le nombre d’erreurs qui s’affichent dans la fenêtre **Liste d’erreurs**. Vous pouvez afficher uniquement les erreurs des fichiers ouverts dans l'éditeur, uniquement les erreurs du fichier actif ou uniquement les erreurs du projet actif. Vous pouvez également effectuer une recherche dans la fenêtre de **liste d’erreurs** pour rechercher des erreurs spécifiques.

- **Recherchez des boîtes de dialogue, des commandes de menu, des options, etc.** Dans la zone de recherche, entrez les mots clés ou expressions pour les éléments recherchés. Par exemple, les options suivantes apparaissent si vous entrez **nouveau projet** :

   ::: moniker range="vs-2017"

   ![Résultats du lancement rapide pour « nouveau projet »](../ide/media/productivity_quicklaunch.png)

   **Lancement rapide** affiche notamment des liens pour créer un projet et pour ajouter un nouvel élément ainsi qu’un lien vers la page **Projets et solutions** dans la boîte de dialogue **Options**, entre autres. Les résultats de la recherche peuvent également inclure des fichiers de projet et des fenêtres Outil.

   ::: moniker-end

   ::: moniker range=">=vs-2019"

   ![Résultats de la recherche pour « nouveau projet »](../ide/media/vs-2019/productivity-quick-launch-new-project.png)

   ::: moniker-end

   Appuyez sur **CTRL** + **Q** pour accéder directement à la zone de recherche.

## <a name="debug-code"></a>Déboguer du code

Le débogage peut prendre beaucoup de temps, mais les conseils suivants peuvent vous aider à accélérer le processus.

- **Utilisez les outils du débogueur Visual Studio**. Dans le contexte de Visual Studio, lorsque vous *déboguez votre application*, cela signifie généralement que vous exécutez l’application en mode débogueur. Le débogueur offre de nombreuses façons de voir ce que votre code effectue pendant son exécution. Consultez [tout d’abord le débogueur Visual Studio](../debugger/debugger-feature-tour.md) pour obtenir un guide de mise en route. 

- **Tester la même page, la même application ou le même site dans divers navigateurs**. Quand vous déboguez votre code, vous pouvez basculer facilement entre les navigateurs web installés, notamment l’[Inspecteur de page (Visual Studio)](/previous-versions/hh974728(v=vs.140)), sans avoir besoin d’ouvrir la boîte de dialogue **Naviguer avec**. Vous pouvez utiliser la liste **cible de débogage** , qui se trouve dans la barre d’outils **standard** en regard du bouton **Démarrer le débogage** , pour vérifier rapidement le navigateur que vous utilisez quand vous déboguez ou affichez des pages.

    ![Sélectionner les options de débogage de navigateur web](../ide/media/webbrowserdropdowntoolbar.png)

- **Définir des points d’arrêt temporaires**. Vous pouvez créer un point d'arrêt temporaire dans la ligne active et démarrer le débogueur simultanément. Lorsque vous atteignez cette ligne de code, le débogueur passe en mode arrêt. Pour plus d’informations, consultez [Naviguer dans le code avec le débogueur](../debugger/navigating-through-code-with-the-debugger.md).

    Pour utiliser cette fonctionnalité, appuyez sur les touches **CTRL** + **F10** ou ouvrez le menu contextuel de la ligne de code sur laquelle vous souhaitez vous arrêter, puis choisissez **Exécuter jusqu’au curseur**.

- **Déplacer le point d’exécution pendant le débogage**. Vous pouvez déplacer le point d'exécution en cours vers une autre section de code, puis redémarrer le débogage à partir de ce point. Cette technique est utile si vous souhaitez déboguer une section de code sans avoir besoin de recréer toutes les étapes nécessaires pour atteindre cette section. Pour plus d’informations, consultez [Naviguer dans le code avec le débogueur](../debugger/navigating-through-code-with-the-debugger.md).

     Pour déplacer le point d’exécution, faites glisser la flèche jaune vers l’emplacement où vous souhaitez définir l’instruction suivante dans le même fichier source, puis appuyez sur la touche **F5** pour continuer le débogage.

- **Capturer des informations de valeur pour les variables**. Vous pouvez ajouter un DataTip à une variable dans votre code et l'épingler afin d'accéder à la dernière valeur connue pour la variable une fois que le débogage est terminé. Pour plus d’informations, consultez [Afficher les valeurs des données dans les conseils de données](../debugger/view-data-values-in-data-tips-in-the-code-editor.md).

     Pour ajouter un DataTip, le débogueur doit être en mode arrêt. Placez le curseur sur la variable, puis appuyez sur le bouton Pin sur le DataTip qui apparaît. Lorsque le débogage est arrêté, une icône d'épingle bleue apparaît dans le fichier source en regard de la ligne de code qui contient la variable. Si vous pointez l'épingle bleue, la valeur de la variable de la session de débogage la plus récente s'affiche.

- **Effacer la fenêtre Exécution**. Vous pouvez effacer le contenu de la [fenêtre exécution](../ide/reference/immediate-window.md) au moment de la conception en entrant `>cls` ou `>Edit.ClearAll`

     Pour plus d’informations sur les commandes supplémentaires, consultez [alias de commandes Visual Studio](../ide/reference/visual-studio-command-aliases.md).

- **[Recherchez des modifications de code et d’autres historiques avec CodeLens](../ide/find-code-changes-and-other-history-with-codelens.md)**. CodeLens vous permet de rester concentré sur votre travail pendant que vous cherchez ce qui s’est produit dans votre code, sans quitter l’éditeur. Vous pouvez trouver les références à un morceau de code, les changements dans votre code, les bogues liés, les éléments de travail, les revues du code et les tests unitaires.

- **Utilisez Live share pour déboguer en temps réel avec d’autres utilisateurs**. Live Share vous permet d’éditer et de déboguer en collaboration avec d’autres utilisateurs en temps réel, quels que soient les langages de programmation que vous utilisez ou les types d’applications que vous créez. Pour plus d’informations, consultez [qu’est-ce que Visual Studio Live share ?](/visualstudio/liveshare/)

- **Utilisez la fenêtre interactive pour écrire et tester du code de petite taille**. Visual Studio fournit une fenêtre de boucle de lecture-évaluation-impression (REPL) interactive qui vous permet d’entrer du code arbitraire et de voir les résultats immédiats. Cette méthode de codage vous permet d’apprendre et de tester les API et les bibliothèques, et de développer de manière interactive du code opérationnel à inclure dans vos projets. Pour Python, consultez [utiliser la fenêtre interactive Python](../python/python-interactive-repl-in-visual-studio.md). La fonctionnalité de fenêtre interactive est également disponible pour C#. 

## <a name="access-visual-studio-tools"></a>Accéder à Visual Studio Tools

Vous pouvez rapidement accéder à une invite de commandes développeur ou à un autre outil Visual Studio si vous l’épinglez au menu Démarrer ou à la barre des tâches.

::: moniker range="vs-2017"

1. Dans l’Explorateur Windows, accédez à *%ProgramData%\Microsoft\Windows\Start Menu\Programs\Visual Studio 2017\Visual Studio Tools*.

::: moniker-end

::: moniker range=">=vs-2019"

1. Dans l’Explorateur Windows, accédez à *%ProgramData%\Microsoft\Windows\Start Menu\Programs\Visual Studio 2019\Visual Studio Tools*.

::: moniker-end

2. Cliquez avec le bouton droit ou ouvrez le menu contextuel pour **Invite de commandes développeur**, puis choisissez **Épingler au menu Démarrer** ou **Épingler à la barre des tâches**.

## <a name="manage-files-toolbars-and-windows"></a>Gérer des fichiers, des barres d’outils et des fenêtres

À tout moment, vous pouvez travailler dans plusieurs fichiers de code et vous déplacer sur plusieurs fenêtres Outil à mesure que vous développez une application. Vous pouvez préserver une bonne organisation en utilisant les conseils suivants :

- **Faire en sorte que les fichiers que vous utilisez fréquemment soient visibles dans l’éditeur**. Vous pouvez épingler des fichiers sur le côté gauche de l’onglet afin qu’ils restent visibles quel que soit le nombre de fichiers ouverts dans l’éditeur.

   Pour épingler un fichier, choisissez l’onglet du fichier, puis choisissez le bouton **activer/désactiver l’état de l’épinglage** .

- **Déplacer des documents et des fenêtres vers d’autres moniteurs**. Si vous utilisez plusieurs écrans lorsque vous développez des applications, vous pouvez travailler plus facilement sur des parties de votre application en déplaçant les fichiers ouverts dans l'éditeur vers un autre moniteur. Vous pouvez également déplacer les fenêtres Outil, comme les fenêtres du débogueur, vers un autre moniteur, et ancrer ensemble des fenêtres de documents et des fenêtres Outil pour créer des « ensembles flottants ». Pour plus d’informations, consultez [Personnalisation des dispositions de fenêtres dans Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md).

   Vous pouvez également gérer des fichiers plus facilement en créant une autre instance de l’**Explorateur de solutions** et en la déplaçant vers un autre moniteur. Pour créer une autre instance de l’**Explorateur de solutions**, ouvrez un menu contextuel dans l’**Explorateur de solutions**, puis choisissez **Nouvelle vue Explorateur de solutions**.

- **Personnaliser les polices qui apparaissent dans Visual Studio**. Vous pouvez modifier le type, la taille et la couleur de police utilisés pour le texte dans l’IDE. Par exemple, vous pouvez personnaliser la couleur des éléments de code spécifiques dans l'éditeur et le type de police dans les fenêtres Outil ou dans tout l'IDE. Pour plus d’informations, consultez [Comment : modifier les polices et les couleurs](../ide/how-to-change-fonts-and-colors-in-visual-studio.md) et [Comment : modifier les polices et les couleurs dans l’éditeur](../ide/reference/how-to-change-fonts-and-colors-in-the-editor.md).

## <a name="see-also"></a>Voir aussi

- [Blog de conseils et d’astuces pour Visual Studio](https://devblogs.microsoft.com/visualstudio/visual-studio-tips-and-tricks/)
- [Raccourcis clavier par défaut pour les commandes fréquemment utilisées](../ide/default-keyboard-shortcuts-for-frequently-used-commands-in-visual-studio.md)
- [Comment : personnaliser des menus et des barres d’outils](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md)
- [Procédure pas à pas : création d’une application simple](../get-started/csharp/tutorial-wpf.md)
- [Conseils et astuces d’accessibilité](../ide/reference/accessibility-tips-and-tricks.md)