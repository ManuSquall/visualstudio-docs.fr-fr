---
title: Les modèles de contrôle courants pour Visual Studio | Microsoft Docs
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: 3e893949-6398-42f1-9eab-a8d8c2b7f02d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4cc9b917210acb92b5db436c54c777f9f55f663b
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56704993"
---
# <a name="common-control-patterns-for-visual-studio"></a>Modèles de contrôle courants pour Visual Studio
##  <a name="BKMK_CommonControls"></a> Contrôles communs

### <a name="overview"></a>Vue d'ensemble
Contrôles communs constituent la majeure partie de l’interface utilisateur dans Visual Studio. Contrôles les plus courants utilisés dans l’interface de Visual Studio doivent suivre le [directives d’interaction de Windows Desktop](/windows/desktop/uxguide/controls). Cette rubrique est spécifique à Visual Studio et couvre des situations particulières ou des détails augmentent ces instructions de Windows.

#### <a name="common-controls-in-this-topic"></a>Contrôles communs dans cette rubrique

-   [Barres de défilement](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_Scrollbars)

-   [Champs d’entrée](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_InputFields)

-   [Zones de liste déroulante et les listes déroulantes](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ComboBoxesAndDropDowns)

-   [Cases à cocher](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CheckBoxes)

-   [Cases d’option](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_RadioButtons)

-   [Images de groupe](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_GroupFrames)

-   [Contrôles de texte](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)

-   [Boutons et des liens hypertexte](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)

-   [Vues de l’arborescence](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViews)

#### <a name="visual-style"></a>Style visuel
La première chose à prendre en compte lors de la stylisation de contrôles est que les contrôles seront utilisés dans l’interface utilisateur à thème. Contrôles dans l’interface utilisateur standard sont l’interface utilisateur sans thème et doivent respecter [style normal de Windows Desktop](/windows/desktop/uxguide/controls), ce qui signifie qu’ils ne sont pas re-basé sur un modèle et qu’il doivent apparaître dans leur apparence de contrôle par défaut.

-   **Boîtes de dialogue standard (utilitaire) :** pas à thème. Ne pas re-template. Utilisez les valeurs par défaut du style de contrôle de base.

-   **Fenêtres Outil, les éditeurs de document, les aires de conception et les boîtes de dialogue à thème :** Utilisez spécialisé apparence à thème à l’aide du service de couleur.

###  <a name="BKMK_Scrollbars"></a> Barres de défilement
 Barres de défilement doivent suivre [modèles courants d’interaction pour Windows les barres de défilement](/windows/desktop/Controls/about-scroll-bars) , sauf si elles sont augmentées avec les informations de contenu, comme dans l’éditeur de code.

###  <a name="BKMK_InputFields"></a> Champs d’entrée
 Pour le comportement de l’interaction typique, suivez le [instructions Windows Desktop pour les zones de texte](/windows/desktop/uxguide/ctrl-text-boxes).

#### <a name="visual-style"></a>Style visuel

-   Champs d’entrée ne doit pas être un style dans les boîtes de dialogue utilitaire. Utiliser le style de base intrinsèque au contrôle.

-   Les champs d’entrée à thème doivent uniquement servir dans les boîtes de dialogue à thème et des fenêtres Outil.

#### <a name="specialized-interactions"></a>Interactions spécialisées

-   Champs en lecture seule aura un arrière-plan gris (désactivé), mais de premier plan par défaut (actif).

-   Requis champs doivent avoir  **\<requis >** en tant que filigranes en leur sein. Vous ne devez pas modifier la couleur d’arrière-plan, sauf dans de rares cas.

-   Validation des erreurs : Consultez [Notifications et progression pour Visual Studio](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)

-   Champs d’entrée doivent être dimensionnées en fonction du contenu, ne pas à la largeur de la fenêtre dans lequel elles sont affichées, ni d’arbitrairement correspond à la longueur d’un champ long, par exemple, un chemin d’accès. Longueur peut être une indication à l’utilisateur de limitations concernant le nombre de caractères est autorisé dans le champ.

     ![Longueur de champ d’entrée incorrecte : il est peu probable que le nom sera ce long. ](../../extensibility/ux-guidelines/media/0707-01_incorrectinputfieldcontrol.png "0707-01_IncorrectInputFieldControl")<br />Longueur de champ d’entrée incorrecte : il est peu probable que le nom sera ce long.

     ![Corriger la longueur de champ d’entrée : le champ d’entrée est une largeur raisonnable pour le contenu attendu. ](../../extensibility/ux-guidelines/media/0707-02_correctinputfieldcontrol.png "0707-02_CorrectInputFieldControl")<br />Corriger la longueur de champ d’entrée : le champ d’entrée est une largeur raisonnable pour le contenu attendu.

