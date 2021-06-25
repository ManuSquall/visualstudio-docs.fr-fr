---
title: Modèles de contrôle courants pour Visual Studio | Microsoft Docs
description: Découvrez comment les contrôles communs de Visual Studio suivent les instructions d’interaction avec les ordinateurs de bureau Windows et les situations spéciales qui augmentent ces instructions.
ms.custom: SEO-VS-2020
ms.date: 04/26/2017
ms.topic: reference
ms.assetid: 3e893949-6398-42f1-9eab-a8d8c2b7f02d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 12d514bdc0aa37598ad57e0466bf57ba75ed2601
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899301"
---
# <a name="common-control-patterns-for-visual-studio"></a>Modèles de contrôle courants pour Visual Studio
## <a name="common-controls"></a><a name="BKMK_CommonControls"></a> Contrôles communs

### <a name="overview"></a>Vue d’ensemble
Les contrôles communs constituent la majeure partie de l’interface utilisateur dans Visual Studio. La plupart des contrôles courants utilisés dans l’interface Visual Studio doivent respecter les [instructions relatives à l’interaction avec les ordinateurs de bureau Windows](/windows/desktop/uxguide/controls). Cette rubrique est spécifique à Visual Studio et couvre des situations particulières ou des détails qui augmentent ces instructions Windows.

#### <a name="common-controls-in-this-topic"></a>Contrôles communs dans cette rubrique

- [Barres de défilement](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_Scrollbars)

- [Champs d’entrée](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_InputFields)

- [Zones de liste déroulante et listes déroulantes](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ComboBoxesAndDropDowns)

- [Cases à cocher](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CheckBoxes)

- [Cases d’option](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_RadioButtons)

- [Frames de groupe](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_GroupFrames)

- [Contrôles de texte](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)

- [Boutons et liens hypertexte](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)

- [Arborescences](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViews)

#### <a name="visual-style"></a>Style de visuel
La première chose à prendre en compte lorsque vous appliquez un style aux contrôles est de savoir si les contrôles seront utilisés dans l’interface utilisateur. Les contrôles dans l’interface utilisateur standard sont des interfaces utilisateur sans thème et doivent suivre le [style de bureau Windows normal](/windows/desktop/uxguide/controls), ce qui signifie qu’ils ne sont pas remodèleés et doivent apparaître dans leur apparence de contrôle par défaut.

- **Boîtes de dialogue standard (utilitaire) :** pas à thème. Ne pas recréer de modèle. Utilisez les valeurs par défaut du style de contrôle de base.

- **Fenêtres outil, éditeurs de documents, aires de conception et boîtes de dialogue à thème :** Utilisez l’apparence spécialisée à thème à l’aide du service de couleurs.

### <a name="scroll-bars"></a><a name="BKMK_Scrollbars"></a> Barres de défilement
 Les barres de défilement doivent suivre [les modèles d’interaction courants pour les barres de défilement Windows](/windows/desktop/Controls/about-scroll-bars) , sauf si elles sont complétées par des informations de contenu, comme dans l’éditeur de code.

### <a name="input-fields"></a><a name="BKMK_InputFields"></a> Champs d’entrée
 Pour le comportement d’interaction standard, suivez les [instructions du bureau Windows pour les zones de texte](/windows/desktop/uxguide/ctrl-text-boxes).

#### <a name="visual-style"></a>Style de visuel

- Les champs d’entrée ne doivent pas être stylisés dans les boîtes de dialogue d’utilitaire. Utilisez le style de base intrinsèque au contrôle.

- Les champs d’entrée à thème doivent uniquement être utilisés dans des boîtes de dialogue et des fenêtres outil.

#### <a name="specialized-interactions"></a>Interactions spécialisées

- Les champs en lecture seule présentent un arrière-plan gris (désactivé) mais un premier plan par défaut (actif).

- Les champs obligatoires doivent comporter des **\<Required>** filigranes. Vous ne devez pas modifier la couleur de l’arrière-plan, sauf dans de rares situations.

- Validation des erreurs : voir [notifications et progression pour Visual Studio](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)

