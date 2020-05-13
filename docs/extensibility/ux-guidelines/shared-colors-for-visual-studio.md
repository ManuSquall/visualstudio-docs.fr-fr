---
title: Couleurs partagées pour Visual Studio (fr) Microsoft Docs
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: 8d11b9a0-6175-4f2e-8e7f-79daee1bfd41
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3e31e5d9c3d1dc284694bd2db2a9f37d863462ad
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699930"
---
# <a name="shared-colors-for-visual-studio"></a>Couleurs partagées pour Visual Studio
Lorsque vous concevez une interface utilisateur qui utilise des éléments de coquille Visual Studio courants, ou que vous souhaitez que votre élément d’interface soit compatible avec des fonctionnalités similaires, utilisez les noms de jetons existants dans les fichiers de définition de paquets pour choisir et attribuer des couleurs. Ainsi, votre interface utilisateur reste cohérente avec l’environnement Visual Studio global et elle se met à jour automatiquement quand des thèmes sont ajoutés ou mis à jour.

Cet article décrit les éléments d’interface utilisateur communs et les noms de jeton qu’ils utilisent, que vous pouvez référencer pour créer une interface utilisateur similaire. Pour plus d’informations sur la façon d’accéder à ces jetons de couleur, consultez [The VSColor Service](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService).

Assurez-vous d’utiliser correctement les noms de jeton :

- **Utilisez des noms de jeton basés sur la fonction et non sur la couleur elle-même.** Les couleurs partagées communes sont associées à des éléments d’interface spécifiques et uniquement destinées à être utilisées pour des fonctionnalités identiques ou similaires. Par exemple, ne réutilisez pas la couleur d’une zone de liste modifiable enfoncée pour une animation de progression en rotation juste parce que vous aimez la couleur. Les fonctions de la boîte combo et l’animation sont différentes, et si la couleur associée à la boîte combo change, il pourrait ne plus être une couleur appropriée pour votre élément d’animation. Une utilisation cohérente des couleurs permet de guider vos utilisateurs et d’éviter toute confusion.

- **Associez correctement les couleurs d’arrière-plan et de texte.** Les couleurs d’arrière-plan destinées à être utilisées avec du texte possèdent une couleur de texte associée. N’utilisez pas de couleurs de texte autres que celles spécifiées pour l’arrière-plan. S’il n’y a pas de couleur de texte associée, n’utilisez pas cette couleur de fond pour n’importe quelle surface sur laquelle vous vous attendez à afficher du texte. D’autres combinaisons de textures et de couleurs de fond peuvent entraîner une interface illisible.

- **Utilisez des couleurs de contrôle appropriées à leur emplacement.** Dans certains États, certains contrôles Visual Studio n’ont pas de couleurs séparées de la frontière et de l’arrière-plan. Au lieu de cela, ils sélectionnent ces couleurs dans les surfaces qui se trouvent derrière. Veillez à toujours utiliser les noms de jeton qui conviennent à l’emplacement où vous placez le contrôle.

> [!IMPORTANT]
> N’utilisez pas de jetons trouvés dans les catégories « Page de démarrage » ou « Cidre ».

## <a name="common-shared-controls"></a>Contrôles partagés communs

Lorsque vous utilisez une barre de commande Visual Studio standard dans votre fonctionnalité, vous aurez accès à des commandes de coques de style. Vous ne devriez pas re-template ces contrôles communs. Toutefois, si vous avez besoin de créer une barre de commandes personnalisée, vous pouvez avoir besoin de générer des contrôles personnalisés également. Dans ce cas, assurez-vous d’utiliser des noms de jeton corrects pour chacun des contrôles suivants afin que votre interface utilisateur soit cohérente avec le reste de Visual Studio.

### <a name="button-controls"></a>Contrôles boutons

![Ligne rouge de contrôle Button](../../extensibility/ux-guidelines/media/0303-155_buttoncontrolredline.png "0303-155_ButtonControlRedline")

| Utiliser... | N’utilisez pas ... |
| --- | --- |
| ... pour les boutons dans le document bien que vous souhaitez intégrer avec visual Studio thèmes (Lumière, Dark, Blue, ou un thème système High Contrast). | ... pour les boutons qui s’afficheront sur un fond personnalisé qui ne fait pas partie d’un thème Visual Studio. |

**Bouton: état standard**

![Bouton standard](../../extensibility/ux-guidelines/media/03.03.Button.Standard.png "03.03.Button.Standard")<br />Bouton standard

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Bouton | `CommonControls.Button` |
| Bordure de bouton | `CommonControls.ButtonBorder` |

**Bouton: état par défaut**

![Bouton par défaut](../../extensibility/ux-guidelines/media/03.03.Button.Default.png "03.03.Button.Default")<br />Bouton par défaut

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Bouton | `CommonControls.ButtonDefault` |
| Bordure de bouton | `CommonControls.ButtonBorderDefault` |

**Bouton: État désactivé**

![Bouton désactivé](../../extensibility/ux-guidelines/media/03.03.Button.Disabled.png "03.03.Button.Disabled")<br />Bouton désactivé

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Bouton | `CommonControls.ButtonDisabled` |
| Bordure de bouton | `CommonControls.ButtonBorderDisabled` |

**Bouton: état de vol stationnaire**

![Bouton au pointage](../../extensibility/ux-guidelines/media/03.03.Button.hover.png "03.03.Button.hover")<br />Bouton au pointage

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Bouton | `CommonControls.ButtonHover` |
| Bordure de bouton | `CommonControls.ButtonBorderHover` |

**Bouton: état pressé**

![Bouton pressé](../../extensibility/ux-guidelines/media/03.03.Button.Pressed.png "03.03.Button.Pressed")<br />Bouton pressé

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Bouton | `CommonControls.ButtonPressed` |
| Bordure de bouton | `CommonControls.ButtonBorderPressed` |

**Bouton : état focalisé**

![Bouton focalisé](../../extensibility/ux-guidelines/media/03.03.Button.Focused.png "03.03.Button.Focused")<br />Bouton focalisé

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Bouton | `CommonControls.ButtonFocused` |
| Bordure de bouton | `CommonControls.ButtonBorderFocused` |

### <a name="check-box-controls"></a>Contrôles de case à cocher
![Boîte à cocher (redline)](../../extensibility/ux-guidelines/media/0303-161_checkboxredline.png "0303-161_CheckboxRedline")<br />Boîte à cocher (redline)

| Utiliser... | N’utilisez pas ... |
| --- | --- |
| ... pour les commandes de case à cocher contenues dans le document bien. | ... pour toute interface utilisateur qui n’est pas un contrôle de la case à cocher. |

**Boîte de cocher : état par défaut**

![Case à cocher](../../extensibility/ux-guidelines/media/0303-162_checkbox.png "0303-162_Checkbox")<br />Boîte à cocher par défaut

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `CommonControls.CheckBoxBackground` |
| Bordure | `CommonControls.CheckBoxBorder` |
| Texte | `CommonControls.CheckBoxText` |
| Glyphe | `CommonControls.CheckBoxGlyph` |

**Boîte à cocher : État désactivé**

![Boîte à cocher désactivée](../../extensibility/ux-guidelines/media/0303-163_checkboxdisabled.png "0303-163_CheckboxDisabled")<br />Boîte à cocher désactivée

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `CommonControls.CheckBoxBackgroundDisabled` |
| Bordure | `CommonControls.CheckBoxBorderDisabled` |
| Texte | `CommonControls.CheckBoxTextDisabled` |
| Glyphe | `CommonControls.CheckBoxGlyphDisabled` |

**Boîte à cocher: état de vol stationnaire**

 ![Case à cocher au pointage](../../extensibility/ux-guidelines/media/0303-164_checkboxhover.png "0303-164_CheckboxHover")<br />Case à cocher au pointage

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `CommonControls.CheckBoxBackgroundHover` |
| Bordure | `CommonControls.CheckBoxBorderHover` |
| Texte | `CommonControls.CheckBoxTextHover` |
| Glyphe | `CommonControls.CheckBoxGlyphHover` |

**Boîte à cocher : état pressé**

![Boîte à cocher pressée](../../extensibility/ux-guidelines/media/0303-165_checkboxpressed.png "0303-165_CheckboxPressed")<br />Boîte à cocher pressée

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `CommonControls.CheckBoxBackgroundPressed` |
| Bordure | `CommonControls.CheckBoxBorderPressed` |
| Texte | `CommonControls.CheckBoxTextPressed` |
| Glyphe | `CommonControls.CheckBoxGlyphPressed` |

**Boîte à cocher : état focalisé**

![Boîte à cocher ciblée](../../extensibility/ux-guidelines/media/0303-166_checkboxfocused.png "0303-166_CheckboxFocused")<br />Boîte à cocher ciblée

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `CommonControls.CheckBoxBackgroundFocused` |
| Bordure | `CommonControls.CheckBoxBorderFocused` |
| Texte | `CommonControls.CheckBoxTextFocused` |
| Glyphe | `CommonControls.CheckBoxGlyphFocused` |

### <a name="drop-downs-and-combo-boxes"></a>Drop-downs et boîtes combo
![Drop-down/combo box (redline)](../../extensibility/ux-guidelines/media/0303-167_dropdowncomboboxredline.png "0303-167_DropDownComboBoxRedline")<br />Drop-down/combo box (redline)

| Utiliser... | N’utilisez pas ... |
| --- | --- |
| ... pour les drop-downs et les boîtes combo dans le document bien. | ... pour toute interface utilisateur qui n’est pas une boîte de drop-down ou combo. |
| | ... pour les [baisses de](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandDropDown) barre de commande ou [les boîtes combo](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandComboBox). |

**Drop-downs et boîtes combo: état par défaut**

![Boîte de drop-down/combo par défaut](../../extensibility/ux-guidelines/media/0303-168_dropdowncombobox.png "0303-168_DropDownComboBox")<br />Boîte de drop-down/combo par défaut

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `CommonControls.ComboBoxBackground` |
| Bordure | `CommonControls.ComboBoxBorder` |
| Texte | `CommonControls.ComboBoxText` |
| Séparateur | `CommonControls.ComboBoxSeparator` |
| Glyphe | `CommonControls.ComboBoxGlyph` |
| Arrière-plan de glyphe | `CommonControls.ComboBoxGlyphBackground` |

**Drop-downs et combo boxes: état désactivé**

![Boîte de drop-down/combo désactivée](../../extensibility/ux-guidelines/media/0303-169_dropdowncomboboxdisabled.png "0303-169_DropDownComboBoxDisabled")<br />Boîte de drop-down/combo désactivée

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `CommonControls.ComboBoxBackgroundDisabled` |
| Bordure | `CommonControls.ComboBoxBorderDisabled` |
| Texte | `CommonControls.ComboBoxTextDisabled` |
| Séparateur | `CommonControls.ComboBoxSeparatorDisabled` |
| Glyphe | `CommonControls.ComboBoxGlyphDisabled` |
| Arrière-plan de glyphe | `CommonControls.ComboBoxGlyphBackgroundDisabled` |

**Drop-downs et boîtes combo: état de vol stationnaire**

![Zone de liste déroulante/liste déroulante au pointage](../../extensibility/ux-guidelines/media/0303-170_dropdowncomboboxhover.png "0303-170_DropDownComboBoxHover")<br />Zone de liste déroulante/liste déroulante au pointage

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `CommonControls.ComboBoxBackgroundHover` |
| Bordure | `CommonControls.ComboBoxBorderHover` |
| Texte | `CommonControls.ComboBoxTextHover` |
| Séparateur | `CommonControls.ComboBoxSeparatorHover` |
| Glyphe | `CommonControls.ComboBoxGlyphHover` |
| Arrière-plan de glyphe | `CommonControls.ComboBoxGlyphBackgroundHover` |

**Drop-downs et boîtes combo: état pressé**

![Baisse pressée/boîte combo](../../extensibility/ux-guidelines/media/0303-171_dropdowncomboboxpressed.png "0303-171_DropDownComboBoxPressed")<br />Baisse pressée/boîte combo

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `CommonControls.ComboBoxBackgroundPressed` |
| Bordure | `CommonControls.ComboBoxBorderPressed` |
| Texte | `CommonControls.ComboBoxTextPressed` |
| Séparateur | `CommonControls.ComboBoxSeparatorPressed` |
| Glyphe | `CommonControls.ComboBoxGlyphPressed` |
| Arrière-plan de glyphe | `CommonControls.ComboBoxGlyphBackgroundPressed` |