###  <a name="BKMK_ComboBoxesAndDropDowns"></a> Zones de liste déroulante et les listes déroulantes
Pour le comportement de l’interaction typique, suivez le [instructions de bureau de Windows pour les listes déroulantes et des zones de liste déroulante](/windows/desktop/uxguide/ctrl-drop).

#### <a name="visual-style"></a>Style visuel

-   Dans les boîtes de dialogue utilitaire, ne pas remodéliser le contrôle. Utiliser le style de base intrinsèque au contrôle.

-   Dans l’interface utilisateur à thème, zones de liste déroulante et les listes déroulantes suivent les thèmes standard pour les contrôles.

#### <a name="layout"></a>Mise en page
Zones de liste déroulante et les listes déroulantes doivent être dimensionnés en fonction du contenu, ne pas à la largeur de la fenêtre dans lequel elles sont affichées, ni d’arbitrairement correspond à la longueur d’un champ long, par exemple, un chemin d’accès.

![Incorrecte : la largeur de la liste déroulante est trop longue pour le contenu qui s’affichera. ](../../extensibility/ux-guidelines/media/0707-03_incorrectdropdownlayout.png "0707-03_IncorrectDropDownLayout")<br />Incorrecte : la largeur de la liste déroulante est trop longue pour le contenu qui s’affichera.

![Correct : la liste déroulante est dimensionnée pour permettre la croissance de traduction, mais pas inutilement longs. ](../../extensibility/ux-guidelines/media/0707-04_correctdropdownlayout.png "0707-04_CorrectDropDownLayout")<br />Correct : la liste déroulante est dimensionnée pour permettre la croissance de traduction, mais pas inutilement longs.

###  <a name="BKMK_CheckBoxes"></a> Cases à cocher
Pour le comportement de l’interaction typique, suivez le [instructions de bureau de Windows pour les cases à cocher](/windows/desktop/uxguide/ctrl-check-boxes).

#### <a name="visual-style"></a>Style visuel

-   Dans les boîtes de dialogue utilitaire, ne pas remodéliser le contrôle. Utiliser le style de base intrinsèque au contrôle.

-   Dans l’interface utilisateur à thème, cases à cocher suivent les thèmes standard pour les contrôles.

#### <a name="specialized-interactions"></a>Interactions spécialisées

-   Interaction avec une case à cocher ne doit jamais affiche une boîte de dialogue ou accéder à une autre zone.

-   Aligner les cases à cocher avec la ligne de base de la première ligne de texte.

     ![Incorrecte : la case à cocher est centrée sur le texte. ](../../extensibility/ux-guidelines/media/0707-05_incorrectcheckboxalign.png "0707-05_IncorrectCheckBoxAlign")<br />Incorrecte : la case à cocher est centrée sur le texte.

     ![Correct : la case à cocher est aligné avec la première ligne du texte. ](../../extensibility/ux-guidelines/media/0707-06_correctcheckboxalign.png "0707-06_CorrectCheckBoxAlign")<br />Correct : la case à cocher est aligné avec la première ligne du texte.

###  <a name="BKMK_RadioButtons"></a> Cases d’option
Pour le comportement de l’interaction typique, suivez le [instructions Windows Desktop pour les boutons radio](/windows/desktop/uxguide/ctrl-radio-buttons).

#### <a name="visual-style"></a>Style visuel
Dans les boîtes de dialogue Utilitaire n'effectuez pas les boutons de case d’option de style. Utiliser le style de base intrinsèque au contrôle.

#### <a name="specialized-interactions"></a>Interactions spécialisées
Il n’est pas nécessaire d’utiliser un cadre de groupe pour encadrer les choix de cases d’option, sauf si vous avez besoin de maintenir la distinction de groupe dans une disposition étroite.

###  <a name="BKMK_GroupFrames"></a> Images de groupe
Pour le comportement de l’interaction typique, suivez le [les instructions pour les cadres de groupe Windows Desktop](/windows/desktop/uxguide/ctrl-group-boxes).

