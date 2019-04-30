---
title: Mise en page pour Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c19e3022-047c-43b6-a046-a82717efed4f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e35cb321772354de29b7b8466b6136c96cabf98d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62798507"
---
# <a name="layout-for-visual-studio"></a>Mise en page pour Visual Studio
La majorité des boîtes de dialogue Visual Studio sont [mise en page de la boîte de dialogue utilitaire](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_UtilityDialogLayout), qui sont l’unthemed boîtes de dialogue de cette norme suivi [principes de mise en page de boîte de dialogue Windows Desktop](/windows/desktop/uxguide/win-dialog-box). Lorsque Visual Studio s’à actualiser son interface utilisateur, certaines des boîtes de dialogue plus apparents ont une nouvelle conception qui établit les expériences comme définition de produit. Ces [mise en page de boîte de dialogue à thème](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_ThemedDialogLayout) ont une apparence à thème.

## <a name="BKMK_UtilityDialogLayout"></a> Mise en page de boîte de dialogue utilitaire

- Tous les contrôles dans une boîte de dialogue Utilitaire doivent commencer en haut/gauche et vers le bas de flux.

- Centre jamais des contrôles dans une boîte de dialogue pour remplir une zone importante.

- Utiliser la police d’environnement pour tout texte de la boîte de dialogue. Lorsque vous écrivez une spécification visual, spécifiez la police d’environnement au lieu de sélectionner une police particulière et la taille. Consultez [la police d’environnement](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).

- Utiliser l’espacement du contrôle cohérent et le positionnement pour prendre en charge l’objectif de qualité dans savoir-faire.

- Boîtes de dialogue peuvent devenir plus complexes à partir d’un plus grand nombre de contrôles, une unique juxtaposition des contrôles ou les deux. Pour ces situations complexes, permettre suffisamment d’espace entre les regroupements de contrôle à un flux logique d’analyse de l’utilisateur.

### <a name="utility-dialog-layout-examples"></a>Exemples de mise en page de boîte de dialogue utilitaire
 Toutes les dimensions sont exprimées en pixels.

 ![Espacement de boîte de dialogue pour les étiquettes au-dessus des contrôles](../../extensibility/ux-guidelines/media/0801-a_utilityspacingabove.png "0801-a_UtilitySpacingAbove")

 **Figure 08.01-a : Instructions de l’espacement des boîtes de dialogue utilitaire avec les étiquettes au-dessus des contrôles**

 ![Espacement de boîte de dialogue pour les étiquettes à gauche des contrôles](../../extensibility/ux-guidelines/media/0801-b_utilityspacingleft.png "0801-b_UtilitySpacingLeft")

 **Figure 08.01-b : Instructions de l’espacement des boîtes de dialogue utilitaire avec des étiquettes à gauche des contrôles**

### <a name="layout-details"></a>Détails de la mise en page

#### <a name="margins"></a>Marges

- Toutes les boîtes de dialogue doivent avoir une bordure de 12 pixels autour de tous les bords.

- Marges dans un cadre de groupe doivent être 9 pixels du bord de l’image.

- Marges dans un contrôle onglet doivent être 6 pixels du bord du contrôle onglet.

#### <a name="command-buttons"></a>Boutons de commande

- Boutons de commande fonctionnent sur le frame de boîte de dialogue, pas sur le contenu. Ils doivent être placés dans la partie inférieure droite et doivent avoir suffisamment d’espace variable ci-dessus pour définir les boutons distinctes.

- S’il existe des boutons horizontaux qui opèrent au sein de la boîte de dialogue, la configuration de bouton de commande alternatif est une pile verticale en haut à droite. Consultez [des boutons de commande intérieurs](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_InteriorCommandButtons) ci-dessous.

- L’espace à gauche des boutons de commande (gauche/centre en bas de la boîte de dialogue) est considéré comme partie de la « bande » des contrôles d’opération de boîte de dialogue. La seule chose qui doit empiéter sur cet espace est un lien d’aide correspondant à la tâche globale ou de la boîte de dialogue.

