---
title: Disposition pour Visual Studio | Microsoft Docs
description: En savoir plus sur la disposition des boîtes de dialogue Visual Studio, y compris les boîtes de dialogue sans thème et les nouvelles boîtes de dialogue qui présentent un aspect à thème.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: c19e3022-047c-43b6-a046-a82717efed4f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e52b7b3fd620080b73e8d3de80672003ecb8fcf7
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900524"
---
# <a name="layout-for-visual-studio"></a>Présentation pour Visual Studio
La plupart des boîtes de dialogue Visual Studio sont [en mode de boîte de dialogue utilitaire](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_UtilityDialogLayout), qui sont les boîtes de dialogue qui suivent les principes de présentation standard de la [boîte de dialogue Windows Desktop](/windows/desktop/uxguide/win-dialog-box). À mesure que Visual Studio se déplace pour actualiser son interface utilisateur, certaines des boîtes de dialogue plus importantes ont une nouvelle conception qui les établit en tant qu’expériences de définition de produit. La [disposition](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_ThemedDialogLayout) de ces boîtes de dialogue à thème a un aspect à thème.

## <a name="utility-dialog-layout"></a><a name="BKMK_UtilityDialogLayout"></a> Disposition de la boîte de dialogue utilitaire

- Tous les contrôles d’une boîte de dialogue utilitaire doivent démarrer en haut/à gauche et circuler vers le bas.

- Ne jamais centrer les contrôles sur une boîte de dialogue pour remplir une grande zone.

- Utilisez la police d’environnement pour tout le texte de la boîte de dialogue. Lors de l’écriture d’une spécification visuelle, spécifiez la police d’environnement au lieu de sélectionner une police et une taille particulières. Consultez [la police de l’environnement](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TheEnvironmentFont).

- Utilisez un espace et un emplacement de contrôle cohérents pour soutenir l’objectif de la qualité de l’artisan.

- Les boîtes de dialogue peuvent devenir plus complexes à partir d’un plus grand nombre de contrôles, d’un juxtaposition unique de contrôles, ou des deux. Pour ces situations complexes, prévoyez un espace suffisant entre les regroupements de contrôle pour permettre à l’utilisateur d’effectuer un traitement logique à analyser.

### <a name="utility-dialog-layout-examples"></a>Exemples de mise en page de la boîte de dialogue utilitaire
 Toutes les dimensions sont exprimées en pixels.

 ![Espacement de boîte de dialogue pour les étiquettes au-dessus des contrôles](../../extensibility/ux-guidelines/media/0801-a_utilityspacingabove.png "0801-a_UtilitySpacingAbove")

 **Figure 08,01-a : instructions d’espacement pour les boîtes de dialogue d’utilitaire avec des étiquettes au-dessus des contrôles**

 ![Espacement de boîte de dialogue pour les étiquettes à gauche des contrôles](../../extensibility/ux-guidelines/media/0801-b_utilityspacingleft.png "0801-b_UtilitySpacingLeft")

 **Figure 08,01-b : instructions d’espacement pour les boîtes de dialogue d’utilitaire avec des étiquettes à gauche de contrôles**

### <a name="layout-details"></a>Détails de la disposition

#### <a name="margins"></a>Marges

- Toutes les boîtes de dialogue doivent avoir une bordure de 12 pixels autour de tous les bords.

- Les marges dans un cadre de groupe doivent être comprises entre 9 pixels et le bord du cadre.

- Les marges dans un contrôle Tab doivent être situées à 6 pixels du bord du contrôle Tab.

#### <a name="command-buttons"></a>Boutons de commande

- Les boutons de commande fonctionnent sur le cadre de la boîte de dialogue, et non sur le contenu. Ils doivent être placés en bas à droite et doivent disposer de suffisamment d’espace pour définir les boutons séparément.