#### <a name="visual-style"></a>Style visuel
Dans les boîtes de dialogue utilitaire n’appliquer un style cadres de groupe. Utiliser le style de base intrinsèque au contrôle.

#### <a name="layout"></a>Mise en page

-   Il n’est pas nécessaire d’utiliser un cadre de groupe pour encadrer les choix de cases d’option, sauf si vous avez besoin de maintenir la distinction de groupe dans une disposition étroite.

-   N’utilisez jamais un cadre de groupe pour un seul contrôle.

-   Parfois, il est acceptable d’utiliser une règle horizontale au lieu d’un conteneur d’image de groupe.

##  <a name="BKMK_TextControls"></a> Contrôles de texte

### <a name="static-text-fields"></a>Champs de texte statique

Un champ de texte statique présente des informations en lecture seule et ne peuvent pas être sélectionné par l’utilisateur. Évitez de l’utiliser pour le texte que l’utilisateur souhaite copier dans le Presse-papiers. Toutefois, le texte statique en lecture seule peut modifier pour refléter un changement d’état. Dans l’exemple ci-dessous, le texte statique de nom de sortie sous les changements de groupe d’informations afin de refléter les modifications apportées à la zone de texte racine Namespace au-dessus de lui.

Il existe deux façons d’afficher des informations de texte statique.

Texte statique peut être sur son propre dans une boîte de dialogue sans toute relation contenant-contenu quand il n’existe aucun conflit de regroupement. Décider si les lignes supplémentaires d’une zone sont vraiment nécessaires. Un exemple est l’affichage d’un chemin de répertoire dans une section créé par une ligne de groupe, comme indiqué ci-dessous :

![Informations de texte statique dans les contrôles de texte](../../extensibility/ux-guidelines/media/DisplayingStaticText.png "DisplayingStaticText.png")<br />Informations de texte statique dans les contrôles de texte

Dans une boîte de dialogue lorsque d’autres zones groupées existent et relation contenant-contenu des informations permet une meilleure lisibilité, et lorsque une section peut être masquée ou affichée (comme dans le **fenêtre Propriétés** volet description) ou vous souhaitez être cohérent avec l’interface utilisateur similaire, Placez le texte statique à l’intérieur d’une zone. Cette zone de groupe doit être une seule règle et dont la couleur la `ButtonShadow`:

![Texte statique dans la fenêtre Propriétés](../../extensibility/ux-guidelines/media/PropertiesWindow.png "PropertiesWindow.png")<br />Texte statique dans la fenêtre Propriétés

### <a name="read-only-text-box"></a>Zone de texte en lecture seule

Cela permet à l’utilisateur à sélectionner le texte dans le champ, mais pas le modifier. Ces zones de texte sont délimitées par le marqueur de biseau 3D habituel avec un `ButtonShadow` remplissage.

Une zone de texte peut devenir active (modifiable) lorsqu’un utilisateur modifie un contrôle associé, telles que l’activation/désactivation d’une case à cocher ou de sélection/désélection d’un bouton radio. Par exemple, dans le **outils &gt; Options** page illustré ci-dessous, le **Page d’accueil** zone de texte devient actif lorsque le **par défaut** case à cocher est désactivée.

![Zone de texte en lecture seule, affichage des états actifs et inactifs](../../extensibility/ux-guidelines/media/ReadOnlyTextBox.png "ReadOnlyTextBox.png")<br />Zone de texte en lecture seule, affichage des états actifs et inactifs

### <a name="using-text-in-dialogs"></a>En utilisant le texte dans les boîtes de dialogue

Recommandations principales du texte dans les boîtes de dialogue :

-   Étiquettes pour les zones de texte, des zones de liste et des images dans les boîtes de dialogue unthemed commencent par un verbe, ont un capital initial sur le premier mot uniquement et se terminent par un signe deux-points.

    > Suivent des contrôles de texte dans les boîtes de dialogue à thème [instructions de l’expérience utilisateur de bureau Windows](/windows/desktop/uxguide/top-violations) et n’effectuez pas de ponctuation de fin, à l’exception des points d’interrogation dans les liens d’aide.

-   Étiquettes des cases à cocher et des cases d’option commencent par un verbe, une majuscule initiale sur le premier mot uniquement et ne contenir aucun signe de ponctuation final.