- Boutons de commande doit être x 23 75 pixels.

- Boutons de commande doit être 6 pixels uns des autres.

  ![Alignement des boutons de base](../../extensibility/ux-guidelines/media/0801-c_buttonalign.png "0801-c_ButtonAlign")

  **Figure 08.01-c : Alignement des boutons de base**

#### <a name="labels"></a>Étiquettes

- Aligner à gauche toutes les étiquettes.

- Pour les étiquettes qui se trouvent au-dessus d’un contrôle, ils doivent aligner à gauche précisément avec le contrôle en dessous et le bas de l’étiquette doit être de 5 pixels au-dessus du haut de l’autre contrôle (par exemple, une zone de liste déroulante).

- Pour les étiquettes qui se trouvent à gauche des contrôles, la largeur minimale entre l’étiquette et le contrôle d’entrée est de 10 pixels. Une deuxième colonne implicite doit être établie pour aligner les zones de texte, zones de liste déroulante ou d’autres contrôles.

- Étiquettes adoptent une majuscule et sont suivies par un signe deux-points. Consultez [style de texte](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).

#### <a name="distance-between-controls"></a>Distance entre les contrôles
 Contrôles de pile raisonnablement. Il n’existe aucune règle absolue pour l’espacement entre les contrôles empilées. La précision entre les contrôles peut-être varier légèrement entre les boîtes de dialogue. L’espacement recommandée est 20 pixels pour les paires de contrôle/étiquette verticale et 9 pixels pour les paires de contrôle/étiquettes horizontales. L’espacement du contrôle minimal pour les paires horizontales est 6 pixels.

 ![Recommandé de distance entre les contrôles](../../extensibility/ux-guidelines/media/0801-d_controldistance.png "0801-d_ControlDistance")

 **Figure 08.01-d : Recommandations pour la distance entre les contrôles**

#### <a name="control-indentation"></a>Mise en retrait du contrôle
 Lorsque les contrôles sont imbriqués, aligner les contrôles internes horizontalement avec le bord gauche du contrôle ci-dessus, généralement l’étiquette.

 ![Imbriqué alignement](../../extensibility/ux-guidelines/media/0801-e_controlalign.png "0801-e_ControlAlign")

 **Figure 08.01-e : Alignement des contrôles imbriqués**

#### <a name="control-width"></a>Largeur du contrôle
 La largeur d’une zone de texte ou d’autres contrôles similaires doit être pas plue de l’entrée moyenne pour le champ. La moyenne des mots anglais sont cinq caractères. Par exemple, une zone de texte qui requiert un nom de chemin d’accès long devrait être aussi longue que la disposition horizontale permet, tandis que d’une liste déroulante pour les noms de plateforme doivent uniquement avoir une longueur qui autorise l’entrée la plus longue.

#### <a name="helper-text"></a>Texte d’aide

- Une boîte de dialogue peut afficher le texte d’assistance qui fournit plus d’informations sur l’objectif de la boîte de dialogue. En règle générale, cela se trouve en haut et peut être des phrases de 1 à 2.

- La longueur de ligne doit être une largeur à l’aise pour un utilisateur à analyser et à lire. Une boîte de dialogue de taille moyenne doit être pas plus de 550 pixels de large.

#### <a name="BKMK_InteriorCommandButtons"></a> Boutons de commande intérieurs
 Dans les boîtes de dialogue plus complexes, un contrôle interne peut avoir ses propres boutons associés, qui peuvent affecter l’emplacement où se trouvent les boutons de validation de la boîte de dialogue.

- Utilisez un alignement vertical (colonne) de l’intérieur boutons lorsque **OK**/**Annuler** est orienté horizontalement dans le coin inférieur droit.

- Utilisez un alignement horizontal (ligne) de l’intérieur boutons lorsque **OK**/**Annuler** est orienté verticalement dans le coin supérieur droit. Cette situation est moins courante.

