---
title: Commandes de navigation dans le code
ms.date: 08/14/2018
ms.prod: visual-studio-dev15
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
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 467dec8039a50b225bda53de9b19b8539f6604be
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53877430"
---
# <a name="navigate-code"></a>Naviguer dans le code

Visual Studio propose de nombreuses manières de parcourir le code dans l’éditeur. Cette rubrique résume les différentes façons de naviguer dans votre code, et fournit des liens vers des rubriques qui abordent ce sujet plus en détail.

## <a name="navigate-backward-and-navigate-forward-commands"></a>Commandes Naviguer vers l’arrière et Naviguer vers l’avant

Vous pouvez utiliser les boutons **Naviguer vers l’arrière** (**Ctrl**+**-**) et **Naviguer vers l’avant** (**Ctrl**+**Maj**+**-**) de la barre d’outils pour déplacer le point d’insertion vers des emplacements précédents ou retourner à des emplacements plus récents à partir d’un emplacement précédent. Ces boutons conservent les 20 derniers emplacements du point d’insertion. Ces commandes sont également disponibles dans le menu **Afficher**, sous **Naviguer vers l’arrière** et **Naviguer vers l’avant**.

![Boutons de navigation Suivant et Précédent](../ide/media/vs2017_nav_buttons.png)

## <a name="navigation-bar"></a>Barre de navigation

Vous pouvez utiliser la **barre de navigation** (les zones de liste déroulante situées en haut de la fenêtre de code) pour accéder à du code dans un code base. Vous pouvez choisir un type ou un membre pour l’atteindre directement. La barre de navigation s’affiche quand vous modifiez du code dans un code base Visual Basic, C# ou C++. Dans une classe partielle, les membres définis en dehors du fichier de code actuel peuvent être désactivés (ils sont affichés en gris).

 ![Barre de navigation dans le code](../ide/media/vside_navigation_bar.png)

Vous pouvez naviguer dans les zones de liste déroulante comme suit :

- Pour naviguer vers un autre projet auquel appartient le fichier actuel, choisissez-le dans la liste déroulante de gauche.

- Pour accéder à une classe ou à un type, choisissez-le dans la liste déroulante du milieu.

- Pour accéder directement à une procédure ou à un autre membre d’une classe, choisissez-le dans la liste déroulante de droite.

- Pour déplacer le focus de la fenêtre de code vers la barre de navigation, appuyez sur la combinaison de touches de raccourci **Ctrl**+**F2**.

- Pour déplacer le focus d’une zone à l’autre dans la barre de navigation, appuyez sur la touche **Tab**.

- Pour sélectionner l’élément de la barre de navigation qui a le focus et retourner dans la fenêtre de code, appuyez sur la touche **Entrée**.

- Pour ramener le focus de la barre de navigation dans le code sans sélectionner aucun élément, appuyez sur la touche **Échap**.

Pour masquer la barre de navigation, changez l’option **Barre de navigation** dans les paramètres **Tous les langages de l’éditeur de texte** (**Outils** > **Options** > **Éditeur de texte** > **Tous les langages**). Vous pouvez également changer les paramètres pour des langages spécifiques.

## <a name="find-all-references"></a>Rechercher toutes les références

Cette option permet de rechercher toutes les références à l’élément sélectionné dans la solution. Vous pouvez l’utiliser pour vérifier l’existence d’éventuels effets secondaires d’une refactorisation volumineuse or de code « mort ». Appuyez sur **F8** pour basculer d’un résultat à un autre. Pour plus d’informations, consultez [Rechercher des références dans votre code](finding-references.md).

Entrée | Fonction
------------ | ---
**Clavier** | Placez le curseur de texte à l’intérieur du nom de type, puis appuyez sur **Maj**+**F12**
**Souris** | Sélectionnez **Rechercher toutes les références** dans le menu contextuel

## <a name="reference-highlighting"></a>Mise en surbrillance des références