-   Les étiquettes pour les boutons, les menus, les éléments de menu et les onglets ont majuscules sur chaque mot (majuscule).

-   Terminologie de l’étiquette doit être cohérente avec les étiquettes similaire dans les autres boîtes de dialogue.

-   Dans la mesure du possible, avoir un auteur d’écrire ou approuver le texte avant d’entrer au développeur pour l’implémentation.

-   Tous les contrôles doivent comporter des étiquettes, sauf dans des circonstances particulières dans les tabulation est suffisante.
Utilisez le texte d’aide lorsque cela est approprié.

### <a name="helper-text"></a>Texte d’aide

Inclus dans les boîtes de dialogue pour aider l’utilisateur à comprendre l’objectif de la boîte de dialogue ou pour indiquer l’action à effectuer. Texte d’aide doit être utilisé uniquement si nécessaire pour éviter d’encombrer les boîtes de dialogue simples. Deux variantes de texte d’assistance sont filigrane et la boîte de dialogue.

Suivez les emplacements courants pour le texte d’aide et être sélectif avec l’introduction de nouveaux domaines. Scénarios courants pour le texte d’assistance sont :

-   Texte d’aide dans les boîtes de dialogue, pour donner des instructions supplémentaires sur la façon d’interagir avec une boîte de dialogue complexe.

-   Texte de filigrane dans les fenêtres Outil vide ou des boîtes de dialogue, pour expliquer la raison pour laquelle aucun contenu n’est visible.

-   Un volet de description, comme en bas de la **fenêtre Propriétés**.

-   Filigrane de texte dans un éditeur vide, pour expliquer l’action de l’utilisateur à effectuer pour commencer.

### <a name="dialog-helper-text"></a>Texte d’assistance de boîte de dialogue

Un concepteur d’expérience utilisateur peut aider à déterminer quand le texte d’aide est approprié. Le concepteur peut définir où le texte d’aide s’affiche, ainsi que son contenu général. Assistance utilisateur peut écriture ou modifier le texte réel.

### <a name="watermarks"></a>Filigranes

Boîtes de dialogue bénéficient de recommandations de filigrane légèrement différente. Car une boîte de dialogue peut apparaître occupé avec nombreux éléments d’interface utilisateur (étiquettes, texte d’indication, boutons et autres contrôles conteneurs avec texte), en particulier lorsque celles s’affichent en noir, filigranes évidence en gris foncé (VSColor : `ButtonShadow`). En règle générale, un filigrane s’affiche à l’intérieur d’un contrôle comme une zone de liste avec un arrière-plan blanc (VSColor : `Window`).

-   Le texte s’affiche en gris foncé (VSColor : `ButtonShadow`). Toutefois, si le filigrane s’affiche sur un gris moyen ou une autre couleur (VSColor : `ButtonFace`) en arrière-plan, puis il est concernent sur sa lisibilité, accédez avec texte noir (VSColor : `WindowText`).

-   Filigranes peuvent être centrés ou aligné à gauche. Appliquer des règles de conception standard lors des décisions d’alignement. Impossible de sélectionner le filigrane sur l’arrière-plan.

![Exemple de texte de filigrane](../../extensibility/ux-guidelines/media/WatermarkTextExample.gif)<br />Exemple de texte de filigrane

### <a name="context-specific-dynamic-text"></a>Texte (dynamique) spécifiques au contexte

Texte dynamique peut être utilisé de deux manières différentes dans une boîte de dialogue ou l’interface utilisateur non modale : sous forme d’étiquette dynamique ou en tant que contenu dynamique.

-   Étiquette dynamique : une utilisation courante du texte dynamique est dans les panneaux descriptifs qui offrent plus d’informations pour l’élément sélectionné, comme dans une boîte de dialogue qui contient une liste d’éléments et propriétés pour les éléments affichés dans une grille à droite. L’étiquette de la grille des propriétés peut-être être dynamique afin que lorsqu’un élément est sélectionné sur la gauche, la grille à droite affiche les informations de cet élément spécifique.

-   Texte dynamique : peut être utile dans les cas où vous avez besoin afficher des informations spécifiques et non les informations de cette façon, mais soyez vigilant ne pas abuser.

Si vous souhaitez que les utilisateurs aient la possibilité de copier les informations, texte dynamique doit être dans un champ de texte en lecture seule.

