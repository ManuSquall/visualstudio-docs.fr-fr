---
title: Modèles de contrôle commun pour Studio Visuel (fr) Microsoft Docs
ms.date: 04/26/2017
ms.topic: conceptual
ms.assetid: 3e893949-6398-42f1-9eab-a8d8c2b7f02d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b0b5a1904c01f5688a00e45de7feed7ae326d9b3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698714"
---
# <a name="common-control-patterns-for-visual-studio"></a>Modèles de contrôle courants pour Visual Studio
## <a name="common-controls"></a><a name="BKMK_CommonControls"></a>Contrôles courants

### <a name="overview"></a>Vue d'ensemble
Les contrôles courants constituent la majorité de l’interface utilisateur de Visual Studio. Les contrôles les plus courants utilisés dans l’interface Visual Studio doivent suivre les [directives d’interaction Windows Desktop](/windows/desktop/uxguide/controls). Ce sujet est spécifique à Visual Studio et couvre des situations spéciales ou des détails qui augmentent ces directives Windows.

#### <a name="common-controls-in-this-topic"></a>Contrôles communs dans ce domaine

- [Barres de défilement](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_Scrollbars)

- [Champs d’entrée](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_InputFields)

- [Boîtes combo et listes de drop-down](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ComboBoxesAndDropDowns)

- [Cases à cocher](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CheckBoxes)

- [Cases d’option](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_RadioButtons)

- [Cadres de groupe](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_GroupFrames)

- [Contrôles de texte](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)

- [Boutons et hyperliens](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)

- [Arborescences](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViews)

#### <a name="visual-style"></a>Style visuel
La première chose à considérer lorsque les commandes de style est de savoir si les contrôles seront utilisés dans l’interface utilisateur thématique. Les contrôles dans l’interface utilisateur standard sont non thématiques interface utilisateur et doivent suivre [le style normal de Windows Desktop](/windows/desktop/uxguide/controls), ce qui signifie qu’ils ne sont pas re-templated et doivent apparaître dans leur apparence de contrôle par défaut.

- **Dialogues standard (utilitaires) :** pas thématiques. Ne re-template. Utilisez des défauts de style de contrôle de base.

- **Fenêtres d’outils, éditeurs de documents, surfaces de conception et dialogues thématiques :** Utilisez l’apparence thématique spécialisée en utilisant le service de couleur.

### <a name="scroll-bars"></a><a name="BKMK_Scrollbars"></a>Barres de défilement
 Les barres de défilement doivent suivre [les modèles d’interaction courants pour les barres de défilement Windows,](/windows/desktop/Controls/about-scroll-bars) sauf si elles sont augmentées avec des informations de contenu, comme dans l’éditeur de code.

### <a name="input-fields"></a><a name="BKMK_InputFields"></a>Champs d’entrée
 Pour un comportement d’interaction typique, suivez les [directives de Windows Desktop pour les boîtes textuelles](/windows/desktop/uxguide/ctrl-text-boxes).

#### <a name="visual-style"></a>Style visuel

- Les champs d’entrée ne devraient pas être coiffés dans les dialogues d’utilité. Utilisez le style de base intrinsèque au contrôle.

- Les champs d’entrée thématiques ne doivent être utilisés que dans les dialogues thématiques et les fenêtres d’outils.

#### <a name="specialized-interactions"></a>Interactions spécialisées

- Les champs de lecture seulement auront un fond gris (handicapé) mais par défaut (actif) au premier plan.

- Les champs ** \<** requis devraient avoir exigé>comme filigranes à l’intérieur d’eux. Vous ne devez pas changer la couleur de l’arrière-plan, sauf dans des situations rares.

- Validation d’erreur : Voir [Notifications et progrès pour Visual Studio](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)

