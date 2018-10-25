---
title: Partagé des couleurs pour Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8d11b9a0-6175-4f2e-8e7f-79daee1bfd41
caps.latest.revision: 6
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 72aaaa4a3eb75043f4a2cf3bdd20352bdd2af93b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49856689"
---
# <a name="shared-colors-for-visual-studio"></a>Couleurs partagées pour Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Quand vous concevez l’interface utilisateur qui utilise des éléments d’interpréteur de commandes Visual Studio, ou si vous voulez que votre élément d’interface soit cohérent avec des fonctionnalités similaires, utilisez des noms de jeton existants dans les fichiers de définition de package pour choisir et assigner des couleurs. Ainsi, votre interface utilisateur reste cohérente avec l’environnement Visual Studio global et elle se met à jour automatiquement quand des thèmes sont ajoutés ou mis à jour.  
  
 Cet article décrit les éléments d’interface utilisateur communs et les noms de jeton qu’ils utilisent, que vous pouvez référencer pour créer une interface utilisateur similaire. Pour plus d’informations sur la façon d’accéder à ces jetons de couleur, consultez [The VSColor Service](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService).  
  
 Assurez-vous d’utiliser correctement les noms de jeton :  
  
-   **Utiliser des noms de jeton basés sur la fonction, pas sur la couleur elle-même.** Les couleurs partagées communes sont associées à des éléments d’interface spécifiques et uniquement destinées à être utilisées pour des fonctionnalités identiques ou similaires. Par exemple, ne réutilisez pas la couleur d’une zone de liste modifiable enfoncée pour une animation de progression en rotation juste parce que vous aimez la couleur. Les fonctions de la zone de liste modifiable et l’animation sont différentes, et si la couleur associée à la zone de liste modifiable change, elle peut ne plus convenir à votre élément d’animation. Une utilisation cohérente des couleurs permet de guider vos utilisateurs et d’éviter toute confusion.  
  
-   **Utiliser des couleurs d’arrière-plan et de texte dans la combinaison correcte.** Les couleurs d’arrière-plan destinées à être utilisées avec du texte possèdent une couleur de texte associée. N’utilisez pas de couleurs de texte autres que celles spécifiées pour l’arrière-plan. En l’absence de couleur de texte associée, n’utilisez pas cette couleur d’arrière-plan pour n’importe quelle surface sur laquelle vous voulez présenter du texte. Des combinaisons d’autres couleurs de texte et d’arrière-plan peuvent donner une interface illisible.  
  
-   **Utiliser les couleurs de contrôle qui sont appropriées à leur emplacement.** Dans certains états, certains contrôles Visual Studio ne présentent pas des couleurs de bordure et d’arrière-plan distinctes. Au lieu de cela, ils sélectionnent ces couleurs dans les surfaces qui se trouvent derrière. Veillez à toujours utiliser les noms de jeton qui conviennent à l’emplacement où vous placez le contrôle.  
  
> [!IMPORTANT]
>  N’utilisez pas les jetons trouvés dans les catégories « Page d’accueil » ou « Cider ».  
  
## <a name="command-structures"></a>Structures de commande  
  
###  <a name="BKMK_CommandMenus"></a> Menus  
 Menus peuvent se produire à plusieurs endroits dans Visual Studio : la barre de menus principale incorporée dans le document ou l’outil windows, ou sur avec le bouton droit à divers endroits de l’IDE. Les implémentations de menus associées aux autres éléments d’interface utilisateur sont décrites dans la section de l’élément correspondant. Vous devez toujours utiliser l’implémentation de menu standard fournie par l’environnement Visual Studio. Toutefois, dans de rares cas, vous n’aurez peut-être pas accès aux menus Visual Studio standard. Dans ce cas, utilisez les noms de jeton suivants pour vous assurer que votre interface utilisateur est cohérente avec les autres menus dans Visual Studio.  
  
 ![Ligne rouge de menus](../../extensibility/ux-guidelines/media/0303-000-menuredline.png "0303-000_MenuRedline")  
  
 Utilisez...  
 -   chaque fois que vous devez créer un menu personnalisé.  
  
- quand vous voulez faire correspondre un nouveau composant d’interface utilisateur aux menus Visual Studio.  
  
  N’utilisez pas...  
  la couleur d’arrière-plan toute seule. Utilisez toujours la combinaison arrière-plan/premier plan spécifiée.  
  
#### <a name="menu-title"></a>Titre de menu  
 Les titres de menu comprennent un arrière-plan, une bordure et le texte du titre, ainsi qu’un glyphe facultatif, généralement quand le menu se trouve dans une barre de commandes.  
  
 ![Ligne rouge de titre de menu](../../extensibility/ux-guidelines/media/0303-001-menutitleredline.png "0303-001_MenuTitleRedline")  
  
 Utilisez...  
 chaque fois que vous créez un titre de menu personnalisé.  
  
 N’utilisez pas...  
 -   pour tout élément que vous ne voulez pas toujours faire correspondre au titre de menu.  
  
- dans une combinaison arrière-plan/premier plan autre que celle spécifiée.  
  
  **Default**  
  
  Composant  
  
  Élément  
  
  Nom du jeton : Category.color  
  
  ![Par défaut de titre de menu](../../extensibility/ux-guidelines/media/0303-002-menutitledefault.png "0303-002_MenuTitleDefault")  
  
  **Titre de menu**  
  
  Présentation  
  
  Aucun.  
  
  Premier plan (texte)  
  
  `Environment.CommandBarTextActive`  
  
  ![Titre de menu avec valeur par défaut de glyphe](../../extensibility/ux-guidelines/media/0303-003-menutitlewithglyphdefault.png "0303-003_MenuTitleWithGlyphDefault")  
  
  **Titre de menu avec glyphe**  
  
  Premier plan (glyphe)  
  
  `Environment.CommandBarMenuGlyph`  
  
  Bordure  
  
  Aucun.  
  
  **Placez le curseur**  
  
  Composant  
  
  Élément  
  
  Nom du jeton : Category.color  
  
  ![Titre de menu au pointage](../../extensibility/ux-guidelines/media/0303-004-menutitlehover.png "0303-004_MenuTitleHover")  
  
  **Titre de menu**  
  
  Présentation  
  
  `Environment.CommandBarMouseOverBackgroundBegin`  
  
  Même si cet arrière-plan n’est pas utilisé dans l’interface utilisateur à thème moderne, il comporte des points et valeurs de dégradés.  
  
  Premier plan (texte)  
  
  `Environment.CommandBarTextHover`  
  
  ![Titre de menu avec glyphe au pointage](../../extensibility/ux-guidelines/media/0303-005-menutitlewithglyphhover.png "0303-005_MenuTitleWithGlyphHover")  
  
  **Titre de menu avec glyphe**  
  
  Premier plan (glyphe)  
  
  `Environment.CommandBarMenuMouseOverGlyph`  
  
  Bordure  
  
  `Environment.CommandBarBorder`  
  
  **Enfoncé**  
  
  Composant  
  
  Élément  
  
  Nom du jeton : Category.color  
  
  ![Titre de menu enfoncé](../../extensibility/ux-guidelines/media/0303-006-menutitlepressed.png "0303-006_MenuTitlePressed")  
  
  **Titre de menu**  
  
  Présentation  
  
  `Environment.CommandBarMenuBackgroundGradientBegin`  
  
  Même si cet arrière-plan n’est pas utilisé dans l’interface utilisateur à thème moderne, il comporte des points et valeurs de dégradés.  
  
  Premier plan (texte)  
  
  `Environment.CommandBarTextActive`  
  
  ![Titre de menu avec glyphe enfoncé](../../extensibility/ux-guidelines/media/0303-007-menutitlewithglyphpressed.png "0303-007_MenuTitleWithGlyphPressed")  
  
  **Titre de menu avec glyphe**  
  
  Premier plan (glyphe)  
  
  `Environment.CommandBarMenuMouseDownGlyph`  
  
  Bordure  
  
  `Environment.CommandBarMenuBorder`  
  
  Uniquement les côtés gauche, supérieur et droit.  
  
  **Désactivé**  
  
  Composant  
  
  Élément  
  
  Nom du jeton : Category.color  
  
  ![Titre de menu avec glyphe désactivé](../../extensibility/ux-guidelines/media/0303-008-menutitlewithglyphdisabled.png "0303-008_MenuTitleWithGlyphDisabled")  
  
  **Titre de menu avec glyphe**  
  
  Présentation  
  
  Aucun.  
  
  Premier plan (texte)  
  
  `Environment.CommandBarTextInactive`  
  
  Premier plan (glyphe)  
  
  `Environment.CommandBarTextInactive`  
  
  Bordure  
  
  Aucun.  
  
#### <a name="menu"></a>Menu  
 Un élément de menu individuel comporte le texte du menu et éventuellement une icône, une case à cocher ou un glyphe de sous-menu. Sa couleur d’arrière-plan et de texte change au passage du curseur de la souris. Ce jeton de couleur est une paire arrière-plan/premier plan.  
  
 ![Ligne rouge d’éléments de menu](../../extensibility/ux-guidelines/media/0303-009-menuitemredline.png "0303-009_MenuItemRedline")  
  
 Utilisez...  
 pour toute liste déroulante lancée à partir d’une barre de menus ou barre de commandes.  
  
 N’utilisez pas...  
 -   pour toute liste déroulante qui apparaît dans un autre contexte.  
  
- dans une combinaison arrière-plan/premier plan autre que celle spécifiée.  
  
  **Default**  
  
  Composant  
  
  Élément  
  
  Nom du jeton : Category.color  
  
  ![Par défaut du menu](../../extensibility/ux-guidelines/media/0303-010-menudefault.png "0303-010_MenuDefault")  
  
  **Menu**  
  
  Présentation  
  
  `Environment.CommandBarMenuBackgroundGradientBegin`  
  
  Même si cet arrière-plan n’est pas utilisé dans l’interface utilisateur à thème moderne, il comporte des points et valeurs de dégradés.  
  
  Premier plan (texte)  
  
  `Environment.CommandBarTextActive`  
  
  Premier plan (glyphe de sous-menu)  
  
  `Environment.CommandBarMenuSubmenuGlyph`  
  
  Bordure  
  
  `Environment.CommandBarMenuBorder`  
  
  Arrière-plan de canal d’icône  
  
  `Environment.CommandBarMenuIconBackground`  
  
  Séparateur  
  
  `Environment.CommandBarMenuSeparator`  
  
  Ombre  
  
  `Environment.DropShadowBackground`  
  
  ![Menu activé](../../extensibility/ux-guidelines/media/0303-011-menuchecked.png "0303-011_MenuChecked")  
  
  **Activé**  
  
  Coche  
  
  `Environment.CommandBarCheckBox`  
  
  Arrière-plan de case à cocher  
  
  `Environment.CommandBarSelectedIcon`  
  
  ![Menu sélectionné](../../extensibility/ux-guidelines/media/0303-012-menuselected.png "0303-012_MenuSelected")  
  
  **sélectionné**  
  
  Arrière-plan d’icône  
  
  `Environment.CommandBarSelected`  
  
  Bordure d’icône  
  
  `Environment.CommandBarSelectedBorder`  
  
  **Placez le curseur**  
  
  Composant  
  
  Élément  
  
  Nom du jeton : Category.color  
  
  ![Pointage de menu](../../extensibility/ux-guidelines/media/0303-013-menuhover.png "0303-013_MenuHover")  
  
  **Élément de menu**  
  
  Présentation  
  
  `Environment.CommandBarMenuItemMouseOver`  
  
  Premier plan (texte)  
  
  `Environment.CommandBarMenuItemMouseOver`  
  
  Premier plan (glyphe de sous-menu)  
  
  `Environment.CommandBarMenuMouseOverSubmenuGlyph`  
  
  ![Pointage de menu activé](../../extensibility/ux-guidelines/media/0303-014-menuhoverchecked.png "0303-014_MenuHoverChecked")  
  
  **Activé**  
  
  Coche  
  
  `Environment.CommandBarCheckBoxMouseOver`  
  
  Arrière-plan de case à cocher  
  
  `Environment.CommandBarHoverOverSelectedIcon`  
  
  ![Pointage de menu sélectionné](../../extensibility/ux-guidelines/media/0303-015-menuhoverselected.png "0303-015_MenuHoverSelected")  
  
  **sélectionné**  
  
  Arrière-plan d’icône  
  
  `Environment.CommandBarHoverOverSelected`  
  
  Bordure d’icône  
  
  `Environment.CommandBarHoverOverSelectedIconBorder`  
  
  **Désactivé**  
  
  Composant  
  
  Élément  
  
  Nom du jeton : Category.color  
  
  ![Menu désactivé](../../extensibility/ux-guidelines/media/0303-016-menudisabled.png "0303-016_MenuDisabled")  
  
  Menu Item  
  
  Premier plan (texte)  
  
  `Environment.CommandBarTextInactive`  
  
  Premier plan (glyphe de sous-menu)  
  
  `Environment.CommandBarMenuSubmenuGlyph`  
  
  ![Menu désactivé activé](../../extensibility/ux-guidelines/media/0303-017-menudisabledchecked.png "0303-017_MenuDisabledChecked")  
  
  Activé  
  
  Coche  
  
  `Environment.CommandBarCheckBoxDisabled`  
  
  Arrière-plan de case à cocher  
  
  `Environment.CommandBarSelectedIconDisabled`  
  
### <a name="command-bar"></a>Barre de commandes  
 La barre de commandes peut apparaître à plusieurs endroits dans l’IDE Visual Studio, notamment dans l’interface de commande et incorporée dans des fenêtres de document ou d’outil.  
  
 En règle générale, utilisez toujours l’implémentation de barre de commandes standard fournie par l’environnement Visual Studio. L’utilisation du mécanisme standard permet à tous les détails visuels d’apparaître correctement et aux éléments interactifs de se comporter de manière cohérente avec les autres contrôles de barre de commandes Visual Studio. Toutefois, si vous avez besoin de créer votre propre barre de commandes, assurez-vous d’utiliser un style adéquat avec les noms de jeton suivants.  
  
 ![Ligne rouge de barre de commandes](../../extensibility/ux-guidelines/media/0303-018-commandbarredline.png "0303-018_CommandBarRedline")  
  
 ![Ligne rouge de bouton de dépassement de capacité](../../extensibility/ux-guidelines/media/0303-019-overflowbuttonredline.png "0303-019_OverflowButtonRedline")  
  
 Utilisez...  
 aux endroits où vous avez besoin d’une barre de commandes incorporée alors que vous ne pouvez pas utiliser l’implémentation de barre de commandes Visual Studio standard.  
  
 N’utilisez pas...  
 -   pour les éléments d’interface utilisateur non similaires à une barre de commandes.  
  
-   pour les composants de barre de commandes autres que ceux pour lesquels des noms de jeton sont spécifiés.  
  
#### <a name="command-bar-group"></a>Groupe de barres de commandes  
 Un groupe de barres de commandes se compose d’un ensemble de contrôles de barre de commandes et peut contenir tout nombre de boutons, boutons partagés, menus déroulants, zones de liste modifiable ou menus. Les couleurs de ces contrôles sont régies par des noms de jeton distincts et sont décrites individuellement dans une autre section de ce guide. Un trait de séparation est utilisé pour diviser un groupe de barres de commandes en sous-groupes associés.  
  
 ![Ligne rouge de groupe de barres de commande](../../extensibility/ux-guidelines/media/0303-020-commandbargroupredline.png "0303-020_CommandBarGroupRedline")  
  
 Utilisez...  
 aux endroits où vous avez besoin d’une barre de commandes incorporée alors que vous ne pouvez pas utiliser l’implémentation de barre de commandes Visual Studio standard.  
  
 N’utilisez pas...  
 -   pour les éléments d’interface utilisateur non similaires à une barre de commandes.  
  
- pour les composants de barre de commandes autres que ceux pour lesquels des noms de jeton sont spécifiés.  
  
  **Par défaut** (aucun autre état)  
  
  Élément  
  
  Nom du jeton : Category.color  
  
  Présentation  
  
  `Environment.CommandBarGradientBegin`  
  
  Même si cet arrière-plan n’est pas utilisé dans l’interface utilisateur à thème moderne, il comporte des points et valeurs de dégradés.  
  
  Bordure  
  
  `Environment.CommandBarToolBarBorder`  
  
  Faire glisser la poignée  
  
  `Environment.CommandBarDragHandle`  
  
  Séparateur  
  
  `Environment.CommandBarToolBarSeparator`  
  
  `Environment.CommandBarToolBarSeparatorHighlight`  
  
#### <a name="command-icons"></a>Icônes de commande  
 ![Ligne rouge d’icône de commande](../../extensibility/ux-guidelines/media/0303-021-commandiconredline1.png "0303-021_CommandIconRedline1")  
  
 ![Ligne rouge d’icône de commande](../../extensibility/ux-guidelines/media/0303-022-commandiconredline2.png "0303-022_CommandIconRedline2")  
  
 Utilisez...  
 pour les boutons à placer sur une barre de commandes.  
  
 N’utilisez pas...  
 -   pour les contrôles qui possèdent leurs propres noms de jeton.  
  