##  <a name="BKMK_ButtonsAndHyperlinks"></a> Boutons et des liens hypertexte

### <a name="overview"></a>Vue d'ensemble
Contrôles de boutons et de liens (liens) doivent suivre [des conseils de Windows Desktop base sur les liens hypertexte](/windows/desktop/uxguide/ctrl-links) pour l’utilisation, le libellé, dimensionnement et l’espacement.

### <a name="choosing-between-buttons-and-links"></a>Choix entre les boutons et les liens
En règle générale, les boutons ont été utilisés pour les actions et des liens hypertexte qui ont été réservées pour la navigation. Boutons peuvent être utilisés dans tous les cas, mais le rôle de liens a été développé dans Visual Studio afin que les boutons et les liens ne sont plus interchangeables dans certaines conditions.

Quand utiliser les boutons de commande :

-   Commandes principales

-   Affichage windows utilisé pour recueillir l’entrée ou faire des choix, même si elles sont des commandes secondaires

-   Actions destructrices ou irréversibles

-   Boutons d’engagement dans les Assistants et les flux de page

Éviter les boutons de commande dans les fenêtres Outil, ou si vous avez besoin de plus de deux mots pour l’étiquette. Liens peuvent avoir des étiquettes de plus de temps.

 Quand utiliser des liens :

-   Navigation vers une autre fenêtre, document ou page web

-   Situations nécessitant une étiquette plus longue ou courte phrase pour décrire l’objectif de l’action

-   Espaces étroite où un bouton serait surcharger l’interface utilisateur, à condition que l’action n’est pas destructifs ou irréversible

-   Minimise les commandes secondaires dans les situations où il existe de nombreuses commandes

#### <a name="examples"></a>Exemples
![Liens utilisés dans la barre d’informations suivant un message d’état de la commande](../../extensibility/ux-guidelines/media/070703-01_commandlinkinfobar.png "070703-01_CommandLinkInfobar")<br />Commandes liens utilisés dans la barre d’informations suivant un message d’état

![Liens utilisés dans la fenêtre contextuelle CodeLens](../../extensibility/ux-guidelines/media/070703-02_linksincodelens.png "070703-02_LinksInCodeLens")<br />Liens utilisés dans la fenêtre contextuelle CodeLens

![Liens utilisés pour les commandes secondaire où boutons bénéficierait de trop peu d’attention](../../extensibility/ux-guidelines/media/070703-03_linksassecondarycommands.png "070703-03_LinksAsSecondaryCommands")<br />Liens utilisés pour les commandes secondaire où boutons bénéficierait de trop peu d’attention

### <a name="common-buttons"></a>Boutons courants

#### <a name="text"></a>Texte
Suivez les instructions de l’écriture de [l’interface utilisateur texte et la terminologie](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology).

#### <a name="visual-style"></a>Style visuel

##### <a name="standard-unthemed"></a>Standard (unthemed)
La plupart des boutons dans Visual Studio s’affiche dans les boîtes de dialogue utilitaire et ne doit pas être filtrables. Ils doivent refléter l’apparence standard des boutons comme stipulé par le système d’exploitation.

##### <a name="themed"></a>À thème
Dans certains cas, boutons peuvent être utilisées dans l’interface utilisateur de style et ces boutons doivent être présentent en conséquence. Consultez [boîtes de dialogue](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs) pour plus d’informations sur les contrôles à thème.

### <a name="special-buttons"></a>Boutons spéciaux

#### <a name="browse-buttons"></a>Boutons de navigation de...
**[Parcourir...]**  boutons sont utilisés dans les grilles, les boîtes de dialogue et fenêtres Outil et autres éléments d’interface utilisateur non modales. Ils affichent un sélecteur qui aide l’utilisateur à remplir une valeur dans un contrôle. Il existe deux variantes de ce bouton, long et court.

![Le bouton long [Parcourir...]](../../extensibility/ux-guidelines/media/070703-04_browselong.gif "070703-04_BrowseLong")<br />Le bouton long [Parcourir...]

![Le bouton court portant uniquement sur les points de suspension [...]](../../extensibility/ux-guidelines/media/070703-05_browseshort.gif "070703-05_BrowseShort")<br />Le bouton court portant uniquement sur les points de suspension [...]

Quand utiliser le bouton court de points de suspension uniquement :

