---
title: Partagé des couleurs pour Visual Studio | Microsoft Docs
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: 8d11b9a0-6175-4f2e-8e7f-79daee1bfd41
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8b36b7c123f4da9ca3ab7a6f33a972345cdf70e6
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66310776"
---
# <a name="shared-colors-for-visual-studio"></a>Couleurs partagées pour Visual Studio
Lorsque vous concevez l’interface utilisateur qui utilise des éléments communs du shell Visual Studio, ou vous souhaitez que votre élément d’interface pour être cohérent avec des fonctionnalités similaires, vous pouvez utiliser des noms de jeton existants dans les fichiers de définition de package pour choisir et assigner des couleurs. Ainsi, votre interface utilisateur reste cohérente avec l’environnement Visual Studio global et elle se met à jour automatiquement quand des thèmes sont ajoutés ou mis à jour.

Cet article décrit les éléments d’interface utilisateur communs et les noms de jeton qu’ils utilisent, que vous pouvez référencer pour créer une interface utilisateur similaire. Pour plus d’informations sur la façon d’accéder à ces jetons de couleur, consultez [The VSColor Service](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService).

Assurez-vous d’utiliser correctement les noms de jeton :

- **Utiliser des noms de jeton basés sur la fonction, pas sur la couleur elle-même.** Les couleurs partagées communes sont associées à des éléments d’interface spécifiques et uniquement destinées à être utilisées pour des fonctionnalités identiques ou similaires. Par exemple, ne réutilisez pas la couleur d’une zone de liste modifiable enfoncée pour une animation de progression en rotation juste parce que vous aimez la couleur. Les fonctions de la zone de liste modifiable et l’animation sont différentes, et si la couleur associé avec les modifications de zone de liste modifiable, il peut ne plus être une couleur appropriée pour votre élément d’animation. Une utilisation cohérente des couleurs permet de guider vos utilisateurs et d’éviter toute confusion.

- **Utiliser des couleurs d’arrière-plan et de texte dans la combinaison correcte.** Les couleurs d’arrière-plan destinées à être utilisées avec du texte possèdent une couleur de texte associée. N’utilisez pas de couleurs de texte autres que celles spécifiées pour l’arrière-plan. S’il n’est pas une couleur de texte associée, n’utilisez pas cette couleur d’arrière-plan pour n’importe quelle surface sur laquelle vous vous attendez afficher le texte. Autres combinaisons de couleurs de texte et d’arrière-plan peuvent entraîner une interface illisible.

- **Utiliser les couleurs de contrôle qui sont appropriées à leur emplacement.** Dans certains États, certains contrôles Visual Studio n’ont une bordure distincte et couleurs d’arrière-plan. Au lieu de cela, ils sélectionnent ces couleurs dans les surfaces qui se trouvent derrière. Veillez à toujours utiliser les noms de jeton qui conviennent à l’emplacement où vous placez le contrôle.

> [!IMPORTANT]
> N’utilisez pas les jetons trouvés dans les catégories « Page d’accueil » ou « Cider ».

## <a name="common-shared-controls"></a>Contrôles partagés communs

Lorsque vous utilisez une barre de commandes de Visual Studio standard dans votre composant, vous aurez accès aux contrôles de l’interpréteur de commandes stylisés. Vous ne devez pas remodéliser ces contrôles communs. Toutefois, si vous avez besoin de créer une barre de commandes personnalisée, vous pouvez avoir besoin de générer des contrôles personnalisés également. Dans ce cas, assurez-vous d’utiliser des noms de jeton corrects pour chacun des contrôles suivants afin que votre interface utilisateur soit cohérente avec le reste de Visual Studio.

### <a name="button-controls"></a>Contrôles boutons

![Ligne rouge de contrôle de bouton](../../extensibility/ux-guidelines/media/0303-155_buttoncontrolredline.png "0303-155_ButtonControlRedline")

| Utilisez... | N’utilisez pas... |
| --- | --- |
| ... pour les boutons dans la zone de document que vous souhaitez intégrer avec les thèmes de Visual Studio (clair, foncé, bleu ou un système à contraste élevé). | ... pour les boutons affichés sur un arrière-plan personnalisé qui ne fait pas partie d’un thème de Visual Studio. |

**Bouton : état standard**

![Bouton standard](../../extensibility/ux-guidelines/media/03.03.Button.Standard.png "03.03.Button.Standard")<br />Bouton standard

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Bouton | `CommonControls.Button` |
| Bordure de bouton | `CommonControls.ButtonBorder` |

**Bouton : état par défaut**

![Bouton par défaut](../../extensibility/ux-guidelines/media/03.03.Button.Default.png "03.03.Button.Default")<br />Bouton par défaut

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Bouton | `CommonControls.ButtonDefault` |
| Bordure de bouton | `CommonControls.ButtonBorderDefault` |

**Bouton : état désactivé**

![Bouton désactivé](../../extensibility/ux-guidelines/media/03.03.Button.Disabled.png "03.03.Button.Disabled")<br />Bouton désactivé

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Bouton | `CommonControls.ButtonDisabled` |
| Bordure de bouton | `CommonControls.ButtonBorderDisabled` |

**Bouton : état de pointage**

![Bouton au pointage](../../extensibility/ux-guidelines/media/03.03.Button.hover.png "03.03.Button.hover")<br />Bouton au pointage

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Bouton | `CommonControls.ButtonHover` |
| Bordure de bouton | `CommonControls.ButtonBorderHover` |

**Bouton : état enfoncé**

![Bouton enfoncé](../../extensibility/ux-guidelines/media/03.03.Button.Pressed.png "03.03.Button.Pressed")<br />Bouton enfoncé

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Bouton | `CommonControls.ButtonPressed` |
| Bordure de bouton | `CommonControls.ButtonBorderPressed` |

**Bouton : état ayant le focus**

![Bouton actif](../../extensibility/ux-guidelines/media/03.03.Button.Focused.png "03.03.Button.Focused")<br />Bouton actif

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Bouton | `CommonControls.ButtonFocused` |
| Bordure de bouton | `CommonControls.ButtonBorderFocused` |

### <a name="check-box-controls"></a>Contrôles de case à cocher
![Case à cocher (ligne rouge)](../../extensibility/ux-guidelines/media/0303-161_checkboxredline.png "0303-161_CheckboxRedline")<br />Case à cocher (ligne rouge)

| Utilisez... | N’utilisez pas... |
| --- | --- |
| ... pour les contrôles de case à cocher contenues dans le document correctement. | ... pour toute interface utilisateur qui n’est pas un contrôle de case à cocher. |

**Case à cocher : état par défaut**

![Case à cocher](../../extensibility/ux-guidelines/media/0303-162_checkbox.png "0303-162_Checkbox")<br />Case à cocher par défaut

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `CommonControls.CheckBoxBackground` |
| Bordure | `CommonControls.CheckBoxBorder` |
| Texte | `CommonControls.CheckBoxText` |
| Glyphe | `CommonControls.CheckBoxGlyph` |

**Case à cocher : l’état désactivé**

![Case à cocher désactivée](../../extensibility/ux-guidelines/media/0303-163_checkboxdisabled.png "0303-163_CheckboxDisabled")<br />Case à cocher désactivée

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `CommonControls.CheckBoxBackgroundDisabled` |
| Bordure | `CommonControls.CheckBoxBorderDisabled` |
| Texte | `CommonControls.CheckBoxTextDisabled` |
| Glyphe | `CommonControls.CheckBoxGlyphDisabled` |

**Case à cocher : placez le curseur état**

 ![Case à cocher au pointage](../../extensibility/ux-guidelines/media/0303-164_checkboxhover.png "0303-164_CheckboxHover")<br />Case à cocher au pointage

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `CommonControls.CheckBoxBackgroundHover` |
| Bordure | `CommonControls.CheckBoxBorderHover` |
| Texte | `CommonControls.CheckBoxTextHover` |
| Glyphe | `CommonControls.CheckBoxGlyphHover` |

**Case à cocher : état enfoncé**

![Case à cocher appuyée](../../extensibility/ux-guidelines/media/0303-165_checkboxpressed.png "0303-165_CheckboxPressed")<br />Case à cocher appuyée

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `CommonControls.CheckBoxBackgroundPressed` |
| Bordure | `CommonControls.CheckBoxBorderPressed` |
| Texte | `CommonControls.CheckBoxTextPressed` |
| Glyphe | `CommonControls.CheckBoxGlyphPressed` |

**Case à cocher : état de focus**

![Case à cocher concentré](../../extensibility/ux-guidelines/media/0303-166_checkboxfocused.png "0303-166_CheckboxFocused")<br />Case à cocher ayant le focus

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `CommonControls.CheckBoxBackgroundFocused` |
| Bordure | `CommonControls.CheckBoxBorderFocused` |
| Texte | `CommonControls.CheckBoxTextFocused` |
| Glyphe | `CommonControls.CheckBoxGlyphFocused` |

### <a name="drop-downs-and-combo-boxes"></a>Listes déroulantes et liste déroulante zones
![Déroulante/zone (ligne rouge)](../../extensibility/ux-guidelines/media/0303-167_dropdowncomboboxredline.png "0303-167_DropDownComboBoxRedline")<br />Déroulante/zone (ligne rouge)

| Utilisez... | N’utilisez pas... |
| --- | --- |
| ... pour listes déroulantes et de la liste déroulante les zones dans le document correctement. | ... pour toute interface utilisateur qui n’est pas une zone de liste déroulante ou zone de liste déroulante. |
| | ... pour la barre de commandes [listes déroulantes](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandDropDown) ou [zones de liste déroulante](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandComboBox). |

**Listes déroulantes et liste déroulante boîtes : état par défaut**

![Par défaut, boîte déroulante/](../../extensibility/ux-guidelines/media/0303-168_dropdowncombobox.png "0303-168_DropDownComboBox")<br />Par défaut, boîte déroulante /

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `CommonControls.ComboBoxBackground` |
| Bordure | `CommonControls.ComboBoxBorder` |
| Texte | `CommonControls.ComboBoxText` |
| Séparateur | `CommonControls.ComboBoxSeparator` |
| Glyphe | `CommonControls.ComboBoxGlyph` |
| Arrière-plan de glyphe | `CommonControls.ComboBoxGlyphBackground` |

**Listes déroulantes et liste déroulante zones : l’état désactivé**

![Désactivée déroulante/zone](../../extensibility/ux-guidelines/media/0303-169_dropdowncomboboxdisabled.png "0303-169_DropDownComboBoxDisabled")<br />Désactivée déroulante/zone

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `CommonControls.ComboBoxBackgroundDisabled` |
| Bordure | `CommonControls.ComboBoxBorderDisabled` |
| Texte | `CommonControls.ComboBoxTextDisabled` |
| Séparateur | `CommonControls.ComboBoxSeparatorDisabled` |
| Glyphe | `CommonControls.ComboBoxGlyphDisabled` |
| Arrière-plan de glyphe | `CommonControls.ComboBoxGlyphBackgroundDisabled` |

**Listes déroulantes et liste déroulante boîtes : placez le curseur état**

![Zone déroulante/pointage](../../extensibility/ux-guidelines/media/0303-170_dropdowncomboboxhover.png "0303-170_DropDownComboBoxHover")<br />Zone de liste déroulante/liste déroulante au pointage

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `CommonControls.ComboBoxBackgroundHover` |
| Bordure | `CommonControls.ComboBoxBorderHover` |
| Texte | `CommonControls.ComboBoxTextHover` |
| Séparateur | `CommonControls.ComboBoxSeparatorHover` |
| Glyphe | `CommonControls.ComboBoxGlyphHover` |
| Arrière-plan de glyphe | `CommonControls.ComboBoxGlyphBackgroundHover` |

**Listes déroulantes et liste déroulante boîtes : état enfoncé**

![Enfoncé déroulante/zone](../../extensibility/ux-guidelines/media/0303-171_dropdowncomboboxpressed.png "0303-171_DropDownComboBoxPressed")<br />Appuyé déroulante/zone

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `CommonControls.ComboBoxBackgroundPressed` |
| Bordure | `CommonControls.ComboBoxBorderPressed` |
| Texte | `CommonControls.ComboBoxTextPressed` |
| Séparateur | `CommonControls.ComboBoxSeparatorPressed` |
| Glyphe | `CommonControls.ComboBoxGlyphPressed` |
| Arrière-plan de glyphe | `CommonControls.ComboBoxGlyphBackgroundPressed` |