- Les champs d’entrée doivent être dimensionnés pour s’ajuster au contenu, pas pour s’ajuster à la largeur de la fenêtre dans laquelle ils sont affichés, ni correspondre arbitrairement à la longueur d’un champ long, comme un chemin d’accès. La longueur peut indiquer à l’utilisateur des limitations quant au nombre de caractères autorisés dans le champ.

     ![Longueur de champ d’entrée incorrecte : il est peu probable que le nom soit ce long.](../../extensibility/ux-guidelines/media/0707-01_incorrectinputfieldcontrol.png "0707-01_IncorrectInputFieldControl")<br />Longueur de champ d’entrée incorrecte : il est peu probable que le nom soit ce long.

     ![Longueur du champ d’entrée correcte : le champ d’entrée est une largeur raisonnable pour le contenu attendu.](../../extensibility/ux-guidelines/media/0707-02_correctinputfieldcontrol.png "0707-02_CorrectInputFieldControl")<br />Longueur du champ d’entrée correcte : le champ d’entrée est une largeur raisonnable pour le contenu attendu.

### <a name="combo-boxes-and-drop-down-lists"></a><a name="BKMK_ComboBoxesAndDropDowns"></a> Zones de liste déroulante et listes déroulantes
Pour le comportement d’interaction standard, suivez les [instructions du bureau Windows pour les listes déroulantes et les zones de liste](/windows/desktop/uxguide/ctrl-drop)déroulante.

#### <a name="visual-style"></a>Style de visuel

- Dans les boîtes de dialogue de l’utilitaire, ne remodèleez pas le contrôle. Utilisez le style de base intrinsèque au contrôle.

- Dans l’interface utilisateur à thème, les zones de liste déroulante et les listes déroulantes suivent les thèmes standard pour les contrôles.

#### <a name="layout"></a>Layout
Les zones de liste modifiable et les listes déroulantes doivent être dimensionnées pour s’ajuster au contenu, et non pour s’ajuster à la largeur de la fenêtre dans laquelle elles sont affichées, ni pour correspondre arbitrairement à la longueur d’un champ long, comme un chemin d’accès.

![Incorrect : la largeur de liste déroulante est trop longue pour le contenu qui sera affiché.](../../extensibility/ux-guidelines/media/0707-03_incorrectdropdownlayout.png "0707-03_IncorrectDropDownLayout")<br />Incorrect : la largeur de liste déroulante est trop longue pour le contenu qui sera affiché.

![Correct : la liste déroulante est dimensionnée pour permettre la croissance de la traduction, mais pas inutilement longue.](../../extensibility/ux-guidelines/media/0707-04_correctdropdownlayout.png "0707-04_CorrectDropDownLayout")<br />Correct : la liste déroulante est dimensionnée pour permettre la croissance de la traduction, mais pas inutilement longue.

### <a name="check-boxes"></a><a name="BKMK_CheckBoxes"></a> Cases à cocher
Pour le comportement d’interaction standard, suivez les [instructions du bureau Windows pour les cases à cocher](/windows/desktop/uxguide/ctrl-check-boxes).

#### <a name="visual-style"></a>Style de visuel

- Dans les boîtes de dialogue de l’utilitaire, ne remodèleez pas le contrôle. Utilisez le style de base intrinsèque au contrôle.

- Dans l’interface utilisateur à thème, les cases à cocher suivent les thèmes standard pour les contrôles.

#### <a name="specialized-interactions"></a>Interactions spécialisées

- L’interaction avec une case à cocher ne doit jamais dépiler une boîte de dialogue ou accéder à une autre zone.

- Aligner les cases à cocher avec la ligne de base de la première ligne de texte.

     ![Incorrect : la case à cocher est centrée sur le texte.](../../extensibility/ux-guidelines/media/0707-05_incorrectcheckboxalign.png "0707-05_IncorrectCheckBoxAlign")<br />Incorrect : la case à cocher est centrée sur le texte.

     ![Correct : la case à cocher est alignée sur la première ligne du texte.](../../extensibility/ux-guidelines/media/0707-06_correctcheckboxalign.png "0707-06_CorrectCheckBoxAlign")<br />Correct : la case à cocher est alignée sur la première ligne du texte.