-   S’il existe plusieurs long **[Parcourir...]**  bouton dans une boîte de dialogue, comme lorsque plusieurs champs permettant la navigation. Utilisez court **[...]**  bouton pour chacun d’eux à éviter les clés d’accès à confusion créées par cette situation (**& Parcourir** et **& rcourir le** dans la même boîte de dialogue).

-   Dans une boîte de dialogue étroite, ou lorsqu’il n’existe aucun emplacement raisonnable pour le bouton long.

-   Si le bouton apparaît dans un contrôle de grille.

Instructions pour l’aide du bouton :

-   N’utilisez pas une clé d’accès. Pour accéder à l’aide du clavier, l’utilisateur doit de tabulation du contrôle adjacentes. Assurez-vous que l’ordre de tabulation est telle que n’importe quel bouton Parcourir immédiatement après le champ qui remplira. N’utilisez jamais un trait de soulignement ci-dessous la première période.

-   Définir le Microsoft Active Accessibility (MSAA) **nom** propriété **Parcourir...**  (y compris les points de suspension) afin que l’écran lecteurs lue en tant que « Browse » et pas « point-point-point » ou « période période période. » Pour les contrôles managés, cela signifie que le **AccessibleName** propriété.

-   N’utilisez jamais de points de suspension **[...]**  bouton pour quoi que ce soit, à l’exception d’une action de navigation. Par exemple, si vous avez besoin d’un **[nouveau...]**  bouton mais n’avez pas assez de place pour le texte, puis la boîte de dialogue doit être redéfinie.

##### <a name="sizing-and-spacing"></a>Dimensionnement et l’espacement
![Boutons de dimensionnement [Parcourir...] : version de la norme est x 23 75 pixels et version courte 26 x 23 pixels](../../extensibility/ux-guidelines/media/070703-06_browsesizing.png "070703-06_BrowseSizing")<br />Bouton de dimensionnement [Parcourir...]

![Boutons d’espacement [Parcourir...] : espacement entre contrôle connexe et de pixels de bouton 7 Parcourir standards, l’espacement entre le contrôle concerné et parcourir court bouton 5 pixels](../../extensibility/ux-guidelines/media/070703-07_browsespacing.png "070703-07_BrowseSpacing")<br />Bouton d'espacement [Parcourir...]

#### <a name="graphical-buttons"></a>Boutons graphiques
Certains boutons doivent toujours utiliser une image graphique et n’incluez jamais de texte pour économiser l’espace et éviter les problèmes de localisation. Ceux-ci sont souvent utilisés dans les sélecteurs de champ et les autres listes pouvant être triés.

> **Remarque :** Les utilisateurs doivent TAB pour accéder à ces boutons (il n’existe aucune clé d’accès), par conséquent, les placer dans un ordre cohérent. Carte le `name` propriété du bouton à l’action nécessaire afin que les lecteurs d’écran interprètent correctement l’action du bouton.

| Fonction | Bouton |
| --- | --- |
| Ajouter | ![Graphical "Add" button](../../extensibility/ux-guidelines/media/070703-08_buttonadd.png "070703-08_ButtonAdd") |
| Remove | ![Graphique bouton « Supprimer »](../../extensibility/ux-guidelines/media/070703-09_buttonremove.png "070703-09_ButtonRemove") |
| Ajouter tout | ![Bouton graphique « Ajouter tout »](../../extensibility/ux-guidelines/media/070703-10_buttonaddall.png "070703-10_ButtonAddAll") |
| Supprimer tout | ![Bouton graphique « Supprimer tout »](../../extensibility/ux-guidelines/media/070703-11_buttonremoveall.png "070703-11_ButtonRemoveAll") |
| Monter | ![Bouton graphique « Monter »](../../extensibility/ux-guidelines/media/070703-12_buttonmoveup.png "070703-12_ButtonMoveUp") |
| Descendre | ![Bouton graphique « Descendre »](../../extensibility/ux-guidelines/media/070703-13_buttonmovedown.png "070703-13_ButtonMoveDown") |
| Supprimer | ![Graphical "Delete" button](../../extensibility/ux-guidelines/media/070703-14_buttondelete.png "070703-14_ButtonDelete") |

##### <a name="sizing-and-spacing"></a>Dimensionnement et l’espacement
Dimensionnement des boutons graphiques est identique à la version courte de la **[Parcourir...]**  bouton (26 x 23 pixels) :