- Les champs d’entrée doivent être dimensionnés pour s’adapter au contenu, non pas pour s’adapter à la largeur de la fenêtre dans laquelle ils sont montrés, ni pour correspondre arbitrairement à la longueur d’un long champ, comme un chemin. La longueur peut être une indication pour l’utilisateur des limites quant au nombre de caractères autorisés sur le terrain.

     ![Durée incorrecte du champ d’entrée : il est peu probable que le nom soit aussi long.](../../extensibility/ux-guidelines/media/0707-01_incorrectinputfieldcontrol.png "0707-01_IncorrectInputFieldControl")<br />Durée incorrecte du champ d’entrée : il est peu probable que le nom soit aussi long.

     ![Durée correcte du champ d’entrée : le champ d’entrée est une largeur raisonnable pour le contenu prévu.](../../extensibility/ux-guidelines/media/0707-02_correctinputfieldcontrol.png "0707-02_CorrectInputFieldControl")<br />Durée correcte du champ d’entrée : le champ d’entrée est une largeur raisonnable pour le contenu prévu.

### <a name="combo-boxes-and-drop-down-lists"></a><a name="BKMK_ComboBoxesAndDropDowns"></a>Boîtes combo et listes de drop-down
Pour un comportement d’interaction typique, suivez les [directives de Windows Desktop pour les listes de dépose et les boîtes combo](/windows/desktop/uxguide/ctrl-drop).

#### <a name="visual-style"></a>Style visuel

- Dans les dialogues utilitaires, ne re-template le contrôle. Utilisez le style de base intrinsèque au contrôle.

- Dans l’interface utilisateur thématique, les boîtes combo et les déposes suivent le thème standard pour les commandes.

#### <a name="layout"></a>Mise en page
Les boîtes combo et les descentes doivent être dimensionnées pour s’adapter au contenu, non pas pour s’adapter à la largeur de la fenêtre dans laquelle elles sont montrées, ni pour correspondre arbitrairement à la longueur d’un long champ, comme un chemin.

![Incorrect : la largeur de chute est trop longue pour le contenu qui sera affiché.](../../extensibility/ux-guidelines/media/0707-03_incorrectdropdownlayout.png "0707-03_IncorrectDropDownLayout")<br />Incorrect : la largeur de chute est trop longue pour le contenu qui sera affiché.

![Correct: la baisse est dimensionnée pour permettre la croissance de la traduction, mais pas inutilement long.](../../extensibility/ux-guidelines/media/0707-04_correctdropdownlayout.png "0707-04_CorrectDropDownLayout")<br />Correct: la baisse est dimensionnée pour permettre la croissance de la traduction, mais pas inutilement long.

### <a name="check-boxes"></a><a name="BKMK_CheckBoxes"></a>Boîtes à cocher
Pour un comportement d’interaction typique, suivez les [directives de Windows Desktop pour les cases à cocher](/windows/desktop/uxguide/ctrl-check-boxes).

#### <a name="visual-style"></a>Style visuel

- Dans les dialogues utilitaires, ne re-template le contrôle. Utilisez le style de base intrinsèque au contrôle.

- Dans l’interface utilisateur thématique, les cases à cocher suivent le thème standard pour les commandes.

#### <a name="specialized-interactions"></a>Interactions spécialisées

- L’interaction avec une case à cocher ne doit jamais faire éclater un dialogue ou naviguer vers une autre zone.

- Alignez les cases à cocher avec la ligne de base de la première ligne de texte.

     ![Incorrect : la case à cocher est centrée sur le texte.](../../extensibility/ux-guidelines/media/0707-05_incorrectcheckboxalign.png "0707-05_IncorrectCheckBoxAlign")<br />Incorrect : la case à cocher est centrée sur le texte.

     ![Correct : la case à cocher est alignée avec la première ligne du texte.](../../extensibility/ux-guidelines/media/0707-06_correctcheckboxalign.png "0707-06_CorrectCheckBoxAlign")<br />Correct : la case à cocher est alignée avec la première ligne du texte.

### <a name="radio-buttons"></a><a name="BKMK_RadioButtons"></a>Boutons radio
Pour un comportement d’interaction typique, suivez les [directives de Windows Desktop pour les boutons radio](/windows/desktop/uxguide/ctrl-radio-buttons).

#### <a name="visual-style"></a>Style visuel
Dans les dialogues utilitaires, ne pas styler les boutons radio. Utilisez le style de base intrinsèque au contrôle.