### <a name="radio-buttons"></a><a name="BKMK_RadioButtons"></a> Cases d’option
Pour le comportement d’interaction standard, suivez les [instructions relatives au bureau Windows pour les cases d’option](/windows/desktop/uxguide/ctrl-radio-buttons).

#### <a name="visual-style"></a>Style de visuel
Dans les boîtes de dialogue d’utilitaire, n’appliquez pas de style aux cases d’option. Utilisez le style de base intrinsèque au contrôle.

#### <a name="specialized-interactions"></a>Interactions spécialisées
Il n’est pas nécessaire d’utiliser un cadre de groupe pour encadrer les choix radio, sauf si vous devez maintenir la distinction entre les groupes dans une disposition serrée.

### <a name="group-frames"></a><a name="BKMK_GroupFrames"></a> Frames de groupe
Pour le comportement d’interaction standard, suivez les [instructions du bureau Windows pour les cadres de groupe](/windows/desktop/uxguide/ctrl-group-boxes).

#### <a name="visual-style"></a>Style de visuel
Dans les boîtes de dialogue de l’utilitaire, ne pas styliser les cadres de groupe. Utilisez le style de base intrinsèque au contrôle.

#### <a name="layout"></a>Layout

- Il n’est pas nécessaire d’utiliser un cadre de groupe pour encadrer les choix radio, sauf si vous devez maintenir la distinction entre les groupes dans une disposition serrée.

- N’utilisez jamais un cadre de groupe pour un seul contrôle.

- Il est parfois acceptable d’utiliser une règle horizontale au lieu d’un conteneur de cadre de groupe.

## <a name="text-controls"></a><a name="BKMK_TextControls"></a> Contrôles de texte

### <a name="static-text-fields"></a>Champs de texte statiques

Un champ de texte statique présente des informations en lecture seule et ne peut pas être sélectionné par l’utilisateur. Évitez de l’utiliser pour tout texte que l’utilisateur peut vouloir copier dans le presse-papiers. Toutefois, le texte statique en lecture seule peut changer pour refléter une modification de l’État. Dans l’exemple ci-dessous, le texte statique du nom de sortie sous le groupe d’informations change pour refléter toutes les modifications apportées à la zone de texte espace de noms racine au-dessus de celle-ci.

Il existe deux façons d’afficher des informations textuelles statiques.

Le texte statique peut être autonome dans une boîte de dialogue sans relation contenant-contenu en l’absence de conflit de regroupement. Déterminez si les lignes supplémentaires d’une zone sont vraiment nécessaires. Par exemple, l’affichage d’un chemin d’accès de répertoire sous une section créée par une ligne de groupe, comme indiqué ci-dessous :

![Informations textuelles statiques dans les contrôles de texte](../../extensibility/ux-guidelines/media/DisplayingStaticText.png "DisplayingStaticText.png")<br />Informations textuelles statiques dans les contrôles de texte

Dans une boîte de dialogue dans laquelle d’autres zones groupées existent et la relation contenant-contenu des informations aiderait à améliorer la lisibilité, et quand une section peut être masquée ou affichée (comme dans le volet **fenêtre Propriétés** Description) ou si vous souhaitez être cohérente avec une interface utilisateur similaire, placez le texte statique dans une zone. Cette zone de groupe doit être une seule règle et comporter la couleur `ButtonShadow` suivante :

![Texte statique dans le Fenêtre Propriétés](../../extensibility/ux-guidelines/media/PropertiesWindow.png "PropertiesWindow.png")<br />Texte statique dans le Fenêtre Propriétés

### <a name="read-only-text-box"></a>Zone de texte en lecture seule

Cela permet à l’utilisateur de sélectionner le texte à l’intérieur du champ, mais pas de le modifier. Ces zones de texte sont encadrées par le biseau 3D habituel avec un `ButtonShadow` remplissage.

