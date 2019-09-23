---
title: Fonctionnalités de l’éditeur de code
ms.date: 02/23/2018
ms.topic: conceptual
helpviewer_keywords:
- code, editing [Visual Studio]
- code editor [Visual Studio]
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3d2540b0c725860ea9a21f32d1d01074cf39380f
ms.sourcegitcommit: 6993bcb0d2b0067b1b7b7899bfba52c31c70b7e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2019
ms.locfileid: "71095284"
---
# <a name="features-of-the-code-editor"></a>Fonctionnalités de l’éditeur de code

L’éditeur Visual Studio fournit de nombreuses fonctionnalités facilitant l’écriture et la gestion de votre code et de votre texte. Vous pouvez développer et réduire différents blocs de code en utilisant le mode Plan. Vous pouvez obtenir plus d’informations sur le code en utilisant IntelliSense, **l’Explorateur d’objets**et la hiérarchie d’appels. Vous pouvez rechercher du code en utilisant des fonctionnalités telles que **Atteindre**, **Atteindre la définition** et **Rechercher toutes les références**. Vous pouvez insérer des blocs de code à l’aide d’extraits de code et vous pouvez générer du code en utilisant des fonctionnalités telles que **Générer à partir de l’utilisation**. Si vous n’avez encore jamais utilisé l’éditeur de Visual Studio, consultez [Éditer votre code](https://visualstudio.microsoft.com/vs/features/ide/) pour obtenir une vue d’ensemble rapide.

> [!NOTE]
> Cette rubrique s’applique à Visual Studio sur Windows. Pour Visual Studio pour Mac, consultez [Éditeur de code Source (Visual Studio pour Mac)](/visualstudio/mac/source-editor).

Vous pouvez afficher votre code de différentes façons. Par défaut, **l’Explorateur de solutions** affiche votre code organisé par fichiers. Pour afficher votre code organisé par classes, cliquez sur l’onglet **Affichage de classes** situé en bas de la fenêtre.

Vous pouvez rechercher et remplacer du texte dans un ou plusieurs fichiers. Pour plus d’informations, consultez [Rechercher et remplacer du texte](../ide/finding-and-replacing-text.md). Vous pouvez utiliser des expressions régulières pour rechercher et remplacer du texte. Pour plus d’informations, consultez [Utiliser des expressions régulières dans Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

Les différents langages de Visual Studio offrent différents ensembles de fonctionnalités et, dans certains cas, les fonctionnalités se comportent différemment dans les différents langages. Un grand nombre de ces différences sont spécifiées dans les descriptions des fonctionnalités, mais pour plus d’informations, vous pouvez consulter les sections relatives aux langages spécifiques de Visual Studio.

## <a name="editor-features"></a>Fonctionnalités de l’éditeur

|||
|-|-|
|Couleurs de syntaxe|Certains éléments de syntaxe des fichiers de code et de balisage apparaissent dans des couleurs différentes pour que vous puissiez les distinguer. Par exemple, les mots clés (tels que `using` en C# et `Imports` en Visual Basic) apparaissent dans une couleur, alors que les types (tels que `Console` et `Uri`) sont d’une autre couleur. D’autres éléments de syntaxe sont également colorés, tels que les commentaires et les littéraux de chaîne. C++ utilise la couleur pour différencier les types, les énumérations et les macros parmi les autres jetons.<br /><br /> Vous pouvez voir la couleur par défaut de chaque type et changer la couleur de tout élément de syntaxe spécifique dans la [boîte de dialogue Polices et couleurs, Environnement, Options](../ide/reference/fonts-and-colors-environment-options-dialog-box.md), que vous pouvez ouvrir à partir du menu **Outils**.|
|Marques d’erreur et d’avertissement|Quand vous ajoutez du code et générez votre solution, vous pouvez voir s’afficher (a) des soulignements ondulés de différente couleur (les tildes) ou (b) des ampoules dans votre code. Les soulignements ondulés rouges indiquent des erreurs de syntaxe, les soulignements ondulés bleus indiquent des erreurs de compilateur, les soulignements ondulés verts indiquent des avertissements et les soulignements ondulés violets indiquent d’autres types d’erreur. Les [actions rapides](../ide/quick-actions.md) suggèrent des solutions aux problèmes rencontrés et facilitent la correction des erreurs.<br /><br /> La couleur par défaut du soulignement ondulé des différentes erreurs et des différents avertissements est présentée dans la boîte de dialogue **Outils** > **Options** > **Environnement** > **Polices et couleurs**. Recherchez **Erreur de syntaxe**, **Erreur du compilateur**, **Avertissement**et **Autre erreur**.|
|Accolades correspondantes|Quand le point d’insertion est placé sur une accolade ouvrante dans un fichier de code, l’accolade ouvrante et l’accolade fermante sont mises en surbrillance. Cette fonctionnalité vous permet de visualiser immédiatement les accolades mal placées ou manquantes. Vous pouvez activer ou désactiver la correspondance d’accolade à l’aide du paramètre **Mise en surbrillance automatique des délimiteurs** (**Outils** > **Options** > **Éditeur de texte**). Vous pouvez modifier la couleur de surbrillance dans le paramètre **Polices et couleurs** (**Outils** > **Options** > **Environnement**). Recherchez **Accolades correspondantes (en surbrillance)** ou **Accolades correspondantes (rectangle)** .|
|Visualiseur de structure|Des lignes en pointillés connectent les accolades correspondantes dans les fichiers de code, permettant de voir plus facilement les paires d’accolades ouvrantes et fermantes. Cela vous permet de trouver plus rapidement du code dans votre code base. Vous pouvez activer ou désactiver ces lignes à l’aide de l’option **Afficher les lignes de repère de structure** située dans la section **Affichage** de la page **Outils** > **Options** > **Éditeur de texte** > **Général**.|
|Numéros de ligne|Les numéros de ligne peuvent être affichés dans la marge de gauche de la fenêtre de code. Ils ne sont pas affichés par défaut. Vous pouvez activer cette option dans les paramètres **Éditeur de texte – Tous les langages** (**Outils** > **Options** > **Éditeur de texte** > **Tous les langages**). Vous pouvez afficher les numéros de ligne des différents langages de programmation en modifiant les paramètres de ces langages (**Outils** > **Options** > **Éditeur de texte** >  **\<langage>** ). Pour imprimer les numéros de ligne, sélectionnez **Inclure les numéros de ligne** dans la boîte de dialogue **Imprimer**.|
|Suivi des modifications|La couleur de la marge de gauche vous permet de conserver une trace des modifications effectuées dans un fichier. Les modifications que vous avez effectuées depuis l’ouverture du fichier mais que vous n’avez pas enregistrées sont signalées par une barre jaune dans la marge de gauche (appelée marge de sélection). Une fois que vous avez enregistré les modifications (mais avant la fermeture du fichier), la barre devient verte. Si vous annulez une modification après avoir enregistré le fichier, la barre devient orange. Pour activer et désactiver cette fonctionnalité, modifiez l’option **Suivi des modifications** dans les paramètres **Éditeur de texte** (**Outils** > **Options** > **Éditeur de texte**).|
|Sélection de code et de texte|Vous pouvez sélectionner du texte en mode linéaire standard ou en mode Zone, dans lequel vous sélectionnez une partie rectangulaire du texte au lieu d’un ensemble de lignes. Pour effectuer une sélection en mode Zone, appuyez sur **Alt** en faisant glisser la souris sur le contenu à sélectionner (ou appuyez sur **Alt**+**Maj**+ **\<touche fléchée>** ). La sélection inclut tous les caractères compris dans le rectangle défini par le premier caractère et le dernier caractère de la sélection. Tout texte tapé ou collé dans la zone sélectionnée est inséré au même endroit sur chaque ligne.|
|Zoom|Vous pouvez effectuer un zoom avant ou arrière dans n’importe quelle fenêtre de code en maintenant enfoncée la touche **Ctrl** tout en actionnant la roulette de défilement de la souris (ou en appuyant sur **Ctrl**+**Maj**+ **.** pour agrandir l’image et sur **Ctrl**+**Maj**+ **,** pour la réduire). Vous pouvez également utiliser la zone **Zoom** dans le coin inférieur gauche de la fenêtre de code pour définir un pourcentage de zoom spécifique. La fonctionnalité de zoom ne fonctionne pas dans les fenêtres d’outils.|
|Espace virtuel|Par défaut, les lignes dans les éditeurs de Visual Studio se terminent après le dernier caractère, de sorte qu’appuyer sur la touche de direction **Droite** à la fin d’une ligne déplace le curseur au début de la ligne suivante. Dans certains autres éditeurs, une ligne ne se termine pas après le dernier caractère et vous pouvez placer le curseur n’importe où sur la ligne. Vous pouvez activer l’espace virtuel dans l’éditeur, dans les paramètres **Outils** > **Options** > **Éditeur de texte** > **Tous les langages**. Notez que vous pouvez activer l’option **Espace virtuel** ou **Retour automatique à la ligne**, mais pas les deux.|
|Impression|Vous pouvez utiliser les options de la boîte de dialogue **Imprimer** pour inclure les numéros de ligne ou masquer les régions réduites de code quand vous imprimez un fichier. Dans la boîte de dialogue **Mise en page** , vous pouvez également choisir d’imprimer le chemin d’accès complet et le nom du fichier en choisissant **En-tête**.<br /><br /> Vous pouvez définir des options d’impression couleur dans la boîte de dialogue **Outils** > **Options** > **Environnement** > **Polices et couleurs**. Choisissez **Imprimante** dans la liste **Afficher les paramètres de** pour personnaliser l’impression couleur. Vous pouvez spécifier des couleurs différentes pour imprimer un fichier que pour le modifier.|
|Annulation globale et rétablissement global|Les commandes **Annuler la dernière action globale** et **Rétablir la dernière action globale** du menu **Edition** annulent et rétablissent les actions globales qui affectent plusieurs fichiers. Les actions globales incluent la modification du nom d’une classe ou d’un espace de noms, l’exécution d’une opération de recherche et remplacement dans une solution, la refactorisation d’une base de données ou toute autre action qui modifie plusieurs fichiers. Vous pouvez appliquer les commandes globales d’annulation et de rétablissement aux actions de la session Visual Studio actuelle, même après avoir fermé la solution dans laquelle une action a été appliquée.|

## <a name="advanced-editing-features"></a>Fonctionnalités d’édition avancées

De nombreuses fonctionnalités avancées sont disponibles dans le menu **Édition** > **Avancé** de la barre d’outils. Toutes ces fonctionnalités ne sont pas disponibles pour tous les types de fichiers de code.

|||
|-|-|
|Mettre le document en forme|Définit la mise en retrait appropriée des lignes de code et place des accolades pour séparer les lignes dans le document.|
|Mettre la sélection en forme|Définit la mise en retrait appropriée des lignes de code et place des accolades pour séparer les lignes dans la sélection.|
|Remplacer les espaces par des tabulations|Remplace les espaces à gauche par des tabulations le cas échéant.|
|Remplacer les tabulations par des espaces|Remplace les tabulations à gauche par des espaces. Si vous souhaitez convertir tous les espaces de votre fichier en tabulations (ou toutes les tabulations en espaces), vous pouvez utiliser les commandes `Edit.ConvertSpacesToTabs` et `Edit.ConvertTabsToSpaces`. Ces commandes n’apparaissent pas dans les menus de Visual Studio, mais vous pouvez les appeler à partir de la fenêtre **Accès rapide** ou de la fenêtre Commande.|
|Mettre en majuscules|Met tous les caractères de la sélection en majuscules ou, en l’absence de sélection, met en majuscule le caractère au point d’insertion. Raccourci : **Ctrl**+**Maj**+**U**.|
|Mettre en minuscules|Met tous les caractères de la sélection en minuscules ou, en l’absence de sélection, met en minuscule le caractère au point d’insertion. Raccourci : **Ctrl**+**U**.|
|Déplacer les lignes sélectionnées vers le haut|Déplace la ligne sélectionnée d’une ligne vers le haut. Raccourci : **Alt**+**Flèche Haut**.|
|Déplacer les lignes sélectionnées vers le bas|Déplace la ligne sélectionnée d’une ligne vers le bas. Raccourci : **Alt**+**Flèche Bas**.|
|Supprimer les espaces blancs horizontaux|Supprime les tabulations et les espaces à la fin de la ligne active. Raccourci : **Ctrl**+**K**, **Ctrl**+ **\\**|
|Afficher les espaces blancs|Affiche les espaces sous forme de points et les tabulations sous forme de flèches. La fin d’un fichier est indiquée par un glyphe rectangulaire. Si l’option **Outils** > **Options** > **Éditeur de texte** > **Tous les langages** > **Retour automatique à la ligne** > **Afficher des glyphes visuels pour le retour automatique à la ligne** est sélectionnée, ce glyphe s’affiche également.|
|Retour automatique à la ligne|Rend visibles toutes les lignes d’un document dans la fenêtre de code. Vous pouvez activer et désactiver cette fonctionnalité dans les paramètres **Éditeur de texte – Tous les langages** (**Outils** > **Options** > **Éditeur de texte** > **Tous les langages**).|
|Commenter la sélection|Ajoute des caractères de commentaire à la sélection ou à la ligne active. Raccourci : **Ctrl**+**K**, **Ctrl**+**C**|
|Annuler le commentaire de la sélection|Supprime les caractères de commentaire de la sélection ou de la ligne active. Raccourci : **Ctrl**+**K**, **Ctrl**+**U**|
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

Pour définir de nouvelles touches d’accès rapide ou en redéfinir d’anciennes, accédez à **Outils** > **Options** > **Environnement** > **Clavier**. Pour plus d’informations sur les touches d’accès rapide, consultez la page [Raccourcis clavier par défaut](../ide/default-keyboard-shortcuts-in-visual-studio.md).

Pour connaître les options de l’éditeur propres à JavaScript, consultez la page [Options JavaScript de l’éditeur](../ide/reference/options-text-editor-javascript-formatting.md).

## <a name="see-also"></a>Voir aussi

- [Éditeur de code source (Visual Studio pour Mac)](/visualstudio/mac/source-editor)
- [IDE Visual Studio](../get-started/visual-studio-ide.md)
- [Bien démarrer avec C++ dans Visual Studio](/cpp/get-started/tutorial-console-cpp)
- [Bien démarrer avec C# et ASP.NET dans Visual Studio](../get-started/csharp/tutorial-aspnet-core.md)
- [Bien démarrer avec Python dans Visual Studio](../ide/quickstart-python.md)