#### <a name="specialized-interactions"></a>Interactions spécialisées
Il n’est pas nécessaire d’utiliser un cadre de groupe pour inclure les choix radio, sauf si vous avez besoin de maintenir la distinction de groupe dans une mise en page serrée.

### <a name="group-frames"></a><a name="BKMK_GroupFrames"></a>Cadres de groupe
Pour un comportement d’interaction typique, suivez les [directives de Windows Desktop pour les cadres de groupe](/windows/desktop/uxguide/ctrl-group-boxes).

#### <a name="visual-style"></a>Style visuel
Dans les dialogues utilitaires, ne stylez pas les cadres de groupe. Utilisez le style de base intrinsèque au contrôle.

#### <a name="layout"></a>Mise en page

- Il n’est pas nécessaire d’utiliser un cadre de groupe pour inclure les choix radio, sauf si vous avez besoin de maintenir la distinction de groupe dans une mise en page serrée.

- N’utilisez jamais un cadre de groupe pour un seul contrôle.

- Il est parfois acceptable d’utiliser une règle horizontale au lieu d’un conteneur à ossature de groupe.

## <a name="text-controls"></a><a name="BKMK_TextControls"></a>Contrôles de texte

### <a name="static-text-fields"></a>Champs de texte statiques

Un champ de texte statique présente des informations de lecture seulement et ne peut pas être sélectionné par l’utilisateur. Évitez de l’utiliser pour n’importe quel texte que l’utilisateur pourrait vouloir copier au presse-papiers. Cependant, le texte statique lu-seulement peut changer pour refléter un changement d’état. Dans l’exemple ci-dessous, le texte statique du nom de sortie sous le groupe d’information change pour refléter les modifications apportées à la boîte de texte Root Namespace au-dessus.

Il existe deux façons d’afficher des informations textuelles statiques.

Le texte statique peut être seul dans un dialogue sans aucun confinement lorsqu’il n’y a pas de conflit de groupement. Décidez si les lignes supplémentaires d’une boîte sont vraiment nécessaires. Un exemple est l’affichage d’un parcours d’annuaire sous une section créée par une ligne de groupe, comme indiqué ci-dessous:

![Informations textuelles statiques dans les contrôles de texte](../../extensibility/ux-guidelines/media/DisplayingStaticText.png "AffichageStaticText.png")<br />Informations textuelles statiques dans les contrôles de texte

Dans un dialogue où d’autres zones groupées existent et le confinement de l’information aiderait à la lisibilité, et quand une section peut être cachée ou montrée (comme dans le volet de description **de fenêtre propriétés)** ou vous voulez être compatible avec l’interface utilisateur similaire, placez le texte statique à l’intérieur d’une boîte. Cette boîte de groupe doit être `ButtonShadow`une règle unique et colorée avec le :

![Texte statique dans la fenêtre propriété](../../extensibility/ux-guidelines/media/PropertiesWindow.png "PropriétésWindow.png")<br />Texte statique dans la fenêtre propriété

### <a name="read-only-text-box"></a>Boîte textuelle de lecture seulement

Cela permet à l’utilisateur de sélectionner le texte à l’intérieur du champ, mais pas de le modifier. Ces boîtes de texte sont bordées par le `ButtonShadow` ciseau 3D habituel avec un remplissage.

Une boîte de texte peut devenir active (modifiable) lorsqu’un utilisateur modifie un contrôle associé, comme la vérification/décocher une case à cocher ou la sélection/désélection d’un bouton radio. Par exemple, dans la page **Options Outils &gt; ** ci-dessous, la boîte de texte de la page **d’accueil** devient active lorsque la case à cocher par défaut **d’utilisation** n’est pas cochée.

![Boîte de texte de lecture seulement, montrant des états inactifs et actifs](../../extensibility/ux-guidelines/media/ReadOnlyTextBox.png "LireOnlyTextBox.png")<br />Boîte de texte de lecture seulement, montrant des états inactifs et actifs

### <a name="using-text-in-dialogs"></a>Utilisation du texte dans les dialogues

Principales lignes directrices pour le texte dans les dialogues:

