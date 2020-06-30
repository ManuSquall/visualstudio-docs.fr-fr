---
title: Modèles de contrôle communs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 3e893949-6398-42f1-9eab-a8d8c2b7f02d
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: dd2b2723a5ecfe66e9471cfea1e8eb55ed7ced59
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547444"
---
# <a name="common-control-patterns-for-visual-studio"></a>Modèles de contrôle courants pour Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

## <a name="common-controls"></a><a name="BKMK_CommonControls"></a>Contrôles communs

### <a name="overview"></a>Vue d’ensemble
 Les contrôles communs constituent la majeure partie de l’interface utilisateur dans Visual Studio. La plupart des contrôles courants utilisés dans l’interface Visual Studio doivent respecter les [instructions relatives à l’interaction avec les ordinateurs de bureau Windows](https://msdn.microsoft.com/library/windows/desktop/dn742399.aspx). Ce document est propre à Visual Studio et aborde des situations particulières ou des détails qui augmentent ces instructions Windows.

#### <a name="common-controls-in-this-topic"></a>Contrôles communs dans cette rubrique

- [Barres](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_Scrollbars)

- [Champs d’entrée](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_InputFields)

- [Zones de liste déroulante et listes déroulantes](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ComboBoxesAndDropDowns)

- [Cases à cocher](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CheckBoxes)

- [Boutons de radio](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_RadioButtons)

- [Frames de groupe](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_GroupFrames)

- [Contrôles de texte](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)

- [Boutons et liens hypertexte](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)

- [Arborescences](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViews)

#### <a name="visual-style"></a>Style visuel
 La première chose à prendre en compte lorsque vous appliquez un style aux contrôles est de savoir si les contrôles seront utilisés dans l’interface utilisateur. Les contrôles dans l’interface utilisateur standard sont des interfaces utilisateur sans thème et doivent suivre le [style de bureau Windows normal](https://msdn.microsoft.com/library/windows/desktop/dn742399\(v=vs.85\).aspx), ce qui signifie qu’ils ne sont pas remodèleés et doivent apparaître dans leur apparence de contrôle par défaut.

- **Boîtes de dialogue standard (utilitaire) :** pas à thème. Ne pas recréer de modèle. Utilisez les valeurs par défaut du style de contrôle de base.

- **Fenêtres outil, éditeurs de documents, aires de conception et boîtes de dialogue à thème :** Utilisez l’apparence spécialisée à thème à l’aide du service de couleurs.

### <a name="scrollbars"></a><a name="BKMK_Scrollbars"></a>Barres
 Les barres de défilement doivent suivre [les modèles d’interaction courants pour les barres de défilement Windows](https://msdn.microsoft.com/library/windows/desktop/bb787527\(v=vs.85\).aspx) , sauf si elles sont complétées par des informations de contenu, comme dans l’éditeur de code.

### <a name="input-fields"></a><a name="BKMK_InputFields"></a>Champs d’entrée
 Pour le comportement d’interaction standard, suivez les [instructions du bureau Windows pour les zones de texte](https://msdn.microsoft.com/library/windows/desktop/dn742442\(v=vs.85\).aspx).

#### <a name="visual-style"></a>Style visuel

- Les champs d’entrée ne doivent pas être stylisés dans les boîtes de dialogue d’utilitaire. Utilisez le style de base intrinsèque au contrôle.

- Les champs d’entrée à thème doivent uniquement être utilisés dans des boîtes de dialogue et des fenêtres outil.

#### <a name="specialized-interactions"></a>Interactions spécialisées

- Les champs en lecture seule présentent un arrière-plan gris (désactivé) mais un premier plan par défaut (actif).

- Les champs obligatoires doivent comporter des **\<Required>** filigranes. Vous ne devez pas modifier la couleur de l’arrière-plan, sauf dans de rares situations.

- Validation des erreurs : voir [notifications et progression pour Visual Studio](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)

- Les champs d’entrée doivent être dimensionnés pour s’ajuster au contenu, et non pour s’ajuster à la largeur de la fenêtre dans laquelle ils sont affichés, ni pour correspondre arbitrairement à la longueur d’un champ long, tel qu’un tracé. La longueur peut indiquer à l’utilisateur des limitations quant au nombre de caractères autorisés dans le champ.

     ![Largeur de contrôle de champ d’entrée incorrecte](../../extensibility/ux-guidelines/media/0707-01-incorrectinputfieldcontrol.png "0707-01_IncorrectInputFieldControl") **longueur de champ d’entrée incorrecte : il est peu probable que le nom soit ce long.**

     ![Corriger la largeur de contrôle du champ d’entrée](../../extensibility/ux-guidelines/media/0707-02-correctinputfieldcontrol.png "0707-02_CorrectInputFieldControl") **correcte longueur du champ d’entrée : le champ d’entrée est une largeur raisonnable pour le contenu attendu.**

### <a name="combo-boxes-and-drop-down-lists"></a><a name="BKMK_ComboBoxesAndDropDowns"></a>Zones de liste déroulante et listes déroulantes
 Pour le comportement d’interaction standard, suivez les [instructions du bureau Windows pour les listes déroulantes et les zones de liste](https://msdn.microsoft.com/library/windows/desktop/dn742404\(v=vs.85\).aspx)déroulante.

#### <a name="visual-style"></a>Style visuel

- Dans les boîtes de dialogue de l’utilitaire, ne recréez pas de modèle le contrôle. Utilisez le style de base intrinsèque au contrôle.

- Dans l’interface utilisateur à thème, les zones de liste déroulante et les listes déroulantes suivent les thèmes standard pour les contrôles.

#### <a name="layout"></a>Layout
 Les zones de liste modifiable et les listes déroulantes doivent être dimensionnées pour s’ajuster au contenu, et non pour s’ajuster à la largeur de la fenêtre dans laquelle elles sont affichées, ni pour correspondre arbitrairement à la longueur d’un champ long, tel qu’un tracé.

 ![Disposition de dépose&#45;incorrecte](../../extensibility/ux-guidelines/media/0707-03-incorrectdropdownlayout.png "0707-03_IncorrectDropDownLayout")

 **Longueur de champ incorrecte pour un contrôle de liste déroulante**

 ![Corriger la disposition de déplacement&#45;vers le PG.](../../extensibility/ux-guidelines/media/0707-04-correctdropdownlayout.png "0707-04_CorrectDropDownLayout")

 **Longueur de champ correcte pour un contrôle de liste déroulante**

### <a name="check-boxes"></a><a name="BKMK_CheckBoxes"></a>Cases à cocher
 Pour le comportement d’interaction standard, suivez les [instructions du bureau Windows pour les cases à cocher](https://msdn.microsoft.com/library/windows/desktop/dn742401\(v=vs.85\).aspx).

#### <a name="visual-style"></a>Style visuel

- Dans les boîtes de dialogue de l’utilitaire, ne recréez pas de modèle le contrôle. Utilisez le style de base intrinsèque au contrôle.

- Dans l’interface utilisateur à thème, les cases à cocher suivent les thèmes standard pour les contrôles.

#### <a name="specialized-interactions"></a>Interactions spécialisées

- L’interaction avec une case à cocher ne doit jamais dépiler une boîte de dialogue ou accéder à une autre zone.

- Aligner les cases à cocher avec la ligne de base de la première ligne de texte.

     ![Mauvais](../../extensibility/ux-guidelines/media/0707-05-incorrectcheckboxalign.png "0707-05_IncorrectCheckBoxAlign") alignement de la case à cocher alignement **des cases incorrectes : la case à cocher est centrée sur le texte.**

     ![Correct check box alignment](../../extensibility/ux-guidelines/media/0707-06-correctcheckboxalign.png "0707-06_CorrectCheckBoxAlign") Alignement de la case à cocher alignement de la case à cocher correcte alignement : la case **à cocher est alignée avec la ligne de base de la première ligne de texte.**

### <a name="radio-buttons"></a><a name="BKMK_RadioButtons"></a>Cases d’option
 Pour le comportement d’interaction standard, suivez les [instructions relatives au bureau Windows pour les cases d’option](https://msdn.microsoft.com/library/windows/desktop/dn742436\(v=vs.85\).aspx).

#### <a name="visual-style"></a>Style visuel
 Dans les boîtes de dialogue d’utilitaire, n’appliquez pas de style aux cases d’option. Utilisez le style de base intrinsèque au contrôle.

#### <a name="specialized-interactions"></a>Interactions spécialisées
 Il n’est pas nécessaire d’utiliser un cadre de groupe pour encadrer les choix radio.

### <a name="group-frames"></a><a name="BKMK_GroupFrames"></a>Frames de groupe
 Pour le comportement d’interaction standard, suivez les [instructions du bureau Windows pour les cadres de groupe](https://msdn.microsoft.com/library/windows/desktop/dn742405\(v=vs.85\).aspx).

#### <a name="visual-style"></a>Style visuel
 Dans les boîtes de dialogue de l’utilitaire, ne pas styliser les cadres de groupe. Utilisez le style de base intrinsèque au contrôle.

#### <a name="layout"></a>Layout

- Il n’est pas nécessaire d’utiliser un cadre de groupe pour encadrer les choix radio, sauf si vous devez maintenir la distinction entre les groupes dans une disposition serrée.

- N’utilisez jamais un cadre de groupe pour un seul contrôle.

- Il est parfois acceptable d’utiliser une règle horizontale au lieu d’un conteneur de cadre de groupe.

## <a name="text-controls"></a><a name="BKMK_TextControls"></a>Contrôles de texte

### <a name="labels"></a>Étiquettes

#### <a name="active-label-state"></a>État de l’étiquette active

##### <a name="utility-standard-dialogs"></a>Boîtes de dialogue de l’utilitaire (standard)

- En général, suivez les conseils Windows Desktop pour les étiquettes de contrôle.

- Dans les boîtes de dialogue de l’utilitaire, les étiquettes doivent apparaître non gras, dans la police et la couleur de texte de l’environnement standard. Consultez [polices et mise en forme pour Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md).

- Les ellipses doivent toujours suivre les étiquettes.

##### <a name="signature-themed-dialogs"></a>Boîtes de dialogue signature (à thème))
 Les contrôles Label peuvent être en gras ou en gris clair.

#### <a name="disabled-label-state"></a>État de l’étiquette désactivé
 Les étiquettes doivent refléter l’apparence du contrôle auquel elles sont associées. Par exemple, si le contrôle associé est désactivé, l’étiquette doit apparaître grise et désactivée. Cette opération est généralement gérée par le système d’exploitation et ne nécessite pas de traitement spécial.

#### <a name="dynamic-labels"></a>Étiquettes dynamiques
 Les étiquettes dynamiques changent en fonction de la sélection actuelle. Dans la mesure du possible, utilisez des étiquettes dynamiques en mode maître/détail pour aider l’utilisateur à comprendre que les informations affichées sont pertinentes pour une sélection spécifique et non pour des informations générales.

 ![Étiquette dynamique utilisée avec un contenu dynamique](../../extensibility/ux-guidelines/media/070702-01-dynamiclabel.png "070702-01_DynamicLabel")

 **Exemple d’étiquette dynamique utilisée avec du contenu dynamique**

#### <a name="instructional-text"></a>Texte d’instructions
 Certains éléments d’interface tirent parti d’un texte d’instructions pour aider l’utilisateur à comprendre l’objet de l’interface utilisateur ou à indiquer l’action à entreprendre.

- Le texte d’instructions est le plus courant en haut des boîtes de dialogue, mais peut apparaître dans d’autres zones pour fournir des instructions à un regroupement de contrôles complexe.

- Le texte d’instructions n’est pas interactif, mais peut contenir des liens hypertexte vers des rubriques d’aide.

- Utilisez le texte d’instructions avec modération et uniquement lorsque cela est nécessaire.

##### <a name="formatting"></a>Mise en forme
 Le texte d’instructions doit être une police d’environnement, un texte de contrôle standard (sans thème). Consultez [polices et mise en forme pour Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md).

 Pour plus d’informations sur l’écriture de texte d’instructions, consultez [texte et terminologie de l’interface utilisateur](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology).

 ![Mise en forme du texte d'instructions](../../extensibility/ux-guidelines/media/070702-02-instructionaltextformatting.png "070702-02_InstructionalTextFormatting")

 **Texte d’instructions dans une boîte de dialogue Visual Studio**

#### <a name="informational-text"></a>Texte informatif
 Le texte informatif est un texte qui donne des informations supplémentaires à l’utilisateur. Il peut être statique ou dynamique, ou utilisé comme notification. Elle est toujours en lecture seule, mais s’il est utile que l’utilisateur ait la possibilité de copier les informations, le texte dynamique doit être placé dans un conteneur de contrôle tel qu’un champ de texte en lecture seule.

##### <a name="dynamic-context-specific-text"></a>Texte dynamique (spécifique au contexte)
 Le texte des informations dynamiques change en fonction du contexte, par exemple lorsque l’utilisateur change le focus. Souvent, mais pas toujours, le contenu dynamique est associé à une étiquette dynamique.

 ![Texte d'informations dynamique](../../extensibility/ux-guidelines/media/070702-03-informationaldynamictext.png "070702-03_InformationalDynamicText")

 **Modifications du texte d’information dynamique en fonction du contexte.**

##### <a name="formatting"></a>Mise en forme
 Il existe deux façons d’afficher des champs de texte en lecture seule : directement sur la surface de l’interface utilisateur (voir ci-dessus) ou contenues dans un autre contrôle, tel qu’un cadre de groupe ou une zone de texte. L’une ou l’autre est correcte en fonction de la situation. Il revient au concepteur de fonctionnalités de déterminer comment présenter les informations en lecture seule.

 Le texte peut être à l’intérieur d’une zone de texte en lecture seule. Cela indique généralement que le contenu peut être sélectionné et copié, bien qu’il ne puisse pas être modifié.

 ![Mise en forme de texte informatif pour les champs de lecture&#45;uniquement](../../extensibility/ux-guidelines/media/070702-04-informationalformatting.png "070702-04_InformationalFormatting")

 **Mise en forme du texte d'informations pour champs en lecture seule**

#### <a name="watermarks"></a>Filigranes
 Alors que la formulation peut être la même, la différence entre les filigranes et le texte d’instructions est que les filigranes sont remplacés par du contenu lorsque le contrôle/la fenêtre n’est pas vide et que le texte d’instructions reste visible en permanence.

 Les filigranes doivent être utilisés lorsqu’une fenêtre ou un contrôle est vide. Ils indiquent ce qui doit être fait pour remplir la zone et peuvent inclure des liens d’action pour ouvrir des fenêtres pertinentes, telles qu’une source de glissement.

##### <a name="visual-style"></a>Style visuel

- Les filigranes doivent être centrés horizontalement dans la fenêtre.

- Les filigranes doivent être alignés au centre et non alignés à gauche.

- Les filigranes peuvent être centrés verticalement ou positionnés près du haut de la zone. S’il est situé près du haut de la zone, il doit y avoir suffisamment d’espace pour que le filigrane se distingue.

- Utilisez le `Environment.GrayText` jeton de couleur et la police d’environnement standard. Les liens hypertexte doivent utiliser les jetons partagés de lien hypertexte standard : `Environment.PanelHyperlink` , `Environment.PanelHyperlinkHover` , `Environment.PanelHyperlinkPressed` et `Environment.PanelHyperlinkDisabled` .

- Les filigranes ne peuvent pas être sélectionnés en arrière-plan

- Si possible, incluez des liens dans le filigrane pour aider l’utilisateur à commencer.

  ![Texte de filigrane dans une fenêtre de concepteur](../../extensibility/ux-guidelines/media/070702-05-watermark1.png "070702-05_Watermark1")

  ![Texte de filigrane dans une fenêtre Outil](../../extensibility/ux-guidelines/media/070702-06-watermark2.png "070702-06_Watermark2")

  **Exemples de texte de filigrane dans Visual Studio**

## <a name="buttons-and-hyperlinks"></a><a name="BKMK_ButtonsAndHyperlinks"></a>Boutons et liens hypertexte

### <a name="overview"></a>Vue d’ensemble
 Les boutons et les contrôles de liens (liens hypertexte) doivent suivre les [instructions du bureau Windows de base sur les liens hypertexte](https://msdn.microsoft.com/library/windows/desktop/dn742406\(v=vs.85\).aspx) pour l’utilisation, le libellé, le dimensionnement et l’espacement.

### <a name="choosing-between-buttons-and-links"></a>Choix entre les boutons et les liens
 Traditionnellement, les boutons ont été utilisés pour les actions et les liens hypertexte sont réservés pour la navigation. Les boutons peuvent être utilisés dans tous les cas, mais le rôle des liens a été développé dans Visual Studio afin que les boutons et les liens soient plus interchangeables dans certaines conditions.

 Quand utiliser des boutons de commande :

- Commandes principales

- Affichage des fenêtres utilisées pour collecter des entrées ou faire des choix, même s’il s’agit de commandes secondaires

- Actions destructrices ou irréversibles

- Boutons d’engagement dans les assistants et les flux de page

  Évitez les boutons de commande dans les fenêtres outil ou si vous avez besoin de plus de deux mots pour l’étiquette. Les liens peuvent avoir des étiquettes plus longues.

  Quand utiliser des liens :

- Navigation vers une autre fenêtre, un document ou une page Web

- Situations qui nécessitent une étiquette plus longue ou une phrase brève pour décrire l’objectif de l’action

- Espaces serrés où un bouton surcharge l’interface utilisateur, à condition que l’action ne soit pas destructrice ou irréversible

- Mettre en évidence les commandes secondaires dans des situations où il existe de nombreuses commandes

#### <a name="examples"></a>Exemples
 ![Liens de commandes de barre d'informations suivant un message d'état](../../extensibility/ux-guidelines/media/070703-01-commandlinkinfobar.png "070703-01_CommandLinkInfobar")

 **Liens de commande utilisés dans la barre d’informations après un message d’État**

 ![Liens utilisés dans la fenêtre contextuelle CodeLens](../../extensibility/ux-guidelines/media/070703-02-linksincodelens.png "070703-02_LinksInCodeLens")

 **Liens utilisés dans la fenêtre contextuelle CodeLens**

 ![Liens utilisés comme commandes secondaires](../../extensibility/ux-guidelines/media/070703-03-linksassecondarycommands.png "070703-03_LinksAsSecondaryCommands")

 **Liens utilisés pour les commandes secondaires qui attirent trop l’attention sur les boutons**

### <a name="common-buttons"></a>Boutons courants

#### <a name="text"></a>Texte
 Suivez les instructions d’écriture dans [texte et terminologie de l’interface utilisateur](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology).

#### <a name="visual-style"></a>Style visuel

##### <a name="standard-dialogs"></a>Boîtes de dialogue standard
 La plupart des boutons dans Visual Studio s’affichent dans les boîtes de dialogue standard et ne doivent pas être stylisés. Ils doivent refléter l’apparence standard des boutons, comme indiqué par le système d’exploitation.

##### <a name="themed"></a>À thème
 Dans certains cas, les boutons peuvent être utilisés dans l’interface utilisateur avec des styles et ces boutons doivent être correctement mis en forme. Pour plus d’informations sur les contrôles à thème, consultez [boîtes de dialogue](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs) .

### <a name="special-buttons"></a>Boutons spéciaux

#### <a name="browse-buttons"></a>Parcourir... boutons
 **[Parcourir...]** les boutons sont utilisés dans les grilles, les boîtes de dialogue et les fenêtres outil et d’autres éléments d’interface utilisateur non modals. Ils affichent un sélecteur qui aide l’utilisateur à remplir une valeur dans un contrôle. Il existe deux variantes de ce bouton, long et Short.

 ![Bouton long &#91;parcourir... &#93;](../../extensibility/ux-guidelines/media/070703-04-browselong.gif "070703-04_BrowseLong")

 **Le bouton long [Parcourir...]**

 ![Les points de suspension&#45;uniquement &#91;bouton Parcourir... &#93;](../../extensibility/ux-guidelines/media/070703-05-browseshort.gif "070703-05_BrowseShort")

 **Bouton des points de suspension [...]**

 Quand utiliser le bouton de sélection de points de suspension uniquement :

- S’il y a plus d’un bouton long **[Browse...]** dans une boîte de dialogue, par exemple lorsque plusieurs champs permettent la navigation. Utilisez le bouton Short **[...]** pour chaque pour éviter les clés d’accès confuses créées par cette situation (**&parcourir** et **B&des lignes** dans la même boîte de dialogue).

- Dans une boîte de dialogue serrée, ou s’il n’y a pas de place raisonnable pour placer le bouton long.

- Si le bouton s’affiche dans un contrôle de grille.

  Instructions pour l’utilisation du bouton :

- N’utilisez pas de clé d’accès. Pour y accéder à l’aide du clavier, l’utilisateur doit effectuer une tabulation à partir du contrôle adjacent. Assurez-vous que l’ordre de tabulation est tel que le bouton Parcourir est placé immédiatement après le champ qu’il remplira. N’utilisez jamais de trait de soulignement en dessous de la première période.

- Définissez la propriété de **nom** Microsoft Active Accessibility (MSAA) sur **Parcourir...** (y compris les points de suspension) pour que les lecteurs d’écran le lisent comme « parcourir », et non pas « point-point-point » ni « période-période-période ». Pour les contrôles managés, cela signifie définir la propriété **AccessibleName** .

- N’utilisez jamais de bouton de sélection **[...]** pour tout sauf une action parcourir. Par exemple, si vous avez besoin d’un bouton **[nouveau...]** mais que vous n’avez pas suffisamment d’espace pour le texte, la boîte de dialogue doit être repensée.

##### <a name="sizing-and-spacing"></a>Dimensionnement et espacement
 ![Dimensionnement &#91;boutons Parcourir... &#93;](../../extensibility/ux-guidelines/media/070703-06-browsesizing.png "070703-06_BrowseSizing")

 **Dimensionnement des boutons [Parcourir...]**

 ![Espacement &#91;boutons Parcourir... &#93;](../../extensibility/ux-guidelines/media/070703-07-browsespacing.png "070703-07_BrowseSpacing")

 **Boutons espacement [Parcourir...]**

#### <a name="graphical-buttons"></a>Boutons graphiques
 Certains boutons doivent toujours utiliser une image graphique et n’incluent jamais de texte pour conserver de l’espace et éviter les problèmes de localisation. Ils sont souvent utilisés dans les sélecteurs de champs et dans d’autres listes pouvant être triées.

> [!NOTE]
> Les utilisateurs doivent passer de la touche Tab à ces boutons (il n’y a pas de clés d’accès). Placez-les dans un ordre raisonnable. Mappez la propriété Name du bouton à l’action qu’elle effectue afin que les lecteurs d’écran interprètent correctement l’action du bouton.

|Nom|Image|
|-|-|
|Ajouter|![Bouton graphique « Ajouter »](../../extensibility/ux-guidelines/media/070703-08-buttonadd.png "070703-08_ButtonAdd")|
|Supprimer|![Bouton graphique « Supprimer »](../../extensibility/ux-guidelines/media/070703-09-buttonremove.png "070703-09_ButtonRemove")|
|Ajouter tout|![Bouton graphique « Ajouter tout »](../../extensibility/ux-guidelines/media/070703-10-buttonaddall.png "070703-10_ButtonAddAll")|
|Supprimer tout|![Bouton graphique « Supprimer tout »](../../extensibility/ux-guidelines/media/070703-11-buttonremoveall.png "070703-11_ButtonRemoveAll")|
|Monter|![Bouton graphique « Monter »](../../extensibility/ux-guidelines/media/070703-12-buttonmoveup.png "070703-12_ButtonMoveUp")|
|Descendre|![Bouton graphique « Descendre »](../../extensibility/ux-guidelines/media/070703-13-buttonmovedown.png "070703-13_ButtonMoveDown")|
|DELETE|![Bouton graphique « Supprimer »](../../extensibility/ux-guidelines/media/070703-14-buttondelete.png "070703-14_ButtonDelete")|

##### <a name="sizing-and-spacing"></a>Dimensionnement et espacement
 Le dimensionnement des boutons graphiques est le même que pour la version abrégée du bouton **[Parcourir...]** (26x23 pixels) :

 ![Bouton avec et sans affichage de couleur transparente](../../extensibility/ux-guidelines/media/070703-15-graphicalbuttonspacing.png "070703-15_GraphicalButtonSpacing")

 **Apparence d’une image graphique sur le bouton, avec et sans couleur transparente affichée**

### <a name="hyperlinks"></a>Liens hypertexte
 Les liens hypertexte sont bien adaptés aux actions basées sur la navigation, telles que l’ouverture d’une rubrique d’aide, d’une boîte de dialogue modale ou d’un Assistant. Si un lien hypertexte est utilisé pour une commande, il doit toujours afficher une modification visible et perceptible de l’interface utilisateur. En général, les actions qui s’engagent sur une action (telles que Save, Cancel et Delete) sont mieux communiquées à l’aide d’un bouton.

#### <a name="writing-style"></a>Style d’écriture
 Suivez les [conseils Windows Desktop pour le texte de l’interface utilisateur](https://msdn.microsoft.com/library/windows/desktop/dn742478\(v=vs.85\).aspx). N’utilisez pas « en savoir plus sur », « en savoir plus sur » ou « obtenir de l’aide pour cette formulation ». Au lieu de cela, le texte du lien aide sur les expressions est la question principale ayant obtenu une réponse du contenu de l’aide. Par exemple, «**Comment faire ajouter un serveur au Explorateur de serveurs ?**»

#### <a name="visual-style"></a>Style visuel

- Les liens hypertexte doivent toujours utiliser [le service VSColor](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService). Si le style d’un lien hypertexte n’est pas correct, il clignote en rouge ou affiche une couleur différente après avoir été visité.

- N’incluez pas de soulignements à l’état de repos du contrôle, sauf si le lien est un fragment de phrase dans une phrase complète, par exemple dans un filigrane.

- Les traits de soulignement ne doivent pas apparaître au pointage. Au lieu de cela, le retour à l’utilisateur pour lequel le lien est actif est une légère modification de couleur et le curseur de lien approprié.

## <a name="tree-views"></a><a name="BKMK_TreeViews"></a>Arborescences

### <a name="overview"></a>Vue d’ensemble
 Les arborescences permettent d’organiser des listes complexes en groupes parent-enfant. Un utilisateur peut développer ou réduire des groupes parents pour afficher ou masquer des éléments enfants sous-jacents. Chaque élément d’une arborescence peut être sélectionné pour fournir une action supplémentaire.

 Cette rubrique traite de l’utilisation acceptable, de la conception appropriée et des fonctionnalités des arborescences.

#### <a name="in-this-topic"></a>Dans cette rubrique

- [Style visuel](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViewVisualStyle)

- [Interactions](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViewInteractions)

### <a name="visual-style"></a><a name="BKMK_TreeViewVisualStyle"></a>Style visuel

#### <a name="expanders"></a>Expanders
 Les contrôles d’arborescence doivent être conformes à la conception de l’Expander utilisée par Windows et Visual Studio. Chaque nœud utilise un contrôle Expander pour afficher ou masquer les éléments sous-jacents. L’utilisation d’un contrôle Expander offre une cohérence aux utilisateurs qui peuvent rencontrer des arborescences différentes dans Windows et Visual Studio.

 ![Contrôle d’une arborescence correcte](../../extensibility/ux-guidelines/media/070705-1-treeviewcorrect.png "070705-1_TreeViewCorrect")

 **Correct : style approprié du nœud d’arborescence à l’aide d’un contrôle Expander**

 ![Nœuds d’une arborescence incorrecte](../../extensibility/ux-guidelines/media/070705-2-treeviewincorrect1.png "070705-2_TreeViewIncorrect1")

 **Incorrect : style de nœud d’arborescence incorrect**

#### <a name="selection"></a>Sélection
 Lorsqu’un nœud est sélectionné dans l’arborescence, la surbrillance doit se développer jusqu’à la largeur totale du contrôle arborescence. Cela permet aux utilisateurs d’identifier clairement l’élément qu’ils ont sélectionné. Les couleurs de sélection doivent refléter le thème Visual Studio actuel.

 ![Contrôle d’une arborescence correcte](../../extensibility/ux-guidelines/media/070705-1-treeviewcorrect.png "070705-1_TreeViewCorrect")

 **Correct : la mise en surbrillance du nœud sélectionné s’ajuste à la largeur totale du contrôle TreeView.**

 ![Mise en surbrillance d’une arborescence incorrecte](../../extensibility/ux-guidelines/media/070705-3-treeviewincorrect2.png "070705-3_TreeViewIncorrect2")

 **Incorrect : la mise en surbrillance du nœud sélectionné ne correspond pas à la largeur totale du contrôle TreeView.**

#### <a name="icons"></a>Icônes
 Les icônes ne doivent être utilisées que dans les contrôles d’arborescence s’ils aident à identifier visuellement les différences entre les éléments. En général, les icônes doivent être utilisées uniquement dans des listes hétérogènes dans lesquelles les icônes contiennent des informations pour différencier les types d’éléments. Dans une liste homogène, l’utilisation d’icônes peut souvent être considérée comme un bruit et doit être évitée. Dans ce cas, l’icône de groupe (parent) peut communiquer le type d’éléments qu’elle contient. L’exception à cette règle serait si l’icône est dynamique et utilisée pour indiquer l’État.

#### <a name="scroll-bars"></a>Barres de défilement
 Les barres de défilement doivent toujours être masquées si le contenu s’ajuste au contrôle d’arborescence. Les barres de défilement sont autorisées à être masquées, ou semi-transparentes dans une fenêtre défilante et apparaissent lorsque la fenêtre contenant l’arborescence a le focus, ou au pointage de l’arborescence elle-même.

 ![Arborescence avec barres de défilement](../../extensibility/ux-guidelines/media/070705-4-scrollbars.png "070705-4_Scrollbars")

 **Les barres de défilement verticale et horizontale s’affichent, car le contenu a dépassé les limites du contrôle TreeView.**

### <a name="interactions"></a><a name="BKMK_TreeViewInteractions"></a>Relations

#### <a name="context-menus"></a>Les menus contextuels :
 Un nœud d’arborescence peut afficher des options de sous-menu dans un menu contextuel. En général, cela se produit lorsqu’un utilisateur clique avec le bouton droit sur un élément ou a appuyé sur la touche de menu d’un clavier Windows avec l’élément sélectionné. Il est important que le nœud gagne le focus et qu’il soit sélectionné. Cela permet à l’utilisateur d’identifier l’élément auquel le sous-menu appartient.

 ![Nœud sélectionné dans une arborescence et menu contextuel](../../extensibility/ux-guidelines/media/070705-5-contextmenu.png "070705-5_ContextMenu")

 **L’élément qui a généré le menu contextuel reçoit le focus pour notifier l’utilisateur de l’élément sélectionné.**

#### <a name="keyboard"></a>Clavier
 L’arborescence doit permettre de sélectionner des éléments et de développer/réduire des nœuds à l’aide du clavier. Cela garantit que la navigation répond à nos exigences en matière d’accessibilité.

##### <a name="tree-view-control"></a>Contrôle Tree View
 Les contrôles d’arborescence Visual Studio doivent suivre la navigation au clavier courante :

- **Flèche vers le haut :** Sélectionner des éléments en déplaçant l’arborescence

- **Flèche bas :** Sélectionner des éléments en déplaçant l’arborescence vers le dessous

- **Flèche droite :** Développer un nœud dans l’arborescence

- **Flèche gauche :** Réduire un nœud dans l’arborescence

- **Touche entrée :** Lancer, charger, exécuter l’élément sélectionné

##### <a name="trid-tree-view-and-grid-view"></a>Grid (arborescence et vue grille)
 Un contrôle Grid est un contrôle complexe qui contient une arborescence dans une grille. Le développement, la réduction et la navigation dans l’arborescence doivent respecter les mêmes commandes de clavier qu’une arborescence, avec les ajouts suivants :

- **Flèche droite :** Développez un nœud. Une fois le nœud développé, il doit continuer à naviguer jusqu’à la colonne la plus proche à droite. La navigation doit s’arrêter à la fin de la ligne.

- **Onglet :** Navigue jusqu’à la cellule la plus proche à droite.  À la fin de la ligne, la navigation continue jusqu’à la ligne suivante.

- **MAJ + TAB :** Navigue jusqu’à la cellule la plus proche sur la gauche.  Au début de la ligne, la navigation se poursuit jusqu’à la cellule la plus à droite dans la ligne précédente.

  ![Contrôle Grid dans Visual Studio](../../extensibility/ux-guidelines/media/070705-6-trid.png "070705-6_Trid")

  **Contrôle Grid dans Visual Studio**