- dans une combinaison arrière-plan/premier plan autre que celle spécifiée.  
  
  **Default**  
  
  Composant  
  
  Élément  
  
  Nom du jeton : Category.color  
  
  ![Commande par défaut d’icône](../../extensibility/ux-guidelines/media/0303-023-commandicondefault.png "0303-023_CommandIconDefault")  
  
  **Default**  
  
  Présentation  
  
  N/A (hérite de l’arrière-plan de la barre commandes)  
  
  Premier plan (texte)  
  
  `Environment.CommandBarTextActive`  
  
  Bordure  
  
  N/A  
  
  ![Commande par défaut d’icône sélectionnée](../../extensibility/ux-guidelines/media/0303-024-commandicondefaultselected.png "0303-024_CommandIconDefaultSelected")  
  
  **sélectionné**  
  
  Présentation  
  
  `Environment.CommandBarSelected`  
  
  Premier plan (texte)  
  
  `Environment.CommandBarTextSelected`  
  
  Bordure  
  
  `Environment.CommandBarSelectedBorder`  
  
  **Pointage et porte sur le clavier**  
  
  Composant  
  
  Élément  
  
  Nom du jeton : Category.color  
  
  ![Pointage d’icône de commande](../../extensibility/ux-guidelines/media/0303-025-commandiconhover.png "0303-025_CommandIconHover")  
  
  **Standard au pointage**  
  
  Présentation  
  
  `Environment.CommandBarMouseOverBackgroundBegin`  
  
  Même si cet arrière-plan n’est pas utilisé dans l’interface utilisateur à thème moderne, il comporte des points et valeurs de dégradés.  
  
  Premier plan (texte)  
  
  `Environment.CommandBarTextHover`  
  
  Bordure  
  
  `Environment.CommandBarBorder`  
  
  ![Pointage d’icône sélectionnée de la commande](../../extensibility/ux-guidelines/media/0303-026-commandiconhoverselected.png "0303-026_CommandIconHoverSelected")  
  
  **Sélectionné au pointage**  
  
  Présentation  
  
  `Environment.CommandBarHoverOverSelected`  
  
  Premier plan (texte)  
  
  `Environment.CommandBarTextHoverOverSelected`  
  
  Bordure  
  
  `Environment.CommandBarHoverOverSelectedIconBorder`  
  
  **Enfoncé**  
  
  Composant  
  
  Élément  
  
  Nom du jeton : Category.color  
  
  ![Icône de commande enfoncée](../../extensibility/ux-guidelines/media/0303-027-commandiconpressed.png "0303-027_CommandIconPressed")  
  
  **Icône de commande appuyée**  
  
  Présentation  
  
  `Environment.CommandBarMouseDownBackgroundBegin`  
  
  Même si cet arrière-plan n’est pas utilisé dans l’interface utilisateur à thème moderne, il comporte des points et valeurs de dégradés.  
  
  Premier plan (texte)  
  
  `Environment.CommandBarTextMouseDown`  
  
  Bordure  
  
  `Environment.CommandBarBorder`  
  
  **Désactivé**  
  
  Composant  
  
  Élément  
  
  Nom du jeton : Category.color  
  
  ![Icône de commande désactivée](../../extensibility/ux-guidelines/media/0303-028-commandicondisabled.png "0303-028_CommandIconDisabled")  
  
  **Icône de commande désactivée**  
  
  Présentation  
  
  N/A (hérite de l’arrière-plan de la barre commandes)  
  
  Premier plan (texte)  
  
  `Environment.CommandBarTextInactive`  
  
  Bordure  
  
  N/A  
  
####  <a name="BKMK_CommandComboBox"></a> Zone de liste déroulante  
  
> [!IMPORTANT]
>  Les zones de liste modifiable ressemblent aux listes déroulantes, mais elles comprennent une zone de texte modifiable. Si votre liste déroulante n’inclut pas de zone de texte modifiable, utilisez les jetons de couleur disponibles sous [Drop-down](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandDropDown).  
  
 ![Ligne rouge de zone de liste déroulante](../../extensibility/ux-guidelines/media/0303-029-comboboxredline.png "0303-029_ComboBoxRedline")  
  
 Utilisez...  
 -   pour créer des zones de liste modifiable personnalisées.  
  
- pour créer un contrôle de barre de commandes similaire à une zone de liste modifiable.  
  
  N’utilisez pas...  
  -   pour tout élément que vous ne voulez pas toujours faire correspondre à l’interface utilisateur de la barre de commandes.  
  