Une zone de texte peut devenir active (modifiable) quand un utilisateur modifie un contrôle associé, par exemple en activant/désactivant une case à cocher ou en sélectionnant/désélectionnant une case d’option. Par exemple, dans la **page &gt; Options des outils** ci-dessous, la zone de texte **page** d’affichage devient active lorsque la case à cocher **utiliser la valeur par défaut** est désactivée.

![Zone de texte en lecture seule, indiquant les États inactifs et actifs](../../extensibility/ux-guidelines/media/ReadOnlyTextBox.png "ReadOnlyTextBox.png")<br />Zone de texte en lecture seule, indiquant les États inactifs et actifs

### <a name="using-text-in-dialogs"></a>Utilisation de texte dans les boîtes de dialogue

Instructions clés pour le texte des boîtes de dialogue :

- Les étiquettes pour les zones de texte, les zones de liste et les cadres dans les boîtes de dialogue sans thème commencent par un verbe, ont une majuscule initiale sur le premier mot uniquement et se terminent par un signe deux-points.

    > Les contrôles de texte dans les boîtes de dialogue à thème suivent les [recommandations Windows Desktop UX](/windows/desktop/uxguide/top-violations) et ne prennent pas de signe de ponctuation finale, à l’exception des points d’interrogation dans les liens d’aide.

- Les étiquettes des cases à cocher et des cases d’option commencent par un verbe, une majuscule initiale sur le premier mot uniquement et n’ont pas de ponctuation finale.

- Les étiquettes pour les boutons, les menus, les éléments de menu et les onglets ont des majuscules initiales pour chaque mot (cas de titre).

- La terminologie des étiquettes doit être cohérente avec les étiquettes similaires dans d’autres boîtes de dialogue.

- Si possible, utilisez un rédacteur ou un éditeur pour écrire ou approuver le texte avant qu’il n’accède au développeur pour l’implémentation.

- Tous les contrôles doivent avoir des étiquettes, sauf dans des circonstances particulières dans lesquelles la tabulation est suffisante.
Utilisez le texte d’assistance si nécessaire.

### <a name="helper-text"></a>Texte d’assistance

Inclus dans les boîtes de dialogue pour aider l’utilisateur à comprendre l’objectif de la boîte de dialogue ou à indiquer l’action à entreprendre. Le texte d’assistance doit être utilisé uniquement lorsque cela est nécessaire pour éviter d’encombrer des boîtes de dialogue simples. Les deux variantes du texte d’assistance sont la boîte de dialogue et le filigrane.

Suivez les emplacements communs du texte d’assistance et soyez sélectif dans l’introduction de nouvelles zones. Les scénarios courants pour le texte d’assistance sont les suivants :

- Texte d’assistance dans les boîtes de dialogue, pour fournir une direction supplémentaire sur l’interaction avec une boîte de dialogue complexe.

- Texte de filigrane dans les fenêtres outil vides ou les boîtes de dialogue pour expliquer pourquoi aucun contenu n’est visible.

- Un volet de description, comme au bas de la **fenêtre Propriétés**.

- Texte de filigrane dans un éditeur vide, pour expliquer l’action que l’utilisateur doit effectuer pour commencer.

### <a name="dialog-helper-text"></a>Texte d’assistance de boîte de dialogue

Un concepteur d’expérience utilisateur peut vous aider à déterminer quand le texte d’assistance est approprié. Le concepteur peut définir où s’affiche le texte d’assistance, ainsi que son contenu général. L’assistance de l’utilisateur peut écrire/modifier le texte réel.

### <a name="watermarks"></a>Filigranes

Les boîtes de dialogue tirent parti de directives relatives aux filigranes légèrement différentes. Comme une boîte de dialogue peut s’afficher comme étant occupée avec de nombreux éléments d’interface utilisateur (étiquettes, texte d’indication, boutons et autres contrôles de conteneur avec du texte), en particulier quand ceux-ci apparaissent en noir, les filigranes sont plus performants en gris foncé (VSColor : `ButtonShadow` ). En général, un filigrane apparaît à l’intérieur d’un contrôle comme une zone de liste avec un arrière-plan blanc (VSColor : `Window` ).