- S’il existe des boutons horizontaux qui fonctionnent dans la boîte de dialogue, l’autre configuration du bouton de commande est une pile verticale en haut à droite. Consultez les [boutons de commande intérieurs](../../extensibility/ux-guidelines/layout-for-visual-studio.md#BKMK_InteriorCommandButtons) ci-dessous.

- L’espace à gauche des boutons de commande (en bas à gauche/au centre de la boîte de dialogue) est considéré comme faisant partie de la « bande » des contrôles d’opération de dialogue. La seule chose qui devrait être à l’abri de cet espace est un lien d’aide qui concerne la tâche ou la boîte de dialogue globale.

- Les boutons de commande doivent être 75x23 pixels.

- Les boutons de commande doivent être espacés de 6 pixels.

  ![Alignement des boutons de base](../../extensibility/ux-guidelines/media/0801-c_buttonalign.png "0801-c_ButtonAlign")

  **Figure 08,01-c : alignement du bouton de base**

#### <a name="labels"></a>Étiquettes

- Aligner à gauche toutes les étiquettes.

- Pour les étiquettes qui se trouvent au-dessus d’un contrôle, elles doivent s’aligner avec précision avec le contrôle situé au-dessous et le bas de l’étiquette doit être de 5 pixels au-dessus de l’autre contrôle (par exemple, une zone de liste modifiable).

- Pour les étiquettes qui se trouvent à gauche des contrôles, la largeur minimale entre l’étiquette et le contrôle d’entrée est de 10 pixels. Une deuxième colonne implicite doit être établie pour aligner les zones de texte, les zones de liste déroulante ou d’autres contrôles.

- Les étiquettes sont en majuscules et sont suivies d’un signe deux-points. Voir [style de texte](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).

#### <a name="distance-between-controls"></a>Distance entre les contrôles
 Contrôles de pile raisonnablement. Il n’existe pas d’indications absolues pour l’espacement entre les contrôles empilés. L’étanchéité entre les contrôles peut varier légèrement entre les boîtes de dialogue. L’espacement recommandé est de 20 pixels pour les paires contrôle/étiquette verticale, et de 9 pixels pour les paires contrôle/étiquette horizontales. L’espacement de contrôle minimal pour les paires horizontales est de 6 pixels.

 ![Distance recommandée entre les contrôles](../../extensibility/ux-guidelines/media/0801-d_controldistance.png "0801-d_ControlDistance")

 **Figure 08,01-d : recommandations relatives à la distance entre les contrôles**

#### <a name="control-indentation"></a>Contrôler la mise en retrait
 Lorsque les contrôles sont imbriqués, alignez les contrôles internes horizontalement avec le bord gauche du contrôle ci-dessus, généralement l’étiquette.

 ![Alignement des contrôles imbriqués](../../extensibility/ux-guidelines/media/0801-e_controlalign.png "0801-e_ControlAlign")

 **Figure 08,01-e : alignement du contrôle imbriqué**

#### <a name="control-width"></a>Largeur du contrôle
 La largeur d’une zone de texte ou d’autres contrôles similaires ne doit pas être supérieure à l’entrée moyenne du champ. Le mot anglais moyen est de cinq caractères. Par exemple, une zone de texte qui requiert un long nom de chemin d’accès doit être aussi longue que la disposition horizontale, tandis qu’une liste déroulante pour les noms de plateformes doit uniquement être une longueur qui autorise l’entrée la plus longue.

#### <a name="helper-text"></a>Texte d’assistance

- Une boîte de dialogue peut afficher du texte d’assistance qui fournit des informations supplémentaires sur l’objectif de la boîte de dialogue. Cela se situe généralement en haut et peut être de 1-2 phrases.

- La longueur de ligne doit être une largeur confortable pour l’analyse et la lecture d’un utilisateur. Une boîte de dialogue de taille moyenne ne doit pas dépasser 550 pixels de largeur.

#### <a name="interior-command-buttons"></a><a name="BKMK_InteriorCommandButtons"></a> Boutons de commande intérieurs
 Dans les boîtes de dialogue plus complexes, un contrôle interne peut avoir ses propres boutons associés, ce qui peut affecter l’emplacement des boutons de validation de la boîte de dialogue.

- Utilisez un alignement vertical (colonne) de boutons intérieurs lorsque l’opération **OK** / sur **Annuler** est orientée horizontalement dans le coin inférieur droit.

- Utilisez un alignement horizontal (ligne) de boutons intérieurs lorsque **OK** / **Annuler** est orienté verticalement dans le coin supérieur droit. Cette situation est moins courante.

- La taille du bouton intérieur doit viser la taille de bouton standard de 75x23 pixels, ce **qui correspond à la taille des** / boutons **Annuler** lorsque cela est possible. Si une étiquette de bouton fait passer le bouton au-delà de la taille de bouton standard, les autres boutons de cet ensemble doivent s’aligner sur cette taille plus grande.

  ![Boutons OK et Annuler horizontaux](../../extensibility/ux-guidelines/media/0801-f_horizokcan.png "0801-f_HorizOKCan")

  **Figure 08,01-f : boutons intérieurs verticaux avec horizontal OK/Annuler**

  ![Boutons OK et Annuler verticaux](../../extensibility/ux-guidelines/media/0801-g_vertokcan.png "0801-g_VertOKCan")

  **Figure 08,01-g : boutons intérieurs horizontaux avec vertical OK/Annuler**

#### <a name="browse-button"></a>[Parcourir...] bouton
 **[Parcourir...]** les boutons qui suivent une zone de texte doivent épeler « parcourir... » entièrement, y compris les points de suspension. Si l’espace est étroit ou s’il y a plusieurs boutons **[Parcourir...]** sur l’écran, le bouton peut être réduit uniquement aux points de suspension.

## <a name="themed-dialog-layout"></a><a name="BKMK_ThemedDialogLayout"></a> Disposition de la boîte de dialogue à thème
 Les boîtes de dialogue à thème dans Visual Studio ont une apparence plus claire et offrent davantage d’espace blanc. La typographie offre davantage d’importance et d’intérêt, offre davantage d’espacement ouvert et une variation des tailles et des poids des polices. Lorsque cela est possible, les barres de chrome et de titre ont été réduites ou supprimées. La disposition de ces boîtes de dialogue doit suivre ce modèle de base :

1. L’arrière-plan de la boîte de dialogue est blanc.

2. Il y a une bordure de règle de 1 pixel dans un gris de valeur moyenne.

3. Le titre de la boîte de dialogue ne se trouve plus dans une barre de titre, mais fournit un intérêt visuel et met l’accent sur une plus grande taille. (Consultez la section taille de police dans [style de texte](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md#BKMK_TextStyle).)

4. Les étiquettes associées à du texte supplémentaire, telles qu’une description, doivent être de type **police d’environnement + gras**.

5. Les colonnes intérieures sont séparées par une règle de 1 pixel en gris clair.

6. Les liens par défaut n’ont pas de trait de soulignement. Les États pointage et enfoncé ont une modification de couleur et un trait de soulignement.

7. Les boutons de validation (comme **OK** / **Annuler**) se trouvent dans le coin inférieur droit.

### <a name="themed-dialog-layout-examples"></a>Exemples de disposition de boîte de dialogue à thème
 ![Disposition de boîte de dialogue à thème](../../extensibility/ux-guidelines/media/0801-h_themeddialog.png "0801-h_ThemedDialog")

 **Figure 08,01-h : boîte de dialogue à thème**

 ![Dimensions de boîte de dialogue à thème](../../extensibility/ux-guidelines/media/0801-i_themeddialogdimensions.png "0801-i_ThemedDialogDimensions")

 **Figure 08,01-i : Dimensions de la boîte de dialogue à thème**

 ![Polices de boîte de dialogue à thème](../../extensibility/ux-guidelines/media/0801-j_themeddialogfonts.png "0801-j_ThemedDialogFonts")

 **Figure 08,01-j : boîte de dialogue à thème-polices**

 ![Couleurs de boîte de dialogue à thème](../../extensibility/ux-guidelines/media/0801-k_themeddialogcolors.png "0801-k_ThemedDialogColors")

 **Figure 08,01-k : boîte de dialogue à thème**

## <a name="see-also"></a>Voir aussi
- [Modèles d’application pour Visual Studio](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)
- [Contrôles (Windows)](/windows/desktop/uxguide/controls)
- [Boîtes de dialogue (Windows)](/windows/desktop/uxguide/win-dialog-box)