- quand vous avez accès à une zone de liste modifiable qui comporte un style.  
  
  **Default**  
  
  Composant  
  
  Élément  
  
  Nom du jeton : Category.color  
  
  ![Champ d’entrée de zone de liste déroulante](../../extensibility/ux-guidelines/media/0303-030-comboboxinputfield.png "0303-030_ComboBoxInputField")  
  
  **Champ d’entrée**  
  
  Présentation  
  
  `Environment.ComboBoxBackground`  
  
  Premier plan (texte)  
  
  `Environment.ComboBoxText`  
  
  Bordure  
  
  `Environment.ComboBoxBorder`  
  
  Séparateur  
  
  Aucun séparateur  
  
  ![Liste de zone de liste déroulante&#45;bouton enfoncé](../../extensibility/ux-guidelines/media/0303-031-comboboxdropdownbutton.png "0303-031_ComboBoxDropdownButton")  
  
  **Bouton de liste déroulante**  
  
  Présentation  
  
  N/A (hérite)  
  
  Premier plan (glyphe)  
  
  `Environment.ComboBoxGlyph`  
  
  ![Zone de liste déroulante&#47;drop&#45;liste déroulante](../../extensibility/ux-guidelines/media/0303-032-comboboxdropdownlist.png "0303-032_ComboBoxDropdownList")  
  
  **Liste déroulante**  
  
  Présentation  
  
  `Environment.ComboBoxPopupBackgroundBegin`  
  
  Même si cet arrière-plan n’est pas utilisé dans l’interface utilisateur à thème moderne, il comporte des points et valeurs de dégradés.  
  
  Premier plan (texte)  
  
  `Environment.ComboBoxItemText`  
  
  Bordure  
  
  `Environment.ComboBoxPopupBorder`  
  
  **Placez le curseur**  
  
  Composant  
  
  Élément  
  
  Nom du jeton : Category.color  
  
  ![Champ d’entrée de zone de liste déroulante au pointage](../../extensibility/ux-guidelines/media/0303-033-comboboxinputfieldhover.png "0303-033_ComboBoxInputFieldHover")  
  
  **Champ d’entrée**  
  
  Présentation  
  
  `Environment.ComboBoxMouseOverBackgroundBegin`  
  
  Même si cet arrière-plan n’est pas utilisé dans l’interface utilisateur à thème moderne, il comporte des points et valeurs de dégradés.  
  
  Premier plan (texte)  
  
  `Environment.ComboBoxMouseOverText`  
  
  Bordure  
  
  `Environment.ComboBoxMouseOverBorder`  
  
  Séparateur  
  
  `Environment.ComboBoxMouseOverSeparator`  
  
  ![Zone de liste déroulante&#47;drop&#45;le bouton de survol](../../extensibility/ux-guidelines/media/0303-034-comboboxdropdownbuttonhover.png "0303-034_ComboBoxDropdownButtonHover")  
  
  **Bouton de liste déroulante**  
  
  Présentation  
  
  `Environment.ComboBoxButtonMouseOverBackground`  
  
  Premier plan (glyphe)  
  
  `Environment.ComboBoxMouseOverGlyph`  
  
  ![Zone de liste déroulante&#47;drop&#45;liste pointage vers le bas](../../extensibility/ux-guidelines/media/0303-035-comboboxdropdownlisthover.png "0303-035_ComboBoxDropdownListHover")  
  
  **Liste déroulante**  
  
  Arrière-plan (élément de menu)  
  
  `Environment.ComboBoxItemMouseOverBackground`  
  
  Premier plan (texte)  
  
  `Environment.ComboBoxItemMouseOverText`  
  
  Bordure (élément de menu)  
  
  `Environment.ComboBoxItemMouseOverBorder`  
  
  **Focus**  
  
  Composant  
  
  Élément  
  
  Nom du jeton : Color.category  
  
  ![Champ d’entrée de zone de liste déroulante concentré](../../extensibility/ux-guidelines/media/0303-036-comboboxinputfieldfocused.png "0303-036_ComboBoxInputFieldFocused")  
  
  **Champ d’entrée**  
  
  Présentation  
  
  `Environment.ComboBoxFocusedBackground`  
  
  Premier plan (texte)  
  
  `Environment.ComboBoxFocusedText`  
  
  Bordure  
  
  `Environment.ComboBoxFocusedBorder`  
  
  Séparateur  
  
  `Environment.ComboBoxFocusedButtonSeparator`  
  
  ![Zone de liste déroulante&#47;drop&#45;vers le bas du bouton actif](../../extensibility/ux-guidelines/media/0303-037-comboboxdropdownbuttonfocused.png "0303-037_ComboBoxDropdownButtonFocused")  
  
  **Bouton de liste déroulante**  
  
  Présentation  
  
  `Environment.ComboBoxFocusedButtonBackground`  
  
  Premier plan (glyphe)  
  
  `Environment.ComboBoxFocusedGlyph`  
  
  **Enfoncé**  
  
  Composant  
  
  Élément  
  
  Nom du jeton : Color.category  
  
  ![Champ d’entrée de zone de liste déroulante enfoncé](../../extensibility/ux-guidelines/media/0303-038-comboboxinputfieldpressed.png "0303-038_ComboBoxInputFieldPressed")  
  
  **Champ d’entrée**  
  
  Présentation  
  
  `Environment.ComboBoxMouseDownBackground`  
  
  Premier plan (texte)  
  
  `Environment.ComboBoxMouseDownText`  
  
  Bordure  
  
  `Environment.ComboBoxMouseDownBorder`  
  
  Séparateur  
  
  `Environment.ComboBoxMouseDownSeparator`  
  
  ![Zone de liste déroulante&#47;drop&#45;le bouton enfoncé](../../extensibility/ux-guidelines/media/0303-039-comboboxdropdownbuttonpressed.png "0303-039_ComboBoxDropdownButtonPressed")  
  
  **Bouton de liste déroulante**  
  
  Présentation  
  
  `Environment.ComboBoxButtonMouseDownBackground`  
  
  Premier plan (glyphe)  
  
  `Environment.ComboBoxMouseDownGlyph`  
  
  **Désactivé**  
  
  ![Champ d’entrée de zone de liste déroulante désactivée](../../extensibility/ux-guidelines/media/0303-041-comboboxinputfielddisabled.png "0303-041_ComboBoxInputFieldDisabled")  
  
  **Champ d’entrée**  
  
  Présentation  
  
  `Environment.ComboBoxDisabledBackground`  
  
  Premier plan (texte)  
  
  `Environment.ComboBoxDisabledText`  
  
  Bordure  
  
  `Environment.ComboBoxDisabledBorder`  
  
  Séparateur  
  
  Aucun séparateur  
  
  ![Zone de liste déroulante&#47;drop&#45;le bouton désactivé](../../extensibility/ux-guidelines/media/0303-040-comboboxdropdownbuttondisabled.png "0303-040_ComboBoxDropdownButtonDisabled")  
  
  **Bouton de liste déroulante**  
  
  Présentation  
  
  Aucun.  
  
  Premier plan (glyphe)  
  
  `Environment.ComboBoxDisabledGlyph`  
  
####  <a name="BKMK_CommandDropDown"></a> Liste déroulante  
  
> [!IMPORTANT]
>  Les listes déroulantes ressemblent aux zones de liste modifiable, mais elles ne disposent pas de zones de texte modifiable. Si votre liste déroulante inclut une zone de texte modifiable, utilisez les jetons de couleur disponibles sous [Combo box](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandComboBox).  
  
 ![DROP&#45;vers le bas ligne rouge](../../extensibility/ux-guidelines/media/0303-042-dropdownredline.png "0303-042_DropdownRedline")  
  
 Utilisez...  
 quand vous créez des contrôles de liste déroulante personnalisés.  
  
 N’utilisez pas...  
 -   pour tout élément qui n’est pas similaire à une liste déroulante.  
  
- pour les zones de liste modifiable ou les boutons partagés.  
  
  **Default**  
  
  Composant  
  
  Élément  
  
  Nom du jeton : Category.color  
  
  ![DROP&#45;vers le bas du champ de sélection](../../extensibility/ux-guidelines/media/0303-043-dropdownselectionfield.png "0303-043_DropdownSelectionField")  
  
  **Champ de sélection**  
  
  Présentation  
  
  `Environment.DropDownBackground`  
  
  Premier plan (texte)  
  
  `DropDownText`  
  
  Bordure  
  
  `DropDownBorder`  
  
  Séparateur  
  
  Aucun séparateur  
  
  ![DROP&#45;bouton enfoncé](../../extensibility/ux-guidelines/media/0303-044-dropdownbutton.png "0303-044_DropdownButton")  
  
  **Bouton de liste déroulante**  
  
  Présentation  
  
  Aucun.  
  
  Premier plan (glyphe)  
  
  `Environment.DropDownGlyph`  
  
  ![DROP&#45;liste déroulante](../../extensibility/ux-guidelines/media/0303-045-dropdownlist.png "0303-045_DropdownList")  
  
  **Liste déroulante**  
  
  Présentation  
  
  `Environment.DropDownPopupBackgroundBegin`  
  
  Même si cet arrière-plan n’est pas utilisé dans l’interface utilisateur à thème moderne, il comporte des points et valeurs de dégradés.  
  
  Premier plan (texte)  
  
  `Environment.ComboBoxItemText`  
  
  Bordure  
  
  `Environment.DropDownPopupBorder`  
  
  Ombre  
  
  `Environment.DropShadowBackground`  
  
  **Placez le curseur**  
  
  Composant  
  
  Élément  
  
  Nom du jeton : Category.color  
  
  ![DROP&#45;vers le bas du champ de sélection de survol](../../extensibility/ux-guidelines/media/0303-046-dropdownselectionfieldhover.png "0303-046_DropdownSelectionFieldHover")  
  
  **Champ de sélection**  
  
  Présentation  
  
  `Environment.DropDownMouseOverBackgroundBegin`  
  
  Même si cet arrière-plan n’est pas utilisé dans l’interface utilisateur à thème moderne, il comporte des points et valeurs de dégradés.  
  
  Premier plan (texte)  
  
  `Environment.DropDownMouseOverText`  
  
  Bordure  
  
  `Environment.DropDownMouseOverBorder`  
  
  Séparateur  
  
  `Environment.DropDownButtonMouseOverSeparator`  
  
  ![DROP&#45;le bouton de survol](../../extensibility/ux-guidelines/media/0303-047-dropdownbuttonhover.png "0303-047_DropdownButtonHover")  
  
  **Bouton de liste déroulante**  
  
  Présentation  
  
  `Environment.DropDownButtonMouseOverBackground`  
  
  Premier plan (glyphe)  
  
  `Environment.DropDownMouseOverGlyph`  
  
  ![DROP&#45;liste pointage vers le bas](../../extensibility/ux-guidelines/media/0303-048-dropdownlisthover.png "0303-048_DropdownListHover")  
  
  **Liste déroulante**  
  
  Arrière-plan (élément de menu)  
  
  `Environment.ComboBoxItemMouseOverBackground`  
  
  Premier plan (texte)  
  
  `Environment.ComboBoxItemMouseOverText`  
  
  Bordure (élément de menu)  
  
  `Environment.ComboBoxItemMouseOverBorder`  
  
  **Enfoncé**  
  
  Composant  
  
  Élément  
  
  Nom du jeton : Category.color  
  
  ![DROP&#45;vers le bas du champ de sélection enfoncé](../../extensibility/ux-guidelines/media/0303-049-dropdownselectionfieldpressed.png "0303-049_DropdownSelectionFieldPressed")  
  
  **Champ de sélection**  
  
  Présentation  
  
  `Environment.DropDownMouseDownBackground`  
  
  Premier plan (texte)  
  
  `Environment.DropDownMouseDownText`  
  
  Bordure  
  
  `Environment.DropDownMouseDownBorder`  
  
  Séparateur  
  
  `Environment.DropDownButtonMouseDownSeparator`  
  
  ![DROP&#45;le bouton enfoncé](../../extensibility/ux-guidelines/media/0303-050-dropdownbuttonpressed.png "0303-050_DropdownButtonPressed")  
  
  **Bouton de liste déroulante**  
  
  Présentation  
  
  `Environment.DropDownButtonMouseDownBackground`  
  
  Premier plan (glyphe)  
  
  `Environment.DropDownMouseDownGlyph`  
  
  **Désactivé**  
  
  Composant  
  
  Élément  
  
  Nom du jeton : Category.color  
  
  ![DROP&#45;vers le bas du champ de sélection désactivée](../../extensibility/ux-guidelines/media/0303-051-dropdownselectionfielddisabled.png "0303-051_DropdownSelectionFieldDisabled")  
  
  Présentation  
  
  `Environment.DropDownDisabledBackground`  
  
  Premier plan (texte)  
  
  `Environment.DropDownDisabledText`  
  
  Bordure  
  
  `Environment.DropDownDisabledBorder`  
  
  Séparateur  
  
  Aucun séparateur  
  
  ![DROP&#45;le bouton désactivé](../../extensibility/ux-guidelines/media/0303-052-dropdownbuttondisabled.png "0303-052_DropdownButtonDisabled")  
  
  Présentation  
  
  N/A  
  
  Premier plan (glyphe)  
  
  `Environment.DropDownDisabledGlyph`  
  
#### <a name="split-button"></a>Bouton Fractionner  
 Les boutons partagés partagent de nombreux noms de jeton avec d’autres contrôles de barre de commandes, tels que des boutons, menus et texte de barre de commandes. Toutes les actions nécessaires et les noms de jeton bouton de liste déroulante sont répétés ici par commodité. Les listes déroulantes de bouton partagé sont des implémentations de la barre de commandes [Menus](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_CommandMenus).  
  
 ![Ligne rouge de bouton partagé](../../extensibility/ux-guidelines/media/0303-053-splitbuttonredline.png "0303-053_SplitButtonRedline")  
  
 Utilisez...  
 quand vous créez un bouton partagé personnalisé.  
  
 N’utilisez pas...  
 -   pour les autres types de boutons.  
  
- dans une combinaison arrière-plan/premier plan autre que celle spécifiée.  
  
  **Default**  
  
  Composant  
  
  Élément  
  
  Nom du jeton : Category.color  
  
  ![Bouton partagé](../../extensibility/ux-guidelines/media/0303-054-splitbutton.png "0303-054_SplitButton")  
  
  **Bouton partagé (par défaut)**  
  
  Présentation  
  
  Aucun.  
  
  Premier plan (texte)  
  
  `Environment.CommandBarTextActive`  
  
  Premier plan (glyphe)  
  
  `Environment.CommandBarSplitButtonGlyph`  
  
  Bordure  
  
  N/A  
  
  Séparateur  
  
  N/A  
  
  **Placez le curseur**  
  
  Composant  
  
  Élément  
  
  Nom du jeton : Category.color  
  
  ![Bouton Fractionner au pointage](../../extensibility/ux-guidelines/media/0303-055-splitbuttonhover.png "0303-055_SplitButtonHover")  
  
  **Bouton partagé (pointage)**  
  
  Présentation  
  
  `Environment.CommandBarMouseOverBackgroundBegin`  
  
  Même si cet arrière-plan n’est pas utilisé dans l’interface utilisateur à thème moderne, il comporte des points et valeurs de dégradés.  
  
  Premier plan (texte)  
  
  `Environment.CommandBarTextHover`  
  
  Premier plan (glyphe)  
  
  `Environment.CommandBarSplitButtonMouseOverGlyph`  
  
  Bordure  
  
  `Environment.CommandBarBorder`  
  
  Séparateur  
  
  `Environment.CommandBarSplitButtonSeparator`  
  
  **Enfoncé**  
  
  Composant  
  
  Élément  
  
  Nom du jeton : Category.color  
  
  ![Bouton Fractionner enfoncé](../../extensibility/ux-guidelines/media/0303-056-splitbuttonpressed.png "0303-056_SplitButtonPressed")  
  
  **Bouton partagé (appuyé)**  
  
  Présentation  
  
  `Environment.CommandBarMouseDownBackgroundBegin`  
  
  Même si cet arrière-plan n’est pas utilisé dans l’interface utilisateur à thème moderne, il comporte des points et valeurs de dégradés.  
  
  Premier plan (texte)  
  
  `Environment.CommandBarTextMouseDown`  
  
  Premier plan (glyphe)  
  
  `Environment.CommandBarSplitButtonMouseDownGlyph`  
  
  Bordure  
  
  `Environment.CommandBarBorder`  
  
  Séparateur  
  
  N/A  
  
  **Désactivé**  
  
  Composant  
  
  Élément  
  
  Nom du jeton : Category.color  
  
  ![Bouton Fractionner désactivé](../../extensibility/ux-guidelines/media/0303-057-splitbuttondisabled.png "0303-057_SplitButtonDisabled")  
  
  **Bouton partagé (désactivé)**  
  
  Présentation  
  
  N/A  
  
  Premier plan (texte)  
  
  `Environment.ComboBoxItemTextInactive`  
  
  Premier plan (glyphe)  
  
  `Environment.CommandBarTextInactive`  
  
  Bordure  
  
  N/A  
  
  Séparateur  
  
  N/A  
  
#### <a name="more-options-and-overflow-buttons"></a>Boutons « Autres options » et « >> »  
 Le bouton « Autres options » est utilisé quand un groupe de barres de commandes peut être personnalisé en ajoutant ou en supprimant des boutons de barre de commandes associés. Le bouton « >> » apparaît quand une barre de commandes est tronquée en raison d’un manque d’espace horizontal. En cliquant dessus, un menu se déroule pour afficher les autres boutons de la barre de commandes qui ne pouvaient pas apparaître. Les couleurs de ces deux boutons sont contrôlées par le même ensemble de noms de jeton.  
  
 ![Ligne rouge de davantage d’options](../../extensibility/ux-guidelines/media/0303-058-moreoptionsredline.png "0303-058_MoreOptionsRedline")  
  
 Utilisez...  
 pour les boutons « Autres options » ou « >> » personnalisés.  
  
 N’utilisez pas...  
 pour les boutons qui n’ont pas de fonctionnalité similaire à celle d’un bouton « Autres options » ou « >> ».  
  
 **Default**  
  
 Composant  
  
 Élément  
  
 Nom du jeton : Category.color  
  
 ![Plus d’options](../../extensibility/ux-guidelines/media/0303-059-moreoptions.png "0303-059_MoreOptions")  
  
 **Plus d’options**  
  
 ![Bouton de dépassement](../../extensibility/ux-guidelines/media/0303-060-overflow.png "0303-060_Overflow")  
  
 **dépassement de capacité**  
  
 Présentation  
  
 `Environment.CommandBarOptionsBackground`  
  
 Premier plan (glyphe)  
  
 `Environment.CommandBarOptionsGlyph`  
  
 **Placez le curseur**  
  
 Composant  
  
 Élément  
  
 Nom du jeton : Category.color  
  
 ![Plus d’options au pointage](../../extensibility/ux-guidelines/media/0303-061-moreoptionshover.png "0303-061_MoreOptionsHover")  
  
 **Plus d’options**  
  
 ![Dépassement au pointage](../../extensibility/ux-guidelines/media/0303-062-overflowoptions.png "0303-062_OverflowOptions")  
  
 **dépassement de capacité**  
  
 Présentation  
  
 `Environment.CommandBarOptionsMouseOverBackgroundBegin`  
  
 Même si cet arrière-plan n’est pas utilisé dans l’interface utilisateur à thème moderne, il comporte des points et valeurs de dégradés.  
  
 Premier plan (glyphe)  
  
 `Environment.CommandBarOptionsMouseDownGlyph`  
  
 **Enfoncé**  
  
 Composant  
  
 Élément  
  
 Nom du jeton : Category.color  
  
 ![Autres options enfoncée](../../extensibility/ux-guidelines/media/0303-063-moreoptionspressed.png "0303-063_MoreOptionsPressed")  
  
 **Plus d’options**  
  
 ![Dépassement enfoncé](../../extensibility/ux-guidelines/media/0303-064-overflowpressed.png "0303-064_OverflowPressed")  
  
 **dépassement de capacité**  
  
 Présentation  
  
 `Environment.CommandBarOptionsMouseDownBackgroundBegin`  
  
 Même si cet arrière-plan n’est pas utilisé dans l’interface utilisateur à thème moderne, il comporte des points et valeurs de dégradés.  
  
 Premier plan (glyphe)  
  
 `Environment.CommandBarOptionsMouseDownGlyph`  
  
## <a name="document-windows"></a>Fenêtres de document  
 Il est inutile de répliquer les fenêtres de document, car elles sont fournies par l’environnement Visual Studio. Toutefois, vous pouvez décider d’exploiter les couleurs utilisées dans les fenêtres de document, afin que votre interface utilisateur apparaisse toujours cohérente avec cette partie de l’environnement Visual Studio.  
  
 Quand vous utilisez les jetons de couleur de fenêtre de document, vous devez veiller à les utiliser uniquement pour les éléments similaires et toujours par paires. Si vous ne le faites pas, vous obtiendrez des résultats inattendus dans votre interface utilisateur.  
  
### <a name="document-window-frame"></a>Cadre de fenêtre de document  
 Les fenêtres de document peuvent être ancrées dans l’IDE ou flottantes dans une fenêtre distincte. Quand une fenêtre de document flotte en dehors de l’IDE, elle figure toujours dans une zone de configuration de document et ses couleurs d’arrière-plan, de bordure, de texte et d’onglets sont les mêmes que celles qu’elle utilise quand elle fait partie de l’IDE. Toutefois, le document se trouve à l’intérieur d’un cadre qui a ses propres couleurs d’arrière-plan, de bordure et de texte. Quand les fenêtres d’outil sont ancrées dans la zone de configuration de document, elles héritent le comportement et la couleur de leurs onglets des noms de jeton de fenêtre de document.  
  
 ![Ligne rouge de fenêtre de document ancrée](../../extensibility/ux-guidelines/media/0303-065-dockeddocumentwindowredline.png "0303-065_DockedDocumentWindowRedline")  
  
 **Fenêtre de document ancrée**  
  
 ![Ligne rouge de fenêtre de document flottante](../../extensibility/ux-guidelines/media/0303-066-floatingdocumentwindowredline.png "0303-066_FloatingDocumentWindowRedline")  
  
 **Fenêtre de document flottante**  
  
 Utilisez...  
 à tout endroit où vous créez une interface utilisateur que vous voulez faire correspondre à la fenêtre de document.  
  
 N’utilisez pas...  
 pour toute interface utilisateur que vous ne voulez pas modifier automatiquement si l’interpréteur de commandes comporte une mise à jour de thème.  
  
 **Default**  
  
 Composant  
  
 Élément  
  
 Nom du jeton : Category.color  
  
 Document : ancré ou flottant  
  
 Présentation  
  
 Dépend du type de document  
  
 Premier plan (texte)  
  
 Dépend du type de document  
  
 Bordure  
  
 `Environment.ToolWindowBorder`  
  
 ![Frame actif](../../extensibility/ux-guidelines/media/0303-067-framefocused.png "0303-067_FrameFocused")  
  
 **Cadre : flottant, avec focus**  
  
 Présentation  
  
 `Environment.ToolWindowFloatingFrame`  
  
 Premier plan (texte)  
  
 `Environment.ToolWindowFloatingFrame`  
  
 Premier plan (glyphe)  
  
 `Environment.RaftedWindowButtonActiveGlyph`  
  
 Bordure  
  
 `Environment.MainWindowActiveDefaultBorder`  
  
 Bordure (glyphe)  
  
 `Environment.RaftedWindowButtonActiveBorder`  
  
 Défini sur transparent  
  
 ![Frame inactif](../../extensibility/ux-guidelines/media/0303-068-frameunfocused.png "0303-068_FrameUnfocused")  
  
 **Cadre : flottant, sans focus**  
  
 Présentation  
  
 `Environment.ToolWindowFloatingFrameInactive`  
  
 Premier plan (texte)  
  
 `Environment.ToolWindowFloatingFrameInactive`  
  
 Premier plan (glyphe)  
  
 `Environment.RaftedWindowButtonInactiveGlyph`  
  
 Bordure  
  
 `Environment.MainWindowInactiveBorder`  
  
 Bordure (glyphe)  
  
 `Environment.RaftedWindowButtonInactiveBorder`  
  
 Défini sur transparent  
  
 **Placez le curseur**  
  
 Composant  
  
 Élément  
  
 Nom du jeton : Category.color  
  
 ![Frame actif au pointage](../../extensibility/ux-guidelines/media/0303-069-framefocusedhover.png "0303-069_FrameFocusedHover")  
  
 **Cadre : flottant, avec focus**  
  
 Arrière-plan (glyphe)  
  
 `Environment.RaftedWindowButtonHoverActive`  
  
 Premier plan (glyphe)  
  
 `Environment.RaftedWindowButtonHoverActiveGlyph`  
  
 Bordure (glyphe)  
  
 `Environment.RaftedWindowButtonHoverActiveBorder`  
  
 ![Frame inactif au pointage](../../extensibility/ux-guidelines/media/0303-070-frameunfocusedhover.png "0303-070_FrameUnfocusedHover")  
  
 **Cadre : flottant, sans focus**  
  
 Arrière-plan (glyphe)  
  
 `EnvironmentRaftedWindowButtonHoverInactive`  
  
 Premier plan (glyphe)  
  
 `Environment.RaftedWindowButtonHoverInactiveGlyph`  
  
 Bordure (glyphe)  
  
 `Environment.RaftedWindowButtonHoverInactiveBorder`  
  
 **Enfoncé**  
  
 Composant  
  
 Élément  
  
 Nom du jeton : Category.color  
  
 ![Frame actif enfoncé](../../extensibility/ux-guidelines/media/0303-071-framefocusedpressed.png "0303-071_FrameFocusedPressed")  
  
 **Cadre : flottant, avec focus**  
  
 Arrière-plan (glyphe)  
  
 `Environment.RaftedWindowButtonDown`  
  
 Premier plan (glyphe)  
  
 `Environment.RaftedWindowButtonDownGlyph`  
  
 Bordure (glyphe)  
  
 `Environment.RaftedWindowButtonDownBorder`  
  
### <a name="document-tabs"></a>Onglets de document  
 Les onglets de document figurent dans le canal d’onglet pour indiquer quels documents sont actuellement ouverts, ainsi que celui qui correspond au document actuellement sélectionné ou actif. Les fenêtres d’outil peuvent également être ancrées dans le canal d’onglet de document, si l’utilisateur les y place. Dans ce cas, elles utilisent les mêmes couleurs d’onglet que celles des fenêtres de document. Si vous créez une interface utilisateur que vous voulez toujours faire correspondre aux couleurs de fenêtre de document (mises à jour du thème comprises ou si de nouveaux thèmes sont installés), alors référencez ces jetons de couleur.  
  
 ![Ligne rouge d’onglet de document](../../extensibility/ux-guidelines/media/0303-072-documenttabredline.png "0303-072_DocumentTabRedline")  
  
 Utilisez...  
 à tout endroit où vous créez une interface utilisateur que vous voulez faire correspondre aux onglets de document et qui sélectionne automatiquement les mises à jour du thème ou de nouvelles couleurs de thème.  
  
 N’utilisez pas...  
 pour toute interface utilisateur que vous ne voulez pas modifier automatiquement quand l’interpréteur de commandes comporte une mise à jour de thème.  
  
#### <a name="open-document-tabs"></a>Onglets de document ouvert  
 Chaque document ouvert possède un onglet dans le canal d’onglet de document qui affiche son nom. Les documents peuvent être soit sélectionnés, soit ouverts en arrière-plan et leurs onglets reflètent ces états :  
  
- L’onglet sélectionné représente le document actuellement affiché dans la zone de configuration de document. Un onglet sélectionné a une bordure de document qui s’étend sur le bord supérieur de la zone de configuration de document.  
  
- Les onglets d’arrière-plan sont les onglets de document qui ne sont pas l’onglet actuellement sélectionné. Une fois que vous cliquez dessus, ils deviennent l’onglet sélectionné et acquièrent toutes les couleurs d’arrière-plan, de bordure et de texte de ces noms de jeton.  
  
  ![Ligne rouge d’onglet de document ouvert](../../extensibility/ux-guidelines/media/0303-073-opendocumenttabredline.png "0303-073_OpenDocumentTabRedline")  
  
  Utilisez...  
  quand vous créez des onglets de document personnalisés.  
  
  N’utilisez pas...  
  -   pour des onglets provisoires (en version préliminaire).  
  
- pour toute interface utilisateur que vous ne voulez pas modifier automatiquement si l’interpréteur de commandes comporte une mise à jour de thème.  
  
#### <a name="selected-tab"></a>Onglet sélectionné  
 **Focus**  
  
 Composant  
  
 Élément  
  
 Nom du jeton : Category.color  
  
 ![Onglet sélectionné actif](../../extensibility/ux-guidelines/media/0303-074-selectedtabfocused.png "0303-074_SelectedTabFocused")  
  
 **Onglet de document sélectionné, actif**  
  
 Présentation  
  
 `Environment.FileTabSelectedGradientTop`  
  
 Même si cet arrière-plan n’est pas utilisé dans l’interface utilisateur à thème moderne, il comporte des points et valeurs de dégradés.  
  
 Premier plan (texte)  
  
 `Environment.FileTabSelectedText`  
  
 Bordure  
  
 `Environment.FileTabSelectedBorder`  
  
 Défini sur la même couleur que l’arrière-plan.  
  
 Bordure de document  
  
 `Environment.FileTabDocumentBorderBackground`  
  
 **Inactif**  
  
 Composant  
  
 Élément  
  
 Nom du jeton : Category.color  
  
 ![Onglet sélectionné inactif](../../extensibility/ux-guidelines/media/0303-075-selectedtabunfocused.png "0303-075_SelectedTabUnfocused")  
  
 **Onglet de document sélectionné, sans focus**  
  
 Présentation  
  
 `Environment.FileTabInactiveGradientTop`  
  
 Même si cet arrière-plan n’est pas utilisé dans l’interface utilisateur à thème moderne, il comporte des points et valeurs de dégradés.  
  
 Premier plan (texte)  
  
 `Environment.FileTabInactiveText`  
  
 Bordure  
  
 `Environment.FileTabInactiveBorder`  
  
 Défini sur la même couleur que l’arrière-plan.  
  
 Bordure de document  
  
 `Environment.FileTabInactiveDocumentBorderBackground`  
  
#### <a name="background-tab"></a>Onglet en arrière-plan  
 **Default**  
  
 ![Onglet en arrière-plan](../../extensibility/ux-guidelines/media/0303-076-backgroundtab.png "0303-076_BackgroundTab")  
  
 **Par défaut d’onglet en arrière-plan**  
  
 Présentation  
  
 `Environment.FileTabBackground`  
  
 Premier plan (texte)  
  
 `Environment.FileTabText`  
  
 Bordure  
  
 `Environment.FileTabBorder`  
  
 Défini sur la même couleur que l’arrière-plan.  
  
 **Placez le curseur**  
  
 ![Onglet en arrière-plan au pointage](../../extensibility/ux-guidelines/media/0303-077-backgroundtabhover.png "0303-077_BackgroundTabHover")  
  
 **Onglet en arrière-plan au pointage**  
  
 Présentation  
  
 `Environment.FileTabHotGradientTop`  
  
 Même si cet arrière-plan n’est pas utilisé dans l’interface utilisateur à thème moderne, il comporte des points et valeurs de dégradés.  
  
 Premier plan (texte)  
  
 `Environment.FileTabHotText`  
  
 Bordure  
  
 `Environment.FileTabHotBorder`  
  
 Défini sur la même couleur que l’arrière-plan.  
  
#### <a name="preview-tab"></a>Onglet d’aperçu  
 L’onglet d’aperçu apparaît du côté droit du canal d’onglet de document quand l’utilisateur clique sur un élément dans la fenêtre Outil de l’Explorateur de solutions. Il sert d’aperçu du document et donne également à l’utilisateur la possibilité de laisser le document ouvert sur le côté gauche du canal d’onglet de document. Une seul onglet d’aperçu peut être ouvert à la fois. Les onglets d’aperçu possèdent deux états, arrière-plan et sélectionné, comme les onglets ouverts, et leur état actif peut être avec ou sans focus.  
  
 ![Ligne rouge d’onglet d’aperçu](../../extensibility/ux-guidelines/media/0303-078-previewtabredline.png "0303-078_PreviewTabRedline")  
  
 Utilisez...  
 à tout endroit où vous créez un aperçu provisoire quand vous voulez faire correspondre un élément à la couleur d’onglet d’aperçu actuelle.  
  
 N’utilisez pas...  
 -   pour tout type de document ou d’onglet qui n’est pas provisoire (en version préliminaire).  
  
- pour toute interface utilisateur que vous ne voulez pas modifier automatiquement si l’interpréteur de commandes comporte une mise à jour de thème.  
  
  **Onglet d’aperçu sélectionné : focus**  
  
  Composant  
  
  Élément  
  
  Nom du jeton : Category.color  
  
  ![Onglet d’aperçu actif](../../extensibility/ux-guidelines/media/0303-079-previewtabfocused.png "0303-079_PreviewTabFocused")  
  
  **Onglet d’aperçu avec focus**  
  
  Présentation  
  
  `Environment.FileTabProvisionalSelectedActive`  
  
  Premier plan (texte)  
  
  `Environment.FileTabProvisionalSelectedActiveForeground`  
  
  Bordure  
  
  `Environment.FileTabProvisionalSelectedActiveBorder`  
  
  Défini sur la même couleur que l’arrière-plan.  
  
  Bordure de document  
  
  `Environment.FileTabProvisionalSelectedActiveBorder`  
  
  **Onglet d’aperçu sélectionné : sans focus**  
  
  Composant  
  
  Élément  
  
  Nom du jeton : Category.color  
  
  ![Onglet d’aperçu inactif](../../extensibility/ux-guidelines/media/0303-080-previewtabunfocused.png "0303-080_PreviewTabUnfocused")  
  
  **Onglet d’aperçu sans focus**  
  
  Présentation  
  
  `Environment.FileTabProvisionalSelectedInactive`  
  
  Premier plan (texte)  
  
  `Environment.FileTabProvisionalSelectedInactiveForeground`  
  
  Bordure  
  
  `Environment.FileTabProvisionalSelectedInactiveBorder`  
  
  Bordure de document  
  
  `Environment.FileTabProvisionalSelectedInactiveBorder`  
  
  **Onglet d’aperçu d’arrière-plan : par défaut**  
  
  Composant  
  
  Élément  
  
  Nom du jeton : Category.color  
  
  ![Onglet d’aperçu d’arrière-plan](../../extensibility/ux-guidelines/media/0303-081-previewbackgroundtab.png "0303-081_PreviewBackgroundTab")  
  
  **Onglet d’arrière-plan onglet d’aperçu**  
  
  Présentation  
  
  `Environment.FileTabProvisionalInactive`  
  
  Premier plan (texte)  
  
  `Environment.FileTabProvisionalInactiveForeground`  
  
  Bordure  
  
  `Environment.FileTabProvisionalInactiveBorder`  
  
  Défini sur la même couleur que l’arrière-plan.  
  
  **Onglet d’aperçu d’arrière-plan : placez le curseur**  
  
  Composant  
  
  Élément  
  
  Nom du jeton : Category.color  
  
  ![Onglet d’aperçu d’arrière-plan au pointage](../../extensibility/ux-guidelines/media/0303-082-previewbackgroundtabhover.png "0303-082_PreviewBackgroundTabHover")  
  
  **Onglet d’arrière-plan onglet d’aperçu au pointage**  
  
  Présentation  
  
  `Environment.FileTabProvisionalHover`  
  
  Premier plan (texte)  
  
  `Environment.FileTabProvisionalHoverForeground`  
  
  Bordure  
  
  `Environment.FileTabProvisionalHoverBorder`  
  
  Défini sur la même couleur que l’arrière-plan.  
  
#### <a name="document-overflow-button"></a>Bouton de dépassement de capacité de document  
 Le bouton de dépassement de capacité de document est présent si un ou plusieurs documents sont ouverts, que l’espace vertical défini dans la configuration actuelle suffise ou non pour loger tous les onglets de document. Le menu déroulant de dépassement de capacité de document, contrôlé par les couleurs **CommandBarMenu** (consultez [Menus](../../misc/shared-colors.md#BKMK_CommandMenus)), présente la liste de tous les documents ouverts, à la fois visibles et masqués, ainsi que le glyphe de dépassement de capacité change selon que tous les documents ouverts sont affichés dans le canal d’onglet.  
  
 ![Ligne rouge de dépassement de capacité](../../extensibility/ux-guidelines/media/0303-083-overflowredline.png "0303-083_OverflowRedline")  
  
 Utilisez...  
 quand vous créez un bouton de dépassement de capacité de document personnalisé.  
  
 N’utilisez pas...  
 -   pour une interface utilisateur qui n’est pas similaire à un bouton de dépassement de capacité.  
  
- pour des boutons de dépassement de capacité de barre de commandes.  
  
  **Default**  
  
  Composant  
  
  Élément  
  
  Nom du jeton : Category.color  
  
  ![Overflow](../../extensibility/ux-guidelines/media/0303-084-overflow.png "0303-084_Overflow")  
  
  **Bouton de dépassement de capacité de document**  
  
  Présentation  
  
  `Environment.DocWellOverflowButtonBackground`  
  
  Premier plan (glyphe)  
  
  `Environment.DocWellOverflowButtonGlyph`  
  
  Bordure  
  
  N/A  
  
  **Placez le curseur**  
  
  Composant  
  
  Élément  
  
  Nom du jeton : Category.color  
  
  ![Dépassement au pointage](../../extensibility/ux-guidelines/media/0303-085-overflowhover.png "0303-085_OverflowHover")  
  
  **Bouton de dépassement de capacité de document au pointage**  
  
  Présentation  
  
  `Environment.DocWellOverflowButtonMouseOverBackground`  
  
  Premier plan (glyphe)  
  
  `Environment.DocWellOverflowButtonMouseOverGlyph`  
  
  Bordure  
  
  `Environment.DocWellOverflowButtonMouseOverBorder`  
  
  **Enfoncé**  
  
  Composant  
  
  Élément  
  
  Nom du jeton : Category.color  
  
  ![Dépassement enfoncé](../../extensibility/ux-guidelines/media/0303-086-overflowpressed.png "0303-086_OverflowPressed")  
  
  **Enfoncé le bouton de dépassement de capacité de document**  
  
  Présentation  
  
  `Environment.DocWellOverflowButtonMouseDownBackground`  
  
  Premier plan (glyphe)  
  
  `Environment.DocWellOverflowButtonMouseDownGlyph`  
  
  Bordure  
  
  `Environment.DocWellOverflowButtonMouseDownBorder`  
  
## <a name="tool-windows"></a>Fenêtres d’outil  
 Il est inutile de répliquer les fenêtres d’outil, car elles sont fournies par l’environnement Visual Studio. Toutefois, vous pouvez décider d’exploiter les couleurs utilisées dans les fenêtres d’outil, afin que votre interface utilisateur apparaisse toujours cohérente avec cette partie de l’environnement Visual Studio.  
  
 ![Ligne rouge de fenêtre outil](../../extensibility/ux-guidelines/media/0303-087-toolwindowredline.png "0303-087_ToolWindowRedline")  
  
 Utilisez...  
 à tout endroit où vous créez une interface utilisateur que vous voulez faire correspondre à des fenêtres d’outil.  
  
 N’utilisez pas...  
 pour toute interface utilisateur que vous ne voulez pas modifier automatiquement si l’interpréteur de commandes comporte une mise à jour de thème.  
  
### <a name="tool-window-frame"></a>Cadre de fenêtre Outil  
 Les fenêtres d’outil dans Visual Studio sont utilisées pour de nombreuses tâches différentes et peuvent exister dans différents états. Si une fenêtre Outil est ouverte, elle peut être affectée à l’un des quatre côtés de la zone de document. Les fenêtres d’outil peuvent également flotter en dehors de l’IDE, ce qui leur permet d’être repositionnées n’importe où sur l’écran de l’utilisateur. Les fenêtres flottantes se trouvent toujours par-dessus l’IDE. Enfin, les fenêtres d’outil peuvent être ancrées comme des fenêtres de document et elles apparaissent sous la forme d’un onglet dans la zone de configuration de document. Les fenêtres d’outil ancrées comme des fenêtres de document sont colorées en partie à l’aide des noms de jeton de fenêtre de document.  
  
 ![Ligne rouge de frame de fenêtre outil](../../extensibility/ux-guidelines/media/0303-088-toolwindowframeredline.png "0303-088_ToolWindowFrameRedline")  
  
 Utilisez...  
 à tout endroit où vous créez une interface utilisateur que vous voulez faire correspondre à des fenêtres d’outil.  
  
 N’utilisez pas...  
 pour toute interface utilisateur que vous ne voulez pas modifier automatiquement si l’interpréteur de commandes comporte une mise à jour de thème.  
  
 **Ancré**  
  
 Composant  
  
 Élément  
  
 Nom du jeton : Category.color  
  
 ![Fenêtre Outil ancrée](../../extensibility/ux-guidelines/media/0303-089-toolwindowdocked.png "0303-089_ToolWindowDocked")  
  
 Présentation  
  
 `Environment.ToolWindowBackground`  
  
 Bordure  
  
 `Environment.ToolWindowBorder`  
  
 **Flottant : focus**  
  
 Composant  
  
 Élément  
  
 Nom du jeton : Category.color  
  
 ![Fenêtre outil Active](../../extensibility/ux-guidelines/media/0303-090-toolwindowfocused.png "0303-090_ToolWindowFocused")  
  
 Présentation  
  
 `Environment.ToolWindowBackground`  
  
 Bordure  
  
 `Environment.MainWindowActiveDefaultBorder`  
  
 **Flottant : sans focus**  
  
 Composant  
  
 Élément  
  
 Nom du jeton : Category.color  
  
 ![Fenêtre outil inactive](../../extensibility/ux-guidelines/media/0303-091-toolwindowunfocused.png "0303-091_ToolWindowUnfocused")  
  
 Présentation  
  
 `Environment.ToolWindowBackground`  
  
 Bordure  
  
 `Environment.MainWindowInactiveBorder`  
  
### <a name="tool-window-title-bar"></a>Barre de titre de fenêtre Outil  
 La bordure de la barre de titre n’est pas une véritable bordure, mais plutôt une ligne épaisse en haut de la barre de titre. Elle n’a pas de nom de jeton pour son état sans focus.  
  
 ![Ligne rouge de barre de titre de fenêtre outil](../../extensibility/ux-guidelines/media/0303-092-toolwindowtitlebarredline.png "0303-092_ToolWindowTitleBarRedline")  
  
 Utilisez...  
 à tout endroit où vous créez une interface utilisateur que vous voulez faire correspondre à des fenêtres d’outil.  
  
 N’utilisez pas...  
 pour toute interface utilisateur que vous ne voulez pas modifier automatiquement si l’interpréteur de commandes comporte une mise à jour de thème.  
  
 **Focus**  
  
 Composant  
  
 Élément  
  
 Nom du jeton : Category.color  
  
 ![Focus de la barre de titre](../../extensibility/ux-guidelines/media/0303-093-titlebarfocused.png "0303-093_TitleBarFocused")  
  
 **Barre de titre avec focus**  
  
 Présentation  
  
 `Environment.TitleBarActiveGradientBegin`  
  
 Même si cet arrière-plan n’est pas utilisé dans l’interface utilisateur à thème moderne, il comporte des points et valeurs de dégradés.  
  
 Premier plan (texte)  
  
 `Environment.TitleBarActiveText`  
  
 Bordure  
  
 `Environment.TitleBarActiveBorder`  
  
 Défini sur la même couleur que l’arrière-plan.  
  
 Faire glisser la poignée  
  
 `Environment.TitleBarDragHandleActive`  
  
 **Inactif**  
  
 Composant  
  
 Élément  
  
 Nom du jeton : Category.color  
  
 ![Barre de titre inactive](../../extensibility/ux-guidelines/media/0303-094-titlebarunfocused.png "0303-094_TitleBarUnfocused")  
  
 **Barre de titre inactive**  
  
 Présentation  
  
 `Environment.TitleBarInactiveGradientBegin`  
  
 Même si cet arrière-plan n’est pas utilisé dans l’interface utilisateur à thème moderne, il comporte des points et valeurs de dégradés.  
  
 Premier plan (texte)  
  
 `Environment.TitleBarInactiveText`  
  
 Bordure  
  
 N/A  
  
 Faire glisser la poignée  
  
 `Environment.TitleBarDragHandle`  
  
#### <a name="title-bar-buttons"></a>Boutons de barre de titre  
 ![Ligne rouge de bouton de barre de titre](../../extensibility/ux-guidelines/media/0303-095-titlebarbuttonredline.png "0303-095_TitleBarButtonRedline")  
  
 Utilisez...  
 pour les boutons qui apparaissent dans l’interface utilisateur et qui utilisent les jetons de couleur des barres de titre de fenêtre Outil.  
  
 N’utilisez pas...  
 -   pour les boutons qui apparaissent à d’autres endroits.  
  
- dans une combinaison arrière-plan/premier plan autre que celle spécifiée.  
  
  **Default**  
  
  Composant  
  
  Élément  
  
  Nom du jeton : Category.color  
  
  ![Bouton actif de la barre de titre](../../extensibility/ux-guidelines/media/0303-096-titlebarbuttonfocused.png "0303-096_TitleBarButtonFocused")  
  
  **Focus**  
  
  Présentation  
  
  N/A  
  
  Premier plan (glyphe)  
  
  `Environment.ToolWindowButtonActiveGlyph`  
  
  Bordure  
  
  N/A  
  
  ![Bouton inactif de la barre de titre](../../extensibility/ux-guidelines/media/0303-097-titlebarbuttonunfocused.png "0303-097_TitleBarButtonUnfocused")  
  
  **Inactif**  
  
  Présentation  
  
  N/A  
  
  Premier plan (glyphe)  
  
  `Environment.ToolWindowButtonInactiveGlyph`  
  
  Bordure  
  
  N/A  
  
  **Placez le curseur**  
  
  Composant  
  
  Élément  
  
  Nom du jeton : Category.color  
  
  ![Bouton de barre de titre actif au pointage](../../extensibility/ux-guidelines/media/0303-098-titlebarbuttonfocusedhover.png "0303-098_TitleBarButtonFocusedHover")  
  
  **Focus**  
  
  Présentation  
  
  `Environment.ToolWindowButtonHoverActive`  
  
  Premier plan (glyphe)  
  
  `Environment.ToolWindowButtonHoverActiveGlyph`  
  
  Bordure  
  
  `Environment.ToolWindowButtonHoverActiveBorder`  
  
  ![Inactif au pointage du bouton de la barre de titre](../../extensibility/ux-guidelines/media/0303-099-titlebarbuttonunfocusedhover.png "0303-099_TitleBarButtonUnfocusedHover")  
  
  **Inactif**  
  
  Présentation  
  
  `Environment.ToolWindowButtonHoverInactive`  
  
  Premier plan (glyphe)  
  
  `Environment.ToolWindowButtonHoverInactiveGlyph`  
  
  Bordure  
  
  `Environment.ToolWindowButtonHoverInactiveBorder`  
  
  **Enfoncé**  
  
  Composant  
  
  Élément  
  
  Nom du jeton : Category.color  
  
  ![Bouton actif et enfoncé la barre de titre](../../extensibility/ux-guidelines/media/0303-100-titlebarbuttonfocusedpressed.png "0303-100_TitleBarButtonFocusedPressed")  
  
  **Focus**  
  
  Présentation  
  
  `Environment.ToolWindowButtonDown`  
  
  Premier plan (glyphe)  
  
  `Environment.ToolWindowButtonDownActiveGlyph`  
  
  Bordure  
  
  `Environment.ToolWindowButtonDownBorder`  
  
  ![Bouton de barre de titre inactif et enfoncé](../../extensibility/ux-guidelines/media/0303-101-titlebarbuttonunfocusedpressed.png "0303-101_TitleBarButtonUnfocusedPressed")  
  
  **Inactif**  
  
  Présentation  
  
  `Environment.ToolWindowButtonDown`  
  
  Premier plan (glyphe)  
  
  `Environment.ToolWindowButtonDownInactiveGlyph`  
  
  Bordure  
  
  `Environment.ToolWindowButtonDownBorder`  
  
### <a name="tool-window-tabs"></a>Onglets de fenêtre Outil  
 ![Ligne rouge d’onglet de fenêtre outil](../../extensibility/ux-guidelines/media/0303-102-toolwindowtabredline.png "0303-102_ToolWindowTabRedline")  
  
 Utilisez...  
 à tout endroit où vous créez une interface utilisateur que vous voulez faire correspondre à des fenêtres d’outil.  
  
 N’utilisez pas...  
 pour toute interface utilisateur que vous ne voulez pas modifier automatiquement si l’interpréteur de commandes comporte une mise à jour de thème.  
  
 **Onglet sélectionné**  
  
 Composant  
  
 Élément  
  
 Nom du jeton : Category.color  
  
 ![Onglet fenêtre outil axé](../../extensibility/ux-guidelines/media/0303-103-toolwindowtabfocused.png "0303-103_ToolWindowTabFocused")  
  
 **Onglet fenêtre outil sélectionné, avec focus**  
  
 Présentation  
  
 `Environment.ToolWindowTabSelectedTab`  
  
 Premier plan (texte)  
  
 `Environment.ToolWindowTabSelectedActiveText`  
  
 Bordure  
  
 `Environment.ToolWindowTabSelectedBorder`  
  
 Défini sur la même couleur que l’arrière-plan.  
  
 Composant  
  
 Élément  
  
 Nom du jeton : Category.color  
  
 ![Onglet de fenêtre outil inactif](../../extensibility/ux-guidelines/media/0303-104-toolwindowtabunfocused.png "0303-104_ToolWindowTabUnfocused")  
  
 **Onglet fenêtre outil sélectionné, sans focus**  
  
 Présentation  
  
 `Environment.ToolWindowTabSelectedTab`  
  
 Premier plan (texte)  
  
 `Environment.ToolWindowTabSelectedText`  
  
 Bordure  
  
 `Environment.ToolWindowTabSelectedBorder`  
  
 Défini sur la même couleur que l’arrière-plan.  
  
 **Onglet en arrière-plan**  
  
 Composant  
  
 Élément  
  
 Nom du jeton : Category.color  
  
 ![Onglet d’arrière-plan de fenêtre outil](../../extensibility/ux-guidelines/media/0303-105-toolwindowbackgroundtab.png "0303-105_ToolWindowBackgroundTab")  
  
 **Onglet de fenêtre outil arrière-plan**  
  
 Présentation  
  
 `Environment.ToolWindowTabGradientBegin`  
  
 Les points de dégradé sont définis sur la même valeur de couleur dans Visual Studio 2013.  
  
 `Environment.ToolWindowTabGradientEnd`  
  
 Les points de dégradé sont définis sur la même valeur de couleur dans Visual Studio 2013.  
  
 Premier plan (texte)  
  
 `Environment.ToolWindowTabText`  
  
 Bordure  
  
 `Environment.ToolWindowTabBorder`  
  
 Composant  
  
 Élément  
  
 Nom du jeton : Category.color  
  
 ![Onglet d’arrière-plan de fenêtre outil au pointage](../../extensibility/ux-guidelines/media/0303-106-toolwindowbackgroundtabhover.png "0303-106_ToolWindowBackgroundTabHover")  
  
 **Onglet de fenêtre outil arrière-plan au pointage**  
  
 Présentation  
  
 `Environment.ToolWindowTabMouseOverBackgroundBegin`  
  
 Les points de dégradé sont définis sur la même valeur de couleur dans Visual Studio 2013.  
  
 `Environment.ToolWindowTabMouseOverBackgroundEnd`  
  
 Les points de dégradé sont définis sur la même valeur de couleur dans Visual Studio 2013.  
  
 Premier plan (texte)  
  
 `Environment.ToolWindowTabMouseOverText`  
  
 Bordure  
  
 `Environment.ToolWindowTabMouseOverBorder`  
  
 Défini sur la même couleur que l’arrière-plan.  
  
### <a name="auto-hide-tabs"></a>Onglets à masquage automatique  
 ![Auto&#45;ligne rouge de masquer](../../extensibility/ux-guidelines/media/0303-107-autohideredline.png "0303-107_AutoHideRedline")  
  
 Utilisez...  
 à tout endroit où vous créez une interface utilisateur que vous voulez faire correspondre à des onglets de fenêtre Outil masqués automatiquement.  
  
 N’utilisez pas...  
 pour toute interface utilisateur que vous ne voulez pas modifier automatiquement si l’interpréteur de commandes comporte une mise à jour de thème.  
  
 **Default**  
  
 Composant  
  
 Élément  
  
 Nom du jeton : Category.color  
  
 ![Auto&#45;masquer l’onglet](../../extensibility/ux-guidelines/media/0303-108-autohidetab.png "0303-108_AutoHideTab")  
  
 **Onglet de masquage automatique par défaut**  
  
 Présentation  
  
 `Environment.AutoHideTabBackgroundBegin`  
  
 Même si cet arrière-plan n’est pas utilisé dans l’interface utilisateur à thème moderne, il comporte des points et valeurs de dégradés.  
  
 Premier plan (texte)  
  
 `Environment.AutoHideTabText`  
  
 Bordure  
  
 `Environment.AutoHideTabBorder`  
  
 **Placez le curseur**  
  
 Composant  
  
 Élément  
  
 Nom du jeton : Category.color  
  
 ![Auto&#45;masquer l’onglet au pointage](../../extensibility/ux-guidelines/media/0303-109-autohidetabhover.png "0303-109_AutoHideTabHover")  
  
 **Onglet de masquage automatique au pointage**  
  
 Présentation  
  
 `Environment.AutoHideTabMouseOverBackgroundBegin`  
  
 Même si cet arrière-plan n’est pas utilisé dans l’interface utilisateur à thème moderne, il comporte des points et valeurs de dégradés.  
  
 Premier plan (texte)  
  
 `Environment.AutoHideTabMouseOverText`  
  
 Bordure  
  
 `Environment.AutoHideTabMouseOverBorder`  
  
## <a name="common-shared-controls"></a>Contrôles partagés communs  
 Quand vous utilisez une barre de commandes Visual Studio standard dans votre composant, vous avez accès à des contrôles d’interpréteur de commandes stylisés et vous ne devez pas remodéliser ces contrôles communs. Toutefois, si vous avez besoin de créer une barre de commandes personnalisée, vous pouvez avoir besoin de générer des contrôles personnalisés également. Dans ce cas, assurez-vous d’utiliser des noms de jeton corrects pour chacun des contrôles suivants afin que votre interface utilisateur soit cohérente avec le reste de Visual Studio.  
  
### <a name="search-box"></a>Zone de recherche  
 Si possible, utilisez le contrôle de recherche commun fourni par l’environnement Visual Studio. Les couleurs de zone de recherche se trouvent dans la catégorie « SearchControl » du fichier **ShellColors.pkgdef** qui contient les noms de jeton du champ d’entrée, du bouton d’action, du bouton de liste déroulante et du menu déroulant.  
  
 Une zone de recherche peut être dans plusieurs états, dont certains s’excluent mutuellement :  
  
- Les états « avec focus » ou « sans focus » font référence à la présence ou non du curseur dans la zone de texte.  
  
- Les états « actif » ou « inactif » font référence à l’éventuel entrée par l’utilisateur d’une requête de recherche dans la zone de texte.  
  
- L’état « pointage » signifie que l’utilisateur a placé le curseur de la souris au-dessus de la zone de recherche (cet état remplace tous les autres états).  
  
- L’état « désactivé » signifie que la fonctionnalité de recherche est désactivée pour le contexte actuel.  
  
  ![Ligne rouge de zone de recherche](../../extensibility/ux-guidelines/media/0303-110-searchboxredline.png "0303-110_SearchBoxRedline")  
  
  Utilisez...  
  quand vous concevez une zone de recherche personnalisée.  
  
  N’utilisez pas...  
  -   pour tout élément qui n’est pas une zone de recherche.  
  
- pour tout élément que vous ne voulez pas toujours faire correspondre à l’interface utilisateur de la zone de recherche.  
  
  **Focus**  
  
  Composant  
  
  Élément  
  
  Nom du jeton : Category.color  
  
  ![Champ d’entrée de recherche actif](../../extensibility/ux-guidelines/media/0303-111-searchinputfieldfocused.png "0303-111_SearchInputFieldFocused")  
  
  **Champ d’entrée**  
  
  Présentation  
  
  `SearchControl.FocusedBackground`  
  
  Premier plan (texte)  
  
  `SearchControl.FocusedBackground`  
  
  Bordure  
  
  `SearchControl.FocusedBorder`  
  
  Séparateur  
  
  `SearchControl.FocusedDropDownSeparator`  
  
  ![Bouton d’action de recherche actif](../../extensibility/ux-guidelines/media/0303-112-searchactionbuttonfocused.png "0303-112_SearchActionButtonFocused")  
  
  **Bouton d’action**  
  
  Présentation  
  
  Aucun.  
  
  Premier plan (glyphe Rechercher)  
  
  `SearchControl.SearchGlyph`  
  
  Premier plan (glyphe Arrêter)  
  
  `SearchControl.StopGlyph`  
  
  Premier plan (glyphe Effacer)  
  
  `SearchControl.ClearGlyph`  
  
  Bordure  
  
  N/A  
  
  ![Liste de recherche&#45;vers le bas du bouton actif](../../extensibility/ux-guidelines/media/0303-113-searchdropdownbuttonfocused.png "0303-113_SearchDropdownButtonFocused")  
  
  **Bouton de liste déroulante**  
  
  Présentation  
  
  `SearchControl.FocusedDropDownButton`  
  
  Premier plan (glyphe)  
  
  `SearchControl.FocusedDropDownButtonGlyph`  
  
  Bordure  
  
  `SearchControl.FocusedDropDownButtonBorder`  
  
  **Inactif**  
  
  Composant  
  
  Élément  
  
  Nom du jeton : Category.color  
  
  ![Champ d’entrée de recherche inactif](../../extensibility/ux-guidelines/media/0303-114-searchinputfieldunfocused.png "0303-114_SearchInputFieldUnfocused")  
  
  **Champ d’entrée actif**  
  
  Présentation  
  
  `SearchControl.SearchActiveBackground`  
  
  Premier plan (texte)  
  
  `SearchControl.SearchActiveBackground`  
  
  Bordure  
  
  `SearchControl.UnfocusedBorder`  
  
  Séparateur  
  
  `SearchControl.DropDownSeparator`  
  
  ![Champ d’entrée de recherche inactif](../../extensibility/ux-guidelines/media/0303-114-1-searchinputfieldunfocusedinactive.png "0303-114-1_SearchInputFieldUnfocusedInactive")  
  
  **Champ d’entrée inactif**  
  
  Présentation  
  
  `SearchControl.Unfocused`  
  
  Premier plan (texte)  
  
  `SearchControl.Unfocused`  
  
  Bordure  
  
  `SearchControl.UnfocusedBorder`  
  
  Séparateur  
  
  `SearchControl.DropDownSeparator`  
  
  ![Bouton d’action de recherche inactif](../../extensibility/ux-guidelines/media/0303-115-searchactionbuttonunfocused.png "0303-115_SearchActionButtonUnfocused")  
  
  **Bouton d’action**  
  
  Présentation  
  
  N/A  
  
  Premier plan (glyphe Rechercher)  
  
  `SearchControl.SearchGlyph`  
  
  Premier plan (glyphe Arrêter)  
  
  `SearchControl.StopGlyph`  
  
  Premier plan (glyphe Effacer)  
  
  `SearchControl.ClearGlyph`  
  
  Bordure  
  
  N/A  
  
  ![Liste de recherche&#45;vers le bas du bouton inactif](../../extensibility/ux-guidelines/media/0303-116-searchdropdownbuttonunfocused.png "0303-116_SearchDropdownButtonUnfocused")  
  
  **Bouton de liste déroulante**  
  
  Présentation  
  
  `SearchControl.UnfocusedDropDownButton`  
  
  Premier plan (glyphe)  
  
  `SearchControl.UnfocusedDropDownButtonGlyph`  
  
  Bordure  
  
  `SearchControl.UnfocusedDropDownButtonBorder`  
  
  **Enfoncé**  
  
  Composant  
  
  Élément  
  
  Nom du jeton : Category.color  
  
  ![Bouton d’action de recherche enfoncé](../../extensibility/ux-guidelines/media/0303-116-1-searchactionbuttonpressed.png "0303-116-1_SearchActionButtonPressed")  
  
  **Bouton d’action**  
  
  Présentation  
  
  `SearchControl.ActionButtonMouseDown`  
  
  Premier plan (glyphe)  
  
  `SearchControl.ActionButtonMouseDownGlyph`  
  
  Bordure  
  
  `SearchControl.ActionButtonMouseDownBorder`  
  
  ![Liste de recherche&#45;le bouton enfoncé](../../extensibility/ux-guidelines/media/0303-116-2-searchdropdownbuttonpressed.png "0303-116-2_SearchDropdownButtonPressed")  
  
  **Bouton de liste déroulante**  
  
  Présentation  
  
  `SearchControl.MouseDownDropDownButton`  
  
  Premier plan (glyphe)  
  
  `SearchControl.MouseDownDropDownButtonGlyph`  
  
  Bordure  
  
  `SearchControl.MouseDownDropDownButtonBorder`  
  
  **Texte mis en surbrillance (uniquement)**  
  
  Composant  
  
  Élément  
  
  Nom du jeton : Category.color  
  
  ![Mise en surbrillance du champ d’entrée de recherche](../../extensibility/ux-guidelines/media/0303-120-searchinputfieldhighlight.png "0303-120_SearchInputFieldHighlight")  
  
  **Champ d’entrée avec le texte mis en surbrillance**  
  
  Présentation  
  
  `SearchControl.Selection`  
  
  Premier plan (texte)  
  
  `SearchControl.FocusedBackground`  
  
  Bordure  
  
  Aucun.  
  
  Séparateur  
  
  `SearchControl.FocusedDropDownSeparator`  
  
  **Désactivé**  
  
  Composant  
  
  Élément  
  
  Nom du jeton : Category.color  
  
  ![Champ d’entrée de recherche désactivé](../../extensibility/ux-guidelines/media/0303-121-searchinputfielddisabled.png "0303-121_SearchInputFieldDisabled")  
  
  **Champ d’entrée**  
  
  Présentation  
  
  `SearchControl.Disabled`  
  
  Premier plan (texte)  
  
  `SearchControl.Disabled`  
  
  Bordure  
  
  `SearchControl.DisabledBorder`  
  
  Séparateur  
  
  `SearchControl.DropDownSeparator`  
  
  ![Bouton d’action de recherche désactivé](../../extensibility/ux-guidelines/media/0303-122-searchactionbuttondisabled.png "0303-122_SearchActionButtonDisabled")  
  
  **Bouton d’action**  
  
  Présentation  
  
  Aucun.  
  
  Premier plan (glyphe)  
  
  `SearchControl.ActionButtonDisabledGlyph`  
  
  Bordure  
  
  Aucun.  
  
  ![Liste de recherche&#45;le bouton désactivé](../../extensibility/ux-guidelines/media/0303-123-searchdropdownbuttondisabled.png "0303-123_SearchDropdownButtonDisabled")  
  
  **Bouton de liste déroulante**  
  
  Présentation  
  
  Aucun.  
  
  Premier plan (glyphe)  
  
  `SearchControl.DisabledDownButtonGlyph`  
  
  Bordure  
  
  Aucun.  
  
#### <a name="search-drop-down-lists"></a>Listes déroulantes de recherche  
 Le menu déroulant de la zone de recherche est susceptible d’être légèrement plus complexe que les autres menus déroulants dans Visual Studio. Les sections « options de recherche » et « recherches suggérées » peuvent apparaître seules ou ensemble dans le menu et chacune possède une couleur distincte. Une ligne sépare également ces deux sections quand elles apparaissent ensemble et une bordure entoure l’ensemble du menu déroulant.  
  
 ![Liste de recherche&#45;vers le bas ligne rouge](../../extensibility/ux-guidelines/media/0303-124-searchdropdownredline.png "0303-124_SearchDropdownRedline")  
  
 Utilisez...  
 -   quand vous créez une liste déroulante de recherche personnalisée.  
  
- les noms de jeton corrects pour les composants de liste corrects.  
  
  N’utilisez pas...  
  -   pour les listes déroulantes qui apparaissent dans d’autres contextes.  
  
- dans une combinaison arrière-plan/premier plan autre que celle spécifiée.  
  
  **Par défaut (aucun autre état)**  
  
  Élément  
  
  Nom du jeton : Category.color  
  
  Bordure  
  
  `SearchControl.PopupBorder`  
  
  Séparateur  
  
  `SearchControl.PopupSectionHeaderSeparator`  
  
  Ombre  
  
  `Environment.DropShadowBackground`  
  
  **Default**  
  
  Composant  
  
  Élément  
  
  Nom du jeton : Category.color  
  
  ![Recherche suggérée](../../extensibility/ux-guidelines/media/0303-125-searchsuggested.png "0303-125_SearchSuggested")  
  
  **Recherches suggérées**  
  
  Présentation  
  
  `SearchControl.PopupItemsListBackgroundGradientBegin`  
  
  Même si cet arrière-plan n’est pas utilisé dans l’interface utilisateur à thème moderne, il comporte des points et valeurs de dégradés.  
  
  Premier plan (texte)  
  
  `SearchControl.PopupItemText`  
  
  ![Case à cocher Rechercher](../../extensibility/ux-guidelines/media/0303-126-searchcheckbox.png "0303-126_SearchCheckbox")  
  
  **Options de recherche (case à cocher)**  
  
  ![Options de recherche](../../extensibility/ux-guidelines/media/0303-127-searchoptions.png "0303-127_SearchOptions")  
  
  **Options de recherche (lien)**  
  
  Présentation  
  
  `SearchControl.PopupSectionBackgroundGradientBegin`  
  
  Même si cet arrière-plan n’est pas utilisé dans l’interface utilisateur à thème moderne, il comporte des points et valeurs de dégradés.  
  
  Premier plan (texte de case à cocher)  
  
  `SearchControl.PopupCheckboxText`  
  
  Premier plan (texte de lien)  
  
  `SearchControl.PopupButtonText`  
  
  Arrière-plan d’en-tête  
  
  `SearchControl.PopupSectionHeaderGradientBegin`  
  
  Même si cet arrière-plan n’est pas utilisé dans l’interface utilisateur à thème moderne, il comporte des points et valeurs de dégradés.  
  
  Premier plan (texte d’en-tête)  
  
  `SearchControl.PopupSectionHeaderText`  
  
  **Placez le curseur**  
  
  Composant  
  
  Élément  
  
  Nom du jeton : Category.color  
  
  ![Recherche suggérée au pointage](../../extensibility/ux-guidelines/media/0303-128-searchsuggestedhover.png "0303-128_SearchSuggestedHover")  
  
  **Recherches suggérées**  
  
  Présentation  
  
  `SearchControl.PopupControlMouseOverBackgroundGradientBegin`  
  
  Même si cet arrière-plan n’est pas utilisé dans l’interface utilisateur à thème moderne, il comporte des points et valeurs de dégradés.  
  
  Premier plan (texte)  
  
  `SearchControl.PopupMouseOverItemText`  
  
  Bordure  
  
  `SearchControl.PopupControlMouseOverBorder`  
  
  ![Case à cocher de recherche au pointage](../../extensibility/ux-guidelines/media/0303-129-searchcheckboxhover.png "0303-129_SearchCheckboxHover")  
  
  **Recherches suggérées (case à cocher)**  
  
  ![Options de survol de recherche](../../extensibility/ux-guidelines/media/0303-130-searchoptionshover.png "0303-130_SearchOptionsHover")  
  
  **Options de recherche**  
  
  Présentation  
  
  `SearchControl.PopupControlMouseOverBackgroundGradientBegin`  
  
  Même si cet arrière-plan n’est pas utilisé dans l’interface utilisateur à thème moderne, il comporte des points et valeurs de dégradés.  
  
  Premier plan (texte de case à cocher)  
  
  `SearchControl.PopupCheckboxMouseDownText`  
  
  Premier plan (texte de lien)  
  
  `SearchControl.PopupButtonMouseDownText`  
  
  Bordure  
  
  `SearchControl.PopupControlMouseOverBorder`  
  
  **Enfoncé**  
  
  Composant  
  
  Élément  
  
  Nom du jeton : Category.color  
  
  ![Recherche suggérée enfoncée](../../extensibility/ux-guidelines/media/0303-131-searchsuggestedpressed.png "0303-131_SearchSuggestedPressed")  
  
  **Recherches suggérées (case à cocher)**  
  
  ![Rechercher les options enfoncées](../../extensibility/ux-guidelines/media/0303-132-searchoptionspressed.png "0303-132_SearchOptionsPressed")  
  
  **Options de recherche**  
  
  Arrière-plan de case à cocher  
  
  `SearchControl.PopupControlMouseDownBackgroundGradientBegin`  
  
  Même si cet arrière-plan n’est pas utilisé dans l’interface utilisateur à thème moderne, il comporte des points et valeurs de dégradés.  
  
  `SearchControl.PopupControlMouseDownBackgroundGradientEnd`  
  
  Même si cet arrière-plan n’est pas utilisé dans l’interface utilisateur à thème moderne, il comporte des points et valeurs de dégradés.  
  
  Premier plan (texte de case à cocher)  
  
  `SearchControl.PopupCheckboxMouseDownText`  
  
  Arrière-plan de lien  
  
  `SearchControl.PopupButtonMouseDownBackgroundGradientBegin`  
  
  Même si cet arrière-plan n’est pas utilisé dans l’interface utilisateur à thème moderne, il comporte des points et valeurs de dégradés.  
  
  Premier plan (texte de lien)  
  
  `SearchControl.PopupButtonMouseDownText`  
  
### <a name="hyperlink"></a>Lien hypertexte  
 Le lien hypertexte est un contrôle qui n’a pas de paire premier plan/arrière-plan. Dans tous les cas, utilisez la couleur du lien hypertexte de premier plan, qui s’affiche correctement sur les arrière-plans foncés, gris et blancs. Si vous n’utilisez pas le jeton de couleur du contrôle de lien hypertexte, la couleur système par défaut pour l’état « appuyé » apparaît, laquelle clignote en rouge. Ce clignotement rouge indique le contrôle n’utilise pas le jeton de couleur d’environnement approprié.  
  
 ![Ligne rouge de lien hypertexte](../../extensibility/ux-guidelines/media/0303-133-hyperlinkredline.png "0303-133_HyperlinkRedline")  
  
 Utilisez...  
 quand vous avez besoin de créer un lien hypertexte personnalisé.  
  
 N’utilisez pas...  
 pour tout élément qui n’est pas un lien hypertexte.  
  
 **Default**  
  
 Composant  
  
 Élément  
  
 Nom du jeton : Category.color  
  
 ![Par défaut de lien hypertexte](../../extensibility/ux-guidelines/media/0303-134-hyperlink.png "0303-134_Hyperlink")  
  
 Premier plan (texte)  
  
 `Environment.PanelHyperlink`  
  
 **Placez le curseur**  
  
 Composant  
  
 Élément  
  
 Nom du jeton : Category.color  
  
 ![Lien hypertexte au pointage](../../extensibility/ux-guidelines/media/0303-135-hyperlinkhover.png "0303-135_HyperlinkHover")  
  
 Premier plan (texte)  
  
 `Environment.PanelHyperlinkHover`  
  
 **Enfoncé**  
  
 Composant  
  
 Élément  
  
 Nom du jeton : Category.color  
  
 ![Lien hypertexte enfoncé](../../extensibility/ux-guidelines/media/0303-136-hyperlinkpressed.png "0303-136_HyperlinkPressed")  
  
 Premier plan (texte)  
  
 `Environment.PanelHyperlinkPressed`  
  
 **Désactivé**  
  
 Composant  
  
 Élément  
  
 Nom du jeton : Category.color  
  
 ![Lien hypertexte désactivé](../../extensibility/ux-guidelines/media/0303-137-hyperlinkdisabled.png "0303-137_HyperlinkDisabled")  
  
 Premier plan (texte)  
  
 `Environment.PanelHyperlinkDisabled`  
  
### <a name="infobar"></a>Barre d'informations  
 Les barres d’informations sont utilisées pour fournir plus d’informations sur un contexte donné et apparaissent toujours en haut d’une fenêtre de document ou d’outil.  
  
 ![Ligne rouge de barre d’informations](../../extensibility/ux-guidelines/media/0303-138-infobarredline.png "0303-138_InfobarRedline")  
  
 Utilisez...  
 quand vous créez des barres d’informations personnalisées.  
  
 N’utilisez pas...  
 pour les éléments d’interface utilisateur non similaires à une barre d’informations.  
  
 Composant  
  
 Élément  
  
 Nom du jeton : Category.color  
  
 ![Barre d’informations](../../extensibility/ux-guidelines/media/0303-139-infobar.png "0303-139_Infobar")  
  
 **Barre d’informations**  
  
 Présentation  
  
 `Environment.InfoBackground`  
  
 Premier plan (texte)  
  
 `Environment.InfoText`  
  
 Bordure  
  
 `Environment.ToolWindowBorder`  
  
### <a name="scroll-bar"></a>Barre de défilement  
 Les barres de défilement sont stylisées par l’environnement Visual Studio et aucun thème ne doit leur être appliqué. Toutefois, vous pouvez décider que vous souhaitez exploiter les couleurs utilisées dans les barres de défilement afin que votre interface utilisateur apparaisse toujours cohérente avec cette partie de l’environnement Visual Studio.  
  
 ![Ligne rouge de barre de défilement](../../extensibility/ux-guidelines/media/0303-140-scrollbarredline.png "0303-140_ScrollbarRedline")  
  
 Utilisez...  
 quand vous créez une interface utilisateur que vous voulez faire correspondre aux barres de défilement Visual Studio.  
  
 N’utilisez pas...  
 pour tout élément ce que vous ne voulez pas toujours faire correspondre à l’interface utilisateur des barres de défilement.  
  
 **Default**  
  
 Composant  
  
 Élément  
  
 Nom du jeton : Category.color  
  
 ![Barre de défilement](../../extensibility/ux-guidelines/media/0303-141-scrollbar.png "0303-141_Scrollbar")  
  
 **Barre de défilement**  
  
 Scrollbar  
  
 `Environment.ScrollBarBackground`  
  
 Premier plan (curseur de défilement)  
  
 `Environment.ScrollBarThumbBackground`  
  
 ![Flèche de barre de défilement](../../extensibility/ux-guidelines/media/0303-142-scrollbararrow.png "0303-142_ScrollbarArrow")  
  
 **Flèche de défilement**  
  
 Présentation  
  
 `Environment.ScrollBarArrowBackground`  
  
 Défini sur la même couleur que la barre de défilement.  
  
 Premier plan (glyphe)  
  
 `Environment.ScrollBarArrowGlyph`  
  
 **Placez le curseur**  
  
 Composant  
  
 Élément  
  
 Nom du jeton : Category.color  
  
 ![Barre de défilement au pointage](../../extensibility/ux-guidelines/media/0303-143-scrollbarhover.png "0303-143_ScrollbarHover")  
  
 **Barre de défilement**  
  
 Scrollbar  
  
 `Environment.ScrollBarBackground`  
  
 Premier plan (curseur de défilement)  
  
 `Environment.ScrollBarThumbMouseOverBackground`  
  
 ![Flèche de survol de barre de défilement](../../extensibility/ux-guidelines/media/0303-144-scrollbararrowhover.png "0303-144_ScrollbarArrowHover")  
  
 **Flèche de défilement**  
  
 Présentation  
  
 `Environment.ScrollBarArrowMouseOverBackground`  
  
 Défini sur la même couleur que la barre de défilement.  
  
 Premier plan (glyphe)  
  
 `Environment.ScrollBarArrowGlyphMouseOver`  
  
 **Enfoncé**  
  
 Composant  
  
 Élément  
  
 Nom du jeton : Category.color  
  
 ![Barre de défilement enfoncée](../../extensibility/ux-guidelines/media/0303-145-scrollbarpressed.png "0303-145_ScrollbarPressed")  
  
 **Barre de défilement**  
  
 Scrollbar  
  
 `Environment.ScrollBarBackground`  
  
 Premier plan (curseur de défilement)  
  
 `Environment.ScrollBarThumbPressedBackground`  
  
 ![Appuyée de flèche de barre de défilement](../../extensibility/ux-guidelines/media/0303-146-scrollbararrowpressed.png "0303-146_ScrollbarArrowPressed")  
  
 **Flèche de défilement**  
  
 Présentation  
  
 `Environment.ScrollBarArrowPressedBackground`  
  
 Défini sur la même couleur que la barre de défilement.  
  
 Premier plan (glyphe)  
  
 `Environment.ScrollBarArrowGlyphPressed`  
  
###  <a name="BKMK_TreeView"></a> Vue d’arborescence  
 Plusieurs fenêtres d’outil, notamment l’Explorateur de solutions, l’Explorateur de serveurs et l’Affichage de classes, implémentent un schéma d’organisation hiérarchique dont les couleurs sont contrôlées par les noms de couleur de la catégorie TreeView. Tous les éléments d’une arborescence ont des couleurs d’arrière-plan et de texte. Les éléments qui possèdent des éléments enfants imbriqués ont également des glyphes qui indiquent si l’élément est développé ou réduit.  
  
 ![Ligne rouge d’arborescence](../../extensibility/ux-guidelines/media/0303-147-treeviewredline.png "0303-147_TreeViewRedline")  
  
 Utilisez...  
 à tout endroit où vous avez besoin d’implémenter un affichage d’organisation hiérarchique.  
  
 N’utilisez pas...  
 -   pour tout élément qui n’est pas similaire à une arborescence.  
  
- dans une combinaison arrière-plan/premier plan autre que celle spécifiée.  
  
  **Default**  
  
  Composant  
  
  Élément  
  
  Nom du jeton : Category.color  
  
  ![Vue arborescente](../../extensibility/ux-guidelines/media/0303-148-treeview.png "0303-148_TreeView")  
  
  Présentation  
  
  `TreeView.Background`  
  
  Premier plan (texte)  
  
  `TreeView.Background`  
  
  Premier plan (glyphe)  
  
  `TreeView.Glyph`  
  
  Bordure  
  
  Aucun.  
  
  **Placez le curseur**  
  
  Composant  
  
  Élément  
  
  Nom du jeton : Category.color  
  
  ![Arborescence au pointage](../../extensibility/ux-guidelines/media/0303-149-treeviewhover.png "0303-149_TreeViewHover")  
  
  Présentation  
  
  `TreeView.Background`  
  
  Premier plan (texte)  
  
  `TreeView.Background`  
  
  Premier plan (glyphe)  
  
  `TreeView.GlyphMouseOver`  
  
  Bordure  
  
  Aucun.  
  
  **Faites glisser**  
  
  Composant  
  
  Élément  
  
  Nom du jeton : Category.color  
  
  ![Glissement d’arborescence](../../extensibility/ux-guidelines/media/0303-150-treeviewdragover.png "0303-150_TreeViewDragOver")  
  
  Présentation  
  
  `TreeView.DragOverItem`  
  
  Premier plan (texte)  
  
  `TreeView.DragOverItem`  
  
  Premier plan (glyphe)  
  
  `TreeView.DragOverItemGlyph`  
  
  Bordure  
  
  Aucun.  
  
  **sélectionné**  
  
  Composant  
  
  Élément  
  
  Nom du jeton : Category.color  
  
  ![Arborescence concentré](../../extensibility/ux-guidelines/media/0303-151-treeviewfocused.png "0303-151_TreeViewFocused")  
  
  **Focus**  
  
  Présentation  
  
  `TreeView.SelectedItemActive`  
  
  Premier plan (texte)  
  
  `TreeView.SelectedItemActive`  
  
  Premier plan (glyphe)  
  
  `TreeView.SelectedItemActiveGlyph`  
  
  Bordure  
  
  `TreeView.FocusVisualBorder`  
  
  ![Arborescence inactive](../../extensibility/ux-guidelines/media/0303-152-treeviewunfocused.png "0303-152_TreeViewUnfocused")  
  
  **Inactif**  
  
  Présentation  
  
  `TreeView.SelectedItemInactive`  
  
  Premier plan (texte)  
  
  `TreeView.SelectedItemInactive`  
  
  Premier plan (glyphe)  
  
  `TreeView.SelectedItemInactiveGlyph`  
  
  Bordure  
  
  Aucun.  
  
  **Pointage sélectionné**  
  
  Composant  
  
  Élément  
  
  Nom du jeton : Category.color  
  
  ![Arborescence actif au pointage](../../extensibility/ux-guidelines/media/0303-153-treeviewfocusedhover.png "0303-153_TreeViewFocusedHover")  
  
  **Focus**  
  
  Présentation  
  
  `TreeView.SelectedItemActive`  
  
  Premier plan (texte)  
  
  `TreeView.SelectedItemActive`  
  
  Premier plan (glyphe)  
  
  `TreeView.SelectedItemActiveGlyphMouseOver`  
  
  Bordure  
  
  Aucun`TreeView.FocusVisualBorder`  
  
  ![Arborescence inactive au pointage](../../extensibility/ux-guidelines/media/0303-154-treeviewunfocusedhover.png "0303-154_TreeViewUnfocusedHover")  
  
  **Inactif**  
  
  Présentation  
  
  `TreeView.SelectedItemInactive`  
  
  Premier plan (texte)  
  
  `TreeView.SelectedItemInactive`  
  
  Premier plan (glyphe)  
  
  `TreeView.SelectedItemActiveGlyphMouseOver`  
  
  Bordure  
  
  Aucun.  
  
### <a name="button-controls"></a>Contrôles boutons  
 ![Ligne rouge de contrôle de bouton](../../extensibility/ux-guidelines/media/0303-155-buttoncontrolredline.png "0303-155_ButtonControlRedline")  
  
 Utilisez...  
 pour les boutons situés dans la zone de configuration de document que vous voulez intégrer aux thèmes Visual Studio (Thème clair, foncé, bleu ou système à contraste élevé).  
  
 N’utilisez pas...  
 pour les boutons affichés sur un arrière-plan personnalisé qui ne fait pas partie d’un thème Visual Studio.  
  
 **Default**  
  
 Composant  
  
 Élément  
  
 Nom du jeton : Category.color  
  
 ![Bouton](../../extensibility/ux-guidelines/media/0303-156-button.png "0303-156_Button")  
  
 Bouton  
  
 `CommonControls.Button`  
  
 Bordure de bouton  
  
 `CommonControls.ButtonBorder`  
  
 **Désactivé**  
  
 Composant  
  
 Élément  
  
 Nom du jeton : Category.color  
  
 ![Bouton désactivé](../../extensibility/ux-guidelines/media/0303-157-buttondisabled.png "0303-157_ButtonDisabled")  
  
 Bouton  
  
 `CommonControls.ButtonDisabled`  
  
 Bordure de bouton  
  
 `CommonControls.ButtonBorderDisabled`  
  
 **Placez le curseur**  
  
 Composant  
  
 Élément  
  
 Nom du jeton : Category.color  
  
 ![Bouton au pointage](../../extensibility/ux-guidelines/media/0303-158-buttonhover.png "0303-158_ButtonHover")  
  
 Bouton  
  
 `CommonControls.ButtonHover`  
  
 Bordure de bouton  
  
 `CommonControls.ButtonBorderHover`  
  
 **Enfoncé**  
  
 Composant  
  
 Élément  
  
 Nom du jeton : Category.color  
  
 ![Bouton enfoncé](../../extensibility/ux-guidelines/media/0303-159-buttonpressed.png "0303-159_ButtonPressed")  
  
 Bouton  
  
 `CommonControls.ButtonPressed`  
  
 Bordure de bouton  
  
 `CommonControls.ButtonBorderPressed`  
  
 **Focus**  
  
 Composant  
  
 Élément  
  
 Nom du jeton : Category.color  
  
 ![Bouton actif](../../extensibility/ux-guidelines/media/0303-160-buttonfocused.png "0303-160_ButtonFocused")  
  
 Bouton  
  
 `CommonControls.ButtonFocused`  
  
 Bordure de bouton  
  
 `CommonControls.ButtonBorderFocused`  
  
### <a name="check-box-controls"></a>Contrôles de case à cocher  
 ![Ligne rouge de case à cocher](../../extensibility/ux-guidelines/media/0303-161-checkboxredline.png "0303-161_CheckboxRedline")  
  
 Utilisez...  
 pour les contrôles de case à cocher contenus dans la zone de configuration de document.  
  
 N’utilisez pas...  
 pour toute interface utilisateur qui n’est pas un contrôle de case à cocher.  
  
 **Default**  
  
 Composant  
  
 Élément  
  
 Nom du jeton : Category.color  
  
 ![Case à cocher](../../extensibility/ux-guidelines/media/0303-162-checkbox.png "0303-162_Checkbox")  
  
 Présentation  
  
 `CommonControls.CheckBoxBackground`  
  
 Bordure  
  
 `CommonControls.CheckBoxBorder`  
  
 Texte  
  
 `CommonControls.CheckBoxText`  
  
 Glyphe  
  
 `CommonControls.CheckBoxGlyph`  
  
 **Désactivé**  
  
 Composant  
  
 Élément  
  
 Nom du jeton : Category.color  
  
 ![Case à cocher désactivée](../../extensibility/ux-guidelines/media/0303-163-checkboxdisabled.png "0303-163_CheckboxDisabled")  
  
 Présentation  
  
 `CommonControls.CheckBoxBackgroundDisabled`  
  
 Bordure  
  
 `CommonControls.CheckBoxBorderDisabled`  
  
 Texte  
  
 `CommonControls.CheckBoxTextDisabled`  
  
 Glyphe  
  
 `CommonControls.CheckBoxGlyphDisabled`  
  
 **Placez le curseur**  
  
 Composant  
  
 Élément  
  
 Nom du jeton : Category.color  
  
 ![Case à cocher au pointage](../../extensibility/ux-guidelines/media/0303-164-checkboxhover.png "0303-164_CheckboxHover")  
  
 Présentation  
  
 `CommonControls.CheckBoxBackgroundHover`  
  
 Bordure  
  
 `CommonControls.CheckBoxBorderHover`  
  
 Texte  
  
 `CommonControls.CheckBoxTextHover`  
  
 Glyphe  
  
 `CommonControls.CheckBoxGlyphHover`  
  
 **Enfoncé**  
  
 Composant  
  
 Élément  
  
 Nom du jeton : Category.color  
  
 ![Case à cocher enfoncée](../../extensibility/ux-guidelines/media/0303-165-checkboxpressed.png "0303-165_CheckboxPressed")  
  
 Présentation  
  
 `CommonControls.CheckBoxBackgroundPressed`  
  
 Bordure  
  
 `CommonControls.CheckBoxBorderPressed`  
  
 Texte  
  
 `CommonControls.CheckBoxTextPressed`  
  
 Glyphe  
  
 `CommonControls.CheckBoxGlyphPressed`  
  
 **Focus**  
  
 Composant  
  
 Élément  
  
 Nom du jeton : Category.color  
  
 ![Case à cocher active](../../extensibility/ux-guidelines/media/0303-166-checkboxfocused.png "0303-166_CheckboxFocused")  
  
 Présentation  
  
 `CommonControls.CheckBoxBackgroundFocused`  
  
 Bordure  
  
 `CommonControls.CheckBoxBorderFocused`  
  
 Texte  
  
 `CommonControls.CheckBoxTextFocused`  
  
 Glyphe  
  
 `CommonControls.CheckBoxGlyphFocused`  
  
### <a name="drop-boxcombo-box-controls"></a>Contrôles de zone déroulante/zone de liste modifiable  
 ![DROP&#45;vers le bas&#47;ligne rouge de zone de liste déroulante](../../extensibility/ux-guidelines/media/0303-167-dropdowncomboboxredline.png "0303-167_DropDownComboBoxRedline")  
  
 Utilisez...  
 pour les zones déroulantes et les zones de liste modifiable qui font partie de la zone de configuration de document.  
  
 N’utilisez pas...  
 -   pour toute interface utilisateur qui n’est pas une zone déroulante ou une zone de liste modifiable.  
  
- pour un [Drop-down](../../misc/shared-colors.md#BKMK_CommandDropDown) ou [Combo box](../../misc/shared-colors.md#BKMK_CommandComboBox) dans la barre de commandes.  
  
  **Default**  
  
  Composant  
  
  Élément  
  
  Nom du jeton : Category.color  
  
  ![DROP&#45;vers le bas&#47;zone de liste déroulante](../../extensibility/ux-guidelines/media/0303-168-dropdowncombobox.png "0303-168_DropDownComboBox")  
  
  Présentation  
  
  `CommonControls.ComboBoxBackground`  
  
  Bordure  
  
  `CommonControls.ComboBoxBorder`  
  
  Texte  
  
  `CommonControls.ComboBoxText`  
  
  Séparateur  
  
  `CommonControls.ComboBoxSeparator`  
  
  Glyphe  
  
  `CommonControls.ComboBoxGlyph`  
  
  Arrière-plan de glyphe  
  
  `CommonControls.ComboBoxGlyphBackground`  
  
  **Désactivé**  
  
  Composant  
  
  Élément  
  
  Nom du jeton : Category.color  
  
  ![DROP&#45;vers le bas&#47;désactivée de zone de liste déroulante](../../extensibility/ux-guidelines/media/0303-169-dropdowncomboboxdisabled.png "0303-169_DropDownComboBoxDisabled")  
  
  Présentation  
  
  `CommonControls.ComboBoxBackgroundDisabled`  
  
  Bordure  
  
  `CommonControls.ComboBoxBorderDisabled`  
  
  Texte  
  
  `CommonControls.ComboBoxTextDisabled`  
  
  Séparateur  
  
  `CommonControls.ComboBoxSeparatorDisabled`  
  
  Glyphe  
  
  `CommonControls.ComboBoxGlyphDisabled`  
  
  Arrière-plan de glyphe  
  
  `CommonControls.ComboBoxGlyphBackgroundDisabled`  
  
  **Placez le curseur**  
  
  Composant  
  
  Élément  
  
  Nom du jeton : Category.color  
  
  ![DROP&#45;vers le bas&#47;zone de liste déroulante au pointage](../../extensibility/ux-guidelines/media/0303-170-dropdowncomboboxhover.png "0303-170_DropDownComboBoxHover")  
  
  Présentation  
  
  `CommonControls.ComboBoxBackgroundHover`  
  
  Bordure  
  
  `CommonControls.ComboBoxBorderHover`  
  
  Texte  
  
  `CommonControls.ComboBoxTextHover`  
  
  Séparateur  
  
  `CommonControls.ComboBoxSeparatorHover`  
  
  Glyphe  
  
  `CommonControls.ComboBoxGlyphHover`  
  
  Arrière-plan de glyphe  
  
  `CommonControls.ComboBoxGlyphBackgroundHover`  
  
  **Enfoncé**  
  
  Composant  
  
  Élément  
  
  Nom du jeton : Category.color  
  
  ![DROP&#45;vers le bas&#47;appuyée de zone de liste déroulante](../../extensibility/ux-guidelines/media/0303-171-dropdowncomboboxpressed.png "0303-171_DropDownComboBoxPressed")  
  
  Présentation  
  
  `CommonControls.ComboBoxBackgroundPressed`  
  
  Bordure  
  
  `CommonControls.ComboBoxBorderPressed`  
  
  Texte  
  
  `CommonControls.ComboBoxTextPressed`  
  
  Séparateur  
  
  `CommonControls.ComboBoxSeparatorPressed`  
  
  Glyphe  
  
  `CommonControls.ComboBoxGlyphPressed`  
  
  Arrière-plan de glyphe  
  
  `CommonControls.ComboBoxGlyphBackgroundPressed`  
  
  **Focus**  
  
  Composant  
  
  Élément  
  
  Nom du jeton : Category.color  
  
  ![DROP&#45;vers le bas&#47;zone de liste déroulante concentré](../../extensibility/ux-guidelines/media/0303-172-dropdowncomboboxfocused.png "0303-172_DropDownComboBoxFocused")  
  
  Présentation  
  
  `CommonControls.ComboBoxBackgroundFocused`  
  
  Bordure  
  
  `CommonControls.ComboBoxBorderFocused`  
  
  Texte  
  
  `CommonControls.ComboBoxTextFocused`  
  
  Séparateur  
  
  `CommonControls.ComboBoxSeparatorFocused`  
  
  Glyphe  
  
  `CommonControls.ComboBoxGlyphFocused`  
  
  Arrière-plan de glyphe  
  
  `CommonControls.ComboBoxGlyphBackgroundFocused`  
  
  **Sélection d’entrée de texte**  
  
  Composant  
  
  Élément  
  
  Nom du jeton : Category.color  
  
  ![DROP&#45;vers le bas&#47;entrée de texte de zone de liste déroulante](../../extensibility/ux-guidelines/media/0303-173-dropdowncomboboxtextinput.png "0303-173_DropDownComboBoxTextInput")  
  
  Surligner  
  
  `CommonControls.ComboBoxTextInputSelection`  
  
  **Appuyé : vue d’élément de liste**  
  
  ![DROP&#45;vers le bas&#47;vue de liste de zone de liste déroulante](../../extensibility/ux-guidelines/media/0303-174-dropdowncomboboxlistview.png "0303-174_DropDownComboBoxListView")  
  
  Présentation  
  
  `CommonControls.ComboBoxListBackground`  
  
  `CommonControls.ComboBoxListBackgroundHover`  
  
  `CommonControls.ComboBoxListItemBackgroundPressed`  
  
  `CommonControls.ComboBoxListItemBackgroundFocused`  
  
  Bordure  
  
  `CommonControls.ComboBoxListBorder`  
  
  `CommonControls.ComboBoxListBorderHover`  
  
  `CommonControls.ComboBoxListBorderPressed`  
  
  `CommonControls.ComboBoxListBorderFocused`  
  
  Texte d’élément  
  
  `CommonControls.ComboBoxListItemText`  
  
  `CommonControls.ComboBoxListItemTextHover`  
  
  `CommonControls.ComboBoxListItemTextPressed`  
  
  `CommonControls.ComboBoxListItemTextFocused`  
  
  Ombre d’arrière-plan  
  
  `CommonControls.ComboBoxListBackgroundShadow`  
  
### <a name="tabular-data-grid-controls"></a>Contrôles de données tabulaires (grille)  
 Les contrôles de données tabulaires, également appelés contrôles de grille, sont des contrôles communs pour Visual Studio qui peuvent être utilisés pour présenter des grandes quantités de données dans plusieurs colonnes. Les contrôles de données tabulaires standard se trouvent à plusieurs endroits dans Visual Studio : la fenêtre Outil Liste d’erreurs, les rapports IntelliTrace et l’affichage du tas de mémoire, entre autres. Utilisez toujours les contrôles de données tabulaires standard fournis. Dans de rares cas, vous pouvez ne pas avoir accès aux contrôles de données tabulaires standard. Si tel est le cas, utilisez les noms de jeton suivants pour veiller à ce que votre interface utilisateur soit cohérente avec les autres contrôles de données tabulaires dans Visual Studio.  
  
 ![Données tabulaires &#40;contrôle de grille&#41; ligne rouge de](../../extensibility/ux-guidelines/media/0303-197-tabulardatagridcontrolredline.png "0303-197_TabularDataGridControlRedline")  
  
 Utilisez...  
 pour les contrôles tabulaires ou de grille.  
  
 N’utilisez pas...  
 pour toute interface utilisateur qui n’est pas un contrôle tabulaire ou de grille.  
  
#### <a name="column-headers"></a>En-têtes de colonnes  
 Les en-têtes de colonnes comprennent un arrière-plan, une bordure, le texte du titre et un éventuel glyphe généralement utilisé pour trier une grille selon cette colonne.  
  
 État  
  
 Élément  
  
 Nom du jeton : Category.color  
  
 Par défaut  
  
 Présentation  
  
 `Header.Default`  
  
 Premier plan (texte)  
  
 `Environment.CommandBarTextActive`  
  
 Premier plan (glyphe)  
  
 `Header.Glyph`  
  
 Bordure  
  
 `Header.SeparatorLine`  
  
 Pointage  
  
 Présentation  
  
 `Header.MouseOver`  
  
 Premier plan (texte)  
  
 `Environment.CommandBarTextHover`  
  
 Premier plan (glyphe)  
  
 `Header.MouseOverGlyph`  
  
 Bordure  
  
 `Header.SeparatorLine`  
  
 Appuyé  
  
 Présentation  
  
 `CommonControls.CheckBoxBackgroundPressed`  
  
 Premier plan (texte)  
  
 `CommonControls.CheckBoxBorderPressed`  
  
 Premier plan (glyphe)  
  
 `CommonControls.CheckBoxTextPressed`  
  
 Bordure  
  
 `CommonControls.CheckBoxGlyphPressed`  
  
#### <a name="list-view-items"></a>Éléments de la vue Liste  
 Les éléments de la vue Liste comprennent un arrière-plan et le contenu. Le contenu peut être du texte, une icône ou les deux.  
  
 État  
  
 Élément  
  
 Nom du jeton : Category.color  
  
 Par défaut  
  
 Présentation  
  
 Transparent  
  
 Premier plan (texte)  
  
 `Environment.CommandBarTextActive`  
  
 Bordure  
  
 Aucun.  
  
 Sélectionné (actif)  
  
 Présentation  
  
 `TreeView.SelectedItemActive`  
  
 Premier plan (texte)  
  
 `TreeView.SelectedItemActiveText`  
  
 Bordure  
  
 Aucun.  
  
 Sélectionné (inactif)  
  
 Présentation  
  
 `TreeView.SelectedItemInactive`  
  
 Premier plan (texte)  
  
 `TreeView.SelectedItemInactiveText`  
  
 Bordure  
  
 Aucun.  
  
## <a name="manifest-designer"></a>Concepteur de manifeste  
 Le concepteur de manifeste sert à faciliter l’édition du fichier manifeste dans des projets Windows 8 et Windows Phone 8. Même s’il n’existe aucune infrastructure partagée disponible à la consommation, vous avez peut-être intérêt à faire correspondre la disposition et les couleurs des onglets d’orientation/de navigation à la structure générale. Pour plus d’informations sur la disposition, consultez [Layout for Visual Studio](../../extensibility/ux-guidelines/layout-for-visual-studio.md).  
  
 ![Ligne rouge de Concepteur de manifeste](../../extensibility/ux-guidelines/media/0303-175-manifestdesignerredline.png "0303-175_ManifestDesignerRedline")  
  
 Utilisez...  
 -   pour les concepteurs qui sont similaires au concepteur de manifeste.  
  
- au lieu d’utiliser des contrôles d’onglet commun en haut d’un éditeur au sein de la zone de configuration de document.  
  
  N’utilisez pas...  
  -   si vous avez plus de six onglets.  
  
- pour toute interface utilisateur qui n’est pas structurée comme le concepteur de manifeste.  
  
  État  
  
  Composant  
  
  Élément  
  
  Nom du jeton : Category.color  
  
  Par défaut (sélectionné)  
  
  Onglet  
  
  Présentation  
  
  `ManifestDesigner.TabActive`  
  
  Bordure  
  
  Aucun.  
  
  Volet Description  
  
  Présentation  
  
  `ManifestDesigner.DescriptionPane`  
  
  Page de contenu  
  
  Présentation  
  
  `ManifestDesigner.Background`  
  
  Texte d’assistance de boîte de dialogue  
  
  `ManifestDesigner.WatermarkText`  
  
  Ce nom de jeton ne correspond pas à sa fonction.  
  
  Non sélectionné  
  
  Onglet  
  
  Présentation  
  
  `ManifestDesigner.Tab.Inactive`  
  
  Pointage  
  
  Onglet  
  
  Présentation  
  
  `ManifestDesigner.Tab.Mouseover`  
  
## <a name="tagging"></a>Étiquetage  
 Visual Studio prend en charge l’étiquetage, qui permet à un utilisateur de déclarer des mots clés pouvant faire l’objet d’une recherche à des fins de suivi. Par exemple, les chefs de projet et développeurs peuvent utiliser Team Foundation Server (TFS) pour étiqueter des éléments de travail. Les tableaux ci-dessous indiquent les noms de couleurs pour l’étiquette elle-même et le glyphe de l’icône de fermeture qui apparaît dans les états Pointage et Sélectionné.  
  
 ![Ligne rouge de balisage](../../extensibility/ux-guidelines/media/0303-176-taggingredline.png "0303-176_TaggingRedline")  
  
 Utilisez...  
 pour une interface utilisateur qui prend en charge l’étiquetage.  
  
 N’utilisez pas...  
 pour tout autre type d’interface utilisateur.  
  
### <a name="tag"></a>Balise  
 Composant  
  
 Élément  
  
 Nom du jeton : Category.color  
  
 ![Balise](../../extensibility/ux-guidelines/media/0303-177-tag.png "0303-177_Tag")  
  
 **Default**  
  
 Présentation  
  
 `Tag.Background`  
  
 Premier plan (texte)  
  
 `Tag.Background`  
  
 ![Étiquette au pointage](../../extensibility/ux-guidelines/media/0303-178-taghover.png "0303-178_TagHover")  
  
 **Placez le curseur**  
  
 Présentation  
  
 `Tag.HoverBackground`  
  
 Premier plan (texte)  
  
 `Tag.HoverBackgroundText`  
  
 ![Étiquette enfoncée](../../extensibility/ux-guidelines/media/0303-179-tagpressed.png "0303-179_TagPressed")  
  
 **Enfoncé**  
  
 Présentation  
  
 `Tag.PressedBackground`  
  
 Premier plan (texte)  
  
 `Tag.PressedBackgroundText`  
  
 ![Étiquette sélectionnée](../../extensibility/ux-guidelines/media/0303-180-tagselected.png "0303-180_TagSelected")  
  
 **sélectionné**  
  
 Présentation  
  
 `Tag.SelectedBackground`  
  
 Premier plan (texte)  
  
 `Tag.SelectedBackgroundText`  
  
### <a name="glyph-close-icon"></a>Glyphe (icône de fermeture)  
 **Default**  
  
 Composant  
  
 Élément  
  
 Nom du jeton : Category.color  
  
 ![Balise &#40;glyphe&#41;](../../extensibility/ux-guidelines/media/0303-181-tagglyph.png "0303-181_TagGlyph")  
  
 **Par défaut (valeur par défaut de la balise)**  
  
 Présentation  
  
 N/A  
  
 Premier plan (glyphe)  
  
 `Tag.TagHoverGlyph`  
  
 **Placez le curseur**  
  
 Composant  
  
 Élément  
  
 Nom du jeton : Category.color  
  
 ![Balise &#40;glyphe&#41; pointage](../../extensibility/ux-guidelines/media/0303-182-tagglyphhover.png "0303-182_TagGlyphHover")  
  
 **Pointage (valeur par défaut de la balise)**  
  
 Présentation  
  
 `Tag.TagHoverGlyphHoverBackground`  
  
 Premier plan (glyphe)  
  
 `Tag.TagHoverGlyphHover`  
  
 Bordure  
  
 `Tag.TagHoverGlyphHoverBorder`  
  
 **Enfoncé**  
  
 Composant  
  
 Élément  
  
 Nom du jeton : Category.color  
  
 ![Balise &#40;glyphe&#41; enfoncé](../../extensibility/ux-guidelines/media/0303-183-tagglyphpressed.png "0303-183_TagGlyphPressed")  
  
 **Appuyé (valeur par défaut de la balise)**  
  
 Présentation  
  
 `Tag.TagHoverGlyphPressedBackground`  
  
 Premier plan (glyphe)  
  
 `Tag.TagHoverGlyphPressed`  
  
 Bordure  
  
 `Tag.TagHoverGlyphPressedBorder`  
  
 **Par défaut sélectionnée/glyphe de balise**  
  
 Composant  
  
 Élément  
  
 Nom du jeton : Category.color  
  
 ![Étiquette sélectionnée](../../extensibility/ux-guidelines/media/0303-184-tagselected.png "0303-184_TagSelected")  
  
 **Par défaut (étiquette sélectionnée)**  
  
 Présentation  
  
 N/A  
  
 Premier plan (glyphe)  
  
 `Tag.TagSelectedGlyph`  
  
 **Étiquette sélectionnée/glyphe au pointage**  
  
 Composant  
  
 Élément  
  
 Nom du jeton : Category.color  
  
 ![Étiquette sélectionnée au pointage](../../extensibility/ux-guidelines/media/0303-185-tagselectedhover.png "0303-185_TagSelectedHover")  
  
 **Pointage (étiquette sélectionnée)**  
  
 Présentation  
  
 `Tag.TagSelectedGlyphHoverBackground`  
  
 Premier plan (glyphe)  
  
 `Tag.TagSelectedGlyphHover`  
  
 Bordure  
  
 `Tag.TagSelectedGlyphHoverBorder`  
  
 **Étiquette sélectionnée/glyphe enfoncé**  
  
 Composant  
  
 Élément  
  
 Nom du jeton : Category.color  
  
 ![Étiquette sélectionnée enfoncée](../../extensibility/ux-guidelines/media/0303-186-tagselectedpressed.png "0303-186_TagSelectedPressed")  
  
 **Appuyé (étiquette sélectionnée)**  
  
 Présentation  
  
 `Tag.TagSelectedGlyphPressedBackground`  
  
 Premier plan (glyphe)  
  
 `Tag.TagSelectedGlyphPressed`  
  
 Bordure  
  
 `Tag.TagSelectedGlyphPressedBorder`  
  
## <a name="shell"></a>Shell  
  
### <a name="background"></a>Présentation  
 L’arrière-plan de l’environnement comporte deux couches. La couche inférieure est une couleur unie qui recouvre l’ensemble de l’IDE. La couche supérieure se place sous l’interface de commande et entre les canaux à masquage automatique de la fenêtre Outil situés sur les côtés gauche et droit de l’IDE. Depuis Visual Studio 2013, les couches d’arrière-plan supérieure et inférieure sont définies sur la même couleur dans les thèmes clairs et foncés.  
  
 ![Ligne rouge d’arrière-plan de shell](../../extensibility/ux-guidelines/media/0303-187-shellbackgroundredline.png "0303-187_ShellBackgroundRedline")  
  
 Utilisez...  
 pour les endroits que vous voulez faire correspondre à l’arrière-plan de l’environnement Visual Studio.  
  
 N’utilisez pas...  
 -   en tant que remplissage pour les endroits qui ne sont pas des surfaces d’arrière-plan.  
  
- en guise d’arrière-plan sur lequel placer des éléments de premier plan.  
  
  Composant  
  
  Élément  
  
  Nom du jeton : Category.color  
  
  Couche inférieure  
  
  Présentation  
  
  `Environment.EnvironmentBackground`  
  
  Composant  
  
  Élément  
  
  Nom du jeton : Category.color  
  
  Couche supérieure  
  
  Présentation  
  
  *Défini sur la même valeur de couleur dans les thèmes clairs de 2013 Visual Studio et foncés de dégradé.*  
  
  `Environment.EnvironmentBackgroundGradientBegin`  
  
  `Environment.EnvironmentBackgroundGradientEnd`  
  
  `Environment.EnvironmentBackgroundGradientMiddle1`  
  
  `Environment.EnvironmentBackgroundGradientMiddle2`  
  
### <a name="command-shelf"></a>Interface de commande  
 Deux ensembles de noms de jeton sont utilisés pour les arrière-plans de l’interface de commande : un jeu pour l’emplacement de la barre de menus et l’autre pour l’emplacement des barres de commandes. Un groupe de barres de commandes possède ses propres valeurs de couleur d’arrière-plan, lesquelles sont décrites dans la section « Barre de commandes ». Le texte de la barre de menus et des barres de commandes est traité dans les sections qui leur sont dédiées.  
  
 ![Ligne rouge d’interface de commande](../../extensibility/ux-guidelines/media/0303-188-commandshelfredline.png "0303-188_CommandShelfRedline")  
  
 Utilisez...  
 -   pour les zones où vous placez des menus ou barres d’outils.  
  
- avec l’arrière-plan correct / ? combinaison de nom du jeton de premier plan.  
  
  N’utilisez pas...  
  pour les zones qui ne sont pas similaires à une interface de commande.  
  
  Composant  
  
  Élément  
  
  Nom du jeton : Category.color  
  
  Barre de menus  
  
  Présentation  
  
  *Défini sur la même valeur de couleur dans les thèmes clairs de 2013 Visual Studio et foncés de dégradé.*  
  
  `Environment.CommandShelfHighlightGradientBegin`  
  
  `Environment.CommandShelfHighlightGradientMiddle`  
  
  `Environment.CommandShelfHighlightGradientEnd`  
  
  Barre de commandes  
  
  Présentation  
  
  *Défini sur la même valeur de couleur dans les thèmes clairs de 2013 Visual Studio et foncés de dégradé.*  
  
  `Environment.CommandShelfBackgroundGradientBegin`  
  
  `Environment.CommandShelfBackgroundGradientMiddle`  
  
  `Environment.CommandShelfBackgroundGradientEnd`  
  
## <a name="toolbox"></a>Boîte à outils  
 La boîte à outils est une fenêtre Outil commune fréquemment utilisée dans Visual Studio. Il s’agit essentiellement d’un contrôle d’arborescence avec un thème spécial et un style appliqués.  
  
 ![Ligne rouge de boîte à outils](../../extensibility/ux-guidelines/media/0303-189-toolboxredline.png "0303-189_ToolboxRedline")  
  
 Utilisez...  
 quand vous concevez une fenêtre Outil que vous voulez toujours cohérente avec la boîte à outils de l’interpréteur de commandes.  
  
 N’utilisez pas...  
 pour tout élément qui n’est pas similaire à l’interface utilisateur de la boîte à outils, ou si vous ne savez pas si votre interface utilisateur aura des problèmes, si les couleurs de la boîte à outils de l’interpréteur de commandes changent.  
  
 **Default**  
  
 Composant  
  
 Élément  
  
 Nom du jeton : Category.color  
  
 ![Nœud parent de boîte à outils](../../extensibility/ux-guidelines/media/0303-190-toolboxparentnode.png "0303-190_ToolboxParentNode")  
  
 **Nœud parent**  
  
 ![Nœud enfant de boîte à outils](../../extensibility/ux-guidelines/media/0303-191-toolboxchildnode.png "0303-191_ToolboxChildNode")  
  
 **Nœud enfant**  
  
 Présentation  
  
 `Environment.ToolboxContent`  
  
 Titres  
  
 `Environment.ToolWindowBackground`  
  
 Éléments individuels ou fenêtre entière en l’absence de contrôles disponibles  
  
 Bordure  
  
 Aucun.  
  
 Premier plan (glyphe)  
  
 `Environment.ToolboxContent`  
  
 Premier plan (texte)  
  
 `Environment.ToolboxContent`  
  
 **Placez le curseur**  
  
 Composant  
  
 Élément  
  
 Nom du jeton : Category.color  
  
 ![Nœud enfant de boîte à outils au pointage](../../extensibility/ux-guidelines/media/0303-192-toolboxchildnodehover.png "0303-192_ToolboxChildNodeHover")  
  
 **Pointage de boîte à outils sur le nœud enfant**  
  
 Présentation  
  
 `Environment.ToolboxContentMouseOver`  
  
 Éléments individuels uniquement  
  
 Bordure  
  
 Aucun.  
  
 Premier plan (texte)  
  
 `Environment.ToolboxContentMouseOver`  
  
 Éléments individuels uniquement  
  
 **sélectionné**  
  
 Composant  
  
 Élément  
  
 Nom du jeton : Category.color  
  
 ![Nœud parent de boîte à outils concentré](../../extensibility/ux-guidelines/media/0303-193-toolboxparentnodefocused.png "0303-193_ToolboxParentNodeFocused")  
  
 **Nœud parent avec focus**  
  
 ![Nœud enfant de boîte à outils concentré](../../extensibility/ux-guidelines/media/0303-194-toolboxchildnodefocused.png "0303-194_ToolboxChildNodeFocused")  
  
 **Nœud enfant avec focus**  
  
 Présentation  
  
 `TreeView.SelectedItemActive`  
  
 À partir de la catégorie [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView)  
  
 Bordure  
  
 `TreeView.FocusVisualBorder`  
  
 À partir de la catégorie [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView)  
  
 Premier plan (glyphe)  
  
 `TreeView.SelectedItemActive`  
  
 À partir de la catégorie [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView)  
  
 Premier plan (texte)  
  
 `TreeView.SelectedItemActive`  
  
 À partir de la catégorie [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView)  
  
 ![Nœud parent de boîte à outils inactif](../../extensibility/ux-guidelines/media/0303-195-toolboxparentnodeunfocused.png "0303-195_ToolboxParentNodeUnfocused")  
  
 **Nœud parent sans focus**  
  
 ![Nœud enfant de boîte à outils inactif](../../extensibility/ux-guidelines/media/0303-196-toolboxchildnodeunfocused.png "0303-196_ToolboxChildNodeUnfocused")  
  
 **Nœud enfant sans focus**  
  
 Présentation  
  
 `TreeView.SelectedItemInactive`  
  
 À partir de la catégorie [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView)  
  
 Bordure  
  
 Aucun.  
  
 Premier plan (glyphe)  
  
 `TreeView.SelectedItemInactive`  
  
 À partir de la catégorie [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView)  
  
 Premier plan (texte)  
  
 `TreeView.SelectedItemInactive`  
  
 À partir de la catégorie [Tree view](../../extensibility/ux-guidelines/shared-colors-for-visual-studio.md#BKMK_TreeView)