- Le texte apparaît en gris foncé (VSColor : `ButtonShadow` ). Toutefois, si le filigrane apparaît sur un arrière-plan de couleur gris moyen ou autre (VSColor : `ButtonFace` ) et qu’il y a un problème de lisibilité, utilisez du texte noir (VSColor : `WindowText` ).

- Les filigranes peuvent être centrés ou alignés à gauche. Appliquez des règles de conception standard lors de la prise de décisions d’alignement. Le filigrane ne peut pas être sélectionné sur l’arrière-plan.

![Exemple de texte de filigrane](../../extensibility/ux-guidelines/media/WatermarkTextExample.gif)<br />Exemple de texte de filigrane

### <a name="context-specific-dynamic-text"></a>Texte spécifique au contexte (dynamique)

Le texte dynamique peut être utilisé de deux façons dans une boîte de dialogue ou une interface utilisateur non modale : comme une étiquette dynamique ou comme du contenu dynamique.

- Étiquette dynamique : une utilisation courante du texte dynamique se trouve dans des panneaux descriptifs qui fournissent plus d’informations pour l’élément sélectionné, comme dans une boîte de dialogue qui contient une liste d’éléments et de propriétés pour les éléments affichés dans une grille à droite. L’étiquette de la grille des propriétés peut être dynamique, de sorte que lorsqu’un élément est sélectionné à gauche, la grille à droite affiche des informations sur cet élément spécifique.

- Texte dynamique : peut être utile dans les cas où vous devez afficher des informations spécifiques et non pas des informations générales de cette manière, mais il est préférable de ne pas surcharger.

Si vous souhaitez que les utilisateurs aient la possibilité de copier les informations, le texte dynamique doit se trouver dans un champ de texte en lecture seule.

## <a name="buttons-and-hyperlinks"></a><a name="BKMK_ButtonsAndHyperlinks"></a> Boutons et liens hypertexte

### <a name="overview"></a>Vue d’ensemble
Les boutons et les contrôles de liens (liens hypertexte) doivent suivre les [instructions du bureau Windows de base sur les liens hypertexte](/windows/desktop/uxguide/ctrl-links) pour l’utilisation, le libellé, le dimensionnement et l’espacement.

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
![Liens de commande utilisés dans la barre d’informations après un message d’État](../../extensibility/ux-guidelines/media/070703-01_commandlinkinfobar.png "070703-01_CommandLinkInfobar")<br />Liens de commande utilisés dans la barre d’informations après un message d’État

![Liens utilisés dans la fenêtre contextuelle CodeLens](../../extensibility/ux-guidelines/media/070703-02_linksincodelens.png "070703-02_LinksInCodeLens")<br />Liens utilisés dans la fenêtre contextuelle CodeLens

![Liens utilisés pour les commandes secondaires qui attirent trop l’attention sur les boutons](../../extensibility/ux-guidelines/media/070703-03_linksassecondarycommands.png "070703-03_LinksAsSecondaryCommands")<br />Liens utilisés pour les commandes secondaires qui attirent trop l’attention sur les boutons

### <a name="common-buttons"></a>Boutons courants

#### <a name="text"></a>Texte
Suivez les instructions d’écriture dans [texte et terminologie de l’interface utilisateur](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology).

#### <a name="visual-style"></a>Style de visuel

##### <a name="standard-unthemed"></a>Standard (pas à thème)
La plupart des boutons dans Visual Studio s’affichent dans les boîtes de dialogue de l’utilitaire et ne doivent pas être stylisés. Ils doivent refléter l’apparence standard des boutons, comme indiqué par le système d’exploitation.

##### <a name="themed"></a>À thème
Dans certains cas, les boutons peuvent être utilisés dans l’interface utilisateur avec des styles et ces boutons doivent être correctement mis en forme. Pour plus d’informations sur les contrôles à thème, consultez [boîtes de dialogue](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs) .

### <a name="special-buttons"></a>Boutons spéciaux

