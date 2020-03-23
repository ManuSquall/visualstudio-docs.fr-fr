---
title: Fonctionnalités de l’éditeur de code
ms.date: 02/23/2018
ms.topic: conceptual
helpviewer_keywords:
- code, editing [Visual Studio]
- code editor [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: de209e0a940fe7f7c64644cea37de3762df0d643
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75588549"
---
# <a name="features-of-the-code-editor"></a>Fonctionnalités de l’éditeur de code

L’éditeur Visual Studio fournit de nombreuses fonctionnalités facilitant l’écriture et la gestion de votre code et de votre texte. Vous pouvez développer et réduire différents blocs de code en utilisant le mode Plan. Vous pouvez obtenir plus d’informations sur le code en utilisant IntelliSense, **l’Explorateur d’objets**et la hiérarchie d’appels. Vous pouvez rechercher du code en utilisant des fonctionnalités telles que **Atteindre**, **Atteindre la définition** et **Rechercher toutes les références**. Vous pouvez insérer des blocs de code à l’aide d’extraits de code et vous pouvez générer du code en utilisant des fonctionnalités telles que **Générer à partir de l’utilisation**. Si vous n’avez jamais utilisé l’éditeur Visual Studio avant, voir [Apprendre à utiliser l’éditeur de code](../get-started/tutorial-editor.md).

> [!NOTE]
> Cette rubrique s’applique à Visual Studio sur Windows. Pour Visual Studio pour Mac, consultez [Éditeur de code Source (Visual Studio pour Mac)](/visualstudio/mac/source-editor).

Vous pouvez afficher votre code de différentes façons. Par défaut, **l’Explorateur de solutions** affiche votre code organisé par fichiers. Pour afficher votre code organisé par classes, cliquez sur l’onglet **Affichage de classes** situé en bas de la fenêtre.

Vous pouvez rechercher et remplacer du texte dans un ou plusieurs fichiers. Pour plus d’informations, consultez [Rechercher et remplacer du texte](../ide/finding-and-replacing-text.md). Vous pouvez utiliser des expressions régulières pour rechercher et remplacer du texte. Pour plus d’informations, consultez [Utiliser des expressions régulières dans Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

Les différents langages de Visual Studio offrent différents ensembles de fonctionnalités et, dans certains cas, les fonctionnalités se comportent différemment dans les différents langages. Un grand nombre de ces différences sont spécifiées dans les descriptions des fonctionnalités, mais pour plus d’informations, vous pouvez consulter les sections relatives aux langages spécifiques de Visual Studio.

## <a name="editor-features"></a>Fonctionnalités de l’éditeur

|||
|-|-|
|Couleurs de syntaxe|Certains éléments de syntaxe des fichiers de code et de balisage apparaissent dans des couleurs différentes pour que vous puissiez les distinguer. Par exemple, les mots clés (tels que `using` en C# et `Imports` en Visual Basic) apparaissent dans une couleur, alors que les types (tels que `Console` et `Uri`) sont d’une autre couleur. D’autres éléments de syntaxe sont également colorés, tels que les commentaires et les littéraux de chaîne. C++ utilise la couleur pour différencier les types, les énumérations et les macros parmi les autres jetons.<br /><br /> Vous pouvez voir la couleur par défaut pour chaque type, et vous pouvez changer la couleur pour n’importe quel élément syntaxe spécifique dans les [polices et les couleurs, l’environnement, options boîte](../ide/reference/fonts-and-colors-environment-options-dialog-box.md)de dialogue , que vous pouvez ouvrir à partir du menu **Tools.**|
|Marques d’erreur et d’avertissement|Quand vous ajoutez du code et générez votre solution, vous pouvez voir s’afficher (a) des soulignements ondulés de différente couleur (les tildes) ou (b) des ampoules dans votre code. Les soulignements ondulés rouges indiquent des erreurs de syntaxe, les soulignements ondulés bleus indiquent des erreurs de compilateur, les soulignements ondulés verts indiquent des avertissements et les soulignements ondulés violets indiquent d’autres types d’erreur. Les [actions rapides](../ide/quick-actions.md) suggèrent des solutions aux problèmes rencontrés et facilitent la correction des erreurs.<br /><br /> Vous pouvez voir la couleur par défaut pour chaque erreur et avertissement squiggle dans les **outils** > **Options** > **Environment** > **Fonts et Colors** boîte de dialogue. Recherchez **Erreur de syntaxe**, **Erreur du compilateur**, **Avertissement**et **Autre erreur**.|
|Accolades correspondantes|Quand le point d’insertion est placé sur une accolade ouvrante dans un fichier de code, l’accolade ouvrante et l’accolade fermante sont mises en surbrillance. Cette fonctionnalité vous permet de visualiser immédiatement les accolades mal placées ou manquantes. Vous pouvez activer ou désactiver la correspondance d’accolade à l’aide du paramètre **Mise en surbrillance automatique des délimiteurs** (**Outils** > **Options** > **Éditeur de texte**). Vous pouvez modifier la couleur de surbrillance dans le paramètre **Polices et couleurs** (**Outils** > **Options** > **Environnement**). Recherchez **Accolades correspondantes (en surbrillance)** ou **Accolades correspondantes (rectangle)**.|
|Visualiseur de structure|Des lignes en pointillés connectent les accolades correspondantes dans les fichiers de code, permettant de voir plus facilement les paires d’accolades ouvrantes et fermantes. Cela vous permet de trouver plus rapidement du code dans votre code base. Vous pouvez activer ou désactiver ces lignes avec les **directives de la structure De l’affichage** dans la section **Afficher** la page générale de**l’éditeur** > **de** texte **Tools** > **Options.** > |
|Numéros de ligne|Les numéros de ligne peuvent être affichés dans la marge de gauche de la fenêtre de code. Ils ne sont pas affichés par défaut. Vous pouvez activer cette option dans les paramètres **Éditeur de texte – Tous les langages** (**Outils** > **Options** > **Éditeur de texte** > **Tous les langages**). Vous pouvez afficher des numéros de ligne pour les langages de programmation individuels en modifiant les paramètres de ces langues **(Tools** > **Options** > **Text Editor** > **\<langue>**). Pour imprimer les numéros de ligne, sélectionnez **Inclure les numéros de ligne** dans la boîte de dialogue **Imprimer**.|
|Suivi des modifications|La couleur de la marge de gauche vous permet de conserver une trace des modifications effectuées dans un fichier. Les modifications que vous avez effectuées depuis l’ouverture du fichier mais que vous n’avez pas enregistrées sont signalées par une barre jaune dans la marge de gauche (appelée marge de sélection). Une fois que vous avez enregistré les modifications (mais avant la fermeture du fichier), la barre devient verte. Si vous annulez une modification après avoir enregistré le fichier, la barre devient orange. Pour activer et désactiver cette fonctionnalité, modifiez l’option **Suivi des modifications** dans les paramètres **Éditeur de texte** (**Outils** > **Options** > **Éditeur de texte**).|
|Sélection de code et de texte|Vous pouvez sélectionner du texte en mode linéaire standard ou en mode Zone, dans lequel vous sélectionnez une partie rectangulaire du texte au lieu d’un ensemble de lignes. Pour faire une sélection en mode boîte, appuyez sur **Alt** que vous faites glisser la souris sur la sélection (ou appuyez sur **Alt**+**Shift**+**\<clé de flèche>**). La sélection inclut tous les caractères compris dans le rectangle défini par le premier caractère et le dernier caractère de la sélection. Tout texte tapé ou collé dans la zone sélectionnée est inséré au même endroit sur chaque ligne.|
|Zoom|Vous pouvez effectuer un zoom avant ou arrière dans n’importe quelle fenêtre de code en maintenant enfoncée la touche **Ctrl** tout en actionnant la roulette de défilement de la souris (ou en appuyant sur **Ctrl**+**Maj**+**.** d’augmenter et **Ctrl**+**Shift**+**,** à diminuer). Vous pouvez également utiliser la boîte **Zoom** dans le coin inférieur gauche de la fenêtre de code pour définir un pourcentage de zoom spécifique. La fonctionnalité de zoom ne fonctionne pas dans les fenêtres d’outils.|
|Espace virtuel|Par défaut, les lignes dans les éditeurs Visual Studio se terminent après le dernier personnage, de sorte que la clé **Right Arrow** à la fin d’une ligne déplace le curseur au début de la ligne suivante. Dans certains autres éditeurs, une ligne ne se termine pas après le dernier caractère et vous pouvez placer le curseur n’importe où sur la ligne. Vous pouvez activer l’espace virtuel dans l’éditeur dans les **paramètres Tools** > **Options** > **Text Editor** > **All Languages.** Notez que vous pouvez activer l’option **Espace virtuel** ou **Retour automatique à la ligne**, mais pas les deux.|
|Impression|Vous pouvez utiliser les options de la boîte de dialogue **Imprimer** pour inclure les numéros de ligne ou masquer les régions réduites de code quand vous imprimez un fichier. Dans la boîte de dialogue **Mise en page** , vous pouvez également choisir d’imprimer le chemin d’accès complet et le nom du fichier en choisissant **En-tête**.<br /><br /> Vous pouvez définir des options d’impression couleur dans la boîte de dialogue **Tools** > **Options** > **Environment** > **Fonts and Colors.** Choisissez **Imprimante** dans la liste **Afficher les paramètres de** pour personnaliser l’impression couleur. Vous pouvez spécifier des couleurs différentes pour imprimer un fichier que pour le modifier.|
|Annulation globale et rétablissement global|Les commandes **Annuler la dernière action globale** et **Rétablir la dernière action globale** du menu **Edition** annulent et rétablissent les actions globales qui affectent plusieurs fichiers. Les actions globales incluent la modification du nom d’une classe ou d’un espace de noms, l’exécution d’une opération de recherche et remplacement dans une solution, la refactorisation d’une base de données ou toute autre action qui modifie plusieurs fichiers. Vous pouvez appliquer les commandes globales d’annulation et de rétablissement aux actions de la session Visual Studio actuelle, même après avoir fermé la solution dans laquelle une action a été appliquée.|

## <a name="advanced-editing-features"></a>Fonctionnalités d’édition avancées

Vous pouvez trouver un certain nombre de fonctionnalités avancées sur le menu **Edit** > **Advanced** sur la barre d’outils. Toutes ces fonctionnalités ne sont pas disponibles pour tous les types de fichiers de code.

|||
|-|-|
|Mettre le document en forme|Définit la mise en retrait appropriée des lignes de code et place des accolades pour séparer les lignes dans le document.|
|Mettre la sélection en forme|Définit la mise en retrait appropriée des lignes de code et place des accolades pour séparer les lignes dans la sélection.|
|Remplacer les espaces par des tabulations|Remplace les espaces à gauche par des tabulations le cas échéant.|
|Remplacer les tabulations par des espaces|Remplace les tabulations à gauche par des espaces. Si vous souhaitez convertir tous les espaces de votre fichier en tabulations (ou toutes les tabulations en espaces), vous pouvez utiliser les commandes `Edit.ConvertSpacesToTabs` et `Edit.ConvertTabsToSpaces`. Ces commandes n’apparaissent pas dans les menus Visual Studio, mais vous pouvez les appeler à partir de la fenêtre **d’accès rapide** ou de la fenêtre de commande.|
|Mettre en majuscules|Met tous les caractères de la sélection en majuscules ou, en l’absence de sélection, met en majuscule le caractère au point d’insertion. Shortcut: **Ctrl**+**Shift**+**U**.|
|Mettre en minuscules|Met tous les caractères de la sélection en minuscules ou, en l’absence de sélection, met en minuscule le caractère au point d’insertion. Shortcut: **Ctrl**+**U**.|
|Déplacer les lignes sélectionnées vers le haut|Déplace la ligne sélectionnée d’une ligne vers le haut. Shortcut: **Alt**+**Up Arrow**.|
|Déplacer les lignes sélectionnées vers le bas|Déplace la ligne sélectionnée d’une ligne vers le bas. Shortcut: **Alt**+**Down Arrow**.|
|Supprimer les espaces blancs horizontaux|Supprime les tabulations et les espaces à la fin de la ligne active. Raccourci: **Ctrl**+**K**, **Ctrl**+**\\**|
|Afficher les espaces blancs|Affiche les espaces sous forme de points et les tabulations sous forme de flèches. La fin d’un fichier est indiquée par un glyphe rectangulaire. Si **Tools** > **Options** > **Text Editor** > **All Languages** > **Word Wrap** > **Afficher des glyphes visibles pour l’enveloppe de mot** est sélectionné, ce glyphe est également affiché.|
|Retour automatique à la ligne|Rend visibles toutes les lignes d’un document dans la fenêtre de code. Vous pouvez activer et désactiver cette fonctionnalité dans les paramètres **Éditeur de texte – Tous les langages** (**Outils** > **Options** > **Éditeur de texte** > **Tous les langages**).|
|Commenter la sélection|Ajoute des caractères de commentaire à la sélection ou à la ligne active. Shortcut: **Ctrl**+**K**, **Ctrl**+**C**|
|Supprimer les marques de commentaire de la sélection|Supprime les caractères de commentaire de la sélection ou de la ligne active. Shortcut: **Ctrl**+**K**, **Ctrl**+**U**|
|Augmenter le retrait de ligne|Ajoute une tabulation (ou les espaces équivalents) aux lignes sélectionnées ou à la ligne active.|
|Réduire le retrait de ligne|Supprime une tabulation (ou les espaces équivalents) des lignes sélectionnées ou de la ligne active.|
|Sélectionner la balise|Dans un document qui contient des balises (par exemple, XML ou HTML), sélectionne la balise.|
|Sélectionner le contenu de la balise|Dans un document qui contient des balises (par exemple, XML ou HTML), sélectionne le contenu.|

## <a name="navigate-and-find-code"></a>Parcourir et rechercher du code

Vous pouvez vous déplacer dans l’éditeur de code de plusieurs manières, notamment naviguer vers l’arrière et vers l’avant pour atteindre des points d’insertion spécifiques, afficher la définition d’un type ou d’un membre et accéder à une méthode spécifique à l’aide de la barre de navigation. Pour plus d’informations, consultez [Naviguer dans le code](navigating-code.md).

## <a name="find-references-in-your-code-base"></a>Rechercher des références dans votre code base

Pour savoir où des éléments de code particuliers sont référencés dans l’ensemble de votre code base, vous pouvez utiliser la commande **Rechercher toutes les références** ou appuyer sur **Maj**+**F12**. De plus, quand vous cliquez sur un type ou un membre, la fonctionnalité de **mise en surbrillance des références** met automatiquement en surbrillance toutes les références à ce type ou membre. Pour plus d’informations, consultez [Rechercher des références dans votre code](finding-references.md).

## <a name="customize-the-editor"></a>Personnaliser l’éditeur

Vous pouvez partager vos paramètres Visual Studio avec un autre développeur, rendre vos paramètres conformes à une norme ou rétablir les paramètres par défaut de Visual Studio à l’aide de la commande **Assistant Importation et exportation de paramètres** du menu **Outils**. Dans l’**Assistant Importation et exportation de paramètres**, vous pouvez changer des paramètres généraux sélectionnés ou des paramètres spécifiques à un langage ou à un projet.

Pour définir de nouveaux hotkeys ou redéfinir les hotkeys existants, rendez-vous sur **Tools** > **Options** > **Environment** > **Keyboard**. Pour plus d’informations sur les hotkeys, voir [les raccourcis clavier par défaut](../ide/default-keyboard-shortcuts-in-visual-studio.md).

Pour connaître les options de l’éditeur propres à JavaScript, consultez la page [Options JavaScript de l’éditeur](../ide/reference/options-text-editor-javascript-formatting.md).

## <a name="see-also"></a>Voir aussi

- [Éditeur de code source (Visual Studio pour Mac)](/visualstudio/mac/source-editor)
- [IDE Visual Studio](../get-started/visual-studio-ide.md)
- [Lancez-vous avec CMD dans Visual Studio](/cpp/get-started/tutorial-console-cpp)
- [Bien démarrer avec C# et ASP.NET dans Visual Studio](../get-started/csharp/tutorial-aspnet-core.md)
- [Bien démarrer avec C++ dans Visual Studio](../ide/quickstart-python.md)