![Apparence d’une image de graphique sur le bouton, avec et sans affichage de couleur transparente](../../extensibility/ux-guidelines/media/070703-15_graphicalbuttonspacing.png "070703-15_GraphicalButtonSpacing")<br />Apparence d’une image de graphique sur le bouton, avec et sans affichage de couleur transparente

### <a name="hyperlinks"></a>Liens hypertexte
Des liens hypertexte sont bien adaptés aux actions de navigation telles que l’ouverture d’une rubrique d’aide, une boîte de dialogue modale ou un Assistant. Si un lien hypertexte est utilisé pour une commande, il doit toujours afficher une modification visible et sensible à l’interface utilisateur. En règle générale, les actions de validation à une action (par exemple, enregistrer, Annuler et supprimer) sont communiquées mieux à l’aide d’un bouton.

#### <a name="writing-style"></a>Style d’écriture
Suivez le [conseils Windows Desktop pour le texte de l’interface utilisateur](/windows/desktop/uxguide/text-ui). N’utilisez pas « En savoir plus à propos, » « Dire me plus sur » ou « Get help avec ce » formulation. Au lieu de cela, une expression texte de lien d’aide en termes de la question principale ayant obtenu une réponse par le contenu d’aide. Par exemple, «**comment ajouter un serveur à l’Explorateur de serveurs ?**»

#### <a name="visual-style"></a>Style visuel

-   Utilisent toujours des liens hypertexte [The VSColor Service](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService). Si un lien hypertexte n’est pas un style correctement, il clignote en rouge lorsqu’il est actif ou affiche une couleur différente après avoir visité.

-   N’incluez pas le contrôle positionné état sauf si le lien est un fragment de phrase au sein d’une phrase complète, comme dans un filigrane des soulignements.

-   Soulignements ondulés ne doit pas s’affichent au pointage. Au lieu de cela, les commentaires à l’utilisateur que le lien est actif sont un changement de couleur légère et le curseur de lien approprié.

##  <a name="BKMK_TreeViews"></a> Vues de l’arborescence

Vues de l’arborescence fournissent un moyen d’organiser complexe répertorie dans des groupes parent-enfant. Un utilisateur peut développer ou réduire des groupes parents pour afficher ou masquer les éléments enfants sous-jacents. Chaque élément dans une vue d’arborescence peut être sélectionné pour fournir des actions.

###  <a name="BKMK_TreeViewVisualStyle"></a> Style visuel de vue arborescence

#### <a name="expanders"></a>Développeurs
Contrôles d’arborescence doivent être conforme à la conception de l’expander utilisée par Windows et Visual Studio. Chaque nœud utilise un contrôle expander pour mettre en évidence ou masquer des éléments sous-jacents. À l’aide d’un contrôle expander fournit une cohérence pour les utilisateurs peuvent rencontrer des arborescences différentes au sein de Windows et Visual Studio.