**Affichage des éléments de liste de zones de listes déroulantes et liste déroulante : état enfoncé**

 ![Affichage des éléments de liste d’appuyée de zone de déroulante/](../../extensibility/ux-guidelines/media/0303-174_dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")<br />Zone déroulante/activé l’affichage des éléments de liste

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `CommonControls.ComboBoxListBackground`<br />`CommonControls.ComboBoxListBackgroundHover`<br />`CommonControls.ComboBoxListItemBackgroundPressed`<br />`CommonControls.ComboBoxListItemBackgroundFocused` |
| Bordure | `CommonControls.ComboBoxListBorder`<br />`CommonControls.ComboBoxListBorderHover`<br />`CommonControls.ComboBoxListBorderPressed`<br />`CommonControls.ComboBoxListBorderFocused` |
| Texte d’élément | `CommonControls.ComboBoxListItemText`<br /> `CommonControls.ComboBoxListItemTextHover`<br />`CommonControls.ComboBoxListItemTextPressed`<br />`CommonControls.ComboBoxListItemTextFocused` |
| Ombre d’arrière-plan | `CommonControls.ComboBoxListBackgroundShadow` |

**Listes déroulantes et liste déroulante boîtes : concentré état**

![Zone déroulante/avec focus](../../extensibility/ux-guidelines/media/0303-172_dropdowncomboboxfocused.png "0303-172_DropDownComboBoxFocused")<br />Zone déroulante/avec focus

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `CommonControls.ComboBoxBackgroundFocused` |
| Bordure | `CommonControls.ComboBoxBorderFocused` |
| Texte | `CommonControls.ComboBoxTextFocused` |
| Séparateur | `CommonControls.ComboBoxSeparatorFocused` |
| Glyphe | `CommonControls.ComboBoxGlyphFocused` |
| Arrière-plan de glyphe | `CommonControls.ComboBoxGlyphBackgroundFocused` |

**Listes déroulantes et liste déroulante boîtes : sélection de saisie de texte**

![Sélection de saisie de texte de déroulante/zone](../../extensibility/ux-guidelines/media/0303-173_dropdowncomboboxtextinput.png "0303-173_DropDownComboBoxTextInput")<br />Sélection d’entrée de texte déroulante/zone

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Surligner | `CommonControls.ComboBoxTextInputSelection` |

### <a name="tabular-data-grid-controls"></a>Contrôles de données tabulaires (grille)
Les contrôles de données tabulaires, également appelés contrôles de grille, sont des contrôles communs pour Visual Studio qui peuvent être utilisés pour présenter des grandes quantités de données dans plusieurs colonnes. Les contrôles de données tabulaires standard se trouvent à plusieurs endroits dans Visual Studio : la fenêtre Outil Liste d’erreurs, les rapports IntelliTrace et l’affichage du tas de mémoire, entre autres. Utilisez toujours les contrôles de données tabulaires standard fournis. Dans de rares cas, vous pouvez ne pas avoir accès aux contrôles de données tabulaires standard. Si tel est le cas, utilisez les noms de jeton suivants pour veiller à ce que votre interface utilisateur soit cohérente avec les autres contrôles de données tabulaires dans Visual Studio.

![Contrôle de grille de données tabulaire / (ligne rouge)](../../extensibility/ux-guidelines/media/0303-197_tabulardatagridcontrolredline.png "0303-197_TabularDataGridControlRedline")<br />Contrôle de grille de données tabulaire / (ligne rouge)

| Utilisez... | N’utilisez pas... |
| --- | --- |
| ... pour tabulaire ou contrôles de grille. | ... pour toute interface utilisateur qui n’est pas un contrôle tabulaire ou de grille. |

#### <a name="column-headers"></a>En-têtes de colonnes
Les en-têtes de colonnes comprennent un arrière-plan, une bordure, le texte du titre et un éventuel glyphe généralement utilisé pour trier une grille selon cette colonne.

**En-tête de colonne : état par défaut**

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `Header.Default` |
| Premier plan (texte) | `Environment.CommandBarTextActive` |
| Premier plan (glyphe) | `Header.Glyph` |
| Bordure | `Header.SeparatorLine` |

**En-tête de colonne : placez le curseur état**

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `Header.MouseOver` |
| Premier plan (texte) | `Environment.CommandBarTextHover` |
| Premier plan (glyphe) | `Header.MouseOverGlyph` |
| Bordure | `Header.SeparatorLine` |

**En-tête de colonne : état enfoncé**

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `CommonControls.CheckBoxBackgroundPressed` |
| Premier plan (texte) | `CommonControls.CheckBoxBorderPressed` |
| Premier plan (glyphe) | `CommonControls.CheckBoxTextPressed` |
| Bordure | `CommonControls.CheckBoxGlyphPressed` |

#### <a name="list-view-items"></a>Éléments de la vue Liste
 Les éléments de la vue Liste comprennent un arrière-plan et le contenu. Le contenu peut être du texte, une icône ou les deux.

**Afficher les éléments de liste : état par défaut**

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | Transparent |
| Premier plan (texte) | `Environment.CommandBarTextActive` |
| Bordure | None |

**Afficher les éléments de liste : état actif**

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `TreeView.SelectedItemActive` |
| Premier plan (texte) | `TreeView.SelectedItemActiveText` |
| Bordure | None |

**Afficher les éléments de liste : état inactif**

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `TreeView.SelectedItemInactive` |
| Premier plan (texte) | `TreeView.SelectedItemInactiveText` |
| Bordure | None |

### <a name="ui-text"></a>Texte de l’interface utilisateur

#### <a name="instructional-text"></a>Texte d’instructions
Texte d’instructions fournit une importante principale des explications sur quoi faire dans une page de boîte de dialogue ou document.

![Par défaut du texte d’instructions](../../extensibility/ux-guidelines/media/0303_InstructionalText.png "0303_InstructionalText.png")<br />Texte d’instructions par défaut

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Premier plan (texte) | `Environment.ControlText` |

#### <a name="secondary-instructional-text"></a>Texte d’instructions secondaire
Dans les pages de document avec un grand nombre de contrôles et texte, du texte démonstration utilise une valeur de couleur différente. Cela permet de transmettre les informations qui sont plus importantes et de réduire la densité des éléments d’interface utilisateur globale. (Voir aussi la section sur le texte d’indication ci-dessous.)

![Texte d’instructions secondaire](../../extensibility/ux-guidelines/media/0303_SecondaryInstructionalText.png "0303_SecondaryInstructionalText.png")<br />Texte d’instructions secondaire

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Premier plan (texte) | `Environment.ControlEditHintText` |

#### <a name="hint-text"></a>Texte d’indication
Texte d’information s’affiche dans un contrôle vide, en dessous d’un contrôle, ou sur une surface de document vide permettant à l’utilisateur ce qu’il faut faire ensuite. Vous pouvez utiliser le texte d’indication avec un arrière-plan de fenêtre ou contrôle.

**Texte d’indication de valeur par défaut**

![Par défaut du texte d’indication](../../extensibility/ux-guidelines/media/0303_HintText.png "0303_HintText.png")<br />Texte d’indication de valeur par défaut

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Premier plan (texte) | `Environment.ControlEditHintText` |

**Texte d’indication requise**

![Required hint text](../../extensibility/ux-guidelines/media/0303_RequiredHintText.png "0303_RequiredHintText.png")<br />Texte d’indication requise

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Premier plan (texte) | `Environment.ControlRequiredHintText` |
| Présentation | `Environment.ControlRequiredBackground` |

**Texte de contrôle de zone de recherche**

> Consultez [zones de recherche](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_SearchBoxes) pour les autres jetons de couleur associées au contrôle de recherche.

![Rechercher le texte de contrôle de zone](../../extensibility/ux-guidelines/media/0303_SearchBoxControl.png "0303_SearchBoxControl.png")<br />Texte de contrôle de zone de recherche

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Premier plan (texte) | `SearchControl.UnfocusedWatermarkText` |

### <a name="hyperlink"></a>Lien hypertexte
Le lien hypertexte est un contrôle qui n’a pas une paire de premier plan/arrière-plan. Dans tous les cas, utilisez la couleur de lien hypertexte de premier plan, qui s’affiche correctement sur les arrière-plans foncés, gris et blancs. Si vous n’utilisez pas le jeton de couleur pour le contrôle de lien hypertexte, vous verrez la couleur système par défaut pour « activé », laquelle clignote en rouge. C’est le signal que le contrôle n’utilise pas le jeton de couleur d’environnement approprié.

![Lien hypertexte (ligne rouge)](../../extensibility/ux-guidelines/media/0303-133_hyperlinkredline.png "0303-133_HyperlinkRedline")<br />Lien hypertexte (ligne rouge)

| Utilisez... | N’utilisez pas... |
| --- | --- |
| ... lorsque vous créez un lien hypertexte personnalisé. | ... pour tout élément qui n’est pas un lien hypertexte. |

**Lien hypertexte : état par défaut**

![Lien hypertexte par défaut](../../extensibility/ux-guidelines/media/0303-134_hyperlink.png "0303-134_Hyperlink")<br />Lien hypertexte par défaut

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Premier plan (texte) | `Environment.PanelHyperlink` |

**Lien hypertexte : état de survol**

![Lien hypertexte au pointage](../../extensibility/ux-guidelines/media/0303-135_hyperlinkhover.png "0303-135_HyperlinkHover")<br />Lien hypertexte au pointage

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Premier plan (texte) | `Environment.PanelHyperlinkHover` |

**Lien hypertexte : un état enfoncé**

![Lien hypertexte enfoncé](../../extensibility/ux-guidelines/media/0303-136_hyperlinkpressed.png "0303-136_HyperlinkPressed")<br />Lien hypertexte enfoncé

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Premier plan (texte) | `Environment.PanelHyperlinkPressed` |

**Lien hypertexte : état désactivé**

![Lien hypertexte désactivé](../../extensibility/ux-guidelines/media/0303-137_hyperlinkdisabled.png "0303-137_HyperlinkDisabled")<br />Lien hypertexte désactivé

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Premier plan (texte) | `Environment.PanelHyperlinkDisabled` |

### <a name="infobars"></a>Infobars
Les barres d’informations sont utilisées pour fournir plus d’informations sur un contexte donné et apparaissent toujours en haut d’une fenêtre de document ou d’outil.

![Barre d’informations (ligne rouge)](../../extensibility/ux-guidelines/media/0303-138_infobarredline.png "0303-138_InfobarRedline")<br />Barre d’informations (ligne rouge)

| Utilisez... | N’utilisez pas... |
| --- | --- |
| ... lors de la création de barres d’informations personnalisées. | ... pour les éléments d’interface utilisateur qui ne sont pas similaire à une barre d’informations. |

**La barre d’informations : état par défaut**

![Valeur par défaut de la barre d’informations](../../extensibility/ux-guidelines/media/0303-139_infobar.png "0303-139_Infobar")<br />Barre d’informations par défaut

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `InfoBar.InfoBarBackground` |
| Premier plan (texte) | `InfoBar.InfoBar` |
| Bordure | `InfoBar.InfoBarBorder` |

**Fermeture de la barre d’informations (&times;) bouton : état par défaut**

![Par défaut de barre d’informations Close (&times;) bouton](../../extensibility/ux-guidelines/media/0303_InfobarCloseDefault.png "0303_InfobarCloseDefault.png")<br />Par défaut de barre d’informations fermer (&times;) bouton

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `InfoBar.CloseButton` |
| Bordure | `InfoBar.CloseButtonBorder` |
| Glyphe | `InfoBar.CloseButtonGlyph` |

**Fermeture de la barre d’informations (&times;) bouton : placez le curseur état**

![Fermeture de la barre d’informations (&times;) bouton au pointage](../../extensibility/ux-guidelines/media/0303_InfobarCloseHover.png "0303_InfobarCloseHover.png")<br />Fermeture de la barre d’informations (&times;) bouton au pointage

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `InfoBar.CloseButtonHover` |
| Bordure | `InfoBar.CloseButtonHoverBorder` |
| Glyphe | `InfoBar.CloseButtonHoverGlyph` |

**Fermeture de la barre d’informations (&times;) bouton : état enfoncé**

![Utilisateur appuie sur la barre d’informations fermer (&times;) bouton](../../extensibility/ux-guidelines/media/0303_InfobarClosePressed.png "0303_InfobarClosePressed.png")<br />Utilisateur appuie sur la barre d’informations fermer (&times;) bouton

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `InfoBar.CloseButtonDown` |
| Bordure | `InfoBar.CloseButtonDownBorder` |
| Glyphe | `InfoBar.CloseButtonDownGlyph` |

**Bouton de lien hypertexte de barre d’informations : état par défaut**

![Bouton de lien hypertexte de barre d’informations par défaut](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonDefault.png "0303_InfobarHyperlinkButtonDefault.png")<br />Bouton de lien hypertexte de barre d’informations par défaut

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Premier plan (texte) | `InfoBar.Hyperlink` |

**Bouton de lien hypertexte de barre d’informations : placez le curseur état**

![Bouton de lien hypertexte de barre d’informations sur pointage](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonHover.png "0303_InfobarHyperlinkButtonHover.png")<br />Bouton de lien hypertexte de barre d’informations sur pointage

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Premier plan (texte) | `Infobar.HyperlinkMouseOver`<br />(Avec un trait de soulignement) |

**Bouton de lien hypertexte de barre d’informations : état enfoncé**

![Bouton de lien hypertexte de barre d’informations appuyé](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonPressed.png "0303_InfobarHyperlinkButtonPressed.png")<br />Bouton de lien hypertexte enfoncé barre d’informations

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Premier plan (texte) | `Infobar.HyperlinkMouseDown`<br />(Avec un trait de soulignement) |

**Barre d’informations inline hyperlink (au sein d’une phrase) : état par défaut**

![Bouton de lien hypertexte de barre d’informations par défaut inline](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonDefault.png "0303_InfobarHyperlinkButtonDefault.png")<br />Bouton de lien hypertexte par défaut inline barre d’informations

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Premier plan (texte) | `InfoBar.Hyperlink` |

**Barre d’informations inline hyperlink (au sein d’une phrase) : placez le curseur état**

![Bouton de lien hypertexte inline de barre d’informations au pointage](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkInlineHover.png "0303_InfobarHyperlinkInlineHover.png")<br />Bouton de lien hypertexte inline de barre d’informations au pointage

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Premier plan (texte) | `Infobar.HyperlinkMouseOver`<br />(Avec un trait de soulignement) |

**Barre d’informations inline hyperlink (au sein d’une phrase) : état enfoncé**

![Bouton de lien hypertexte enfoncé barre d’informations inline](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkInlinePressed.png "0303_InfobarHyperlinkInlinePressed.png")<br />Bouton de barre d’informations inline hyperlink enfoncé

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Premier plan (texte) | `Infobar.HyperlinkMouseDown`<br />(Avec un trait de soulignement) |

**Bouton de barre d’informations : état par défaut**

![Bouton de barre d’informations par défaut](../../extensibility/ux-guidelines/media/0303_InfobarButtonDefault.png "0303_InfobarButtonDefault.png")<br />Bouton de barre d’informations par défaut

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `InfoBar.Button` |
| Premier plan (texte) | `InfoBar.Button` |
| Bordure | `InfoBar.ButtonBorder` |

**Bouton de barre d’informations : placez le curseur état**

![Bouton de barre d’informations sur le pointage](../../extensibility/ux-guidelines/media/0303_InfobarButtonHover.png "0303_InfobarButtonHover.png")<br />Bouton de barre d’informations sur pointage

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `InfoBar.ButtonMouseOver` |
| Premier plan (texte) | `InfoBar.ButtonMouseOver` |
| Bordure | `InfoBar.ButtonMouseOverBorder` |

**Bouton de barre d’informations : état enfoncé**

![Bouton de barre d’informations appuyé](../../extensibility/ux-guidelines/media/0303_InfobarButtonPressed.png "0303_InfobarButtonPressed.png")<br />Bouton de barre d’informations appuyé

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `InfoBar.ButtonMouseDown` |
| Premier plan (texte) | `InfoBar.ButtonMouseDown` |
| Bordure | `InfoBar.ButtonMouseDownBorder` |

**Bouton de barre d’informations : l’état désactivé**

![Bouton de barre d’informations désactivé](../../extensibility/ux-guidelines/media/0303_InfobarButtonDisabled.png "0303_InfobarButtonDisabled.png")<br />Bouton de barre d’informations désactivé

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `InfoBar.ButtonDisabled` |
| Premier plan (texte) | `InfoBar.ButtonDisabled` |
| Bordure | `InfoBar.ButtonDisabledBorder` |

**Bouton de barre d’informations : état de focus**

![Bouton de barre d’informations ayant le focus](../../extensibility/ux-guidelines/media/0303_InfobarButtonFocus.png "0303_InfobarButtonFocus.png")<br />Bouton de barre d’informations ayant le focus

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `InfoBar.ButtonFocus` |
| Premier plan (texte) | `InfoBar.ButtonFocus` |
| Bordure | `InfoBar.ButtonFocusBorder` |

### <a name="scroll-bars"></a>Barres de défilement
Barres de défilement sont stylisées par l’environnement Visual Studio et ne doivent pas être à thème. Toutefois, vous pouvez décider que vous souhaitez exploiter les couleurs utilisées dans les barres de défilement afin que votre interface utilisateur apparaisse toujours cohérente avec cette partie de l’environnement Visual Studio.

![Barre de défilement (ligne rouge)](../../extensibility/ux-guidelines/media/0303-140_scrollbarredline.png "0303-140_ScrollbarRedline")<br />Barre de défilement (ligne rouge)

| Utilisez... | N’utilisez pas... |
| --- | --- |
| ... lorsque vous créez l’interface utilisateur que vous souhaitez faire correspondre les barres de défilement de Visual Studio. | ... pour tout ce que vous ne souhaitez pas toujours correspondre à l’interface utilisateur de la barre de défilement. |

**Barre de défilement : état par défaut**

![Barre de défilement par défaut](../../extensibility/ux-guidelines/media/0303-141_scrollbar.png "0303-141_Scrollbar")<br />Barre de défilement par défaut

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Barre de défilement | `Environment.ScrollBarBackground` |
| Premier plan (curseur de défilement) | `Environment.ScrollBarThumbBackground` |

**Barre de défilement : placez le curseur état**

![Barre de défilement au pointage](../../extensibility/ux-guidelines/media/0303-143_scrollbarhover.png "0303-143_ScrollbarHover")<br />Barre de défilement au pointage

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Barre de défilement | `Environment.ScrollBarBackground` |
| Premier plan (curseur de défilement) | `Environment.ScrollBarThumbMouseOverBackground` |

*Barre de défilement : état enfoncé**

![Pressed scroll bar](../../extensibility/ux-guidelines/media/0303-145_scrollbarpressed.png "0303-145_ScrollbarPressed")<br />Vous appuyez sur la barre de défilement

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Barre de défilement | `Environment.ScrollBarBackground` |
| Premier plan (curseur de défilement) | `Environment.ScrollBarThumbPressedBackground` |

**Flèche de barre de défilement : état par défaut**

![Flèche de barre de défilement par défaut](../../extensibility/ux-guidelines/media/0303-142_scrollbararrow.png "0303-142_ScrollbarArrow")<br />Flèche de barre de défilement par défaut

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `Environment.ScrollBarArrowBackground`<br />(Défini à la même couleur que la barre de défilement). |
| Premier plan (glyphe) | `Environment.ScrollBarArrowGlyph` |

**Flèche de barre de défilement : placez le curseur état**

![Flèche de survol de barre de défilement](../../extensibility/ux-guidelines/media/0303-144_scrollbararrowhover.png "0303-144_ScrollbarArrowHover")<br />Flèche de barre de défilement au pointage

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `Environment.ScrollBarArrowMouseOverBackground`<br />(Défini à la même couleur que la barre de défilement). |
| Premier plan (glyphe) | `Environment.ScrollBarArrowGlyphMouseOver` |

**Flèche de barre de défilement : état enfoncé**

![Flèche de barre de défilement appuyé](../../extensibility/ux-guidelines/media/0303-146_scrollbararrowpressed.png "0303-146_ScrollbarArrowPressed")<br />Vous appuyez sur la flèche de barre de défilement

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `Environment.ScrollBarArrowPressedBackground`<br />(Défini à la même couleur que la barre de défilement). |
| Premier plan (glyphe) | `Environment.ScrollBarArrowGlyphPressed` |

### <a name="BKMK_SearchBoxes"></a>Zones de recherche
Si possible, utilisez le contrôle de recherche commun fourni par l’environnement Visual Studio. Les couleurs de zone de recherche se trouvent dans la catégorie « SearchControl » du fichier **ShellColors.pkgdef** qui contient les noms de jeton du champ d’entrée, du bouton d’action, du bouton de liste déroulante et du menu déroulant.

Une zone de recherche peut être dans plusieurs états, dont certains s’excluent mutuellement :

- Les états « avec focus » ou « sans focus » font référence à la présence ou non du curseur dans la zone de texte.

- Les états « actif » ou « inactif » font référence à l’éventuel entrée par l’utilisateur d’une requête de recherche dans la zone de texte.

- L’état « pointage » signifie que l’utilisateur a placé le curseur de la souris au-dessus de la zone de recherche (cet état remplace tous les autres états).

- L’état « désactivé » signifie que la fonctionnalité de recherche est désactivée pour le contexte actuel.

![Zone de recherche (ligne rouge)](../../extensibility/ux-guidelines/media/0303-110_searchboxredline.png "0303-110_SearchBoxRedline")<br />Zone de recherche (ligne rouge)

| Utilisez... | N’utilisez pas... |
| --- | --- |
| ... lorsque vous créez une zone de recherche personnalisée. | ... pour tout élément qui n’est pas une zone de recherche. |
| | ... pour tout élément que vous ne souhaitez pas toujours correspondre à la recherche la zone de l’interface utilisateur. |

**Focus du champ d’entrée de recherche**

![Champ d’entrée de recherche ciblée dans](../../extensibility/ux-guidelines/media/0303-111_searchinputfieldfocused.png "0303-111_SearchInputFieldFocused")<br />Focus du champ d’entrée de recherche

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `SearchControl.FocusedBackground` |
| Premier plan (texte) | `SearchControl.FocusedBackground` |
| Bordure | `SearchControl.FocusedBorder` |
| Séparateur | `SearchControl.FocusedDropDownSeparator` |

**Champ d’entrée de recherche inactif, active**

![Champ d’entrée de recherche inactif](../../extensibility/ux-guidelines/media/0303-114_searchinputfieldunfocused.png "0303-114_SearchInputFieldUnfocused")<br />Champ d’entrée de recherche inactif, active

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `SearchControl.SearchActiveBackground` |
| Premier plan (texte) | `SearchControl.SearchActiveBackground` |
| Bordure | `SearchControl.UnfocusedBorder` |
| Séparateur | `SearchControl.DropDownSeparator` |

**Champ d’entrée de recherche inactif, inactif**

![Champ d’entrée de recherche inactif, inactive](../../extensibility/ux-guidelines/media/0303-114-1_searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")<br />Champ d’entrée de recherche inactif, inactif

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `SearchControl.Unfocused` |
| Premier plan (texte) | `SearchControl.Unfocused` |
| Bordure | `SearchControl.UnfocusedBorder` |
| Séparateur | `SearchControl.DropDownSeparator` |

**Champ d’entrée de recherche en surbrillance (texte uniquement)**

![Champ d’entrée de recherche en surbrillance](../../extensibility/ux-guidelines/media/0303-120_searchinputfieldhighlight.png "0303-120_SearchInputFieldHighlight")<br />Champ d’entrée de recherche en surbrillance

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `SearchControl.Selection` |
| Premier plan (texte) | `SearchControl.FocusedBackground` |
| Bordure | None |
| Séparateur | `SearchControl.FocusedDropDownSeparator` |

**Champ d’entrée de recherche désactivé**

![Champ d’entrée de recherche désactivé](../../extensibility/ux-guidelines/media/0303-121_searchinputfielddisabled.png "0303-121_SearchInputFieldDisabled")<br />Champ d’entrée de recherche désactivé

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `SearchControl.Disabled` |
| Premier plan (texte) | `SearchControl.Disabled` |
| Bordure | `SearchControl.DisabledBorder` |
| Séparateur | `SearchControl.DropDownSeparator` |

**Bouton d’action de recherche**

![Bouton d’action de recherche actif](../../extensibility/ux-guidelines/media/0303-112_searchactionbuttonfocused.png "0303-112_SearchActionButtonFocused")<br />Bouton d’action de recherche

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | None |
| Premier plan (glyphe Rechercher) | `SearchControl.SearchGlyph` |
| Premier plan (glyphe Arrêter) | `SearchControl.StopGlyph` |
| Premier plan (glyphe Effacer) | `SearchControl.ClearGlyph` |
| Bordure | N/A |

**Bouton d’action de recherche inactif**

![Bouton d’action de recherche inactif](../../extensibility/ux-guidelines/media/0303-115_searchactionbuttonunfocused.png "0303-115_SearchActionButtonUnfocused")<br />Bouton d’action de recherche inactif

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | N/A |
| Premier plan (glyphe Rechercher) | `SearchControl.SearchGlyph` |
| Premier plan (glyphe Arrêter) | `SearchControl.StopGlyph` |
| Premier plan (glyphe Effacer) | `SearchControl.ClearGlyph` |
| Bordure | N/A |

**Bouton d’action de recherche enfoncé**

![Bouton d’action de recherche enfoncé](../../extensibility/ux-guidelines/media/0303-116-1_searchactionbuttonpressed.png "0303-116-1_SearchActionButtonPressed")<br />Bouton d’action de recherche enfoncé

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `SearchControl.ActionButtonMouseDown` |
| Premier plan (glyphe) | `SearchControl.ActionButtonMouseDownGlyph` |
| Bordure | `SearchControl.ActionButtonMouseDownBorder` |

**Bouton d’action de recherche désactivé**

![Bouton d’action de recherche désactivé](../../extensibility/ux-guidelines/media/0303-122_searchactionbuttondisabled.png "0303-122_SearchActionButtonDisabled")<br />Bouton d’action de recherche désactivé

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | None |
| Premier plan (glyphe) | `SearchControl.ActionButtonDisabledGlyph` |
| Bordure | None |

**Bouton de liste déroulante de recherche**

![Bouton de liste déroulante de recherche ciblée dans](../../extensibility/ux-guidelines/media/0303-113_searchdropdownbuttonfocused.png "0303-113_SearchDropdownButtonFocused")<br />Bouton de liste déroulante de recherche

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `SearchControl.FocusedDropDownButton` |
| Premier plan (glyphe) | `SearchControl.FocusedDropDownButtonGlyph` |
| Bordure | `SearchControl.FocusedDropDownButtonBorder` |

**Bouton de liste déroulante de recherche inactif**

![Bouton de liste déroulante de recherche inactif](../../extensibility/ux-guidelines/media/0303-116_searchdropdownbuttonunfocused.png "0303-116_SearchDropdownButtonUnfocused")<br />Bouton de liste déroulante de recherche inactif

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `SearchControl.UnfocusedDropDownButton` |
| Premier plan (glyphe) | `SearchControl.UnfocusedDropDownButtonGlyph` |
| Bordure | `SearchControl.UnfocusedDropDownButtonBorder` |

**Bouton de liste déroulante de recherche enfoncé**

![Bouton de liste déroulante de recherche enfoncé](../../extensibility/ux-guidelines/media/0303-116-2_searchdropdownbuttonpressed.png "0303-116-2_SearchDropdownButtonPressed")<br />Bouton de liste déroulante de recherche enfoncé

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `SearchControl.MouseDownDropDownButton` |
| Premier plan (glyphe) | `SearchControl.MouseDownDropDownButtonGlyph` |
| Bordure | `SearchControl.MouseDownDropDownButtonBorder` |

**Bouton de liste déroulante de recherche désactivé**

![Bouton de liste déroulante de recherche désactivé](../../extensibility/ux-guidelines/media/0303-123_searchdropdownbuttondisabled.png "0303-123_SearchDropdownButtonDisabled")<br />Bouton de liste déroulante de recherche désactivé

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | None |
| Premier plan (glyphe) | `SearchControl.DisabledDownButtonGlyph` |
| Bordure | None |

#### <a name="search-drop-down-lists"></a>Listes déroulantes de recherche
Menu de liste déroulante de la zone de recherche a susceptibles d’être légèrement plus complexe que les autres menus déroulants dans Visual Studio. Les sections « options de recherche » ni « recherches suggérées » peuvent apparaître seules ou ensemble dans le menu, et chacun d’eux est coloré séparément. Une ligne sépare également ces deux sections quand elles apparaissent ensemble et une bordure entoure l’ensemble du menu déroulant.

![Liste déroulante de recherche (ligne rouge)](../../extensibility/ux-guidelines/media/0303-124_searchdropdownredline.png "0303-124_SearchDropdownRedline")<br />Liste déroulante de recherche (ligne rouge)

| Utilisez... | N’utilisez pas... |
| --- | --- |
| ... lors de la création d’une liste déroulante de recherche personnalisée. | ... pour les listes déroulantes qui apparaissent dans d’autres contextes. |
| ... les noms de jeton correctes pour les composants de la liste correcte. | ... dans n’importe quelle combinaison arrière-plan/premier plan autre que celle spécifiée. |

**Rechercher des éléments de liste déroulante**

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Bordure | `SearchControl.PopupBorder` |
| Séparateur | `SearchControl.PopupSectionHeaderSeparator` |
| Ombre | `Environment.DropShadowBackground` |

**Suggéré recherches : état par défaut**

![Par défaut des recherches suggérées](../../extensibility/ux-guidelines/media/0303-125_searchsuggested.png "0303-125_SearchSuggested")<br />Par défaut des recherches suggérées

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `SearchControl.PopupItemsListBackgroundGradientBegin`<br />(Points de dégradé pour ce jeton ne pas utilisé dans l’interface utilisateur à thème.) |
| Premier plan (texte) | `SearchControl.PopupItemText` |

**Suggéré recherches : placez le curseur état**

![Suggéré recherches pointage](../../extensibility/ux-guidelines/media/0303-128_searchsuggestedhover.png "0303-128_SearchSuggestedHover")<br />Recherches suggérées au pointage

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br />(Points de dégradé pour ce jeton ne pas utilisé dans l’interface utilisateur à thème.) |
| Premier plan (texte) | `SearchControl.PopupMouseOverItemText` |
| Bordure | `SearchControl.PopupControlMouseOverBorder` |

**Options de recherche : état par défaut**

![Case à cocher Rechercher](../../extensibility/ux-guidelines/media/0303-126_searchcheckbox.png "0303-126_SearchCheckbox")<br />Options de recherche par défaut (case à cocher)

![Options de recherche](../../extensibility/ux-guidelines/media/0303-127_searchoptions.png "0303-127_SearchOptions")<br />Options de recherche par défaut (lien)

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `SearchControl.PopupSectionBackgroundGradientBegin`<br />(Points de dégradé pour ce jeton ne pas utilisé dans l’interface utilisateur à thème.) |
| Premier plan (texte de case à cocher) | `SearchControl.PopupCheckboxText` |
| Premier plan (texte de lien) | `SearchControl.PopupButtonText` |
| Arrière-plan d’en-tête | `SearchControl.PopupSectionHeaderGradientBegin`<br />(Points de dégradé pour ce jeton ne pas utilisé dans l’interface utilisateur à thème.) |
| Premier plan (texte d’en-tête) | `SearchControl.PopupSectionHeaderText` |

**Options de recherche : placez le curseur état**

![Options (case à cocher) de recherche au pointage](../../extensibility/ux-guidelines/media/0303-129_searchcheckboxhover.png "0303-129_SearchCheckboxHover")<br />Options de recherche (case à cocher) au pointage

![Options (lien) de recherche au pointage](../../extensibility/ux-guidelines/media/0303-130_searchoptionshover.png "0303-130_SearchOptionsHover")<br />Options de recherche (lien) au pointage

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br />(Points de dégradé pour ce jeton ne pas utilisé dans l’interface utilisateur à thème.) |
| Premier plan (texte de case à cocher) | `SearchControl.PopupCheckboxMouseDownText` |
| Premier plan (texte de lien) | `SearchControl.PopupButtonMouseDownText` |
| Bordure | `SearchControl.PopupControlMouseOverBorder` |

**Options de recherche : état enfoncé**

![Utilisateur appuie sur les options de recherche (case à cocher)](../../extensibility/ux-guidelines/media/0303-131_searchsuggestedpressed.png "0303-131_SearchSuggestedPressed")<br />Utilisateur appuie sur les options de recherche (case à cocher)

![Utilisateur appuie sur les options de recherche (lien)](../../extensibility/ux-guidelines/media/0303-132_searchoptionspressed.png "0303-132_SearchOptionsPressed")<br />Utilisateur appuie sur les options de recherche (lien)

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan de case à cocher | `SearchControl.PopupControlMouseDownBackgroundGradientBegin`<br />`SearchControl.PopupControlMouseDownBackgroundGradientEnd`<br />(Points de dégradé pour ce jeton ne pas utilisé dans l’interface utilisateur à thème.) |
| Premier plan (texte de case à cocher) | `SearchControl.PopupCheckboxMouseDownText` |
| Arrière-plan de lien | `SearchControl.PopupButtonMouseDownBackgroundGradientBegin`<br />(Points de dégradé pour ce jeton ne pas utilisé dans l’interface utilisateur à thème.) |
| Premier plan (texte de lien) | `SearchControl.PopupButtonMouseDownText` |

### <a name="BKMK_TreeView"></a> Vues de l’arborescence
Plusieurs fenêtres d’outils, y compris l’Explorateur de solutions, l’Explorateur de serveurs et l’affichage de classes, implémentent un schéma d’organisation hiérarchique dont les couleurs sont contrôlées par les noms de couleur de la `TreeView` catégorie. Tous les éléments d’une arborescence ont des couleurs d’arrière-plan et de texte. Les éléments qui possèdent des éléments enfants imbriqués ont également des glyphes qui indiquent si l’élément est développé ou réduit.

![Vue arborescente (ligne rouge)](../../extensibility/ux-guidelines/media/0303-147_treeviewredline.png "0303-147_TreeViewRedline")<br />Vue arborescente (ligne rouge)

| Utilisez... | N’utilisez pas... |
| --- | --- |
| ... n’importe où vous devez implémenter une vue hiérarchique de l’organisation. | ... pour tout élément qui n’est pas similaire à une arborescence. |
| | ... dans n’importe quelle combinaison arrière-plan/premier plan autre que celle spécifiée. |

**Élément d’arborescence : état par défaut**

![Élément d’arborescence par défaut](../../extensibility/ux-guidelines/media/0303-148_treeview.png "0303-148_TreeView")<br />Élément d’arborescence par défaut

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `TreeView.Background` |
| Premier plan (texte) | `TreeView.Background` |
| Premier plan (glyphe) | `TreeView.Glyph` |
| Bordure | None |

**Élément d’arborescence : placez le curseur état**

![Élément d’arborescence au pointage](../../extensibility/ux-guidelines/media/0303-149_treeviewhover.png "0303-149_TreeViewHover")<br />Élément d’arborescence au pointage

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `TreeView.Background` |
| Premier plan (texte) | `TreeView.Background` |
| Premier plan (glyphe) | `TreeView.GlyphMouseOver` |
| Bordure | None |

**Élément d’arborescence : faites glisser sur l’état**

![Arborescence affiche l’élément sur glisser sur](../../extensibility/ux-guidelines/media/0303-150_treeviewdragover.png "0303-150_TreeViewDragOver")<br />Élément d’arborescence sur glisser

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `TreeView.DragOverItem` |
| Premier plan (texte) | `TreeView.DragOverItem` |
| Premier plan (glyphe) | `TreeView.DragOverItemGlyph` |
| Bordure | None |

**Élément d’arborescence : sélectionnée, concentré état**

![Sélectionné et concentre l’élément d’arborescence](../../extensibility/ux-guidelines/media/0303-151_treeviewfocused.png "0303-151_TreeViewFocused")<br />Élément d’arborescence sélectionné et vous oriente

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `TreeView.SelectedItemActive` |
| Premier plan (texte) | `TreeView.SelectedItemActive` |
| Premier plan (glyphe) | `TreeView.SelectedItemActiveGlyph` |
| Bordure | `TreeView.FocusVisualBorder` |

**Élément d’arborescence : état sélectionné, sans focus**

![Élément d’arborescence sélectionné et inactif](../../extensibility/ux-guidelines/media/0303-152_treeviewunfocused.png "0303-152_TreeViewUnfocused")<br />Élément d’arborescence sélectionné et inactif

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `TreeView.SelectedItemInactive` |
| Premier plan (texte) | `TreeView.SelectedItemInactive` |
| Premier plan (glyphe) | `TreeView.SelectedItemInactiveGlyph` |
| Bordure | None |

**Élément d’arborescence : Survolé, sélectionné et concentre l’état**

![Sélectionné et concentre l’élément d’arborescence au pointage](../../extensibility/ux-guidelines/media/0303-153_treeviewfocusedhover.png "0303-153_TreeViewFocusedHover")<br />Élément d’arborescence sélectionné et vous oriente sur pointage

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `TreeView.SelectedItemActive` |
| Premier plan (texte) | `TreeView.SelectedItemActive` |
| Premier plan (glyphe) | `TreeView.SelectedItemActiveGlyphMouseOver` |
| Bordure | `TreeView.FocusVisualBorder` |

**Élément d’arborescence : état Survolé, sélectionné et inactif**

![Élément d’arborescence sélectionné et inactif au pointage](../../extensibility/ux-guidelines/media/0303-154_treeviewunfocusedhover.png "0303-154_TreeViewUnfocusedHover")<br />Élément d’arborescence sélectionné et inactif au pointage

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `TreeView.SelectedItemInactive` |
| Premier plan (texte) | `TreeView.SelectedItemInactive` |
| Premier plan (glyphe) | `TreeView.SelectedItemActiveGlyphMouseOver` |
| Bordure | None |

## <a name="shell-appearance"></a>Apparence Shell

### <a name="background"></a>Présentation
L’arrière-plan de l’environnement comporte deux couches. La couche inférieure est une couleur unie qui recouvre l’ensemble de l’IDE. La couche supérieure se place sous l’interface de commande et entre les canaux à masquage automatique de la fenêtre Outil situés sur les côtés gauche et droit de l’IDE. Les couches d’arrière-plan supérieure et inférieure sont définies sur la même couleur dans les thèmes clairs et foncés.

![Arrière-plan du shell Visual Studio (ligne rouge)](../../extensibility/ux-guidelines/media/0303-187_shellbackgroundredline.png "0303-187_ShellBackgroundRedline")<br />Arrière-plan du shell Visual Studio (ligne rouge)

| Utilisez... | N’utilisez pas... |
| --- | --- |
| ... pour les endroits où vous souhaitez faire correspondre l’arrière-plan de l’environnement Visual Studio. | ... en tant que remplissage pour les emplacements qui ne sont pas des surfaces d’arrière-plan. |
| | ... comme arrière-plan pour placer des éléments de premier plan sur. |

**Aspect du shell couche bas**

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `Environment.EnvironmentBackground` |

**Apparence d’interpréteur de commandes de couche supérieure**

> Les points de dégradé sont définis sur la même valeur de couleur dans les thèmes clairs et foncés de Visual Studio 2013.

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `Environment.EnvironmentBackgroundGradientBegin`<br />`Environment.EnvironmentBackgroundGradientEnd`<br />`Environment.EnvironmentBackgroundGradientMiddle1`<br />`Environment.EnvironmentBackgroundGradientMiddle2` |

### <a name="command-shelf"></a>Interface de commande
Deux ensembles de noms de jeton sont utilisés pour les arrière-plans de l’interface de commande : un jeu pour l’emplacement de la barre de menus et l’autre pour l’emplacement des barres de commandes. Un groupe de barres de commandes possède ses propres valeurs de couleur d’arrière-plan, lesquelles sont décrites dans la section « Barre de commandes ». Le texte de la barre de menus et des barres de commandes est traité dans les sections qui leur sont dédiées.

![Conservation de commande Visual Studio (ligne rouge)](../../extensibility/ux-guidelines/media/0303-188_commandshelfredline.png "0303-188_CommandShelfRedline")<br />Conservation de commande Visual Studio (ligne rouge)

| Utilisez... | N’utilisez pas... |
| --- | --- |
| ... pour les zones où vous placez des menus ou barres d’outils. | ... pour les zones qui ne sont pas similaires à une interface de commande. |
|... avec la combinaison de nom de jeton correcte d’arrière-plan/premier plan. | |

**Barre de menus de conservation de commande**

> Les points de dégradé sont définis sur la même valeur de couleur dans les thèmes clairs et foncés de Visual Studio 2013.

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `Environment.CommandShelfHighlightGradientBegin`<br /><br />`Environment.CommandShelfHighlightGradientMiddle`<br />`Environment.CommandShelfHighlightGradientEnd` |

**Barre de commandes de conservation de commande**

> Les points de dégradé sont définis sur la même valeur de couleur dans les thèmes clairs et foncés de Visual Studio 2013.

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `Environment.CommandShelfBackgroundGradientBegin`<br />`Environment.CommandShelfBackgroundGradientMiddle`<br />`Environment.CommandShelfBackgroundGradientEnd` |

## <a name="manifest-designer"></a>Concepteur de manifeste
Le concepteur de manifeste sert à faciliter l’édition du fichier manifeste dans des projets Windows 8 et Windows Phone 8. Même s’il n’existe aucune infrastructure partagée disponible à la consommation, vous avez peut-être intérêt à faire correspondre la disposition et les couleurs des onglets d’orientation/de navigation à la structure générale. Pour plus d’informations sur la disposition, consultez [Layout for Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).

![Concepteur de manifeste (ligne rouge)](../../extensibility/ux-guidelines/media/0303-175_manifestdesignerredline.png "0303-175_ManifestDesignerRedline")<br />Concepteur de manifeste (ligne rouge)

| Utilisez... | N’utilisez pas... |
| --- | --- |
| ... pour les concepteurs qui sont similaires au Concepteur de manifeste. | ... Si vous avez plus de six onglets. |
| ... à la place à l’aide de contrôles d’onglet commun en haut d’un éditeur dans le document bien. | ... pour toute interface utilisateur qui ne sont pas structurée telles que le Concepteur de manifeste. |

**Manifest, onglet sélectionné de concepteur : état par défaut**

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `ManifestDesigner.TabActive` |
| Bordure | None |

**Volet de description sélectionné de Concepteur de manifeste : état par défaut**

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `ManifestDesigner.DescriptionPane` |

**Page de contenu sélectionné Concepteur de manifeste : état par défaut**

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `ManifestDesigner.Background` |
| Texte d’assistance de boîte de dialogue | `ManifestDesigner.WatermarkText`<br />(Ce nom de jeton ne correspond pas à sa fonction.) |

**Manifest, onglet Concepteur : désélectionné état**

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `ManifestDesigner.Tab.Inactive` |

**Manifest, onglet Concepteur : placez le curseur état**

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `ManifestDesigner.Tab.Mouseover` |

## <a name="command-structures"></a>Structures de commande

### <a name="BKMK_CommandMenus"></a> Menus
Menus peuvent se produire à plusieurs endroits dans Visual Studio : la barre de menus principale incorporée dans le document ou l’outil windows, ou sur avec le bouton droit à divers endroits de l’IDE. Les implémentations de menus associées aux autres éléments d’interface utilisateur sont décrites dans la section de l’élément correspondant. Vous devez toujours utiliser l’implémentation de menu standard fournie par l’environnement Visual Studio. Toutefois, dans de rares cas, vous n’aurez peut-être pas accès aux menus Visual Studio standard. Dans ce cas, utilisez les noms de jeton suivants pour vous assurer que votre interface utilisateur est cohérente avec les autres menus dans Visual Studio.

![Menu de Visual Studio (ligne rouge)](../../extensibility/ux-guidelines/media/0303-000_menuredline.png "0303-000_MenuRedline")<br />Menu de Visual Studio (ligne rouge)

| Utilisez... | N’utilisez pas... |
| --- | --- |
| ... que vous deviez créer un menu personnalisé.| ... la couleur d’arrière-plan uniquement. Utilisez toujours la combinaison arrière-plan/premier plan spécifiée. |
| ... lorsque vous avez un nouveau composant d’interface utilisateur que vous souhaitez faire correspondre les menus de Visual Studio.| |

#### <a name="menu-titles"></a>Titres de menu
Les titres de menu comprennent un arrière-plan, une bordure et le texte du titre, ainsi qu’un glyphe facultatif, généralement quand le menu se trouve dans une barre de commandes.

![Titre de menu (ligne rouge)](../../extensibility/ux-guidelines/media/0303-001_menutitleredline.png "0303-001_MenuTitleRedline")<br />Titre de menu (ligne rouge)

| Utilisez... | N’utilisez pas... |
| --- | --- |
| ... chaque fois que vous créez un titre de menu personnalisé. | ... pour tout élément que vous ne souhaitez pas toujours correspondre au titre de menu. |
| | ... dans n’importe quelle combinaison arrière-plan/premier plan autre que celle spécifiée. |

**Titre de menu : état par défaut**

![Par défaut de titre de menu](../../extensibility/ux-guidelines/media/0303-002_menutitledefault.png "0303-002_MenuTitleDefault")<br />Titre de menu par défaut

![Par défaut de titre de menu avec glyphe](../../extensibility/ux-guidelines/media/0303-003_menutitlewithglyphdefault.png "0303-003_MenuTitleWithGlyphDefault")<br />Titre de menu par défaut avec glyphe

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | None |
| Premier plan (texte) | `Environment.CommandBarTextActive` |
| Premier plan (glyphe) | `Environment.CommandBarMenuGlyph` |
| Bordure | None |

**Titre de menu : placez le curseur état**

![Titre de menu au pointage](../../extensibility/ux-guidelines/media/0303-004_menutitlehover.png "0303-004_MenuTitleHover")<br />Titre de menu au pointage

![Titre de menu avec glyphe au pointage](../../extensibility/ux-guidelines/media/0303-005_menutitlewithglyphhover.png "0303-005_MenuTitleWithGlyphHover")<br />Titre de menu avec glyphe au pointage

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `Environment.CommandBarMouseOverBackgroundBegin`<br />(Points de dégradé pour ce jeton ne pas utilisé dans l’interface utilisateur à thème.) |
| Premier plan (texte) | `Environment.CommandBarTextHover` |
| Premier plan (glyphe) | `Environment.CommandBarMenuMouseOverGlyph` |
| Bordure | `Environment.CommandBarBorder` |

**Titre de menu : état enfoncé**

![Titre de menu d’enfoncé](../../extensibility/ux-guidelines/media/0303-006_menutitlepressed.png "0303-006_MenuTitlePressed")<br />Titre de menu appuyé

![Utilisateur appuie sur le titre de menu avec glyphe](../../extensibility/ux-guidelines/media/0303-007_menutitlewithglyphpressed.png "0303-007_MenuTitleWithGlyphPressed")<br />Titre de menu avec glyphe d’enfoncé

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `Environment.CommandBarMenuBackgroundGradientBegin`<br/>(Points de dégradé pour ce jeton ne pas utilisé dans l’interface utilisateur à thème.) |
| Premier plan (texte) | `Environment.CommandBarTextActive` |
| Premier plan (glyphe) | `Environment.CommandBarMenuMouseDownGlyph` |
| Bordure | `Environment.CommandBarMenuBorder`<br />(Uniquement, haut, côtés gauche et droit.) |

**Titre de menu : l’état désactivé**

![Désactivé le titre de menu avec glyphe](../../extensibility/ux-guidelines/media/0303-008_menutitlewithglyphdisabled.png "0303-008_MenuTitleWithGlyphDisabled")<br />Titre de menu désactivé avec glyphe

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | None |
| Premier plan (texte) | `Environment.CommandBarTextInactive` |
| Premier plan (glyphe) | `Environment.CommandBarTextInactive` |
| Bordure | None |

#### <a name="menu-items"></a>Éléments de menu
Un élément de menu individuel comporte le texte du menu et éventuellement une icône, une case à cocher ou un glyphe de sous-menu. Sa couleur d’arrière-plan et de texte change au passage du curseur de la souris. Ce jeton de couleur est une paire arrière-plan/premier plan.

![Ligne rouge d’éléments de menu](../../extensibility/ux-guidelines/media/0303-009_menuitemredline.png "0303-009_MenuItemRedline")

| Utilisez... | N’utilisez pas... |
|---|---|
| ... pour toute liste déroulante qui est lancé à partir d’une barre de menus ou la barre de commandes. | ... pour toute liste déroulante dans un autre contexte. |
| | ... dans n’importe quelle combinaison arrière-plan/premier plan autre que celle spécifiée. |

**Éléments de menu : état par défaut**

![Éléments de menu par défaut](../../extensibility/ux-guidelines/media/0303-010_menudefault.png "0303-010_MenuDefault")<br />Éléments de menu par défaut

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `Environment.CommandBarMenuBackgroundGradientBegin`<br />(Points de dégradé pour ce jeton ne pas utilisé dans l’interface utilisateur à thème.) |
| Premier plan (texte) | `Environment.CommandBarTextActive` |
| Premier plan (glyphe de sous-menu) | `Environment.CommandBarMenuSubmenuGlyph` |
| Bordure | `Environment.CommandBarMenuBorder` |
| Arrière-plan de canal d’icône | `Environment.CommandBarMenuIconBackground` |
| Séparateur | `Environment.CommandBarMenuSeparator` |
| Ombre | `Environment.DropShadowBackground` |

**Éléments de menu : activé et sélectionné les États**

![Menu activé](../../extensibility/ux-guidelines/media/0303-011_menuchecked.png "0303-011_MenuChecked")<br />Élément de menu activé

![Menu sélectionné](../../extensibility/ux-guidelines/media/0303-012_menuselected.png "0303-012_MenuSelected")<br />Élément de menu sélectionné

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Coche | `Environment.CommandBarCheckBox` |
| Arrière-plan de case à cocher | `Environment.CommandBarSelectedIcon` |
| Arrière-plan d’icône | `Environment.CommandBarSelected` |
| Bordure d’icône | `Environment.CommandBarSelectedBorder` |

**Éléments de menu : placez le curseur état**

![Pointage de menu](../../extensibility/ux-guidelines/media/0303-013_menuhover.png "0303-013_MenuHover")<br />Élément de menu au pointage

![Pointage de menu activé](../../extensibility/ux-guidelines/media/0303-014_menuhoverchecked.png "0303-014_MenuHoverChecked")<br />Vérifié l’élément de menu au pointage

![Pointage de menu sélectionné](../../extensibility/ux-guidelines/media/0303-015_menuhoverselected.png "0303-015_MenuHoverSelected")<br />Élément de menu sélectionné au pointage

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `Environment.CommandBarMenuItemMouseOver` |
| Premier plan (texte) | `Environment.CommandBarMenuItemMouseOver` |
| Premier plan (glyphe de sous-menu) | `Environment.CommandBarMenuMouseOverSubmenuGlyph` |
| Coche | `Environment.CommandBarCheckBoxMouseOver` |
| Arrière-plan de case à cocher | `Environment.CommandBarHoverOverSelectedIcon` |
| Arrière-plan d’icône | `Environment.CommandBarHoverOverSelected` |
| Bordure d’icône | `Environment.CommandBarHoverOverSelectedIconBorder` |

**Éléments de menu : l’état désactivé**

![Menu désactivé](../../extensibility/ux-guidelines/media/0303-016_menudisabled.png "0303-016_MenuDisabled")<br />Élément de menu désactivé

![Menu désactivé activé](../../extensibility/ux-guidelines/media/0303-017_menudisabledchecked.png "0303-017_MenuDisabledChecked")<br />Élément de menu désactivé avec la case à cocher

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Premier plan (texte) | `Environment.CommandBarTextInactive` |
| Premier plan (glyphe de sous-menu) | `Environment.CommandBarMenuSubmenuGlyph` |
| Coche | `Environment.CommandBarCheckBoxDisabled` |
| Arrière-plan de case à cocher | `Environment.CommandBarSelectedIconDisabled` |

### <a name="command-bars"></a>Barres de commandes
Une barre de commandes peut apparaître à plusieurs endroits dans l’IDE de Visual Studio, plus particulièrement conservation de commande et outil incorporé dans les fenêtres de document.

En règle générale, utilisez toujours l’implémentation de barre de commandes standard fournie par l’environnement Visual Studio. L’utilisation du mécanisme standard permet à tous les détails visuels d’apparaître correctement et aux éléments interactifs de se comporter de manière cohérente avec les autres contrôles de barre de commandes Visual Studio. Toutefois, si vous avez besoin de créer votre propre barre de commandes, assurez-vous d’utiliser un style adéquat avec les noms de jeton suivants.

![Ligne rouge de barre de commandes](../../extensibility/ux-guidelines/media/0303-018_commandbarredline.png "0303-018_CommandBarRedline")<br />Barre de commandes (ligne rouge)

![Ligne rouge de bouton de dépassement de capacité](../../extensibility/ux-guidelines/media/0303-019_overflowbuttonredline.png "0303-019_OverflowButtonRedline")<br />Bouton de dépassement (ligne rouge)

| Utilisez... | N’utilisez pas... |
| --- | --- |
| ... dans les endroits où vous avez besoin d’une barre de commandes incorporées, mais ne pouvez pas utiliser l’implémentation de barre de commandes Visual Studio standard. | ... pour les éléments d’interface utilisateur qui ne sont pas similaire à une barre de commandes. |
| | ... pour les composants de barre de commandes autres que celles pour lesquelles les noms de jeton sont spécifiés. |

#### <a name="command-bar-groups"></a>Groupes de barre de commandes
Un groupe de barres de commandes se compose d’un ensemble de contrôles de barre de commandes et peut contenir tout nombre de boutons, boutons partagés, menus déroulants, zones de liste modifiable ou menus. Les couleurs de ces contrôles sont régies par des noms de jeton distincts et sont décrites individuellement dans une autre section de ce guide. Un trait de séparation est utilisé pour diviser un groupe de barres de commandes en sous-groupes associés.

![Ligne rouge de groupe de barres de commande](../../extensibility/ux-guidelines/media/0303-020_commandbargroupredline.png "0303-020_CommandBarGroupRedline")<br />Groupe de barres de commande (ligne rouge)

| Utilisez... | N’utilisez pas... |
| --- | --- |
| ... dans les endroits où vous avez besoin d’une barre de commandes incorporées, mais ne pouvez pas utiliser l’implémentation de barre de commandes Visual Studio standard. | ... pour les éléments d’interface utilisateur qui ne sont pas similaire à une barre de commandes. |
| | ... pour les composants de barre de commandes autres que celles pour lesquelles les noms de jeton sont spécifiés. |

**Groupe de barres de commande : état par défaut**

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `Environment.CommandBarGradientBegin`<br />(Points de dégradé pour ce jeton ne pas utilisé dans l’interface utilisateur à thème.) |
| Bordure | `Environment.CommandBarToolBarBorder` |
| Faire glisser la poignée | `Environment.CommandBarDragHandle` |
| Séparateur | `Environment.CommandBarToolBarSeparator`<br />`Environment.CommandBarToolBarSeparatorHighlight` |

#### <a name="command-icons"></a>Icônes de commande
![Ligne rouge d’icône de commande](../../extensibility/ux-guidelines/media/0303-021_commandiconredline1.png "0303-021_CommandIconRedline1")<br />Icône de commande (ligne rouge)

![Ligne rouge d’icône de commande avec le texte](../../extensibility/ux-guidelines/media/0303-022_commandiconredline2.png "0303-022_CommandIconRedline2")<br />Icône de commande avec le texte (ligne rouge)

| Utilisez... | N’utilisez pas... |
| --- | --- |
| ... pour les boutons qui seront placés sur une barre de commandes. | ... pour les contrôles qui ont leurs propres noms de jeton. |
| | ... dans n’importe quelle combinaison arrière-plan/premier plan autre que celle spécifiée. |

**Icône de commande : état par défaut**

![Commande par défaut d’icône](../../extensibility/ux-guidelines/media/0303-023_commandicondefault.png "0303-023_CommandIconDefault")<br />Icône de commande par défaut

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | N/A (hérite de l’arrière-plan de la barre commandes) |
| Premier plan (texte) | `Environment.CommandBarTextActive` |
| Bordure | N/A |

**Icône de commande : état, sélectionnée par défaut**

![Par défaut, l’icône de la commande sélectionnée](../../extensibility/ux-guidelines/media/0303-024_commandicondefaultselected.png "0303-024_CommandIconDefaultSelected")<br />Par défaut, l’icône de la commande sélectionnée

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `Environment.CommandBarSelected` |
| Premier plan (texte) | `Environment.CommandBarTextSelected` |
| Bordure | `Environment.CommandBarSelectedBorder` |

**Icône de commande : États pointage ou le focus**

![Icône de commande sur pointage ou le focus](../../extensibility/ux-guidelines/media/0303-025_commandiconhover.png "0303-025_CommandIconHover")<br />Icône de commande sur pointage ou le focus

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `Environment.CommandBarMouseOverBackgroundBegin`<br />(Points de dégradé pour ce jeton ne pas utilisé dans l’interface utilisateur à thème.) |
| Premier plan (texte) | `Environment.CommandBarTextHover` |
| Bordure | `Environment.CommandBarBorder` |

**Icône de commande : États pointage ou le focus, sélectionné**

![Sélectionné l’icône de commande sur pointage ou le focus](../../extensibility/ux-guidelines/media/0303-026_commandiconhoverselected.png "0303-026_CommandIconHoverSelected")<br />Icône de commande sélectionnée sur pointage ou le focus

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `Environment.CommandBarHoverOverSelected` |
| Premier plan (texte) | `Environment.CommandBarTextHoverOverSelected` |
| Bordure | `Environment.CommandBarHoverOverSelectedIconBorder` |

 **Icône de commande : état enfoncé**

![Icône de commande d’enfoncé](../../extensibility/ux-guidelines/media/0303-027_commandiconpressed.png "0303-027_CommandIconPressed")<br />Icône de commande appuyée

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `Environment.CommandBarMouseDownBackgroundBegin`<br />(Points de dégradé pour ce jeton ne pas utilisé dans l’interface utilisateur à thème.) |
| Premier plan (texte) | `Environment.CommandBarTextMouseDown` |
| Bordure | `Environment.CommandBarBorder` |

**Icône de commande : l’état désactivé**

![Icône de commande désactivée](../../extensibility/ux-guidelines/media/0303-028_commandicondisabled.png "0303-028_CommandIconDisabled")<br />Icône de commande désactivée

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | N/A (hérite de l’arrière-plan de la barre commandes) |
| Premier plan (texte) | `Environment.CommandBarTextInactive` |
| Bordure | N/A |

#### <a name="BKMK_CommandComboBox"></a> Zones de liste déroulante de barre de commande

> [!IMPORTANT]
> Les zones de liste modifiable ressemblent aux listes déroulantes, mais elles comprennent une zone de texte modifiable. Si votre liste déroulante n’inclut pas de zone de texte modifiable, utilisez les jetons de couleur pour [barre listes déroulantes de commandes](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandDropDown).

![Ligne rouge de zone de liste déroulante de la barre de commandes](../../extensibility/ux-guidelines/media/0303-029_comboboxredline.png "0303-029_ComboBoxRedline")<br />Zone de liste déroulante de barre de commandes (ligne rouge)

| Utilisez... | N’utilisez pas... |
| --- | --- |
| ... lors de la création de zones de liste déroulante personnalisés. | ... pour quoi que ce soit vous ne souhaitez toujours correspondre à la commande interface utilisateur de barre. |
| ... lors de la création d’un contrôle de barre de commande est similaire à une zone de liste déroulante. | ... lorsque vous avez accès à une zone de liste déroulante de style. |

**Champ d’entrée de zone de liste déroulante de la barre de commande : état par défaut**

![Champ d’entrée de zone de liste déroulante de la barre de commande](../../extensibility/ux-guidelines/media/0303-030_comboboxinputfield.png "0303-030_ComboBoxInputField")<br />Champ d’entrée de zone de liste déroulante de la barre de commande

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `Environment.ComboBoxBackground` |
| Premier plan (texte) | `Environment.ComboBoxText` |
| Bordure | `Environment.ComboBoxBorder` |
| Séparateur | Aucun séparateur |

**Bouton de liste déroulante de barre de commande : état par défaut**

![Liste de zone de liste déroulante&#45;bouton enfoncé](../../extensibility/ux-guidelines/media/0303-031_comboboxdropdownbutton.png "0303-031_ComboBoxDropdownButton")<br />Bouton de liste déroulante de barre de commande

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | N/A (hérite de l’arrière-plan de la barre commandes) |
| Premier plan (glyphe) | `Environment.ComboBoxGlyph` |

**Liste déroulante de barre de commande : état par défaut**

![Liste déroulante de barre de commandes](../../extensibility/ux-guidelines/media/0303-032_comboboxdropdownlist.png "0303-032_ComboBoxDropdownList")<br />Liste déroulante de barre de commande

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `Environment.ComboBoxPopupBackgroundBegin`<br />(Points de dégradé pour ce jeton ne pas utilisé dans l’interface utilisateur à thème.) |
| Premier plan (texte) | `Environment.ComboBoxItemText` |
| Bordure | `Environment.ComboBoxPopupBorder` |

**Champ d’entrée de zone de liste déroulante de la barre de commande : placez le curseur état**

![Commande barre boîte d’entrée champ de liste déroulante au pointage](../../extensibility/ux-guidelines/media/0303-033_comboboxinputfieldhover.png "0303-033_ComboBoxInputFieldHover")<br />Commande barre boîte d’entrée champ de liste déroulante au pointage

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `Environment.ComboBoxMouseOverBackgroundBegin`<br />(Points de dégradé pour ce jeton ne pas utilisé dans l’interface utilisateur à thème.) |
| Premier plan (texte) | `Environment.ComboBoxMouseOverText` |
| Bordure | `Environment.ComboBoxMouseOverBorder` |
| Séparateur | `Environment.ComboBoxMouseOverSeparator` |

 **Bouton de liste déroulante de barre de commande : placez le curseur état**

![Bouton liste déroulante au pointage](../../extensibility/ux-guidelines/media/0303-034_comboboxdropdownbuttonhover.png "0303-034_ComboBoxDropdownButtonHover")<br />Bouton liste déroulante au pointage

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `Environment.ComboBoxButtonMouseOverBackground` |
| Premier plan (glyphe) | `Environment.ComboBoxMouseOverGlyph` |

**Liste déroulante de barre de commande : placez le curseur état**

 ![Liste de liste déroulante de barre de commandes pointage](../../extensibility/ux-guidelines/media/0303-035_comboboxdropdownlisthover.png "0303-035_ComboBoxDropdownListHover")<br />Liste de liste déroulante de barre de commandes pointage

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan (élément de menu) | `Environment.ComboBoxItemMouseOverBackground` |
| Premier plan (texte) | `Environment.ComboBoxItemMouseOverText` |
| Bordure (élément de menu) | `Environment.ComboBoxItemMouseOverBorder` |

 **Champ d’entrée de zone de liste déroulante de la barre de commande : état de focus**

![Focus du champ d’entrée de zone de liste déroulante de la barre de commandes](../../extensibility/ux-guidelines/media/0303-036_comboboxinputfieldfocused.png "0303-036_ComboBoxInputFieldFocused")<br />Focus du champ d’entrée de zone de liste déroulante de la barre de commande

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `Environment.ComboBoxFocusedBackground` |
| Premier plan (texte) | `Environment.ComboBoxFocusedText` |
| Bordure | `Environment.ComboBoxFocusedBorder` |
| Séparateur | `Environment.ComboBoxFocusedButtonSeparator` |

**Bouton de liste déroulante de barre de commande : état de focus**

![Bouton déroulant de barre de commandes de focus](../../extensibility/ux-guidelines/media/0303-037_comboboxdropdownbuttonfocused.png "0303-037_ComboBoxDropdownButtonFocused")<br />Commande ayant le focus à la barre de bouton de liste déroulante

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `Environment.ComboBoxFocusedButtonBackground` |
| Premier plan (glyphe) | `Environment.ComboBoxFocusedGlyph` |

 **Champ d’entrée de zone de liste déroulante de la barre de commande : état enfoncé**

![Enfoncé commande champ d’entrée de zone de liste déroulante de la barre](../../extensibility/ux-guidelines/media/0303-038_comboboxinputfieldpressed.png "0303-038_ComboBoxInputFieldPressed")<br />Champ d’entrée de zone de liste déroulante de la barre de commande d’enfoncé

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `Environment.ComboBoxMouseDownBackground` |
| Premier plan (texte) | `Environment.ComboBoxMouseDownText` |
| Bordure | `Environment.ComboBoxMouseDownBorder` |
| Séparateur | `Environment.ComboBoxMouseDownSeparator` |

**Bouton de liste déroulante de barre de commande : état enfoncé**

![Enfoncé le bouton déroulant de barre de commandes](../../extensibility/ux-guidelines/media/0303-039_comboboxdropdownbuttonpressed.png "0303-039_ComboBoxDropdownButtonPressed")<br />Enfoncé le bouton déroulant de barre de commandes

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `Environment.ComboBoxButtonMouseDownBackground` |
| Premier plan (glyphe) | `Environment.ComboBoxMouseDownGlyph` |

**Champ d’entrée de zone de liste déroulante de la barre de commande : l’état désactivé**

![Désactivé le champ d’entrée de zone de liste déroulante de la barre de commandes](../../extensibility/ux-guidelines/media/0303-041_comboboxinputfielddisabled.png "0303-041_ComboBoxInputFieldDisabled")<br />Commande désactivé champ d’entrée de zone de liste déroulante de la barre

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `Environment.ComboBoxDisabledBackground` |
| Premier plan (texte) | `Environment.ComboBoxDisabledText` |
| Bordure | `Environment.ComboBoxDisabledBorder` |
| Séparateur | Aucun séparateur |

**Bouton de liste déroulante de barre de commande : l’état désactivé**

![Désactiver le bouton déroulant de barre de commandes](../../extensibility/ux-guidelines/media/0303-040_comboboxdropdownbuttondisabled.png "0303-040_ComboBoxDropdownButtonDisabled")<br />Commande désactivé bouton déroulant de barre

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | None |
| Premier plan (glyphe) | `Environment.ComboBoxDisabledGlyph` |

#### <a name="BKMK_CommandDropDown"></a> Commande Barres déroulantes

> [!IMPORTANT]
> Les listes déroulantes ressemblent aux zones de liste modifiable, mais elles ne disposent pas de zones de texte modifiable. Si votre liste déroulante inclut une zone de texte modifiable, utilisez les jetons de couleur pour [barre des zones de liste déroulante de commandes](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandComboBox).

![Liste déroulante de la barre de commandes (ligne rouge)](../../extensibility/ux-guidelines/media/0303-042_dropdownredline.png "0303-042_DropdownRedline")<br />Liste déroulante de la barre de commandes (ligne rouge)

| Utilisez... | N’utilisez pas... |
| --- | --- |
| ... lorsque vous créez des contrôles de liste déroulante personnalisée. | ... pour tout élément qui n’est pas similaire à une liste déroulante. |
| | ... pour les zones de liste déroulante ou des boutons partagés. |

**Champ de sélection de liste déroulante de la barre de commande : état par défaut**

![Par défaut du champ de sélection de liste déroulante de la barre de commandes](../../extensibility/ux-guidelines/media/0303-043_dropdownselectionfield.png "0303-043_DropdownSelectionField")<br />Champ de sélection de liste déroulante de la barre de commande par défaut

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `Environment.DropDownBackground` |
| Premier plan (texte) | `DropDownText` |
| Bordure | `DropDownBorder` |
| Séparateur | Aucun séparateur |

**Bouton de liste déroulante de barre de commande : état par défaut**

![Par défaut du bouton déroulant de barre de commandes](../../extensibility/ux-guidelines/media/0303-044_dropdownbutton.png "0303-044_DropdownButton")<br />Bouton de liste déroulante de barre de commande par défaut

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | None |
| Premier plan (glyphe) | `Environment.DropDownGlyph` |

**Liste déroulante de barre de commande : état par défaut**

![Valeur par défaut de la liste déroulante de la barre de commandes](../../extensibility/ux-guidelines/media/0303-045_dropdownlist.png "0303-045_DropdownList")<br />Liste de liste déroulante de barre de commandes par défaut

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `Environment.DropDownPopupBackgroundBegin`<br />(Points de dégradé pour ce jeton ne pas utilisé dans l’interface utilisateur à thème.) |
| Premier plan (texte) | `Environment.ComboBoxItemText` |
| Bordure | `Environment.DropDownPopupBorder` |
| Ombre | `Environment.DropShadowBackground` |

**Champ de sélection de liste déroulante de la barre de commande : placez le curseur état**

![Champ de sélection de liste déroulante de la barre de commandes pointage](../../extensibility/ux-guidelines/media/0303-046_dropdownselectionfieldhover.png "0303-046_DropdownSelectionFieldHover")<br />Champ de sélection de liste déroulante de la barre de commandes pointage

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `Environment.DropDownMouseOverBackgroundBegin`<br />(Points de dégradé pour ce jeton ne pas utilisé dans l’interface utilisateur à thème.) |
| Premier plan (texte) | `Environment.DropDownMouseOverText` |
| Bordure | `Environment.DropDownMouseOverBorder` |
| Séparateur | `Environment.DropDownButtonMouseOverSeparator` |

**Bouton de liste déroulante de barre de commande : placez le curseur état**

![Bouton liste déroulante au pointage](../../extensibility/ux-guidelines/media/0303-047_dropdownbuttonhover.png "0303-047_DropdownButtonHover")<br />Bouton liste déroulante au pointage

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `Environment.DropDownButtonMouseOverBackground` |
| Premier plan (glyphe) | `Environment.DropDownMouseOverGlyph` |

**Liste déroulante de barre de commande : placez le curseur état**

![Liste de liste déroulante de barre de commandes pointage](../../extensibility/ux-guidelines/media/0303-048_dropdownlisthover.png "0303-048_DropdownListHover")<br />Liste de liste déroulante de barre de commandes pointage

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan (élément de menu) | `Environment.ComboBoxItemMouseOverBackground` |
| Premier plan (texte) | `Environment.ComboBoxItemMouseOverText` |
| Bordure (élément de menu) | `Environment.ComboBoxItemMouseOverBorder` |

 **Champ de sélection de liste déroulante de la barre de commande : état enfoncé**

![DROP&#45;vers le bas du champ de sélection enfoncé](../../extensibility/ux-guidelines/media/0303-049_dropdownselectionfieldpressed.png "0303-049_DropdownSelectionFieldPressed")<br />Enfoncé commande champ de sélection de liste déroulante de la barre

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `Environment.DropDownMouseDownBackground` |
| Premier plan (texte) | `Environment.DropDownMouseDownText` |
| Bordure | `Environment.DropDownMouseDownBorder` |
| Séparateur | `Environment.DropDownButtonMouseDownSeparator` |

**Bouton de liste déroulante de barre de commande : état enfoncé**

![Enfoncé le bouton déroulant de barre de commandes](../../extensibility/ux-guidelines/media/0303-050_dropdownbuttonpressed.png "0303-050_DropdownButtonPressed")<br />Enfoncé le bouton déroulant de barre de commandes

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `Environment.DropDownButtonMouseDownBackground` |
| Premier plan (glyphe) | `Environment.DropDownMouseDownGlyph` |

**Champ de sélection de liste déroulante de la barre de commande : l’état désactivé**

![Désactivé le champ de sélection de liste déroulante de la barre de commandes](../../extensibility/ux-guidelines/media/0303-051_dropdownselectionfielddisabled.png "0303-051_DropdownSelectionFieldDisabled")<br />Commande désactivé champ de sélection de liste déroulante de la barre

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `Environment.DropDownDisabledBackground` |
| Premier plan (texte) | `Environment.DropDownDisabledText` |
| Bordure | `Environment.DropDownDisabledBorder` |
| Séparateur | Aucun séparateur |

**Bouton de liste déroulante de barre de commande : l’état désactivé**

![Désactiver le bouton déroulant de barre de commandes](../../extensibility/ux-guidelines/media/0303-052_dropdownbuttondisabled.png "0303-052_DropdownButtonDisabled")<br />Commande désactivé bouton déroulant de barre

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | N/A |
| Premier plan (glyphe) | `Environment.DropDownDisabledGlyph` |

#### <a name="command-bar-split-buttons"></a>Boutons de barre de commandes partagés
Les boutons partagés partagent de nombreux noms de jeton avec d’autres contrôles de barre de commandes, tels que des boutons, menus et texte de barre de commandes. Toutes les actions nécessaires et les noms de jeton bouton de liste déroulante sont répétés ici par commodité. Listes de liste déroulante du bouton partagé sont des implémentations de [barre de menus de commandes](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandMenus).

![Ligne rouge de bouton partagé](../../extensibility/ux-guidelines/media/0303-053_splitbuttonredline.png "0303-053_SplitButtonRedline")<br />Barre de commandes de bouton partagé (ligne rouge)

| Utilisez... | N’utilisez pas... |
| --- | --- |
| ... lors de la création d’un bouton partagé personnalisé. | ... pour d’autres types de boutons. |
| | ... dans n’importe quelle combinaison arrière-plan/premier plan autre que celle spécifiée. |

**Bouton de barre de commandes partagé : état par défaut**

![Valeur par défaut de la commande de barre de bouton partagé](../../extensibility/ux-guidelines/media/0303-054_splitbutton.png "0303-054_SplitButton")<br />Bouton de barre de commandes par défaut partagé

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | None |
| Premier plan (texte) | `Environment.CommandBarTextActive` |
| Premier plan (glyphe) | `Environment.CommandBarSplitButtonGlyph` |
| Bordure | N/A |
| Séparateur | N/A |

**Bouton de barre de commandes partagé : placez le curseur état**

![Bouton de survol de partagé de barre de commandes](../../extensibility/ux-guidelines/media/0303-055_splitbuttonhover.png "0303-055_SplitButtonHover")<br />Barre de commandes fractionner bouton au pointage

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `Environment.CommandBarMouseOverBackgroundBegin`<br />(Points de dégradé pour ce jeton ne pas utilisé dans l’interface utilisateur à thème.) |
| Premier plan (texte) | `Environment.CommandBarTextHover` |
| Premier plan (glyphe) | `Environment.CommandBarSplitButtonMouseOverGlyph` |
| Bordure | `Environment.CommandBarBorder` |
| Séparateur | `Environment.CommandBarSplitButtonSeparator` |

**Bouton de barre de commandes partagé : état enfoncé**

![Enfoncé le bouton partagé de barre de commandes](../../extensibility/ux-guidelines/media/0303-056_splitbuttonpressed.png "0303-056_SplitButtonPressed")<br />Bouton de barre de commandes appuyé partagé

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `Environment.CommandBarMouseDownBackgroundBegin`<br />(Points de dégradé pour ce jeton ne pas utilisé dans l’interface utilisateur à thème.) |
| Premier plan (texte) | `Environment.CommandBarTextMouseDown` |
| Premier plan (glyphe) | `Environment.CommandBarSplitButtonMouseDownGlyph` |
| Bordure | `Environment.CommandBarBorder` |
| Séparateur | N/A |

**Bouton de barre de commandes partagé : l’état désactivé**

![Désactivé la commande de barre de bouton partagé](../../extensibility/ux-guidelines/media/0303-057_splitbuttondisabled.png "0303-057_SplitButtonDisabled")<br />Bouton de barre de commandes désactivée partagé

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | N/A |
| Premier plan (texte) | `Environment.ComboBoxItemTextInactive` |
| Premier plan (glyphe) | `Environment.CommandBarTextInactive` |
| Bordure | N/A |
| Séparateur | N/A |

#### <a name="command-bar-more-options-and-overflow-buttons"></a>Boutons de commande de la barre « Autres options » et « Dépassement »
Le bouton « Autres options » est utilisé quand un groupe de barres de commandes peut être personnalisé en ajoutant ou en supprimant des boutons de barre de commandes associés. Le bouton « >> » apparaît quand une barre de commandes est tronquée en raison d’un manque d’espace horizontal. En cliquant dessus, un menu se déroule pour afficher les autres boutons de la barre de commandes qui ne pouvaient pas apparaître. Les couleurs de ces deux boutons sont contrôlées par le même ensemble de noms de jeton.

![Bouton « Plus d’options » de la barre de commandes (ligne rouge)](../../extensibility/ux-guidelines/media/0303-058_moreoptionsredline.png "0303-058_MoreOptionsRedline")<br />Bouton « Plus d’options » de la barre de commandes (ligne rouge)

| Utilisez... | N’utilisez pas... |
| --- | --- |
| ... pour personnalisé « autres options » ou « Dépassement » boutons. | ... pour les boutons qui n’ont pas une fonctionnalité similaire à un « Autres options » ou un bouton « Dépassement ». |

**« Autres options » et « Overflow » des boutons de la barre de commandes : état par défaut**

![Par défaut du bouton « Plus d’options » de la barre de commandes](../../extensibility/ux-guidelines/media/0303-059_moreoptions.png "0303-059_MoreOptions")<br />Bouton « Plus d’options » de la barre de commandes par défaut

![Par défaut la valeur « Overflow » un bouton de barre de commandes](../../extensibility/ux-guidelines/media/0303-060_overflow.png "0303-060_Overflow")<br />Par défaut la valeur « Overflow » bouton

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `Environment.CommandBarOptionsBackground` |
| Premier plan (glyphe) | `Environment.CommandBarOptionsGlyph` |

**« Autres options » et « Overflow » des boutons de la barre de commandes : placez le curseur état**

![Bouton « Autres options » de survol de la barre de commandes](../../extensibility/ux-guidelines/media/0303-061_moreoptionshover.png "0303-061_MoreOptionsHover")<br />Bouton « Autres options » de survol de la barre de commandes

![La valeur « Overflow » bouton au pointage](../../extensibility/ux-guidelines/media/0303-062_overflowoptions.png "0303-062_OverflowOptions")<br />La valeur « Overflow » bouton au pointage

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `Environment.CommandBarOptionsMouseOverBackgroundBegin`<br />(Points de dégradé pour ce jeton ne pas utilisé dans l’interface utilisateur à thème.) |
| Premier plan (glyphe) | `Environment.CommandBarOptionsMouseDownGlyph` |

**« Autres options » et « Overflow » des boutons de la barre de commandes : état enfoncé**

![Enfoncé le bouton « Plus d’options » de la barre de commandes](../../extensibility/ux-guidelines/media/0303-063_moreoptionspressed.png "0303-063_MoreOptionsPressed")<br />Enfoncé le bouton « Plus d’options » de la barre de commandes

![Dépassement enfoncé](../../extensibility/ux-guidelines/media/0303-064_overflowpressed.png "0303-064_OverflowPressed")<br />Enfoncé le bouton de barre de commande « Overflow »

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `Environment.CommandBarOptionsMouseDownBackgroundBegin`<br />(Points de dégradé pour ce jeton ne pas utilisé dans l’interface utilisateur à thème.) |
| Premier plan (glyphe) | `Environment.CommandBarOptionsMouseDownGlyph` |

## <a name="document-windows"></a>Fenêtres de document
Il est inutile de répliquer les fenêtres de document, car elles sont fournies par l’environnement Visual Studio. Toutefois, vous pouvez décider d’exploiter les couleurs utilisées dans les fenêtres de document, afin que votre interface utilisateur apparaisse toujours cohérente avec cette partie de l’environnement Visual Studio.

Lorsque vous utilisez des jetons de couleur de fenêtre de document, veillez à les utiliser uniquement pour les éléments similaires et toujours par paires. Si vous ne le faites, vous pouvez obtenir des résultats inattendus dans votre interface utilisateur.

### <a name="document-window-frames"></a>Frames de fenêtre de document
Les fenêtres de document peuvent être ancrées dans l’IDE ou flottantes dans une fenêtre distincte. Quand une fenêtre de document flotte en dehors de l’IDE, il toujours se trouve dans une zone de configuration de document et a en arrière-plan, bordure, le texte et les couleurs d’onglet sont les mêmes que lorsqu’il fait partie de l’IDE. Toutefois, le document se trouve à l’intérieur d’un cadre qui a ses propres couleurs d’arrière-plan, de bordure et de texte. Quand les fenêtres d’outil sont ancrées dans la zone de configuration de document, elles héritent le comportement et la couleur de leurs onglets des noms de jeton de fenêtre de document.

![Fenêtre de document ancrée (ligne rouge)](../../extensibility/ux-guidelines/media/0303-065_dockeddocumentwindowredline.png "0303-065_DockedDocumentWindowRedline")<br />Fenêtre de document ancrée (ligne rouge)

![Fenêtre de document flottante (ligne rouge)](../../extensibility/ux-guidelines/media/0303-066_floatingdocumentwindowredline.png "0303-066_FloatingDocumentWindowRedline")<br />Fenêtre de document flottante (ligne rouge)

| Utilisez... | N’utilisez pas... |
| --- | --- |
| ... n’importe où vous créez l’interface utilisateur que vous souhaitez faire correspondre la fenêtre de document. | ... pour toute interface utilisateur que vous ne souhaitez automatiquement changer si l’interpréteur de commandes a une mise à jour de thème. |

**Fenêtre de document ancrés ou flottants : état par défaut**

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | Dépend du type de document |
| Premier plan (texte) | Dépend du type de document |
| Bordure | `Environment.ToolWindowBorder` |

**Ayant le focus, flottante frame de fenêtre de document : état par défaut**

![Par défaut le focus, flottante frame de fenêtre de document](../../extensibility/ux-guidelines/media/0303-067_framefocused.png "0303-067_FrameFocused")<br />Par défaut le focus, flottante frame de fenêtre de document

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `Environment.ToolWindowFloatingFrame` |
| Premier plan (texte) | `Environment.ToolWindowFloatingFrame` |
| Premier plan (glyphe) | `Environment.RaftedWindowButtonActiveGlyph` |
| Bordure | `Environment.MainWindowActiveDefaultBorder` |
| Bordure (glyphe) | `Environment.RaftedWindowButtonActiveBorder`<br />(Défini sur transparent) |

**Frame de fenêtre de document flottante inactif : état par défaut**

![Frame de fenêtre de document inactif, flottante par défaut](../../extensibility/ux-guidelines/media/0303-068_frameunfocused.png "0303-068_FrameUnfocused")<br />Par défaut du frame de fenêtre de document flottante inactif

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `Environment.ToolWindowFloatingFrameInactive` |
| Premier plan (texte) | `Environment.ToolWindowFloatingFrameInactive` |
| Premier plan (glyphe) | `Environment.RaftedWindowButtonInactiveGlyph` |
| Bordure | `Environment.MainWindowInactiveBorder` |
| Bordure (glyphe) | `Environment.RaftedWindowButtonInactiveBorder`<br />(Défini sur transparent) |

**Ayant le focus, flottante frame de fenêtre de document : placez le curseur état**

![Ayant le focus, flottante frame de fenêtre de document au pointage](../../extensibility/ux-guidelines/media/0303-069_framefocusedhover.png "0303-069_FrameFocusedHover")<br />Ayant le focus, flottante frame de fenêtre de document au pointage

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan (glyphe) | `Environment.RaftedWindowButtonHoverActive` |
| Premier plan (glyphe) | `Environment.RaftedWindowButtonHoverActiveGlyph` |
| Bordure (glyphe) | `Environment.RaftedWindowButtonHoverActiveBorder` |

**Frame de fenêtre de document flottante inactif : placez le curseur état**

![Frame de fenêtre de document flottante inactif au pointage](../../extensibility/ux-guidelines/media/0303-070_frameunfocusedhover.png "0303-070_FrameUnfocusedHover")<br />Frame de fenêtre de document flottante inactif au pointage

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan (glyphe) | `EnvironmentRaftedWindowButtonHoverInactive` |
| Premier plan (glyphe) | `Environment.RaftedWindowButtonHoverInactiveGlyph` |
| Bordure (glyphe) | `Environment.RaftedWindowButtonHoverInactiveBorder` |

**Ayant le focus, flottante frame de fenêtre de document : état enfoncé**

![Ayant le focus, flottante frame de fenêtre de document sur Presse](../../extensibility/ux-guidelines/media/0303-071_framefocusedpressed.png "0303-071_FrameFocusedPressed")<br />Ayant le focus, flottante frame de fenêtre de document sur Presse

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan (glyphe) | `Environment.RaftedWindowButtonDown` |
| Premier plan (glyphe) | `Environment.RaftedWindowButtonDownGlyph` |
| Bordure (glyphe) | `Environment.RaftedWindowButtonDownBorder` |

### <a name="document-tabs"></a>Onglets de document
Les onglets de document figurent dans le canal d’onglet pour indiquer quels documents sont actuellement ouverts, ainsi que celui qui correspond au document actuellement sélectionné ou actif. Les fenêtres d’outil peuvent également être ancrées dans le canal d’onglet de document, si l’utilisateur les y place. Dans ce cas, elles utilisent les mêmes couleurs d’onglet que celles des fenêtres de document. Si vous créez une interface utilisateur que vous voulez toujours faire correspondre aux couleurs de fenêtre de document (mises à jour du thème comprises ou si de nouveaux thèmes sont installés), alors référencez ces jetons de couleur.

![Onglets de document (ligne rouge)](../../extensibility/ux-guidelines/media/0303-072_documenttabredline.png "0303-072_DocumentTabRedline")<br />Onglets de document (ligne rouge)

| Utilisez... | N’utilisez pas... |
| --- | --- |
| ... n’importe où vous créez l’interface utilisateur que vous souhaitez correspondent à des onglets de document et récupère automatiquement mises à jour de thème ou de nouvelles couleurs de thème. | ... pour toute interface utilisateur que vous ne souhaitez pas modifier automatiquement quand l’interpréteur de commandes a un thème à mettre à jour. |

#### <a name="open-document-tabs"></a>Onglets de document ouvert
Chaque document ouvert possède un onglet dans le canal d’onglet de document qui affiche son nom. Les documents peuvent être soit sélectionnés, soit ouverts en arrière-plan et leurs onglets reflètent ces états :

- L’onglet sélectionné représente le document actuellement affiché dans la zone de configuration de document. Un onglet sélectionné a une bordure de document qui s’étend sur le bord supérieur de la zone de configuration de document.

- Les onglets d’arrière-plan sont les onglets de document qui ne sont pas l’onglet actuellement sélectionné. Une fois que vous cliquez dessus, ils deviennent l’onglet sélectionné et acquièrent toutes les couleurs d’arrière-plan, de bordure et de texte de ces noms de jeton.

![Open document tab (redline)](../../extensibility/ux-guidelines/media/0303-073_opendocumenttabredline.png "0303-073_OpenDocumentTabRedline")<br />Onglet de document ouvert (ligne rouge)

| Utilisez... | N’utilisez pas... |
| --- | --- |
| ... lorsque vous créez des onglets de document personnalisées. | ... pour les onglets provisoires (version préliminaire). |
| | ... pour toute interface utilisateur que vous ne souhaitez pas modifier automatiquement si l’interpréteur de commandes comporte une mise à jour de thème. |

**Onglet de document sélectionné, avec focus**

![Sélectionnée, le focus d’onglet de document](../../extensibility/ux-guidelines/media/0303-074_selectedtabfocused.png "0303-074_SelectedTabFocused")<br />Onglet de document sélectionné, avec focus

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `Environment.FileTabSelectedGradientTop`<br />(Points de dégradé pour ce jeton ne pas utilisé dans l’interface utilisateur à thème.) |
| Premier plan (texte) | `Environment.FileTabSelectedText` |
| Bordure | `Environment.FileTabSelectedBorder`<br />(Défini sur la même couleur comme arrière-plan). |
| Bordure de document | `Environment.FileTabDocumentBorderBackground` |

**Onglet de document sélectionné, sans focus**

![Onglet de document sélectionné, sans focus](../../extensibility/ux-guidelines/media/0303-075_selectedtabunfocused.png "0303-075_SelectedTabUnfocused")<br />Onglet de document sélectionné, sans focus

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `Environment.FileTabInactiveGradientTop`<br />(Points de dégradé pour ce jeton ne pas utilisé dans l’interface utilisateur à thème.) |
| Premier plan (texte) | `Environment.FileTabInactiveText` |
| Bordure | `Environment.FileTabInactiveBorder`<br />(Défini sur la même couleur comme arrière-plan). |
| Bordure de document | `Environment.FileTabInactiveDocumentBorderBackground` |

**Onglet de document en arrière-plan : état par défaut**

![Onglet de document en arrière-plan par défaut](../../extensibility/ux-guidelines/media/0303-076_backgroundtab.png "0303-076_BackgroundTab")<br />Onglet de document en arrière-plan par défaut

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `Environment.FileTabBackground` |
| Premier plan (texte) | `Environment.FileTabText` |
| Bordure | `Environment.FileTabBorder`<br />(Défini sur la même couleur comme arrière-plan). |

**Onglet de document en arrière-plan : placez le curseur état**

![Onglet de document en arrière-plan au pointage](../../extensibility/ux-guidelines/media/0303-077_backgroundtabhover.png "0303-077_BackgroundTabHover")<br />Onglet de document en arrière-plan au pointage

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `Environment.FileTabHotGradientTop`<br />(Points de dégradé pour ce jeton ne pas utilisé dans l’interface utilisateur à thème.) |
| Premier plan (texte) | `Environment.FileTabHotText` |
| Bordure | `Environment.FileTabHotBorder`<br />(Défini sur la même couleur comme arrière-plan). |

#### <a name="preview-tab"></a>Onglet d’aperçu
Également appelé un onglet « provisoire ». L’onglet d’aperçu apparaît du côté droit du canal d’onglet de document quand l’utilisateur clique sur un élément dans la fenêtre Outil de l’Explorateur de solutions. Il sert d’aperçu du document et donne également à l’utilisateur la possibilité de laisser le document ouvert sur le côté gauche du canal d’onglet de document. Une seul onglet d’aperçu peut être ouvert à la fois. Les onglets d’aperçu possèdent deux états, arrière-plan et sélectionné, comme les onglets ouverts, et leur état actif peut être avec ou sans focus.

![Onglet d’aperçu (ligne rouge)](../../extensibility/ux-guidelines/media/0303-078_previewtabredline.png "0303-078_PreviewTabRedline")<br />Onglet d’aperçu (ligne rouge)

| Utilisez... | N’utilisez pas... |
| --- | --- |
| ... n’importe où vous créez provisoire afficher un aperçu et souhaitez certains élément correspond à la couleur d’onglet Aperçu actuelle. | ... pour tout type de document ou d’onglet qui n’est pas provisoire (version préliminaire). |
| | ... pour toute interface utilisateur que vous ne souhaitez pas modifier automatiquement si l’interpréteur de commandes comporte une mise à jour de thème. |

**Onglet d’aperçu ciblé et sélectionné**

![Onglet d’aperçu sélectionné, focalisé,](../../extensibility/ux-guidelines/media/0303-079_previewtabfocused.png "0303-079_PreviewTabFocused")<br />Onglet d’aperçu ciblé et sélectionné

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `Environment.FileTabProvisionalSelectedActive` |
| Premier plan (texte) | `Environment.FileTabProvisionalSelectedActiveForeground` |
| Bordure | `Environment.FileTabProvisionalSelectedActiveBorder`<br />(Défini sur la même couleur comme arrière-plan). |
| Bordure de document | `Environment.FileTabProvisionalSelectedActiveBorder` |

**Onglet d’aperçu inactif, sélectionné**

![Onglet d’aperçu inactif, sélectionné](../../extensibility/ux-guidelines/media/0303-080_previewtabunfocused.png "0303-080_PreviewTabUnfocused")<br />Onglet d’aperçu inactif, sélectionné

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `Environment.FileTabProvisionalSelectedInactive` |
| Premier plan (texte) | `Environment.FileTabProvisionalSelectedInactiveForeground` |
| Bordure | `Environment.FileTabProvisionalSelectedInactiveBorder` |
| Bordure de document | `Environment.FileTabProvisionalSelectedInactiveBorder` |

**Onglet d’aperçu d’arrière-plan : état par défaut**

![Onglet d’aperçu d’arrière-plan par défaut](../../extensibility/ux-guidelines/media/0303-081_previewbackgroundtab.png "0303-081_PreviewBackgroundTab")<br />Onglet d’aperçu d’arrière-plan par défaut

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `Environment.FileTabProvisionalInactive` |
| Premier plan (texte) | `Environment.FileTabProvisionalInactiveForeground` |
| Bordure | `Environment.FileTabProvisionalInactiveBorder`<br />(Défini sur la même couleur comme arrière-plan). |

**Onglet d’aperçu d’arrière-plan : placez le curseur état**

![Onglet d’aperçu d’arrière-plan au pointage](../../extensibility/ux-guidelines/media/0303-082_previewbackgroundtabhover.png "0303-082_PreviewBackgroundTabHover")<br />Onglet d’aperçu d’arrière-plan au pointage

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `Environment.FileTabProvisionalHover` |
| Premier plan (texte) | `Environment.FileTabProvisionalHoverForeground` |
| Bordure | `Environment.FileTabProvisionalHoverBorder`<br />(Défini sur la même couleur comme arrière-plan). |

#### <a name="document-overflow-button"></a>Bouton de dépassement de capacité de document
Le bouton de dépassement de capacité de document est présent si un ou plusieurs documents sont ouverts, que l’espace vertical défini dans la configuration actuelle suffise ou non pour loger tous les onglets de document. Le menu de liste déroulante de dépassement de capacité de document, qui est contrôlé par le [barre de menu de commandes](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandMenus) couleurs, affiche une liste de tous les documents ouverts, visibles et masqués et les modifications de glyphe de dépassement de capacité selon que tous les documents ouverts sont affiché dans le canal d’onglet.

![Bouton de dépassement de capacité de document (ligne rouge)](../../extensibility/ux-guidelines/media/0303-083_overflowredline.png "0303-083_OverflowRedline")<br />Bouton de dépassement de capacité de document (ligne rouge)

| Utilisez... | N’utilisez pas... |
| --- | --- |
| ... lors de la création d’un bouton de dépassement de capacité de document personnalisées. | ... pour l’interface utilisateur qui n’est pas similaire à un bouton de dépassement de capacité. |
| | ... pour les boutons de dépassement de capacité de barre de commandes. |

**Bouton de dépassement de capacité de document : état par défaut**

![Bouton de dépassement de capacité de document par défaut](../../extensibility/ux-guidelines/media/0303-084_overflow.png "0303-084_Overflow")<br />Bouton de dépassement de capacité de document par défaut

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `Environment.DocWellOverflowButtonBackground` |
| Premier plan (glyphe) | `Environment.DocWellOverflowButtonGlyph` |
| Bordure | N/A |

**Bouton de dépassement de capacité de document : placez le curseur état**

![Bouton de dépassement de capacité de document au pointage](../../extensibility/ux-guidelines/media/0303-085_overflowhover.png "0303-085_OverflowHover")<br />Bouton de dépassement de capacité de document au pointage

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `Environment.DocWellOverflowButtonMouseOverBackground` |
| Premier plan (glyphe) | `Environment.DocWellOverflowButtonMouseOverGlyph` |
| Bordure | `Environment.DocWellOverflowButtonMouseOverBorder` |

**Bouton de dépassement de capacité de document : état enfoncé**

![Bouton de dépassement de capacité de document sur Presse](../../extensibility/ux-guidelines/media/0303-086_overflowpressed.png "0303-086_OverflowPressed")<br />Bouton de dépassement de capacité de document sur Presse

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `Environment.DocWellOverflowButtonMouseDownBackground` |
| Premier plan (glyphe) | `Environment.DocWellOverflowButtonMouseDownGlyph` |
| Bordure | `Environment.DocWellOverflowButtonMouseDownBorder` |

### <a name="tagging"></a>Étiquetage
Visual Studio prend en charge l’étiquetage, qui permet à un utilisateur de déclarer des mots clés pouvant faire l’objet d’une recherche à des fins de suivi. Par exemple, les chefs de projet et développeurs peuvent utiliser Team Foundation Server (TFS) pour étiqueter des éléments de travail. Les tableaux ci-dessous indiquent les noms de couleurs pour l’étiquette elle-même et le glyphe de l’icône de fermeture qui apparaît dans les états Pointage et Sélectionné.

![Balisage dans Visual Studio (ligne rouge)](../../extensibility/ux-guidelines/media/0303-176_taggingredline.png "0303-176_TaggingRedline")<br />Balisage dans Visual Studio (ligne rouge)

| Utilisez... | N’utilisez pas... |
| --- | --- |
| ... pour l’interface utilisateur qui prend en charge de balisage. | ... pour n’importe quel autre type d’interface utilisateur. |

#### <a name="tags"></a>Balises

**Balise : état par défaut**

![Balise par défaut](../../extensibility/ux-guidelines/media/0303-177_tag.png "0303-177_Tag")<br />Balise par défaut

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `Tag.Background` |
| Premier plan (texte) | `Tag.Background` |

**Balise : état de pointage**

![Étiquette au pointage](../../extensibility/ux-guidelines/media/0303-178_taghover.png "0303-178_TagHover")<br />Balise au pointage

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `Tag.HoverBackground` |
| Premier plan (texte) | `Tag.HoverBackgroundText` |

**Balise : état enfoncé**

![Enfoncé balise](../../extensibility/ux-guidelines/media/0303-179_tagpressed.png "0303-179_TagPressed")<br />Balise appuyé

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `Tag.PressedBackground` |
| Premier plan (texte) | `Tag.PressedBackgroundText` |

**Balise : état sélectionné**

![Sélectionné balise](../../extensibility/ux-guidelines/media/0303-180_tagselected.png "0303-180_TagSelected")<br />Étiquette sélectionnée

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `Tag.SelectedBackground` |
| Premier plan (texte) | `Tag.SelectedBackgroundText` |

#### <a name="close-times-tag-glyph"></a>Fermer (&times;) glyphe de balise

**Fermer (&times;) glyphe de balise : état par défaut**

![Par défaut de fermeture (&times;) glyphe de balise](../../extensibility/ux-guidelines/media/0303-181_tagglyph.png "0303-181_TagGlyph")<br />Par défaut de fermeture (&times;) glyphe de balise

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | N/A |
| Premier plan (glyphe) | `Tag.TagHoverGlyph` |

**Fermer (&times;) glyphe de balise : placez le curseur état**

![Fermer (&times;) étiquette glyphe au pointage](../../extensibility/ux-guidelines/media/0303-182_tagglyphhover.png "0303-182_TagGlyphHover")<br />Fermer (&times;) étiquette glyphe au pointage

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `Tag.TagHoverGlyphHoverBackground` |
| Premier plan (glyphe) | `Tag.TagHoverGlyphHover` |
| Bordure | `Tag.TagHoverGlyphHoverBorder` |

**Fermer (&times;) glyphe de balise : état enfoncé**

![Enfoncé fermer (&times;) glyphe de balise](../../extensibility/ux-guidelines/media/0303-183_tagglyphpressed.png "0303-183_TagGlyphPressed")<br />Enfoncé fermer (&times;) glyphe de balise

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `Tag.TagHoverGlyphPressedBackground` |
| Premier plan (glyphe) | `Tag.TagHoverGlyphPressed` |
| Bordure | `Tag.TagHoverGlyphPressedBorder` |

**Sélectionné la balise de fermeture (&times;) glyphe : état par défaut**

![Par défaut de la balise sélectionnée par la commande Fermer (&times;) glyphe](../../extensibility/ux-guidelines/media/0303-184_tagselected.png "0303-184_TagSelected")<br />Par défaut de la balise sélectionnée par la commande Fermer (&times;) glyphe

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | N/A |
| Premier plan (glyphe) | `Tag.TagSelectedGlyph` |

**Sélectionné la balise de fermeture (&times;) glyphe : placez le curseur état**

![Sélectionné la balise de fermeture (&times;) glyphe au pointage](../../extensibility/ux-guidelines/media/0303-185_tagselectedhover.png "0303-185_TagSelectedHover")<br />Sélectionné la balise de fermeture (&times;) glyphe au pointage

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `Tag.TagSelectedGlyphHoverBackground` |
| Premier plan (glyphe) | `Tag.TagSelectedGlyphHover` |
| Bordure | `Tag.TagSelectedGlyphHoverBorder` |

**Sélectionné la balise de fermeture (&times;) glyphe : état enfoncé**

![Sélectionnée, l’utilisateur appuie sur la balise de fermeture (&times;) glyphe](../../extensibility/ux-guidelines/media/0303-186_tagselectedpressed.png "0303-186_TagSelectedPressed")<br />Sélectionnée, l’utilisateur appuie sur la balise de fermeture (&times;) glyphe

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `Tag.TagSelectedGlyphPressedBackground` |
| Premier plan (glyphe) | `Tag.TagSelectedGlyphPressed` |
| Bordure | `Tag.TagSelectedGlyphPressedBorder` |

## <a name="tool-windows"></a>Fenêtres d’outil
Il est inutile de répliquer les fenêtres Outil, car elles sont fournies par l’environnement Visual Studio. Toutefois, vous pouvez décider d’exploiter les couleurs utilisées dans les fenêtres d’outil, afin que votre interface utilisateur apparaisse toujours cohérente avec cette partie de l’environnement Visual Studio.

![Fenêtre outil (ligne rouge)](../../extensibility/ux-guidelines/media/0303-087_toolwindowredline.png "0303-087_ToolWindowRedline")<br />Fenêtre outil (ligne rouge)

| Utilisez... | N’utilisez pas... |
| --- | --- |
| ... n’importe où vous créez l’interface utilisateur que vous souhaitez faire correspondre les fenêtres Outil. | ... pour toute interface utilisateur que vous ne souhaitez pas modifier automatiquement si l’interpréteur de commandes comporte une mise à jour de thème. |

### <a name="tool-window-frame"></a>Cadre de fenêtre Outil
Les fenêtres d’outil dans Visual Studio sont utilisées pour de nombreuses tâches différentes et peuvent exister dans différents états. Si une fenêtre Outil est ouverte, elle peut être affectée à l’un des quatre côtés de la zone de document. Les fenêtres d’outil peuvent également flotter en dehors de l’IDE, ce qui leur permet d’être repositionnées n’importe où sur l’écran de l’utilisateur. Les fenêtres flottantes se trouvent toujours par-dessus l’IDE. Enfin, les fenêtres d’outil peuvent être ancrées comme des fenêtres de document et elles apparaissent sous la forme d’un onglet dans la zone de configuration de document. Les fenêtres d’outil ancrées comme des fenêtres de document sont colorées en partie à l’aide des noms de jeton de fenêtre de document.

![Frame de fenêtre outil (ligne rouge)](../../extensibility/ux-guidelines/media/0303-088_toolwindowframeredline.png "0303-088_ToolWindowFrameRedline")<br />Frame de fenêtre outil (ligne rouge)

| Utilisez... | N’utilisez pas... |
| --- | --- |
| ... n’importe où vous créez l’interface utilisateur que vous souhaitez faire correspondre les fenêtres Outil. | ... pour toute interface utilisateur que vous ne souhaitez pas modifier automatiquement si l’interpréteur de commandes comporte une mise à jour de thème. |

**Fenêtre Outil ancrée**

![Fenêtre Outil ancrée](../../extensibility/ux-guidelines/media/0303-089_toolwindowdocked.png "0303-089_ToolWindowDocked")<br />Fenêtre Outil ancrée

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `Environment.ToolWindowBackground` |
| Bordure | `Environment.ToolWindowBorder` |

**Flottant, avec focus de fenêtre outil**

![Flottant, avec focus fenêtre outil](../../extensibility/ux-guidelines/media/0303-090_toolwindowfocused.png "0303-090_ToolWindowFocused")<br />Flottant, avec focus de fenêtre outil

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `Environment.ToolWindowBackground` |
| Bordure | `Environment.MainWindowActiveDefaultBorder` |

**Flottant, fenêtre outil inactif**

![Fenêtre d’outil flottante, sans focus](../../extensibility/ux-guidelines/media/0303-091_toolwindowunfocused.png "0303-091_ToolWindowUnfocused")<br />Flottant, fenêtre outil inactif

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `Environment.ToolWindowBackground` |
| Bordure | `Environment.MainWindowInactiveBorder` |

### <a name="toolbox-like-windows"></a>Type de la boîte à outils windows
La boîte à outils est une des fenêtres Outil commune fréquemment utilisées dans Visual Studio. Il est essentiellement un contrôle d’arborescence avec un thème spécial et le style appliqué.

![Fenêtre de boîte à outils-type (ligne rouge)](../../extensibility/ux-guidelines/media/0303-189_toolboxredline.png "0303-189_ToolboxRedline")<br />Fenêtre de boîte à outils-type (ligne rouge)

| Utilisez... | N’utilisez pas... |
| --- | --- |
| ... lorsque vous concevez une fenêtre outil qui vous voulez toujours cohérente avec la boîte à outils de l’interpréteur de commandes. | ... pour tout ce qui n’est pas similaire à la boîte à outils de l’interface utilisateur, ou si vous ne savez pas si votre interface utilisateur aura des problèmes si la modification des couleurs de la boîte à outils de l’interpréteur de commandes. |

**Nœuds de la boîte à outils : état par défaut**

![Nœud parent de boîte à outils par défaut](../../extensibility/ux-guidelines/media/0303-190_toolboxparentnode.png "0303-190_ToolboxParentNode")<br />Nœud parent de boîte à outils par défaut

![Nœud enfant de boîte à outils par défaut](../../extensibility/ux-guidelines/media/0303-191_toolboxchildnode.png "0303-191_ToolboxChildNode")<br />Nœud enfant de boîte à outils par défaut

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `Environment.ToolboxContent`<br />(En-têtes) |
| Présentation | `Environment.ToolWindowBackground`<br />(Les éléments individuels ou fenêtre entière si aucun contrôle disponible) |
| Bordure | None |
| Premier plan (glyphe) | `Environment.ToolboxContent` |
| Premier plan (texte) | `Environment.ToolboxContent` |

**Nœuds enfants de boîte à outils : placez le curseur état**

![Nœud enfant de boîte à outils au pointage](../../extensibility/ux-guidelines/media/0303-192_toolboxchildnodehover.png "0303-192_ToolboxChildNodeHover")<br />Nœud enfant de boîte à outils au pointage

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `Environment.ToolboxContentMouseOver`<br />(Pour les éléments individuels uniquement) |
| Bordure | None |
| Premier plan (texte) | `Environment.ToolboxContentMouseOver`<br />(Pour les éléments individuels uniquement) |

**Les nœuds de la boîte à outils sélectionnés : état de focus**

![Nœud parent de boîte à outils sélectionné, focalisé,](../../extensibility/ux-guidelines/media/0303-193_toolboxparentnodefocused.png "0303-193_ToolboxParentNodeFocused")<br />Nœud parent de boîte à outils ayant le focus, sélectionné

![Nœud enfant de boîte à outils sélectionné, focalisé,](../../extensibility/ux-guidelines/media/0303-194_toolboxchildnodefocused.png "0303-194_ToolboxChildNodeFocused")<br />Nœud enfant de boîte à outils ayant le focus, sélectionné

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `TreeView.SelectedItemActive`<br />À partir de la catégorie [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |
| Bordure | `TreeView.FocusVisualBorder`<br />À partir de la catégorie [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |
| Premier plan (glyphe) | `TreeView.SelectedItemActive`<br />À partir de la catégorie [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |
| Premier plan (texte) | `TreeView.SelectedItemActive`<br />À partir de la catégorie [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |

**Les nœuds de la boîte à outils sélectionnés : état inactif**

![Nœud parent de boîte à outils sélectionné, sans focus](../../extensibility/ux-guidelines/media/0303-195_toolboxparentnodeunfocused.png "0303-195_ToolboxParentNodeUnfocused")<br />Nœud parent de boîte à outils sélectionné, sans focus

![Nœud enfant de boîte à outils sélectionné, sans focus](../../extensibility/ux-guidelines/media/0303-196_toolboxchildnodeunfocused.png "0303-196_ToolboxChildNodeUnfocused")<br />Nœud enfant de boîte à outils sélectionné, sans focus

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `TreeView.SelectedItemInactive`<br />À partir de la catégorie [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |
| Bordure | None |
| Premier plan (glyphe) | `TreeView.SelectedItemInactive`<br />À partir de la catégorie [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |
| Premier plan (texte) | `TreeView.SelectedItemInactive`<br />À partir de la catégorie [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |

### <a name="tool-window-title-bar"></a>Barre de titre de fenêtre Outil
La bordure de barre de titre n’est pas une véritable bordure, il est une ligne épaisse en haut de la barre de titre. Il n’a pas un nom de jeton pour son état inactif.

![Barre de titre de fenêtre outil (ligne rouge)](../../extensibility/ux-guidelines/media/0303-092_toolwindowtitlebarredline.png "0303-092_ToolWindowTitleBarRedline")<br />Barre de titre de fenêtre outil (ligne rouge)

| Utilisez... | N’utilisez pas... |
| --- | --- |
| ... n’importe où vous créez l’interface utilisateur que vous souhaitez faire correspondre les fenêtres Outil. | ... pour toute interface utilisateur que vous ne souhaitez pas modifier automatiquement si l’interpréteur de commandes comporte une mise à jour de thème. |

**Barre de titre avec focus**

![Barre de titre avec focus](../../extensibility/ux-guidelines/media/0303-093_titlebarfocused.png "0303-093_TitleBarFocused")<br />Barre de titre avec focus

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `Environment.TitleBarActiveGradientBegin`<br />(Points de dégradé pour ce jeton ne pas utilisé dans l’interface utilisateur à thème.) |
| Premier plan (texte) | `Environment.TitleBarActiveText` |
| Bordure | `Environment.TitleBarActiveBorder`<br />(Défini sur la même couleur comme arrière-plan). |
| Faire glisser la poignée | `Environment.TitleBarDragHandleActive` |

**Barre de titre inactive**

![Barre de titre inactive](../../extensibility/ux-guidelines/media/0303-094_titlebarunfocused.png "0303-094_TitleBarUnfocused")<br />Barre de titre sans focus

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `Environment.TitleBarInactiveGradientBegin`<br />(Points de dégradé pour ce jeton ne pas utilisé dans l’interface utilisateur à thème.) |
| Premier plan (texte) | `Environment.TitleBarInactiveText` |
| Bordure | N/A |
| Faire glisser la poignée | `Environment.TitleBarDragHandle` |

#### <a name="tool-window-title-bar-buttons"></a>Boutons de barre de titre de fenêtre outil
![Bouton de la barre de titre (ligne rouge)](../../extensibility/ux-guidelines/media/0303-095_titlebarbuttonredline.png "0303-095_TitleBarButtonRedline")<br />Bouton de la barre de titre (ligne rouge)

| Utilisez... | N’utilisez pas... |
| --- | --- |
| ... pour les boutons qui apparaissent dans l’interface utilisateur qui utilise des jetons de couleur dans les barres de titre de fenêtre outil. | ... pour les boutons qui apparaissent dans d’autres emplacements. |
| | ... dans n’importe quelle combinaison arrière-plan/premier plan autre que celle spécifiée. |

**Boutons de barre de titre de focus : état par défaut**

![Par défaut, les boutons de barre de titre de focus](../../extensibility/ux-guidelines/media/0303-096_titlebarbuttonfocused.png "0303-096_TitleBarButtonFocused")<br />Par défaut, les boutons de barre de titre avec focus

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | N/A |
| Premier plan (glyphe) | `Environment.ToolWindowButtonActiveGlyph` |
| Bordure | N/A |

**Boutons de barre de titre inactif : état par défaut**

![Par défaut, les boutons de barre de titre inactif](../../extensibility/ux-guidelines/media/0303-097_titlebarbuttonunfocused.png "0303-097_TitleBarButtonUnfocused")<br />Par défaut, les boutons de barre de titre sans focus

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | N/A |
| Premier plan (glyphe) | `Environment.ToolWindowButtonInactiveGlyph` |
| Bordure | N/A |

**Boutons de barre de titre de focus : pointez l’état**

![Boutons de barre de titre actif au pointage](../../extensibility/ux-guidelines/media/0303-098_titlebarbuttonfocusedhover.png "0303-098_TitleBarButtonFocusedHover")<br />Boutons de barre de titre avec focus au pointage

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `Environment.ToolWindowButtonHoverActive` |
| Premier plan (glyphe) | `Environment.ToolWindowButtonHoverActiveGlyph` |
| Bordure | `Environment.ToolWindowButtonHoverActiveBorder` |

**Boutons de barre de titre inactif : placez le curseur état**

![Boutons de barre de titre inactif au pointage](../../extensibility/ux-guidelines/media/0303-099_titlebarbuttonunfocusedhover.png "0303-099_TitleBarButtonUnfocusedHover")<br />Boutons de barre de titre inactif au pointage

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `Environment.ToolWindowButtonHoverInactive` |
| Premier plan (glyphe) | `Environment.ToolWindowButtonHoverInactiveGlyph` |
| Bordure | `Environment.ToolWindowButtonHoverInactiveBorder` |

**Boutons de barre de titre de focus : état enfoncé**

![Appuyez sur consacré aux boutons de barre de titre](../../extensibility/ux-guidelines/media/0303-100_titlebarbuttonfocusedpressed.png "0303-100_TitleBarButtonFocusedPressed")<br />Boutons de barre de titre avec focus sur appuyez sur

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `Environment.ToolWindowButtonDown` |
| Premier plan (glyphe) | `Environment.ToolWindowButtonDownActiveGlyph` |
| Bordure | `Environment.ToolWindowButtonDownBorder` |

**Boutons de barre de titre inactif : état enfoncé**

![Boutons de barre de titre inactif sur press](../../extensibility/ux-guidelines/media/0303-101_titlebarbuttonunfocusedpressed.png "0303-101_TitleBarButtonUnfocusedPressed")<br />Boutons de barre de titre inactif sur appuyez sur

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `Environment.ToolWindowButtonDown` |
| Premier plan (glyphe) | `Environment.ToolWindowButtonDownInactiveGlyph` |
| Bordure | `Environment.ToolWindowButtonDownBorder` |

### <a name="tool-window-tabs"></a>Onglets de fenêtre Outil
![Onglet fenêtre outil (ligne rouge)](../../extensibility/ux-guidelines/media/0303-102_toolwindowtabredline.png "0303-102_ToolWindowTabRedline")<br />Onglet fenêtre outil (ligne rouge)

| Utilisez... | N’utilisez pas... |
| --- | --- |
| ... n’importe où vous créez l’interface utilisateur que vous souhaitez faire correspondre les fenêtres Outil. | ... pour toute interface utilisateur que vous ne souhaitez pas modifier automatiquement si l’interpréteur de commandes comporte une mise à jour de thème. |

**Onglet fenêtre outil sélectionné, avec focus**

![Sélectionnée, le focus d’onglet de fenêtre outil](../../extensibility/ux-guidelines/media/0303-103_toolwindowtabfocused.png "0303-103_ToolWindowTabFocused")<br />Onglet de fenêtre Outil sélectionné, avec focus

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `Environment.ToolWindowTabSelectedTab` |
| Premier plan (texte) | `Environment.ToolWindowTabSelectedActiveText` |
| Bordure | `Environment.ToolWindowTabSelectedBorder`<br />(Défini sur la même couleur comme arrière-plan). |

**Onglet fenêtre outil sélectionné, sans focus**

![Onglet fenêtre outil sélectionné, sans focus](../../extensibility/ux-guidelines/media/0303-104_toolwindowtabunfocused.png "0303-104_ToolWindowTabUnfocused")<br />Onglet de fenêtre Outil sélectionné, sans focus

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `Environment.ToolWindowTabSelectedTab` |
| Premier plan (texte) | `Environment.ToolWindowTabSelectedText` |
| Bordure | `Environment.ToolWindowTabSelectedBorder`<br />(Défini sur la même couleur comme arrière-plan). |

**Onglet de fenêtre outil arrière-plan : état par défaut**

![Onglet de fenêtre outil arrière-plan par défaut](../../extensibility/ux-guidelines/media/0303-105_toolwindowbackgroundtab.png "0303-105_ToolWindowBackgroundTab")<br />Onglet de fenêtre outil arrière-plan par défaut

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `Environment.ToolWindowTabGradientBegin`<br />`Environment.ToolWindowTabGradientEnd`<br />(Dégradé sont définis sur la même valeur de couleur dans Visual Studio 2013.) |
| Premier plan (texte) | `Environment.ToolWindowTabText` |
| Bordure | `Environment.ToolWindowTabBorder` |

**Onglet de fenêtre outil arrière-plan : placez le curseur état**

![Onglet de fenêtre outil arrière-plan au pointage](../../extensibility/ux-guidelines/media/0303-106_toolwindowbackgroundtabhover.png "0303-106_ToolWindowBackgroundTabHover")<br />Onglet de fenêtre Outil d’arrière-plan au pointage

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `Environment.ToolWindowTabMouseOverBackgroundBegin`<br />`Environment.ToolWindowTabMouseOverBackgroundEnd`<br />(Dégradé sont définis sur la même valeur de couleur dans Visual Studio 2013.) |
| Premier plan (texte) | `Environment.ToolWindowTabMouseOverText` |
| Bordure | `Environment.ToolWindowTabMouseOverBorder`<br />(Défini sur la même couleur comme arrière-plan). |

### <a name="auto-hide-tabs"></a>Onglets à masquage automatique

![Onglets de masquage automatique (ligne rouge)](../../extensibility/ux-guidelines/media/0303-107_autohideredline.png "0303-107_AutoHideRedline")onglets de masquage automatique (ligne rouge)

| Utilisez... | N’utilisez pas... |
| --- | --- |
| ... n’importe où vous créez l’interface utilisateur que vous souhaitez faire correspondre les onglets de la fenêtre outil masqués automatiquement. | ... pour toute interface utilisateur que vous ne souhaitez pas modifier automatiquement si l’interpréteur de commandes comporte une mise à jour de thème. |

**Onglets à masquage automatique : état par défaut**

![Onglet de masquage automatique par défaut](../../extensibility/ux-guidelines/media/0303-108_autohidetab.png "0303-108_AutoHideTab")<br />Onglet à masquage automatique par défaut

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `Environment.AutoHideTabBackgroundBegin`<br />(Points de dégradé pour ce jeton ne pas utilisé dans l’interface utilisateur à thème.) |
| Premier plan (texte) | `Environment.AutoHideTabText` |
| Bordure | `Environment.AutoHideTabBorder` |

**Onglets à masquage automatique : état de pointage**

![Onglet de masquage automatique de survol](../../extensibility/ux-guidelines/media/0303-109_autohidetabhover.png "0303-109_AutoHideTabHover")<br />Masquer automatiquement l'onglet au pointage

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Présentation | `Environment.AutoHideTabMouseOverBackgroundBegin`<br />(Points de dégradé pour ce jeton ne pas utilisé dans l’interface utilisateur à thème.) |
| Premier plan (texte) | `Environment.AutoHideTabMouseOverText` |
| Bordure | `Environment.AutoHideTabMouseOverBorder` |