- Les étiquettes pour les boîtes de texte, les boîtes de liste et les cadres dans des dialogues non considérés commencent par un verbe, ont un capital initial sur le premier mot seulement, et se terminent par un côlon.

    > Les contrôles de texte dans les dialogues thématiques suivent les [directives UX de bureau de Windows](/windows/desktop/uxguide/top-violations) et ne prennent pas la ponctuation de fin, à l’exception des points d’interrogation dans les liens d’aide.

- Les étiquettes pour les cases à cocher et les boutons d’option commencent par un verbe, un capital initial sur le premier mot seulement, et n’ont pas de ponctuation de fin.

- Les étiquettes pour les boutons, les menus, les éléments de menu et les onglets ont des majuscules initiales sur chaque mot (cas de titre).

- La terminologie de l’étiquette doit être compatible avec des étiquettes similaires dans d’autres dialogues.

- Si possible, demandez à un auteur/éditeur d’écrire ou d’approuver le texte avant qu’il ne soit envoyé au développeur pour y être implémenté.

- Tous les contrôles doivent avoir des étiquettes, sauf dans des circonstances particulières où le tabbing est suffisant.
Utilisez du texte d’aide le cas échéant.

### <a name="helper-text"></a>Texte d’aide

Inclus dans les dialogues pour aider l’utilisateur à comprendre le but du dialogue ou pour indiquer quelles mesures prendre. Le texte d’aide ne doit être utilisé que si nécessaire pour éviter d’encombrer les dialogues simples. Les deux variantes du texte d’aide sont le dialogue et le filigrane.

Suivez les emplacements communs pour le texte d’aide et soyez sélectif dans l’introduction de nouveaux domaines. Les scénarios courants pour le texte de l’aide sont les :

- Texte d’aide dans les dialogues, pour donner une orientation supplémentaire sur la façon d’interagir avec un dialogue complexe.

- Texte filigrane dans les fenêtres ou les dialogues vides d’outils, pour expliquer pourquoi aucun contenu n’est visible.

- Une vitre de description, comme au bas de la **fenêtre propriétés**.

- Texte filigrane dans un éditeur vide, pour expliquer quelles mesures l’utilisateur devrait prendre pour commencer.

### <a name="dialog-helper-text"></a>Texte d’assistance de boîte de dialogue

Un concepteur d’expérience utilisateur peut aider à déterminer quand le texte d’aide est approprié. Le concepteur peut définir où le texte d’aide apparaît ainsi que son contenu général. L’assistance utilisateur peut écrire/modifier le texte réel.

### <a name="watermarks"></a>Filigranes

Les dialogues bénéficient de lignes directrices légèrement différentes en filigrane. Parce qu’un dialogue peut sembler occupé avec de nombreux éléments d’interface utilisateur (étiquettes, texte d’indice, boutons et autres contrôles `ButtonShadow`de conteneur avec du texte), en particulier lorsque ceux apparaissent en noir, les filigranes se distinguent mieux en gris foncé (VSColor: ). Typiquement, un filigrane apparaît à l’intérieur d’un contrôle comme une boîte de liste avec un fond blanc (VSColor: `Window`).

- Le texte apparaît en gris `ButtonShadow`foncé (VSColor: ). Cependant, si le filigrane apparaît sur un fond `ButtonFace`gris ou autre (VSColor: ) et qu’il `WindowText`y a des inquiétudes quant à sa lisibilité, allez avec le texte noir (VSColor : ).

- Les filigranes peuvent être centrés ou à gauche. Appliquer des règles de conception standard lors de la prise de décisions d’alignement. Le filigrane ne peut pas être sélectionné en arrière-plan.

![Exemple de texte de filigrane](../../extensibility/ux-guidelines/media/WatermarkTextExample.gif)<br />Exemple de texte de filigrane

### <a name="context-specific-dynamic-text"></a>Texte spécifique au contexte (dynamique)

Le texte dynamique peut être utilisé de deux façons dans un dialogue ou une interface utilisateur sans mode : soit comme une étiquette dynamique, soit comme contenu dynamique.

