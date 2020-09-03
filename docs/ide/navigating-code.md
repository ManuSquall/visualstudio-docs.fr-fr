---
title: Commandes de navigation dans le code
ms.date: 11/21/2019
ms.topic: conceptual
helpviewer_keywords:
- code editor, navigation
- code editor, go to
- code editor, go to definition
- code editor, go to line
- code editor, peek definition
- code editor, navigation bar
- go to definition
- peek definition
- go to line
- go to
author: TerryGLee
ms.author: tglee
manager: tglee
ms.workload:
- multiple
ms.openlocfilehash: 0216a71b675473d54aec9738ea7bdc85b7643841
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75585819"
---
# <a name="navigate-code"></a>Naviguer dans le code

Visual Studio propose de nombreuses manières de parcourir le code dans l’éditeur. Cette rubrique résume les différentes façons de naviguer dans votre code, et fournit des liens vers des rubriques qui abordent ce sujet plus en détail.

## <a name="navigate-backward-and-navigate-forward-commands"></a>Commandes Naviguer vers l’arrière et Naviguer vers l’avant

Vous pouvez utiliser les boutons naviguer vers l' **arrière** (**CTRL** + **-** ) et naviguer vers l' **avant** (**CTRL** + **MAJ** + **-** ) de la barre d’outils pour déplacer le point d’insertion vers des emplacements précédents ou pour revenir à un emplacement plus récent à partir d’un emplacement précédent. Ces boutons conservent les 20 derniers emplacements du point d’insertion. Ces commandes sont également disponibles dans le menu **Afficher**, sous **Naviguer vers l’arrière** et **Naviguer vers l’avant**.

![Boutons de navigation Suivant et Précédent](../ide/media/vs2017_nav_buttons.png)

## <a name="navigation-bar"></a>Barre de navigation

Vous pouvez utiliser la **barre de navigation** (les zones de liste déroulante situées en haut de la fenêtre de code) pour accéder à du code dans un code base. Vous pouvez choisir un type ou un membre pour l’atteindre directement. La barre de navigation s’affiche quand vous modifiez du code dans un code base Visual Basic, C# ou C++. Dans une classe partielle, les membres définis en dehors du fichier de code actuel peuvent être désactivés (ils sont affichés en gris).

![Barre de navigation dans le code](../ide/media/vside_navigation_bar.png)

Vous pouvez naviguer dans les zones de liste déroulante comme suit :

- Pour naviguer vers un autre projet auquel appartient le fichier actuel, choisissez-le dans la liste déroulante de gauche.

- Pour accéder à une classe ou à un type, choisissez-le dans la liste déroulante du milieu.

- Pour accéder directement à une procédure ou à un autre membre d’une classe, choisissez-le dans la liste déroulante de droite.

- Pour déplacer le focus de la fenêtre de code vers la barre de navigation, appuyez sur la combinaison de touches de raccourci **CTRL** + **F2**.

- Pour déplacer le focus d’une zone à l’autre dans la barre de navigation, appuyez sur la touche **Tab**.

- Pour sélectionner l’élément de la barre de navigation qui a le focus et retourner dans la fenêtre de code, appuyez sur la touche **Entrée**.

- Pour ramener le focus de la barre de navigation dans le code sans sélectionner aucun élément, appuyez sur la touche **Échap**.

Pour masquer la barre de navigation, modifiez l’option **barre de navigation** dans les paramètres **tous les langages** de l’éditeur de texte (**Outils**  >  **options**  >  **éditeur de texte**  >  **tous les langages**) ou modifiez les paramètres des différentes langues.

## <a name="find-all-references"></a>Rechercher toutes les références

Cette option permet de rechercher toutes les références à l’élément sélectionné dans la solution. Vous pouvez l’utiliser pour vérifier l’existence d’éventuels effets secondaires d’une refactorisation volumineuse or de code « mort ». Appuyez sur **F8** pour basculer d’un résultat à un autre. Pour plus d’informations, consultez [Rechercher des références dans votre code](finding-references.md).