Quand vous cliquez sur un symbole dans le code source, toutes les instances de ce symbole sont mises en surbrillance dans le document. Les symboles en surbrillance peuvent inclure des déclarations et des références, ainsi que de nombreux autres symboles pouvant être retournés par la fonctionnalité **Rechercher toutes les références** . Ceux-ci incluent les noms de classes, d’objets, de variables, de méthodes et de propriétés. Dans le code Visual Basic, les mots clés de nombreuses structures de contrôle sont également mis en surbrillance. Pour passer au symbole en surbrillance suivant ou précédent, appuyez sur **Ctrl**+**Maj**+**Flèche bas** ou **Ctrl**+**Maj**+**Flèche haut**. Vous pouvez changer la couleur de mise en surbrillance dans **Outils** > **Options** > **Environnement** > **Polices et couleurs** > **Référence en surbrillance**.

## <a name="go-to-commands"></a>Commandes Atteindre

L’option Atteindre propose les commandes suivantes, disponibles dans le menu **Édition**, sous **Atteindre** :

- **Atteindre la ligne** (**Ctrl**+**G**) : accéder au numéro de ligne spécifié dans le document actif.

- **Atteindre tout** (**Ctrl**+**T** ou **Ctrl**+**,**) : accéder à la ligne, au type, au fichier, au membre ou au symbole spécifié.

- **Atteindre le fichier** (**Ctrl**+**1**, **Ctrl**+**F**) : accéder au fichier spécifié dans la solution.

- **Aller au fichier récent** (**Ctrl**+**1**, **Ctrl**+**R**) : accéder au fichier spécifié, récemment ouvert, dans la solution (nouveauté de Visual Studio 2017 version 15.8).

- **Atteindre le type** (**Ctrl**+**1**, **Ctrl**+**T**) : accéder au type spécifié dans la solution.

- **Atteindre le membre** (**Ctrl**+**1**, **Ctrl**+**M**) : accéder au membre spécifié dans la solution.

- **Atteindre le symbole** (**Ctrl**+**1**, **Ctrl**+**S**) : accéder au symbole spécifié dans la solution.

Dans Visual Studio 2017 version 15.8 et les versions ultérieures, les commandes de navigation **Atteindre** suivantes sont également disponibles :

- **Aller au problème suivant dans le fichier** (**Alt**+**Pg. suiv**) et **Aller au problème précédent dans le fichier** (**Alt**+**Pg. préc**)

- **Accéder à l’emplacement de la dernière modification** (**Ctrl**+**Maj**+**Ret. arr**)

Découvrez plus en détail ces commandes dans la rubrique [Rechercher du code à l’aide des commandes Atteindre](../ide/go-to.md).

## <a name="go-to-definition"></a>Atteindre la définition

L’option Atteindre la définition permet d’atteindre la définition de l’élément sélectionné. Pour plus d’informations, consultez [Atteindre la définition et Aperçu de la définition](../ide/go-to-and-peek-definition.md).

Entrée | Fonction
------------ | ---
**Clavier** | Placez le curseur de texte à l’intérieur du nom de type, puis appuyez sur **F12**.
**Souris** | Cliquez avec le bouton droit sur le nom de type et sélectionnez **Atteindre la définition** OU appuyez sur **Ctrl**, puis cliquez sur le nom de type (nouveauté de Visual Studio 2017 version 15.4)

## <a name="peek-definition"></a>Aperçu de définition

L’option Aperçu de la définition affiche la définition de l’élément sélectionné dans une fenêtre sans vous obliger à quitter votre emplacement actuel dans l’éditeur de code. Pour plus d'informations, voir [Procédure : Afficher et modifier le code avec l’Aperçu de définition](../ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12.md) et [Atteindre la définition et Aperçu de la définition](../ide/go-to-and-peek-definition.md).