- Étiquette dynamique : une utilisation commune du texte dynamique est dans les panneaux descriptifs qui offrent plus d’informations pour l’élément sélectionné, comme dans un dialogue qui contient une liste d’éléments et de propriétés pour les éléments affichés dans une grille à droite. L’étiquette pour la grille de propriété peut être dynamique de sorte que lorsqu’un élément est sélectionné à gauche, la grille à droite affiche des informations pour cet élément spécifique.

- Texte dynamique: peut être utile dans les cas où vous avez besoin d’afficher des informations spécifiques et non des informations générales de cette façon, mais il faut prendre soin de ne pas abuser.

Si vous voulez que les utilisateurs aient la possibilité de copier l’information, le texte dynamique doit être dans un champ de texte lu uniquement.

## <a name="buttons-and-hyperlinks"></a><a name="BKMK_ButtonsAndHyperlinks"></a>Boutons et hyperliens

### <a name="overview"></a>Vue d'ensemble
Les boutons et les commandes de liens (hyperliens) doivent suivre [les conseils de base de Windows Desktop sur les hyperliens](/windows/desktop/uxguide/ctrl-links) pour l’utilisation, la formulation, le dimensionnement et l’espacement.

### <a name="choosing-between-buttons-and-links"></a>Choisir entre les boutons et les liens
Traditionnellement, les boutons ont été utilisés pour les actions et les hyperliens ont été réservés à la navigation. Les boutons peuvent être utilisés dans tous les cas, mais le rôle des liens a été élargi dans Visual Studio de sorte que les boutons et les liens sont plus interchangeables dans certaines conditions.

Quand utiliser des boutons de commande :

- Commandes primaires

- Affichage des fenêtres utilisées pour recueillir des entrées ou faire des choix, même s’il s’œux secondaires

- Actions destructrices ou irréversibles

- Boutons d’engagement au sein des assistants et des flux de pages

Évitez les boutons de commande dans les fenêtres d’outils, ou si vous avez besoin de plus de deux mots pour l’étiquette. Les liens peuvent avoir des étiquettes plus longues.

 Quand utiliser des liens :

- Navigation vers une autre fenêtre, un document ou une autre page Web

- Situations nécessitant une étiquette plus longue ou une peine courte pour décrire l’intention de l’action

- Des espaces restreints où un bouton submergerait l’interface utilisateur, à condition que l’action ne soit pas destructrice ou irréversible

- Désaçant les commandes secondaires dans les situations où il existe de nombreux commandements

#### <a name="examples"></a>Exemples
![Liens de commande utilisés dans l’InfoBar à la suite d’un message d’état](../../extensibility/ux-guidelines/media/070703-01_commandlinkinfobar.png "070703-01_CommandLinkInfobar")<br />Liens de commande utilisés dans l’InfoBar à la suite d’un message d’état

![Liens utilisés dans la fenêtre contextuelle CodeLens](../../extensibility/ux-guidelines/media/070703-02_linksincodelens.png "070703-02_LinksInCodeLens")<br />Liens utilisés dans la fenêtre contextuelle CodeLens

![Liens utilisés pour les commandes secondaires où les boutons attireraient trop d’attention](../../extensibility/ux-guidelines/media/070703-03_linksassecondarycommands.png "070703-03_LinksAsSecondaryCommands")<br />Liens utilisés pour les commandes secondaires où les boutons attireraient trop d’attention

### <a name="common-buttons"></a>Boutons courants

#### <a name="text"></a>Texte
Suivez les directives d’écriture dans le [texte et la terminologie de l’interface utilisateur.](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology)

#### <a name="visual-style"></a>Style visuel

##### <a name="standard-unthemed"></a>Standard (non jugé)
La plupart des boutons de Visual Studio apparaîtront dans les dialogues utilitaires et ne doivent pas être stylés. Ils doivent refléter l’apparence standard des boutons dictés par le système d’exploitation.

##### <a name="themed"></a>Thème
Dans certains cas, les boutons peuvent être utilisés dans l’interface utilisateur de style et ces boutons doivent être stylés de manière appropriée. Consultez [Dialogs](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs) pour obtenir de l’information sur les contrôles thématiques.

### <a name="special-buttons"></a>Boutons spéciaux

