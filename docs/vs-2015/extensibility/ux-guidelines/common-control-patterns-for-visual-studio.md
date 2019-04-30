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
ms.openlocfilehash: 246464baea7e07e4d97e3483b423d200cf2b960c
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63430039"
---
# <a name="common-control-patterns-for-visual-studio"></a>Modèles de contrôle courants pour Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

## <a name="BKMK_CommonControls"></a> Contrôles communs

### <a name="overview"></a>Vue d'ensemble
 Contrôles communs constituent la majeure partie de l’interface utilisateur dans Visual Studio. Contrôles les plus courants utilisés dans l’interface de Visual Studio doivent suivre le [directives d’interaction de Windows Desktop](https://msdn.microsoft.com/library/windows/desktop/dn742399.aspx). Ce document est spécifique à Visual Studio et couvre des situations particulières ou des détails augmentent ces instructions de Windows.

#### <a name="common-controls-in-this-topic"></a>Contrôles communs dans cette rubrique

- [Barres de défilement](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_Scrollbars)

- [Champs d’entrée](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_InputFields)

- [Zones de liste déroulante et les listes déroulantes](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ComboBoxesAndDropDowns)

- [Cases à cocher](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CheckBoxes)

- [Cases d’option](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_RadioButtons)

- [Images de groupe](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_GroupFrames)

- [Contrôles de texte](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)

- [Boutons et des liens hypertexte](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)

- [Vues de l’arborescence](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViews)

#### <a name="visual-style"></a>Style visuel
 La première chose à prendre en compte lors de la stylisation de contrôles est que les contrôles seront utilisés dans l’interface utilisateur à thème. Contrôles dans l’interface utilisateur standard sont l’interface utilisateur sans thème et doivent respecter [style normal de Windows Desktop](https://msdn.microsoft.com/library/windows/desktop/dn742399\(v=vs.85\).aspx), ce qui signifie qu’ils ne sont pas re-basé sur un modèle et qu’il doivent apparaître dans leur apparence de contrôle par défaut.

- **Boîtes de dialogue standard (utilitaire) :** pas à thème. Ne pas re-template. Utilisez les valeurs par défaut du style de contrôle de base.

- **Fenêtres Outil, les éditeurs de document, les aires de conception et les boîtes de dialogue à thème :** Utilisez spécialisé apparence à thème à l’aide du service de couleur.

### <a name="BKMK_Scrollbars"></a> Barres de défilement
 Barres de défilement doivent suivre [des modèles d’interaction commun pour les barres de défilement Windows](https://msdn.microsoft.com/library/windows/desktop/bb787527\(v=vs.85\).aspx) , sauf si elles sont ajoutent les informations de contenu, comme dans l’éditeur de code.

### <a name="BKMK_InputFields"></a> Champs d’entrée
 Pour le comportement de l’interaction typique, suivez le [instructions Windows Desktop pour les zones de texte](https://msdn.microsoft.com/library/windows/desktop/dn742442\(v=vs.85\).aspx).

#### <a name="visual-style"></a>Style visuel

- Champs d’entrée ne doivent pas être style dans les boîtes de dialogue utilitaire. Utiliser le style de base intrinsèque au contrôle.

- Les champs d’entrée à thème doivent uniquement servir dans les boîtes de dialogue à thème et des fenêtres Outil.

#### <a name="specialized-interactions"></a>Interactions spécialisées

- Champs en lecture seule aura un arrière-plan gris (désactivé), mais de premier plan par défaut (actif).

- Requis champs doivent avoir  **\<requis >** en tant que filigranes en leur sein. Vous ne devez pas modifier la couleur d’arrière-plan, sauf dans de rares cas.

- Validation des erreurs : Consultez [Notifications et progression pour Visual Studio](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)

- Champs d’entrée doivent être dimensionnées en fonction du contenu, ne pas à la largeur de la fenêtre dans lequel elles sont affichées, ni d’arbitrairement correspond à la longueur d’un champ long, par exemple un chemin d’accès. Longueur peut être une indication à l’utilisateur de limitations concernant le nombre de caractères est autorisé dans le champ.

     ![Largeur du contrôle de champ d’entrée incorrecte](../../extensibility/ux-guidelines/media/0707-01-incorrectinputfieldcontrol.png "0707-01_IncorrectInputFieldControl") **longueur de champ d’entrée incorrecte : Il est peu probable que le nom sera ce long.**

     ![Corriger la largeur du contrôle de champ d’entrée](../../extensibility/ux-guidelines/media/0707-02-correctinputfieldcontrol.png "0707-02_CorrectInputFieldControl") **Correct d’entrée de longueur de champ : Le champ d’entrée est une largeur raisonnable pour le contenu attendu.**

### <a name="BKMK_ComboBoxesAndDropDowns"></a> Zones de liste déroulante et les listes déroulantes
 Pour le comportement de l’interaction typique, suivez le [instructions de bureau de Windows pour les listes déroulantes et des zones de liste déroulante](https://msdn.microsoft.com/library/windows/desktop/dn742404\(v=vs.85\).aspx).

#### <a name="visual-style"></a>Style visuel

- Dans les boîtes de dialogue Utilitaire n'effectuez pas remodéliser le contrôle. Utiliser le style de base intrinsèque au contrôle.

- Dans l’interface utilisateur à thème, zones de liste déroulante et les listes déroulantes suivent les thèmes standard pour les contrôles.

#### <a name="layout"></a>Mise en page
 Zones de liste déroulante et les listes déroulantes doivent être dimensionnés en fonction du contenu, ne pas à la largeur de la fenêtre dans lequel elles sont affichées, ni d’arbitrairement correspond à la longueur d’un champ long, par exemple un chemin d’accès.

 ![Drop incorrect&#45;vers le bas disposition](../../extensibility/ux-guidelines/media/0707-03-incorrectdropdownlayout.png "0707-03_IncorrectDropDownLayout")

 **Longueur de champ incorrect pour un contrôle de liste déroulante**

 ![Drop correct&#45;vers le bas disposition](../../extensibility/ux-guidelines/media/0707-04-correctdropdownlayout.png "0707-04_CorrectDropDownLayout")

 **Longueur de champ correct pour un contrôle de liste déroulante**

### <a name="BKMK_CheckBoxes"></a> Cases à cocher
 Pour le comportement de l’interaction typique, suivez le [instructions de bureau de Windows pour les cases à cocher](https://msdn.microsoft.com/library/windows/desktop/dn742401\(v=vs.85\).aspx).

#### <a name="visual-style"></a>Style visuel

- Dans les boîtes de dialogue Utilitaire n'effectuez pas remodéliser le contrôle. Utiliser le style de base intrinsèque au contrôle.

- Dans l’interface utilisateur à thème, cases à cocher suivent les thèmes standard pour les contrôles.

#### <a name="specialized-interactions"></a>Interactions spécialisées

- Interaction avec une case à cocher ne doit jamais affiche une boîte de dialogue ou accéder à une autre zone.

- Aligner les cases à cocher avec la ligne de base de la première ligne de texte.

     ![Alignement de la case à cocher incorrect](../../extensibility/ux-guidelines/media/0707-05-incorrectcheckboxalign.png "0707-05_IncorrectCheckBoxAlign") **alignement de la case à cocher Incorrect : Case à cocher est centrée sur le texte.**

     ![Corriger l’alignement de la case à cocher](../../extensibility/ux-guidelines/media/0707-06-correctcheckboxalign.png "0707-06_CorrectCheckBoxAlign") **corriger l’alignement de la case à cocher : Case à cocher est aligné avec la ligne de base de la première ligne de texte.**

### <a name="BKMK_RadioButtons"></a> Cases d’option
 Pour le comportement de l’interaction typique, suivez le [instructions Windows Desktop pour les boutons radio](https://msdn.microsoft.com/library/windows/desktop/dn742436\(v=vs.85\).aspx).

#### <a name="visual-style"></a>Style visuel
 Dans les boîtes de dialogue Utilitaire n'effectuez pas les boutons de case d’option de style. Utiliser le style de base intrinsèque au contrôle.

#### <a name="specialized-interactions"></a>Interactions spécialisées
 Il n’est pas nécessaire d’utiliser un cadre de groupe pour encadrer les choix de cases d’option.

### <a name="BKMK_GroupFrames"></a> Images de groupe
 Pour le comportement de l’interaction typique, suivez le [les instructions pour les cadres de groupe Windows Desktop](https://msdn.microsoft.com/library/windows/desktop/dn742405\(v=vs.85\).aspx).

#### <a name="visual-style"></a>Style visuel
 Dans les boîtes de dialogue Utilitaire n'effectuez pas les trames de groupe de style. Utiliser le style de base intrinsèque au contrôle.

#### <a name="layout"></a>Mise en page

- Il n’est pas nécessaire d’utiliser un cadre de groupe pour encadrer les choix de cases d’option, sauf si vous avez besoin de maintenir la distinction de groupe dans une disposition étroite.

- N’utilisez jamais un cadre de groupe pour un seul contrôle.

- Parfois, il est acceptable d’utiliser une règle horizontale au lieu d’un conteneur d’image de groupe.

## <a name="BKMK_TextControls"></a> Contrôles de texte

### <a name="labels"></a>Étiquettes

#### <a name="active-label-state"></a>État de l’étiquette active

##### <a name="utility-standard-dialogs"></a>Boîtes de dialogue (standard) utilitaire)

- En règle générale, suivez les instructions de bureau de Windows pour les étiquettes de contrôle.

- Dans les boîtes de dialogue Utilitaire étiquettes doivent apparaître en gras, dans la couleur de police et texte environnement standard. Consultez [polices et mise en forme pour Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md).

- Points de suspension doivent toujours suivre des étiquettes.

##### <a name="signature-themed-dialogs"></a>Boîtes de dialogue Signature (thèmes))
 Contrôles d’étiquette peuvent être en gras ou gris clair.

#### <a name="disabled-label-state"></a>État de l’étiquette désactivé
 Étiquettes doivent refléter l’apparence du contrôle qu'auquel elles sont associées. Par exemple, si le contrôle associé est désactivé, l’étiquette doit apparaître en gris et désactivé. Cela est généralement géré par le système d’exploitation et nécessite un traitement spécial.

#### <a name="dynamic-labels"></a>Étiquettes dynamiques
 Modification des étiquettes dynamique basée sur la sélection actuelle. Si possible, utilisez des étiquettes dynamiques dans les dispositions maître/détail pour aider l’utilisateur à comprendre que les informations affichées convient une sélection spécifique et les informations générales pas.

 ![Étiquette dynamique utilisée avec un contenu dynamique](../../extensibility/ux-guidelines/media/070702-01-dynamiclabel.png "070702-01_DynamicLabel")

 **Exemple d’une étiquette dynamique utilisée avec un contenu dynamique**

#### <a name="instructional-text"></a>Texte d’instructions
 Certains éléments d’interface tirer parti de texte d’instructions pour aider l’utilisateur à comprendre l’objectif de l’interface utilisateur ou pour indiquer l’action à effectuer.

- Texte d’instructions est plus courant en haut des boîtes de dialogue, mais il peut apparaître dans d’autres domaines pour donner instruction à un regroupement de contrôle complexe.

- Texte d’instructions est non interactif, mais peut contenir des liens hypertexte vers des rubriques d’aide.

- Utilisez le texte d’instructions avec parcimonie et uniquement si nécessaire.

##### <a name="formatting"></a>Mise en forme
 Texte d’instructions doit être la police d’environnement, texte du contrôle (non-à thème) standard. Consultez [polices et mise en forme pour Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md).

 Pour plus d’informations sur l’écriture de texte d’instructions, consultez [l’interface utilisateur texte et la terminologie](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology).

 ![Mise en forme du texte d’instructions](../../extensibility/ux-guidelines/media/070702-02-instructionaltextformatting.png "070702-02_InstructionalTextFormatting")

 **Texte d’instructions dans une boîte de dialogue Visual Studio**

#### <a name="informational-text"></a>Texte informatif
 Texte d’information est un texte qui donne des informations utilisateur supplémentaires. Il peut être statique ou dynamique ou comme une notification. Il est toujours en lecture seule, mais si elle est utile pour l’utilisateur ait la possibilité de copier les informations, texte dynamique doit être placé dans un conteneur de contrôle tel qu’un champ de texte en lecture seule.

##### <a name="dynamic-context-specific-text"></a>Texte (contextuelles) dynamique
 Informations dynamiques texte change en fonction du contexte, tel que lorsque l’utilisateur bascule le focus. Souvent, mais pas toujours, le contenu dynamique est associé à une étiquette dynamique.

 ![Texte d’information dynamique](../../extensibility/ux-guidelines/media/070702-03-informationaldynamictext.png "070702-03_InformationalDynamicText")

 **Texte d’information dynamique change selon le contexte.**

##### <a name="formatting"></a>Mise en forme
 Il existe deux manières d’afficher les champs de texte en lecture seule : soit directement sur l’interface utilisateur de surface (voir ci-dessus) ou contenues dans un autre contrôle, tel qu’une zone d’image ou texte de groupe. Une est correcte en fonction de la situation. Il incombe du Concepteur de fonctionnalités pour déterminer comment présenter les informations en lecture seule.

 Texte peut être à l’intérieur d’une zone de texte en lecture seule. Cela indique généralement que le contenu peut être sélectionné et copié, bien qu’il ne peut pas être modifié.

 ![Mise en forme pour la lecture de texte informatif&#45;seuls des champs](../../extensibility/ux-guidelines/media/070702-04-informationalformatting.png "070702-04_InformationalFormatting")

 **Texte d’information de mise en forme pour les champs en lecture seule**

#### <a name="watermarks"></a>Filigranes
 Le libellé peut être le même, la différence entre les filigranes et des instructions est que les filigranes sont remplacées par contenu lorsque la fenêtre/contrôle n’est pas vide et un texte d’instructions reste visible à tout moment.

 Filigranes doivent être utilisés quand une fenêtre ou un contrôle est vide. Ils indiquent ce qui doit être fait pour remplir la zone et peuvent inclure des liens d’action pour ouvrir des fenêtres pertinentes, comme une source de glissement.

##### <a name="visual-style"></a>Style visuel

- Filigranes doivent être centrées horizontalement dans la fenêtre.

- Filigranes doivent être aligné au centre, ne pas aligné à gauche.

- Filigranes peuvent être centrés verticalement ou positionnés au début de la zone. Si, en haut de la zone, il doit y avoir suffisamment d’espace ci-dessus afin que le filigrane de faire ressortir.

- Utilisez le `Environment.GrayText` police d’environnement standard et de jeton de couleur. Liens hypertexte doivent utiliser les jetons de lien hypertexte standard partagé : `Environment.PanelHyperlink`, `Environment.PanelHyperlinkHover`, `Environment.PanelHyperlinkPressed`, et `Environment.PanelHyperlinkDisabled`.

- Filigranes ne peuvent pas être sélectionnés sur l’arrière-plan

- Si possible, inclure des liens dans le filigrane pour aider l’utilisateur.

  ![Un texte dans une fenêtre de concepteur en filigrane](../../extensibility/ux-guidelines/media/070702-05-watermark1.png "070702-05_Watermark1")

  ![Un texte dans une fenêtre outil en filigrane](../../extensibility/ux-guidelines/media/070702-06-watermark2.png "070702-06_Watermark2")

  **Exemples de texte de filigrane dans Visual Studio**

## <a name="BKMK_ButtonsAndHyperlinks"></a> Boutons et des liens hypertexte

### <a name="overview"></a>Vue d'ensemble
 Contrôles de boutons et de liens (liens) doivent suivre [des conseils de Windows Desktop base sur les liens hypertexte](https://msdn.microsoft.com/library/windows/desktop/dn742406\(v=vs.85\).aspx) pour l’utilisation, le libellé, dimensionnement et l’espacement.

### <a name="choosing-between-buttons-and-links"></a>Choix entre les boutons et les liens
 En règle générale, les boutons ont été utilisés pour les actions et des liens hypertexte qui ont été réservées pour la navigation. Boutons peuvent être utilisés dans tous les cas, mais le rôle de liens a été développé dans Visual Studio afin que les boutons et les liens ne sont plus interchangeables dans certaines conditions.

 Quand utiliser les boutons de commande :

- Commandes principales

- Affichage windows utilisé pour recueillir l’entrée ou faire des choix, même si elles sont des commandes secondaires

- Actions destructrices ou irréversibles

- Boutons d’engagement dans les Assistants et les flux de page

  Éviter les boutons de commande dans les fenêtres Outil, ou si vous avez besoin de plus de deux mots pour l’étiquette. Liens peuvent avoir des étiquettes de plus de temps.

  Quand utiliser des liens :

- Navigation vers une autre fenêtre, document ou page web

- Situations nécessitant une étiquette plus longue ou courte phrase pour décrire l’objectif de l’action

- Espaces étroite où un bouton serait surcharger l’interface utilisateur, à condition que l’action n’est pas destructifs ou irréversible

- Minimise les commandes secondaires dans les situations où il existe de nombreuses commandes

#### <a name="examples"></a>Exemples
 ![Liens de commande de barre d’informations suivant un message d’état](../../extensibility/ux-guidelines/media/070703-01-commandlinkinfobar.png "070703-01_CommandLinkInfobar")

 **Commandes liens utilisés dans la barre d’informations suivant un message d’état**

 ![Liens utilisés dans la fenêtre contextuelle CodeLens](../../extensibility/ux-guidelines/media/070703-02-linksincodelens.png "070703-02_LinksInCodeLens")

 **Liens utilisés dans la fenêtre contextuelle CodeLens**

 ![Liens utilisés comme commandes secondaires](../../extensibility/ux-guidelines/media/070703-03-linksassecondarycommands.png "070703-03_LinksAsSecondaryCommands")

 **Liens utilisés pour les commandes secondaire où boutons bénéficierait de trop peu d’attention**

### <a name="common-buttons"></a>Boutons courants

#### <a name="text"></a>Texte
 Suivez les instructions de l’écriture de [l’interface utilisateur texte et la terminologie](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology).

#### <a name="visual-style"></a>Style visuel

##### <a name="standard-dialogs"></a>Boîtes de dialogue standard
 La plupart des boutons dans Visual Studio s’affiche dans les boîtes de dialogue standard et ne doit pas être filtrables. Ils doivent refléter l’apparence standard des boutons comme stipulé par le système d’exploitation.

##### <a name="themed"></a>À thème
 Dans certains cas, boutons peuvent être utilisées dans l’interface utilisateur de style et ces boutons doivent être présentent en conséquence. Consultez [boîtes de dialogue](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs) pour plus d’informations sur les contrôles à thème.

### <a name="special-buttons"></a>Boutons spéciaux

#### <a name="browse-buttons"></a>Parcourir... boutons
 **[Parcourir...]**  boutons sont utilisés dans les grilles, les boîtes de dialogue et fenêtres Outil et autres éléments d’interface utilisateur non modales. Ils affichent un sélecteur qui aide l’utilisateur à remplir une valeur dans un contrôle. Il existe deux variantes de ce bouton, long et court.

 ![Long &#91;Parcourir... &#93; bouton](../../extensibility/ux-guidelines/media/070703-04-browselong.gif "070703-04_BrowseLong")

 **Le bouton long [Parcourir...]**

 ![Abrégée des points de suspension&#45;uniquement &#91;Parcourir... &#93; bouton](../../extensibility/ux-guidelines/media/070703-05-browseshort.gif "070703-05_BrowseShort")

 **Le bouton court portant uniquement sur les points de suspension [...]**

 Quand utiliser le bouton court de points de suspension uniquement :

- S’il existe plusieurs long **[Parcourir...]**  bouton dans une boîte de dialogue, telles que lorsque plusieurs champs permettant la navigation. Utilisez court **[...]**  bouton pour chacun d’eux à éviter les clés d’accès à confusion créées par cette situation (**& Parcourir** et **& rcourir le** dans la même boîte de dialogue).

- Dans une boîte de dialogue étroite, ou lorsqu’il n’existe aucun emplacement raisonnable pour le bouton long.

- Si le bouton apparaît dans un contrôle de grille.

  Instructions pour l’aide du bouton :

- N’utilisez pas une clé d’accès. Pour accéder à l’aide du clavier, l’utilisateur doit de tabulation du contrôle adjacentes. Assurez-vous que l’ordre de tabulation est telle que n’importe quel bouton Parcourir immédiatement après le champ qui remplira. N’utilisez jamais un trait de soulignement ci-dessous la première période.

- Définir le Microsoft Active Accessibility (MSAA) **nom** propriété **Parcourir...**  (y compris les points de suspension) afin que l’écran lecteurs lue en tant que « Browse » et pas « point-point-point » ou « période période période. » Pour les contrôles managés, cela signifie que le **AccessibleName** propriété.

- N’utilisez jamais de points de suspension **[...]**  bouton pour quoi que ce soit, à l’exception d’une action de navigation. Par exemple, si vous avez besoin d’un **[nouveau...]**  bouton mais n’avez pas assez de place pour le texte, puis la boîte de dialogue doit être redéfinie.

##### <a name="sizing-and-spacing"></a>Dimensionnement et l’espacement
 ![Dimensionnement &#91;Parcourir... &#93; boutons](../../extensibility/ux-guidelines/media/070703-06-browsesizing.png "070703-06_BrowseSizing")

 **Boutons de dimensionnement [Parcourir...]**

 ![Espacement &#91;Parcourir... &#93; boutons](../../extensibility/ux-guidelines/media/070703-07-browsespacing.png "070703-07_BrowseSpacing")

 **Boutons d’espacement [Parcourir...]**

#### <a name="graphical-buttons"></a>Boutons graphiques
 Certains boutons doivent toujours utiliser une image graphique et n’incluez jamais de texte pour économiser l’espace et éviter les problèmes de localisation. Ceux-ci sont souvent utilisés dans les sélecteurs de champ et les autres listes pouvant être triés.

> [!NOTE]
> Les utilisateurs doivent TAB pour accéder à ces boutons (il n’existe aucune clé d’accès), par conséquent, les placer dans un ordre cohérent. Mapper la propriété name du bouton à l’action nécessaire afin que les lecteurs d’écran interprètent correctement l’action du bouton.

|||
|-|-|
|Ajouter|![Graphical "Add" button](../../extensibility/ux-guidelines/media/070703-08-buttonadd.png "070703-08_ButtonAdd")|
|Remove|![Graphique bouton « Supprimer »](../../extensibility/ux-guidelines/media/070703-09-buttonremove.png "070703-09_ButtonRemove")|
|Ajouter tout|![Bouton graphique « Ajouter tout »](../../extensibility/ux-guidelines/media/070703-10-buttonaddall.png "070703-10_ButtonAddAll")|
|Supprimer tout|![Bouton graphique « Supprimer tout »](../../extensibility/ux-guidelines/media/070703-11-buttonremoveall.png "070703-11_ButtonRemoveAll")|
|Monter|![Bouton graphique « Monter »](../../extensibility/ux-guidelines/media/070703-12-buttonmoveup.png "070703-12_ButtonMoveUp")|
|Descendre|![Bouton graphique « Descendre »](../../extensibility/ux-guidelines/media/070703-13-buttonmovedown.png "070703-13_ButtonMoveDown")|
|Supprimer|![Graphical "Delete" button](../../extensibility/ux-guidelines/media/070703-14-buttondelete.png "070703-14_ButtonDelete")|

##### <a name="sizing-and-spacing"></a>Dimensionnement et l’espacement
 Dimensionnement des boutons graphiques est identique à la version courte de la **[Parcourir...]**  bouton (26 x 23 pixels) :

 ![Bouton avec et sans affichage de couleur transparente](../../extensibility/ux-guidelines/media/070703-15-graphicalbuttonspacing.png "070703-15_GraphicalButtonSpacing")

 **Apparence d’une image de graphique sur le bouton, avec et sans affichage de couleur transparente**

### <a name="hyperlinks"></a>Liens hypertexte
 Des liens hypertexte sont bien adaptés aux actions de navigation telles que l’ouverture d’une rubrique d’aide, boîte de dialogue modale ou l’Assistant. Si un lien hypertexte est utilisé pour une commande, il doit toujours afficher une modification visible et sensible à l’interface utilisateur. En règle générale, les actions de validation à une action (par exemple, enregistrer, Annuler et supprimer) sont communiquées mieux à l’aide d’un bouton.

#### <a name="writing-style"></a>Style d’écriture
 Suivez le [conseils Windows Desktop pour le texte de l’interface utilisateur](https://msdn.microsoft.com/library/windows/desktop/dn742478\(v=vs.85\).aspx). N’utilisez pas « En savoir plus à propos, » « Dire me plus sur » ou « Get help avec ce » formulation. Au lieu de cela, une expression texte de lien d’aide en termes de la question principale ayant obtenu une réponse par le contenu d’aide. Par exemple, «**comment ajouter un serveur à l’Explorateur de serveurs ?**»

#### <a name="visual-style"></a>Style visuel

- Utilisent toujours des liens hypertexte [The VSColor Service](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService). Si un lien hypertexte n’est pas un style correctement, il clignote en rouge lorsqu’il est actif ou affiche une couleur différente après avoir visité.

- N’incluez pas de traits de soulignement au contrôle positionné état sauf si le lien est un fragment de phrase au sein d’une phrase complète, comme dans un filigrane.

- Traits de soulignement ne doivent pas apparaître sur le pointage. Au lieu de cela, les commentaires à l’utilisateur que le lien est actif sont un changement de couleur légère et le curseur de lien approprié.

## <a name="BKMK_TreeViews"></a> Vues de l’arborescence

### <a name="overview"></a>Vue d'ensemble
 Vues de l’arborescence fournissent un moyen d’organiser complexe répertorie dans des groupes parent-enfant. Un utilisateur peut développer ou réduire des groupes parents pour afficher ou masquer les éléments enfants sous-jacents. Chaque élément dans une vue d’arborescence peut être sélectionné pour fournir des actions.

 Cette rubrique décrit les utilisations acceptables, une conception appropriée et fonctionnalités de vues de l’arborescence.

#### <a name="in-this-topic"></a>Dans cette rubrique

- [Style visuel](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViewVisualStyle)

- [Interactions](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViewInteractions)

### <a name="BKMK_TreeViewVisualStyle"></a> Style visuel

#### <a name="expanders"></a>Développeurs
 Contrôles d’arborescence doivent être conforme à la conception de l’expander utilisée par Windows et Visual Studio. Chaque nœud utilise un contrôle expander pour mettre en évidence ou masquer des éléments sous-jacents. À l’aide d’un contrôle expander fournit une cohérence pour les utilisateurs peuvent rencontrer des arborescences différentes au sein de Windows et Visual Studio.

 ![Corriger le contrôle tree view](../../extensibility/ux-guidelines/media/070705-1-treeviewcorrect.png "070705-1_TreeViewCorrect")

 **Correct : style approprié de nœud d’arborescence à l’aide d’un contrôle expander**

 ![Nœuds d’une arborescence incorrecte](../../extensibility/ux-guidelines/media/070705-2-treeviewincorrect1.png "070705-2_TreeViewIncorrect1")

 **Incorrect : le style incorrect de nœud d’arborescence**

#### <a name="selection"></a>Sélection
 Lorsqu’un nœud est sélectionné dans l’arborescence, la mise en surbrillance doit se développer pour la largeur totale du contrôle arborescence. Cela permet aux utilisateurs à identifier clairement quel élément qu’ils ont sélectionnées. Couleurs de la sélection doivent refléter le thème de Visual Studio actuel.

 ![Corriger le contrôle tree view](../../extensibility/ux-guidelines/media/070705-1-treeviewcorrect.png "070705-1_TreeViewCorrect")

 **Correct : mise en surbrillance du nœud sélectionné correspond à toute la largeur du contrôle arborescence.**

 ![Mise en surbrillance d’une arborescence incorrecte](../../extensibility/ux-guidelines/media/070705-3-treeviewincorrect2.png "070705-3_TreeViewIncorrect2")

 **Incorrect : mise en surbrillance du nœud sélectionné ne correspond pas toute la largeur du contrôle arborescence.**

#### <a name="icons"></a>Icônes
 Icônes doivent uniquement être utilisées dans les contrôles d’arborescence si ils permettent d’identifier visuellement les différences entre les éléments. En règle générale, les icônes doivent être utilisés uniquement dans les listes hétérogènes dans lequel les icônes communiquent les informations pour différencier les types d’éléments. Dans une liste homogène à l’aide des icônes peuvent fréquemment être vu comme un bruit et doit être évitée. Dans ce cas, l’icône de groupe (parent) peut transmettre le type d’éléments qu’il contient. L’exception à cette règle serait si l’icône est dynamique et est utilisée pour indiquer l’état.

#### <a name="scroll-bars"></a>Barres de défilement
 Barres de défilement doivent toujours être masquées si le contenu tient dans le contrôle arborescence. Il est acceptable pour les barres de défilement pour être masquées ou semi-transparent dans une fenêtre de défilement et s’affichent lorsque la fenêtre contenant l’arborescence a le focus ou lors de pointage de l’arborescence afficher lui-même.

 ![Arborescence avec barres de défilement](../../extensibility/ux-guidelines/media/070705-4-scrollbars.png "070705-4_Scrollbars")

 **Les deux barres de défilement horizontales et verticales sont affichées, car le contenu a dépassé les limites du contrôle arborescence.**

### <a name="BKMK_TreeViewInteractions"></a> Interactions

#### <a name="context-menus"></a>Menus contextuels
 Un nœud d’arborescence peut révéler des options de sous-menu dans un menu contextuel. En règle générale, cela se produit lorsqu’un utilisateur a cliqué un élément ou appuyé sur la touche de Menu un clavier Windows avec l’élément sélectionné. Il est important que le nœud Obtient le focus et qu’il est sélectionné. Cela permet à l’utilisateur d’identifier quel élément auquel appartient le sous-menu.

 ![Menu nœud et le contexte d’arbre sélectionné](../../extensibility/ux-guidelines/media/070705-5-contextmenu.png "070705-5_ContextMenu")

 **L’élément produisant a le focus de gains de menu contextuel pour notifier l’utilisateur auquel l’élément a été sélectionné.**

#### <a name="keyboard"></a>Clavier
 L’arborescence doit fournir la possibilité de sélectionner des éléments et développer/réduire les nœuds à l’aide du clavier. Cela garantit que la navigation répond à nos exigences en termes d’accessibilité.

##### <a name="tree-view-control"></a>Contrôle d’arborescence
 Contrôles d’arborescence de Visual Studio doivent suivre la navigation au clavier courants :

- **Flèche haut :** Sélectionner des éléments en déplaçant l’arborescence

- **Bas :** Sélectionner des éléments en déplaçant vers le bas de l’arborescence

- **Flèche droite :** Développez un nœud dans l’arborescence

- **Flèche gauche :** Réduire un nœud dans l’arborescence

- **Entrez la clé :** Lancer, charger, exécuter l’élément sélectionné

##### <a name="trid-tree-view-and-grid-view"></a>Grid (vue de l’arborescence et affichage de grille)
 Un contrôle Grid est un contrôle complexe qui contienne une arborescence dans une grille. Développement, la réduction et la navigation dans l’arborescence doivent respecter les mêmes commandes de clavier comme une arborescence, avec les ajouts suivants :

- **Flèche droite :** Développez le nœud. Une fois que le nœud est développé, il doit continuer accédant à la colonne le plus proche sur la droite. Navigation doit s’arrêter à la fin de la ligne.

- **Onglet :** Navigue vers la cellule la plus proche sur la droite.  À la fin de la ligne, la navigation se poursuit à la ligne suivante.

- **Maj + Tab :** Navigue vers la cellule la plus proche sur la gauche.  Au début de la ligne, la navigation se poursuit à la cellule la plus à droite de la ligne précédente.

  ![Contrôle Grid dans Visual Studio](../../extensibility/ux-guidelines/media/070705-6-trid.png "070705-6_Trid")

  **Un contrôle Grid dans Visual Studio**