#### <a name="browse-buttons"></a>Parcourir... boutons
**[Parcourir...]** les boutons sont utilisés dans les grilles, les boîtes de dialogue et les fenêtres outil et d’autres éléments d’interface utilisateur non modals. Ils affichent un sélecteur qui aide l’utilisateur à remplir une valeur dans un contrôle. Il existe deux variantes de ce bouton, long et Short.

![Le bouton long [Parcourir...]](../../extensibility/ux-guidelines/media/070703-04_browselong.gif "070703-04_BrowseLong")<br />Le bouton long [Parcourir...]

![Bouton des points de suspension [...]](../../extensibility/ux-guidelines/media/070703-05_browseshort.gif "070703-05_BrowseShort")<br />Bouton des points de suspension [...]

Quand utiliser le bouton de sélection de points de suspension uniquement :

- S’il y a plus d’un bouton long **[Browse...]** dans une boîte de dialogue, comme lorsque plusieurs champs permettent de naviguer. Utilisez le bouton Short **[...]** pour chaque pour éviter les clés d’accès confuses créées par cette situation (**&parcourir** et **B&des lignes** dans la même boîte de dialogue).

- Dans une boîte de dialogue serrée, ou s’il n’y a pas de place raisonnable pour placer le bouton long.

- Si le bouton s’affiche dans un contrôle de grille.

Instructions pour l’utilisation du bouton :

- N’utilisez pas de clé d’accès. Pour y accéder à l’aide du clavier, l’utilisateur doit effectuer une tabulation à partir du contrôle adjacent. Assurez-vous que l’ordre de tabulation est tel que le bouton Parcourir est placé immédiatement après le champ qu’il remplira. N’utilisez jamais de trait de soulignement en dessous de la première période.

- Définissez la propriété de **nom** Microsoft Active Accessibility (MSAA) sur **Parcourir...** (y compris les points de suspension) pour que les lecteurs d’écran le lisent comme « parcourir », et non pas « point-point-point » ni « période-période-période ». Pour les contrôles managés, cela signifie définir la propriété **AccessibleName** .

- N’utilisez jamais de bouton de sélection **[...]** pour tout sauf une action parcourir. Par exemple, si vous avez besoin d’un bouton **[nouveau...]** mais que vous n’avez pas suffisamment d’espace pour le texte, la boîte de dialogue doit être repensée.

##### <a name="sizing-and-spacing"></a>Dimensionnement et espacement
![Boutons de dimensionnement [Parcourir...] : la version standard est 75x23 pixels, la version abrégée est 26x23 pixels](../../extensibility/ux-guidelines/media/070703-06_browsesizing.png "070703-06_BrowseSizing")<br />Bouton de dimensionnement [Parcourir...]

![Boutons espacement [Parcourir...] : espacement entre le contrôle associé et le bouton Parcourir standard 7 pixels, espacement entre le contrôle associé et le bouton Parcourir de petite taille 5 pixels](../../extensibility/ux-guidelines/media/070703-07_browsespacing.png "070703-07_BrowseSpacing")<br />Bouton d'espacement [Parcourir...]

#### <a name="graphical-buttons"></a>Boutons graphiques
Certains boutons doivent toujours utiliser une image graphique et n’incluent jamais de texte pour conserver de l’espace et éviter les problèmes de localisation. Ils sont souvent utilisés dans les sélecteurs de champs et dans d’autres listes pouvant être triées.

> [!NOTE]
> Les utilisateurs doivent passer de la touche Tab à ces boutons (il n’y a pas de clés d’accès). Placez-les dans un ordre raisonnable. Mappez la `name` propriété du bouton à l’action qu’il effectue afin que les lecteurs d’écran interprètent correctement l’action du bouton.

