---
title: Écriture de code dans l’éditeur de code et de texte | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.texteditor
dev_langs:
- JScript
- VB
- CSharp
helpviewer_keywords:
- code editor, word wrap
- outlining
- code, editing
- squiggles
- code editor, outlining
- code editor, error and warning markers
- word wrap
- code editor, syntax coloring
- code editor, go to definition
- diff
- code editor [Visual Studio]
- code editor, diff
- error and warning markers
- code editor, navigation bar
- code editor, customizing
- comment selection
- code editor, tabify
- brace matching
- code editor, line numbers
- printing
- code editor, brace matching
- code editor, squiggles
- code editor, features
- line numbers
- go to definition
- syntax coloring
- code editor, navigate to
- code editor, comparing files
- code editor, zoom
- code editor
- code files
- go to line
- tabify
- zoom
- navigate to
- line break characters
- code editor, virtual space
- code editor, change tracking
- code editor, comment selection
- code editor, printing
- virtual space
- code editor, line break characters
- code editor, go to line
- code
ms.assetid: cb53ab9a-5b76-4759-b9e8-7bf32298ecbe
caps.latest.revision: 46
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: aa647d8a8d52588481d18347cb3400141978bd20
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85548029"
---
# <a name="writing-code-in-the-code-and-text-editor"></a>Écriture de code dans l'éditeur de code et de texte
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
L’éditeur Visual Studio fournit de nombreuses fonctionnalités facilitant l’écriture et la gestion de votre code. Vous pouvez développer et réduire différents blocs de code en utilisant le mode Plan. Vous pouvez obtenir plus d’informations sur le code que vous utilisez à l’aide d’IntelliSense, de l’ **Explorateur d’objets**et de la hiérarchie d’appels. Vous pouvez naviguer dans votre code en utilisant des fonctionnalités telles que **Naviguer vers**, **Atteindre la définition**et **Rechercher toutes les références**. Vous pouvez insérer des blocs de code à l’aide d’extraits de code et vous pouvez générer du code en utilisant des fonctionnalités telles que **Générer à partir de l’utilisation**. Si vous n’avez encore jamais utilisé l’éditeur Visual Studio 2015, consultez [Modification de votre code](https://www.visualstudio.com/features/ide-vs) pour obtenir une vue d’ensemble rapide.

 Vous pouvez afficher votre code de différentes façons. Pour consulter l’affichage de classes de votre solution, vous pouvez ouvrir la fenêtre **Affichage de classes** ou développer les nœuds dans l’ **Explorateur de solutions** sous vos fichiers de classe.

 Vous pouvez rechercher et remplacer du texte pour un ou plusieurs fichiers. Pour plus d’informations, consultez [recherche et remplacement de texte](../ide/finding-and-replacing-text.md). Si vous utilisez des expressions régulières, notez que la recherche et le remplacement utilisent à présent les expressions régulières .NET. Pour plus d’informations, consultez [Utilisation d’expressions régulières dans Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

 Les différents langages de Visual Studio offrent différents ensembles de fonctionnalités et, dans certains cas, les fonctionnalités se comportent différemment dans les différents langages. Un grand nombre de ces différences sont spécifiées dans les descriptions des fonctionnalités, mais pour plus d’informations, vous pouvez consulter les sections relatives aux langages spécifiques de Visual Studio.

> [!IMPORTANT]
> L’édition de Visual Studio et les paramètres que vous utilisez peuvent affecter les fonctionnalités de l’environnement IDE. Elles peuvent différer de celles décrites dans cette rubrique.

## <a name="editor-features"></a>Fonctionnalités de l’éditeur

|Fonctionnalité|Description|
|-|-|
|Couleurs de syntaxe|Certains éléments de syntaxe des fichiers de code et de balisage apparaissent dans des couleurs différentes pour que vous puissiez les distinguer. Par exemple, les mots clés (tels que `using` en C# et `Imports` en Visual Basic) apparaissent dans une couleur, alors que les types (tels que `Console` et `Uri`) sont d’une autre couleur. D’autres éléments de syntaxe sont également colorés, tels que les commentaires et les littéraux de chaîne. C++ utilise la couleur pour différencier les types, les énumérations et les macros parmi les autres jetons.<br /><br /> Vous pouvez voir la couleur par défaut de chaque type et vous pouvez modifier cette couleur pour tout élément de syntaxe spécifique dans la [boîte de dialogue Polices et couleurs, Environnement, Options](../ide/reference/fonts-and-colors-environment-options-dialog-box.md), que vous pouvez ouvrir à partir du menu **Outils** .|
|Marques d’erreur et d’avertissement|Quand vous ajoutez du code et générez votre solution, vous pouvez voir s’afficher (a) des soulignements ondulés de différente couleur (les tildes) ou (b) des ampoules dans votre code. Les soulignements ondulés rouges indiquent des erreurs de syntaxe, les soulignements ondulés bleus indiquent des erreurs de compilateur, les soulignements ondulés verts indiquent des avertissements et les soulignements ondulés violets indiquent d’autres types d’erreur. Les [ampoules](../ide/perform-quick-actions-with-light-bulbs.md) suggèrent des solutions aux problèmes rencontrés et facilitent la correction des erreurs.<br /><br /> Vous pouvez voir la couleur par défaut pour chaque tilde d’erreur et d’avertissement dans la boîte de dialogue **Outils/Options/environnement/polices et couleurs** . Recherchez **Erreur de syntaxe**, **Erreur du compilateur**, **Avertissement**et **Autre erreur**.|
|Accolades correspondantes|Quand le point d’insertion est placé sur une accolade ouvrante dans un fichier de code, l’accolade ouvrante et l’accolade fermante sont mises en surbrillance. Cette fonctionnalité vous permet de visualiser immédiatement les accolades mal placées ou manquantes. Vous pouvez activer ou désactiver la correspondance des accolades avec le paramètre de **mise en surbrillance automatique des délimiteurs** (**Outils/Options/éditeur de texte**). Vous pouvez modifier la couleur de surbrillance dans le paramètre **polices et couleurs** (**Outils/Options/environnement**). Recherchez **Accolades correspondantes (en surbrillance)** ou **Accolades correspondantes (rectangle)**.|
|Numéros de ligne|Les numéros de ligne peuvent être affichés dans la marge de gauche de la fenêtre de code. Ils ne sont pas affichés par défaut. Vous pouvez activer cette option dans les paramètres **tous les langages** de l’éditeur de texte (**Outils/Options/éditeur de texte/tous les langages**). Vous pouvez afficher les numéros de ligne pour des langages de programmation individuels en modifiant les paramètres de ces langages (**outils \<language> /options/éditeur de texte/**). Pour imprimer les numéros de ligne, sélectionnez Inclure les numéros de ligne dans la boîte de dialogue **Imprimer**.|
|Suivi des modifications|La couleur de la marge de gauche vous permet de conserver une trace des modifications effectuées dans un fichier. Les modifications que vous avez effectuées depuis l’ouverture du fichier mais que vous n’avez pas enregistrées sont signalées par une barre jaune dans la marge de gauche (appelée marge de sélection). Une fois que vous avez enregistré les modifications (mais avant la fermeture du fichier), la barre devient verte. Si vous annulez une modification après avoir enregistré le fichier, la barre devient orange. Pour activer et désactiver cette fonctionnalité, modifiez l’option **suivi des modifications** dans les paramètres **éditeur de texte** (**Outils/Options/éditeur de texte**).|
|Sélection de code et de texte|Vous pouvez sélectionner du texte en mode linéaire standard ou en mode Zone, dans lequel vous sélectionnez une partie rectangulaire du texte au lieu d’un ensemble de lignes. Pour effectuer une sélection en mode zone, appuyez sur ALT tout en faisant glisser la souris sur la sélection (ou appuyez sur ALT + MAJ + \<arrow key> ). La sélection inclut tous les caractères compris dans le rectangle défini par le premier caractère et le dernier caractère de la sélection. Tout texte tapé ou collé dans la zone sélectionnée est inséré au même endroit sur chaque ligne.|
|Zoom|Vous pouvez effectuer un zoom avant ou arrière dans n’importe quelle fenêtre de code en maintenant enfoncée la touche Ctrl tout en actionnant la roulette de défilement de la souris (ou en appuyant sur Ctrl+Maj+. pour agrandir l’image et sur Ctrl+Maj+, pour la réduire). Vous pouvez également utiliser la zone zoom dans l’angle inférieur gauche de la fenêtre de code pour définir un pourcentage de zoom spécifique. La fonctionnalité de zoom ne fonctionne pas dans les fenêtres d’outils.|
|Espace virtuel|Par défaut, les lignes dans les éditeurs Visual Studio se terminent après le dernier caractère, de sorte qu’un appui sur la touche de direction DROITE à la fin d’une ligne place le curseur au début de la ligne suivante. Dans certains autres éditeurs, une ligne ne se termine pas après le dernier caractère et vous pouvez placer le curseur n’importe où sur la ligne. Vous pouvez activer l’espace virtuel dans l’éditeur, dans les paramètres **Outils/Options/éditeur de texte/tous les langages** . Notez que vous pouvez activer l’option **Espace virtuel** ou **Retour automatique à la ligne**, mais pas les deux.|
|Impression|Vous pouvez utiliser les options de la boîte de dialogue **Imprimer** pour inclure les numéros de ligne ou masquer les régions réduites de code quand vous imprimez un fichier. Dans la boîte de dialogue **Mise en page** , vous pouvez également choisir d’imprimer le chemin d’accès complet et le nom du fichier en choisissant **En-tête**.<br /><br /> Vous pouvez définir des options d’impression couleur dans la boîte de dialogue **Outils/Options/environnement/polices et couleurs** . Choisissez **Imprimante** dans la liste **Afficher les paramètres de** pour personnaliser l’impression couleur. Vous pouvez spécifier des couleurs différentes pour imprimer un fichier que pour le modifier.|
|Annulation globale et rétablissement global|Les commandes **Annuler la dernière action globale** et **Rétablir la dernière action globale** du menu **Edition** annulent et rétablissent les actions globales qui affectent plusieurs fichiers. Les actions globales incluent la modification du nom d’une classe ou d’un espace de noms, l’exécution d’une opération de recherche et remplacement dans une solution, la refactorisation d’une base de données ou toute autre action qui modifie plusieurs fichiers. Vous pouvez appliquer les commandes globales d’annulation et de rétablissement aux actions de la session Visual Studio actuelle, même après avoir fermé la solution dans laquelle une action a été appliquée.|

## <a name="advanced-editing-features"></a>Fonctionnalités d’édition avancées
 De nombreuses fonctionnalités avancées sont disponibles dans le sous-menu **Edition/Options avancées**. Toutes ces fonctionnalités ne sont pas disponibles pour tous les types de fichiers de code.

|Fonctionnalité|Description|
|-|-|
|Mettre le document en forme|Définit la mise en retrait appropriée des lignes de code et place des accolades pour séparer les lignes dans le document.|
|Mettre la sélection en forme|Définit la mise en retrait appropriée des lignes de code et place des accolades pour séparer les lignes dans la sélection.|
|Remplacer les espaces par des tabulations|Remplace les espaces à gauche par des tabulations le cas échéant.|
|Remplacer les tabulations par des espaces|Remplace les tabulations à gauche par des espaces. Si vous souhaitez convertir tous les espaces de votre fichier en tabulations (ou toutes les tabulations en espaces), vous pouvez utiliser les commandes `Edit.ConvertSpacesToTabs` et `Edit.ConvertTabsToSpaces`. Ces commandes n’apparaissent pas dans les menus de Visual Studio, mais vous pouvez les appeler à partir de la fenêtre Accès rapide ou de la fenêtre Commande.|
|Mettre en majuscules|Met tous les caractères de la sélection en majuscules ou, en l’absence de sélection, met en majuscule le caractère au point d’insertion.|
|Mettre en minuscules|Met tous les caractères de la sélection en minuscules ou, en l’absence de sélection, met en minuscule le caractère au point d’insertion.|
|Valider le document|Valide les fichiers de code JScript.|
|Supprimer les espaces blancs horizontaux|Supprime les tabulations et les espaces à la fin de la ligne active.|
|Afficher les espaces blancs|Affiche les espaces sous forme de points et les tabulations sous forme de flèches. La fin d’un fichier est indiquée par un glyphe rectangulaire. Si l’option **Outils/Options/éditeur de texte/tous les langages/retour automatique à la ligne/afficher les glyphes visibles pour le retour automatique à la ligne** est sélectionnée, ce glyphe s’affiche également.|
|Retour automatique à la ligne|Rend visibles toutes les lignes d’un document dans la fenêtre de code. Vous pouvez activer et désactiver cette option dans les paramètres Tous les langages de l’éditeur de texte (**Outils/Options/Éditeur de texte/Tous les langages**).|
|Supprimer les marques de commentaire de la sélection|Ajoute des caractères de commentaire à la sélection ou à la ligne active.|
|Commenter la sélection|Supprime les caractères de commentaire de la sélection ou de la ligne active.|
|Augmenter le retrait de ligne|Ajoute une tabulation (ou les espaces équivalents) aux lignes sélectionnées ou à la ligne active.|
|Réduire le retrait de ligne|Supprime une tabulation (ou les espaces équivalents) des lignes sélectionnées ou de la ligne active.|
|Sélectionner la balise|Dans un document qui contient des balises (par exemple, XML ou HTML), sélectionne la balise.|
|Sélectionner le contenu de la balise|Dans un document qui contient des balises (par exemple, XML ou HTML), sélectionne le contenu.|

## <a name="navigate-in-the-code-window"></a>Naviguer dans la fenêtre de code
 Vous pouvez vous déplacer dans un document de différentes façons. Outre les opérations standard, vous pouvez utiliser les boutons **Naviguer vers l’arrière** (ou Ctrl+Moins) et **Naviguer vers l’avant** (Ctrl+Maj+Moins) dans la barre d’outils pour déplacer le point d’insertion vers des emplacements précédents ou retourner à des emplacements plus récents dans le document actif. Ces boutons conservent les 20 derniers emplacements du point d’insertion.

 ![Boutons de navigation Suivant et Précédent](../ide/media/vs2015-nav-buttons.png "VS2015_Nav_buttons")

 Vous pouvez également utiliser la barre de défilement améliorée dans une fenêtre de code pour bénéficier d’une vue panoramique de votre code. En mode plan, vous pouvez afficher des aperçus du code en déplaçant le curseur vers le haut et le bas dans la barre de défilement. Pour plus d’informations, consultez [How to: Track Your Code by Customizing the Scrollbar](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md).

 Les commandes suivantes sont des méthodes de navigation spécifiques au code :

|Commande|Description|
|-|-|
|Atteindre \<line number>|(**Edition/Atteindre** ou Ctrl+G) : permet d’accéder à une ligne spécifique dans le document actif.|
|Naviguer vers|(**Edition/Naviguer vers** ou Ctrl+,) : recherche un symbole ou un fichier dans la solution active. Cette commande vous aide à recueillir un ensemble approprié de correspondances à partir d’une requête. Vous pouvez rechercher des mots clés contenus dans un symbole en utilisant la casse mixte et des traits de soulignement pour diviser le symbole en mots clés.|
|Rechercher toutes les références|(menu contextuel) : recherche toutes les références à l’élément sélectionné dans la solution.|
|Atteindre la définition|(menu contextuel ou F12) : recherche la définition de l’élément sélectionné.|
|Aperçu de la définition|(menu contextuel ou Alt+F12) : recherche la définition de l’élément sélectionné et l’affiche dans une fenêtre contextuelle. Pour plus d’informations, consultez [Comment : afficher et modifier le code à l’aide de l’aperçu de définition (ALT + F12)](../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md).|
|Méthode suivante, Méthode précédente|(**Edition/Méthode suivante, Méthode précédente**) Dans des fichiers de code Visual Basic, utilisez ces commandes pour déplacer le point d’insertion entre les différentes méthodes.|
|Mise en surbrillance des références|Quand vous cliquez sur un symbole dans le code source, toutes les instances de ce symbole sont mises en surbrillance dans le document. Les symboles en surbrillance peuvent inclure des déclarations et des références, ainsi que de nombreux autres symboles pouvant être retournés par la fonctionnalité **Rechercher toutes les références** . Ceux-ci incluent les noms de classes, d’objets, de variables, de méthodes et de propriétés. Dans le code Visual Basic, les mots clés de nombreuses structures de contrôle sont également mis en surbrillance. Pour passer au symbole en surbrillance suivant ou précédent, appuyez sur Ctrl+Maj+Bas ou sur Ctrl+Maj+Haut. Vous pouvez modifier la couleur de mise en surbrillance dans **Outils/Options/environnement/polices et couleurs/référence en surbrillance.**|
|Rechercher des informations relatives au code|Vous pouvez rechercher des informations sur un code spécifique, telles que les modifications et les auteurs de ces modifications, les références, les bogues, les éléments de travail, les révisions du code et l’état de test unitaire quand vous utilisez CodeLens dans l’éditeur de code. CodeLens fonctionne comme un afficheur d’alertes quand vous utilisez Visual Studio Enterprise avec Team Foundation Server. Consultez [Rechercher les modifications de code et d’autres historiques](../ide/find-code-changes-and-other-history-with-codelens.md).|

 Vous pouvez également utiliser la **barre de navigation**, autrement dit, les deux zones de liste déroulante affichées en haut de la fenêtre de code, pour naviguer dans un fichier de code. Cette barre vous permet d’accéder directement à un type particulier ou à l’un des membres au sein d’un type. La barre de navigation apparaît avec les fichiers de code Visual Basic, C# et C++.

 Pour masquer la barre de navigation, modifiez l’option **Barre de navigation** dans les paramètres Tous les langages de l’éditeur de texte (**Outils/Options/Éditeur de texte/Tous les langages**) ou modifiez les paramètres pour des langages spécifiques. Vous pouvez naviguer dans les zones de liste déroulante comme suit :

- Pour déplacer le focus de la fenêtre de code vers la barre de navigation, appuyez sur la combinaison de touches de raccourci Ctrl+F2.

- Pour ramener le focus de la barre de navigation dans la fenêtre de code, appuyez sur la touche Échap.

- Pour déplacer le focus d’un élément à un autre dans la barre de navigation, appuyez sur la touche Tab.

- Pour sélectionner l’élément de la barre de navigation qui a le focus et retourner dans l’environnement IDE, appuyez sur la touche Entrée.

- Pour accéder à une classe ou à un type, cliquez sur son nom dans la liste déroulante gauche.

- Pour accéder directement à une procédure dans une classe, cliquez sur une procédure dans la liste déroulante droite.

  Dans une classe partielle, les membres définis en dehors du fichier de code actuel peuvent être grisés.

## <a name="find-code-using-navigate-to"></a>Rechercher du code à l’aide de Naviguer vers
La commande « Naviguer vers » de Visual Studio effectue une recherche de votre code pour vous aider à trouver rapidement les éléments spécifiés dans les fichiers de code, les chemins de fichiers et les symboles de code. Contrairement à d’autres types de recherche de texte, tels que Rechercher ou Rechercher dans les fichiers, Naviguer vers limite ses recherches aux zones où réside réellement le code, telles que les fichiers, les formulaires et les modules de code. Par exemple, si vous recherchez une chaîne dans une application web ASP.NET à l’aide de Rechercher ou Rechercher dans les fichiers dans la solution entière, vous pouvez obtenir plusieurs résultats, notamment les instances de la chaîne dans les notes du code. En utilisant Navigate to, toutefois, vous ne pouvez obtenir qu’une seule fonction, en ignorant toutes les instances de la chaîne dans les notes de code.

### <a name="navigate-code-using-navigate-to"></a>Parcourir le code à l’aide de Naviguer vers

1. Dans Visual Studio, ouvrez une solution ou un dossier.
1. Dans le menu principal, choisissez **Edition**, **Naviguer vers**, ou appuyez sur **Ctrl +,**.

    Une petite zone de texte s’affiche dans l’angle supérieur de l’éditeur de code.
1. Dans la zone de texte, entrez le nom de l’élément de code que vous souhaitez rechercher.

    ![Fenêtre Naviguer vers](../ide/media/vside-navigatetowindow.png "Fenêtre Naviguer vers")

    À mesure que vous tapez, les résultats s’affichent dans une liste déroulante sous la zone de texte.
1. Pour accéder à un élément, sélectionnez-le dans la liste.

### <a name="filter-your-search"></a>Filtrer votre recherche

Pour limiter votre recherche aux symboles de code, faites précéder votre requête de navigation d’un \@ caractère «». Par exemple, si vous recherchez `@application`, Naviguer vers affiche uniquement les classes qui contiennent le mot « application ».

Si vous utilisez la casse mixte dans votre code, vous trouverez les éléments de code plus rapidement en entrant uniquement les majuscules du nom d’élément de code. Par exemple, si votre code a un composant nommé `ViewSwitcher`, vous pouvez le trouver en entrant simplement les majuscules du nom (`"VS"`) dans la fenêtre Naviguer vers.

![Fenêtre Naviguer vers - recherche en lettres capitales](../ide/media/vside-capitalsearch.png "Fenêtre Naviguer vers - recherche en lettres capitales")

Cette fonctionnalité est particulièrement utile si votre code contient des noms longs.

## <a name="customize-the-editor"></a>Personnaliser l’éditeur
 **Importation et exportation de paramètres**: vous pouvez partager des paramètres avec un autre développeur, rendre vos paramètres conformes à une norme ou rétablir les paramètres par défaut de Visual Studio à l’aide de l’ **Assistant Importation et exportation de paramètres** dans le menu **Outils** . Vous pouvez modifier des paramètres généraux ou des paramètres spécifiques à un langage ou à un projet.

 **Configuration du clavier**: vous pouvez définir de nouvelles touches d’accès rapide ou redéfinir les touches existantes dans les paramètres Outils/Options/Environnement/Clavier. Pour plus d’informations sur les touches d’accès rapide, consultez [Raccourcis clavier par défaut](../ide/default-keyboard-shortcuts-in-visual-studio.md).

 Pour plus d’informations sur les options d’éditeur spécifiques au langage, consultez les rubriques suivantes :

- [Paramètres de Visual Basic](https://msdn.microsoft.com/library/2712b3b1-18f2-430c-ae91-28468bbf5f32)

- [Utilisation de l’environnement de développement Visual Studio pour C#](../csharp-ide/using-the-visual-studio-development-environment-for-csharp.md)

- [Options, Text Editor, JavaScript, Formatting](../ide/reference/options-text-editor-javascript-formatting.md)

## <a name="in-this-section"></a>Contenu de cette section

- [Recherche et remplacement de texte](../ide/finding-and-replacing-text.md)

- [Encodages et sauts de ligne](../ide/encodings-and-line-breaks.md)

- [mode Plan](../ide/outlining.md)

- [Refactorisation](../ide/refactoring-in-visual-studio.md)

- [Conseils de productivité](../ide/productivity-tips-for-visual-studio.md)

- [Utilisation d’IntelliSense](../ide/using-intellisense.md)

- [Personnalisation de l’éditeur](../ide/customizing-the-editor.md)

- [Comment : suivre votre code en personnalisant la barre de défilement](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md)

- [Guide pratique pour afficher et modifier le code avec l’Aperçu de définition (ALT + F12)](../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md)

- [Effectuer des actions rapides avec des ampoules](../ide/perform-quick-actions-with-light-bulbs.md)

- [Extraits de code](../ide/code-snippets.md)

- [Utilisation de la boîte à outils](../ide/using-the-toolbox.md)

- [Affichage de la structure du code](../ide/viewing-the-structure-of-code.md)

- [Définition de signets dans le code](../ide/setting-bookmarks-in-code.md)

- [Utilisation de la liste des tâches](../ide/using-the-task-list.md)

- [Rechercher les modifications de code et autres historiques](../ide/find-code-changes-and-other-history-with-codelens.md)

## <a name="see-also"></a>Voir aussi
 [IDE Visual Studio](../ide/visual-studio-ide.md)