#### <a name="browse-buttons"></a>Parcourir... Boutons
**[Parcourir...]** les boutons sont utilisés dans les grilles, les dialogues et les fenêtres d’outils et d’autres éléments d’interface utilisateur sans mode. Ils affichent un cueilleur qui aide l’utilisateur à remplir une valeur dans un contrôle. Il y a deux variantes de ce bouton, longue et courte.

![Le long bouton [Browse...]](../../extensibility/ux-guidelines/media/070703-04_browselong.gif "070703-04_BrowseLong")<br />Le long bouton [Browse...]

![Le bouton court ellipsis-seulement [...]](../../extensibility/ux-guidelines/media/070703-05_browseshort.gif "070703-05_BrowseShort")<br />Le bouton court ellipsis-seulement [...]

Quand utiliser le bouton court ellipsis-seulement :

- S’il y a plus d’un long **bouton [Parcourir...]** dans un dialogue, comme lorsque plusieurs champs permettent la navigation. Utilisez le bouton court **[...]** pour chacun pour éviter les touches d’accès déroutantes créées par cette situation (**&Parcourir** et B **&rames** dans le même dialogue).

- Dans un dialogue serré, ou quand il n’y a pas d’endroit raisonnable pour mettre le long bouton.

- Si le bouton apparaîtra dans un contrôle de grille.

Lignes directrices pour l’utilisation du bouton :

- N’utilisez pas de clé d’accès. Pour y accéder à l’aide du clavier, l’utilisateur doit onglet à partir du contrôle adjacent. Assurez-vous que l’ordre d’onglet est tel que n’importe quel bouton de navigation tombe immédiatement après le champ qu’il remplira. N’utilisez jamais un soulignement en dessous de la première période.

- Définissez la propriété Microsoft Active Accessibility (MSAA) **Nom** à **parcourir ...** (y compris l’ellipsis) de sorte que les lecteurs d’écran le liront comme "Browse" et non pas "point-point-point" ou "période-période-période." Pour les contrôles gérés, cela signifie la mise en place de la propriété **AccessibleName.**

- N’utilisez jamais un bouton d’élipsis **[...]** pour autre chose qu’une action de navigation. Par exemple, si vous avez besoin **d’un [nouveau ...]** bouton, mais n’ont pas assez de place pour le texte, alors le dialogue doit être redessiné.

##### <a name="sizing-and-spacing"></a>Dimensionnement et espacement
![Sizing [Browse...] boutons: version standard est 75x23 pixels, version courte est 26x23 pixels](../../extensibility/ux-guidelines/media/070703-06_browsesizing.png "070703-06_BrowseSizing")<br />Bouton de dimensionnement [Parcourir...]

![Espacement [Parcourir...] boutons: espacement entre le contrôle connexe et standard Bouton Parcourir 7 pixels, espacement entre le contrôle connexe et court bouton Browse 5 pixels](../../extensibility/ux-guidelines/media/070703-07_browsespacing.png "070703-07_BrowseSpacing")<br />Bouton d'espacement [Parcourir...]

#### <a name="graphical-buttons"></a>Boutons graphiques
Certains boutons doivent toujours utiliser une image graphique et ne jamais inclure de texte pour conserver l’espace et éviter les problèmes de localisation. Ceux-ci sont souvent utilisés dans les cueilleurs de terrain et d’autres listes triables.

> [!NOTE]
> Les utilisateurs doivent ongletr ces boutons (il n’y a pas de clés d’accès), afin de les placer dans un ordre raisonnable. Carte `name` de la propriété du bouton à l’action qu’il prend de sorte que les lecteurs d’écran interprètent correctement l’action du bouton.

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
Dimensionner pour les boutons graphiques est le même que pour la version courte du bouton **[Browse...]** (26x23 pixels):

![Apparition d’une image graphique sur le bouton, avec et sans couleur transparente affichant](../../extensibility/ux-guidelines/media/070703-15_graphicalbuttonspacing.png "070703-15_GraphicalButtonSpacing")<br />Apparition d’une image graphique sur le bouton, avec et sans couleur transparente affichant