Entrée | Fonction
------------ | ---
**Clavier** | Placez le curseur de texte à l’intérieur du nom de type, puis appuyez sur **Alt**+**F12**
**Souris** | Cliquez avec le bouton droit sur le nom de type et sélectionnez **Aperçu de la définition** OU appuyez sur **Ctrl** et cliquez sur le nom de type (si l’option **Ouvrir la définition dans l’aperçu** est sélectionnée)

## <a name="go-to-implementation"></a>Accéder à l’implémentation

L’option Accéder à l’implémentation vous permet de naviguer d’un type ou d’une classe de base vers ses implémentations. S’il existe plusieurs implémentations, elles sont répertoriées dans la fenêtre **Résultats de la recherche de symbole** :

Entrée | Fonction
------------ | ---
**Clavier** | Placez le curseur de texte à l’intérieur du nom de type, puis appuyez sur **Ctrl**+**F12**
**Souris** | Cliquez avec le bouton droit sur le nom de type et sélectionnez **Accéder à l’implémentation**.

## <a name="call-hierarchy"></a>Hiérarchie d'appels

Vous pouvez afficher les appels en provenance et à destination d’une méthode dans la [fenêtre Hiérarchie d’appels](../ide/reference/call-hierarchy.md):

Entrée | Fonction
------------ | ---
**Clavier** | Placez le curseur de texte à l’intérieur du nom de type, puis appuyez sur **Ctrl**+**K**, **Ctrl**+**T**
**Souris** | Cliquez avec le bouton droit sur le nom du membre, puis sélectionnez **Afficher la hiérarchie d’appels**

## <a name="next-method-and-previous-method-commands-visual-basic"></a>Commandes Méthode suivante et Méthode précédente (Visual Basic)

Dans des fichiers de code Visual Basic, utilisez ces commandes pour déplacer le point d’insertion vers les différentes méthodes. Choisissez **Édition** > **Méthode suivante** ou **Édition** > **Méthode précédente**.

## <a name="structure-visualizer"></a>Visualiseur de structure

La fonctionnalité Visualiseur de structure de l’éditeur de code montre des *lignes de repère de structure* (lignes en pointillés verticales qui indiquent les accolades correspondantes dans votre code base). Cela permet de voir plus facilement où commencent et où se terminent les blocs logiques.

![Visualiseur de structure](../ide/media/vside_structure_visualizer.png)

Pour désactiver les lignes de repère de structure, accédez à **Outils** > **Options** > **Éditeur de texte** > **Général**, puis décochez la case **Afficher les lignes de repère de structure**.

## <a name="enhanced-scroll-bar"></a>Barre de défilement améliorée

Vous pouvez utiliser la barre de défilement améliorée dans une fenêtre de code pour bénéficier d’une vue panoramique de votre code. En mode plan, vous pouvez afficher des aperçus du code en déplaçant le curseur vers le haut et vers le bas dans la barre de défilement. Pour plus d'informations, voir [Procédure : Suivre votre code en personnalisant la barre de défilement](../ide/how-to-track-your-code-by-customizing-the-scrollbar.md).

## <a name="codelens-information"></a>Informations sur CodeLens

Vous pouvez rechercher des informations sur un code spécifique, telles que les modifications et les auteurs de ces modifications, les références, les bogues, les éléments de travail, les révisions du code et l’état de test unitaire quand vous utilisez CodeLens dans l’éditeur de code. CodeLens fonctionne comme un afficheur d’alertes quand vous utilisez Visual Studio Enterprise avec Team Foundation Server. Consultez [Rechercher les modifications de code et d’autres historiques](../ide/find-code-changes-and-other-history-with-codelens.md).

## <a name="see-also"></a>Voir aussi

- [Fonctionnalités de l’éditeur de code](../ide/writing-code-in-the-code-and-text-editor.md)
- [Afficher la hiérarchie d’appels](../ide/reference/call-hierarchy.md)
