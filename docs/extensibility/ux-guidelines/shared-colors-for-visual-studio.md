---
title: Couleurs partagées pour Visual Studio | Microsoft Docs
description: Apprenez à utiliser des éléments et des thèmes Visual Studio Shell courants pour concevoir votre propre interface utilisateur personnalisée qui est cohérente avec l’environnement Visual Studio.
ms.date: 04/26/2017
ms.topic: reference
ms.assetid: 8d11b9a0-6175-4f2e-8e7f-79daee1bfd41
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 262f90fb8d03a9404cdbba8b942e90f6fe6fd3aa
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903968"
---
# <a name="shared-colors-for-visual-studio"></a>Couleurs partagées pour Visual Studio
Quand vous concevez une interface utilisateur qui utilise des éléments de Shell Visual Studio communs ou si vous souhaitez que votre élément d’interface soit cohérent avec des fonctionnalités similaires, utilisez des noms de jeton existants dans les fichiers de définition de package pour choisir et assigner des couleurs. Ainsi, votre interface utilisateur reste cohérente avec l’environnement Visual Studio global et elle se met à jour automatiquement quand des thèmes sont ajoutés ou mis à jour.

Cet article décrit les éléments d’interface utilisateur communs et les noms de jeton qu’ils utilisent, que vous pouvez référencer pour créer une interface utilisateur similaire. Pour plus d’informations sur la façon d’accéder à ces jetons de couleur, consultez [The VSColor Service](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService).

Assurez-vous d’utiliser correctement les noms de jeton :

- **Utilisez des noms de jeton basés sur la fonction et non sur la couleur elle-même.** Les couleurs partagées communes sont associées à des éléments d’interface spécifiques et uniquement destinées à être utilisées pour des fonctionnalités identiques ou similaires. Par exemple, ne réutilisez pas la couleur d’une zone de liste modifiable enfoncée pour une animation de progression en rotation juste parce que vous aimez la couleur. Les fonctions de la zone de liste déroulante et de l’animation sont différentes, et si la couleur associée à la zone de liste déroulante change, il se peut qu’elle ne soit plus une couleur appropriée pour votre élément d’animation. Une utilisation cohérente des couleurs permet de guider vos utilisateurs et d’éviter toute confusion.

- **Associez correctement les couleurs d’arrière-plan et de texte.** Les couleurs d’arrière-plan destinées à être utilisées avec du texte possèdent une couleur de texte associée. N’utilisez pas de couleurs de texte autres que celles spécifiées pour l’arrière-plan. S’il n’existe pas de couleur de texte associée, n’utilisez pas cette couleur d’arrière-plan pour les surfaces sur lesquelles vous prévoyez d’afficher du texte. D’autres combinaisons de texte et de couleurs d’arrière-plan peuvent entraîner une interface illisible.

- **Utilisez des couleurs de contrôle appropriées à leur emplacement.** Dans certains États, certains contrôles Visual Studio n’ont pas de couleurs de bordure et d’arrière-plan distinctes. Au lieu de cela, ils sélectionnent ces couleurs dans les surfaces qui se trouvent derrière. Veillez à toujours utiliser les noms de jeton qui conviennent à l’emplacement où vous placez le contrôle.

> [!IMPORTANT]
> N’utilisez pas de jetons trouvés dans les catégories « page de démarrage » ou « cidre ».

## <a name="common-shared-controls"></a>Contrôles partagés communs

Quand vous utilisez une barre de commandes Visual Studio standard dans votre fonctionnalité, vous avez accès aux contrôles de l’interpréteur de commandes. Vous ne devez pas recréer un modèle pour ces contrôles communs. Toutefois, si vous avez besoin de créer une barre de commandes personnalisée, vous pouvez avoir besoin de générer des contrôles personnalisés également. Dans ce cas, assurez-vous d’utiliser des noms de jeton corrects pour chacun des contrôles suivants afin que votre interface utilisateur soit cohérente avec le reste de Visual Studio.

### <a name="button-controls"></a>Contrôles boutons

![Ligne rouge de contrôle Button](../../extensibility/ux-guidelines/media/0303-155_buttoncontrolredline.png "0303-155_ButtonControlRedline")

| Utilisez... | N’utilisez pas... |
| --- | --- |
| ... pour les boutons de la zone document que vous souhaitez intégrer aux thèmes Visual Studio (clair, foncé, bleu ou un thème contraste élevé système). | ... pour les boutons qui s’affichent sur un arrière-plan personnalisé qui ne fait pas partie d’un thème Visual Studio. |

**Bouton : état standard**

![Bouton standard](../../extensibility/ux-guidelines/media/03.03.Button.Standard.png "03.03. Button. standard")<br />Bouton standard

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Bouton | `CommonControls.Button` |
| Bordure de bouton | `CommonControls.ButtonBorder` |

**Button : état par défaut**

![Bouton par défaut](../../extensibility/ux-guidelines/media/03.03.Button.Default.png "03.03. Button. default")<br />Bouton par défaut

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Bouton | `CommonControls.ButtonDefault` |
| Bordure de bouton | `CommonControls.ButtonBorderDefault` |

**Bouton : état désactivé**

![Bouton désactivé](../../extensibility/ux-guidelines/media/03.03.Button.Disabled.png "03.03. Button. Disabled")<br />Bouton désactivé

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Bouton | `CommonControls.ButtonDisabled` |
| Bordure de bouton | `CommonControls.ButtonBorderDisabled` |

**Bouton : état sensitif**

![Bouton au pointage](../../extensibility/ux-guidelines/media/03.03.Button.hover.png "03.03. Button. pointage")<br />Bouton au pointage

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Bouton | `CommonControls.ButtonHover` |
| Bordure de bouton | `CommonControls.ButtonBorderHover` |

**Bouton : état enfoncé**

![Bouton enfoncé](../../extensibility/ux-guidelines/media/03.03.Button.Pressed.png "03.03. Button. enfoncé")<br />Bouton enfoncé

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Bouton | `CommonControls.ButtonPressed` |
| Bordure de bouton | `CommonControls.ButtonBorderPressed` |

**Button : état ciblé**

![Bouton ayant le focus](../../extensibility/ux-guidelines/media/03.03.Button.Focused.png "03.03. Button. Focused")<br />Bouton ayant le focus

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Bouton | `CommonControls.ButtonFocused` |
| Bordure de bouton | `CommonControls.ButtonBorderFocused` |

### <a name="check-box-controls"></a>Contrôles de case à cocher
![Case à cocher (ligne rouge)](../../extensibility/ux-guidelines/media/0303-161_checkboxredline.png "0303-161_CheckboxRedline")<br />Case à cocher (ligne rouge)

| Utilisez... | N’utilisez pas... |
| --- | --- |
| ... pour les contrôles de case à cocher contenus dans la zone de document. | ... pour toute interface utilisateur qui n’est pas un contrôle de case à cocher. |

**Case à cocher : état par défaut**

![Case à cocher](../../extensibility/ux-guidelines/media/0303-162_checkbox.png "0303-162_Checkbox")<br />Case à cocher par défaut

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `CommonControls.CheckBoxBackground` |
| Bordure | `CommonControls.CheckBoxBorder` |
| Texte | `CommonControls.CheckBoxText` |
| Glyphe | `CommonControls.CheckBoxGlyph` |

**Case à cocher : état désactivé**

![Case à cocher désactivée](../../extensibility/ux-guidelines/media/0303-163_checkboxdisabled.png "0303-163_CheckboxDisabled")<br />Case à cocher désactivée

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `CommonControls.CheckBoxBackgroundDisabled` |
| Bordure | `CommonControls.CheckBoxBorderDisabled` |
| Texte | `CommonControls.CheckBoxTextDisabled` |
| Glyphe | `CommonControls.CheckBoxGlyphDisabled` |

**Case à cocher : état pointé**

 ![Case à cocher au pointage](../../extensibility/ux-guidelines/media/0303-164_checkboxhover.png "0303-164_CheckboxHover")<br />Case à cocher au pointage

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `CommonControls.CheckBoxBackgroundHover` |
| Bordure | `CommonControls.CheckBoxBorderHover` |
| Texte | `CommonControls.CheckBoxTextHover` |
| Glyphe | `CommonControls.CheckBoxGlyphHover` |

**Case à cocher : état enfoncé**

![Case à cocher activée](../../extensibility/ux-guidelines/media/0303-165_checkboxpressed.png "0303-165_CheckboxPressed")<br />Case à cocher activée

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `CommonControls.CheckBoxBackgroundPressed` |
| Bordure | `CommonControls.CheckBoxBorderPressed` |
| Texte | `CommonControls.CheckBoxTextPressed` |
| Glyphe | `CommonControls.CheckBoxGlyphPressed` |

**Case à cocher : état ciblé**

![Case à cocher prioritaire](../../extensibility/ux-guidelines/media/0303-166_checkboxfocused.png "0303-166_CheckboxFocused")<br />Case à cocher prioritaire

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `CommonControls.CheckBoxBackgroundFocused` |
| Bordure | `CommonControls.CheckBoxBorderFocused` |
| Texte | `CommonControls.CheckBoxTextFocused` |
| Glyphe | `CommonControls.CheckBoxGlyphFocused` |

### <a name="drop-downs-and-combo-boxes"></a>Listes déroulantes et zones de liste modifiable
![Zone de liste déroulante/zone de liste déroulante (ligne rouge)](../../extensibility/ux-guidelines/media/0303-167_dropdowncomboboxredline.png "0303-167_DropDownComboBoxRedline")<br />Zone de liste déroulante/zone de liste déroulante (ligne rouge)

| Utilisez... | N’utilisez pas... |
| --- | --- |
| ... pour les listes déroulantes et les zones de liste déroulante dans le document. | ... pour toute interface utilisateur qui n’est pas une zone de liste déroulante ou une zone de liste modifiable. |
| | ... pour les [listes](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandDropDown) déroulantes ou les [zones de liste](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandComboBox)déroulante de barre de commandes. |

**Listes déroulantes et zones de liste modifiable : état par défaut**

![Zone de liste déroulante/liste déroulante par défaut](../../extensibility/ux-guidelines/media/0303-168_dropdowncombobox.png "0303-168_DropDownComboBox")<br />Zone de liste déroulante/liste déroulante par défaut

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `CommonControls.ComboBoxBackground` |
| Bordure | `CommonControls.ComboBoxBorder` |
| Texte | `CommonControls.ComboBoxText` |
| Séparateur | `CommonControls.ComboBoxSeparator` |
| Glyphe | `CommonControls.ComboBoxGlyph` |
| Arrière-plan de glyphe | `CommonControls.ComboBoxGlyphBackground` |

**Listes déroulantes et zones de liste modifiable : état désactivé**

![Zone de liste déroulante/liste déroulante désactivée](../../extensibility/ux-guidelines/media/0303-169_dropdowncomboboxdisabled.png "0303-169_DropDownComboBoxDisabled")<br />Zone de liste déroulante/liste déroulante désactivée

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `CommonControls.ComboBoxBackgroundDisabled` |
| Bordure | `CommonControls.ComboBoxBorderDisabled` |
| Texte | `CommonControls.ComboBoxTextDisabled` |
| Séparateur | `CommonControls.ComboBoxSeparatorDisabled` |
| Glyphe | `CommonControls.ComboBoxGlyphDisabled` |
| Arrière-plan de glyphe | `CommonControls.ComboBoxGlyphBackgroundDisabled` |

**Listes déroulantes et zones de liste modifiable : état sensitif**

![Zone de liste déroulante/liste déroulante au pointage](../../extensibility/ux-guidelines/media/0303-170_dropdowncomboboxhover.png "0303-170_DropDownComboBoxHover")<br />Zone de liste déroulante/liste déroulante au pointage

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `CommonControls.ComboBoxBackgroundHover` |
| Bordure | `CommonControls.ComboBoxBorderHover` |
| Texte | `CommonControls.ComboBoxTextHover` |
| Séparateur | `CommonControls.ComboBoxSeparatorHover` |
| Glyphe | `CommonControls.ComboBoxGlyphHover` |
| Arrière-plan de glyphe | `CommonControls.ComboBoxGlyphBackgroundHover` |

**Listes déroulantes et zones de liste modifiable : état enfoncé**

![Zone de liste déroulante/zone de liste déroulante enfoncée](../../extensibility/ux-guidelines/media/0303-171_dropdowncomboboxpressed.png "0303-171_DropDownComboBoxPressed")<br />Zone de liste déroulante/zone de liste déroulante enfoncée

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `CommonControls.ComboBoxBackgroundPressed` |
| Bordure | `CommonControls.ComboBoxBorderPressed` |
| Texte | `CommonControls.ComboBoxTextPressed` |
| Séparateur | `CommonControls.ComboBoxSeparatorPressed` |
| Glyphe | `CommonControls.ComboBoxGlyphPressed` |
| Arrière-plan de glyphe | `CommonControls.ComboBoxGlyphBackgroundPressed` |