Entrée | Fonction
------------ | ---
**Clavier** | Placez le curseur de texte à l’intérieur du nom de type, puis appuyez sur **MAJ** + **F12** .
**Souris** | Sélectionnez **Rechercher toutes les références** dans le menu contextuel (clic droit)

## <a name="reference-highlighting"></a>Mise en surbrillance des références

Quand vous cliquez sur un symbole dans le code source, toutes les instances de ce symbole sont mises en surbrillance dans le document. Les symboles en surbrillance peuvent inclure des déclarations et des références, ainsi que de nombreux autres symboles pouvant être retournés par la fonctionnalité **Rechercher toutes les références** . Ceux-ci incluent les noms de classes, d’objets, de variables, de méthodes et de propriétés. Dans le code Visual Basic, les mots clés de nombreuses structures de contrôle sont également mis en surbrillance. Pour passer au symbole en surbrillance suivant ou précédent, appuyez sur **CTRL** + **MAJ** + **flèche bas** ou **CTRL** + **MAJ** + **flèche haut**. Vous pouvez modifier la couleur de mise en surbrillance dans **Outils**  >  **options**  >  **environnement**  >  **polices et couleurs**  >  **référence en surbrillance**.

## <a name="go-to-commands"></a>Commandes Atteindre

L’option Atteindre propose les commandes suivantes, disponibles dans le menu **Édition**, sous **Atteindre** :

- **Atteindre la ligne** (**Ctrl**+**G**) : accéder au numéro de ligne spécifié dans le document actif.

- **Atteindre tout** (**CTRL** + **T** ou **CTRL** + **,**) : accéder à la ligne, au type, au fichier, au membre ou au symbole spécifié.

- **Atteindre le fichier** (**CTRL** + **1**, **CTRL** + **F**) : accéder au fichier spécifié dans la solution.

- **Accéder au fichier récent** (**CTRL** + **1**, **CTRL** + **R**) : accéder au fichier spécifié, visité récemment dans la solution.

- **Atteindre le type** (**CTRL** + **1**, **CTRL** + **T**) : accéder au type spécifié dans la solution.

- **Atteindre le membre** (**CTRL** + **1**, **CTRL** + **M**) : accéder au membre spécifié dans la solution.

- **Atteindre le symbole** (**CTRL** + **1**, **CTRL** + **S**) : accéder au symbole spécifié dans la solution.

Dans Visual Studio 2017 version 15.8 et les versions ultérieures, les commandes de navigation **Atteindre** suivantes sont également disponibles :

- **Aller au problème suivant dans le fichier** (**Alt**+**Pg. suiv**) et **Aller au problème précédent dans le fichier** (**Alt**+**Pg. préc**)

- **Accéder à l’emplacement de la dernière modification** (**Ctrl**+**Maj**+**Ret. arr**)

Découvrez plus en détail ces commandes dans la rubrique [Rechercher du code à l’aide des commandes Atteindre](../ide/go-to.md).

## <a name="go-to-definition"></a>Atteindre la définition

L’option Atteindre la définition permet d’atteindre la définition de l’élément sélectionné. Pour plus d’informations, consultez [Atteindre la définition et Aperçu de la définition](../ide/go-to-and-peek-definition.md).

Entrée | Fonction
------------ | ---
**Clavier** | Placez le curseur de texte à l’intérieur du nom de type, puis appuyez sur **F12**.
**Souris** | Cliquez avec le bouton droit sur le nom de type et sélectionnez **Atteindre la définition** OU appuyez sur **Ctrl**, puis cliquez sur le nom de type.

## <a name="peek-definition"></a>Aperçu de la définition

L’option Aperçu de la définition affiche la définition de l’élément sélectionné dans une fenêtre sans vous obliger à quitter votre emplacement actuel dans l’éditeur de code. Pour plus d’informations, consultez [Comment : afficher et modifier le code à l’aide de l’aperçu de définition](../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md) et atteindre la définition [et aperçu de la définition](../ide/go-to-and-peek-definition.md).

Entrée | Fonction
------------ | ---
**Clavier** | Placez le curseur de texte à l’intérieur du nom de type, puis appuyez sur **ALT** + **F12** .
**Souris** | Cliquez avec le bouton droit sur le nom de type et sélectionnez **Aperçu de la définition** OU appuyez sur **Ctrl** et cliquez sur le nom de type (si l’option **Ouvrir la définition dans l’aperçu** est sélectionnée)