### <a name="hyperlinks"></a>Liens hypertexte
Les hyperliens sont bien adaptés aux actions basées sur la navigation, comme l’ouverture d’un sujet d’aide, de dialogue modal ou d’un assistant. Si un lien hypertexte est utilisé pour une commande, il doit toujours afficher un changement visible et notable à l’interface utilisateur. En général, les actions qui s’engagent à une action (comme Enregistrer, annuler et supprimer) sont mieux communiquées à l’aide d’un bouton.

#### <a name="writing-style"></a>Style d’écriture
Suivez les conseils Windows Desktop pour le [texte de l’interface utilisateur](/windows/desktop/uxguide/text-ui). N’utilisez pas le phrasé « En savoir plus », « Parlez-moi » ou « Obtenez de l’aide avec cela ». Au lieu de cela, phrase Aide lien texte en termes de la question principale répondue par le contenu d’aide. Par exemple, "**Comment puis-je ajouter un serveur à l’explorateur de serveur ?**"

#### <a name="visual-style"></a>Style visuel

- Les hyperliens doivent toujours utiliser [le service VSColor](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService). Si un hyperlien n’est pas correctement coiffé, il clignote en rouge lorsqu’il est actif ou montre une couleur différente après avoir été visité.

- N’incluez pas les souligne à l’état de repos de contrôle à moins que le lien soit un fragment de phrase dans une phrase complète, comme dans un filigrane.

- Les soulignes ne devraient pas apparaître sur le plan stationnaire. Au lieu de cela, la rétroaction à l’utilisateur que le lien est actif est un léger changement de couleur et le curseur de lien approprié.

## <a name="tree-views"></a><a name="BKMK_TreeViews"></a>Vues d’arbre

Les vues sur les arbres permettent d’organiser des listes complexes en groupes parents-enfants. Un utilisateur peut élargir ou effondrer des groupes parentaux pour révéler ou cacher des articles sous-jacents pour enfants. Chaque élément dans une vue d’arbre peut être choisi pour fournir d’autres mesures.

### <a name="tree-view-visual-style"></a><a name="BKMK_TreeViewVisualStyle"></a>Style visuel de vue d’arbre

#### <a name="expanders"></a>Expandeurs
Les commandes de vue d’arbre doivent se conformer à la conception d’extenseur utilisée par Windows et Visual Studio. Chaque nœud utilise un contrôle d’extenseur pour révéler ou cacher des éléments sous-jacents. L’utilisation d’un contrôle d’extenseur fournit la cohérence pour les utilisateurs qui pourraient rencontrer différentes vues d’arbre au sein de Windows et Visual Studio.