**Listes déroulantes et zones de liste modifiable affichage des éléments : état enfoncé**

 ![Affichage d’élément de liste déroulante/zone de liste déroulante](../../extensibility/ux-guidelines/media/0303-174_dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")<br />Affichage d’élément de liste déroulante/zone de liste déroulante

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `CommonControls.ComboBoxListBackground`<br />`CommonControls.ComboBoxListBackgroundHover`<br />`CommonControls.ComboBoxListItemBackgroundPressed`<br />`CommonControls.ComboBoxListItemBackgroundFocused` |
| Bordure | `CommonControls.ComboBoxListBorder`<br />`CommonControls.ComboBoxListBorderHover`<br />`CommonControls.ComboBoxListBorderPressed`<br />`CommonControls.ComboBoxListBorderFocused` |
| Texte d’élément | `CommonControls.ComboBoxListItemText`<br /> `CommonControls.ComboBoxListItemTextHover`<br />`CommonControls.ComboBoxListItemTextPressed`<br />`CommonControls.ComboBoxListItemTextFocused` |
| Ombre d’arrière-plan | `CommonControls.ComboBoxListBackgroundShadow` |

**Listes déroulantes et zones de liste modifiable : état ciblé**

![Zone de liste déroulante/liste déroulante avec focus](../../extensibility/ux-guidelines/media/0303-172_dropdowncomboboxfocused.png "0303-172_DropDownComboBoxFocused")<br />Zone de liste déroulante/liste déroulante avec focus

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `CommonControls.ComboBoxBackgroundFocused` |
| Bordure | `CommonControls.ComboBoxBorderFocused` |
| Texte | `CommonControls.ComboBoxTextFocused` |
| Séparateur | `CommonControls.ComboBoxSeparatorFocused` |
| Glyphe | `CommonControls.ComboBoxGlyphFocused` |
| Arrière-plan de glyphe | `CommonControls.ComboBoxGlyphBackgroundFocused` |

**Listes déroulantes et zones de liste modifiable : sélection d’entrée de texte**

![Sélection d’entrée de texte de zone de liste déroulante/zone de liste déroulante](../../extensibility/ux-guidelines/media/0303-173_dropdowncomboboxtextinput.png "0303-173_DropDownComboBoxTextInput")<br />Sélection d’entrée de texte de zone de liste déroulante/zone de liste déroulante

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Surlignage | `CommonControls.ComboBoxTextInputSelection` |

### <a name="tabular-data-grid-controls"></a>Contrôles de données tabulaires (grille)
Les contrôles de données tabulaires, également appelés contrôles de grille, sont des contrôles communs pour Visual Studio qui peuvent être utilisés pour présenter des grandes quantités de données dans plusieurs colonnes. Les contrôles de données tabulaires standard se trouvent à plusieurs endroits dans Visual Studio : la fenêtre Outil Liste d’erreurs, les rapports IntelliTrace et l’affichage du tas de mémoire, entre autres. Utilisez toujours les contrôles de données tabulaires standard fournis. Dans de rares cas, vous pouvez ne pas avoir accès aux contrôles de données tabulaires standard. Si tel est le cas, utilisez les noms de jeton suivants pour veiller à ce que votre interface utilisateur soit cohérente avec les autres contrôles de données tabulaires dans Visual Studio.

![Contrôle de grille/données tabulaire (ligne rouge)](../../extensibility/ux-guidelines/media/0303-197_tabulardatagridcontrolredline.png "0303-197_TabularDataGridControlRedline")<br />Contrôle de grille/données tabulaire (ligne rouge)

| Utilisez... | N’utilisez pas... |
| --- | --- |
| ... pour les contrôles tabulaires ou de grille. | ... pour toute interface utilisateur qui n’est pas un contrôle tabulaire ou de grille. |

#### <a name="column-headers"></a>En-têtes de colonne
Les en-têtes de colonnes comprennent un arrière-plan, une bordure, le texte du titre et un éventuel glyphe généralement utilisé pour trier une grille selon cette colonne.

**En-tête de colonne : état par défaut**

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Header.Default` |
| Premier plan (texte) | `Environment.CommandBarTextActive` |
| Premier plan (glyphe) | `Header.Glyph` |
| Bordure | `Header.SeparatorLine` |

**En-tête de colonne : état sensitif**

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Header.MouseOver` |
| Premier plan (texte) | `Environment.CommandBarTextHover` |
| Premier plan (glyphe) | `Header.MouseOverGlyph` |
| Bordure | `Header.SeparatorLine` |

**En-tête de colonne : état enfoncé**

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `CommonControls.CheckBoxBackgroundPressed` |
| Premier plan (texte) | `CommonControls.CheckBoxBorderPressed` |
| Premier plan (glyphe) | `CommonControls.CheckBoxTextPressed` |
| Bordure | `CommonControls.CheckBoxGlyphPressed` |

#### <a name="list-view-items"></a>Éléments de la vue Liste
 Les éléments de la vue Liste comprennent un arrière-plan et le contenu. Le contenu peut être du texte, une icône ou les deux.

**Éléments de la vue Liste : état par défaut**

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | Transparent |
| Premier plan (texte) | `Environment.CommandBarTextActive` |
| Bordure | Aucun |

**Éléments de la vue Liste : état actif**

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `TreeView.SelectedItemActive` |
| Premier plan (texte) | `TreeView.SelectedItemActiveText` |
| Bordure | Aucun |

**Éléments de la vue Liste : état inactif**

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `TreeView.SelectedItemInactive` |
| Premier plan (texte) | `TreeView.SelectedItemInactiveText` |
| Bordure | Aucun |

### <a name="ui-text"></a>Texte de l’interface utilisateur

#### <a name="instructional-text"></a>Texte d’instructions
Le texte d’instructions donne une explication principale importante de ce que vous devez faire dans une page de document ou de boîte de dialogue.

![Texte d’instructions par défaut](../../extensibility/ux-guidelines/media/0303_InstructionalText.png "0303_InstructionalText.png")<br />Texte d’instructions par défaut

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Premier plan (texte) | `Environment.ControlText` |

#### <a name="secondary-instructional-text"></a>Texte d’instruction secondaire
Dans les pages de document avec un grand nombre de contrôles et de texte, certains textes d’instructions utilisent une valeur de couleur différente. Cela permet de transmettre les informations les plus importantes et de réduire la densité globale des éléments d’interface utilisateur. (Voir également la section ci-dessous sur le texte d’indication.)

![Texte d’instruction secondaire](../../extensibility/ux-guidelines/media/0303_SecondaryInstructionalText.png "0303_SecondaryInstructionalText.png")<br />Texte d’instruction secondaire

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Premier plan (texte) | `Environment.ControlEditHintText` |

#### <a name="hint-text"></a>Texte d’indication
Le texte d’indication s’affiche dans un contrôle vide, sous un contrôle, ou sur une surface de document vide pour montrer à l’utilisateur ce qu’il doit faire ensuite. Vous pouvez utiliser le texte d’indication avec l’arrière-plan de la fenêtre ou du contrôle.

**Texte d’indication par défaut**

![Texte d’indication par défaut](../../extensibility/ux-guidelines/media/0303_HintText.png "0303_HintText.png")<br />Texte d’indication par défaut

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Premier plan (texte) | `Environment.ControlEditHintText` |

**Texte d’indication obligatoire**

![Texte d’indication obligatoire](../../extensibility/ux-guidelines/media/0303_RequiredHintText.png "0303_RequiredHintText.png")<br />Texte d’indication obligatoire

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Premier plan (texte) | `Environment.ControlRequiredHintText` |
| Arrière-plan | `Environment.ControlRequiredBackground` |

**Texte du contrôle zone de recherche**

> Consultez [zones de recherche](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_SearchBoxes) pour d’autres jetons de couleur liés au contrôle de recherche.

![Texte du contrôle zone de recherche](../../extensibility/ux-guidelines/media/0303_SearchBoxControl.png "0303_SearchBoxControl.png")<br />Texte du contrôle zone de recherche

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Premier plan (texte) | `SearchControl.UnfocusedWatermarkText` |

### <a name="hyperlink"></a>Hyperlink
Le lien hypertexte est un contrôle qui n’a pas de paire premier plan/arrière-plan. Dans tous les cas, utilisez la couleur du lien hypertexte de premier plan, qui s’affiche correctement sur les arrière-plans foncés, gris et blancs. Si vous n’utilisez pas le jeton de couleur du contrôle de lien hypertexte, vous verrez la couleur système par défaut pour « pressé » qui clignotera en rouge. C’est le signal que le contrôle n’utilise pas le jeton de couleur d’environnement approprié.

![Lien hypertexte (ligne rouge)](../../extensibility/ux-guidelines/media/0303-133_hyperlinkredline.png "0303-133_HyperlinkRedline")<br />Lien hypertexte (ligne rouge)

| Utilisez... | N’utilisez pas... |
| --- | --- |
| ... Lorsque vous devez créer un lien hypertexte personnalisé. | ... pour tout ce qui n’est pas un lien hypertexte. |

**Lien hypertexte : état par défaut**

![Lien hypertexte par défaut](../../extensibility/ux-guidelines/media/0303-134_hyperlink.png "0303-134_Hyperlink")<br />Lien hypertexte par défaut

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Premier plan (texte) | `Environment.PanelHyperlink` |

**Lien hypertexte : état sensitif**

![Lien hypertexte au pointage](../../extensibility/ux-guidelines/media/0303-135_hyperlinkhover.png "0303-135_HyperlinkHover")<br />Lien hypertexte au pointage

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Premier plan (texte) | `Environment.PanelHyperlinkHover` |

**Lien hypertexte : état enfoncé**

![Lien hypertexte appuyé](../../extensibility/ux-guidelines/media/0303-136_hyperlinkpressed.png "0303-136_HyperlinkPressed")<br />Lien hypertexte appuyé

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Premier plan (texte) | `Environment.PanelHyperlinkPressed` |

**Lien hypertexte : état désactivé**

![Lien hypertexte désactivé](../../extensibility/ux-guidelines/media/0303-137_hyperlinkdisabled.png "0303-137_HyperlinkDisabled")<br />Lien hypertexte désactivé

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Premier plan (texte) | `Environment.PanelHyperlinkDisabled` |

### <a name="infobars"></a>Barres
Les barres d’informations sont utilisées pour fournir plus d’informations sur un contexte donné et apparaissent toujours en haut d’une fenêtre de document ou d’outil.

![Barre d’informations (ligne rouge)](../../extensibility/ux-guidelines/media/0303-138_infobarredline.png "0303-138_InfobarRedline")<br />Barre d’informations (ligne rouge)

| Utilisez... | N’utilisez pas... |
| --- | --- |
| ... lors de la création de barres personnalisés. | ... pour les éléments d’interface utilisateur qui ne sont pas similaires à une barre d’informations. |

**Barre d’informations : état par défaut**

![Barre d’informations par défaut](../../extensibility/ux-guidelines/media/0303-139_infobar.png "0303-139_Infobar")<br />Barre d’informations par défaut

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `InfoBar.InfoBarBackground` |
| Premier plan (texte) | `InfoBar.InfoBar` |
| Bordure | `InfoBar.InfoBarBorder` |

**Bouton de fermeture de la barre d’informations ( &times; ) : état par défaut**

![Bouton Fermer la barre d’informations par défaut ( &times; )](../../extensibility/ux-guidelines/media/0303_InfobarCloseDefault.png "0303_InfobarCloseDefault.png")<br />Bouton Fermer la barre d’informations par défaut ( &times; )

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `InfoBar.CloseButton` |
| Bordure | `InfoBar.CloseButtonBorder` |
| Glyphe | `InfoBar.CloseButtonGlyph` |

**Bouton de fermeture de la barre d’informations ( &times; ) : état sensitif**

![Bouton Fermer la barre d’informations ( &times; ) au pointage](../../extensibility/ux-guidelines/media/0303_InfobarCloseHover.png "0303_InfobarCloseHover.png")<br />Bouton Fermer la barre d’informations ( &times; ) au pointage

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `InfoBar.CloseButtonHover` |
| Bordure | `InfoBar.CloseButtonHoverBorder` |
| Glyphe | `InfoBar.CloseButtonHoverGlyph` |

**Bouton de fermeture de la barre d’informations ( &times; ) : état enfoncé**

![Bouton Fermer la barre d’informations appuyée ( &times; )](../../extensibility/ux-guidelines/media/0303_InfobarClosePressed.png "0303_InfobarClosePressed.png")<br />Bouton Fermer la barre d’informations appuyée ( &times; )

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `InfoBar.CloseButtonDown` |
| Bordure | `InfoBar.CloseButtonDownBorder` |
| Glyphe | `InfoBar.CloseButtonDownGlyph` |

**Bouton de lien hypertexte de la barre d’informations : état par défaut**

![Bouton de lien hypertexte de la barre d’informations par défaut](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonDefault.png "0303_InfobarHyperlinkButtonDefault.png")<br />Bouton de lien hypertexte de la barre d’informations par défaut

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Premier plan (texte) | `InfoBar.Hyperlink` |

**Bouton de lien hypertexte de la barre d’informations : état sensitif**

![Bouton de lien hypertexte de la barre d’informations au pointage](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonHover.png "0303_InfobarHyperlinkButtonHover.png")<br />Bouton de lien hypertexte de la barre d’informations au pointage

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Premier plan (texte) | `Infobar.HyperlinkMouseOver`<br />(Avec soulignement) |

**Bouton de lien hypertexte de la barre d’informations : état enfoncé**

![Bouton de lien hypertexte de barre d’informations appuyé](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonPressed.png "0303_InfobarHyperlinkButtonPressed.png")<br />Bouton de lien hypertexte de barre d’informations appuyé

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Premier plan (texte) | `Infobar.HyperlinkMouseDown`<br />(Avec soulignement) |

**Lien hypertexte incorporé de la barre d’informations (dans une phrase) : état par défaut**

![Bouton de lien hypertexte de la barre d’informations incluse par défaut](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonDefault.png "0303_InfobarHyperlinkButtonDefault.png")<br />Bouton de lien hypertexte de la barre d’informations incluse par défaut

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Premier plan (texte) | `InfoBar.Hyperlink` |

**Lien hypertexte inline de la barre d’informations (au sein d’une phrase) : état sensitif**

![Bouton lien hypertexte inline de la barre d’informations au survol](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkInlineHover.png "0303_InfobarHyperlinkInlineHover.png")<br />Bouton lien hypertexte inline de la barre d’informations au survol

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Premier plan (texte) | `Infobar.HyperlinkMouseOver`<br />(Avec soulignement) |

**Lien hypertexte inline de la barre d’informations (dans une phrase) : état enfoncé**

![Bouton de lien hypertexte de la barre d’informations Inline appuyé](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkInlinePressed.png "0303_InfobarHyperlinkInlinePressed.png")<br />Bouton de lien hypertexte de la barre d’informations Inline appuyé

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Premier plan (texte) | `Infobar.HyperlinkMouseDown`<br />(Avec soulignement) |

**Bouton de la barre d’informations : état par défaut**

![Bouton de barre d’informations par défaut](../../extensibility/ux-guidelines/media/0303_InfobarButtonDefault.png "0303_InfobarButtonDefault.png")<br />Bouton de barre d’informations par défaut

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `InfoBar.Button` |
| Premier plan (texte) | `InfoBar.Button` |
| Bordure | `InfoBar.ButtonBorder` |

**Bouton de la barre d’informations : état sensitif**

![Bouton de la barre d’informations au pointage](../../extensibility/ux-guidelines/media/0303_InfobarButtonHover.png "0303_InfobarButtonHover.png")<br />Bouton de la barre d’informations au pointage

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `InfoBar.ButtonMouseOver` |
| Premier plan (texte) | `InfoBar.ButtonMouseOver` |
| Bordure | `InfoBar.ButtonMouseOverBorder` |

**Bouton de la barre d’informations : état enfoncé**

![Bouton de la barre d’informations appuyée](../../extensibility/ux-guidelines/media/0303_InfobarButtonPressed.png "0303_InfobarButtonPressed.png")<br />Bouton de la barre d’informations appuyée

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `InfoBar.ButtonMouseDown` |
| Premier plan (texte) | `InfoBar.ButtonMouseDown` |
| Bordure | `InfoBar.ButtonMouseDownBorder` |

**Bouton de la barre d’informations : état désactivé**

![Bouton de barre d’informations désactivé](../../extensibility/ux-guidelines/media/0303_InfobarButtonDisabled.png "0303_InfobarButtonDisabled.png")<br />Bouton de barre d’informations désactivé

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `InfoBar.ButtonDisabled` |
| Premier plan (texte) | `InfoBar.ButtonDisabled` |
| Bordure | `InfoBar.ButtonDisabledBorder` |

**Bouton de la barre d’informations : état Focus**

![Bouton de barre d’informations Focused](../../extensibility/ux-guidelines/media/0303_InfobarButtonFocus.png "0303_InfobarButtonFocus.png")<br />Bouton de barre d’informations Focused

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `InfoBar.ButtonFocus` |
| Premier plan (texte) | `InfoBar.ButtonFocus` |
| Bordure | `InfoBar.ButtonFocusBorder` |

### <a name="scroll-bars"></a>Barres de défilement
Les barres de défilement sont stylisées par l’environnement Visual Studio et n’ont pas besoin d’être à thème. Toutefois, vous pouvez décider que vous souhaitez tirer parti des couleurs utilisées dans les barres de défilement afin que votre interface utilisateur apparaisse toujours cohérente avec cette partie de l’environnement Visual Studio.

![Barre de défilement (ligne rouge)](../../extensibility/ux-guidelines/media/0303-140_scrollbarredline.png "0303-140_ScrollbarRedline")<br />Barre de défilement (ligne rouge)

| Utilisez... | N’utilisez pas... |
| --- | --- |
| ... Lorsque vous créez une interface utilisateur que vous souhaitez faire correspondre aux barres de défilement Visual Studio. | ... pour tout ce que vous ne souhaitez pas faire correspondre systématiquement à l’interface utilisateur de la barre de défilement. |

**Barre de défilement : état par défaut**

![Barre de défilement par défaut](../../extensibility/ux-guidelines/media/0303-141_scrollbar.png "0303-141_Scrollbar")<br />Barre de défilement par défaut

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Scroll bar | `Environment.ScrollBarBackground` |
| Premier plan (curseur de défilement) | `Environment.ScrollBarThumbBackground` |

**Barre de défilement : état de survol**

![Barre de défilement au pointage](../../extensibility/ux-guidelines/media/0303-143_scrollbarhover.png "0303-143_ScrollbarHover")<br />Barre de défilement au pointage

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Scroll bar | `Environment.ScrollBarBackground` |
| Premier plan (curseur de défilement) | `Environment.ScrollBarThumbMouseOverBackground` |

*Barre de défilement : état enfoncé**

![Barre de défilement appuyée](../../extensibility/ux-guidelines/media/0303-145_scrollbarpressed.png "0303-145_ScrollbarPressed")<br />Barre de défilement appuyée

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Scroll bar | `Environment.ScrollBarBackground` |
| Premier plan (curseur de défilement) | `Environment.ScrollBarThumbPressedBackground` |

**Flèche de barre de défilement : état par défaut**

![Flèche de la barre de défilement par défaut](../../extensibility/ux-guidelines/media/0303-142_scrollbararrow.png "0303-142_ScrollbarArrow")<br />Flèche de la barre de défilement par défaut

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.ScrollBarArrowBackground`<br />(Défini sur la même couleur que la barre de défilement.) |
| Premier plan (glyphe) | `Environment.ScrollBarArrowGlyph` |

**Barre de défilement flèche : état sensitif**

![Flèche de barre de défilement au pointage](../../extensibility/ux-guidelines/media/0303-144_scrollbararrowhover.png "0303-144_ScrollbarArrowHover")<br />Flèche de barre de défilement au pointage

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.ScrollBarArrowMouseOverBackground`<br />(Défini sur la même couleur que la barre de défilement.) |
| Premier plan (glyphe) | `Environment.ScrollBarArrowGlyphMouseOver` |

**Flèche de barre de défilement : état enfoncé**

![Flèche de barre de défilement appuyée](../../extensibility/ux-guidelines/media/0303-146_scrollbararrowpressed.png "0303-146_ScrollbarArrowPressed")<br />Flèche de barre de défilement appuyée

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.ScrollBarArrowPressedBackground`<br />(Défini sur la même couleur que la barre de défilement.) |
| Premier plan (glyphe) | `Environment.ScrollBarArrowGlyphPressed` |

### <a name="search-boxes"></a><a name="BKMK_SearchBoxes"></a>Zones de recherche
Si possible, utilisez le contrôle de recherche commun fourni par l’environnement Visual Studio. Les couleurs de zone de recherche se trouvent dans la catégorie « SearchControl » du fichier **ShellColors.pkgdef** qui contient les noms de jeton du champ d’entrée, du bouton d’action, du bouton de liste déroulante et du menu déroulant.

Une zone de recherche peut être dans plusieurs états, dont certains s’excluent mutuellement :

- Les états « avec focus » ou « sans focus » font référence à la présence ou non du curseur dans la zone de texte.

- Les états « actif » ou « inactif » font référence à l’éventuel entrée par l’utilisateur d’une requête de recherche dans la zone de texte.

- L’état « pointage » signifie que l’utilisateur a placé le curseur de la souris au-dessus de la zone de recherche (cet état remplace tous les autres états).

- L’état « désactivé » signifie que la fonctionnalité de recherche est désactivée pour le contexte actuel.

![Zone de recherche (ligne rouge)](../../extensibility/ux-guidelines/media/0303-110_searchboxredline.png "0303-110_SearchBoxRedline")<br />Zone de recherche (ligne rouge)

| Utilisez... | N’utilisez pas... |
| --- | --- |
| ... Lorsque vous concevez une zone de recherche personnalisée. | ... pour tout ce qui n’est pas une zone de recherche. |
| | ... pour tout ce que vous ne voulez pas toujours faire correspondre à l’interface utilisateur de la zone de recherche. |

**Champ d’entrée de recherche ciblée**

![Champ d’entrée de recherche ciblée](../../extensibility/ux-guidelines/media/0303-111_searchinputfieldfocused.png "0303-111_SearchInputFieldFocused")<br />Champ d’entrée de recherche ciblée

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `SearchControl.FocusedBackground` |
| Premier plan (texte) | `SearchControl.FocusedBackground` |
| Bordure | `SearchControl.FocusedBorder` |
| Séparateur | `SearchControl.FocusedDropDownSeparator` |

**Champ d’entrée de recherche active inactif**

![Champ d'entrée de recherche inactif](../../extensibility/ux-guidelines/media/0303-114_searchinputfieldunfocused.png "0303-114_SearchInputFieldUnfocused")<br />Champ d’entrée de recherche active inactif

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `SearchControl.SearchActiveBackground` |
| Premier plan (texte) | `SearchControl.SearchActiveBackground` |
| Bordure | `SearchControl.UnfocusedBorder` |
| Séparateur | `SearchControl.DropDownSeparator` |

**Champ d’entrée de recherche inactif**

![Champ d’entrée de recherche inactif](../../extensibility/ux-guidelines/media/0303-114-1_searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")<br />Champ d’entrée de recherche inactif

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `SearchControl.Unfocused` |
| Premier plan (texte) | `SearchControl.Unfocused` |
| Bordure | `SearchControl.UnfocusedBorder` |
| Séparateur | `SearchControl.DropDownSeparator` |

**Champ d’entrée de recherche en surbrillance (texte uniquement)**

![Champ d’entrée de recherche en surbrillance](../../extensibility/ux-guidelines/media/0303-120_searchinputfieldhighlight.png "0303-120_SearchInputFieldHighlight")<br />Champ d’entrée de recherche en surbrillance

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `SearchControl.Selection` |
| Premier plan (texte) | `SearchControl.FocusedBackground` |
| Bordure | Aucun |
| Séparateur | `SearchControl.FocusedDropDownSeparator` |

**Champ d’entrée de recherche désactivé**

![Champ d’entrée de recherche désactivé](../../extensibility/ux-guidelines/media/0303-121_searchinputfielddisabled.png "0303-121_SearchInputFieldDisabled")<br />Champ d’entrée de recherche désactivé

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `SearchControl.Disabled` |
| Premier plan (texte) | `SearchControl.Disabled` |
| Bordure | `SearchControl.DisabledBorder` |
| Séparateur | `SearchControl.DropDownSeparator` |

**Bouton d’action de recherche ciblée**

![Bouton d'action de recherche actif](../../extensibility/ux-guidelines/media/0303-112_searchactionbuttonfocused.png "0303-112_SearchActionButtonFocused")<br />Bouton d’action de recherche ciblée

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | Aucun |
| Premier plan (glyphe Rechercher) | `SearchControl.SearchGlyph` |
| Premier plan (glyphe Arrêter) | `SearchControl.StopGlyph` |
| Premier plan (glyphe Effacer) | `SearchControl.ClearGlyph` |
| Bordure | N/A |

**Bouton d’action de recherche inactif**

![Bouton d’action de recherche inactif](../../extensibility/ux-guidelines/media/0303-115_searchactionbuttonunfocused.png "0303-115_SearchActionButtonUnfocused")<br />Bouton d’action de recherche inactif

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | N/A |
| Premier plan (glyphe Rechercher) | `SearchControl.SearchGlyph` |
| Premier plan (glyphe Arrêter) | `SearchControl.StopGlyph` |
| Premier plan (glyphe Effacer) | `SearchControl.ClearGlyph` |
| Bordure | N/A |

**Bouton d’action de recherche appuyé**

![Bouton d’action de recherche appuyé](../../extensibility/ux-guidelines/media/0303-116-1_searchactionbuttonpressed.png "0303-116-1_SearchActionButtonPressed")<br />Bouton d’action de recherche appuyé

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `SearchControl.ActionButtonMouseDown` |
| Premier plan (glyphe) | `SearchControl.ActionButtonMouseDownGlyph` |
| Bordure | `SearchControl.ActionButtonMouseDownBorder` |

**Bouton d’action de recherche désactivé**

![Bouton d'action de recherche désactivé](../../extensibility/ux-guidelines/media/0303-122_searchactionbuttondisabled.png "0303-122_SearchActionButtonDisabled")<br />Bouton d’action de recherche désactivé

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | Aucun |
| Premier plan (glyphe) | `SearchControl.ActionButtonDisabledGlyph` |
| Bordure | Aucun |

**Bouton de liste déroulante recherche ciblée**

![Bouton de liste déroulante recherche ciblée](../../extensibility/ux-guidelines/media/0303-113_searchdropdownbuttonfocused.png "0303-113_SearchDropdownButtonFocused")<br />Bouton de liste déroulante recherche ciblée

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `SearchControl.FocusedDropDownButton` |
| Premier plan (glyphe) | `SearchControl.FocusedDropDownButtonGlyph` |
| Bordure | `SearchControl.FocusedDropDownButtonBorder` |

**Bouton de liste déroulante de recherche inactif**

![Bouton de liste déroulante de recherche inactif](../../extensibility/ux-guidelines/media/0303-116_searchdropdownbuttonunfocused.png "0303-116_SearchDropdownButtonUnfocused")<br />Bouton de liste déroulante de recherche inactif

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `SearchControl.UnfocusedDropDownButton` |
| Premier plan (glyphe) | `SearchControl.UnfocusedDropDownButtonGlyph` |
| Bordure | `SearchControl.UnfocusedDropDownButtonBorder` |

**Bouton de liste déroulante de recherche appuyée**

![Bouton de liste déroulante de recherche appuyée](../../extensibility/ux-guidelines/media/0303-116-2_searchdropdownbuttonpressed.png "0303-116-2_SearchDropdownButtonPressed")<br />Bouton de liste déroulante de recherche appuyée

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `SearchControl.MouseDownDropDownButton` |
| Premier plan (glyphe) | `SearchControl.MouseDownDropDownButtonGlyph` |
| Bordure | `SearchControl.MouseDownDropDownButtonBorder` |

**Bouton de liste déroulante de recherche désactivé**

![Bouton de liste déroulante de recherche désactivé](../../extensibility/ux-guidelines/media/0303-123_searchdropdownbuttondisabled.png "0303-123_SearchDropdownButtonDisabled")<br />Bouton de liste déroulante de recherche désactivé

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | Aucun |
| Premier plan (glyphe) | `SearchControl.DisabledDownButtonGlyph` |
| Bordure | Aucun |

#### <a name="search-drop-down-lists"></a>Listes déroulantes de recherche
Le menu déroulant de la zone de recherche est susceptible d’être légèrement plus complexe que les autres menus déroulants dans Visual Studio. Les sections « recherches suggérées » et « options de recherche » peuvent apparaître seules ou ensemble dans le menu, et chacune d’elles est colorée séparément. Une ligne sépare également ces deux sections quand elles apparaissent ensemble et une bordure entoure l’ensemble du menu déroulant.

![Liste déroulante de recherche (ligne rouge)](../../extensibility/ux-guidelines/media/0303-124_searchdropdownredline.png "0303-124_SearchDropdownRedline")<br />Liste déroulante de recherche (ligne rouge)

| Utilisez... | N’utilisez pas... |
| --- | --- |
| ... Lorsque vous créez une liste déroulante de recherche personnalisée. | ... pour les listes déroulantes qui apparaissent dans d’autres contextes. |
| ... les noms de jeton corrects pour les composants de liste corrects. | ... dans toute combinaison d’arrière-plan/premier plan autre que celle spécifiée. |

**Éléments de liste déroulante de recherche**

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Bordure | `SearchControl.PopupBorder` |
| Séparateur | `SearchControl.PopupSectionHeaderSeparator` |
| Shadow | `Environment.DropShadowBackground` |

**Recherches suggérées : état par défaut**

![Recherches suggérées par défaut](../../extensibility/ux-guidelines/media/0303-125_searchsuggested.png "0303-125_SearchSuggested")<br />Recherches suggérées par défaut

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `SearchControl.PopupItemsListBackgroundGradientBegin`<br />(Les points de dégradé de ce jeton ne sont pas utilisés dans l’interface utilisateur à thème.) |
| Premier plan (texte) | `SearchControl.PopupItemText` |

**Recherches suggérées : état pointé**

![Recherches suggérées au survol](../../extensibility/ux-guidelines/media/0303-128_searchsuggestedhover.png "0303-128_SearchSuggestedHover")<br />Recherches suggérées au survol

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br />(Les points de dégradé de ce jeton ne sont pas utilisés dans l’interface utilisateur à thème.) |
| Premier plan (texte) | `SearchControl.PopupMouseOverItemText` |
| Bordure | `SearchControl.PopupControlMouseOverBorder` |

**Options de recherche : état par défaut**

![Case à cocher de recherche](../../extensibility/ux-guidelines/media/0303-126_searchcheckbox.png "0303-126_SearchCheckbox")<br />Options de recherche par défaut (case à cocher)

![Options de recherche](../../extensibility/ux-guidelines/media/0303-127_searchoptions.png "0303-127_SearchOptions")<br />Options de recherche par défaut (lien)

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `SearchControl.PopupSectionBackgroundGradientBegin`<br />(Les points de dégradé de ce jeton ne sont pas utilisés dans l’interface utilisateur à thème.) |
| Premier plan (texte de case à cocher) | `SearchControl.PopupCheckboxText` |
| Premier plan (texte de lien) | `SearchControl.PopupButtonText` |
| Arrière-plan d’en-tête | `SearchControl.PopupSectionHeaderGradientBegin`<br />(Les points de dégradé de ce jeton ne sont pas utilisés dans l’interface utilisateur à thème.) |
| Premier plan (texte d’en-tête) | `SearchControl.PopupSectionHeaderText` |

**Options de recherche : état du survol**

![Options de recherche (case à cocher) au survol](../../extensibility/ux-guidelines/media/0303-129_searchcheckboxhover.png "0303-129_SearchCheckboxHover")<br />Options de recherche (case à cocher) au survol

![Options de recherche (lien) au survol](../../extensibility/ux-guidelines/media/0303-130_searchoptionshover.png "0303-130_SearchOptionsHover")<br />Options de recherche (lien) au survol

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br />(Les points de dégradé de ce jeton ne sont pas utilisés dans l’interface utilisateur à thème.) |
| Premier plan (texte de case à cocher) | `SearchControl.PopupCheckboxMouseDownText` |
| Premier plan (texte de lien) | `SearchControl.PopupButtonMouseDownText` |
| Bordure | `SearchControl.PopupControlMouseOverBorder` |

**Options de recherche : état appuyé**

![Options de recherche appuyée (case à cocher)](../../extensibility/ux-guidelines/media/0303-131_searchsuggestedpressed.png "0303-131_SearchSuggestedPressed")<br />Options de recherche appuyée (case à cocher)

![Options de recherche appuyée (lien)](../../extensibility/ux-guidelines/media/0303-132_searchoptionspressed.png "0303-132_SearchOptionsPressed")<br />Options de recherche appuyée (lien)

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan de case à cocher | `SearchControl.PopupControlMouseDownBackgroundGradientBegin`<br />`SearchControl.PopupControlMouseDownBackgroundGradientEnd`<br />(Les points de dégradé de ce jeton ne sont pas utilisés dans l’interface utilisateur à thème.) |
| Premier plan (texte de case à cocher) | `SearchControl.PopupCheckboxMouseDownText` |
| Arrière-plan de lien | `SearchControl.PopupButtonMouseDownBackgroundGradientBegin`<br />(Les points de dégradé de ce jeton ne sont pas utilisés dans l’interface utilisateur à thème.) |
| Premier plan (texte de lien) | `SearchControl.PopupButtonMouseDownText` |

### <a name="tree-views"></a><a name="BKMK_TreeView"></a> Arborescences
Plusieurs fenêtres outil, y compris les Explorateur de solutions, les Explorateur de serveurs et les Affichage de classes, implémentent un schéma organisationnel hiérarchique dont les couleurs sont contrôlées par les noms de couleur de la `TreeView` catégorie. Tous les éléments d’une arborescence ont des couleurs d’arrière-plan et de texte. Les éléments qui possèdent des éléments enfants imbriqués ont également des glyphes qui indiquent si l’élément est développé ou réduit.

![Arborescence (ligne rouge)](../../extensibility/ux-guidelines/media/0303-147_treeviewredline.png "0303-147_TreeViewRedline")<br />Arborescence (ligne rouge)

| Utilisez... | N’utilisez pas... |
| --- | --- |
| ... partout où vous avez besoin d’implémenter une vue organisationnelle hiérarchique. | ... pour tout ce qui n’est pas similaire à une arborescence. |
| | ... dans toute combinaison d’arrière-plan/premier plan autre que celle spécifiée. |

**Élément d’arborescence : état par défaut**

![Élément d’affichage de l’arborescence par défaut](../../extensibility/ux-guidelines/media/0303-148_treeview.png "0303-148_TreeView")<br />Élément d’affichage de l’arborescence par défaut

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `TreeView.Background` |
| Premier plan (texte) | `TreeView.Background` |
| Premier plan (glyphe) | `TreeView.Glyph` |
| Bordure | Aucun |

**Élément d’arborescence : état de survol**

![Élément d’arborescence au survol](../../extensibility/ux-guidelines/media/0303-149_treeviewhover.png "0303-149_TreeViewHover")<br />Élément d’arborescence au survol

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `TreeView.Background` |
| Premier plan (texte) | `TreeView.Background` |
| Premier plan (glyphe) | `TreeView.GlyphMouseOver` |
| Bordure | Aucun |

**Élément d’arborescence : faire glisser l’État**

![Élément d’arborescence sur lequel faire glisser](../../extensibility/ux-guidelines/media/0303-150_treeviewdragover.png "0303-150_TreeViewDragOver")<br />Élément d’arborescence sur lequel faire glisser

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `TreeView.DragOverItem` |
| Premier plan (texte) | `TreeView.DragOverItem` |
| Premier plan (glyphe) | `TreeView.DragOverItemGlyph` |
| Bordure | Aucun |

**Élément d’arborescence : sélectionné, état ciblé**

![Élément d’arborescence sélectionné et ayant le focus](../../extensibility/ux-guidelines/media/0303-151_treeviewfocused.png "0303-151_TreeViewFocused")<br />Élément d’arborescence sélectionné et ayant le focus

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `TreeView.SelectedItemActive` |
| Premier plan (texte) | `TreeView.SelectedItemActive` |
| Premier plan (glyphe) | `TreeView.SelectedItemActiveGlyph` |
| Bordure | `TreeView.FocusVisualBorder` |

**Élément d’arborescence : état sélectionné, sans focus**

![Élément d’affichage de l’arborescence sélectionné et inactif](../../extensibility/ux-guidelines/media/0303-152_treeviewunfocused.png "0303-152_TreeViewUnfocused")<br />Élément d’affichage de l’arborescence sélectionné et inactif

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `TreeView.SelectedItemInactive` |
| Premier plan (texte) | `TreeView.SelectedItemInactive` |
| Premier plan (glyphe) | `TreeView.SelectedItemInactiveGlyph` |
| Bordure | Aucun |

**Élément d’arborescence : pointage, sélectionné et état ciblé**

![Élément d’arborescence sélectionné et ayant le focus au pointage](../../extensibility/ux-guidelines/media/0303-153_treeviewfocusedhover.png "0303-153_TreeViewFocusedHover")<br />Élément d’arborescence sélectionné et ayant le focus au pointage

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `TreeView.SelectedItemActive` |
| Premier plan (texte) | `TreeView.SelectedItemActive` |
| Premier plan (glyphe) | `TreeView.SelectedItemActiveGlyphMouseOver` |
| Bordure | `TreeView.FocusVisualBorder` |

**Élément d’arborescence : état pointé, sélectionné et inactif**

![Élément d’affichage de l’arborescence sélectionné et inactif au pointage](../../extensibility/ux-guidelines/media/0303-154_treeviewunfocusedhover.png "0303-154_TreeViewUnfocusedHover")<br />Élément d’affichage de l’arborescence sélectionné et inactif au pointage

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `TreeView.SelectedItemInactive` |
| Premier plan (texte) | `TreeView.SelectedItemInactive` |
| Premier plan (glyphe) | `TreeView.SelectedItemActiveGlyphMouseOver` |
| Bordure | Aucun |

## <a name="shell-appearance"></a>Apparence Shell

### <a name="background"></a>Arrière-plan
L’arrière-plan de l’environnement comporte deux couches. La couche inférieure est une couleur unie qui recouvre l’ensemble de l’IDE. La couche supérieure se place sous l’interface de commande et entre les canaux à masquage automatique de la fenêtre Outil situés sur les côtés gauche et droit de l’IDE. Les couches d’arrière-plan supérieure et inférieure sont définies sur la même couleur dans les thèmes clairs et foncés.

![Arrière-plan du shell Visual Studio (ligne rouge)](../../extensibility/ux-guidelines/media/0303-187_shellbackgroundredline.png "0303-187_ShellBackgroundRedline")<br />Arrière-plan du shell Visual Studio (ligne rouge)

| Utilisez... | N’utilisez pas... |
| --- | --- |
| ... pour les emplacements où vous souhaitez faire correspondre l’arrière-plan de l’environnement Visual Studio. | ... comme un remplissage pour les endroits qui ne sont pas des surfaces d’arrière-plan. |
| | ... comme arrière-plan pour placer des éléments de premier plan. |

**Apparence de l’interpréteur de commandes de la couche inférieure**

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.EnvironmentBackground` |

**Apparence du shell de la couche supérieure**

> Les points de dégradé sont définis sur la même valeur de couleur dans les thèmes clairs et foncés de Visual Studio 2013.

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.EnvironmentBackgroundGradientBegin`<br />`Environment.EnvironmentBackgroundGradientEnd`<br />`Environment.EnvironmentBackgroundGradientMiddle1`<br />`Environment.EnvironmentBackgroundGradientMiddle2` |

### <a name="command-shelf"></a>Interface de commande
Deux ensembles de noms de jeton sont utilisés pour les arrière-plans de l’interface de commande : un jeu pour l’emplacement de la barre de menus et l’autre pour l’emplacement des barres de commandes. Un groupe de barres de commandes possède ses propres valeurs de couleur d’arrière-plan, lesquelles sont décrites dans la section « Barre de commandes ». Le texte de la barre de menus et des barres de commandes est traité dans les sections qui leur sont dédiées.

![Étagère de commande Visual Studio (ligne rouge)](../../extensibility/ux-guidelines/media/0303-188_commandshelfredline.png "0303-188_CommandShelfRedline")<br />Étagère de commande Visual Studio (ligne rouge)

| Utilisez... | N’utilisez pas... |
| --- | --- |
| ... pour les zones où vous placez des menus ou des barres d’outils. | ... pour les zones qui ne sont pas similaires à une commande. |
|... avec la combinaison de nom de jeton d’arrière-plan/premier plan correcte. | |

**Barre de menus de l’étagère de commande**

> Les points de dégradé sont définis sur la même valeur de couleur dans les thèmes clairs et foncés de Visual Studio 2013.

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.CommandShelfHighlightGradientBegin`<br /><br />`Environment.CommandShelfHighlightGradientMiddle`<br />`Environment.CommandShelfHighlightGradientEnd` |

**Barre de commandes de l’étagère de commande**

> Les points de dégradé sont définis sur la même valeur de couleur dans les thèmes clairs et foncés de Visual Studio 2013.

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.CommandShelfBackgroundGradientBegin`<br />`Environment.CommandShelfBackgroundGradientMiddle`<br />`Environment.CommandShelfBackgroundGradientEnd` |

## <a name="manifest-designer"></a>Concepteur de manifeste
Le concepteur de manifeste sert à faciliter l’édition du fichier manifeste dans des projets Windows 8 et Windows Phone 8. Même s’il n’existe aucune infrastructure partagée disponible à la consommation, vous avez peut-être intérêt à faire correspondre la disposition et les couleurs des onglets d’orientation/de navigation à la structure générale. Pour plus d’informations sur la disposition, consultez [Layout for Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).

![Concepteur de manifeste (ligne rouge)](../../extensibility/ux-guidelines/media/0303-175_manifestdesignerredline.png "0303-175_ManifestDesignerRedline")<br />Concepteur de manifeste (ligne rouge)

| Utilisez... | N’utilisez pas... |
| --- | --- |
| ... pour les concepteurs qui sont similaires au concepteur de manifeste. | ... Si vous avez plus de six onglets. |
| ... au lieu d’utiliser des contrôles d’onglet communs en haut d’un éditeur dans la barre d’outils document. | ... pour toute interface utilisateur qui n’est pas structurée comme le concepteur de manifeste. |

**Concepteur de manifeste onglet sélectionné : état par défaut**

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `ManifestDesigner.TabActive` |
| Bordure | Aucun |

**Concepteur de manifeste volet Description sélectionné : état par défaut**

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `ManifestDesigner.DescriptionPane` |

**Page de contenu sélectionnée du concepteur de manifeste : état par défaut**

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `ManifestDesigner.Background` |
| Texte d’assistance de boîte de dialogue | `ManifestDesigner.WatermarkText`<br />(Ce nom de jeton ne correspond pas à sa fonction.) |

**Onglet Concepteur de manifeste : état non sélectionné**

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `ManifestDesigner.Tab.Inactive` |

**Onglet Concepteur de manifeste : état sensitif**

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `ManifestDesigner.Tab.Mouseover` |

## <a name="command-structures"></a>Structures de commande

### <a name="menus"></a><a name="BKMK_CommandMenus"></a> Menus
Les menus peuvent se trouver à plusieurs endroits dans Visual Studio : la barre de menus principale, incorporée dans les fenêtres de document ou d’outil, ou en cliquant avec le bouton droit à différents emplacements dans l’IDE. Les implémentations de menus associées aux autres éléments d’interface utilisateur sont décrites dans la section de l’élément correspondant. Vous devez toujours utiliser l’implémentation de menu standard fournie par l’environnement Visual Studio. Toutefois, dans de rares cas, vous n’aurez peut-être pas accès aux menus Visual Studio standard. Dans ce cas, utilisez les noms de jeton suivants pour vous assurer que votre interface utilisateur est cohérente avec les autres menus dans Visual Studio.

![Menu Visual Studio (ligne rouge)](../../extensibility/ux-guidelines/media/0303-000_menuredline.png "0303-000_MenuRedline")<br />Menu Visual Studio (ligne rouge)

| Utilisez... | N’utilisez pas... |
| --- | --- |
| ... Lorsque vous devez créer un menu personnalisé.| ... la couleur d’arrière-plan seule. Utilisez toujours la combinaison arrière-plan/premier plan spécifiée. |
| ... Quand vous avez un nouveau composant d’interface utilisateur qui doit correspondre aux menus Visual Studio.| |

#### <a name="menu-titles"></a>Titres de menu
Les titres de menu comprennent un arrière-plan, une bordure et le texte du titre, ainsi qu’un glyphe facultatif, généralement quand le menu se trouve dans une barre de commandes.

![Titre de menu (ligne rouge)](../../extensibility/ux-guidelines/media/0303-001_menutitleredline.png "0303-001_MenuTitleRedline")<br />Titre de menu (ligne rouge)

| Utilisez... | N’utilisez pas... |
| --- | --- |
| ... chaque fois que vous créez un titre de menu personnalisé. | ... pour tout ce que vous ne voulez pas toujours faire correspondre au titre de menu. |
| | ... dans toute combinaison d’arrière-plan/premier plan autre que celle spécifiée. |

**Titre du menu : état par défaut**

![Titre de menu par défaut](../../extensibility/ux-guidelines/media/0303-002_menutitledefault.png "0303-002_MenuTitleDefault")<br />Titre de menu par défaut

![Titre de menu par défaut avec glyphe](../../extensibility/ux-guidelines/media/0303-003_menutitlewithglyphdefault.png "0303-003_MenuTitleWithGlyphDefault")<br />Titre de menu par défaut avec glyphe

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | Aucun |
| Premier plan (texte) | `Environment.CommandBarTextActive` |
| Premier plan (glyphe) | `Environment.CommandBarMenuGlyph` |
| Bordure | Aucun |

**Titre du menu : état du survol**

![Titre de menu au pointage](../../extensibility/ux-guidelines/media/0303-004_menutitlehover.png "0303-004_MenuTitleHover")<br />Titre de menu au pointage

![Titre de menu avec glyphe au pointage](../../extensibility/ux-guidelines/media/0303-005_menutitlewithglyphhover.png "0303-005_MenuTitleWithGlyphHover")<br />Titre de menu avec glyphe au pointage

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.CommandBarMouseOverBackgroundBegin`<br />(Les points de dégradé de ce jeton ne sont pas utilisés dans l’interface utilisateur à thème.) |
| Premier plan (texte) | `Environment.CommandBarTextHover` |
| Premier plan (glyphe) | `Environment.CommandBarMenuMouseOverGlyph` |
| Bordure | `Environment.CommandBarBorder` |

**Titre du menu : état enfoncé**

![Titre de menu appuyé](../../extensibility/ux-guidelines/media/0303-006_menutitlepressed.png "0303-006_MenuTitlePressed")<br />Titre de menu appuyé

![Titre de menu appuyé avec glyphe](../../extensibility/ux-guidelines/media/0303-007_menutitlewithglyphpressed.png "0303-007_MenuTitleWithGlyphPressed")<br />Titre de menu appuyé avec glyphe

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.CommandBarMenuBackgroundGradientBegin`<br/>(Les points de dégradé de ce jeton ne sont pas utilisés dans l’interface utilisateur à thème.) |
| Premier plan (texte) | `Environment.CommandBarTextActive` |
| Premier plan (glyphe) | `Environment.CommandBarMenuMouseDownGlyph` |
| Bordure | `Environment.CommandBarMenuBorder`<br />(Uniquement les côtés gauche, supérieur et droit.) |

**Titre du menu : état désactivé**

![Titre de menu désactivé avec glyphe](../../extensibility/ux-guidelines/media/0303-008_menutitlewithglyphdisabled.png "0303-008_MenuTitleWithGlyphDisabled")<br />Titre de menu désactivé avec glyphe

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | Aucun |
| Premier plan (texte) | `Environment.CommandBarTextInactive` |
| Premier plan (glyphe) | `Environment.CommandBarTextInactive` |
| Bordure | Aucun |

#### <a name="menu-items"></a>Éléments de menu
Un élément de menu individuel comporte le texte du menu et éventuellement une icône, une case à cocher ou un glyphe de sous-menu. Sa couleur d’arrière-plan et de texte change au passage du curseur de la souris. Ce jeton de couleur est une paire arrière-plan/premier plan.

![Ligne rouge d'éléments de menu](../../extensibility/ux-guidelines/media/0303-009_menuitemredline.png "0303-009_MenuItemRedline")

| Utilisez... | N’utilisez pas... |
|---|---|
| ... pour toute liste déroulante lancée à partir d’une barre de menus ou d’une barre de commandes. | ... pour toute liste déroulante dans un autre contexte. |
| | ... dans toute combinaison d’arrière-plan/premier plan autre que celle spécifiée. |

**Éléments de menu : état par défaut**

![Éléments de menu par défaut](../../extensibility/ux-guidelines/media/0303-010_menudefault.png "0303-010_MenuDefault")<br />Éléments de menu par défaut

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.CommandBarMenuBackgroundGradientBegin`<br />(Les points de dégradé de ce jeton ne sont pas utilisés dans l’interface utilisateur à thème.) |
| Premier plan (texte) | `Environment.CommandBarTextActive` |
| Premier plan (glyphe de sous-menu) | `Environment.CommandBarMenuSubmenuGlyph` |
| Bordure | `Environment.CommandBarMenuBorder` |
| Arrière-plan de canal d’icône | `Environment.CommandBarMenuIconBackground` |
| Séparateur | `Environment.CommandBarMenuSeparator` |
| Shadow | `Environment.DropShadowBackground` |

**Éléments de menu : États activés et sélectionnés**

![Menu activé](../../extensibility/ux-guidelines/media/0303-011_menuchecked.png "0303-011_MenuChecked")<br />Élément de menu activé

![Menu sélectionné](../../extensibility/ux-guidelines/media/0303-012_menuselected.png "0303-012_MenuSelected")<br />Élément de menu sélectionné

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Coche | `Environment.CommandBarCheckBox` |
| Arrière-plan de case à cocher | `Environment.CommandBarSelectedIcon` |
| Arrière-plan d’icône | `Environment.CommandBarSelected` |
| Bordure d’icône | `Environment.CommandBarSelectedBorder` |

**Éléments de menu : état du survol**

![Pointage de menu](../../extensibility/ux-guidelines/media/0303-013_menuhover.png "0303-013_MenuHover")<br />Élément de menu au pointage

![Pointage de menu activé](../../extensibility/ux-guidelines/media/0303-014_menuhoverchecked.png "0303-014_MenuHoverChecked")<br />Élément de menu coché au pointage

![Pointage de menu sélectionné](../../extensibility/ux-guidelines/media/0303-015_menuhoverselected.png "0303-015_MenuHoverSelected")<br />Élément de menu sélectionné au pointage

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.CommandBarMenuItemMouseOver` |
| Premier plan (texte) | `Environment.CommandBarMenuItemMouseOverText` |
| Premier plan (glyphe de sous-menu) | `Environment.CommandBarMenuMouseOverSubmenuGlyph` |
| Coche | `Environment.CommandBarCheckBoxMouseOver` |
| Arrière-plan de case à cocher | `Environment.CommandBarHoverOverSelectedIcon` |
| Arrière-plan d’icône | `Environment.CommandBarHoverOverSelected` |
| Bordure d’icône | `Environment.CommandBarHoverOverSelectedIconBorder` |

**Éléments de menu : état désactivé**

![Menu désactivé](../../extensibility/ux-guidelines/media/0303-016_menudisabled.png "0303-016_MenuDisabled")<br />Élément de menu désactivé

![Menu désactivé activé](../../extensibility/ux-guidelines/media/0303-017_menudisabledchecked.png "0303-017_MenuDisabledChecked")<br />Élément de menu désactivé avec coche

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Premier plan (texte) | `Environment.CommandBarTextInactive` |
| Premier plan (glyphe de sous-menu) | `Environment.CommandBarMenuSubmenuGlyph` |
| Coche | `Environment.CommandBarCheckBoxDisabled` |
| Arrière-plan de case à cocher | `Environment.CommandBarSelectedIconDisabled` |

### <a name="command-bars"></a>Barres de commandes
Une barre de commandes peut apparaître à plusieurs endroits dans l’IDE de Visual Studio, notamment dans l’étagère de commande et incorporée dans les fenêtres d’outils ou de documents.

En règle générale, utilisez toujours l’implémentation de barre de commandes standard fournie par l’environnement Visual Studio. L’utilisation du mécanisme standard permet à tous les détails visuels d’apparaître correctement et aux éléments interactifs de se comporter de manière cohérente avec les autres contrôles de barre de commandes Visual Studio. Toutefois, si vous avez besoin de créer votre propre barre de commandes, assurez-vous d’utiliser un style adéquat avec les noms de jeton suivants.

![Ligne rouge de barre de commandes](../../extensibility/ux-guidelines/media/0303-018_commandbarredline.png "0303-018_CommandBarRedline")<br />Barre de commandes (ligne rouge)

![Ligne rouge de bouton de dépassement](../../extensibility/ux-guidelines/media/0303-019_overflowbuttonredline.png "0303-019_OverflowButtonRedline")<br />Bouton de dépassement de capacité (ligne rouge)

| Utilisez... | N’utilisez pas... |
| --- | --- |
| ... à des endroits où vous avez besoin d’une barre de commandes incorporée, mais qui ne peuvent pas utiliser l’implémentation de barre de commandes Visual Studio standard. | ... pour les éléments d’interface utilisateur qui ne sont pas similaires à une barre de commandes. |
| | ... pour les composants de barre de commandes autres que ceux pour lesquels des noms de jeton sont spécifiés. |

#### <a name="command-bar-groups"></a>Groupes de barres de commandes
Un groupe de barres de commandes se compose d’un ensemble de contrôles de barre de commandes et peut contenir tout nombre de boutons, boutons partagés, menus déroulants, zones de liste modifiable ou menus. Les couleurs de ces contrôles sont régies par des noms de jeton distincts et sont décrites individuellement dans une autre section de ce guide. Un trait de séparation est utilisé pour diviser un groupe de barres de commandes en sous-groupes associés.

![Ligne rouge de groupe de barres de commandes](../../extensibility/ux-guidelines/media/0303-020_commandbargroupredline.png "0303-020_CommandBarGroupRedline")<br />Groupe de barres de commandes (ligne rouge)

| Utilisez... | N’utilisez pas... |
| --- | --- |
| ... à des endroits où vous avez besoin d’une barre de commandes incorporée, mais qui ne peuvent pas utiliser l’implémentation de barre de commandes Visual Studio standard. | ... pour les éléments d’interface utilisateur qui ne sont pas similaires à une barre de commandes. |
| | ... pour les composants de barre de commandes autres que ceux pour lesquels des noms de jeton sont spécifiés. |

**Groupe de barres de commandes : état par défaut**

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.CommandBarGradientBegin`<br />(Les points de dégradé de ce jeton ne sont pas utilisés dans l’interface utilisateur à thème.) |
| Bordure | `Environment.CommandBarToolBarBorder` |
| Poignée de redimensionnement | `Environment.CommandBarDragHandle` |
| Séparateur | `Environment.CommandBarToolBarSeparator`<br />`Environment.CommandBarToolBarSeparatorHighlight` |

#### <a name="command-icons"></a>Icônes de commande
![Ligne rouge d'icône de commande](../../extensibility/ux-guidelines/media/0303-021_commandiconredline1.png "0303-021_CommandIconRedline1")<br />Icône de commande (ligne rouge)

![Icône de commande avec texte ligne rouge](../../extensibility/ux-guidelines/media/0303-022_commandiconredline2.png "0303-022_CommandIconRedline2")<br />Icône de commande avec texte (ligne rouge)

| Utilisez... | N’utilisez pas... |
| --- | --- |
| ... pour tous les boutons qui seront placés sur une barre de commandes. | ... pour les contrôles qui ont leurs propres noms de jeton. |
| | ... dans toute combinaison d’arrière-plan/premier plan autre que celle spécifiée. |

**Icône de commande : état par défaut**

![Valeur par défaut d'icône de commande](../../extensibility/ux-guidelines/media/0303-023_commandicondefault.png "0303-023_CommandIconDefault")<br />Icône de commande par défaut

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | N/A (hérite de l’arrière-plan de la barre commandes) |
| Premier plan (texte) | `Environment.CommandBarTextActive` |
| Bordure | N/A |

**Icône de commande : état par défaut, sélectionné**

![Icône de commande sélectionnée par défaut](../../extensibility/ux-guidelines/media/0303-024_commandicondefaultselected.png "0303-024_CommandIconDefaultSelected")<br />Icône de commande sélectionnée par défaut

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.CommandBarSelected` |
| Premier plan (texte) | `Environment.CommandBarTextSelected` |
| Bordure | `Environment.CommandBarSelectedBorder` |

**Icône de commande : États de survol ou de focus**

![Icône de commande au survol ou au focus](../../extensibility/ux-guidelines/media/0303-025_commandiconhover.png "0303-025_CommandIconHover")<br />Icône de commande au survol ou au focus

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.CommandBarMouseOverBackgroundBegin`<br />(Les points de dégradé de ce jeton ne sont pas utilisés dans l’interface utilisateur à thème.) |
| Premier plan (texte) | `Environment.CommandBarTextHover` |
| Bordure | `Environment.CommandBarBorder` |

**Icône de commande : États de survol ou de focus, sélectionnés**

![Icône de commande sélectionnée au survol ou au focus](../../extensibility/ux-guidelines/media/0303-026_commandiconhoverselected.png "0303-026_CommandIconHoverSelected")<br />Icône de commande sélectionnée au survol ou au focus

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.CommandBarHoverOverSelected` |
| Premier plan (texte) | `Environment.CommandBarTextHoverOverSelected` |
| Bordure | `Environment.CommandBarHoverOverSelectedIconBorder` |

 **Icône de commande : état enfoncé**

![Icône de commande appuyée](../../extensibility/ux-guidelines/media/0303-027_commandiconpressed.png "0303-027_CommandIconPressed")<br />Icône de commande appuyée

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.CommandBarMouseDownBackgroundBegin`<br />(Les points de dégradé de ce jeton ne sont pas utilisés dans l’interface utilisateur à thème.) |
| Premier plan (texte) | `Environment.CommandBarTextMouseDown` |
| Bordure | `Environment.CommandBarBorder` |

**Icône de commande : état désactivé**

![Icône de commande désactivée](../../extensibility/ux-guidelines/media/0303-028_commandicondisabled.png "0303-028_CommandIconDisabled")<br />Icône de commande désactivée

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | N/A (hérite de l’arrière-plan de la barre commandes) |
| Premier plan (texte) | `Environment.CommandBarTextInactive` |
| Bordure | N/A |

#### <a name="command-bar-combo-boxes"></a><a name="BKMK_CommandComboBox"></a> Zones de liste déroulante de barre de commandes

> [!IMPORTANT]
> Les zones de liste modifiable ressemblent aux listes déroulantes, mais elles comprennent une zone de texte modifiable. Si votre liste déroulante n’inclut pas de zone de texte modifiable, utilisez les jetons de couleur pour les listes déroulantes de [barre de commandes](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandDropDown).

![Ligne rouge de zone de liste modifiable de barre de commandes](../../extensibility/ux-guidelines/media/0303-029_comboboxredline.png "0303-029_ComboBoxRedline")<br />Zone de liste déroulante de barre de commandes (ligne rouge)

| Utilisez... | N’utilisez pas... |
| --- | --- |
| ... lors de la création de zones de liste modifiable personnalisées. | ... pour tout ce que vous ne voulez pas toujours faire correspondre à l’interface utilisateur de la barre de commandes. |
| ... lors de la création d’un contrôle de barre de commandes similaire à une zone de liste déroulante. | ... Lorsque vous avez accès à une zone de liste déroulante avec des styles. |

**Champ d’entrée de la zone de liste déroulante de barre de commandes : état par défaut**

![Champ d’entrée de zone de liste déroulante de barre de commandes](../../extensibility/ux-guidelines/media/0303-030_comboboxinputfield.png "0303-030_ComboBoxInputField")<br />Champ d’entrée de zone de liste déroulante de barre de commandes

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.ComboBoxBackground` |
| Premier plan (texte) | `Environment.ComboBoxText` |
| Bordure | `Environment.ComboBoxBorder` |
| Séparateur | Aucun séparateur |

**Bouton de liste déroulante de barre de commandes : état par défaut**

![Bouton de déplacement de la zone de liste déroulante&#45;](../../extensibility/ux-guidelines/media/0303-031_comboboxdropdownbutton.png "0303-031_ComboBoxDropdownButton")<br />Bouton de liste déroulante de barre de commandes

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | N/A (hérite de l’arrière-plan de la barre commandes) |
| Premier plan (glyphe) | `Environment.ComboBoxGlyph` |

**Liste déroulante de barre de commandes : état par défaut**

![Liste déroulante de barre de commandes](../../extensibility/ux-guidelines/media/0303-032_comboboxdropdownlist.png "0303-032_ComboBoxDropdownList")<br />Liste déroulante de barre de commandes

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.ComboBoxPopupBackgroundBegin`<br />(Les points de dégradé de ce jeton ne sont pas utilisés dans l’interface utilisateur à thème.) |
| Premier plan (texte) | `Environment.ComboBoxItemText` |
| Bordure | `Environment.ComboBoxPopupBorder` |

**Champ d’entrée de la zone de liste déroulante de la barre de commandes : état sensitif**

![Champ d’entrée de la zone de liste déroulante de barre de commandes au survol](../../extensibility/ux-guidelines/media/0303-033_comboboxinputfieldhover.png "0303-033_ComboBoxInputFieldHover")<br />Champ d’entrée de la zone de liste déroulante de barre de commandes au survol

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.ComboBoxMouseOverBackgroundBegin`<br />(Les points de dégradé de ce jeton ne sont pas utilisés dans l’interface utilisateur à thème.) |
| Premier plan (texte) | `Environment.ComboBoxMouseOverText` |
| Bordure | `Environment.ComboBoxMouseOverBorder` |
| Séparateur | `Environment.ComboBoxMouseOverSeparator` |

 **Bouton de liste déroulante de barre de commandes : état pointé**

![Bouton déroulant de la zone de liste déroulante de barre de commandes au pointage](../../extensibility/ux-guidelines/media/0303-034_comboboxdropdownbuttonhover.png "0303-034_ComboBoxDropdownButtonHover")<br />Bouton de liste déroulante de barre de commandes au pointage

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.ComboBoxButtonMouseOverBackground` |
| Premier plan (glyphe) | `Environment.ComboBoxMouseOverGlyph` |

**Liste déroulante de barre de commandes : état de survol**

 ![Liste déroulante de la zone de liste déroulante de barre de commandes au pointage](../../extensibility/ux-guidelines/media/0303-035_comboboxdropdownlisthover.png "0303-035_ComboBoxDropdownListHover")<br />Liste déroulante de barre de commandes au pointage

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan (élément de menu) | `Environment.ComboBoxItemMouseOverBackground` |
| Premier plan (texte) | `Environment.ComboBoxItemMouseOverText` |
| Bordure (élément de menu) | `Environment.ComboBoxItemMouseOverBorder` |

 **Champ d’entrée de la zone de liste déroulante de la barre de commandes : état Focus**

![Champ d’entrée de la zone de liste déroulante de barre de commandes Active](../../extensibility/ux-guidelines/media/0303-036_comboboxinputfieldfocused.png "0303-036_ComboBoxInputFieldFocused")<br />Champ d’entrée de la zone de liste déroulante de barre de commandes Active

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.ComboBoxFocusedBackground` |
| Premier plan (texte) | `Environment.ComboBoxFocusedText` |
| Bordure | `Environment.ComboBoxFocusedBorder` |
| Séparateur | `Environment.ComboBoxFocusedButtonSeparator` |

**Bouton de liste déroulante de barre de commandes : état Focused**

![Bouton de liste déroulante de barre de commandes ciblée](../../extensibility/ux-guidelines/media/0303-037_comboboxdropdownbuttonfocused.png "0303-037_ComboBoxDropdownButtonFocused")<br />Bouton de liste déroulante de barre de commandes ciblée

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.ComboBoxFocusedButtonBackground` |
| Premier plan (glyphe) | `Environment.ComboBoxFocusedGlyph` |

 **Champ d’entrée de la zone de liste déroulante de la barre de commandes : état enfoncé**

![Champ d’entrée de zone de liste déroulante de barre de commandes appuyée](../../extensibility/ux-guidelines/media/0303-038_comboboxinputfieldpressed.png "0303-038_ComboBoxInputFieldPressed")<br />Champ d’entrée de zone de liste déroulante de barre de commandes appuyée

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.ComboBoxMouseDownBackground` |
| Premier plan (texte) | `Environment.ComboBoxMouseDownText` |
| Bordure | `Environment.ComboBoxMouseDownBorder` |
| Séparateur | `Environment.ComboBoxMouseDownSeparator` |

**Bouton de liste déroulante de barre de commandes : état enfoncé**

![Bouton de liste déroulante de la barre de commandes appuyée](../../extensibility/ux-guidelines/media/0303-039_comboboxdropdownbuttonpressed.png "0303-039_ComboBoxDropdownButtonPressed")<br />Bouton de liste déroulante de barre de commandes appuyée

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.ComboBoxButtonMouseDownBackground` |
| Premier plan (glyphe) | `Environment.ComboBoxMouseDownGlyph` |

**Champ d’entrée de la zone de liste déroulante de la barre de commandes : état désactivé**

![Champ d’entrée de zone de liste déroulante de barre de commandes désactivé](../../extensibility/ux-guidelines/media/0303-041_comboboxinputfielddisabled.png "0303-041_ComboBoxInputFieldDisabled")<br />Champ d’entrée de zone de liste déroulante de barre de commandes désactivé

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.ComboBoxDisabledBackground` |
| Premier plan (texte) | `Environment.ComboBoxDisabledText` |
| Bordure | `Environment.ComboBoxDisabledBorder` |
| Séparateur | Aucun séparateur |

**Bouton déroulant de la barre de commandes : état désactivé**

![Bouton de liste déroulante de la barre de commandes désactivée](../../extensibility/ux-guidelines/media/0303-040_comboboxdropdownbuttondisabled.png "0303-040_ComboBoxDropdownButtonDisabled")<br />Bouton de liste déroulante de barre de commandes désactivée

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | Aucun |
| Premier plan (glyphe) | `Environment.ComboBoxDisabledGlyph` |

#### <a name="command-bar-drop-downs"></a><a name="BKMK_CommandDropDown"></a> Listes déroulantes de la barre de commandes

> [!IMPORTANT]
> Les listes déroulantes ressemblent aux zones de liste modifiable, mais elles ne disposent pas de zones de texte modifiable. Si votre liste déroulante contient une zone de texte modifiable, utilisez les jetons de couleur pour les [zones de liste déroulante de barre de commandes](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandComboBox).

![Liste déroulante de barre de commandes (ligne rouge)](../../extensibility/ux-guidelines/media/0303-042_dropdownredline.png "0303-042_DropdownRedline")<br />Liste déroulante de barre de commandes (ligne rouge)

| Utilisez... | N’utilisez pas... |
| --- | --- |
| ... Lorsque vous créez des contrôles de liste déroulante personnalisés. | ... pour tout élément qui n’est pas similaire à une liste déroulante. |
| | ... pour les zones de liste modifiable ou les boutons partagés. |

**Zone de liste déroulante de barre de commandes champ : état par défaut**

![Zone de liste déroulante de barre de commandes par défaut](../../extensibility/ux-guidelines/media/0303-043_dropdownselectionfield.png "0303-043_DropdownSelectionField")<br />Zone de liste déroulante de barre de commandes par défaut

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.DropDownBackground` |
| Premier plan (texte) | `DropDownText` |
| Bordure | `DropDownBorder` |
| Séparateur | Aucun séparateur |

**Bouton de liste déroulante de barre de commandes : état par défaut**

![Bouton de liste déroulante de barre de commandes par défaut](../../extensibility/ux-guidelines/media/0303-044_dropdownbutton.png "0303-044_DropdownButton")<br />Bouton de liste déroulante de barre de commandes par défaut

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | Aucun |
| Premier plan (glyphe) | `Environment.DropDownGlyph` |

**Liste déroulante de barre de commandes : état par défaut**

![Liste déroulante de la barre de commandes par défaut](../../extensibility/ux-guidelines/media/0303-045_dropdownlist.png "0303-045_DropdownList")<br />Liste déroulante de la barre de commandes par défaut

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.DropDownPopupBackgroundBegin`<br />(Les points de dégradé de ce jeton ne sont pas utilisés dans l’interface utilisateur à thème.) |
| Premier plan (texte) | `Environment.ComboBoxItemText` |
| Bordure | `Environment.DropDownPopupBorder` |
| Shadow | `Environment.DropShadowBackground` |

**Zone de liste déroulante de barre de commandes champ : état de survol**

![Zone de liste déroulante de barre de commandes au pointage](../../extensibility/ux-guidelines/media/0303-046_dropdownselectionfieldhover.png "0303-046_DropdownSelectionFieldHover")<br />Zone de liste déroulante de barre de commandes au pointage

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.DropDownMouseOverBackgroundBegin`<br />(Les points de dégradé de ce jeton ne sont pas utilisés dans l’interface utilisateur à thème.) |
| Premier plan (texte) | `Environment.DropDownMouseOverText` |
| Bordure | `Environment.DropDownMouseOverBorder` |
| Séparateur | `Environment.DropDownButtonMouseOverSeparator` |

**Bouton de liste déroulante de barre de commandes : état pointé**

![Bouton de liste déroulante de barre de commandes au pointage](../../extensibility/ux-guidelines/media/0303-047_dropdownbuttonhover.png "0303-047_DropdownButtonHover")<br />Bouton de liste déroulante de barre de commandes au pointage

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.DropDownButtonMouseOverBackground` |
| Premier plan (glyphe) | `Environment.DropDownMouseOverGlyph` |

**Liste déroulante de barre de commandes : état de survol**

![Liste déroulante de barre de commandes au pointage](../../extensibility/ux-guidelines/media/0303-048_dropdownlisthover.png "0303-048_DropdownListHover")<br />Liste déroulante de barre de commandes au pointage

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan (élément de menu) | `Environment.ComboBoxItemMouseOverBackground` |
| Premier plan (texte) | `Environment.ComboBoxItemMouseOverText` |
| Bordure (élément de menu) | `Environment.ComboBoxItemMouseOverBorder` |

 **Zone de liste déroulante de la barre de commandes : état enfoncé**

![Déplacer le champ de sélection vers le&#45;enfoncé](../../extensibility/ux-guidelines/media/0303-049_dropdownselectionfieldpressed.png "0303-049_DropdownSelectionFieldPressed")<br />Zone de liste déroulante de la barre de commandes appuyée

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.DropDownMouseDownBackground` |
| Premier plan (texte) | `Environment.DropDownMouseDownText` |
| Bordure | `Environment.DropDownMouseDownBorder` |
| Séparateur | `Environment.DropDownButtonMouseDownSeparator` |

**Bouton de liste déroulante de barre de commandes : état enfoncé**

![Bouton de liste déroulante de barre de commandes appuyée](../../extensibility/ux-guidelines/media/0303-050_dropdownbuttonpressed.png "0303-050_DropdownButtonPressed")<br />Bouton de liste déroulante de barre de commandes appuyée

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.DropDownButtonMouseDownBackground` |
| Premier plan (glyphe) | `Environment.DropDownMouseDownGlyph` |

**Zone de liste déroulante de barre de commandes champ : état désactivé**

![Champ de sélection de la barre de commandes désactivée](../../extensibility/ux-guidelines/media/0303-051_dropdownselectionfielddisabled.png "0303-051_DropdownSelectionFieldDisabled")<br />Champ de sélection de la barre de commandes désactivée

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.DropDownDisabledBackground` |
| Premier plan (texte) | `Environment.DropDownDisabledText` |
| Bordure | `Environment.DropDownDisabledBorder` |
| Séparateur | Aucun séparateur |

**Bouton déroulant de la barre de commandes : état désactivé**

![Bouton de liste déroulante de barre de commandes désactivée](../../extensibility/ux-guidelines/media/0303-052_dropdownbuttondisabled.png "0303-052_DropdownButtonDisabled")<br />Bouton de liste déroulante de barre de commandes désactivée

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | N/A |
| Premier plan (glyphe) | `Environment.DropDownDisabledGlyph` |

#### <a name="command-bar-split-buttons"></a>Boutons partagés de la barre de commandes
Les boutons partagés partagent de nombreux noms de jeton avec d’autres contrôles de barre de commandes, tels que des boutons, menus et texte de barre de commandes. Toutes les actions nécessaires et les noms de jeton bouton de liste déroulante sont répétés ici par commodité. Les listes déroulantes de bouton partagé sont des implémentations de [menus de barre de commandes](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandMenus).

![Ligne rouge de bouton Fractionner](../../extensibility/ux-guidelines/media/0303-053_splitbuttonredline.png "0303-053_SplitButtonRedline")<br />Bouton de fractionnement de la barre de commandes (ligne rouge)

| Utilisez... | N’utilisez pas... |
| --- | --- |
| ... Lorsque vous créez un bouton partagé personnalisé. | ... pour les autres types de boutons. |
| | ... dans toute combinaison d’arrière-plan/premier plan autre que celle spécifiée. |

**Bouton de fractionnement de la barre de commandes : état par défaut**

![Bouton de fractionnement de la barre de commandes par défaut](../../extensibility/ux-guidelines/media/0303-054_splitbutton.png "0303-054_SplitButton")<br />Bouton de fractionnement de la barre de commandes par défaut

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | Aucun |
| Premier plan (texte) | `Environment.CommandBarTextActive` |
| Premier plan (glyphe) | `Environment.CommandBarSplitButtonGlyph` |
| Bordure | N/A |
| Séparateur | N/A |

**Bouton de fractionnement de la barre de commandes : état sensitif**

![Bouton partagé de barre de commandes au pointage](../../extensibility/ux-guidelines/media/0303-055_splitbuttonhover.png "0303-055_SplitButtonHover")<br />Bouton partagé de barre de commandes au pointage

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.CommandBarMouseOverBackgroundBegin`<br />(Les points de dégradé de ce jeton ne sont pas utilisés dans l’interface utilisateur à thème.) |
| Premier plan (texte) | `Environment.CommandBarTextHover` |
| Premier plan (glyphe) | `Environment.CommandBarSplitButtonMouseOverGlyph` |
| Bordure | `Environment.CommandBarBorder` |
| Séparateur | `Environment.CommandBarSplitButtonSeparator` |

**Bouton de fractionnement de la barre de commandes : état enfoncé**

![Bouton de fractionnement de la barre de commandes appuyé](../../extensibility/ux-guidelines/media/0303-056_splitbuttonpressed.png "0303-056_SplitButtonPressed")<br />Bouton de fractionnement de la barre de commandes appuyé

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.CommandBarMouseDownBackgroundBegin`<br />(Les points de dégradé de ce jeton ne sont pas utilisés dans l’interface utilisateur à thème.) |
| Premier plan (texte) | `Environment.CommandBarTextMouseDown` |
| Premier plan (glyphe) | `Environment.CommandBarSplitButtonMouseDownGlyph` |
| Bordure | `Environment.CommandBarBorder` |
| Séparateur | N/A |

**Bouton de fractionnement de la barre de commandes : état désactivé**

![Bouton de fractionnement de la barre de commandes désactivé](../../extensibility/ux-guidelines/media/0303-057_splitbuttondisabled.png "0303-057_SplitButtonDisabled")<br />Bouton de fractionnement de la barre de commandes désactivé

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | N/A |
| Premier plan (texte) | `Environment.ComboBoxItemTextInactive` |
| Premier plan (glyphe) | `Environment.CommandBarTextInactive` |
| Bordure | N/A |
| Séparateur | N/A |

#### <a name="command-bar-more-options-and-overflow-buttons"></a>Boutons « autres options » et « dépassement » de la barre de commandes
Le bouton « Autres options » est utilisé quand un groupe de barres de commandes peut être personnalisé en ajoutant ou en supprimant des boutons de barre de commandes associés. Le bouton « >> » apparaît quand une barre de commandes est tronquée en raison d’un manque d’espace horizontal. En cliquant dessus, un menu se déroule pour afficher les autres boutons de la barre de commandes qui ne pouvaient pas apparaître. Les couleurs de ces deux boutons sont contrôlées par le même ensemble de noms de jeton.

![Bouton « autres options » de la barre de commandes (ligne rouge)](../../extensibility/ux-guidelines/media/0303-058_moreoptionsredline.png "0303-058_MoreOptionsRedline")<br />Bouton « autres options » de la barre de commandes (ligne rouge)

| Utilisez... | N’utilisez pas... |
| --- | --- |
| ... pour les boutons « autres options » ou « Overflow » personnalisés. | ... pour les boutons qui n’ont pas de fonctionnalité similaire à un bouton « autres options » ou « overflow ». |

**Boutons « autres options » et « dépassement » de la barre de commandes : état par défaut**

![Bouton « autres options » dans la barre de commandes par défaut](../../extensibility/ux-guidelines/media/0303-059_moreoptions.png "0303-059_MoreOptions")<br />Bouton « autres options » dans la barre de commandes par défaut

![Bouton « overflow » de la barre de commandes par défaut](../../extensibility/ux-guidelines/media/0303-060_overflow.png "0303-060_Overflow")<br />Bouton « overflow » de la barre de commandes par défaut

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.CommandBarOptionsBackground` |
| Premier plan (glyphe) | `Environment.CommandBarOptionsGlyph` |

**Boutons « autres options » et « dépassement » de la barre de commandes : état de survol**

![Bouton « autres options » de la barre de commandes au pointage](../../extensibility/ux-guidelines/media/0303-061_moreoptionshover.png "0303-061_MoreOptionsHover")<br />Bouton « autres options » de la barre de commandes au pointage

![Bouton « overflow » de la barre de commandes au pointage](../../extensibility/ux-guidelines/media/0303-062_overflowoptions.png "0303-062_OverflowOptions")<br />Bouton « overflow » de la barre de commandes au pointage

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.CommandBarOptionsMouseOverBackgroundBegin`<br />(Les points de dégradé de ce jeton ne sont pas utilisés dans l’interface utilisateur à thème.) |
| Premier plan (glyphe) | `Environment.CommandBarOptionsMouseDownGlyph` |

**Boutons « autres options » et « dépassement » de la barre de commandes : état enfoncé**

![Bouton « autres options » dans la barre de commandes](../../extensibility/ux-guidelines/media/0303-063_moreoptionspressed.png "0303-063_MoreOptionsPressed")<br />Bouton « autres options » dans la barre de commandes

![Bouton de dépassement enfoncé](../../extensibility/ux-guidelines/media/0303-064_overflowpressed.png "0303-064_OverflowPressed")<br />Bouton « overflow » de la barre de commandes appuyée

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.CommandBarOptionsMouseDownBackgroundBegin`<br />(Les points de dégradé de ce jeton ne sont pas utilisés dans l’interface utilisateur à thème.) |
| Premier plan (glyphe) | `Environment.CommandBarOptionsMouseDownGlyph` |

## <a name="document-windows"></a>Fenêtres de document
Il n’est pas nécessaire de répliquer les fenêtres de document, car elles sont fournies par l’environnement Visual Studio. Toutefois, vous pouvez décider d’exploiter les couleurs utilisées dans les fenêtres de document, afin que votre interface utilisateur apparaisse toujours cohérente avec cette partie de l’environnement Visual Studio.

Lorsque vous utilisez des jetons de couleur de fenêtre de document, veillez à les utiliser uniquement pour les éléments similaires et toujours par paires. Si vous ne le faites pas, vous risquez d’obtenir des résultats inattendus dans votre interface utilisateur.

### <a name="document-window-frames"></a>Frames de fenêtre de document
Les fenêtres de document peuvent être ancrées dans l’IDE ou flottantes dans une fenêtre distincte. Quand une fenêtre de document flotte en dehors de l’IDE, elle se trouve toujours dans un document et les couleurs d’arrière-plan, de bordure, de texte et d’onglet sont les mêmes que lorsqu’elle fait partie de l’IDE. Toutefois, le document se trouve à l’intérieur d’un cadre qui a ses propres couleurs d’arrière-plan, de bordure et de texte. Quand les fenêtres d’outil sont ancrées dans la zone de configuration de document, elles héritent le comportement et la couleur de leurs onglets des noms de jeton de fenêtre de document.

![Fenêtre de document ancrée (ligne rouge)](../../extensibility/ux-guidelines/media/0303-065_dockeddocumentwindowredline.png "0303-065_DockedDocumentWindowRedline")<br />Fenêtre de document ancrée (ligne rouge)

![Fenêtre de document flottante (ligne rouge)](../../extensibility/ux-guidelines/media/0303-066_floatingdocumentwindowredline.png "0303-066_FloatingDocumentWindowRedline")<br />Fenêtre de document flottante (ligne rouge)

| Utilisez... | N’utilisez pas... |
| --- | --- |
| ... à tout endroit où vous créez une interface utilisateur que vous souhaitez faire correspondre à la fenêtre de document. | ...  pour toute interface utilisateur que vous ne souhaitez pas modifier automatiquement si l’interpréteur de commandes comporte une mise à jour de thème. |

**Fenêtre de document ancrée ou flottante : état par défaut**

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | Dépend du type de document |
| Premier plan (texte) | Dépend du type de document |
| Bordure | `Environment.ToolWindowBorder` |

**Frame de fenêtre de document flottant et avec focus : état par défaut**

![Frame de fenêtre de document flottant et avec focus par défaut](../../extensibility/ux-guidelines/media/0303-067_framefocused.png "0303-067_FrameFocused")<br />Frame de fenêtre de document flottant et avec focus par défaut

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.ToolWindowFloatingFrame` |
| Premier plan (texte) | `Environment.ToolWindowFloatingFrame` |
| Premier plan (glyphe) | `Environment.RaftedWindowButtonActiveGlyph` |
| Bordure | `Environment.MainWindowActiveDefaultBorder` |
| Bordure (glyphe) | `Environment.RaftedWindowButtonActiveBorder`<br />(Défini sur transparent) |

**Frame de fenêtre de document flottant sans Focus : état par défaut**

![Frame de fenêtre de document flottant sans focus par défaut](../../extensibility/ux-guidelines/media/0303-068_frameunfocused.png "0303-068_FrameUnfocused")<br />Frame de fenêtre de document flottant sans focus par défaut

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.ToolWindowFloatingFrameInactive` |
| Premier plan (texte) | `Environment.ToolWindowFloatingFrameInactive` |
| Premier plan (glyphe) | `Environment.RaftedWindowButtonInactiveGlyph` |
| Bordure | `Environment.MainWindowInactiveBorder` |
| Bordure (glyphe) | `Environment.RaftedWindowButtonInactiveBorder`<br />(Défini sur transparent) |

**Frame de fenêtre de document flottant et avec focus : état sensitif**

![Frame de fenêtre de document flottant au pointage au survol](../../extensibility/ux-guidelines/media/0303-069_framefocusedhover.png "0303-069_FrameFocusedHover")<br />Frame de fenêtre de document flottant au pointage au survol

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan (glyphe) | `Environment.RaftedWindowButtonHoverActive` |
| Premier plan (glyphe) | `Environment.RaftedWindowButtonHoverActiveGlyph` |
| Bordure (glyphe) | `Environment.RaftedWindowButtonHoverActiveBorder` |

**Frame de fenêtre de document flottant sans Focus : état sensitif**

![Frame de fenêtre de document flottant inactif au pointage](../../extensibility/ux-guidelines/media/0303-070_frameunfocusedhover.png "0303-070_FrameUnfocusedHover")<br />Frame de fenêtre de document flottant inactif au pointage

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan (glyphe) | `EnvironmentRaftedWindowButtonHoverInactive` |
| Premier plan (glyphe) | `Environment.RaftedWindowButtonHoverInactiveGlyph` |
| Bordure (glyphe) | `Environment.RaftedWindowButtonHoverInactiveBorder` |

**Frame de fenêtre de document flottant ayant le focus : état enfoncé**

![Frame de fenêtre de document flottant sur une pression](../../extensibility/ux-guidelines/media/0303-071_framefocusedpressed.png "0303-071_FrameFocusedPressed")<br />Frame de fenêtre de document flottant sur une pression

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan (glyphe) | `Environment.RaftedWindowButtonDown` |
| Premier plan (glyphe) | `Environment.RaftedWindowButtonDownGlyph` |
| Bordure (glyphe) | `Environment.RaftedWindowButtonDownBorder` |

### <a name="document-tabs"></a>Onglets de document
Les onglets de document figurent dans le canal d’onglet pour indiquer quels documents sont actuellement ouverts, ainsi que celui qui correspond au document actuellement sélectionné ou actif. Les fenêtres d’outil peuvent également être ancrées dans le canal d’onglet de document, si l’utilisateur les y place. Dans ce cas, elles utilisent les mêmes couleurs d’onglet que celles des fenêtres de document. Si vous créez une interface utilisateur que vous voulez toujours faire correspondre aux couleurs de fenêtre de document (mises à jour du thème comprises ou si de nouveaux thèmes sont installés), alors référencez ces jetons de couleur.

![Onglets de document (ligne rouge)](../../extensibility/ux-guidelines/media/0303-072_documenttabredline.png "0303-072_DocumentTabRedline")<br />Onglets de document (ligne rouge)

| Utilisez... | N’utilisez pas... |
| --- | --- |
| ... à tout endroit où vous créez une interface utilisateur pour laquelle vous souhaitez faire correspondre les onglets de document et sélectionner automatiquement les mises à jour de thème ou les nouvelles couleurs de thème. | ... pour toute interface utilisateur que vous ne souhaitez pas modifier automatiquement lorsque l’interpréteur de commandes a une mise à jour de thème. |

#### <a name="open-document-tabs"></a>Onglets de document ouvert
Chaque document ouvert possède un onglet dans le canal d’onglet de document qui affiche son nom. Les documents peuvent être soit sélectionnés, soit ouverts en arrière-plan et leurs onglets reflètent ces états :

- L’onglet sélectionné représente le document actuellement affiché dans la zone de configuration de document. Un onglet sélectionné a une bordure de document qui s’étend sur le bord supérieur de la zone de configuration de document.

- Les onglets d’arrière-plan sont les onglets de document qui ne sont pas l’onglet actuellement sélectionné. Une fois que vous cliquez dessus, ils deviennent l’onglet sélectionné et acquièrent toutes les couleurs d’arrière-plan, de bordure et de texte de ces noms de jeton.

![Ouvrir l’onglet du document (ligne rouge)](../../extensibility/ux-guidelines/media/0303-073_opendocumenttabredline.png "0303-073_OpenDocumentTabRedline")<br />Ouvrir l’onglet du document (ligne rouge)

| Utilisez... | N’utilisez pas... |
| --- | --- |
| ... Lorsque vous créez des onglets de document personnalisés. | ... pour les onglets provisoires (version préliminaire). |
| | ... pour toute interface utilisateur que vous ne souhaitez pas modifier automatiquement si l’interpréteur de commandes comporte une mise à jour de thème. |

**Onglet de document sélectionné, avec focus**

![Onglet de document sélectionné, avec focus](../../extensibility/ux-guidelines/media/0303-074_selectedtabfocused.png "0303-074_SelectedTabFocused")<br />Onglet de document sélectionné, avec focus

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.FileTabSelectedGradientTop`<br />(Les points de dégradé de ce jeton ne sont pas utilisés dans l’interface utilisateur à thème.) |
| Premier plan (texte) | `Environment.FileTabSelectedText` |
| Bordure | `Environment.FileTabSelectedBorder`<br />(Défini sur la même couleur que l’arrière-plan.) |
| Bordure de document | `Environment.FileTabDocumentBorderBackground` |

**Onglet de document sélectionné, sans focus**

![Onglet de document sélectionné, sans focus](../../extensibility/ux-guidelines/media/0303-075_selectedtabunfocused.png "0303-075_SelectedTabUnfocused")<br />Onglet de document sélectionné, sans focus

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.FileTabInactiveGradientTop`<br />(Les points de dégradé de ce jeton ne sont pas utilisés dans l’interface utilisateur à thème.) |
| Premier plan (texte) | `Environment.FileTabInactiveText` |
| Bordure | `Environment.FileTabInactiveBorder`<br />(Défini sur la même couleur que l’arrière-plan.) |
| Bordure de document | `Environment.FileTabInactiveDocumentBorderBackground` |

**Onglet document en arrière-plan : état par défaut**

![Onglet document en arrière-plan par défaut](../../extensibility/ux-guidelines/media/0303-076_backgroundtab.png "0303-076_BackgroundTab")<br />Onglet document en arrière-plan par défaut

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.FileTabBackground` |
| Premier plan (texte) | `Environment.FileTabText` |
| Bordure | `Environment.FileTabBorder`<br />(Défini sur la même couleur que l’arrière-plan.) |

**Onglet document en arrière-plan : état sensitif**

![Onglet document en arrière-plan au pointage](../../extensibility/ux-guidelines/media/0303-077_backgroundtabhover.png "0303-077_BackgroundTabHover")<br />Onglet document en arrière-plan au pointage

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.FileTabHotGradientTop`<br />(Les points de dégradé de ce jeton ne sont pas utilisés dans l’interface utilisateur à thème.) |
| Premier plan (texte) | `Environment.FileTabHotText` |
| Bordure | `Environment.FileTabHotBorder`<br />(Défini sur la même couleur que l’arrière-plan.) |

#### <a name="preview-tab"></a>Onglet d’aperçu
Également appelé onglet « provisoire ». L’onglet Aperçu apparaît sur le côté droit du canal de l’onglet de document quand l’utilisateur clique sur un élément dans la fenêtre outil Explorateur de solutions. Il sert d’aperçu du document et donne également à l’utilisateur la possibilité de laisser le document ouvert sur le côté gauche du canal d’onglet de document. Une seul onglet d’aperçu peut être ouvert à la fois. Les onglets d’aperçu possèdent deux états, arrière-plan et sélectionné, comme les onglets ouverts, et leur état actif peut être avec ou sans focus.

![Onglet Aperçu (ligne rouge)](../../extensibility/ux-guidelines/media/0303-078_previewtabredline.png "0303-078_PreviewTabRedline")<br />Onglet Aperçu (ligne rouge)

| Utilisez... | N’utilisez pas... |
| --- | --- |
| ... partout où vous créez un aperçu provisoire et souhaitez que certains éléments correspondent à la couleur d’onglet d’aperçu actuelle. | ... pour tout type de document ou d’onglet qui n’est pas provisoire (version préliminaire). |
| | ... pour toute interface utilisateur que vous ne souhaitez pas modifier automatiquement si l’interpréteur de commandes comporte une mise à jour de thème. |

**Onglet d’aperçu sélectionné**

![Onglet d’aperçu sélectionné](../../extensibility/ux-guidelines/media/0303-079_previewtabfocused.png "0303-079_PreviewTabFocused")<br />Onglet d’aperçu sélectionné

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.FileTabProvisionalSelectedActive` |
| Premier plan (texte) | `Environment.FileTabProvisionalSelectedActiveForeground` |
| Bordure | `Environment.FileTabProvisionalSelectedActiveBorder`<br />(Défini sur la même couleur que l’arrière-plan.) |
| Bordure de document | `Environment.FileTabProvisionalSelectedActiveBorder` |

**Inactif, onglet Aperçu sélectionné**

![Inactif, onglet Aperçu sélectionné](../../extensibility/ux-guidelines/media/0303-080_previewtabunfocused.png "0303-080_PreviewTabUnfocused")<br />Inactif, onglet Aperçu sélectionné

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.FileTabProvisionalSelectedInactive` |
| Premier plan (texte) | `Environment.FileTabProvisionalSelectedInactiveForeground` |
| Bordure | `Environment.FileTabProvisionalSelectedInactiveBorder` |
| Bordure de document | `Environment.FileTabProvisionalSelectedInactiveBorder` |

**Onglet Aperçu en arrière-plan : état par défaut**

![Onglet d’aperçu d’arrière-plan par défaut](../../extensibility/ux-guidelines/media/0303-081_previewbackgroundtab.png "0303-081_PreviewBackgroundTab")<br />Onglet d’aperçu d’arrière-plan par défaut

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.FileTabProvisionalInactive` |
| Premier plan (texte) | `Environment.FileTabProvisionalInactiveForeground` |
| Bordure | `Environment.FileTabProvisionalInactiveBorder`<br />(Défini sur la même couleur que l’arrière-plan.) |

**Onglet d’aperçu en arrière-plan : état sensitif**

![Onglet d’aperçu en arrière-plan au pointage](../../extensibility/ux-guidelines/media/0303-082_previewbackgroundtabhover.png "0303-082_PreviewBackgroundTabHover")<br />Onglet d’aperçu en arrière-plan au pointage

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.FileTabProvisionalHover` |
| Premier plan (texte) | `Environment.FileTabProvisionalHoverForeground` |
| Bordure | `Environment.FileTabProvisionalHoverBorder`<br />(Défini sur la même couleur que l’arrière-plan.) |

#### <a name="document-overflow-button"></a>Bouton de dépassement de capacité de document
Le bouton de dépassement de capacité de document est présent si un ou plusieurs documents sont ouverts, que l’espace vertical défini dans la configuration actuelle suffise ou non pour loger tous les onglets de document. Le menu déroulant de dépassement de capacité de document, contrôlé par les couleurs de [menu de barre de commandes](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandMenus) , affiche une liste de tous les documents ouverts, visibles et masqués, et le glyphe de dépassement de capacité change selon que tous les documents ouverts sont affichés ou non dans le canal d’onglets.

![Bouton de dépassement de capacité de document (ligne rouge)](../../extensibility/ux-guidelines/media/0303-083_overflowredline.png "0303-083_OverflowRedline")<br />Bouton de dépassement de capacité de document (ligne rouge)

| Utilisez... | N’utilisez pas... |
| --- | --- |
| ... Lorsque vous créez un bouton de dépassement de capacité de document personnalisé. | ... pour une interface utilisateur qui n’est pas similaire à un bouton de dépassement de capacité. |
| | ... pour les boutons de dépassement de capacité de barre de commandes. |

**Bouton de dépassement de capacité de document : état par défaut**

![Bouton de dépassement de capacité de document par défaut](../../extensibility/ux-guidelines/media/0303-084_overflow.png "0303-084_Overflow")<br />Bouton de dépassement de capacité de document par défaut

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.DocWellOverflowButtonBackground` |
| Premier plan (glyphe) | `Environment.DocWellOverflowButtonGlyph` |
| Bordure | N/A |

**Bouton de dépassement de capacité de document : état pointé**

![Bouton de dépassement de capacité de document au pointage](../../extensibility/ux-guidelines/media/0303-085_overflowhover.png "0303-085_OverflowHover")<br />Bouton de dépassement de capacité de document au pointage

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.DocWellOverflowButtonMouseOverBackground` |
| Premier plan (glyphe) | `Environment.DocWellOverflowButtonMouseOverGlyph` |
| Bordure | `Environment.DocWellOverflowButtonMouseOverBorder` |

**Bouton de dépassement de capacité de document : état enfoncé**

![Bouton de dépassement de capacité de document en appui](../../extensibility/ux-guidelines/media/0303-086_overflowpressed.png "0303-086_OverflowPressed")<br />Bouton de dépassement de capacité de document en appui

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.DocWellOverflowButtonMouseDownBackground` |
| Premier plan (glyphe) | `Environment.DocWellOverflowButtonMouseDownGlyph` |
| Bordure | `Environment.DocWellOverflowButtonMouseDownBorder` |

### <a name="tagging"></a>Marquage
Visual Studio prend en charge l’étiquetage, qui permet à un utilisateur de déclarer des mots clés pouvant faire l’objet d’une recherche à des fins de suivi. Par exemple, les chefs de projet et développeurs peuvent utiliser Team Foundation Server (TFS) pour étiqueter des éléments de travail. Les tableaux ci-dessous indiquent les noms de couleurs pour l’étiquette elle-même et le glyphe de l’icône de fermeture qui apparaît dans les états Pointage et Sélectionné.

![Balisage dans Visual Studio (ligne rouge)](../../extensibility/ux-guidelines/media/0303-176_taggingredline.png "0303-176_TaggingRedline")<br />Balisage dans Visual Studio (ligne rouge)

| Utilisez... | N’utilisez pas... |
| --- | --- |
| ... pour l’interface utilisateur qui prend en charge le balisage. | ... pour tout autre type d’interface utilisateur. |

#### <a name="tags"></a>Balises

**Tag : état par défaut**

![Balise par défaut](../../extensibility/ux-guidelines/media/0303-177_tag.png "0303-177_Tag")<br />Balise par défaut

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Tag.Background` |
| Premier plan (texte) | `Tag.Background` |

**Balise : état sensitif**

![Balise au pointage](../../extensibility/ux-guidelines/media/0303-178_taghover.png "0303-178_TagHover")<br />Balise au pointage

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Tag.HoverBackground` |
| Premier plan (texte) | `Tag.HoverBackgroundText` |

**Étiquette : état appuyé**

![Étiquette appuyée](../../extensibility/ux-guidelines/media/0303-179_tagpressed.png "0303-179_TagPressed")<br />Étiquette appuyée

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Tag.PressedBackground` |
| Premier plan (texte) | `Tag.PressedBackgroundText` |

**Étiquette : état sélectionné**

![Balise sélectionnée](../../extensibility/ux-guidelines/media/0303-180_tagselected.png "0303-180_TagSelected")<br />Balise sélectionnée

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Tag.SelectedBackground` |
| Premier plan (texte) | `Tag.SelectedBackgroundText` |

#### <a name="close-times-tag-glyph"></a>Glyphe de la &times; balise Close ()

**Glyphe de &times; balise de fermeture () : état par défaut**

![Glyphe de balise de fermeture par défaut ( &times; )](../../extensibility/ux-guidelines/media/0303-181_tagglyph.png "0303-181_TagGlyph")<br />Glyphe de balise de fermeture par défaut ( &times; )

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | N/A |
| Premier plan (glyphe) | `Tag.TagHoverGlyph` |

**Glyphe de &times; balise de fermeture () : état sensitif**

![Le &times; glyphe de la balise de fermeture () au pointage](../../extensibility/ux-guidelines/media/0303-182_tagglyphhover.png "0303-182_TagGlyphHover")<br />Le &times; glyphe de la balise de fermeture () au pointage

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Tag.TagHoverGlyphHoverBackground` |
| Premier plan (glyphe) | `Tag.TagHoverGlyphHover` |
| Bordure | `Tag.TagHoverGlyphHoverBorder` |

**Glyphe de &times; balise de fermeture () : état enfoncé**

![Glyphe de balise de fermeture ( &times; ) appuyé](../../extensibility/ux-guidelines/media/0303-183_tagglyphpressed.png "0303-183_TagGlyphPressed")<br />Glyphe de balise de fermeture ( &times; ) appuyé

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Tag.TagHoverGlyphPressedBackground` |
| Premier plan (glyphe) | `Tag.TagHoverGlyphPressed` |
| Bordure | `Tag.TagHoverGlyphPressedBorder` |

**Balise sélectionnée avec Close ( &times; ) Glyphs : état par défaut**

![Balise sélectionnée par défaut avec le glyphe Close ( &times; )](../../extensibility/ux-guidelines/media/0303-184_tagselected.png "0303-184_TagSelected")<br />Balise sélectionnée par défaut avec le glyphe Close ( &times; )

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | N/A |
| Premier plan (glyphe) | `Tag.TagSelectedGlyph` |

**Étiquette sélectionnée avec l’état de fermeture ( &times; ) glyphe : survol**

![Balise sélectionnée avec le &times; glyphe Close () au pointage](../../extensibility/ux-guidelines/media/0303-185_tagselectedhover.png "0303-185_TagSelectedHover")<br />Balise sélectionnée avec le &times; glyphe Close () au pointage

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Tag.TagSelectedGlyphHoverBackground` |
| Premier plan (glyphe) | `Tag.TagSelectedGlyphHover` |
| Bordure | `Tag.TagSelectedGlyphHoverBorder` |

**Balise sélectionnée avec l' &times; État Close () Glyphs : enfoncé**

![Sélectionné, étiquette appuyée avec le &times; glyphe Close ()](../../extensibility/ux-guidelines/media/0303-186_tagselectedpressed.png "0303-186_TagSelectedPressed")<br />Sélectionné, étiquette appuyée avec le &times; glyphe Close ()

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Tag.TagSelectedGlyphPressedBackground` |
| Premier plan (glyphe) | `Tag.TagSelectedGlyphPressed` |
| Bordure | `Tag.TagSelectedGlyphPressedBorder` |

## <a name="tool-windows"></a>Fenêtres d’outil
Il n’est pas nécessaire de répliquer les fenêtres outil, car elles sont fournies par l’environnement Visual Studio. Toutefois, vous pouvez décider d’exploiter les couleurs utilisées dans les fenêtres d’outil, afin que votre interface utilisateur apparaisse toujours cohérente avec cette partie de l’environnement Visual Studio.

![Fenêtre outil (ligne rouge)](../../extensibility/ux-guidelines/media/0303-087_toolwindowredline.png "0303-087_ToolWindowRedline")<br />Fenêtre outil (ligne rouge)

| Utilisez... | N’utilisez pas... |
| --- | --- |
| ... à tout endroit où vous créez une interface utilisateur pour laquelle vous souhaitez faire correspondre les fenêtres d’outils. | ... pour toute interface utilisateur que vous ne souhaitez pas modifier automatiquement si l’interpréteur de commandes comporte une mise à jour de thème. |

### <a name="tool-window-frame"></a>Cadre de fenêtre Outil
Les fenêtres d’outil dans Visual Studio sont utilisées pour de nombreuses tâches différentes et peuvent exister dans différents états. Si une fenêtre Outil est ouverte, elle peut être affectée à l’un des quatre côtés de la zone de document. Les fenêtres d’outil peuvent également flotter en dehors de l’IDE, ce qui leur permet d’être repositionnées n’importe où sur l’écran de l’utilisateur. Les fenêtres flottantes se trouvent toujours par-dessus l’IDE. Enfin, les fenêtres d’outil peuvent être ancrées comme des fenêtres de document et elles apparaissent sous la forme d’un onglet dans la zone de configuration de document. Les fenêtres d’outil ancrées comme des fenêtres de document sont colorées en partie à l’aide des noms de jeton de fenêtre de document.

![Frame de fenêtre outil (ligne rouge)](../../extensibility/ux-guidelines/media/0303-088_toolwindowframeredline.png "0303-088_ToolWindowFrameRedline")<br />Frame de fenêtre outil (ligne rouge)

| Utilisez... | N’utilisez pas... |
| --- | --- |
| ...  à tout endroit où vous créez une interface utilisateur pour laquelle vous souhaitez faire correspondre les fenêtres d’outils. | ... pour toute interface utilisateur que vous ne souhaitez pas modifier automatiquement si l’interpréteur de commandes comporte une mise à jour de thème. |

**Fenêtre outil ancrée**

![Fenêtre outil ancrée](../../extensibility/ux-guidelines/media/0303-089_toolwindowdocked.png "0303-089_ToolWindowDocked")<br />Fenêtre outil ancrée

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.ToolWindowBackground` |
| Bordure | `Environment.ToolWindowBorder` |

**Flottant, fenêtre outil ciblée**

![Flottant, fenêtre outil ciblée](../../extensibility/ux-guidelines/media/0303-090_toolwindowfocused.png "0303-090_ToolWindowFocused")<br />Flottant, fenêtre outil ciblée

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.ToolWindowBackground` |
| Bordure | `Environment.MainWindowActiveDefaultBorder` |

**Fenêtre outil flottante, inactive**

![Fenêtre outil flottante, inactive](../../extensibility/ux-guidelines/media/0303-091_toolwindowunfocused.png "0303-091_ToolWindowUnfocused")<br />Fenêtre outil flottante, inactive

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.ToolWindowBackground` |
| Bordure | `Environment.MainWindowInactiveBorder` |

### <a name="toolbox-like-windows"></a>Windows de type boîte à outils
La boîte à outils est l’une des fenêtres d’outils courantes les plus fréquemment utilisées dans Visual Studio. Il s’agit essentiellement d’un contrôle d’arborescence avec un thème spécial et un style appliqué.

![Fenêtre de type boîte à outils (ligne rouge)](../../extensibility/ux-guidelines/media/0303-189_toolboxredline.png "0303-189_ToolboxRedline")<br />Fenêtre de type boîte à outils (ligne rouge)

| Utilisez... | N’utilisez pas... |
| --- | --- |
| ... Quand vous concevez une fenêtre outil que vous voulez toujours cohérente avec la boîte à outils de l’interpréteur de commandes. | ... pour tout ce qui n’est pas similaire à l’interface utilisateur de la boîte à outils, ou si vous ne savez pas si votre interface utilisateur aura des problèmes si les couleurs de la boîte à outils de l’interpréteur de commandes changent. |

**Nœuds de boîte à outils : état par défaut**

![Nœud parent de boîte à outils par défaut](../../extensibility/ux-guidelines/media/0303-190_toolboxparentnode.png "0303-190_ToolboxParentNode")<br />Nœud parent de boîte à outils par défaut

![Nœud enfant de boîte à outils par défaut](../../extensibility/ux-guidelines/media/0303-191_toolboxchildnode.png "0303-191_ToolboxChildNode")<br />Nœud enfant de boîte à outils par défaut

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.ToolboxContent`<br />En-têtes |
| Arrière-plan | `Environment.ToolWindowBackground`<br />(Éléments individuels ou fenêtre entière si aucun contrôle n’est disponible) |
| Bordure | Aucun |
| Premier plan (glyphe) | `Environment.ToolboxContent` |
| Premier plan (texte) | `Environment.ToolboxContent` |

**Nœuds de boîte à outils enfants : état sensitif**

![Nœud enfant de boîte à outils au pointage](../../extensibility/ux-guidelines/media/0303-192_toolboxchildnodehover.png "0303-192_ToolboxChildNodeHover")<br />Nœud enfant de boîte à outils au pointage

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.ToolboxContentMouseOver`<br />(Éléments individuels uniquement) |
| Bordure | Aucun |
| Premier plan (texte) | `Environment.ToolboxContentMouseOver`<br />(Éléments individuels uniquement) |

**Nœuds de boîte à outils sélectionnés : état ciblé**

![Nœud parent de boîte à outils sélectionné](../../extensibility/ux-guidelines/media/0303-193_toolboxparentnodefocused.png "0303-193_ToolboxParentNodeFocused")<br />Nœud parent de boîte à outils sélectionné

![Nœud enfant de boîte à outils sélectionné et ciblé](../../extensibility/ux-guidelines/media/0303-194_toolboxchildnodefocused.png "0303-194_ToolboxChildNodeFocused")<br />Nœud enfant de boîte à outils sélectionné et ciblé

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `TreeView.SelectedItemActive`<br />À partir de la catégorie [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |
| Bordure | `TreeView.FocusVisualBorder`<br />À partir de la catégorie [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |
| Premier plan (glyphe) | `TreeView.SelectedItemActive`<br />À partir de la catégorie [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |
| Premier plan (texte) | `TreeView.SelectedItemActive`<br />À partir de la catégorie [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |

**Nœuds de boîte à outils sélectionnés : état sans focus**

![Nœud parent de boîte à outils sélectionné, sans focus](../../extensibility/ux-guidelines/media/0303-195_toolboxparentnodeunfocused.png "0303-195_ToolboxParentNodeUnfocused")<br />Nœud parent de boîte à outils sélectionné, sans focus

![Nœud enfant de boîte à outils sélectionné, sans focus](../../extensibility/ux-guidelines/media/0303-196_toolboxchildnodeunfocused.png "0303-196_ToolboxChildNodeUnfocused")<br />Nœud enfant de boîte à outils sélectionné, sans focus

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `TreeView.SelectedItemInactive`<br />À partir de la catégorie [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |
| Bordure | Aucun |
| Premier plan (glyphe) | `TreeView.SelectedItemInactive`<br />À partir de la catégorie [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |
| Premier plan (texte) | `TreeView.SelectedItemInactive`<br />À partir de la catégorie [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |

### <a name="tool-window-title-bar"></a>Barre de titre de fenêtre Outil
La bordure de barre de titre n’est pas une véritable bordure, il s’agit d’une ligne épaisse en haut de la barre de titre. Il n’a pas de nom de jeton pour son état sans focus.

![Barre de titre de la fenêtre outil (ligne rouge)](../../extensibility/ux-guidelines/media/0303-092_toolwindowtitlebarredline.png "0303-092_ToolWindowTitleBarRedline")<br />Barre de titre de la fenêtre outil (ligne rouge)

| Utilisez... | N’utilisez pas... |
| --- | --- |
| ... à tout endroit où vous créez une interface utilisateur pour laquelle vous souhaitez faire correspondre les fenêtres d’outils. | ... pour toute interface utilisateur que vous ne souhaitez pas modifier automatiquement si l’interpréteur de commandes comporte une mise à jour de thème. |

**Barre de titre avec focus**

![Barre de titre avec focus](../../extensibility/ux-guidelines/media/0303-093_titlebarfocused.png "0303-093_TitleBarFocused")<br />Barre de titre avec focus

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.TitleBarActiveGradientBegin`<br />(Les points de dégradé de ce jeton ne sont pas utilisés dans l’interface utilisateur à thème.) |
| Premier plan (texte) | `Environment.TitleBarActiveText` |
| Bordure | `Environment.TitleBarActiveBorder`<br />(Défini sur la même couleur que l’arrière-plan.) |
| Poignée de redimensionnement | `Environment.TitleBarDragHandleActive` |

**Barre de titre sans focus**

![Barre de titre inactive](../../extensibility/ux-guidelines/media/0303-094_titlebarunfocused.png "0303-094_TitleBarUnfocused")<br />Barre de titre sans focus

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.TitleBarInactiveGradientBegin`<br />(Les points de dégradé de ce jeton ne sont pas utilisés dans l’interface utilisateur à thème.) |
| Premier plan (texte) | `Environment.TitleBarInactiveText` |
| Bordure | N/A |
| Poignée de redimensionnement | `Environment.TitleBarDragHandle` |

#### <a name="tool-window-title-bar-buttons"></a>Boutons de la barre de titre de la fenêtre outil
![Bouton de barre de titre (ligne rouge)](../../extensibility/ux-guidelines/media/0303-095_titlebarbuttonredline.png "0303-095_TitleBarButtonRedline")<br />Bouton de barre de titre (ligne rouge)

| Utilisez... | N’utilisez pas... |
| --- | --- |
| ... pour les boutons qui apparaissent dans l’interface utilisateur et qui utilisent des jetons de couleur des barres de titre de la fenêtre outil. | ... pour les boutons qui s’affichent dans d’autres emplacements. |
| | ... dans toute combinaison d’arrière-plan/premier plan autre que celle spécifiée. |

**Boutons de la barre de titre avec focus : état par défaut**

![Boutons de barre de titre par défaut, avec focus](../../extensibility/ux-guidelines/media/0303-096_titlebarbuttonfocused.png "0303-096_TitleBarButtonFocused")<br />Boutons de barre de titre par défaut, avec focus

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | N/A |
| Premier plan (glyphe) | `Environment.ToolWindowButtonActiveGlyph` |
| Bordure | N/A |

**Boutons de la barre de titre sans Focus : état par défaut**

![Boutons de barre de titre par défaut, sans focus](../../extensibility/ux-guidelines/media/0303-097_titlebarbuttonunfocused.png "0303-097_TitleBarButtonUnfocused")<br />Boutons de barre de titre par défaut, sans focus

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | N/A |
| Premier plan (glyphe) | `Environment.ToolWindowButtonInactiveGlyph` |
| Bordure | N/A |

**Boutons de la barre de titre ciblée : état du survol**

![Boutons de barre de titre ciblés au survol](../../extensibility/ux-guidelines/media/0303-098_titlebarbuttonfocusedhover.png "0303-098_TitleBarButtonFocusedHover")<br />Boutons de barre de titre ciblés au survol

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.ToolWindowButtonHoverActive` |
| Premier plan (glyphe) | `Environment.ToolWindowButtonHoverActiveGlyph` |
| Bordure | `Environment.ToolWindowButtonHoverActiveBorder` |

**Boutons de la barre de titre sans Focus : état du survol**

![Boutons de barre de titre sans focus au pointage](../../extensibility/ux-guidelines/media/0303-099_titlebarbuttonunfocusedhover.png "0303-099_TitleBarButtonUnfocusedHover")<br />Boutons de barre de titre sans focus au pointage

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.ToolWindowButtonHoverInactive` |
| Premier plan (glyphe) | `Environment.ToolWindowButtonHoverInactiveGlyph` |
| Bordure | `Environment.ToolWindowButtonHoverInactiveBorder` |

**Boutons de la barre de titre ciblée : état enfoncé**

![Boutons de la barre de titre ciblée sur](../../extensibility/ux-guidelines/media/0303-100_titlebarbuttonfocusedpressed.png "0303-100_TitleBarButtonFocusedPressed")<br />Boutons de la barre de titre ciblée sur

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.ToolWindowButtonDown` |
| Premier plan (glyphe) | `Environment.ToolWindowButtonDownActiveGlyph` |
| Bordure | `Environment.ToolWindowButtonDownBorder` |

**Boutons de la barre de titre sans Focus : état enfoncé**

![Boutons de la barre de titre sans focus sur la pression](../../extensibility/ux-guidelines/media/0303-101_titlebarbuttonunfocusedpressed.png "0303-101_TitleBarButtonUnfocusedPressed")<br />Boutons de la barre de titre sans focus sur la pression

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.ToolWindowButtonDown` |
| Premier plan (glyphe) | `Environment.ToolWindowButtonDownInactiveGlyph` |
| Bordure | `Environment.ToolWindowButtonDownBorder` |

### <a name="tool-window-tabs"></a>Onglets de fenêtre Outil
![Onglet de fenêtre outil (ligne rouge)](../../extensibility/ux-guidelines/media/0303-102_toolwindowtabredline.png "0303-102_ToolWindowTabRedline")<br />Onglet de fenêtre outil (ligne rouge)

| Utilisez... | N’utilisez pas... |
| --- | --- |
| ... à tout endroit où vous créez une interface utilisateur pour laquelle vous souhaitez faire correspondre les fenêtres d’outils. | ... pour toute interface utilisateur que vous ne souhaitez pas modifier automatiquement si l’interpréteur de commandes comporte une mise à jour de thème. |

**Onglet de fenêtre Outil sélectionné, avec focus**

![Onglet de fenêtre Outil sélectionné, avec focus](../../extensibility/ux-guidelines/media/0303-103_toolwindowtabfocused.png "0303-103_ToolWindowTabFocused")<br />Onglet de fenêtre Outil sélectionné, avec focus

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.ToolWindowTabSelectedTab` |
| Premier plan (texte) | `Environment.ToolWindowTabSelectedActiveText` |
| Bordure | `Environment.ToolWindowTabSelectedBorder`<br />(Défini sur la même couleur que l’arrière-plan.) |

**Onglet de fenêtre Outil sélectionné, sans focus**

![Onglet de fenêtre Outil sélectionné, sans focus](../../extensibility/ux-guidelines/media/0303-104_toolwindowtabunfocused.png "0303-104_ToolWindowTabUnfocused")<br />Onglet de fenêtre Outil sélectionné, sans focus

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.ToolWindowTabSelectedTab` |
| Premier plan (texte) | `Environment.ToolWindowTabSelectedText` |
| Bordure | `Environment.ToolWindowTabSelectedBorder`<br />(Défini sur la même couleur que l’arrière-plan.) |

**Onglet de fenêtre outil d’arrière-plan : état par défaut**

![Onglet de fenêtre outil d’arrière-plan par défaut](../../extensibility/ux-guidelines/media/0303-105_toolwindowbackgroundtab.png "0303-105_ToolWindowBackgroundTab")<br />Onglet de fenêtre outil d’arrière-plan par défaut

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.ToolWindowTabGradientBegin`<br />`Environment.ToolWindowTabGradientEnd`<br />(Les points de dégradé sont définis sur la même valeur de couleur dans Visual Studio 2013.) |
| Premier plan (texte) | `Environment.ToolWindowTabText` |
| Bordure | `Environment.ToolWindowTabBorder` |

**Onglet de fenêtre outil d’arrière-plan : état sensitif**

![Onglet de fenêtre Outil d’arrière-plan au pointage](../../extensibility/ux-guidelines/media/0303-106_toolwindowbackgroundtabhover.png "0303-106_ToolWindowBackgroundTabHover")<br />Onglet de fenêtre Outil d’arrière-plan au pointage

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.ToolWindowTabMouseOverBackgroundBegin`<br />`Environment.ToolWindowTabMouseOverBackgroundEnd`<br />(Les points de dégradé sont définis sur la même valeur de couleur dans Visual Studio 2013.) |
| Premier plan (texte) | `Environment.ToolWindowTabMouseOverText` |
| Bordure | `Environment.ToolWindowTabMouseOverBorder`<br />(Défini sur la même couleur que l’arrière-plan.) |

### <a name="auto-hide-tabs"></a>Onglets à masquage automatique

![Masquer automatiquement les onglets (ligne rouge)](../../extensibility/ux-guidelines/media/0303-107_autohideredline.png "0303-107_AutoHideRedline") Masquer automatiquement les onglets (ligne rouge)

| Utilisez... | N’utilisez pas... |
| --- | --- |
| ... à tout endroit où vous créez une interface utilisateur pour laquelle vous souhaitez faire correspondre les onglets de fenêtre outil masqués automatiquement. | ... pour toute interface utilisateur que vous ne souhaitez pas modifier automatiquement si l’interpréteur de commandes comporte une mise à jour de thème. |

**Masquer automatiquement les onglets : état par défaut**

![Onglet à masquage automatique par défaut](../../extensibility/ux-guidelines/media/0303-108_autohidetab.png "0303-108_AutoHideTab")<br />Onglet à masquage automatique par défaut

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.AutoHideTabBackgroundBegin`<br />(Les points de dégradé de ce jeton ne sont pas utilisés dans l’interface utilisateur à thème.) |
| Premier plan (texte) | `Environment.AutoHideTabText` |
| Bordure | `Environment.AutoHideTabBorder` |

**Masquer automatiquement les onglets : état sensitif**

![Masquer automatiquement l'onglet au pointage](../../extensibility/ux-guidelines/media/0303-109_autohidetabhover.png "0303-109_AutoHideTabHover")<br />Masquer automatiquement l'onglet au pointage

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.AutoHideTabMouseOverBackgroundBegin`<br />(Les points de dégradé de ce jeton ne sont pas utilisés dans l’interface utilisateur à thème.) |
| Premier plan (texte) | `Environment.AutoHideTabMouseOverText` |
| Bordure | `Environment.AutoHideTabMouseOverBorder` |