- Taille du bouton intérieurs doit cibler la taille des boutons standard de 75 x 23 pixels, correspondant à la taille de **OK**/**Annuler** boutons lorsque cela est possible. Si une étiquette de bouton rend le bouton de dépassement de la taille de bouton standard, les autres boutons dans cet ensemble doivent s’aligner avec cette taille plus large.

  ![Boutons horizontaux OK et annuler](../../extensibility/ux-guidelines/media/0801-f_horizokcan.png "0801-f_HorizOKCan")

  **Figure 08.01-f: Boutons intérieurs verticales avec horizontal OK/Annuler**

  ![Boutons verticale OK et annuler](../../extensibility/ux-guidelines/media/0801-g_vertokcan.png "0801-g_VertOKCan")

  **Figure 08.01-g : Boutons intérieurs horizontales avec OK/Annuler verticaux**

#### <a name="browse-button"></a>[Parcourir...] bouton
 **[Parcourir...]**  boutons qui suivent une zone de texte énoncez à « Parcourir... » dans sa totalité, y compris les points de suspension. Si l’espace est étroit ou il existe plusieurs **[Parcourir...]**  boutons à l’écran, le bouton peut être réduit à simplement les points de suspension.

## <a name="BKMK_ThemedDialogLayout"></a> Mise en page de boîte de dialogue à thème
 Boîtes de dialogue à thème dans Visual Studio ont une apparence plus claire et offrent davantage d’espace blanc. Typographie fournit plus l’accent et centres d’intérêt, offrant plus ouvert interligne et une variante de tailles de police et les poids. Si possible, les barres de titre et de chrome ont été réduites ou supprimés. La disposition de ces boîtes de dialogue doit suivre ce modèle de base :

1. L’arrière-plan de la boîte de dialogue est blanc.

2. Il existe une bordure de la règle de 1 pixel dans un gris moyen de valeur.

3. Le titre de la boîte de dialogue n’est plus se trouve dans une barre de titre, mais fournit un intérêt visuel et une accentuation dans une taille supérieure. (Consultez la section de taille de police dans [style de texte](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).)

4. Les étiquettes couplés avec un texte supplémentaire, telle qu’une description, doivent être **police d’environnement + gras**.

5. Intérieurs colonnes sont séparées par une règle de 1 pixel en gris clair.

6. Liens par défaut n’ont aucun trait de soulignement. États survol et enfoncés ont un changement de couleur suivi d’un trait de soulignement.

7. Valider des boutons (comme **OK**/**Annuler**) se trouvent dans le coin inférieur droit.

### <a name="themed-dialog-layout-examples"></a>Exemples de mise en page de boîte de dialogue à thème
 ![Mise en page de boîte de dialogue à thème](../../extensibility/ux-guidelines/media/0801-h_themeddialog.png "0801-h_ThemedDialog")

 **Figure 08.01-h : Boîte de dialogue à thème**

 ![Dimensions de la boîte de dialogue à thème](../../extensibility/ux-guidelines/media/0801-i_themeddialogdimensions.png "0801-i_ThemedDialogDimensions")

 **Figure 08.01-i : Boîte de dialogue à thème - Dimensions**

 ![Polices de boîte de dialogue à thème](../../extensibility/ux-guidelines/media/0801-j_themeddialogfonts.png "0801-j_ThemedDialogFonts")

 **Figure 08.01-j : Boîte de dialogue à thème - polices**

 ![Couleurs de la boîte de dialogue à thème](../../extensibility/ux-guidelines/media/0801-k_themeddialogcolors.png "0801-k_ThemedDialogColors")

 **Figure 08.01-k : Boîte de dialogue à thème - couleurs**

## <a name="see-also"></a>Voir aussi
- [Modèles d’application pour Visual Studio](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)
- [Contrôles (Windows)](/windows/desktop/uxguide/controls)
- [Boîtes de dialogue (Windows)](/windows/desktop/uxguide/win-dialog-box)