## <a name="go-to-implementation"></a>Accéder à l’implémentation

L’option Accéder à l’implémentation vous permet de naviguer d’un type ou d’une classe de base vers ses implémentations. S’il existe plusieurs implémentations, elles sont répertoriées dans la fenêtre **Résultats de la recherche de symbole** :

Entrée | Fonction
------------ | ---
**Clavier** | Placez le curseur de texte à l’intérieur du nom de type, puis appuyez sur **CTRL** + **F12**
**Souris** | Cliquez avec le bouton droit sur le nom de type et sélectionnez **Accéder à l’implémentation**.

## <a name="go-to-base"></a>Accéder à la base

À l’aide de l’option atteindre la base, vous pouvez naviguer vers le haut de la chaîne d’héritage de l’élément sélectionné. S’il y a plusieurs résultats, ceux-ci sont répertoriés dans la fenêtre **atteindre la base** :

Entrée | Fonction
------------ | ---
**Clavier** | Placez le curseur de texte à l’intérieur du nom de type, puis appuyez sur **ALT**de + **début**
**Souris** | Cliquez avec le bouton droit sur le nom du type et sélectionnez **atteindre la base** .

## <a name="call-hierarchy"></a>Hiérarchie d'appels

Vous pouvez afficher les appels en provenance et à destination d’une méthode dans la [fenêtre Hiérarchie d’appels](../ide/reference/call-hierarchy.md):

Entrée | Fonction
------------ | ---
**Clavier** | Placez le curseur de texte à l’intérieur du nom de type, puis appuyez sur **CTRL** + **K**, **CTRL** + **T**
**Souris** | Cliquez avec le bouton droit sur le nom du membre, puis sélectionnez **Afficher la hiérarchie d’appels**

## <a name="next-method-and-previous-method-commands-visual-basic"></a>Commandes Méthode suivante et Méthode précédente (Visual Basic)

Dans des fichiers de code Visual Basic, utilisez ces commandes pour déplacer le point d’insertion vers les différentes méthodes. Choisissez **modifier**la  >  **méthode suivante** ou **modifier**la  >  **méthode précédente**.

## <a name="structure-visualizer"></a>Visualiseur de structure

La fonctionnalité visualiseur de structure de l’éditeur de code affiche des lignes de *repère de structure* (lignes en pointillés verticales qui indiquent les accolades correspondantes dans votre code base). Cela permet de voir plus facilement où commencent et où se terminent les blocs logiques.

![Visualiseur de structure](../ide/media/vside_structure_visualizer.png)

Pour désactiver les lignes de repère de structure, accédez à **Outils**  >  **options**  >  **éditeur de texte**  >  **général** et décochez la case **afficher les lignes de repère de structure** .

## <a name="enhanced-scroll-bar"></a>Barre de défilement améliorée

Vous pouvez utiliser la barre de défilement améliorée dans une fenêtre de code pour bénéficier d’une vue panoramique de votre code. En mode plan, vous pouvez afficher des aperçus du code en déplaçant le curseur vers le haut et vers le bas dans la barre de défilement. Pour plus d’informations, consultez [Comment : suivre votre code en personnalisant la barre de défilement](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md).

## <a name="codelens-information"></a>Informations sur CodeLens

Vous pouvez rechercher des informations sur un code spécifique, telles que les modifications et les auteurs de ces modifications, les références, les bogues, les éléments de travail, les révisions du code et l’état de test unitaire quand vous utilisez CodeLens dans l’éditeur de code. CodeLens fonctionne comme un afficheur d’alertes quand vous utilisez Visual Studio Enterprise avec Team Foundation Server. Consultez [Rechercher les modifications de code et d’autres historiques](../ide/find-code-changes-and-other-history-with-codelens.md).

## <a name="see-also"></a>Voir aussi

- [Fonctionnalités de l’éditeur de code](../ide/writing-code-in-the-code-and-text-editor.md)
- [Afficher la hiérarchie d’appels](../ide/reference/call-hierarchy.md)