| Fonction | Bouton |
| --- | --- |
| Ajouter | ![Bouton graphique « Ajouter »](../../extensibility/ux-guidelines/media/070703-08_buttonadd.png "070703-08_ButtonAdd") |
| Supprimer | ![Bouton graphique « Supprimer »](../../extensibility/ux-guidelines/media/070703-09_buttonremove.png "070703-09_ButtonRemove") |
| Ajouter tout | ![Bouton graphique « Ajouter tout »](../../extensibility/ux-guidelines/media/070703-10_buttonaddall.png "070703-10_ButtonAddAll") |
| Supprimer tout | ![Bouton graphique « Supprimer tout »](../../extensibility/ux-guidelines/media/070703-11_buttonremoveall.png "070703-11_ButtonRemoveAll") |
| Monter | ![Bouton graphique « Monter »](../../extensibility/ux-guidelines/media/070703-12_buttonmoveup.png "070703-12_ButtonMoveUp") |
| Descendre | ![Bouton graphique « Descendre »](../../extensibility/ux-guidelines/media/070703-13_buttonmovedown.png "070703-13_ButtonMoveDown") |
| DELETE | ![Bouton graphique « Supprimer »](../../extensibility/ux-guidelines/media/070703-14_buttondelete.png "070703-14_ButtonDelete") |

##### <a name="sizing-and-spacing"></a>Dimensionnement et espacement
Le dimensionnement des boutons graphiques est le même que pour la version abrégée du bouton **[Parcourir...]** (26x23 pixels) :

![Apparence d’une image graphique sur le bouton, avec et sans couleur transparente affichée](../../extensibility/ux-guidelines/media/070703-15_graphicalbuttonspacing.png "070703-15_GraphicalButtonSpacing")<br />Apparence d’une image graphique sur le bouton, avec et sans couleur transparente affichée

### <a name="hyperlinks"></a>Liens hypertexte
Les liens hypertexte sont bien adaptés aux actions basées sur la navigation, telles que l’ouverture d’une rubrique d’aide, d’une boîte de dialogue modale ou d’un Assistant. Si un lien hypertexte est utilisé pour une commande, il doit toujours afficher une modification visible et perceptible de l’interface utilisateur. En général, les actions qui s’engagent sur une action (telles que Save, Cancel et Delete) sont mieux communiquées à l’aide d’un bouton.

#### <a name="writing-style"></a>Style d’écriture
Suivez les [conseils Windows Desktop pour le texte de l’interface utilisateur](/windows/desktop/uxguide/text-ui). N’utilisez pas « en savoir plus sur », « en savoir plus sur » ou « obtenir de l’aide pour cette formulation ». Au lieu de cela, le texte du lien aide sur les expressions est la question principale ayant obtenu une réponse du contenu de l’aide. Par exemple, «**Comment faire ajouter un serveur au Explorateur de serveurs ?**»

#### <a name="visual-style"></a>Style de visuel

- Les liens hypertexte doivent toujours utiliser [le service VSColor](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService). Si le style d’un lien hypertexte n’est pas correct, il clignote en rouge ou affiche une couleur différente après avoir été visité.

- N’incluez pas de soulignements à l’état de repos du contrôle, sauf si le lien est un fragment de phrase dans une phrase complète, comme dans un filigrane.

- Les traits de soulignement ne doivent pas apparaître au pointage. Au lieu de cela, le retour à l’utilisateur pour lequel le lien est actif est une légère modification de couleur et le curseur de lien approprié.

## <a name="tree-views"></a><a name="BKMK_TreeViews"></a> Arborescences

Les arborescences permettent d’organiser des listes complexes en groupes parent-enfant. Un utilisateur peut développer ou réduire des groupes parents pour afficher ou masquer des éléments enfants sous-jacents. Chaque élément d’une arborescence peut être sélectionné pour fournir une action supplémentaire.

### <a name="tree-view-visual-style"></a><a name="BKMK_TreeViewVisualStyle"></a> Style visuel de l’arborescence

#### <a name="expanders"></a>Expanders
Les contrôles d’arborescence doivent être conformes à la conception de l’Expander utilisée par Windows et Visual Studio. Chaque nœud utilise un contrôle Expander pour afficher ou masquer les éléments sous-jacents. L’utilisation d’un contrôle Expander offre une cohérence aux utilisateurs qui peuvent rencontrer des arborescences différentes dans Windows et Visual Studio.