**Drop-downs et combo boîtes liste de la vue de l’élément: état pressé**

 ![Drop-down/combo box pressed list item view](../../extensibility/ux-guidelines/media/0303-174_dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")<br />Drop-down/combo box pressed list item view

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `CommonControls.ComboBoxListBackground`<br />`CommonControls.ComboBoxListBackgroundHover`<br />`CommonControls.ComboBoxListItemBackgroundPressed`<br />`CommonControls.ComboBoxListItemBackgroundFocused` |
| Bordure | `CommonControls.ComboBoxListBorder`<br />`CommonControls.ComboBoxListBorderHover`<br />`CommonControls.ComboBoxListBorderPressed`<br />`CommonControls.ComboBoxListBorderFocused` |
| Texte d’élément | `CommonControls.ComboBoxListItemText`<br /> `CommonControls.ComboBoxListItemTextHover`<br />`CommonControls.ComboBoxListItemTextPressed`<br />`CommonControls.ComboBoxListItemTextFocused` |
| Ombre d’arrière-plan | `CommonControls.ComboBoxListBackgroundShadow` |

**Drop-downs et boîtes combo: état focalisé**

![Drop-down/combo box avec mise au point](../../extensibility/ux-guidelines/media/0303-172_dropdowncomboboxfocused.png "0303-172_DropDownComboBoxFocused")<br />Drop-down/combo box avec mise au point

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `CommonControls.ComboBoxBackgroundFocused` |
| Bordure | `CommonControls.ComboBoxBorderFocused` |
| Texte | `CommonControls.ComboBoxTextFocused` |
| Séparateur | `CommonControls.ComboBoxSeparatorFocused` |
| Glyphe | `CommonControls.ComboBoxGlyphFocused` |
| Arrière-plan de glyphe | `CommonControls.ComboBoxGlyphBackgroundFocused` |

**Drop-downs et combo boxes: sélection d’entrées de texte**

![Sélection d’entrées de texte Drop-down/combo box](../../extensibility/ux-guidelines/media/0303-173_dropdowncomboboxtextinput.png "0303-173_DropDownComboBoxTextInput")<br />Sélection d’entrées de texte Drop-down/combo box

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Surligner | `CommonControls.ComboBoxTextInputSelection` |

### <a name="tabular-data-grid-controls"></a>Contrôles de données tabulaires (grille)
Les contrôles de données tabulaires, également appelés contrôles de grille, sont des contrôles communs pour Visual Studio qui peuvent être utilisés pour présenter des grandes quantités de données dans plusieurs colonnes. Les contrôles de données tabulaires standard se trouvent à plusieurs endroits dans Visual Studio : la fenêtre Outil Liste d’erreurs, les rapports IntelliTrace et l’affichage du tas de mémoire, entre autres. Utilisez toujours les contrôles de données tabulaires standard fournis. Dans de rares cas, vous pouvez ne pas avoir accès aux contrôles de données tabulaires standard. Si tel est le cas, utilisez les noms de jeton suivants pour veiller à ce que votre interface utilisateur soit cohérente avec les autres contrôles de données tabulaires dans Visual Studio.

![Contrôle des données/grilles tabulaires (ligne rouge)](../../extensibility/ux-guidelines/media/0303-197_tabulardatagridcontrolredline.png "0303-197_TabularDataGridControlRedline")<br />Contrôle des données/grilles tabulaires (ligne rouge)

| Utiliser... | N’utilisez pas ... |
| --- | --- |
| ... pour les commandes tabulaires ou de grille. | ... pour toute interface utilisateur qui n’est pas un contrôle tabulaire ou de grille. |

#### <a name="column-headers"></a>En-têtes de colonne
Les en-têtes de colonnes comprennent un arrière-plan, une bordure, le texte du titre et un éventuel glyphe généralement utilisé pour trier une grille selon cette colonne.

**En-tête de colonne : état par défaut**

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Header.Default` |
| Premier plan (texte) | `Environment.CommandBarTextActive` |
| Premier plan (glyphe) | `Header.Glyph` |
| Bordure | `Header.SeparatorLine` |

**Tête de colonne : état de vol stationnaire**

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Header.MouseOver` |
| Premier plan (texte) | `Environment.CommandBarTextHover` |
| Premier plan (glyphe) | `Header.MouseOverGlyph` |
| Bordure | `Header.SeparatorLine` |

**En-tête de colonne : état pressé**

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `CommonControls.CheckBoxBackgroundPressed` |
| Premier plan (texte) | `CommonControls.CheckBoxBorderPressed` |
| Premier plan (glyphe) | `CommonControls.CheckBoxTextPressed` |
| Bordure | `CommonControls.CheckBoxGlyphPressed` |

#### <a name="list-view-items"></a>Éléments de la vue Liste
 Les éléments de la vue Liste comprennent un arrière-plan et le contenu. Le contenu peut être du texte, une icône ou les deux.

**Afficher les éléments de liste : état par défaut**

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | Transparent |
| Premier plan (texte) | `Environment.CommandBarTextActive` |
| Bordure | None |

**Éléments de vue de liste : état actif**

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `TreeView.SelectedItemActive` |
| Premier plan (texte) | `TreeView.SelectedItemActiveText` |
| Bordure | None |

**Articles de vue de liste : état inactif**

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `TreeView.SelectedItemInactive` |
| Premier plan (texte) | `TreeView.SelectedItemInactiveText` |
| Bordure | None |

### <a name="ui-text"></a>Texte de l’interface utilisateur

#### <a name="instructional-text"></a>Texte pédagogique
Le texte pédagogique donne une explication principale importante de ce qu’il faut faire dans un dialogue ou une page de document.

![Texte pédagogique par défaut](../../extensibility/ux-guidelines/media/0303_InstructionalText.png "0303_InstructionalText.png")<br />Texte pédagogique par défaut

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Au premier plan (texte) | `Environment.ControlText` |

#### <a name="secondary-instructional-text"></a>Texte pédagogique secondaire
Dans les pages de documents avec beaucoup de texte et de contrôles, certains textes pédagogiques utilise une valeur de couleur différente. Cela permet de transmettre quelles informations sont les plus importantes et de réduire la densité globale des éléments d’interface utilisateur. (Voir aussi la section ci-dessous sur le texte de l’indice.)

![Texte pédagogique secondaire](../../extensibility/ux-guidelines/media/0303_SecondaryInstructionalText.png "0303_SecondaryInstructionalText.png")<br />Texte pédagogique secondaire

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Au premier plan (texte) | `Environment.ControlEditHintText` |

#### <a name="hint-text"></a>Texte de l’astuce
Le texte de l’indice apparaît dans un contrôle vide, sous un contrôle, ou sur une surface de document vide pour montrer à l’utilisateur ce qu’il faut faire ensuite. Vous pouvez utiliser du texte d’indice avec des arrière-plans de fenêtre ou de contrôle.

**Texte d’indice par défaut**

![Texte d’indice par défaut](../../extensibility/ux-guidelines/media/0303_HintText.png "0303_HintText.png")<br />Texte d’indice par défaut

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Au premier plan (texte) | `Environment.ControlEditHintText` |

**Texte d’indice requis**

![Texte d’indice requis](../../extensibility/ux-guidelines/media/0303_RequiredHintText.png "0303_RequiredHintText.png")<br />Texte d’indice requis

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Au premier plan (texte) | `Environment.ControlRequiredHintText` |
| Arrière-plan | `Environment.ControlRequiredBackground` |

**Texte de contrôle de la boîte de recherche**

> Voir [les boîtes de recherche](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_SearchBoxes) pour d’autres jetons de couleur liés au contrôle de recherche.

![Texte de contrôle de la boîte de recherche](../../extensibility/ux-guidelines/media/0303_SearchBoxControl.png "0303_SearchBoxControl.png")<br />Texte de contrôle de la boîte de recherche

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Au premier plan (texte) | `SearchControl.UnfocusedWatermarkText` |

### <a name="hyperlink"></a>Hyperlink
L’hyperlien est un contrôle qui n’a pas de paire de premier plan/arrière-plan. Dans tous les cas, utilisez la couleur hyperlien de premier plan, qui apparaîtra correctement sur les fonds foncés, gris et blancs. Si vous n’utilisez pas le jeton de couleur pour le contrôle hyperlien, vous verrez la couleur du système par défaut pour "pressé", qui clignotera en rouge. C’est le signal que le contrôle n’utilise pas le jeton de couleur environnement correct.

![Hyperlien (ligne rouge)](../../extensibility/ux-guidelines/media/0303-133_hyperlinkredline.png "0303-133_HyperlinkRedline")<br />Hyperlien (ligne rouge)

| Utiliser... | N’utilisez pas ... |
| --- | --- |
| ... lorsque vous avez besoin de créer un lien hypertexte personnalisé. | ... pour tout ce qui n’est pas un lien hypertexte. |

**Hyperlink: état par défaut**

![Hyperlien par défaut](../../extensibility/ux-guidelines/media/0303-134_hyperlink.png "0303-134_Hyperlink")<br />Hyperlien par défaut

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Premier plan (texte) | `Environment.PanelHyperlink` |

**Hyperlien : état de vol stationnaire**

![Lien hypertexte au pointage](../../extensibility/ux-guidelines/media/0303-135_hyperlinkhover.png "0303-135_HyperlinkHover")<br />Lien hypertexte au pointage

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Premier plan (texte) | `Environment.PanelHyperlinkHover` |

**Hyperlien : état pressé**

![Hyperlien pressé](../../extensibility/ux-guidelines/media/0303-136_hyperlinkpressed.png "0303-136_HyperlinkPressed")<br />Hyperlien pressé

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Premier plan (texte) | `Environment.PanelHyperlinkPressed` |

**Hyperlien : état désactivé**

![Hyperlien désactivé](../../extensibility/ux-guidelines/media/0303-137_hyperlinkdisabled.png "0303-137_HyperlinkDisabled")<br />Hyperlien désactivé

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Premier plan (texte) | `Environment.PanelHyperlinkDisabled` |

### <a name="infobars"></a>Infobars (Infobars)
Les barres d’informations sont utilisées pour fournir plus d’informations sur un contexte donné et apparaissent toujours en haut d’une fenêtre de document ou d’outil.

![Infobar (ligne rouge)](../../extensibility/ux-guidelines/media/0303-138_infobarredline.png "0303-138_InfobarRedline")<br />Infobar (ligne rouge)

| Utiliser... | N’utilisez pas ... |
| --- | --- |
| ... lors de la création d’infobars personnalisés. | ... pour les éléments d’interface utilisateur qui ne sont pas similaires à une infobar. |

**Infobar: État par défaut**

![Infobar par défaut](../../extensibility/ux-guidelines/media/0303-139_infobar.png "0303-139_Infobar")<br />Infobar par défaut

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `InfoBar.InfoBarBackground` |
| Premier plan (texte) | `InfoBar.InfoBar` |
| Bordure | `InfoBar.InfoBarBorder` |

**Infobar Close&times;( ) bouton: état par défaut**

![Infobar par&times;défaut Fermer ( ) bouton](../../extensibility/ux-guidelines/media/0303_InfobarCloseDefault.png "0303_InfobarCloseDefault.png")<br />Infobar par&times;défaut Fermer ( ) bouton

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `InfoBar.CloseButton` |
| Bordure | `InfoBar.CloseButtonBorder` |
| Glyphe | `InfoBar.CloseButtonGlyph` |

**Infobar Fermer&times;( ) bouton: état de vol stationnaire**

![Infobar Fermer&times;( ) bouton sur le plan stationnaire](../../extensibility/ux-guidelines/media/0303_InfobarCloseHover.png "0303_InfobarCloseHover.png")<br />Infobar Fermer&times;( ) bouton sur le plan stationnaire

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `InfoBar.CloseButtonHover` |
| Bordure | `InfoBar.CloseButtonHoverBorder` |
| Glyphe | `InfoBar.CloseButtonHoverGlyph` |

**Infobar Close&times;( ) bouton: État pressé**

![Infobar pressé&times;Fermer ( ) bouton](../../extensibility/ux-guidelines/media/0303_InfobarClosePressed.png "0303_InfobarClosePressed.png")<br />Infobar pressé&times;Fermer ( ) bouton

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `InfoBar.CloseButtonDown` |
| Bordure | `InfoBar.CloseButtonDownBorder` |
| Glyphe | `InfoBar.CloseButtonDownGlyph` |

**Bouton hyperlien Infobar : état par défaut**

![Bouton hyperlien infobar par défaut](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonDefault.png "0303_InfobarHyperlinkButtonDefault.png")<br />Bouton hyperlien infobar par défaut

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Au premier plan (texte) | `InfoBar.Hyperlink` |

**Bouton hyperlien Infobar : état de vol stationnaire**

![Bouton hyperlien Infobar sur le plan stationnaire](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonHover.png "0303_InfobarHyperlinkButtonHover.png")<br />Bouton hyperlien Infobar sur le plan stationnaire

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Au premier plan (texte) | `Infobar.HyperlinkMouseOver`<br />(Avec le soulignement) |

**Bouton hyperlien Infobar : état pressé**

![Bouton hyperlien infobar pressé](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonPressed.png "0303_InfobarHyperlinkButtonPressed.png")<br />Bouton hyperlien infobar pressé

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Au premier plan (texte) | `Infobar.HyperlinkMouseDown`<br />(Avec le soulignement) |

**Hyperlien en ligne Infobar (dans une phrase): état par défaut**

![Bouton hyperlien infobar en ligne par défaut](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkButtonDefault.png "0303_InfobarHyperlinkButtonDefault.png")<br />Bouton hyperlien infobar en ligne par défaut

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Au premier plan (texte) | `InfoBar.Hyperlink` |

**Infobar hyperlien en ligne (dans une phrase): état de vol stationnaire**

![Bouton hyperlien en ligne Infobar sur le plan stationnaire](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkInlineHover.png "0303_InfobarHyperlinkInlineHover.png")<br />Bouton hyperlien en ligne Infobar sur le plan stationnaire

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Au premier plan (texte) | `Infobar.HyperlinkMouseOver`<br />(Avec le soulignement) |

**Infobar hyperlien en ligne (dans une phrase): état pressé**

![Bouton hyperlien en ligne infobar pressé](../../extensibility/ux-guidelines/media/0303_InfobarHyperlinkInlinePressed.png "0303_InfobarHyperlinkInlinePressed.png")<br />Bouton hyperlien en ligne infobar pressé

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Au premier plan (texte) | `Infobar.HyperlinkMouseDown`<br />(Avec le soulignement) |

**Bouton Infobar : état par défaut**

![Bouton infobar par défaut](../../extensibility/ux-guidelines/media/0303_InfobarButtonDefault.png "0303_InfobarButtonDefault.png")<br />Bouton infobar par défaut

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `InfoBar.Button` |
| Au premier plan (texte) | `InfoBar.Button` |
| Bordure | `InfoBar.ButtonBorder` |

**Bouton Infobar: état de vol stationnaire**

![Bouton Infobar sur le plan stationnaire](../../extensibility/ux-guidelines/media/0303_InfobarButtonHover.png "0303_InfobarButtonHover.png")<br />Bouton Infobar sur le plan stationnaire

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `InfoBar.ButtonMouseOver` |
| Au premier plan (texte) | `InfoBar.ButtonMouseOver` |
| Bordure | `InfoBar.ButtonMouseOverBorder` |

**Bouton Infobar : état pressé**

![Bouton infobar pressé](../../extensibility/ux-guidelines/media/0303_InfobarButtonPressed.png "0303_InfobarButtonPressed.png")<br />Bouton infobar pressé

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `InfoBar.ButtonMouseDown` |
| Au premier plan (texte) | `InfoBar.ButtonMouseDown` |
| Bordure | `InfoBar.ButtonMouseDownBorder` |

**Bouton Infobar : état désactivé**

![Bouton d’infobar désactivé](../../extensibility/ux-guidelines/media/0303_InfobarButtonDisabled.png "0303_InfobarButtonDisabled.png")<br />Bouton d’infobar désactivé

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `InfoBar.ButtonDisabled` |
| Au premier plan (texte) | `InfoBar.ButtonDisabled` |
| Bordure | `InfoBar.ButtonDisabledBorder` |

**Bouton Infobar : état focalisé**

![Bouton infobar focalisé](../../extensibility/ux-guidelines/media/0303_InfobarButtonFocus.png "0303_InfobarButtonFocus.png")<br />Bouton infobar focalisé

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `InfoBar.ButtonFocus` |
| Au premier plan (texte) | `InfoBar.ButtonFocus` |
| Bordure | `InfoBar.ButtonFocusBorder` |

### <a name="scroll-bars"></a>Barres de défilement
Les barres de défilement sont stylées par l’environnement Visual Studio, et n’ont pas besoin d’être sur le thème. Cependant, vous pouvez décider que vous voulez tirer parti des couleurs utilisées dans les barres de défilement de sorte que votre interface utilisateur semble toujours compatible avec cette partie de l’environnement Visual Studio.

![Barre de défilement (redline)](../../extensibility/ux-guidelines/media/0303-140_scrollbarredline.png "0303-140_ScrollbarRedline")<br />Barre de défilement (redline)

| Utiliser... | N’utilisez pas ... |
| --- | --- |
| ... lorsque vous créez l’interface utilisateur que vous souhaitez faire correspondre les barres de défilement Visual Studio. | ... pour tout ce que vous ne voulez pas toujours correspondre à l’interface utilisateur barre de défilement. |

**Barre de défilement : état par défaut**

![Barre de défilement par défaut](../../extensibility/ux-guidelines/media/0303-141_scrollbar.png "0303-141_Scrollbar")<br />Barre de défilement par défaut

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Barre de défilement | `Environment.ScrollBarBackground` |
| Premier plan (curseur de défilement) | `Environment.ScrollBarThumbBackground` |

**Barre de défilement : état de vol stationnaire**

![Barre de défilement au pointage](../../extensibility/ux-guidelines/media/0303-143_scrollbarhover.png "0303-143_ScrollbarHover")<br />Barre de défilement au pointage

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Barre de défilement | `Environment.ScrollBarBackground` |
| Premier plan (curseur de défilement) | `Environment.ScrollBarThumbMouseOverBackground` |

*Barre de défilement : état pressé**

![Barre de défilement pressée](../../extensibility/ux-guidelines/media/0303-145_scrollbarpressed.png "0303-145_ScrollbarPressed")<br />Barre de défilement pressée

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Barre de défilement | `Environment.ScrollBarBackground` |
| Premier plan (curseur de défilement) | `Environment.ScrollBarThumbPressedBackground` |

**Flèche de barre de défilement : état par défaut**

![Flèche de barre de défilement par défaut](../../extensibility/ux-guidelines/media/0303-142_scrollbararrow.png "0303-142_ScrollbarArrow")<br />Flèche de barre de défilement par défaut

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.ScrollBarArrowBackground`<br />(Définir à la même couleur que la barre de défilement.) |
| Premier plan (glyphe) | `Environment.ScrollBarArrowGlyph` |

**Flèche de barre de défilement : état de plan plan plan planer**

![Flèche de barre de défilement au pointage](../../extensibility/ux-guidelines/media/0303-144_scrollbararrowhover.png "0303-144_ScrollbarArrowHover")<br />Flèche de barre de défilement au pointage

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.ScrollBarArrowMouseOverBackground`<br />(Définir à la même couleur que la barre de défilement.) |
| Premier plan (glyphe) | `Environment.ScrollBarArrowGlyphMouseOver` |

**Flèche de barre de défilement : état pressé**

![Flèche de barre de défilement pressée](../../extensibility/ux-guidelines/media/0303-146_scrollbararrowpressed.png "0303-146_ScrollbarArrowPressed")<br />Flèche de barre de défilement pressée

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.ScrollBarArrowPressedBackground`<br />(Définir à la même couleur que la barre de défilement.) |
| Premier plan (glyphe) | `Environment.ScrollBarArrowGlyphPressed` |

### <a name="search-boxes"></a><a name="BKMK_SearchBoxes"></a>Boîtes de recherche
Si possible, utilisez le contrôle de recherche commun fourni par l’environnement Visual Studio. Les couleurs de zone de recherche se trouvent dans la catégorie « SearchControl » du fichier **ShellColors.pkgdef** qui contient les noms de jeton du champ d’entrée, du bouton d’action, du bouton de liste déroulante et du menu déroulant.

Une zone de recherche peut être dans plusieurs états, dont certains s’excluent mutuellement :

- Les états « avec focus » ou « sans focus » font référence à la présence ou non du curseur dans la zone de texte.

- Les états « actif » ou « inactif » font référence à l’éventuel entrée par l’utilisateur d’une requête de recherche dans la zone de texte.

- L’état « pointage » signifie que l’utilisateur a placé le curseur de la souris au-dessus de la zone de recherche (cet état remplace tous les autres états).

- L’état « désactivé » signifie que la fonctionnalité de recherche est désactivée pour le contexte actuel.

![Boîte de recherche (redline)](../../extensibility/ux-guidelines/media/0303-110_searchboxredline.png "0303-110_SearchBoxRedline")<br />Boîte de recherche (redline)

| Utiliser... | N’utilisez pas ... |
| --- | --- |
| ... lorsque vous concevez une boîte de recherche personnalisée. | ... pour tout ce qui n’est pas une boîte de recherche. |
| | ... pour tout ce que vous ne voulez pas toujours correspondre à l’interface utilisateur boîte de recherche. |

**Champ d’entrée de recherche ciblé**

![Champ d’entrée de recherche ciblé](../../extensibility/ux-guidelines/media/0303-111_searchinputfieldfocused.png "0303-111_SearchInputFieldFocused")<br />Champ d’entrée de recherche ciblé

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `SearchControl.FocusedBackground` |
| Premier plan (texte) | `SearchControl.FocusedBackground` |
| Bordure | `SearchControl.FocusedBorder` |
| Séparateur | `SearchControl.FocusedDropDownSeparator` |

**Champ d’entrée de recherche actif non focalisé**

![Champ d'entrée de recherche inactif](../../extensibility/ux-guidelines/media/0303-114_searchinputfieldunfocused.png "0303-114_SearchInputFieldUnfocused")<br />Champ d’entrée de recherche actif non focalisé

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `SearchControl.SearchActiveBackground` |
| Premier plan (texte) | `SearchControl.SearchActiveBackground` |
| Bordure | `SearchControl.UnfocusedBorder` |
| Séparateur | `SearchControl.DropDownSeparator` |

**Champ d’entrée de recherche non focalisé et inactif**

![Champ d’entrée de recherche non focalisé et inactif](../../extensibility/ux-guidelines/media/0303-114-1_searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")<br />Champ d’entrée de recherche non focalisé et inactif

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `SearchControl.Unfocused` |
| Premier plan (texte) | `SearchControl.Unfocused` |
| Bordure | `SearchControl.UnfocusedBorder` |
| Séparateur | `SearchControl.DropDownSeparator` |

**Champ d’entrée de recherche mis en évidence (texte seulement)**

![Champ d’entrée de recherche mis en évidence](../../extensibility/ux-guidelines/media/0303-120_searchinputfieldhighlight.png "0303-120_SearchInputFieldHighlight")<br />Champ d’entrée de recherche mis en évidence

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `SearchControl.Selection` |
| Premier plan (texte) | `SearchControl.FocusedBackground` |
| Bordure | None |
| Séparateur | `SearchControl.FocusedDropDownSeparator` |

**Champ d’entrée de recherche désactivé**

![Champ d’entrée de recherche désactivé](../../extensibility/ux-guidelines/media/0303-121_searchinputfielddisabled.png "0303-121_SearchInputFieldDisabled")<br />Champ d’entrée de recherche désactivé

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `SearchControl.Disabled` |
| Premier plan (texte) | `SearchControl.Disabled` |
| Bordure | `SearchControl.DisabledBorder` |
| Séparateur | `SearchControl.DropDownSeparator` |

**Bouton d’action de recherche focalisé**

![Bouton d'action de recherche actif](../../extensibility/ux-guidelines/media/0303-112_searchactionbuttonfocused.png "0303-112_SearchActionButtonFocused")<br />Bouton d’action de recherche focalisé

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | None |
| Premier plan (glyphe Rechercher) | `SearchControl.SearchGlyph` |
| Premier plan (glyphe Arrêter) | `SearchControl.StopGlyph` |
| Premier plan (glyphe Effacer) | `SearchControl.ClearGlyph` |
| Bordure | N/A |

**Bouton d’action de recherche non focalisé**

![Bouton d’action de recherche non focalisé](../../extensibility/ux-guidelines/media/0303-115_searchactionbuttonunfocused.png "0303-115_SearchActionButtonUnfocused")<br />Bouton d’action de recherche non focalisé

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | N/A |
| Premier plan (glyphe Rechercher) | `SearchControl.SearchGlyph` |
| Premier plan (glyphe Arrêter) | `SearchControl.StopGlyph` |
| Premier plan (glyphe Effacer) | `SearchControl.ClearGlyph` |
| Bordure | N/A |

**Bouton d’action de recherche pressé**

![Bouton d’action de recherche pressé](../../extensibility/ux-guidelines/media/0303-116-1_searchactionbuttonpressed.png "0303-116-1_SearchActionButtonPressed")<br />Bouton d’action de recherche pressé

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `SearchControl.ActionButtonMouseDown` |
| Premier plan (glyphe) | `SearchControl.ActionButtonMouseDownGlyph` |
| Bordure | `SearchControl.ActionButtonMouseDownBorder` |

**Bouton d’action de recherche désactivé**

![Bouton d'action de recherche désactivé](../../extensibility/ux-guidelines/media/0303-122_searchactionbuttondisabled.png "0303-122_SearchActionButtonDisabled")<br />Bouton d’action de recherche désactivé

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | None |
| Premier plan (glyphe) | `SearchControl.ActionButtonDisabledGlyph` |
| Bordure | None |

**Bouton de drop-down de recherche focalisé**

![Bouton de drop-down de recherche focalisé](../../extensibility/ux-guidelines/media/0303-113_searchdropdownbuttonfocused.png "0303-113_SearchDropdownButtonFocused")<br />Bouton de drop-down de recherche focalisé

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `SearchControl.FocusedDropDownButton` |
| Premier plan (glyphe) | `SearchControl.FocusedDropDownButtonGlyph` |
| Bordure | `SearchControl.FocusedDropDownButtonBorder` |

**Bouton de chute de recherche non focalisé**

![Bouton de chute de recherche non focalisé](../../extensibility/ux-guidelines/media/0303-116_searchdropdownbuttonunfocused.png "0303-116_SearchDropdownButtonUnfocused")<br />Bouton de chute de recherche non focalisé

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `SearchControl.UnfocusedDropDownButton` |
| Premier plan (glyphe) | `SearchControl.UnfocusedDropDownButtonGlyph` |
| Bordure | `SearchControl.UnfocusedDropDownButtonBorder` |

**Bouton de chute de recherche pressé**

![Bouton de chute de recherche pressé](../../extensibility/ux-guidelines/media/0303-116-2_searchdropdownbuttonpressed.png "0303-116-2_SearchDropdownButtonPressed")<br />Bouton de chute de recherche pressé

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `SearchControl.MouseDownDropDownButton` |
| Premier plan (glyphe) | `SearchControl.MouseDownDropDownButtonGlyph` |
| Bordure | `SearchControl.MouseDownDropDownButtonBorder` |

**Bouton de chute de recherche désactivé**

![Bouton de chute de recherche désactivé](../../extensibility/ux-guidelines/media/0303-123_searchdropdownbuttondisabled.png "0303-123_SearchDropdownButtonDisabled")<br />Bouton de chute de recherche désactivé

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | None |
| Premier plan (glyphe) | `SearchControl.DisabledDownButtonGlyph` |
| Bordure | None |

#### <a name="search-drop-down-lists"></a>Listes déroulantes de recherche
Le menu de la boîte de recherche est un peu plus complexe que les autres menus déroulants de Visual Studio. Les sections « recherches suggérées » et « options de recherche » peuvent apparaître seules ou ensemble dans le menu, et chacune est colorée séparément. Une ligne sépare également ces deux sections quand elles apparaissent ensemble et une bordure entoure l’ensemble du menu déroulant.

![Liste d’abandon de recherche (redline)](../../extensibility/ux-guidelines/media/0303-124_searchdropdownredline.png "0303-124_SearchDropdownRedline")<br />Liste d’abandon de recherche (redline)

| Utiliser... | N’utilisez pas ... |
| --- | --- |
| ... lorsque vous créez une liste de recherche personnalisée. | ... pour les listes de décrochage qui apparaissent dans d’autres contextes. |
| ... les noms de jetons corrects pour les composants de liste corrects. | ... dans n’importe quelle combinaison de fond/premier plan autre que spécifiée. |

**Rechercher des éléments de liste d’abandon**

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Bordure | `SearchControl.PopupBorder` |
| Séparateur | `SearchControl.PopupSectionHeaderSeparator` |
| Shadow | `Environment.DropShadowBackground` |

**Recherches suggérées : état par défaut**

![Recherches suggérées par défaut](../../extensibility/ux-guidelines/media/0303-125_searchsuggested.png "0303-125_SearchSuggested")<br />Recherches suggérées par défaut

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `SearchControl.PopupItemsListBackgroundGradientBegin`<br />(Gradient s’arrête pour ce jeton non utilisé dans l’interface utilisateur thématique.) |
| Premier plan (texte) | `SearchControl.PopupItemText` |

**Recherches suggérées : état de vol stationnaire**

![Recherches suggérées sur le plan stationnaire](../../extensibility/ux-guidelines/media/0303-128_searchsuggestedhover.png "0303-128_SearchSuggestedHover")<br />Recherches suggérées sur le plan stationnaire

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br />(Gradient s’arrête pour ce jeton non utilisé dans l’interface utilisateur thématique.) |
| Premier plan (texte) | `SearchControl.PopupMouseOverItemText` |
| Bordure | `SearchControl.PopupControlMouseOverBorder` |

**Options de recherche : état par défaut**

![Case à cocher de recherche](../../extensibility/ux-guidelines/media/0303-126_searchcheckbox.png "0303-126_SearchCheckbox")<br />Options de recherche par défaut (case à cocher)

![Options de recherche](../../extensibility/ux-guidelines/media/0303-127_searchoptions.png "0303-127_SearchOptions")<br />Options de recherche par défaut (lien)

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `SearchControl.PopupSectionBackgroundGradientBegin`<br />(Gradient s’arrête pour ce jeton non utilisé dans l’interface utilisateur thématique.) |
| Premier plan (texte de case à cocher) | `SearchControl.PopupCheckboxText` |
| Premier plan (texte de lien) | `SearchControl.PopupButtonText` |
| Arrière-plan d’en-tête | `SearchControl.PopupSectionHeaderGradientBegin`<br />(Gradient s’arrête pour ce jeton non utilisé dans l’interface utilisateur thématique.) |
| Premier plan (texte d’en-tête) | `SearchControl.PopupSectionHeaderText` |

**Options de recherche : état de vol stationnaire**

![Options de recherche (case à cocher) sur le plan stationnaire](../../extensibility/ux-guidelines/media/0303-129_searchcheckboxhover.png "0303-129_SearchCheckboxHover")<br />Options de recherche (case à cocher) sur le plan stationnaire

![Options de recherche (lien) sur le plan stationnaire](../../extensibility/ux-guidelines/media/0303-130_searchoptionshover.png "0303-130_SearchOptionsHover")<br />Options de recherche (lien) sur le plan stationnaire

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `SearchControl.PopupControlMouseOverBackgroundGradientBegin`<br />(Gradient s’arrête pour ce jeton non utilisé dans l’interface utilisateur thématique.) |
| Premier plan (texte de case à cocher) | `SearchControl.PopupCheckboxMouseDownText` |
| Premier plan (texte de lien) | `SearchControl.PopupButtonMouseDownText` |
| Bordure | `SearchControl.PopupControlMouseOverBorder` |

**Options de recherche : état pressé**

![Options de recherche pressées (case à cocher)](../../extensibility/ux-guidelines/media/0303-131_searchsuggestedpressed.png "0303-131_SearchSuggestedPressed")<br />Options de recherche pressées (case à cocher)

![Options de recherche pressées (lien)](../../extensibility/ux-guidelines/media/0303-132_searchoptionspressed.png "0303-132_SearchOptionsPressed")<br />Options de recherche pressées (lien)

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan de case à cocher | `SearchControl.PopupControlMouseDownBackgroundGradientBegin`<br />`SearchControl.PopupControlMouseDownBackgroundGradientEnd`<br />(Gradient s’arrête pour ce jeton non utilisé dans l’interface utilisateur thématique.) |
| Premier plan (texte de case à cocher) | `SearchControl.PopupCheckboxMouseDownText` |
| Arrière-plan de lien | `SearchControl.PopupButtonMouseDownBackgroundGradientBegin`<br />(Gradient s’arrête pour ce jeton non utilisé dans l’interface utilisateur thématique.) |
| Premier plan (texte de lien) | `SearchControl.PopupButtonMouseDownText` |

### <a name="tree-views"></a><a name="BKMK_TreeView"></a>Vues d’arbre
Plusieurs fenêtres d’outils, y compris le Solution Explorer, Server Explorer, et Class View, implémentent un schéma organisationnel hiérarchique dont les couleurs sont contrôlées par des noms de couleur dans la `TreeView` catégorie. Tous les éléments d’une arborescence ont des couleurs d’arrière-plan et de texte. Les éléments qui possèdent des éléments enfants imbriqués ont également des glyphes qui indiquent si l’élément est développé ou réduit.

![Vue d’arbre (ligne rouge)](../../extensibility/ux-guidelines/media/0303-147_treeviewredline.png "0303-147_TreeViewRedline")<br />Vue d’arbre (ligne rouge)

| Utiliser... | N’utilisez pas ... |
| --- | --- |
| ... où vous avez besoin pour mettre en œuvre une vue organisationnelle hiérarchique. | ... pour tout ce qui n’est pas similaire à une vue d’arbre. |
| | ... dans n’importe quelle combinaison de fond/premier plan autre que spécifiée. |

**Article de vue d’arbre : état par défaut**

![Élément de vue d’arbre par défaut](../../extensibility/ux-guidelines/media/0303-148_treeview.png "0303-148_TreeView")<br />Élément de vue d’arbre par défaut

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `TreeView.Background` |
| Premier plan (texte) | `TreeView.Background` |
| Premier plan (glyphe) | `TreeView.Glyph` |
| Bordure | None |

**Article de vue d’arbre : état de vol stationnaire**

![Article de vue d’arbre sur le planeur](../../extensibility/ux-guidelines/media/0303-149_treeviewhover.png "0303-149_TreeViewHover")<br />Article de vue d’arbre sur le planeur

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `TreeView.Background` |
| Premier plan (texte) | `TreeView.Background` |
| Premier plan (glyphe) | `TreeView.GlyphMouseOver` |
| Bordure | None |

**Article de vue d’arbre : traînez au-dessus de l’état**

![Article de vue d’arbre sur la traînée au-dessus](../../extensibility/ux-guidelines/media/0303-150_treeviewdragover.png "0303-150_TreeViewDragOver")<br />Article de vue d’arbre sur la traînée au-dessus

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `TreeView.DragOverItem` |
| Premier plan (texte) | `TreeView.DragOverItem` |
| Premier plan (glyphe) | `TreeView.DragOverItemGlyph` |
| Bordure | None |

**Article de vue d’arbre : état choisi et ciblé**

![Élément de vue d’arbre sélectionné et concentré](../../extensibility/ux-guidelines/media/0303-151_treeviewfocused.png "0303-151_TreeViewFocused")<br />Élément de vue d’arbre sélectionné et concentré

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `TreeView.SelectedItemActive` |
| Premier plan (texte) | `TreeView.SelectedItemActive` |
| Premier plan (glyphe) | `TreeView.SelectedItemActiveGlyph` |
| Bordure | `TreeView.FocusVisualBorder` |

**Article de vue d’arbre : état choisi et non focalisé**

![Élément choisi et non focalisé de vue d’arbre](../../extensibility/ux-guidelines/media/0303-152_treeviewunfocused.png "0303-152_TreeViewUnfocused")<br />Élément choisi et non focalisé de vue d’arbre

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `TreeView.SelectedItemInactive` |
| Premier plan (texte) | `TreeView.SelectedItemInactive` |
| Premier plan (glyphe) | `TreeView.SelectedItemInactiveGlyph` |
| Bordure | None |

**Article de vue d’arbre : état plané, choisi et concentré**

![Élément choisi et concentré de vue d’arbre sur le plan stationnaire](../../extensibility/ux-guidelines/media/0303-153_treeviewfocusedhover.png "0303-153_TreeViewFocusedHover")<br />Élément choisi et concentré de vue d’arbre sur le plan stationnaire

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `TreeView.SelectedItemActive` |
| Premier plan (texte) | `TreeView.SelectedItemActive` |
| Premier plan (glyphe) | `TreeView.SelectedItemActiveGlyphMouseOver` |
| Bordure | `TreeView.FocusVisualBorder` |

**Article de vue d’arbre : état plané, choisi, et non focalisé**

![Élément choisi et non focalisé de vue d’arbre sur le plan stationnaire](../../extensibility/ux-guidelines/media/0303-154_treeviewunfocusedhover.png "0303-154_TreeViewUnfocusedHover")<br />Élément choisi et non focalisé de vue d’arbre sur le plan stationnaire

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `TreeView.SelectedItemInactive` |
| Premier plan (texte) | `TreeView.SelectedItemInactive` |
| Premier plan (glyphe) | `TreeView.SelectedItemActiveGlyphMouseOver` |
| Bordure | None |

## <a name="shell-appearance"></a>Apparence Shell

### <a name="background"></a>Arrière-plan
L’arrière-plan de l’environnement comporte deux couches. La couche inférieure est une couleur unie qui recouvre l’ensemble de l’IDE. La couche supérieure se place sous l’interface de commande et entre les canaux à masquage automatique de la fenêtre Outil situés sur les côtés gauche et droit de l’IDE. Les couches de fond supérieure et inférieure sont réglées à la même couleur dans les thèmes Lumière et Obscurité.

![Fond de coquille visual studio (redline)](../../extensibility/ux-guidelines/media/0303-187_shellbackgroundredline.png "0303-187_ShellBackgroundRedline")<br />Fond de coquille visual studio (redline)

| Utiliser... | N’utilisez pas ... |
| --- | --- |
| ... pour les endroits où vous voulez faire correspondre l’arrière-plan de l’environnement Visual Studio. | ... comme un remplissage pour les endroits qui ne sont pas des surfaces de fond. |
| | ... comme arrière-plan pour placer des éléments de premier plan. |

**Aspect inférieur de la coquille de couche**

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.EnvironmentBackground` |

**Aspect de la coquille de couche supérieure**

> Les points de dégradé sont définis sur la même valeur de couleur dans les thèmes clairs et foncés de Visual Studio 2013.

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.EnvironmentBackgroundGradientBegin`<br />`Environment.EnvironmentBackgroundGradientEnd`<br />`Environment.EnvironmentBackgroundGradientMiddle1`<br />`Environment.EnvironmentBackgroundGradientMiddle2` |

### <a name="command-shelf"></a>Interface de commande
Deux ensembles de noms de jeton sont utilisés pour les arrière-plans de l’interface de commande : un jeu pour l’emplacement de la barre de menus et l’autre pour l’emplacement des barres de commandes. Un groupe de barres de commandes possède ses propres valeurs de couleur d’arrière-plan, lesquelles sont décrites dans la section « Barre de commandes ». Le texte de la barre de menus et des barres de commandes est traité dans les sections qui leur sont dédiées.

![Étagère de commande de studio visuel (ligne rouge)](../../extensibility/ux-guidelines/media/0303-188_commandshelfredline.png "0303-188_CommandShelfRedline")<br />Étagère de commande de studio visuel (ligne rouge)

| Utiliser... | N’utilisez pas ... |
| --- | --- |
| ... pour les zones où vous placez des menus ou des barres d’outils. | ... pour les zones qui ne sont pas similaires à une étagère de commande. |
|... avec la combinaison correcte de nom de jet de fond/premier plan. | |

**Barre de menu d’étagère de commande**

> Les points de dégradé sont définis sur la même valeur de couleur dans les thèmes clairs et foncés de Visual Studio 2013.

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.CommandShelfHighlightGradientBegin`<br /><br />`Environment.CommandShelfHighlightGradientMiddle`<br />`Environment.CommandShelfHighlightGradientEnd` |

**Barre de commande de commande**

> Les points de dégradé sont définis sur la même valeur de couleur dans les thèmes clairs et foncés de Visual Studio 2013.

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.CommandShelfBackgroundGradientBegin`<br />`Environment.CommandShelfBackgroundGradientMiddle`<br />`Environment.CommandShelfBackgroundGradientEnd` |

## <a name="manifest-designer"></a>Concepteur de manifeste
Le concepteur de manifeste sert à faciliter l’édition du fichier manifeste dans des projets Windows 8 et Windows Phone 8. Même s’il n’existe aucune infrastructure partagée disponible à la consommation, vous avez peut-être intérêt à faire correspondre la disposition et les couleurs des onglets d’orientation/de navigation à la structure générale. Pour plus d’informations sur la disposition, consultez [Layout for Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).

![Manifest Designer (redline)](../../extensibility/ux-guidelines/media/0303-175_manifestdesignerredline.png "0303-175_ManifestDesignerRedline")<br />Manifest Designer (redline)

| Utiliser... | N’utilisez pas ... |
| --- | --- |
| ... pour les designers qui sont similaires à la Manifest Designer. | ... si vous avez plus de six onglets. |
| ... au lieu d’utiliser les commandes d’onglets communes en haut d’un éditeur dans le document bien. | ... pour toute interface utilisateur qui n’est pas structuré comme le Concepteur Manifeste. |

**Onglet sélectionné Par Manifest Designer : état par défaut**

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `ManifestDesigner.TabActive` |
| Bordure | None |

**Manifeste Designer carte de description sélectionnée: état par défaut**

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `ManifestDesigner.DescriptionPane` |

**Manifeste Designer page de contenu sélectionnée: état par défaut**

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `ManifestDesigner.Background` |
| Texte d’assistance de boîte de dialogue | `ManifestDesigner.WatermarkText`<br />(Ce nom de jeton ne correspond pas à sa fonction.) |

**Onglet Manifest Designer : état non sélectionné**

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `ManifestDesigner.Tab.Inactive` |

**Onglet Manifest Designer: état de vol stationnaire**

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `ManifestDesigner.Tab.Mouseover` |

## <a name="command-structures"></a>Structures de commande

### <a name="menus"></a><a name="BKMK_CommandMenus"></a>Menus
Les menus peuvent se faire à plusieurs endroits au sein de Visual Studio : la barre principale du menu, intégrée dans des fenêtres de documents ou d’outils, ou en clic droit à divers endroits dans l’IDE. Les implémentations de menus associées aux autres éléments d’interface utilisateur sont décrites dans la section de l’élément correspondant. Vous devez toujours utiliser l’implémentation de menu standard fournie par l’environnement Visual Studio. Toutefois, dans de rares cas, vous n’aurez peut-être pas accès aux menus Visual Studio standard. Dans ce cas, utilisez les noms de jeton suivants pour vous assurer que votre interface utilisateur est cohérente avec les autres menus dans Visual Studio.

![Menu Studio Visuel (redline)](../../extensibility/ux-guidelines/media/0303-000_menuredline.png "0303-000_MenuRedline")<br />Menu Studio Visuel (redline)

| Utiliser... | N’utilisez pas ... |
| --- | --- |
| ... lorsque vous avez besoin de créer un menu personnalisé.| ... la couleur de fond seule. Utilisez toujours la combinaison arrière-plan/premier plan spécifiée. |
| ... lorsque vous avez un nouveau composant d’interface utilisateur que vous souhaitez assortir aux menus Visual Studio.| |

#### <a name="menu-titles"></a>Titres de menu
Les titres de menu comprennent un arrière-plan, une bordure et le texte du titre, ainsi qu’un glyphe facultatif, généralement quand le menu se trouve dans une barre de commandes.

![Titre du menu (redline)](../../extensibility/ux-guidelines/media/0303-001_menutitleredline.png "0303-001_MenuTitleRedline")<br />Titre du menu (redline)

| Utiliser... | N’utilisez pas ... |
| --- | --- |
| ... chaque fois que vous créez un titre de menu personnalisé. | ... pour tout ce que vous ne voulez pas toujours correspondre au titre du menu. |
| | ... dans n’importe quelle combinaison de fond/premier plan autre que spécifiée. |

**Titre du menu: état par défaut**

![Titre du menu par défaut](../../extensibility/ux-guidelines/media/0303-002_menutitledefault.png "0303-002_MenuTitleDefault")<br />Titre du menu par défaut

![Titre du menu par défaut avec glyph](../../extensibility/ux-guidelines/media/0303-003_menutitlewithglyphdefault.png "0303-003_MenuTitleWithGlyphDefault")<br />Titre du menu par défaut avec glyph

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | None |
| Au premier plan (texte) | `Environment.CommandBarTextActive` |
| Au premier plan (glyphe) | `Environment.CommandBarMenuGlyph` |
| Bordure | None |

**Titre du menu: état de vol stationnaire**

![Titre de menu au pointage](../../extensibility/ux-guidelines/media/0303-004_menutitlehover.png "0303-004_MenuTitleHover")<br />Titre de menu au pointage

![Titre de menu avec glyphe au pointage](../../extensibility/ux-guidelines/media/0303-005_menutitlewithglyphhover.png "0303-005_MenuTitleWithGlyphHover")<br />Titre de menu avec glyphe au pointage

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.CommandBarMouseOverBackgroundBegin`<br />(Gradient s’arrête pour ce jeton non utilisé dans l’interface utilisateur thématique.) |
| Au premier plan (texte) | `Environment.CommandBarTextHover` |
| Au premier plan (glyphe) | `Environment.CommandBarMenuMouseOverGlyph` |
| Bordure | `Environment.CommandBarBorder` |

**Titre du menu: état pressé**

![Titre du menu pressé](../../extensibility/ux-guidelines/media/0303-006_menutitlepressed.png "0303-006_MenuTitlePressed")<br />Titre du menu pressé

![Titre de menu pressé avec glyph](../../extensibility/ux-guidelines/media/0303-007_menutitlewithglyphpressed.png "0303-007_MenuTitleWithGlyphPressed")<br />Titre de menu pressé avec glyph

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.CommandBarMenuBackgroundGradientBegin`<br/>(Gradient s’arrête pour ce jeton non utilisé dans l’interface utilisateur thématique.) |
| Premier plan (texte) | `Environment.CommandBarTextActive` |
| Premier plan (glyphe) | `Environment.CommandBarMenuMouseDownGlyph` |
| Bordure | `Environment.CommandBarMenuBorder`<br />(Seulement à gauche, en haut et sur les côtés droit.) |

**Titre du menu: État handicapé**

![Titre du menu désactivé avec glyph](../../extensibility/ux-guidelines/media/0303-008_menutitlewithglyphdisabled.png "0303-008_MenuTitleWithGlyphDisabled")<br />Titre du menu désactivé avec glyph

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | None |
| Premier plan (texte) | `Environment.CommandBarTextInactive` |
| Premier plan (glyphe) | `Environment.CommandBarTextInactive` |
| Bordure | None |

#### <a name="menu-items"></a>Éléments de menu
Un élément de menu individuel comporte le texte du menu et éventuellement une icône, une case à cocher ou un glyphe de sous-menu. Sa couleur d’arrière-plan et de texte change au passage du curseur de la souris. Ce jeton de couleur est une paire arrière-plan/premier plan.

![Ligne rouge d'éléments de menu](../../extensibility/ux-guidelines/media/0303-009_menuitemredline.png "0303-009_MenuItemRedline")

| Utiliser... | N’utilisez pas ... |
|---|---|
| ... pour toute liste de décrochage qui est lancée à partir d’une barre de menu ou d’une barre de commande. | ... pour toute liste de décrochage dans un autre contexte. |
| | ... dans n’importe quelle combinaison de fond/premier plan autre que spécifiée. |

**Éléments du menu: état par défaut**

![Éléments de menu par défaut](../../extensibility/ux-guidelines/media/0303-010_menudefault.png "0303-010_MenuDefault")<br />Éléments de menu par défaut

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.CommandBarMenuBackgroundGradientBegin`<br />(Gradient s’arrête pour ce jeton non utilisé dans l’interface utilisateur thématique.) |
| Premier plan (texte) | `Environment.CommandBarTextActive` |
| Premier plan (glyphe de sous-menu) | `Environment.CommandBarMenuSubmenuGlyph` |
| Bordure | `Environment.CommandBarMenuBorder` |
| Arrière-plan de canal d’icône | `Environment.CommandBarMenuIconBackground` |
| Séparateur | `Environment.CommandBarMenuSeparator` |
| Shadow | `Environment.DropShadowBackground` |

**Éléments du menu : états vérifiés et sélectionnés**

![Menu activé](../../extensibility/ux-guidelines/media/0303-011_menuchecked.png "0303-011_MenuChecked")<br />Article de menu vérifié

![Menu sélectionné](../../extensibility/ux-guidelines/media/0303-012_menuselected.png "0303-012_MenuSelected")<br />Élément de menu sélectionné

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Coche | `Environment.CommandBarCheckBox` |
| Arrière-plan de case à cocher | `Environment.CommandBarSelectedIcon` |
| Arrière-plan d’icône | `Environment.CommandBarSelected` |
| Bordure d’icône | `Environment.CommandBarSelectedBorder` |

**Éléments du menu: état de vol stationnaire**

![Pointage de menu](../../extensibility/ux-guidelines/media/0303-013_menuhover.png "0303-013_MenuHover")<br />Élément de menu sur le plan stationnaire

![Pointage de menu activé](../../extensibility/ux-guidelines/media/0303-014_menuhoverchecked.png "0303-014_MenuHoverChecked")<br />Article de menu vérifié sur le plan stationnaire

![Pointage de menu sélectionné](../../extensibility/ux-guidelines/media/0303-015_menuhoverselected.png "0303-015_MenuHoverSelected")<br />Élément de menu sélectionné sur le plan stationnaire

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.CommandBarMenuItemMouseOver` |
| Premier plan (texte) | `Environment.CommandBarMenuItemMouseOverText` |
| Premier plan (glyphe de sous-menu) | `Environment.CommandBarMenuMouseOverSubmenuGlyph` |
| Coche | `Environment.CommandBarCheckBoxMouseOver` |
| Arrière-plan de case à cocher | `Environment.CommandBarHoverOverSelectedIcon` |
| Arrière-plan d’icône | `Environment.CommandBarHoverOverSelected` |
| Bordure d’icône | `Environment.CommandBarHoverOverSelectedIconBorder` |

**Éléments du menu: état désactivé**

![Menu désactivé](../../extensibility/ux-guidelines/media/0303-016_menudisabled.png "0303-016_MenuDisabled")<br />Élément de menu désactivé

![Menu désactivé activé](../../extensibility/ux-guidelines/media/0303-017_menudisabledchecked.png "0303-017_MenuDisabledChecked")<br />Élément de menu désactivé avec la marque de contrôle

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Premier plan (texte) | `Environment.CommandBarTextInactive` |
| Premier plan (glyphe de sous-menu) | `Environment.CommandBarMenuSubmenuGlyph` |
| Coche | `Environment.CommandBarCheckBoxDisabled` |
| Arrière-plan de case à cocher | `Environment.CommandBarSelectedIconDisabled` |

### <a name="command-bars"></a>Barres de commande
Une barre de commande peut apparaître à plusieurs endroits dans l’IDE Visual Studio, notamment l’étagère de commande et intégrée dans des fenêtres d’outils ou de documents.

En règle générale, utilisez toujours l’implémentation de barre de commandes standard fournie par l’environnement Visual Studio. L’utilisation du mécanisme standard permet à tous les détails visuels d’apparaître correctement et aux éléments interactifs de se comporter de manière cohérente avec les autres contrôles de barre de commandes Visual Studio. Toutefois, si vous avez besoin de créer votre propre barre de commandes, assurez-vous d’utiliser un style adéquat avec les noms de jeton suivants.

![Ligne rouge de barre de commandes](../../extensibility/ux-guidelines/media/0303-018_commandbarredline.png "0303-018_CommandBarRedline")<br />Barre de commande (ligne rouge)

![Ligne rouge de bouton de dépassement](../../extensibility/ux-guidelines/media/0303-019_overflowbuttonredline.png "0303-019_OverflowButtonRedline")<br />Bouton de débordement (redline)

| Utiliser... | N’utilisez pas ... |
| --- | --- |
| ... dans les endroits où vous avez besoin d’une barre de commande intégrée, mais sont incapables d’utiliser l’implémentation standard de barre de commande Visual Studio. | ... pour les éléments d’interface utilisateur qui ne sont pas similaires à une barre de commande. |
| | ... pour les composants de barre de commande autres que ceux pour lesquels les noms de jetons sont spécifiés. |

#### <a name="command-bar-groups"></a>Groupes de barreaux de commandement
Un groupe de barres de commandes se compose d’un ensemble de contrôles de barre de commandes et peut contenir tout nombre de boutons, boutons partagés, menus déroulants, zones de liste modifiable ou menus. Les couleurs de ces contrôles sont régies par des noms de jeton distincts et sont décrites individuellement dans une autre section de ce guide. Un trait de séparation est utilisé pour diviser un groupe de barres de commandes en sous-groupes associés.

![Ligne rouge de groupe de barres de commandes](../../extensibility/ux-guidelines/media/0303-020_commandbargroupredline.png "0303-020_CommandBarGroupRedline")<br />Groupe de barre de commande (redline)

| Utiliser... | N’utilisez pas ... |
| --- | --- |
| ... dans les endroits où vous avez besoin d’une barre de commande intégrée, mais sont incapables d’utiliser l’implémentation standard de barre de commande Visual Studio. | ... pour les éléments d’interface utilisateur qui ne sont pas similaires à une barre de commande. |
| | ... pour les composants de barre de commande autres que ceux pour lesquels les noms de jetons sont spécifiés. |

**Groupe de barre de commande : état par défaut**

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.CommandBarGradientBegin`<br />(Gradient s’arrête pour ce jeton non utilisé dans l’interface utilisateur thématique.) |
| Bordure | `Environment.CommandBarToolBarBorder` |
| Poignée de redimensionnement | `Environment.CommandBarDragHandle` |
| Séparateur | `Environment.CommandBarToolBarSeparator`<br />`Environment.CommandBarToolBarSeparatorHighlight` |

#### <a name="command-icons"></a>Icônes de commande
![Ligne rouge d'icône de commande](../../extensibility/ux-guidelines/media/0303-021_commandiconredline1.png "0303-021_CommandIconRedline1")<br />Icône de commande (redline)

![Icône de commande avec la ligne rouge de texte](../../extensibility/ux-guidelines/media/0303-022_commandiconredline2.png "0303-022_CommandIconRedline2")<br />Icône de commande avec le texte (redline)

| Utiliser... | N’utilisez pas ... |
| --- | --- |
| ... pour tous les boutons qui seront placés sur une barre de commande. | ... pour les contrôles qui ont leurs propres noms symboliques. |
| | ... dans n’importe quelle combinaison de fond/premier plan autre que spécifiée. |

**Icône de commande : état par défaut**

![Valeur par défaut d'icône de commande](../../extensibility/ux-guidelines/media/0303-023_commandicondefault.png "0303-023_CommandIconDefault")<br />Icône de commande par défaut

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | N/A (hérite de l’arrière-plan de la barre commandes) |
| Premier plan (texte) | `Environment.CommandBarTextActive` |
| Bordure | N/A |

**Icône de commande : état par défaut, sélectionné**

![Par défaut, icône de commande sélectionnée](../../extensibility/ux-guidelines/media/0303-024_commandicondefaultselected.png "0303-024_CommandIconDefaultSelected")<br />Par défaut, icône de commande sélectionnée

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.CommandBarSelected` |
| Premier plan (texte) | `Environment.CommandBarTextSelected` |
| Bordure | `Environment.CommandBarSelectedBorder` |

**Icône de commande : états de vol stationnaire ou de mise au point**

![Icône de commande sur le plan stationnaire ou la concentration](../../extensibility/ux-guidelines/media/0303-025_commandiconhover.png "0303-025_CommandIconHover")<br />Icône de commande sur le plan stationnaire ou la concentration

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.CommandBarMouseOverBackgroundBegin`<br />(Gradient s’arrête pour ce jeton non utilisé dans l’interface utilisateur thématique.) |
| Premier plan (texte) | `Environment.CommandBarTextHover` |
| Bordure | `Environment.CommandBarBorder` |

**Icône de commande : états de vol stationnaire ou de mise au point, sélectionnés**

![Icône de commande sélectionnée sur le plan stationnaire ou la mise au point](../../extensibility/ux-guidelines/media/0303-026_commandiconhoverselected.png "0303-026_CommandIconHoverSelected")<br />Icône de commande sélectionnée sur le plan stationnaire ou la mise au point

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.CommandBarHoverOverSelected` |
| Premier plan (texte) | `Environment.CommandBarTextHoverOverSelected` |
| Bordure | `Environment.CommandBarHoverOverSelectedIconBorder` |

 **Icône de commande : état pressé**

![Icône de commande appuyée](../../extensibility/ux-guidelines/media/0303-027_commandiconpressed.png "0303-027_CommandIconPressed")<br />Icône de commande appuyée

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.CommandBarMouseDownBackgroundBegin`<br />(Gradient s’arrête pour ce jeton non utilisé dans l’interface utilisateur thématique.) |
| Premier plan (texte) | `Environment.CommandBarTextMouseDown` |
| Bordure | `Environment.CommandBarBorder` |

**Icône de commande : état désactivé**

![Icône de commande désactivée](../../extensibility/ux-guidelines/media/0303-028_commandicondisabled.png "0303-028_CommandIconDisabled")<br />Icône de commande désactivée

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | N/A (hérite de l’arrière-plan de la barre commandes) |
| Premier plan (texte) | `Environment.CommandBarTextInactive` |
| Bordure | N/A |

#### <a name="command-bar-combo-boxes"></a><a name="BKMK_CommandComboBox"></a>Boîtes combo barres de commande

> [!IMPORTANT]
> Les zones de liste modifiable ressemblent aux listes déroulantes, mais elles comprennent une zone de texte modifiable. Si votre décrochage n’inclut pas une région de texte modifiable, utilisez les jetons de couleur pour [les baisses de barres de commande](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandDropDown).

![Boîte combo de barre de commande redline](../../extensibility/ux-guidelines/media/0303-029_comboboxredline.png "0303-029_ComboBoxRedline")<br />Boîte combo de barre de commande (redline)

| Utiliser... | N’utilisez pas ... |
| --- | --- |
| ... lors de la construction de boîtes combo personnalisées. | ... pour tout ce que vous ne voulez pas toujours correspondre à l’interface utilisateur barre de commande. |
| ... lors de la création d’un contrôle de barre de commande qui est similaire à une boîte combo. | ... lorsque vous avez accès à une boîte combo de style. |

**Champ d’entrée de boîte combo de barre de commande : état par défaut**

![Champ d’entrée de boîte combo de barre de commande](../../extensibility/ux-guidelines/media/0303-030_comboboxinputfield.png "0303-030_ComboBoxInputField")<br />Champ d’entrée de boîte combo de barre de commande

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.ComboBoxBackground` |
| Premier plan (texte) | `Environment.ComboBoxText` |
| Bordure | `Environment.ComboBoxBorder` |
| Séparateur | Aucun séparateur |

**Bouton d’abandon de la barre de commande : état par défaut**

![Combo boîte goutte&#45;vers le bas bouton](../../extensibility/ux-guidelines/media/0303-031_comboboxdropdownbutton.png "0303-031_ComboBoxDropdownButton")<br />Bouton d’abandon de barre de commande

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | N/A (hérite de l’arrière-plan de la barre commandes) |
| Premier plan (glyphe) | `Environment.ComboBoxGlyph` |

**Liste d’abandon de la barre de commandement : état par défaut**

![Liste d’abandon de barres de commandement](../../extensibility/ux-guidelines/media/0303-032_comboboxdropdownlist.png "0303-032_ComboBoxDropdownList")<br />Liste d’abandon de barres de commandement

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.ComboBoxPopupBackgroundBegin`<br />(Gradient s’arrête pour ce jeton non utilisé dans l’interface utilisateur thématique.) |
| Premier plan (texte) | `Environment.ComboBoxItemText` |
| Bordure | `Environment.ComboBoxPopupBorder` |

**Champ d’entrée de boîte combo de barre de commande : état de vol stationnaire**

![Champ d’entrée de boîte de combo de barre de commande sur le plan stationnaire](../../extensibility/ux-guidelines/media/0303-033_comboboxinputfieldhover.png "0303-033_ComboBoxInputFieldHover")<br />Champ d’entrée de boîte de combo de barre de commande sur le plan stationnaire

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.ComboBoxMouseOverBackgroundBegin`<br />(Gradient s’arrête pour ce jeton non utilisé dans l’interface utilisateur thématique.) |
| Premier plan (texte) | `Environment.ComboBoxMouseOverText` |
| Bordure | `Environment.ComboBoxMouseOverBorder` |
| Séparateur | `Environment.ComboBoxMouseOverSeparator` |

 **Bouton d’abandon de barre de commande : état de vol stationnaire**

![Bouton de chute de barre de commande sur le plan stationnaire](../../extensibility/ux-guidelines/media/0303-034_comboboxdropdownbuttonhover.png "0303-034_ComboBoxDropdownButtonHover")<br />Bouton de chute de barre de commande sur le plan stationnaire

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.ComboBoxButtonMouseOverBackground` |
| Premier plan (glyphe) | `Environment.ComboBoxMouseOverGlyph` |

**Liste d’abandon de barres de commandement : état de vol stationnaire**

 ![Liste d’abandon de barre de commande sur le plan stationnaire](../../extensibility/ux-guidelines/media/0303-035_comboboxdropdownlisthover.png "0303-035_ComboBoxDropdownListHover")<br />Liste d’abandon de barre de commande sur le plan stationnaire

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan (élément de menu) | `Environment.ComboBoxItemMouseOverBackground` |
| Premier plan (texte) | `Environment.ComboBoxItemMouseOverText` |
| Bordure (élément de menu) | `Environment.ComboBoxItemMouseOverBorder` |

 **Champ d’entrée de boîte combo de barre de commande : état focalisé**

![Champ d’entrée de boîte combo de barre de commande focalisé](../../extensibility/ux-guidelines/media/0303-036_comboboxinputfieldfocused.png "0303-036_ComboBoxInputFieldFocused")<br />Champ d’entrée de boîte combo de barre de commande focalisé

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.ComboBoxFocusedBackground` |
| Premier plan (texte) | `Environment.ComboBoxFocusedText` |
| Bordure | `Environment.ComboBoxFocusedBorder` |
| Séparateur | `Environment.ComboBoxFocusedButtonSeparator` |

**Bouton d’abandon de la barre de commande : état focalisé**

![Bouton de décrochage de barre de commande focalisé](../../extensibility/ux-guidelines/media/0303-037_comboboxdropdownbuttonfocused.png "0303-037_ComboBoxDropdownButtonFocused")<br />Bouton de décrochage de barre de commande focalisé

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.ComboBoxFocusedButtonBackground` |
| Premier plan (glyphe) | `Environment.ComboBoxFocusedGlyph` |

 **Champ d’entrée de boîte combo de barre de commande : état pressé**

![Champ d’entrée de boîte combo de barre de commande pressée](../../extensibility/ux-guidelines/media/0303-038_comboboxinputfieldpressed.png "0303-038_ComboBoxInputFieldPressed")<br />Champ d’entrée de boîte combo de barre de commande pressée

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.ComboBoxMouseDownBackground` |
| Premier plan (texte) | `Environment.ComboBoxMouseDownText` |
| Bordure | `Environment.ComboBoxMouseDownBorder` |
| Séparateur | `Environment.ComboBoxMouseDownSeparator` |

**Bouton de décrochage de barre de commande : état pressé**

![Bouton de chute de barre de commande pressé](../../extensibility/ux-guidelines/media/0303-039_comboboxdropdownbuttonpressed.png "0303-039_ComboBoxDropdownButtonPressed")<br />Bouton de chute de barre de commande pressé

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.ComboBoxButtonMouseDownBackground` |
| Premier plan (glyphe) | `Environment.ComboBoxMouseDownGlyph` |

**Champ d’entrée de boîte combo de barre de commande : état désactivé**

![Champ d’entrée de boîte combo de barre de commande désactivée](../../extensibility/ux-guidelines/media/0303-041_comboboxinputfielddisabled.png "0303-041_ComboBoxInputFieldDisabled")<br />Champ d’entrée de boîte combo de barre de commande désactivée

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.ComboBoxDisabledBackground` |
| Premier plan (texte) | `Environment.ComboBoxDisabledText` |
| Bordure | `Environment.ComboBoxDisabledBorder` |
| Séparateur | Aucun séparateur |

**Bouton d’abandon de barres de commande : état désactivé**

![Bouton d’abandon de barre de commande désactivé](../../extensibility/ux-guidelines/media/0303-040_comboboxdropdownbuttondisabled.png "0303-040_ComboBoxDropdownButtonDisabled")<br />Bouton d’abandon de barre de commande désactivé

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | None |
| Premier plan (glyphe) | `Environment.ComboBoxDisabledGlyph` |

#### <a name="command-bar-drop-downs"></a><a name="BKMK_CommandDropDown"></a>Baisses de barres de commandement

> [!IMPORTANT]
> Les listes déroulantes ressemblent aux zones de liste modifiable, mais elles ne disposent pas de zones de texte modifiable. Si votre drop-down inclut une région de texte modifiable, utilisez les jetons de couleur pour [les boîtes combo de barre de commande.](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandComboBox)

![Baisse de la barre de commandement (ligne rouge)](../../extensibility/ux-guidelines/media/0303-042_dropdownredline.png "0303-042_DropdownRedline")<br />Baisse de la barre de commandement (ligne rouge)

| Utiliser... | N’utilisez pas ... |
| --- | --- |
| ... lorsque vous créez des contrôles de liste d’abandon personnalisés. | ... pour tout ce qui n’est pas similaire à une liste d’abandon. |
| | ... pour les boîtes combo ou les boutons fendus. |

**Champ de sélection de la barre de commande : état par défaut**

![Champ de sélection de la barre de commande par défaut](../../extensibility/ux-guidelines/media/0303-043_dropdownselectionfield.png "0303-043_DropdownSelectionField")<br />Champ de sélection de la barre de commande par défaut

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.DropDownBackground` |
| Premier plan (texte) | `DropDownText` |
| Bordure | `DropDownBorder` |
| Séparateur | Aucun séparateur |

**Bouton d’abandon de la barre de commande : état par défaut**

![Bouton d’abandon par barre de commande par défaut](../../extensibility/ux-guidelines/media/0303-044_dropdownbutton.png "0303-044_DropdownButton")<br />Bouton d’abandon par barre de commande par défaut

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | None |
| Premier plan (glyphe) | `Environment.DropDownGlyph` |

**Liste d’abandon de la barre de commandement : état par défaut**

![Liste d’abandon de barres de commande par défaut](../../extensibility/ux-guidelines/media/0303-045_dropdownlist.png "0303-045_DropdownList")<br />Liste d’abandon de barres de commande par défaut

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.DropDownPopupBackgroundBegin`<br />(Gradient s’arrête pour ce jeton non utilisé dans l’interface utilisateur thématique.) |
| Premier plan (texte) | `Environment.ComboBoxItemText` |
| Bordure | `Environment.DropDownPopupBorder` |
| Shadow | `Environment.DropShadowBackground` |

**Champ de sélection de la barre de commandement : état de vol stationnaire**

![Champ de sélection de chute de barre de commande sur le plan stationnaire](../../extensibility/ux-guidelines/media/0303-046_dropdownselectionfieldhover.png "0303-046_DropdownSelectionFieldHover")<br />Champ de sélection de chute de barre de commande sur le plan stationnaire

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.DropDownMouseOverBackgroundBegin`<br />(Gradient s’arrête pour ce jeton non utilisé dans l’interface utilisateur thématique.) |
| Premier plan (texte) | `Environment.DropDownMouseOverText` |
| Bordure | `Environment.DropDownMouseOverBorder` |
| Séparateur | `Environment.DropDownButtonMouseOverSeparator` |

**Bouton d’abandon de barre de commande : état de vol stationnaire**

![Bouton de chute de barre de commande sur le plan stationnaire](../../extensibility/ux-guidelines/media/0303-047_dropdownbuttonhover.png "0303-047_DropdownButtonHover")<br />Bouton de chute de barre de commande sur le plan stationnaire

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.DropDownButtonMouseOverBackground` |
| Premier plan (glyphe) | `Environment.DropDownMouseOverGlyph` |

**Liste d’abandon de barres de commandement : état de vol stationnaire**

![Liste d’abandon de barre de commande sur le plan stationnaire](../../extensibility/ux-guidelines/media/0303-048_dropdownlisthover.png "0303-048_DropdownListHover")<br />Liste d’abandon de barre de commande sur le plan stationnaire

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan (élément de menu) | `Environment.ComboBoxItemMouseOverBackground` |
| Premier plan (texte) | `Environment.ComboBoxItemMouseOverText` |
| Bordure (élément de menu) | `Environment.ComboBoxItemMouseOverBorder` |

 **Champ de sélection de la barre de commandement : état pressé**

![Drop&#45;down selection field pressed](../../extensibility/ux-guidelines/media/0303-049_dropdownselectionfieldpressed.png "0303-049_DropdownSelectionFieldPressed")<br />Champ de sélection de la barre de commande pressée

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.DropDownMouseDownBackground` |
| Premier plan (texte) | `Environment.DropDownMouseDownText` |
| Bordure | `Environment.DropDownMouseDownBorder` |
| Séparateur | `Environment.DropDownButtonMouseDownSeparator` |

**Bouton de décrochage de barre de commande : état pressé**

![Bouton de chute de barre de commande pressé](../../extensibility/ux-guidelines/media/0303-050_dropdownbuttonpressed.png "0303-050_DropdownButtonPressed")<br />Bouton de chute de barre de commande pressé

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.DropDownButtonMouseDownBackground` |
| Premier plan (glyphe) | `Environment.DropDownMouseDownGlyph` |

**Champ de sélection de la barre de commandement : état désactivé**

![Champ de sélection de barres de commande désactivée](../../extensibility/ux-guidelines/media/0303-051_dropdownselectionfielddisabled.png "0303-051_DropdownSelectionFieldDisabled")<br />Champ de sélection de barres de commande désactivée

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.DropDownDisabledBackground` |
| Premier plan (texte) | `Environment.DropDownDisabledText` |
| Bordure | `Environment.DropDownDisabledBorder` |
| Séparateur | Aucun séparateur |

**Bouton d’abandon de barres de commande : état désactivé**

![Bouton d’abandon de barre de commande désactivé](../../extensibility/ux-guidelines/media/0303-052_dropdownbuttondisabled.png "0303-052_DropdownButtonDisabled")<br />Bouton d’abandon de barre de commande désactivé

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | N/A |
| Premier plan (glyphe) | `Environment.DropDownDisabledGlyph` |

#### <a name="command-bar-split-buttons"></a>Boutons fractionnés de barre de commande
Les boutons partagés partagent de nombreux noms de jeton avec d’autres contrôles de barre de commandes, tels que des boutons, menus et texte de barre de commandes. Toutes les actions nécessaires et les noms de jeton bouton de liste déroulante sont répétés ici par commodité. Les listes d’abandon des boutons fractionnés sont des implémentations de menus de barres de [commande.](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandMenus)

![Ligne rouge de bouton Fractionner](../../extensibility/ux-guidelines/media/0303-053_splitbuttonredline.png "0303-053_SplitButtonRedline")<br />Bouton fractionné de barre de commande (redline)

| Utiliser... | N’utilisez pas ... |
| --- | --- |
| ... lorsque vous créez un bouton split personnalisé. | ... pour d’autres types de boutons. |
| | ... dans n’importe quelle combinaison de fond/premier plan autre que spécifiée. |

**Bouton fractionné de barre de commande : état par défaut**

![Bouton fractionné de barre de commande par défaut](../../extensibility/ux-guidelines/media/0303-054_splitbutton.png "0303-054_SplitButton")<br />Bouton fractionné de barre de commande par défaut

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | None |
| Premier plan (texte) | `Environment.CommandBarTextActive` |
| Premier plan (glyphe) | `Environment.CommandBarSplitButtonGlyph` |
| Bordure | N/A |
| Séparateur | N/A |

**Bouton fractionné de barre de commande : état de vol stationnaire**

![Bouton fractionné de barre de commande sur le plan stationnaire](../../extensibility/ux-guidelines/media/0303-055_splitbuttonhover.png "0303-055_SplitButtonHover")<br />Bouton fractionné de barre de commande sur le plan stationnaire

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.CommandBarMouseOverBackgroundBegin`<br />(Gradient s’arrête pour ce jeton non utilisé dans l’interface utilisateur thématique.) |
| Premier plan (texte) | `Environment.CommandBarTextHover` |
| Premier plan (glyphe) | `Environment.CommandBarSplitButtonMouseOverGlyph` |
| Bordure | `Environment.CommandBarBorder` |
| Séparateur | `Environment.CommandBarSplitButtonSeparator` |

**Bouton fractionné de barre de commande : état pressé**

![Bouton fractionné de barre de commande pressé](../../extensibility/ux-guidelines/media/0303-056_splitbuttonpressed.png "0303-056_SplitButtonPressed")<br />Bouton fractionné de barre de commande pressé

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.CommandBarMouseDownBackgroundBegin`<br />(Gradient s’arrête pour ce jeton non utilisé dans l’interface utilisateur thématique.) |
| Premier plan (texte) | `Environment.CommandBarTextMouseDown` |
| Premier plan (glyphe) | `Environment.CommandBarSplitButtonMouseDownGlyph` |
| Bordure | `Environment.CommandBarBorder` |
| Séparateur | N/A |

**Bouton fractionné de barre de commande : état désactivé**

![Bouton fractionné de barre de commande désactivé](../../extensibility/ux-guidelines/media/0303-057_splitbuttondisabled.png "0303-057_SplitButtonDisabled")<br />Bouton fractionné de barre de commande désactivé

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | N/A |
| Premier plan (texte) | `Environment.ComboBoxItemTextInactive` |
| Premier plan (glyphe) | `Environment.CommandBarTextInactive` |
| Bordure | N/A |
| Séparateur | N/A |

#### <a name="command-bar-more-options-and-overflow-buttons"></a>Barre de commande 'Plus d’options' et boutons 'Overflow'
Le bouton « Autres options » est utilisé quand un groupe de barres de commandes peut être personnalisé en ajoutant ou en supprimant des boutons de barre de commandes associés. Le bouton « >> » apparaît quand une barre de commandes est tronquée en raison d’un manque d’espace horizontal. En cliquant dessus, un menu se déroule pour afficher les autres boutons de la barre de commandes qui ne pouvaient pas apparaître. Les couleurs de ces deux boutons sont contrôlées par le même ensemble de noms de jeton.

![Bouton 'Plus d’options' (redline)](../../extensibility/ux-guidelines/media/0303-058_moreoptionsredline.png "0303-058_MoreOptionsRedline")<br />Bouton 'Plus d’options' (redline)

| Utiliser... | N’utilisez pas ... |
| --- | --- |
| ... pour les boutons personnalisés 'Plus d’options' ou 'Overflow'. | ... pour les boutons qui n’ont pas de fonctionnalité similaire à un bouton 'Plus d’options' ou 'Overflow'. |

**Barre de commande 'Plus d’options' et boutons 'Overflow' : état par défaut**

![Bouton de la barre de commande par défaut 'Plus d’options'](../../extensibility/ux-guidelines/media/0303-059_moreoptions.png "0303-059_MoreOptions")<br />Bouton de la barre de commande par défaut 'Plus d’options'

![Bouton 'Overflow' de la barre de commande par défaut](../../extensibility/ux-guidelines/media/0303-060_overflow.png "0303-060_Overflow")<br />Bouton 'Overflow' de la barre de commande par défaut

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.CommandBarOptionsBackground` |
| Premier plan (glyphe) | `Environment.CommandBarOptionsGlyph` |

**Barre de commande 'Plus d’options' et boutons 'Overflow' : état de vol stationnaire**

![Bouton 'Plus d’options' sur le bouton de commande](../../extensibility/ux-guidelines/media/0303-061_moreoptionshover.png "0303-061_MoreOptionsHover")<br />Bouton 'Plus d’options' sur le bouton de commande

![Bouton 'Overflow' de barre de commande sur le plan stationnaire](../../extensibility/ux-guidelines/media/0303-062_overflowoptions.png "0303-062_OverflowOptions")<br />Bouton 'Overflow' de barre de commande sur le plan stationnaire

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.CommandBarOptionsMouseOverBackgroundBegin`<br />(Gradient s’arrête pour ce jeton non utilisé dans l’interface utilisateur thématique.) |
| Premier plan (glyphe) | `Environment.CommandBarOptionsMouseDownGlyph` |

**Barre de commande 'Plus d’options' et boutons 'Overflow': état pressé**

![Bouton de la barre de commande pressée 'Plus d’options'](../../extensibility/ux-guidelines/media/0303-063_moreoptionspressed.png "0303-063_MoreOptionsPressed")<br />Bouton de la barre de commande pressée 'Plus d’options'

![Bouton de dépassement enfoncé](../../extensibility/ux-guidelines/media/0303-064_overflowpressed.png "0303-064_OverflowPressed")<br />Bouton 'Overflow' de la barre de commande pressée

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.CommandBarOptionsMouseDownBackgroundBegin`<br />(Gradient s’arrête pour ce jeton non utilisé dans l’interface utilisateur thématique.) |
| Premier plan (glyphe) | `Environment.CommandBarOptionsMouseDownGlyph` |

## <a name="document-windows"></a>Fenêtres de document
Il n’est pas nécessaire de reproduire les fenêtres de documents, car elles sont fournies par l’environnement Visual Studio. Toutefois, vous pouvez décider d’exploiter les couleurs utilisées dans les fenêtres de document, afin que votre interface utilisateur apparaisse toujours cohérente avec cette partie de l’environnement Visual Studio.

Lorsque vous utilisez des jetons de couleur de fenêtre de document, veillez à les utiliser uniquement pour des éléments similaires, et toujours par paires. Si vous ne le faites pas, vous pourriez obtenir des résultats inattendus dans votre interface utilisateur.

### <a name="document-window-frames"></a>Cadres de fenêtre de document
Les fenêtres de document peuvent être ancrées dans l’IDE ou flottantes dans une fenêtre distincte. Lorsqu’une fenêtre de document flotte à l’extérieur de l’IDE, elle se trouve toujours bien dans un document et possède des couleurs d’arrière-plan, de bordure, de texte et d’onglet qui sont les mêmes que lorsqu’il fait partie de l’IDE. Toutefois, le document se trouve à l’intérieur d’un cadre qui a ses propres couleurs d’arrière-plan, de bordure et de texte. Quand les fenêtres d’outil sont ancrées dans la zone de configuration de document, elles héritent le comportement et la couleur de leurs onglets des noms de jeton de fenêtre de document.

![Fenêtre de document amarrée (redline)](../../extensibility/ux-guidelines/media/0303-065_dockeddocumentwindowredline.png "0303-065_DockedDocumentWindowRedline")<br />Fenêtre de document amarrée (redline)

![Fenêtre de document flottante (redline)](../../extensibility/ux-guidelines/media/0303-066_floatingdocumentwindowredline.png "0303-066_FloatingDocumentWindowRedline")<br />Fenêtre de document flottante (redline)

| Utiliser... | N’utilisez pas ... |
| --- | --- |
| ... où que vous créez l’interface utilisateur que vous souhaitez faire correspondre la fenêtre de document. | ...  pour toute interface utilisateur que vous ne voulez pas changer automatiquement si la coquille a une mise à jour thème. |

**Fenêtre de document amarrée ou flottante : état par défaut**

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | Dépend du type de document |
| Premier plan (texte) | Dépend du type de document |
| Bordure | `Environment.ToolWindowBorder` |

**Cadre de fenêtre de document focalisé et flottant : état par défaut**

![Cadre de fenêtre de document flottant axé par défaut](../../extensibility/ux-guidelines/media/0303-067_framefocused.png "0303-067_FrameFocused")<br />Cadre de fenêtre de document flottant axé par défaut

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.ToolWindowFloatingFrame` |
| Premier plan (texte) | `Environment.ToolWindowFloatingFrame` |
| Premier plan (glyphe) | `Environment.RaftedWindowButtonActiveGlyph` |
| Bordure | `Environment.MainWindowActiveDefaultBorder` |
| Bordure (glyphe) | `Environment.RaftedWindowButtonActiveBorder`<br />(Définir pour transparent) |

**Cadre de fenêtre de document flottant non focalisé : état par défaut**

![Cadre de fenêtre de document flottant non focalisé par défaut](../../extensibility/ux-guidelines/media/0303-068_frameunfocused.png "0303-068_FrameUnfocused")<br />Cadre de fenêtre de document flottant non focalisé par défaut

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.ToolWindowFloatingFrameInactive` |
| Premier plan (texte) | `Environment.ToolWindowFloatingFrameInactive` |
| Premier plan (glyphe) | `Environment.RaftedWindowButtonInactiveGlyph` |
| Bordure | `Environment.MainWindowInactiveBorder` |
| Bordure (glyphe) | `Environment.RaftedWindowButtonInactiveBorder`<br />(Définir pour transparent) |

**Cadre de fenêtre de document flottant concentré : état de vol stationnaire**

![Cadre de fenêtre de document flottant concentré sur le plan stationnaire](../../extensibility/ux-guidelines/media/0303-069_framefocusedhover.png "0303-069_FrameFocusedHover")<br />Cadre de fenêtre de document flottant concentré sur le plan stationnaire

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan (glyphe) | `Environment.RaftedWindowButtonHoverActive` |
| Premier plan (glyphe) | `Environment.RaftedWindowButtonHoverActiveGlyph` |
| Bordure (glyphe) | `Environment.RaftedWindowButtonHoverActiveBorder` |

**Cadre de fenêtre de document flottant non focalisé : état de vol stationnaire**

![Cadre de fenêtre flottante et non focalisé sur le plan stationnaire](../../extensibility/ux-guidelines/media/0303-070_frameunfocusedhover.png "0303-070_FrameUnfocusedHover")<br />Cadre de fenêtre flottante et non focalisé sur le plan stationnaire

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan (glyphe) | `EnvironmentRaftedWindowButtonHoverInactive` |
| Premier plan (glyphe) | `Environment.RaftedWindowButtonHoverInactiveGlyph` |
| Bordure (glyphe) | `Environment.RaftedWindowButtonHoverInactiveBorder` |

**Cadre de fenêtre de document flottant concentré : état pressé**

![Cadre de fenêtre de document concentré et flottant sur la presse](../../extensibility/ux-guidelines/media/0303-071_framefocusedpressed.png "0303-071_FrameFocusedPressed")<br />Cadre de fenêtre de document concentré et flottant sur la presse

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan (glyphe) | `Environment.RaftedWindowButtonDown` |
| Premier plan (glyphe) | `Environment.RaftedWindowButtonDownGlyph` |
| Bordure (glyphe) | `Environment.RaftedWindowButtonDownBorder` |

### <a name="document-tabs"></a>Onglets de document
Les onglets de document figurent dans le canal d’onglet pour indiquer quels documents sont actuellement ouverts, ainsi que celui qui correspond au document actuellement sélectionné ou actif. Les fenêtres d’outil peuvent également être ancrées dans le canal d’onglet de document, si l’utilisateur les y place. Dans ce cas, elles utilisent les mêmes couleurs d’onglet que celles des fenêtres de document. Si vous créez une interface utilisateur que vous voulez toujours faire correspondre aux couleurs de fenêtre de document (mises à jour du thème comprises ou si de nouveaux thèmes sont installés), alors référencez ces jetons de couleur.

![Onglets de documents (redline)](../../extensibility/ux-guidelines/media/0303-072_documenttabredline.png "0303-072_DocumentTabRedline")<br />Onglets de documents (redline)

| Utiliser... | N’utilisez pas ... |
| --- | --- |
| ... partout où vous créez l’interface utilisateur que vous souhaitez faire correspondre les onglets de documents et prendre automatiquement des mises à jour de thème ou de nouvelles couleurs de thème. | ... pour toute interface utilisateur que vous ne voulez pas modifier automatiquement lorsque la coquille a une mise à jour thème. |

#### <a name="open-document-tabs"></a>Onglets de document ouvert
Chaque document ouvert possède un onglet dans le canal d’onglet de document qui affiche son nom. Les documents peuvent être soit sélectionnés, soit ouverts en arrière-plan et leurs onglets reflètent ces états :

- L’onglet sélectionné représente le document actuellement affiché dans la zone de configuration de document. Un onglet sélectionné a une bordure de document qui s’étend sur le bord supérieur de la zone de configuration de document.

- Les onglets d’arrière-plan sont des onglets de documents qui ne sont pas l’onglet actuellement sélectionné. Une fois cliqués, ils deviennent l’onglet sélectionné et acquièrent toutes les couleurs de fond, de bordure et de texte de ces noms symboliques.

![Onglet de document ouvert (redline)](../../extensibility/ux-guidelines/media/0303-073_opendocumenttabredline.png "0303-073_OpenDocumentTabRedline")<br />Onglet de document ouvert (redline)

| Utiliser... | N’utilisez pas ... |
| --- | --- |
| ... lorsque vous créez des onglets de documents personnalisés. | ... pour les onglets provisoires (aperçu). |
| | ... pour toute interface utilisateur que vous ne souhaitez pas modifier automatiquement si la coquille a une mise à jour thème. |

**Onglet de document sélectionné et ciblé**

![Onglet de document sélectionné et ciblé](../../extensibility/ux-guidelines/media/0303-074_selectedtabfocused.png "0303-074_SelectedTabFocused")<br />Onglet de document sélectionné et ciblé

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.FileTabSelectedGradientTop`<br />(Gradient s’arrête pour ce jeton non utilisé dans l’interface utilisateur thématique.) |
| Premier plan (texte) | `Environment.FileTabSelectedText` |
| Bordure | `Environment.FileTabSelectedBorder`<br />(Définir à la même couleur que l’arrière-plan.) |
| Bordure de document | `Environment.FileTabDocumentBorderBackground` |

**Onglet de document sélectionné et non focalisé**

![Onglet de document sélectionné et non focalisé](../../extensibility/ux-guidelines/media/0303-075_selectedtabunfocused.png "0303-075_SelectedTabUnfocused")<br />Onglet de document sélectionné et non focalisé

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.FileTabInactiveGradientTop`<br />(Gradient s’arrête pour ce jeton non utilisé dans l’interface utilisateur thématique.) |
| Premier plan (texte) | `Environment.FileTabInactiveText` |
| Bordure | `Environment.FileTabInactiveBorder`<br />(Définir à la même couleur que l’arrière-plan.) |
| Bordure de document | `Environment.FileTabInactiveDocumentBorderBackground` |

**Onglet de document d’arrière-plan : état par défaut**

![Onglet de document d’arrière-plan par défaut](../../extensibility/ux-guidelines/media/0303-076_backgroundtab.png "0303-076_BackgroundTab")<br />Onglet de document d’arrière-plan par défaut

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.FileTabBackground` |
| Premier plan (texte) | `Environment.FileTabText` |
| Bordure | `Environment.FileTabBorder`<br />(Définir à la même couleur que l’arrière-plan.) |

**Onglet de document d’arrière-plan : état de vol stationnaire**

![Onglet de document d’arrière-plan sur le plan stationnaire](../../extensibility/ux-guidelines/media/0303-077_backgroundtabhover.png "0303-077_BackgroundTabHover")<br />Onglet de document d’arrière-plan sur le plan stationnaire

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.FileTabHotGradientTop`<br />(Gradient s’arrête pour ce jeton non utilisé dans l’interface utilisateur thématique.) |
| Premier plan (texte) | `Environment.FileTabHotText` |
| Bordure | `Environment.FileTabHotBorder`<br />(Définir à la même couleur que l’arrière-plan.) |

#### <a name="preview-tab"></a>Onglet d’aperçu
Aussi appelé un onglet "provisoire". L’onglet aperçu apparaît sur le côté droit du canal de l’onglet document lorsque l’utilisateur clique sur un élément dans la fenêtre de l’outil Solution Explorer. Il sert d’aperçu du document et donne également à l’utilisateur la possibilité de laisser le document ouvert sur le côté gauche du canal d’onglet de document. Une seul onglet d’aperçu peut être ouvert à la fois. Les onglets d’aperçu possèdent deux états, arrière-plan et sélectionné, comme les onglets ouverts, et leur état actif peut être avec ou sans focus.

![Onglet d’aperçu (redline)](../../extensibility/ux-guidelines/media/0303-078_previewtabredline.png "0303-078_PreviewTabRedline")<br />Onglet d’aperçu (redline)

| Utiliser... | N’utilisez pas ... |
| --- | --- |
| ... partout où vous créez un aperçu provisoire et que vous souhaitez un élément correspondant à la couleur actuelle de l’onglet aperçu. | ... pour tout type de document ou d’onglet qui n’est pas provisoire (aperçu). |
| | ... pour toute interface utilisateur que vous ne souhaitez pas modifier automatiquement si la coquille a une mise à jour thème. |

**Onglet de prévisualisation ciblé et sélectionné**

![Onglet de prévisualisation ciblé et sélectionné](../../extensibility/ux-guidelines/media/0303-079_previewtabfocused.png "0303-079_PreviewTabFocused")<br />Onglet de prévisualisation ciblé et sélectionné

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.FileTabProvisionalSelectedActive` |
| Premier plan (texte) | `Environment.FileTabProvisionalSelectedActiveForeground` |
| Bordure | `Environment.FileTabProvisionalSelectedActiveBorder`<br />(Définir à la même couleur que l’arrière-plan.) |
| Bordure de document | `Environment.FileTabProvisionalSelectedActiveBorder` |

**Onglet d’aperçu non focalisé et sélectionné**

![Onglet d’aperçu non focalisé et sélectionné](../../extensibility/ux-guidelines/media/0303-080_previewtabunfocused.png "0303-080_PreviewTabUnfocused")<br />Onglet d’aperçu non focalisé et sélectionné

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.FileTabProvisionalSelectedInactive` |
| Premier plan (texte) | `Environment.FileTabProvisionalSelectedInactiveForeground` |
| Bordure | `Environment.FileTabProvisionalSelectedInactiveBorder` |
| Bordure de document | `Environment.FileTabProvisionalSelectedInactiveBorder` |

**Onglet de prévisualisation d’arrière-plan : état par défaut**

![Onglet de prévisualisation d’arrière-plan par défaut](../../extensibility/ux-guidelines/media/0303-081_previewbackgroundtab.png "0303-081_PreviewBackgroundTab")<br />Onglet de prévisualisation d’arrière-plan par défaut

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.FileTabProvisionalInactive` |
| Premier plan (texte) | `Environment.FileTabProvisionalInactiveForeground` |
| Bordure | `Environment.FileTabProvisionalInactiveBorder`<br />(Définir à la même couleur que l’arrière-plan.) |

**Onglet d’aperçu d’arrière-plan : état de vol stationnaire**

![Onglet d’aperçu d’arrière-plan sur le plan stationnaire](../../extensibility/ux-guidelines/media/0303-082_previewbackgroundtabhover.png "0303-082_PreviewBackgroundTabHover")<br />Onglet d’aperçu d’arrière-plan sur le plan stationnaire

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.FileTabProvisionalHover` |
| Premier plan (texte) | `Environment.FileTabProvisionalHoverForeground` |
| Bordure | `Environment.FileTabProvisionalHoverBorder`<br />(Définir à la même couleur que l’arrière-plan.) |

#### <a name="document-overflow-button"></a>Bouton de dépassement de capacité de document
Le bouton de dépassement de capacité de document est présent si un ou plusieurs documents sont ouverts, que l’espace vertical défini dans la configuration actuelle suffise ou non pour loger tous les onglets de document. Le menu de débordement de document, qui est contrôlé par les couleurs du menu de barre de [commande,](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandMenus) affiche une liste de tous les documents ouverts, visibles et cachés, et le glyphe de débordement change selon que tous les documents ouverts sont affichés dans le canal d’onglet.

![Bouton de débordement de document (redline)](../../extensibility/ux-guidelines/media/0303-083_overflowredline.png "0303-083_OverflowRedline")<br />Bouton de débordement de document (redline)

| Utiliser... | N’utilisez pas ... |
| --- | --- |
| ... lorsque vous créez un bouton de débordement de document personnalisé. | ... pour l’interface utilisateur qui n’est pas similaire à un bouton de débordement. |
| | ... pour les boutons de débordement de barre de commande. |

**Bouton de débordement de document : état par défaut**

![Bouton de débordement de document par défaut](../../extensibility/ux-guidelines/media/0303-084_overflow.png "0303-084_Overflow")<br />Bouton de débordement de document par défaut

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.DocWellOverflowButtonBackground` |
| Premier plan (glyphe) | `Environment.DocWellOverflowButtonGlyph` |
| Bordure | N/A |

**Bouton de débordement de document : état de vol stationnaire**

![Bouton de dépassement de capacité de document au pointage](../../extensibility/ux-guidelines/media/0303-085_overflowhover.png "0303-085_OverflowHover")<br />Bouton de dépassement de capacité de document au pointage

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.DocWellOverflowButtonMouseOverBackground` |
| Premier plan (glyphe) | `Environment.DocWellOverflowButtonMouseOverGlyph` |
| Bordure | `Environment.DocWellOverflowButtonMouseOverBorder` |

**Bouton de débordement de document : état pressé**

![Bouton de débordement de document sur la presse](../../extensibility/ux-guidelines/media/0303-086_overflowpressed.png "0303-086_OverflowPressed")<br />Bouton de débordement de document sur la presse

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.DocWellOverflowButtonMouseDownBackground` |
| Premier plan (glyphe) | `Environment.DocWellOverflowButtonMouseDownGlyph` |
| Bordure | `Environment.DocWellOverflowButtonMouseDownBorder` |

### <a name="tagging"></a>Marquage
Visual Studio prend en charge l’étiquetage, qui permet à un utilisateur de déclarer des mots clés pouvant faire l’objet d’une recherche à des fins de suivi. Par exemple, les chefs de projet et développeurs peuvent utiliser Team Foundation Server (TFS) pour étiqueter des éléments de travail. Les tableaux ci-dessous indiquent les noms de couleurs pour l’étiquette elle-même et le glyphe de l’icône de fermeture qui apparaît dans les états Pointage et Sélectionné.

![Marquage dans Visual Studio (redline)](../../extensibility/ux-guidelines/media/0303-176_taggingredline.png "0303-176_TaggingRedline")<br />Marquage dans Visual Studio (redline)

| Utiliser... | N’utilisez pas ... |
| --- | --- |
| ... pour l’interface utilisateur qui prend en charge le marquage. | ... pour tout autre type d’interface utilisateur. |

#### <a name="tags"></a>Balises

**Tag: état par défaut**

![Étiquette par défaut](../../extensibility/ux-guidelines/media/0303-177_tag.png "0303-177_Tag")<br />Étiquette par défaut

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Tag.Background` |
| Premier plan (texte) | `Tag.Background` |

**Tag: état de vol stationnaire**

![Balise au pointage](../../extensibility/ux-guidelines/media/0303-178_taghover.png "0303-178_TagHover")<br />Balise au pointage

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Tag.HoverBackground` |
| Premier plan (texte) | `Tag.HoverBackgroundText` |

**Tag: état pressé**

![Étiquette pressée](../../extensibility/ux-guidelines/media/0303-179_tagpressed.png "0303-179_TagPressed")<br />Étiquette pressée

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Tag.PressedBackground` |
| Premier plan (texte) | `Tag.PressedBackgroundText` |

**Tag: état sélectionné**

![Tag sélectionné](../../extensibility/ux-guidelines/media/0303-180_tagselected.png "0303-180_TagSelected")<br />Tag sélectionné

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Tag.SelectedBackground` |
| Premier plan (texte) | `Tag.SelectedBackgroundText` |

#### <a name="close-times-tag-glyph"></a>Fermer&times;( ) tag glyph

**Fermer&times;( ) tag glyph: état par défaut**

![Fermeture par&times;défaut ( ) tag glyph](../../extensibility/ux-guidelines/media/0303-181_tagglyph.png "0303-181_TagGlyph")<br />Fermeture par&times;défaut ( ) tag glyph

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | N/A |
| Premier plan (glyphe) | `Tag.TagHoverGlyph` |

**Fermer&times;( ) tag glyph: état de vol stationnaire**

![Fermer&times;( ) tag glyph sur le plan stationnaire](../../extensibility/ux-guidelines/media/0303-182_tagglyphhover.png "0303-182_TagGlyphHover")<br />Fermer&times;( ) tag glyph sur le plan stationnaire

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Tag.TagHoverGlyphHoverBackground` |
| Premier plan (glyphe) | `Tag.TagHoverGlyphHover` |
| Bordure | `Tag.TagHoverGlyphHoverBorder` |

**Fermer&times;( ) tag glyph: état pressé**

![Pressed Close&times;( ) tag glyph](../../extensibility/ux-guidelines/media/0303-183_tagglyphpressed.png "0303-183_TagGlyphPressed")<br />Pressed Close&times;( ) tag glyph

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Tag.TagHoverGlyphPressedBackground` |
| Premier plan (glyphe) | `Tag.TagHoverGlyphPressed` |
| Bordure | `Tag.TagHoverGlyphPressedBorder` |

**Tag sélectionné avec&times;Close ( ) glyph: état par défaut**

![Tag sélectionné par&times;défaut avec Close ( ) glyph](../../extensibility/ux-guidelines/media/0303-184_tagselected.png "0303-184_TagSelected")<br />Tag sélectionné par&times;défaut avec Close ( ) glyph

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | N/A |
| Premier plan (glyphe) | `Tag.TagSelectedGlyph` |

**Tag sélectionné avec&times;Close ( ) glyph: état de vol stationnaire**

![Tag sélectionné avec&times;Close ( ) glyph sur le plan stationnaire](../../extensibility/ux-guidelines/media/0303-185_tagselectedhover.png "0303-185_TagSelectedHover")<br />Tag sélectionné avec&times;Close ( ) glyph sur le plan stationnaire

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Tag.TagSelectedGlyphHoverBackground` |
| Premier plan (glyphe) | `Tag.TagSelectedGlyphHover` |
| Bordure | `Tag.TagSelectedGlyphHoverBorder` |

**Tag sélectionné avec&times;Close ( ) glyph: état pressé**

![Sélectionné, étiquette pressée&times;avec Close ( ) glyph](../../extensibility/ux-guidelines/media/0303-186_tagselectedpressed.png "0303-186_TagSelectedPressed")<br />Sélectionné, étiquette pressée&times;avec Close ( ) glyph

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Tag.TagSelectedGlyphPressedBackground` |
| Premier plan (glyphe) | `Tag.TagSelectedGlyphPressed` |
| Bordure | `Tag.TagSelectedGlyphPressedBorder` |

## <a name="tool-windows"></a>Fenêtres d’outil
Il n’est pas nécessaire de reproduire les fenêtres des outils, car elles sont fournies par l’environnement Visual Studio. Toutefois, vous pouvez décider d’exploiter les couleurs utilisées dans les fenêtres d’outil, afin que votre interface utilisateur apparaisse toujours cohérente avec cette partie de l’environnement Visual Studio.

![Fenêtre d’outil (redline)](../../extensibility/ux-guidelines/media/0303-087_toolwindowredline.png "0303-087_ToolWindowRedline")<br />Fenêtre d’outil (redline)

| Utiliser... | N’utilisez pas ... |
| --- | --- |
| ... partout où vous créez l’interface utilisateur que vous souhaitez faire correspondre les fenêtres d’outils. | ... pour toute interface utilisateur que vous ne souhaitez pas modifier automatiquement si la coquille a une mise à jour thème. |

### <a name="tool-window-frame"></a>Cadre de fenêtre Outil
Les fenêtres d’outil dans Visual Studio sont utilisées pour de nombreuses tâches différentes et peuvent exister dans différents états. Si une fenêtre Outil est ouverte, elle peut être affectée à l’un des quatre côtés de la zone de document. Les fenêtres d’outil peuvent également flotter en dehors de l’IDE, ce qui leur permet d’être repositionnées n’importe où sur l’écran de l’utilisateur. Les fenêtres flottantes se trouvent toujours par-dessus l’IDE. Enfin, les fenêtres d’outil peuvent être ancrées comme des fenêtres de document et elles apparaissent sous la forme d’un onglet dans la zone de configuration de document. Les fenêtres d’outil ancrées comme des fenêtres de document sont colorées en partie à l’aide des noms de jeton de fenêtre de document.

![Cadre de fenêtre d’outil (redline)](../../extensibility/ux-guidelines/media/0303-088_toolwindowframeredline.png "0303-088_ToolWindowFrameRedline")<br />Cadre de fenêtre d’outil (redline)

| Utiliser... | N’utilisez pas ... |
| --- | --- |
| ...  partout où vous créez l’interface utilisateur que vous souhaitez faire correspondre les fenêtres d’outils. | ... pour toute interface utilisateur que vous ne souhaitez pas modifier automatiquement si la coquille a une mise à jour thème. |

**Fenêtre d’outil amarrée**

![Fenêtre d’outil amarrée](../../extensibility/ux-guidelines/media/0303-089_toolwindowdocked.png "0303-089_ToolWindowDocked")<br />Fenêtre d’outil amarrée

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.ToolWindowBackground` |
| Bordure | `Environment.ToolWindowBorder` |

**Fenêtre d’outil flottante et ciblée**

![Fenêtre d’outil flottante et ciblée](../../extensibility/ux-guidelines/media/0303-090_toolwindowfocused.png "0303-090_ToolWindowFocused")<br />Fenêtre d’outil flottante et ciblée

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.ToolWindowBackground` |
| Bordure | `Environment.MainWindowActiveDefaultBorder` |

**Fenêtre flottante et non focalisée d’outil**

![Fenêtre flottante et non focalisée d’outil](../../extensibility/ux-guidelines/media/0303-091_toolwindowunfocused.png "0303-091_ToolWindowUnfocused")<br />Fenêtre flottante et non focalisée d’outil

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.ToolWindowBackground` |
| Bordure | `Environment.MainWindowInactiveBorder` |

### <a name="toolbox-like-windows"></a>Fenêtres en ce qui ameillement
La boîte à outils est l’une des fenêtres d’outils communes les plus fréquemment utilisées dans Visual Studio. Il s’agit essentiellement d’un contrôle des arbres avec un thème spécial et le style appliqué.

![Fenêtre en type boîte à outils (redline)](../../extensibility/ux-guidelines/media/0303-189_toolboxredline.png "0303-189_ToolboxRedline")<br />Fenêtre en type boîte à outils (redline)

| Utiliser... | N’utilisez pas ... |
| --- | --- |
| ... lorsque vous concevez une fenêtre d’outil que vous voulez toujours être compatible avec la boîte à outils shell. | ... pour tout ce qui n’est pas similaire à l’interface utilisateur boîte à outils, ou si vous n’êtes pas sûr si votre interface utilisateur aura des problèmes si les couleurs de boîte à outils shell changer. |

**Noeuds de boîte à outils : état par défaut**

![Noeud parent par défaut de boîte à outils](../../extensibility/ux-guidelines/media/0303-190_toolboxparentnode.png "0303-190_ToolboxParentNode")<br />Noeud parent par défaut de boîte à outils

![Noeud d’enfant par défaut de boîte à outils](../../extensibility/ux-guidelines/media/0303-191_toolboxchildnode.png "0303-191_ToolboxChildNode")<br />Noeud d’enfant par défaut de boîte à outils

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.ToolboxContent`<br />(Headings) |
| Arrière-plan | `Environment.ToolWindowBackground`<br />(Articles individuels, ou fenêtre entière si aucun contrôle disponible) |
| Bordure | None |
| Premier plan (glyphe) | `Environment.ToolboxContent` |
| Premier plan (texte) | `Environment.ToolboxContent` |

**Noeuds d’enfant de boîte à outils : état de vol stationnaire**

![Nœud enfant de boîte à outils au pointage](../../extensibility/ux-guidelines/media/0303-192_toolboxchildnodehover.png "0303-192_ToolboxChildNodeHover")<br />Nœud enfant de boîte à outils au pointage

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.ToolboxContentMouseOver`<br />(Articles individuels seulement) |
| Bordure | None |
| Premier plan (texte) | `Environment.ToolboxContentMouseOver`<br />(Articles individuels seulement) |

**Nœuds de boîte à outils sélectionnés : état focalisé**

![Nœud parent ciblé et sélectionné](../../extensibility/ux-guidelines/media/0303-193_toolboxparentnodefocused.png "0303-193_ToolboxParentNodeFocused")<br />Nœud parent ciblé et sélectionné

![Nœud d’enfant ciblé et sélectionné](../../extensibility/ux-guidelines/media/0303-194_toolboxchildnodefocused.png "0303-194_ToolboxChildNodeFocused")<br />Nœud d’enfant ciblé et sélectionné

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `TreeView.SelectedItemActive`<br />À partir de la catégorie [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |
| Bordure | `TreeView.FocusVisualBorder`<br />À partir de la catégorie [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |
| Premier plan (glyphe) | `TreeView.SelectedItemActive`<br />À partir de la catégorie [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |
| Premier plan (texte) | `TreeView.SelectedItemActive`<br />À partir de la catégorie [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |

**Nœuds de boîte à outils sélectionnés : état non focalisé**

![Nœud parent sélectionné et non focalisé](../../extensibility/ux-guidelines/media/0303-195_toolboxparentnodeunfocused.png "0303-195_ToolboxParentNodeUnfocused")<br />Nœud parent sélectionné et non focalisé

![Nœud d’enfant sélectionné et non focalisé](../../extensibility/ux-guidelines/media/0303-196_toolboxchildnodeunfocused.png "0303-196_ToolboxChildNodeUnfocused")<br />Nœud d’enfant sélectionné et non focalisé

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `TreeView.SelectedItemInactive`<br />À partir de la catégorie [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |
| Bordure | None |
| Premier plan (glyphe) | `TreeView.SelectedItemInactive`<br />À partir de la catégorie [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |
| Premier plan (texte) | `TreeView.SelectedItemInactive`<br />À partir de la catégorie [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView) |

### <a name="tool-window-title-bar"></a>Barre de titre de fenêtre Outil
La frontière de barre de titre n’est pas une vraie frontière, c’est une ligne épaisse à travers le haut de la barre de titre. Il n’a pas de nom symbolique pour son état non focalisé.

![Barre de titre de fenêtre d’outil (redline)](../../extensibility/ux-guidelines/media/0303-092_toolwindowtitlebarredline.png "0303-092_ToolWindowTitleBarRedline")<br />Barre de titre de fenêtre d’outil (redline)

| Utiliser... | N’utilisez pas ... |
| --- | --- |
| ... partout où vous créez l’interface utilisateur que vous souhaitez faire correspondre les fenêtres d’outils. | ... pour toute interface utilisateur que vous ne souhaitez pas modifier automatiquement si la coquille a une mise à jour thème. |

**Barre de titre avec focus**

![Barre de titre avec focus](../../extensibility/ux-guidelines/media/0303-093_titlebarfocused.png "0303-093_TitleBarFocused")<br />Barre de titre avec focus

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.TitleBarActiveGradientBegin`<br />(Gradient s’arrête pour ce jeton non utilisé dans l’interface utilisateur thématique.) |
| Premier plan (texte) | `Environment.TitleBarActiveText` |
| Bordure | `Environment.TitleBarActiveBorder`<br />(Définir à la même couleur que l’arrière-plan.) |
| Poignée de redimensionnement | `Environment.TitleBarDragHandleActive` |

**Barre de titre sans focus**

![Barre de titre inactive](../../extensibility/ux-guidelines/media/0303-094_titlebarunfocused.png "0303-094_TitleBarUnfocused")<br />Barre de titre sans focus

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.TitleBarInactiveGradientBegin`<br />(Gradient s’arrête pour ce jeton non utilisé dans l’interface utilisateur thématique.) |
| Premier plan (texte) | `Environment.TitleBarInactiveText` |
| Bordure | N/A |
| Poignée de redimensionnement | `Environment.TitleBarDragHandle` |

#### <a name="tool-window-title-bar-buttons"></a>Boutons de barre de titre de fenêtre d’outil
![Bouton de barre de titre (redline)](../../extensibility/ux-guidelines/media/0303-095_titlebarbuttonredline.png "0303-095_TitleBarButtonRedline")<br />Bouton de barre de titre (redline)

| Utiliser... | N’utilisez pas ... |
| --- | --- |
| ... pour les boutons qui apparaissent dans l’interface utilisateur qui utilise des jetons de couleur à partir des barres de titre de fenêtre d’outil. | ... pour les boutons qui apparaissent dans d’autres endroits. |
| | ... dans n’importe quelle combinaison de fond/premier plan autre que spécifiée. |

**Boutons de barre de titre ciblés : état par défaut**

![Boutons de barre de titre par défaut et ciblés](../../extensibility/ux-guidelines/media/0303-096_titlebarbuttonfocused.png "0303-096_TitleBarButtonFocused")<br />Boutons de barre de titre par défaut et ciblés

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | N/A |
| Premier plan (glyphe) | `Environment.ToolWindowButtonActiveGlyph` |
| Bordure | N/A |

**Boutons de barre de titre non focalisé : état par défaut**

![Boutons de barre de titre non focalisés par défaut](../../extensibility/ux-guidelines/media/0303-097_titlebarbuttonunfocused.png "0303-097_TitleBarButtonUnfocused")<br />Boutons de barre de titre non focalisés par défaut

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | N/A |
| Premier plan (glyphe) | `Environment.ToolWindowButtonInactiveGlyph` |
| Bordure | N/A |

**Boutons de barre de titre focalisés : état de vol stationnaire**

![Boutons de barre de titre concentrés sur le plan stationnaire](../../extensibility/ux-guidelines/media/0303-098_titlebarbuttonfocusedhover.png "0303-098_TitleBarButtonFocusedHover")<br />Boutons de barre de titre concentrés sur le plan stationnaire

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.ToolWindowButtonHoverActive` |
| Premier plan (glyphe) | `Environment.ToolWindowButtonHoverActiveGlyph` |
| Bordure | `Environment.ToolWindowButtonHoverActiveBorder` |

**Boutons de barre de titre non focalisé : état de vol stationnaire**

![Boutons de barre de titre non focalisé sur le plan stationnaire](../../extensibility/ux-guidelines/media/0303-099_titlebarbuttonunfocusedhover.png "0303-099_TitleBarButtonUnfocusedHover")<br />Boutons de barre de titre non focalisé sur le plan stationnaire

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.ToolWindowButtonHoverInactive` |
| Premier plan (glyphe) | `Environment.ToolWindowButtonHoverInactiveGlyph` |
| Bordure | `Environment.ToolWindowButtonHoverInactiveBorder` |

**Boutons de barre de titre ciblés : état pressé**

![Boutons de barre de titre concentrés sur la presse](../../extensibility/ux-guidelines/media/0303-100_titlebarbuttonfocusedpressed.png "0303-100_TitleBarButtonFocusedPressed")<br />Boutons de barre de titre concentrés sur la presse

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.ToolWindowButtonDown` |
| Premier plan (glyphe) | `Environment.ToolWindowButtonDownActiveGlyph` |
| Bordure | `Environment.ToolWindowButtonDownBorder` |

**Boutons de barre de titre non focalisé : état pressé**

![Boutons de barre de titre non focalisé sur la presse](../../extensibility/ux-guidelines/media/0303-101_titlebarbuttonunfocusedpressed.png "0303-101_TitleBarButtonUnfocusedPressed")<br />Boutons de barre de titre non focalisé sur la presse

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.ToolWindowButtonDown` |
| Premier plan (glyphe) | `Environment.ToolWindowButtonDownInactiveGlyph` |
| Bordure | `Environment.ToolWindowButtonDownBorder` |

### <a name="tool-window-tabs"></a>Onglets de fenêtre Outil
![Onglet de fenêtre d’outil (redline)](../../extensibility/ux-guidelines/media/0303-102_toolwindowtabredline.png "0303-102_ToolWindowTabRedline")<br />Onglet de fenêtre d’outil (redline)

| Utiliser... | N’utilisez pas ... |
| --- | --- |
| ... partout où vous créez l’interface utilisateur que vous souhaitez faire correspondre les fenêtres d’outils. | ... pour toute interface utilisateur que vous ne souhaitez pas modifier automatiquement si la coquille a une mise à jour thème. |

**Onglet de fenêtre Outil sélectionné, avec focus**

![Onglet de fenêtre Outil sélectionné, avec focus](../../extensibility/ux-guidelines/media/0303-103_toolwindowtabfocused.png "0303-103_ToolWindowTabFocused")<br />Onglet de fenêtre Outil sélectionné, avec focus

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.ToolWindowTabSelectedTab` |
| Premier plan (texte) | `Environment.ToolWindowTabSelectedActiveText` |
| Bordure | `Environment.ToolWindowTabSelectedBorder`<br />(Définir à la même couleur que l’arrière-plan.) |

**Onglet de fenêtre Outil sélectionné, sans focus**

![Onglet de fenêtre Outil sélectionné, sans focus](../../extensibility/ux-guidelines/media/0303-104_toolwindowtabunfocused.png "0303-104_ToolWindowTabUnfocused")<br />Onglet de fenêtre Outil sélectionné, sans focus

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.ToolWindowTabSelectedTab` |
| Premier plan (texte) | `Environment.ToolWindowTabSelectedText` |
| Bordure | `Environment.ToolWindowTabSelectedBorder`<br />(Définir à la même couleur que l’arrière-plan.) |

**Onglet de fenêtre d’outil d’arrière-plan : état par défaut**

![Onglet de fenêtre d’outil d’arrière-plan par défaut](../../extensibility/ux-guidelines/media/0303-105_toolwindowbackgroundtab.png "0303-105_ToolWindowBackgroundTab")<br />Onglet de fenêtre d’outil d’arrière-plan par défaut

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.ToolWindowTabGradientBegin`<br />`Environment.ToolWindowTabGradientEnd`<br />(Gradient s’arrête fixé à la même valeur de couleur dans Visual Studio 2013.) |
| Premier plan (texte) | `Environment.ToolWindowTabText` |
| Bordure | `Environment.ToolWindowTabBorder` |

**Onglet de fenêtre d’outil de fond : état de vol stationnaire**

![Onglet de fenêtre Outil d’arrière-plan au pointage](../../extensibility/ux-guidelines/media/0303-106_toolwindowbackgroundtabhover.png "0303-106_ToolWindowBackgroundTabHover")<br />Onglet de fenêtre Outil d’arrière-plan au pointage

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.ToolWindowTabMouseOverBackgroundBegin`<br />`Environment.ToolWindowTabMouseOverBackgroundEnd`<br />(Gradient s’arrête fixé à la même valeur de couleur dans Visual Studio 2013.) |
| Premier plan (texte) | `Environment.ToolWindowTabMouseOverText` |
| Bordure | `Environment.ToolWindowTabMouseOverBorder`<br />(Définir à la même couleur que l’arrière-plan.) |

### <a name="auto-hide-tabs"></a>Onglets à masquage automatique

![Onglets de cache automatique (redline)](../../extensibility/ux-guidelines/media/0303-107_autohideredline.png "0303-107_AutoHideRedline") Onglets de cache automatique (redline)

| Utiliser... | N’utilisez pas ... |
| --- | --- |
| ... partout où vous créez l’interface utilisateur que vous souhaitez faire correspondre les onglets de fenêtre d’outil auto-cachés. | ... pour toute interface utilisateur que vous ne souhaitez pas modifier automatiquement si la coquille a une mise à jour thème. |

**Onglets de cache automatique : état par défaut**

![Onglet à masquage automatique par défaut](../../extensibility/ux-guidelines/media/0303-108_autohidetab.png "0303-108_AutoHideTab")<br />Onglet à masquage automatique par défaut

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.AutoHideTabBackgroundBegin`<br />(Gradient s’arrête pour ce jeton non utilisé dans l’interface utilisateur thématique.) |
| Premier plan (texte) | `Environment.AutoHideTabText` |
| Bordure | `Environment.AutoHideTabBorder` |

**Onglets de cache automatique : état de vol stationnaire**

![Masquer automatiquement l'onglet au pointage](../../extensibility/ux-guidelines/media/0303-109_autohidetabhover.png "0303-109_AutoHideTabHover")<br />Masquer automatiquement l'onglet au pointage

| Élément | Nom du jeton : Category.color |
| --- | --- |
| Arrière-plan | `Environment.AutoHideTabMouseOverBackgroundBegin`<br />(Gradient s’arrête pour ce jeton non utilisé dans l’interface utilisateur thématique.) |
| Premier plan (texte) | `Environment.AutoHideTabMouseOverText` |
| Bordure | `Environment.AutoHideTabMouseOverBorder` |
