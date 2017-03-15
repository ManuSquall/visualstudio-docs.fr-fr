---
title: "Mod&#232;les de contr&#244;le courants de Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3e893949-6398-42f1-9eab-a8d8c2b7f02d
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# Mod&#232;les de contr&#244;le courants de Visual Studio
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

##  <a name="BKMK_CommonControls"></a> Contrôles courants  
  
### Vue d'ensemble  
 Contrôles communs constituent la majeure partie de l'interface utilisateur dans Visual Studio. Contrôles les plus courants utilisés dans l'interface de Visual Studio doivent suivre le [directives d'interaction Windows Desktop](https://msdn.microsoft.com/library/windows/desktop/dn742399.aspx). Ce document est spécifique à Visual Studio et décrit des situations particulières ou détails de compléter ces recommandations pour Windows.  
  
#### Contrôles communs dans cette rubrique.  
  
-   [Barres de défilement](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_Scrollbars)  
  
-   [Champs d'entrée](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_InputFields)  
  
-   [Zones de liste déroulante et les listes déroulantes](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ComboBoxesAndDropDowns)  
  
-   [Cases à cocher](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CheckBoxes)  
  
-   [Cases d'option](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_RadioButtons)  
  
-   [Images de groupe](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_GroupFrames)  
  
-   [Contrôles de texte](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)  
  
-   [Boutons et des liens hypertexte](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)  
  
-   [Vues de l'arborescence](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViews)  
  
#### Style visuel  
 La première chose à prendre en compte lors de la stylisation de contrôles est que les contrôles seront utilisées dans l'interface utilisateur à thème. Contrôles de l'interface utilisateur standard sont l'interface utilisateur sans thème et doit suivre [style normal de Windows Desktop](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742399\(v=vs.85\).aspx), ce qui signifie qu'ils ne sont pas ré\-basé sur un modèle et qu'il doivent apparaître dans leur apparence de contrôle par défaut.  
  
-   **Les boîtes de dialogue standard \(utilitaire\):** pas à thème. Ne pas re\-template. Utilisez les valeurs par défaut du style de contrôle de base.  
  
-   **Fenêtres Outil, les éditeurs de document, les surfaces de conception et les boîtes de dialogue à thème :** utiliser apparence à thème spécialisée à l'aide du service de couleur.  
  
###  <a name="BKMK_Scrollbars"></a> Barres de défilement  
 Barres de défilement doivent suivre [modèles courants d'interaction des barres de défilement Windows](https://msdn.microsoft.com/en-us/library/windows/desktop/bb787527\(v=vs.85\).aspx) sauf si elles sont étendues avec les informations de contenu, comme dans l'éditeur de code.  
  
###  <a name="BKMK_InputFields"></a> Champs d'entrée  
 Pour le comportement d'interaction typique, suivez les [instructions de bureau Windows pour les zones de texte](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742442\(v=vs.85\).aspx).  
  
#### Style visuel  
  
-   Champs d'entrée ne doivent pas un style dans les boîtes de dialogue utilitaire. Utiliser le style de base intrinsèque au contrôle.  
  
-   Champs d'entrée à thème doivent uniquement servir dans les fenêtres Outil et boîtes de dialogue à thème.  
  
#### Interactions spécialisées  
  
-   Les champs en lecture seule aura un arrière\-plan grisé \(désactivé\), mais de premier plan par défaut \(actif\).  
  
-   Requis champs doivent avoir **\< requis \>** en tant que filigranes dans celles\-ci. Vous ne devez pas modifier la couleur d'arrière\-plan, sauf dans les rares cas.  
  
-   Validation de l'erreur : consultez [Notifications et progression pour Visual Studio](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)  
  
-   Champs d'entrée doivent être dimensionnées en fonction du contenu, ne pas à la largeur de la fenêtre dans lequel elles sont affichées, ni aux arbitrairement correspond à la longueur d'un champ long, par exemple un chemin d'accès. Longueur peut être une indication à l'utilisateur de limitations concernant le nombre de caractères est autorisé dans le champ.  
  
     ![Incorrect input field control width](../../extensibility/ux-guidelines/media/0707-01_incorrectinputfieldcontrol.png "0707\-01\_IncorrectInputFieldControl")   
     **Longueur de champ d'entrée incorrecte : il est improbable que le nom de cette longueur.**  
  
     ![Correct input field control width](../../extensibility/ux-guidelines/media/0707-02_correctinputfieldcontrol.png "0707\-02\_CorrectInputFieldControl")   
     **Corriger la longueur du champ d'entrée : le champ d'entrée est une largeur raisonnable pour le contenu attendu.**  
  
###  <a name="BKMK_ComboBoxesAndDropDowns"></a> Zones de liste déroulante et les listes déroulantes  
 Pour le comportement d'interaction typique, suivez les [les instructions pour les listes déroulantes et zones de liste déroulante Windows Desktop](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742404\(v=vs.85\).aspx).  
  
#### Style visuel  
  
-   Dans les boîtes de dialogue utilitaire ne faire pas re\-modèle du contrôle. Utiliser le style de base intrinsèque au contrôle.  
  
-   Dans l'interface utilisateur à thème, listes déroulantes et les zones de liste déroulante suivent les thèmes standard pour les contrôles.  
  
#### Disposition  
 Déroulants et les zones de liste déroulante doivent être dimensionnées en fonction du contenu, ne pas à la largeur de la fenêtre dans lequel elles sont affichées, ni aux arbitrairement correspond à la longueur d'un champ long, par exemple un chemin d'accès.  
  
 ![Incorrect drop&#45;down layout](../../extensibility/ux-guidelines/media/0707-03_incorrectdropdownlayout.png "0707\-03\_IncorrectDropDownLayout")  
  
 **Longueur de champ incorrect pour un contrôle de liste déroulante**  
  
 ![Correct drop&#45;down layout](../../extensibility/ux-guidelines/media/0707-04_correctdropdownlayout.png "0707\-04\_CorrectDropDownLayout")  
  
 **Longueur de champ est correct pour un contrôle de liste déroulante**  
  
###  <a name="BKMK_CheckBoxes"></a> Cases à cocher  
 Pour le comportement d'interaction typique, suivez les [instructions de bureau Windows pour les cases à cocher](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742401\(v=vs.85\).aspx).  
  
#### Style visuel  
  
-   Dans les boîtes de dialogue utilitaire ne faire pas re\-modèle du contrôle. Utiliser le style de base intrinsèque au contrôle.  
  
-   Dans l'interface utilisateur à thème, cases à cocher suivre les thèmes standard pour les contrôles.  
  
#### Interactions spécialisées  
  
-   L'interaction avec une case à cocher ne doit jamais apparaître une boîte de dialogue ou naviguer vers une autre zone.  
  
-   Aligner les cases à cocher avec la ligne de base de la première ligne de texte.  
  
     ![Incorrect check box alignment](../../extensibility/ux-guidelines/media/0707-05_incorrectcheckboxalign.png "0707\-05\_IncorrectCheckBoxAlign")   
     **Alignement de la case à cocher incorrect : case à cocher est centré sur le texte.**  
  
     ![Correct check box alignment](../../extensibility/ux-guidelines/media/0707-06_correctcheckboxalign.png "0707\-06\_CorrectCheckBoxAlign")   
     **Corriger l'alignement de la case à cocher : case à cocher est alignée avec la ligne de base de la première ligne de texte.**  
  
###  <a name="BKMK_RadioButtons"></a> Cases d'option  
 Pour le comportement d'interaction typique, suivez les [instructions de bureau Windows de cases d'option](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742436\(v=vs.85\).aspx).  
  
#### Style visuel  
 Dans les boîtes de dialogue utilitaire ne faire pas style cases d'option. Utiliser le style de base intrinsèque au contrôle.  
  
#### Interactions spécialisées  
 Il n'est pas nécessaire d'utiliser un cadre de groupe pour encadrer les choix de cases d'option.  
  
###  <a name="BKMK_GroupFrames"></a> Images de groupe  
 Pour le comportement d'interaction typique, suivez les [instructions de bureau Windows pour les cadres de groupe](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742405\(v=vs.85\).aspx).  
  
#### Style visuel  
 Dans les boîtes de dialogue utilitaire, n'effectuez pas les trames de groupe de style. Utiliser le style de base intrinsèque au contrôle.  
  
#### Disposition  
  
-   Il n'est pas nécessaire d'utiliser un cadre de groupe pour encadrer les choix de cases d'option, sauf si vous avez besoin de maintenir la distinction de groupe dans une disposition étroite.  
  
-   N'utilisez jamais un cadre de groupe pour un seul contrôle.  
  
-   Parfois, il est acceptable d'utiliser une règle horizontale au lieu d'un conteneur d'image de groupe.  
  
##  <a name="BKMK_TextControls"></a> Contrôles de texte  
  
### Étiquettes  
  
#### État de l'étiquette active  
  
##### Boîtes de dialogue \(standard\) utilitaire\)  
  
-   En général, suivez les instructions de bureau Windows pour les étiquettes de contrôle.  
  
-   Dans les boîtes de dialogue Utilitaire étiquettes doivent apparaître en gras, dans l'environnement standard police et couleur du texte. Consultez [Mise en forme pour Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md).  
  
-   Ellipses doivent toujours observer les étiquettes.  
  
##### Signature \(thèmes\) les boîtes de dialogue\)  
 Contrôles d'étiquette peuvent être en gras ou gris clair.  
  
#### État de l'étiquette désactivé  
 Étiquettes doivent refléter l'apparence du contrôle qu'auquel ils sont associés. Par exemple, si le contrôle associé est désactivé, l'étiquette doit apparaître en gris et désactivé. Cela est généralement gérée par le système d'exploitation et nécessite un traitement spécial.  
  
#### Étiquettes dynamiques  
 Modification des étiquettes dynamique basée sur la sélection actuelle. Si possible, utilisez des étiquettes dynamiques dans les mises en page maître\/détail pour aider l'utilisateur à comprendre que les informations affichées ne sont applique à une sélection spécifique et des informations générales non.  
  
 ![Dynamic label used with dynamic content](../../extensibility/ux-guidelines/media/070702-01_dynamiclabel.png "070702\-01\_DynamicLabel")  
  
 **Exemple d'une étiquette dynamique utilisée avec un contenu dynamique**  
  
#### Texte d'instructions  
 Certains éléments d'interface bénéficient du texte d'instructions pour aider l'utilisateur à comprendre l'objectif de l'interface utilisateur ou pour indiquer l'action à effectuer.  
  
-   Texte d'instructions est plus courant en haut des boîtes de dialogue, mais peut apparaître dans d'autres domaines pour donner instruction à un regroupement de contrôle complexe.  
  
-   Texte d'instructions est non interactif, mais peut contenir des liens hypertexte vers des rubriques d'aide.  
  
-   Utilisez le texte d'instructions avec modération et uniquement si nécessaire.  
  
##### Mise en forme  
 Texte d'instructions doit être police d'environnement, texte du contrôle \(sans thème\) standard. Consultez [Mise en forme pour Visual Studio](../../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md).  
  
 Pour plus d'informations sur l'écriture d'instructions, consultez la page [Texte de l'interface utilisateur et la terminologie](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology).  
  
 ![Instructional text formatting](../../extensibility/ux-guidelines/media/070702-02_instructionaltextformatting.png "070702\-02\_InstructionalTextFormatting")  
  
 **Texte d'instructions dans une boîte de dialogue Visual Studio**  
  
#### Texte d'information  
 Texte d'information est le texte qui donne des informations utilisateur supplémentaires. Il peut être statique ou dynamique ou comme une notification. Il est toujours en lecture seule, mais si elle est utile pour l'utilisateur doit avoir la possibilité de copier les informations, texte dynamique doit être placé dans un conteneur de contrôle comme un champ de texte en lecture seule.  
  
##### Texte \(contextuelle\) dynamique  
 Informations dynamiques texte change en fonction du contexte, tel que lorsque l'utilisateur bascule le focus. Souvent, mais pas toujours, le contenu dynamique est associé à une étiquette dynamique.  
  
 ![Dynamic information text](../../extensibility/ux-guidelines/media/070702-03_informationaldynamictext.png "070702\-03\_InformationalDynamicText")  
  
 **Texte d'information dynamique change en fonction du contexte.**  
  
##### Mise en forme  
 Il existe deux manières d'afficher les champs de texte en lecture seule : directement sur l'interface utilisateur \(voir ci\-dessus\) ou contenues dans un autre contrôle, tel qu'une zone de groupe image ou texte. Une est correct en fonction de la situation. Il incombe au Concepteur de fonctionnalités pour déterminer comment présenter les informations en lecture seule.  
  
 Texte peut être à l'intérieur d'une zone de texte en lecture seule. Cela indique généralement que le contenu peut être sélectionné et copié, bien qu'il ne peut pas être modifié.  
  
 ![Informational text formatting for read&#45;only fields](../../extensibility/ux-guidelines/media/070702-04_informationalformatting.png "070702\-04\_InformationalFormatting")  
  
 **Mise en forme du texte d'informations pour champs en lecture seule**  
  
#### Filigranes  
 Le libellé peut être le même, la différence entre les filigranes et des instructions est que les filigranes sont remplacés par le contenu lorsque la fenêtre\/contrôle n'est pas vide et un texte d'instructions reste visible en permanence.  
  
 Filigranes doivent être utilisés lorsqu'un contrôle ou une fenêtre est vide. Ils indiquent ce qui doit être fait pour remplir la zone et peuvent inclure des liens d'action pour ouvrir les fenêtres appropriées, comme une source de glissement.  
  
##### Style visuel  
  
-   Filigranes doivent être centrées horizontalement dans la fenêtre.  
  
-   Filigranes doivent être aligné au centre, non aligné à gauche.  
  
-   Filigranes peuvent centrés verticalement ou positionnés en haut de la zone. Si, en haut de la zone, il faut suffisamment d'espace ci\-dessus afin que le filigrane.  
  
-   Utilisez le `Environment.GrayText` police d'environnement standard et de jeton de couleur. Les liens hypertexte doivent utiliser les jetons de lien hypertexte standard partagé : `Environment.PanelHyperlink`, `Environment.PanelHyperlinkHover`, `Environment.PanelHyperlinkPressed`, et `Environment.PanelHyperlinkDisabled`.  
  
-   Filigranes ne peut pas être sélectionnés à l'arrière\-plan  
  
-   Si possible, inclure des liens dans le filigrane pour aider l'utilisateur.  
  
 ![Watermark text in a designer window](../../extensibility/ux-guidelines/media/070702-05_watermark1.png "070702\-05\_Watermark1")  
  
 ![Watermark text in a tool window](../../extensibility/ux-guidelines/media/070702-06_watermark2.png "070702\-06\_Watermark2")  
  
 **Exemples de texte de filigrane dans Visual Studio**  
  
##  <a name="BKMK_ButtonsAndHyperlinks"></a> Boutons et des liens hypertexte  
  
### Vue d'ensemble  
 Les contrôles boutons et liens \(liens\) doivent suivre [des conseils de Windows Desktop base sur des liens hypertexte](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742406\(v=vs.85\).aspx) pour l'utilisation, le libellé, dimensionner et l'espacement.  
  
### Choix entre les boutons et les liens  
 Traditionnellement, les boutons ont été utilisés pour les actions et des liens hypertexte qui ont été réservées pour la navigation. Boutons peuvent être utilisés dans tous les cas, mais le rôle de liens a été développé dans Visual Studio afin que les boutons et les liens sont plus interchangeables dans certaines conditions.  
  
 Quand utiliser les boutons de commande :  
  
-   Commandes principales  
  
-   Affichage windows utilisé pour recueillir l'entrée ou faire des choix, même si elles sont des commandes secondaires  
  
-   Actions destructrices ou irréversibles  
  
-   Boutons d'engagement dans les Assistants et les flux de page  
  
 Éviter les boutons de commande dans les fenêtres Outil, ou si vous avez besoin de plus de deux mots pour l'étiquette. Les étiquettes plus longues peuvent disposer.  
  
 Quand utiliser des liens :  
  
-   Navigation vers une autre fenêtre, document ou page web  
  
-   Situations nécessitant une étiquette plus longue ou courte phrase pour décrire l'objectif de l'action  
  
-   Espaces étroite où un bouton serait surcharger l'interface utilisateur, si l'action n'est pas irréversible ou destructeurs  
  
-   Minimise les commandes secondaires dans les situations où il existe de nombreuses commandes  
  
#### Exemples  
 ![Infobar command links following a status message](../../extensibility/ux-guidelines/media/070703-01_commandlinkinfobar.png "070703\-01\_CommandLinkInfobar")  
  
 **Commandes liens utilisés dans la barre d'informations suivant un message d'état**  
  
 ![Links used in the CodeLens popup](../../extensibility/ux-guidelines/media/070703-02_linksincodelens.png "070703\-02\_LinksInCodeLens")  
  
 **Liens utilisés dans la fenêtre contextuelle CodeLens**  
  
 ![Links used as secondary commands](../../extensibility/ux-guidelines/media/070703-03_linksassecondarycommands.png "070703\-03\_LinksAsSecondaryCommands")  
  
 **Liens utilisés pour les commandes secondaires où boutons bénéficierait de trop peu d'attention**  
  
### Boutons courants  
  
#### Texte  
 Suivez les instructions de l'écriture de [Texte de l'interface utilisateur et la terminologie](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology).  
  
#### Style visuel  
  
##### Boîtes de dialogue standard  
 La plupart des boutons dans Visual Studio s'affichent dans les boîtes de dialogue standard et ne doit pas être stylé. Ils doivent refléter l'apparence des boutons standard comme indiqué par le système d'exploitation.  
  
##### À thème  
 Dans certains cas, boutons peuvent être utilisés dans l'interface utilisateur de style et doivent avoir le format correctement ces boutons. Consultez [Boîtes de dialogue](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs) Pour plus d'informations sur les contrôles à thème.  
  
### Boutons spéciaux  
  
#### Parcourir... boutons  
 **\[Parcourir...\]** boutons sont utilisés dans les grilles, boîtes de dialogue et fenêtres d'outils et autres éléments d'interface utilisateur non modales. Ils affichent un sélecteur qui aide l'utilisateur à remplir une valeur dans un contrôle. Il existe deux variantes de ce bouton, long et court.  
  
 ![Long &#91;Browse...&#93; button](../../extensibility/ux-guidelines/media/070703-04_browselong.gif "070703\-04\_BrowseLong")  
  
 **Long \[Parcourir...\] bouton**  
  
 ![Short ellipsis&#45;only &#91;Browse...&#93; button](../../extensibility/ux-guidelines/media/070703-05_browseshort.gif "070703\-05\_BrowseShort")  
  
 **Le bouton courte uniquement des points de suspension \[...\]**  
  
 Quand utiliser le bouton court sélection uniquement :  
  
-   S'il existe plusieurs long **\[Parcourir...\]** bouton dans une boîte de dialogue, telles que lorsque plusieurs champs permettant la navigation. Utilisez court **\[...\]** bouton pour chaque afin d'éviter les clés d'accès à confusion créées par cette situation \(**& Parcourir** et **B & Rechercher** dans la même boîte de dialogue\).  
  
-   Dans une boîte de dialogue étroite, ou lorsqu'il n'existe aucun emplacement pour le bouton de temps raisonnable.  
  
-   Si le bouton s'affiche dans un contrôle de grille.  
  
 Instructions d'utilisation du bouton :  
  
-   N'utilisez pas une clé d'accès. Pour accéder à l'aide du clavier, l'utilisateur doit tabuler de contrôle adjacent. Assurez\-vous que l'ordre de tabulation est telle que n'importe quel bouton Parcourir immédiatement après le champ qui seront affichés. N'utilisez jamais un trait de soulignement sous la première période.  
  
-   Définir le Microsoft Active Accessibility \(MSAA\) **nom** propriété **Parcourir...** \(y compris les points de suspension\) afin que l'écran lecteurs lue en tant que « Parcourir » et non « point\-point\-point » ou « période période période. » Pour les contrôles managés, cela signifie que la **AccessibleName** propriété.  
  
-   N'utilisez jamais de points de suspension **\[...\]** bouton n'est pas une action de navigation. Par exemple, si vous avez besoin d'un **\[nouveau\]** bouton mais n'avez pas assez de place pour le texte, puis la boîte de dialogue doit être redéfinie.  
  
##### Dimensionnement et l'espacement  
 ![Sizing &#91;Browse...&#93; buttons](../../extensibility/ux-guidelines/media/070703-06_browsesizing.png "070703\-06\_BrowseSizing")  
  
 **Dimensionnement \[Parcourir...\] boutons**  
  
 ![Spacing &#91;Browse...&#93; buttons](../../extensibility/ux-guidelines/media/070703-07_browsespacing.png "070703\-07\_BrowseSpacing")  
  
 **Espacement \[Parcourir...\] boutons**  
  
#### Boutons graphiques  
 Certains boutons doivent toujours utiliser une image graphique et n'incluez jamais de texte pour économiser de l'espace et éviter les problèmes de localisation. Ils sont souvent utilisés dans les sélecteurs de champ et d'autres listes pouvant être triées.  
  
> [!NOTE]
>  Les utilisateurs doivent donc de les placer dans un ordre cohérent, onglet ces boutons \(il existe des clés d'accès\). Mapper la propriété name du bouton à l'action que nécessaire afin que les lecteurs d'écran interprètent correctement l'action du bouton.  
  
|||  
|-|-|  
|Ajouter|![Graphical "Add" button](../../extensibility/ux-guidelines/media/070703-08_buttonadd.png "070703\-08\_ButtonAdd")|  
|Supprimer|![Graphical "Remove" button](../../extensibility/ux-guidelines/media/070703-09_buttonremove.png "070703\-09\_ButtonRemove")|  
|Ajouter tout|![Graphical "Add All" button](../../extensibility/ux-guidelines/media/070703-10_buttonaddall.png "070703\-10\_ButtonAddAll")|  
|Supprimer tous les|![Graphical "Remove All" button](../../extensibility/ux-guidelines/media/070703-11_buttonremoveall.png "070703\-11\_ButtonRemoveAll")|  
|Monter|![Graphical "Move Up" button](../../extensibility/ux-guidelines/media/070703-12_buttonmoveup.png "070703\-12\_ButtonMoveUp")|  
|Descendre|![Graphical "Move Down" button](../../extensibility/ux-guidelines/media/070703-13_buttonmovedown.png "070703\-13\_ButtonMoveDown")|  
|Supprimer|![Graphical "Delete" button](../../extensibility/ux-guidelines/media/070703-14_buttondelete.png "070703\-14\_ButtonDelete")|  
  
##### Dimensionnement et l'espacement  
 Dimensionnement des boutons graphiques est identique à la version courte de la **\[Parcourir...\]** bouton \(26 x 23 pixels\) :  
  
 ![Button with and without transparent color showing](../../extensibility/ux-guidelines/media/070703-15_graphicalbuttonspacing.png "070703\-15\_GraphicalButtonSpacing")  
  
 **Apparence d'une image graphique sur un bouton, avec et sans affichage de couleur transparente**  
  
### Liens hypertexte  
 Les liens hypertexte sont bien adaptés à des actions de navigation, comme l'ouverture d'une rubrique d'aide, une boîte de dialogue modale ou un Assistant. Si un lien hypertexte est utilisé pour une commande, il doit toujours afficher une modification notable et visible à l'interface utilisateur. En règle générale, les actions qu'à une action \(par exemple enregistrer, Annuler et supprimer\) la validation sont communiquées mieux à l'aide d'un bouton.  
  
#### Style d'écriture  
 Suivez les [des conseils de bureau Windows pour le texte de l'interface utilisateur](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742478\(v=vs.85\).aspx). N'utilisez pas « En savoir plus à propos, » « Dire me plus sur » ou « Get help avec ce » formulation. Au lieu de cela, une phrase texte du lien aide en termes de la question principale rédigée par le contenu d'aide. Par exemple, «**comment ajouter un serveur à l'Explorateur de serveurs?**»  
  
#### Style visuel  
  
-   Utilisent toujours des liens hypertexte [Le Service VSColor](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService). Si un lien hypertexte est un style pas correctement, il clignote en rouge lorsqu'elles sont actives ou affiche une couleur différente après avoir visité.  
  
-   N'incluez pas de soulignement au contrôle positionné état sauf si le lien est un fragment de phrase au sein d'une phrase complète, comme dans un filigrane.  
  
-   Soulignement ne doit pas apparaître pointage. En revanche, les commentaires à l'utilisateur que le lien est actif sont un changement de couleur léger et le curseur de lien approprié.  
  
##  <a name="BKMK_TreeViews"></a> Vues de l'arborescence  
  
### Vue d'ensemble  
 Vues de l'arborescence fournissent des listes pour organiser complexes dans des groupes parent\-enfant. Un utilisateur peut développer ou réduire des groupes parents pour afficher ou masquer des éléments enfants sous\-jacents. Chaque élément dans une arborescence peut être sélectionné pour fournir des actions.  
  
 Cette rubrique traite des fonctionnalités de vues de l'arborescence, conception et utilisation acceptable.  
  
#### Dans cette rubrique  
  
-   [Style visuel](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViewVisualStyle)  
  
-   [Interactions](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TreeViewInteractions)  
  
###  <a name="BKMK_TreeViewVisualStyle"></a> Style visuel  
  
#### Développeurs  
 Contrôles d'arborescence doivent être conforme à la conception expander utilisée par Windows et Visual Studio. Chaque nœud utilise un contrôle expander pour afficher ou masquer les éléments sous\-jacents. À l'aide d'un contrôle expander fournit une cohérence pour les utilisateurs peuvent rencontrer des arborescences différentes dans Windows et Visual Studio.  
  
 ![Correct tree view control](../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705\-1\_TreeViewCorrect")  
  
 **Correct : style approprié du nœud d'arborescence à l'aide d'un contrôle expander**  
  
 ![Incorrect tree view nodes](../../extensibility/ux-guidelines/media/070705-2_treeviewincorrect1.png "070705\-2\_TreeViewIncorrect1")  
  
 **Incorrecte : le style incorrect du nœud d'arborescence**  
  
#### Sélection  
 Lorsqu'un nœud est sélectionné dans l'arborescence, la mise en surbrillance doit se développer pour toute la largeur du contrôle TreeView. Cela permet aux utilisateurs à identifier clairement l'élément sélectionné. Couleurs de la sélection doivent refléter le thème actuel de Visual Studio.  
  
 ![Correct tree view control](../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705\-1\_TreeViewCorrect")  
  
 **Correct : mise en surbrillance du nœud sélectionné correspond à toute la largeur du contrôle TreeView.**  
  
 ![Incorrect tree view highlighting](../../extensibility/ux-guidelines/media/070705-3_treeviewincorrect2.png "070705\-3\_TreeViewIncorrect2")  
  
 **Incorrecte : mise en surbrillance du nœud sélectionné ne tient pas toute la largeur du contrôle TreeView.**  
  
#### Icônes  
 Icônes doivent uniquement servir dans les contrôles d'arborescence si elles permettent d'identifier visuellement les différences entre les éléments. En général, les icônes doivent être utilisées uniquement dans les listes hétérogènes dans lequel les icônes communiquent les informations afin de différencier les types d'éléments. Dans une liste homogène à l'aide des icônes peut souvent être considérée comme bruit et doit être évitée. Dans ce cas, l'icône de groupe \(parent\) peut transmettre le type d'éléments qu'il contient. L'exception à cette règle est si l'icône est dynamique et est utilisée pour indiquer l'état.  
  
#### Barres de défilement  
 Barres de défilement doivent toujours être masquées si le contenu tient dans le contrôle arborescence. Il est acceptable pour les barres de défilement pour être masquées ou semi\-transparent dans une fenêtre déroulante et s'affiche lorsque la fenêtre de l'arborescence a le focus ou lors de pointage de l'arborescence afficher lui\-même.  
  
 ![Tree view with scroll bars](../../extensibility/ux-guidelines/media/070705-4_scrollbars.png "070705\-4\_Scrollbars")  
  
 **Les barres de défilement verticale et horizontale sont affichent parce que le contenu a dépassé les limites du contrôle arborescence.**  
  
###  <a name="BKMK_TreeViewInteractions"></a> Interactions  
  
#### Menus contextuels  
 Un nœud d'arborescence peut révéler des options du sous\-menu dans un menu contextuel. En général, cela se produit lorsqu'un utilisateur a cliqué un élément ou appuyé sur la touche de Menu un clavier Windows avec l'élément sélectionné. Il est important que le nœud Obtient le focus et est sélectionné. Cela aide l'utilisateur à identifier l'élément auquel appartient le sous\-menu.  
  
 ![Selected tree node and context menu](../../extensibility/ux-guidelines/media/070705-5_contextmenu.png "070705\-5\_ContextMenu")  
  
 **L'élément qui a le focus de gains de menu contextuel pour informer l'utilisateur génèrent des élément qui a été sélectionné.**  
  
#### Clavier  
 L'arborescence doit fournir la possibilité de sélectionner les éléments et développer\/réduire les nœuds à l'aide du clavier. Cela garantit que la navigation répond à nos exigences en termes d'accessibilité.  
  
##### Contrôle d'arborescence  
 Contrôles d'arborescence de Visual Studio doivent suivre les raccourcis clavier courants :  
  
-   **Haut :** sélectionner les éléments en remontant l'arborescence  
  
-   **Bas :** sélectionner les éléments à déplacer vers le bas de l'arborescence  
  
-   **Droite :** développer un nœud dans l'arborescence  
  
-   **Gauche :** réduire un nœud dans l'arborescence  
  
-   **Touche ENTRÉE :** lancer, charger, exécuter l'élément sélectionné  
  
##### Grid \(vue de l'arborescence et affichage de grille\)  
 Un contrôle Grid est un contrôle complexe qui contient une arborescence dans une grille. Développement et réduction sur la navigation dans l'arborescence doivent respecter les mêmes raccourcis clavier comme une arborescence, avec les ajouts suivants :  
  
-   **Droite :** développer un nœud. Une fois que le nœud est développé, il doit continuer à naviguer à la colonne la plus proche sur la droite. Navigation doit s'arrêter à la fin de la ligne.  
  
-   **Onglet :** permet d'accéder à la cellule la plus proche sur la droite.  À la fin de la ligne, la navigation se poursuit à la ligne suivante.  
  
-   **Maj \+ Tab :** permet d'accéder à la cellule la plus proche sur la gauche.  Au début de la ligne, la navigation se poursuit à la cellule la plus à droite de la ligne précédente.  
  
 ![Trid control in Visual Studio](../../extensibility/ux-guidelines/media/070705-6_trid.png "070705\-6\_Trid")  
  
 **Un contrôle Grid dans Visual Studio**