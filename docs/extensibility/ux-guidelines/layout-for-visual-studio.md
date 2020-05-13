---
title: Mise en page pour Visual Studio (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c19e3022-047c-43b6-a046-a82717efed4f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4eb8eb7468751d46b922c15530389c554a8d3e36
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698404"
---
# <a name="layout-for-visual-studio"></a>Présentation pour Visual Studio
La majorité des dialogues Visual Studio sont [la mise en page du dialogue utilitaire](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_UtilityDialogLayout), qui sont les dialogues non considérés qui suivent les principes standard de mise en page de dialogue Windows [Desktop](/windows/desktop/uxguide/win-dialog-box). Comme Visual Studio se déplace pour rafraîchir son interface utilisateur, certains des dialogues les plus importants ont un nouveau design qui les établit comme des expériences de définition des produits. Ces [mises en page de dialogue thématique](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_ThemedDialogLayout) ont une apparence thématique.

## <a name="utility-dialog-layout"></a><a name="BKMK_UtilityDialogLayout"></a>Mise en page du dialogue utilitaire

- Tous les contrôles dans un dialogue utilitaire doivent commencer en haut/gauche et s’écouler vers le bas.

- Ne jamais centrer les commandes sur un dialogue pour remplir une grande surface.

- Utilisez la police de l’environnement pour tout le texte de dialogue. Lors de l’écriture d’une spécification visuelle, spécifiez la police de l’environnement au lieu de sélectionner une police et une taille particulières. Voir [La police de l’environnement](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).

- Utilisez un espacement et un placement de contrôle constants pour soutenir l’objectif de qualité de l’artisanat.

- Les dialogues peuvent devenir plus complexes à partir d’un plus grand nombre de contrôles, une juxtaposition unique de contrôles, ou les deux. Pour ces situations complexes, laisser suffisamment d’espace entre les groupes de contrôle pour donner à l’utilisateur un flux logique à analyser.

### <a name="utility-dialog-layout-examples"></a>Exemples de mise en page de dialogue d’utilité
 Toutes les dimensions sont exprimées sous forme de pixels.

 ![Espacement de boîte de dialogue pour les étiquettes au-dessus des contrôles](../../extensibility/ux-guidelines/media/0801-a_utilityspacingabove.png "0801-a_UtilitySpacingAbove")

 **Figure 08.01-a : Lignes directrices d’espacement pour les dialogues d’utilité avec des étiquettes au-dessus des contrôles**

 ![Espacement de boîte de dialogue pour les étiquettes à gauche des contrôles](../../extensibility/ux-guidelines/media/0801-b_utilityspacingleft.png "0801-b_UtilitySpacingLeft")

 **Figure 08.01-b : Lignes directrices d’espacement pour les dialogues utilitaires avec des étiquettes à gauche des contrôles**

### <a name="layout-details"></a>Détails de mise en page

#### <a name="margins"></a>Marges

- Tous les dialogues devraient avoir une bordure de 12 pixels sur tous les bords.

- Les marges dans un cadre de groupe doivent être de 9 pixels à partir du bord du cadre.

- Les marges dans un contrôle de l’onglet doivent être de 6 pixels à partir du bord du contrôle de l’onglet.

#### <a name="command-buttons"></a>Boutons de commande

- Les boutons de commande fonctionnent sur le cadre de dialogue, pas sur le contenu. Ils doivent être placés en bas à droite et doivent avoir assez d’espace variable au-dessus pour régler les boutons distinctement séparés.

- S’il y a des boutons horizontaux qui fonctionnent dans le dialogue, la configuration alternative de bouton de commande est une pile verticale en haut à droite. Voir [les boutons de commande intérieur ci-dessous.](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_InteriorCommandButtons)

- L’espace à gauche des boutons de commande (en bas à gauche/centre du dialogue) est considéré comme faisant partie de la « bande » des commandes de fonctionnement de dialogue. La seule chose qui devrait s’immiscer dans cet espace est un lien d’aide qui est pertinent à la tâche globale ou le dialogue.

- Les boutons de commande doivent être 75x23 pixels.

- Les boutons de commande doivent être distants de 6 pixels.

  ![Alignement des boutons de base](../../extensibility/ux-guidelines/media/0801-c_buttonalign.png "0801-c_ButtonAlign")

  **Figure 08.01-c : Alignement de bouton de base**

#### <a name="labels"></a>Étiquettes

- Alignez toutes les étiquettes.

- Pour les étiquettes qui se trouvent au-dessus d’un contrôle, ils doivent s’aligner précisément avec le contrôle en dessous et le bas de l’étiquette doit être de 5 pixels au-dessus du haut de l’autre contrôle (par exemple, une boîte combo).

- Pour les étiquettes qui se trouvent à gauche des commandes, la largeur minimale entre l’étiquette et le contrôle des entrées est de 10 pixels. Une deuxième colonne implicite doit être établie pour aligner les boîtes de texte, les boîtes combo, ou d’autres contrôles.

- Les étiquettes sont des cas de phrase et sont suivies d’un côlon. Voir [le style texte](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).

#### <a name="distance-between-controls"></a>Distance entre les commandes
 Stack contrôle raisonnablement. Il n’y a pas de ligne directrice absolue pour l’espacement entre les commandes empilées. L’étroitesse entre les contrôles peut varier légèrement d’un dialogue à l’autre. L’espacement recommandé est de 20 pixels pour les paires de contrôle/étiquette verticale, et de 9 pixels pour les paires de contrôle/étiquette horizontale. L’espacement minimum de contrôle pour les paires horizontales est de 6 pixels.

 ![Distance recommandée entre les contrôles](../../extensibility/ux-guidelines/media/0801-d_controldistance.png "0801-d_ControlDistance")

 **Figure 08.01-d : Recommandations de distance entre les contrôles**

#### <a name="control-indentation"></a>Contrôle de l’indentation
 Lorsque les commandes sont imbriquées, alignez les commandes intérieures horizontalement avec le bord gauche du contrôle ci-dessus, habituellement l’étiquette.

 ![Alignement des contrôles imbriqués](../../extensibility/ux-guidelines/media/0801-e_controlalign.png "0801-e_ControlAlign")

 **Figure 08.01-e : Alignement de contrôle imbriqué**

#### <a name="control-width"></a>Largeur de contrôle
 La largeur d’une boîte de texte ou d’autres contrôles similaires ne doit pas être plus longue que l’entrée moyenne pour le champ. Le mot anglais moyen est de cinq caractères. Par exemple, une boîte de texte qui nécessite un nom de long chemin doit être aussi longue que la disposition horizontale le permet, tandis qu’un dropdown pour les noms de plate-forme ne devrait être qu’une longueur qui permet la plus longue entrée.

#### <a name="helper-text"></a>Texte d’aide

- Un dialogue peut afficher du texte d’aide qui fournit plus d’informations sur le but du dialogue. Cela se trouve généralement en haut et peut être de 1-2 phrases.

- La longueur de la ligne doit être une largeur confortable pour un utilisateur à analyser et à lire. Un dialogue moyen ne doit pas dépasser 550 pixels de large.

#### <a name="interior-command-buttons"></a><a name="BKMK_InteriorCommandButtons"></a>Boutons de commande intérieurs
 Dans les dialogues plus complexes, un contrôle interne peut avoir ses propres boutons connexes, ce qui pourrait affecter l’endroit où les boutons de validation du dialogue sont situés.

- Utilisez un alignement vertical (colonne) des boutons intérieurs lorsque **OK**/**Cancel** sont orientés horizontalement dans le coin inférieur droit.

- Utilisez un alignement horizontal (ligne) de boutons intérieurs lorsque **OK**/**Cancel** sont orientés verticalement dans le coin supérieur droit. Cette situation est moins courante.

- La taille intérieure du bouton doit cibler la taille standard du bouton de 75x23 pixels, correspondant à la taille des boutons **OK**/**Cancel** lorsque c’est possible. Si une étiquette de bouton fait dépasser la taille standard du bouton, les autres boutons de cet ensemble doivent s’aligner sur cette taille plus large.

  ![Boutons OK et Annuler horizontaux](../../extensibility/ux-guidelines/media/0801-f_horizokcan.png "0801-f_HorizOKCan")

  **Figure 08.01-f: Boutons intérieurs verticaux avec OK horizontal/Annuler**

  ![Boutons OK et Annuler verticaux](../../extensibility/ux-guidelines/media/0801-g_vertokcan.png "0801-g_VertOKCan")

  **Figure 08.01-g : Boutons intérieurs horizontaux avec OK/Annuler vertical**

#### <a name="browse-button"></a>[Parcourir...] Bouton
 **[Parcourir...]** boutons qui suivent une boîte de texte doit épeler "Browse ..." dans son intégralité, y compris l’ellipsis. Si l’espace est serré ou s’il y a plusieurs boutons **[Browse...]** sur l’écran, le bouton peut être réduit à seulement l’ellipsis.

## <a name="themed-dialog-layout"></a><a name="BKMK_ThemedDialogLayout"></a>Mise en page de dialogue thématique
 Les dialogues thématiques de Visual Studio ont une apparence plus légère et offrent plus d’espace blanc. La typographie offre plus d’emphase et d’intérêt, offrant un espacement plus ouvert et une variation de la taille et des poids des polices. Dans la mesure du possible, les barres de chrome et de titre ont été réduites ou supprimées. La disposition de ces dialogues devrait suivre ce modèle de base :

1. Le fond du dialogue est blanc.

2. Il y a une bordure de règle d’un pixel dans un gris de valeur moyenne.

3. Le titre de dialogue ne se trouve plus dans une barre de titre, mais fournit un intérêt visuel et l’accent dans une plus grande taille de point. (Voir la section de taille de police dans [le style texte](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).)

4. Les étiquettes couplées avec du texte supplémentaire, comme une description, devraient être **police de l’environnement - Bold**.

5. Les colonnes intérieures sont séparées par une règle d’un pixel en gris clair.

6. Les liens par défaut n’ont pas de soulignement. Les états de vol stationnaire et pressés ont un changement de couleur plus souligner.

7. Commit boutons (comme **OK**/**Cancel**) s’asseoir dans le coin inférieur droit.