![Correct : style approprié de nœud d’arborescence à l’aide d’un contrôle expander](../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705-1_TreeViewCorrect")<br />Correct : style approprié de nœud d’arborescence à l’aide d’un contrôle expander

![Incorrect : le style incorrect de nœud d’arborescence](../../extensibility/ux-guidelines/media/070705-2_treeviewincorrect1.png "070705-2_TreeViewIncorrect1")<br />Incorrect : le style incorrect de nœud d’arborescence

#### <a name="selection"></a>Sélection
Lorsqu’un nœud est sélectionné dans l’arborescence, la mise en surbrillance doit se développer pour la largeur totale du contrôle arborescence. Cela permet aux utilisateurs à identifier clairement quel élément qu’ils ont sélectionnées. Couleurs de la sélection doivent refléter le thème de Visual Studio actuel.

![Correct : mise en surbrillance du nœud sélectionné correspond à toute la largeur du contrôle arborescence. ](../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705-1_TreeViewCorrect")<br />Correct : mise en surbrillance du nœud sélectionné correspond à toute la largeur du contrôle arborescence.

![Incorrect : mise en surbrillance du nœud sélectionné ne tient pas toute la largeur du contrôle arborescence. ](../../extensibility/ux-guidelines/media/070705-3_treeviewincorrect2.png "070705-3_TreeViewIncorrect2")<br />Incorrect : mise en surbrillance du nœud sélectionné ne tient pas toute la largeur du contrôle arborescence.

#### <a name="icons"></a>Icônes
Icônes doivent uniquement être utilisées dans les contrôles d’arborescence si ils permettent d’identifier visuellement les différences entre les éléments. En règle générale, les icônes doivent être utilisés uniquement dans les listes hétérogènes dans lequel les icônes communiquent les informations pour différencier les types d’éléments. Dans une liste homogène à l’aide des icônes peuvent fréquemment être vu comme un bruit et doit être évitée. Dans ce cas, l’icône de groupe (parent) peut transmettre le type d’éléments qu’il contient. L’exception à cette règle serait si l’icône est dynamique et est utilisée pour indiquer l’état.

#### <a name="scroll-bars"></a>Barres de défilement
Barres de défilement doivent toujours être masquées si le contenu tient dans le contrôle arborescence. Il est acceptable pour les barres de défilement pour être masquées ou semi-transparent dans une fenêtre de défilement et s’affichent lorsque la fenêtre contenant l’arborescence a le focus ou lors de pointage de l’arborescence afficher lui-même.

![Les deux barres de défilement horizontales et verticales sont affichées, car le contenu a dépassé les limites du contrôle arborescence. ](../../extensibility/ux-guidelines/media/070705-4_scrollbars.png "070705-4_Scrollbars")<br />Les deux barres de défilement horizontales et verticales sont affichées, car le contenu a dépassé les limites du contrôle arborescence.

###  <a name="BKMK_TreeViewInteractions"></a> Interactions de vue d’arborescence

#### <a name="context-menus"></a>Menus contextuels
Un nœud d’arborescence peut révéler des options de sous-menu dans un menu contextuel. En règle générale, cela se produit lorsqu’un utilisateur a cliqué un élément ou appuyé sur la touche de Menu un clavier Windows avec l’élément sélectionné. Il est important que le nœud Obtient le focus et qu’il est sélectionné. Cela permet à l’utilisateur d’identifier quel élément auquel appartient le sous-menu.

![L’élément produisant a le focus de gains de menu contextuel pour notifier l’utilisateur auquel l’élément a été sélectionné. ](../../extensibility/ux-guidelines/media/070705-5_contextmenu.png "070705-5_ContextMenu")<br />L’élément produisant a le focus de gains de menu contextuel pour notifier l’utilisateur auquel l’élément a été sélectionné.

#### <a name="keyboard"></a>Clavier
L’arborescence doit fournir la possibilité de sélectionner des éléments et développer/réduire les nœuds à l’aide du clavier. Cela garantit que la navigation répond à nos exigences en termes d’accessibilité.

##### <a name="tree-view-control"></a>Contrôle d’arborescence
Contrôles d’arborescence de Visual Studio doivent suivre la navigation au clavier courants :

-   **Flèche haut :** Sélectionner des éléments en déplaçant l’arborescence

-   **Bas :** Sélectionner des éléments en déplaçant vers le bas de l’arborescence

-   **Flèche droite :** Développez un nœud dans l’arborescence

-   **Flèche gauche :** Réduire un nœud dans l’arborescence

-   **Entrez la clé :** Lancer, charger, exécuter l’élément sélectionné

##### <a name="trid-tree-view-and-grid-view"></a>Grid (vue de l’arborescence et affichage de grille)
Un contrôle Grid est un contrôle complexe qui contienne une arborescence dans une grille. Développement, la réduction et la navigation dans l’arborescence doivent respecter les mêmes commandes de clavier comme une arborescence, avec les ajouts suivants :

-   **Flèche droite :** Développez le nœud. Une fois que le nœud est développé, il doit continuer accédant à la colonne le plus proche sur la droite. Navigation doit s’arrêter à la fin de la ligne.

-   **Onglet :** Navigue vers la cellule la plus proche sur la droite.  À la fin de la ligne, la navigation se poursuit à la ligne suivante.

-   **Maj + Tab :** Navigue vers la cellule la plus proche sur la gauche.  Au début de la ligne, la navigation se poursuit à la cellule la plus à droite de la ligne précédente.

![Un contrôle Grid dans Visual Studio](../../extensibility/ux-guidelines/media/070705-6_trid.png "070705-6_Trid")<br />Un contrôle Grid dans Visual Studio