![Correct : style approprié du nœud d’arborescence à l’aide d’un contrôle Expander](../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705-1_TreeViewCorrect")<br />Correct : style approprié du nœud d’arborescence à l’aide d’un contrôle Expander

![Incorrect : style de nœud d’arborescence incorrect](../../extensibility/ux-guidelines/media/070705-2_treeviewincorrect1.png "070705-2_TreeViewIncorrect1")<br />Incorrect : style de nœud d’arborescence incorrect

#### <a name="selection"></a>Sélection
Lorsqu’un nœud est sélectionné dans l’arborescence, la surbrillance doit se développer jusqu’à la largeur totale du contrôle arborescence. Cela permet aux utilisateurs d’identifier clairement l’élément qu’ils ont sélectionné. Les couleurs de sélection doivent refléter le thème Visual Studio actuel.

![Correct : la mise en surbrillance du nœud sélectionné s’ajuste à la largeur totale du contrôle TreeView.](../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705-1_TreeViewCorrect")<br />Correct : la mise en surbrillance du nœud sélectionné s’ajuste à la largeur totale du contrôle TreeView.

![Incorrect : la mise en surbrillance du nœud sélectionné ne correspond pas à la largeur totale du contrôle TreeView.](../../extensibility/ux-guidelines/media/070705-3_treeviewincorrect2.png "070705-3_TreeViewIncorrect2")<br />Incorrect : la mise en surbrillance du nœud sélectionné ne correspond pas à la largeur totale du contrôle TreeView.

#### <a name="icons"></a>Icônes
Les icônes ne doivent être utilisées que dans les contrôles d’arborescence s’ils aident à identifier visuellement les différences entre les éléments. En général, les icônes doivent être utilisées uniquement dans des listes hétérogènes dans lesquelles les icônes contiennent des informations pour différencier les types d’éléments. Dans une liste homogène, l’utilisation d’icônes peut souvent être considérée comme un bruit et doit être évitée. Dans ce cas, l’icône de groupe (parent) peut communiquer le type d’éléments qu’elle contient. L’exception à cette règle serait si l’icône est dynamique et utilisée pour indiquer l’État.

#### <a name="scroll-bars"></a>Barres de défilement
Les barres de défilement doivent toujours être masquées si le contenu s’ajuste au contrôle d’arborescence. Les barres de défilement sont autorisées à être masquées, ou semi-transparentes dans une fenêtre défilante et apparaissent lorsque la fenêtre contenant l’arborescence a le focus, ou au pointage de l’arborescence elle-même.

![Les barres de défilement verticale et horizontale s’affichent, car le contenu a dépassé les limites du contrôle TreeView.](../../extensibility/ux-guidelines/media/070705-4_scrollbars.png "070705-4_Scrollbars")<br />Les barres de défilement verticale et horizontale s’affichent, car le contenu a dépassé les limites du contrôle TreeView.

### <a name="tree-view-interactions"></a><a name="BKMK_TreeViewInteractions"></a> Interactions de l’arborescence

#### <a name="context-menus"></a>Menu contextuels
Un nœud d’arborescence peut afficher des options de sous-menu dans un menu contextuel. En général, cela se produit lorsqu’un utilisateur clique avec le bouton droit sur un élément ou a appuyé sur la touche de menu d’un clavier Windows avec l’élément sélectionné. Il est important que le nœud gagne le focus et qu’il soit sélectionné. Cela permet à l’utilisateur d’identifier l’élément auquel le sous-menu appartient.

![L’élément qui a généré le menu contextuel reçoit le focus pour notifier l’utilisateur de l’élément sélectionné.](../../extensibility/ux-guidelines/media/070705-5_contextmenu.png "070705-5_ContextMenu")<br />L’élément qui a généré le menu contextuel reçoit le focus pour notifier l’utilisateur de l’élément sélectionné.

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

![Contrôle Grid dans Visual Studio](../../extensibility/ux-guidelines/media/070705-6_trid.png "070705-6_Trid")<br />Contrôle Grid dans Visual Studio