![Correct: bon style de noeud de vue d’arbre à l’aide d’un contrôle d’extenseur](../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705-1_TreeViewCorrect")<br />Correct: bon style de noeud de vue d’arbre à l’aide d’un contrôle d’extenseur

![Incorrect : style incorrect de nœud de vue d’arbre](../../extensibility/ux-guidelines/media/070705-2_treeviewincorrect1.png "070705-2_TreeViewIncorrect1")<br />Incorrect : style incorrect de nœud de vue d’arbre

#### <a name="selection"></a>Sélection
Lorsqu’un nœud est sélectionné dans la vue de l’arbre, le point culminant doit s’étendre à toute la largeur du contrôle de la vue de l’arbre. Cela permet aux utilisateurs d’identifier clairement l’élément qu’ils ont choisi. Les couleurs de sélection doivent refléter le thème actuel de Visual Studio.

![Correct: point culminant du nœud sélectionné correspond à toute la largeur de la vue de l’arbre de contrôle.](../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705-1_TreeViewCorrect")<br />Correct: point culminant du nœud sélectionné correspond à toute la largeur de la vue de l’arbre de contrôle.

![Incorrect : le point culminant du nœud sélectionné ne correspond pas à toute la largeur du contrôle de vue de l’arbre.](../../extensibility/ux-guidelines/media/070705-3_treeviewincorrect2.png "070705-3_TreeViewIncorrect2")<br />Incorrect : le point culminant du nœud sélectionné ne correspond pas à toute la largeur du contrôle de vue de l’arbre.

#### <a name="icons"></a>Icônes
Les icônes ne doivent être utilisées que dans les commandes de vue des arbres si elles aident à identifier visuellement les différences entre les éléments. En général, les icônes ne doivent être utilisées que dans des listes hétérogènes dans lesquelles les icônes portent des informations pour différencier les types d’éléments. Dans une liste homogène utilisant des icônes peut souvent être considéré comme du bruit et doit être évité. Dans ce cas, l’icône de groupe (parent) peut transmettre le type d’éléments en son sein. L’exception à cette règle serait si l’icône est dynamique et est utilisé pour indiquer l’état.

#### <a name="scroll-bars"></a>Barres de défilement
Les barres de défilement doivent toujours être cachées si le contenu s’inscrit dans le contrôle de vue de l’arbre. Il est acceptable que les barres de défilement soient cachées, ou semi-transparentes dans une fenêtre défilementable et apparaissent lorsque la fenêtre contenant la vue de l’arbre est mise au point, ou sur le plan planeur de la vue de l’arbre elle-même.

![Les barres de défilement verticales et horizontales sont affichées parce que le contenu a dépassé les limites du contrôle de vue de l’arbre.](../../extensibility/ux-guidelines/media/070705-4_scrollbars.png "070705-4_Scrollbars")<br />Les barres de défilement verticales et horizontales sont affichées parce que le contenu a dépassé les limites du contrôle de vue de l’arbre.

### <a name="tree-view-interactions"></a><a name="BKMK_TreeViewInteractions"></a>Interactions de vue d’arbre

#### <a name="context-menus"></a>Menu contextuels
Un nœud de vue d’arbre peut révéler des options de sous-mois dans un menu de contexte. En règle générale, cela se produit lorsqu’un utilisateur a cliqué correctement sur un élément ou appuyé sur la touche du menu sur un clavier Windows avec l’élément sélectionné. Il est important que le nœud se concentre et soit sélectionné. Cela permet à l’utilisateur d’identifier à quel élément le sous-groupe appartient.

![L’élément qui a généré le menu contextuelle gains focus pour informer l’utilisateur quel élément a été sélectionné.](../../extensibility/ux-guidelines/media/070705-5_contextmenu.png "070705-5_ContextMenu")<br />L’élément qui a généré le menu contextuelle gains focus pour informer l’utilisateur quel élément a été sélectionné.

#### <a name="keyboard"></a>Clavier
La vue de l’arbre devrait fournir la possibilité de sélectionner des éléments et d’étendre/effondrer les nœuds à l’aide du clavier. Cela garantit que la navigation répond à nos exigences en matière d’accessibilité.

##### <a name="tree-view-control"></a>Contrôle de vue d’arbre
Les commandes visuelles d’arbres de studio devraient suivre la navigation commune de clavier :

- **Flèche vers le haut:** Sélectionnez les articles en déplaçant vers le haut de l’arbre

- **Flèche descendante:** Sélectionnez les articles en descendant l’arbre

- **Flèche droite:** Étendre un nœud dans l’arbre

- **Flèche gauche:** Effondrez un nœud dans l’arbre

- **Entrez la clé :** Initier, charger, exécuter un élément sélectionné

##### <a name="trid-tree-view-and-grid-view"></a>Trid (vue d’arbre et vue de grille)
Un contrôle tridé est un contrôle complexe qui contient une vue d’arbre dans une grille. L’expansion, l’effondrement et la navigation de l’arbre doivent respecter les mêmes commandes de clavier qu’une vue d’arbre, avec les ajouts suivants :

- **Flèche droite:** Élargissez un nœud. Une fois le nœud élargi, il doit continuer à naviguer jusqu’à la colonne la plus proche sur la droite. La navigation doit s’arrêter à la fin de la rangée.

- **Onglet:** Navigue vers la cellule la plus proche sur la droite.  À la fin de la rangée, la navigation se poursuit jusqu’à la rangée suivante.

- **Changement et onglet :** Navigue vers la cellule la plus proche sur la gauche.  Au début de la rangée, la navigation continue à la cellule la plus droite dans la rangée précédente.

![Un contrôle trid dans Visual Studio](../../extensibility/ux-guidelines/media/070705-6_trid.png "070705-6_Trid")<br />Un contrôle trid dans Visual Studio