### <a name="themed-dialog-layout-examples"></a>Exemples de mise en page de dialogue thématique
 ![Disposition de boîte de dialogue à thème](../../extensibility/ux-guidelines/media/0801-h_themeddialog.png "0801-h_ThemedDialog")

 **Figure 08.01-h : Dialogue thématique**

 ![Dimensions de boîte de dialogue à thème](../../extensibility/ux-guidelines/media/0801-i_themeddialogdimensions.png "0801-i_ThemedDialogDimensions")

 **Figure 08.01-i: Dialogue thématique - Dimensions**

 ![Polices de boîte de dialogue à thème](../../extensibility/ux-guidelines/media/0801-j_themeddialogfonts.png "0801-j_ThemedDialogFonts")

 **Figure 08.01-j: Dialogue thématique - Fonts**

 ![Couleurs de boîte de dialogue à thème](../../extensibility/ux-guidelines/media/0801-k_themeddialogcolors.png "0801-k_ThemedDialogColors")

 **Figure 08.01-k: dialogue thématique - Couleurs**

## <a name="see-also"></a>Voir aussi
- [Modèles d’application pour Visual Studio](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)
- [Contrôles (Windows)](/windows/desktop/uxguide/controls)
- [Boîtes de dialogue (Windows)](/windows/desktop/uxguide/win-dialog-box)
