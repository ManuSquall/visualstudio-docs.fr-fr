---
title: "Les modèles de contrôle courants pour Visual Studio | Documents Microsoft"
ms.custom: 
ms.date: 04/26/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3e893949-6398-42f1-9eab-a8d8c2b7f02d
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: ded7ed6dd843a7879100704276766bfcb528b6f7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="common-control-patterns-for-visual-studio"></a>Modèles de contrôle courants pour Visual Studio
##  <a name="BKMK_CommonControls"></a>Contrôles communs  
  
### <a name="overview"></a>Vue d'ensemble  
Contrôles communs constituent la majeure partie de l’interface utilisateur dans Visual Studio. Contrôles les plus courants utilisés dans l’interface de Visual Studio doivent suivre le [directives d’interaction de bureau Windows](https://msdn.microsoft.com/library/windows/desktop/dn742399.aspx). Cette rubrique est spécifique à Visual Studio et traite des situations particulières ou des détails qui augmentent les instructions de Windows.  
  
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
La première chose à prendre en compte lorsque les styles de contrôles est que les contrôles seront utilisées dans l’interface utilisateur à thème. Contrôles d’interface utilisateur standard sont l’interface utilisateur sans thème et doivent respecter [style normal de bureau Windows](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742399\(v=vs.85\).aspx), ce qui signifie qu’ils ne sont pas re-basé sur un modèle et qu’il doivent apparaître dans leur apparence de contrôle par défaut.  
  
-   **Les boîtes de dialogue standard (utilitaire) :** pas à thème. Ne pas remodéliser. Utiliser les valeurs par défaut du style de contrôle de base.  
  
-   **Outil windows, les éditeurs de document, les aires de conception et les boîtes de dialogue à thème :** utiliser spécialisée apparence à thème à l’aide du service de couleur.  
  
###  <a name="BKMK_Scrollbars"></a>Barres de défilement  
 Barres de défilement doivent suivre [barres de défilement des modèles courants d’interaction pour Windows](https://msdn.microsoft.com/en-us/library/windows/desktop/bb787527\(v=vs.85\).aspx) , sauf si elles sont augmentés avec les informations de contenu, comme dans l’éditeur de code.  
  
###  <a name="BKMK_InputFields"></a>Champs d’entrée  
 Pour le comportement de l’interaction typique, suivez les [des recommandations de bureau Windows pour les zones de texte](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742442\(v=vs.85\).aspx).  
  
#### <a name="visual-style"></a>Style visuel  
  
-   Champs d’entrée ne doit pas être un style dans les boîtes de dialogue utilitaire. Utiliser le style de base intrinsèque au contrôle.  
  
-   Les champs d’entrée à thème doivent uniquement être utilisés dans les fenêtres Outil et les boîtes de dialogue à thème.  
  
#### <a name="specialized-interactions"></a>Interactions spécialisées  
  
-   Les champs en lecture seule aura un arrière-plan de gris (désactivé), mais de premier plan par défaut (actif).  
  
-   Requis des champs doivent avoir  **\<requis >** en tant que filigranes dans celles-ci. Vous ne devez pas modifier la couleur d’arrière-plan, sauf dans les rares cas.  
  
-   Validation des erreurs : consultez [Notifications et progression pour Visual Studio](../../extensibility/ux-guidelines/notifications-and-progress-for-visual-studio.md)  
  
-   Champs d’entrée doivent être dimensionnées en fonction du contenu, ne pas à la largeur de la fenêtre dans lequel elles sont affichées, ni à arbitrairement correspond à la longueur d’un champ long, comme un chemin d’accès. Longueur peut être une indication à l’utilisateur de limitations concernant le nombre de caractères est autorisé dans le champ.  
  
     ![Longueur de champ d’entrée incorrect : il est peu probable que le nom doit être ce long. ] (../../extensibility/ux-guidelines/media/0707-01_incorrectinputfieldcontrol.png "0707-01_IncorrectInputFieldControl")<br />Longueur de champ d’entrée incorrect : il est peu probable que le nom doit être ce long.
  
     ![Corriger la longueur de champ d’entrée : le champ d’entrée est une largeur raisonnable pour le contenu attendu. ] (../../extensibility/ux-guidelines/media/0707-02_correctinputfieldcontrol.png "0707-02_CorrectInputFieldControl")<br />Corriger la longueur de champ d’entrée : le champ d’entrée est une largeur raisonnable pour le contenu attendu.
  
###  <a name="BKMK_ComboBoxesAndDropDowns"></a>Zones de liste déroulante et les listes déroulantes  
Pour le comportement de l’interaction typique, suivez les [des recommandations de bureau Windows pour les listes déroulantes et les zones de liste déroulante](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742404\(v=vs.85\).aspx).  
  
#### <a name="visual-style"></a>Style visuel  
  
-   Dans les boîtes de dialogue utilitaire, ne pas remodéliser le contrôle. Utiliser le style de base intrinsèque au contrôle.  
  
-   Dans l’interface utilisateur à thème, zones de liste déroulante et les zones déroulantes suivent les thèmes standard pour les contrôles.  
  
#### <a name="layout"></a>Disposition  
Zones de liste déroulante et les zones déroulantes doivent être dimensionnées en fonction du contenu, ne pas à la largeur de la fenêtre dans lequel elles sont affichées, ni à arbitrairement correspond à la longueur d’un champ long, comme un chemin d’accès.  
  
![Incorrecte : la largeur de la liste déroulante est trop longue pour le contenu qui sera affiché. ] (../../extensibility/ux-guidelines/media/0707-03_incorrectdropdownlayout.png "0707-03_IncorrectDropDownLayout")<br />Incorrecte : la largeur de la liste déroulante est trop longue pour le contenu qui sera affiché.
  
![Correct : la liste déroulante est dimensionnée pour permettre la croissance de traduction, mais pas inutilement long. ] (../../extensibility/ux-guidelines/media/0707-04_correctdropdownlayout.png "0707-04_CorrectDropDownLayout")<br />Correct : la liste déroulante est dimensionnée pour permettre la croissance de traduction, mais pas inutilement long. 
  
###  <a name="BKMK_CheckBoxes"></a>Cases à cocher  
Pour le comportement de l’interaction typique, suivez les [des recommandations de bureau Windows pour les cases à cocher](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742401\(v=vs.85\).aspx).  
  
#### <a name="visual-style"></a>Style visuel  
  
-   Dans les boîtes de dialogue utilitaire, ne pas remodéliser le contrôle. Utiliser le style de base intrinsèque au contrôle.  
  
-   Dans l’interface utilisateur à thème, cases à cocher suivent les thèmes standard pour les contrôles.  
  
#### <a name="specialized-interactions"></a>Interactions spécialisées  
  
-   Interaction avec une case à cocher ne doit jamais affiche une boîte de dialogue ou accéder à une autre zone.  
  
-   Aligner les cases à cocher avec la ligne de base de la première ligne de texte.  
  
     ![Incorrecte : la case à cocher est centré sur le texte. ] (../../extensibility/ux-guidelines/media/0707-05_incorrectcheckboxalign.png "0707-05_IncorrectCheckBoxAlign")<br />Incorrecte : la case à cocher est centré sur le texte.
  
     ![Correct : la case à cocher est aligné avec la première ligne du texte. ] (../../extensibility/ux-guidelines/media/0707-06_correctcheckboxalign.png "0707-06_CorrectCheckBoxAlign")<br />Correct : la case à cocher est aligné avec la première ligne du texte.
  
###  <a name="BKMK_RadioButtons"></a>Cases d’option  
Pour le comportement de l’interaction typique, suivez les [des recommandations de bureau Windows pour les cases d’option](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742436\(v=vs.85\).aspx).  
  
#### <a name="visual-style"></a>Style visuel  
Dans les boîtes de dialogue utilitaire, n'effectuez pas les boutons de case d’option de style. Utiliser le style de base intrinsèque au contrôle.  
  
#### <a name="specialized-interactions"></a>Interactions spécialisées  
Il n’est pas nécessaire d’utiliser un cadre de groupe à placer les choix de cases d’option, sauf si vous avez besoin maintenir la distinction de groupe dans une disposition étroite.  
  
###  <a name="BKMK_GroupFrames"></a>Images de groupe  
Pour le comportement de l’interaction typique, suivez les [des recommandations de bureau Windows pour les images de groupe](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742405\(v=vs.85\).aspx).  
  
#### <a name="visual-style"></a>Style visuel  
Dans l’utilitaire de boîtes de dialogue, ne style cadres de groupe. Utiliser le style de base intrinsèque au contrôle.  
  
#### <a name="layout"></a>Disposition  
  
-   Il n’est pas nécessaire d’utiliser un cadre de groupe à placer les choix de cases d’option, sauf si vous avez besoin maintenir la distinction de groupe dans une disposition étroite.  
  
-   N’utilisez jamais un cadre de groupe pour un seul contrôle.  
  
-   Parfois, il est acceptable d’utiliser une règle horizontale au lieu d’un conteneur de frame de groupe.  
  
##  <a name="BKMK_TextControls"></a>Contrôles de texte

### <a name="static-text-fields"></a>Champs de texte statique

Un champ de texte statique présente des informations en lecture seule et ne peut pas être sélectionné par l’utilisateur. Évitez de l’utiliser pour le texte que l’utilisateur peut souhaiter à copier dans le Presse-papiers. Toutefois, le texte statique en lecture seule peut modifier pour refléter un changement d’état. Dans l’exemple ci-dessous, le texte statique de nom de sortie sous la modification des informations de groupe afin de refléter les modifications apportées à la zone de texte racine Namespace au-dessus de lui.

Il existe deux manières d’afficher les informations de texte statique.

Texte statique peut être sur son propre dans une boîte de dialogue sans toute relation contenant-contenu lorsqu’il n’existe aucun conflit de regroupement. Décider si les lignes supplémentaires d’une zone sont réellement nécessaires. Un exemple est l’affichage d’un chemin d’accès de répertoire sous une section créée par une ligne de groupe, comme indiqué ci-dessous :  

![Les informations de texte statique dans les contrôles de texte](../../extensibility/ux-guidelines/media/DisplayingStaticText.png "DisplayingStaticText.png")<br />Informations de texte statique dans les contrôles de texte

Dans une boîte de dialogue lorsque d’autres zones groupées existent et relation contenant-contenu de l’information peut vous aider à une meilleure lisibilité, et lorsque une section peut être masquée ou affichée (comme dans le **fenêtre Propriétés** volet description) ou vous souhaitez être cohérent avec l’interface utilisateur similaires, Placez le texte statique dans une zone. Cette zone de groupe doit être une seule règle et de couleur avec la `ButtonShadow`:

![Texte statique dans la fenêtre Propriétés](../../extensibility/ux-guidelines/media/PropertiesWindow.png "PropertiesWindow.png")<br />Texte statique dans la fenêtre Propriétés

### <a name="read-only-text-box"></a>Zone de texte en lecture seule

Cela permet à l’utilisateur à sélectionner le texte dans le champ, mais pas le modifier. Ces zones de texte sont délimitées par le biseau 3D habituel avec un `ButtonShadow` remplissage.

Une zone de texte peut devenir active (modifiable) lorsqu’un utilisateur modifie un contrôle associé, tel que vérification/si vous décochez une case à cocher ou en sélectionnant/en désactivant une case d’option. Par exemple, dans le **outils &gt; Options** page illustré ci-dessous, le **Page d’accueil** zone de texte devient active lorsque le **par défaut** case à cocher est désactivée.

![Zone de texte en lecture seule, affichant les états inactif et actif](../../extensibility/ux-guidelines/media/ReadOnlyTextBox.png "ReadOnlyTextBox.png")<br />Zone de texte en lecture seule, affichant les états inactif et actif

### <a name="using-text-in-dialogs"></a>Utilisation de texte dans les boîtes de dialogue

Recommandations principales du texte dans les boîtes de dialogue :

-   Étiquettes pour les zones de texte, des zones de liste et des images dans les boîtes de dialogue unthemed démarrer avec un verbe, ont un capital initial sur le premier mot uniquement et se terminent par un signe deux-points.

    > Contrôles de texte dans les boîtes de dialogue à thème suivent [des recommandations UX bureau Windows](https://msdn.microsoft.com/library/windows/desktop/dn742479.aspx) ne prennent pas de ponctuation, à l’exception des points d’interrogation dans les liens d’aide.

-   Étiquettes pour les cases à cocher et des cases d’option Démarrer avec un verbe, la première lettre en majuscule sur le premier mot uniquement et aucun signe de ponctuation final.

-   Étiquettes de boutons, des menus, des éléments de menu et des onglets ont majuscules sur chaque mot (majuscule).

-   Terminologie de l’étiquette doit être cohérente avec les étiquettes similaire dans les autres boîtes de dialogue.

-   Si possible, avoir un auteur écrire ou d’approuver le texte avant d’entrer au développeur de l’implémentation.

-   Tous les contrôles doivent comporter des étiquettes, sauf dans des circonstances particulières dans les tabulation est suffisante.
Utilisez le texte d’aide lorsque cela est approprié.

### <a name="helper-text"></a>Texte d’aide

Inclus dans les boîtes de dialogue pour aider l’utilisateur à comprendre l’objectif de la boîte de dialogue ou pour indiquer l’action à effectuer. Texte d’aide doit être utilisé uniquement si nécessaire pour éviter de surcharger les boîtes de dialogue simples. Deux variantes de texte d’aide sont la boîte de dialogue et le filigrane.

Suivez les emplacements courants pour le texte d’aide et soyez sélectif avec l’introduction de nouveaux domaines. Scénarios courants pour le texte d’aide sont :

-   Texte d’aide dans les boîtes de dialogue, pour donner des instructions supplémentaires sur la façon d’interagir avec une boîte de dialogue complexe.

-   Texte de filigrane dans les fenêtres Outil vide ou des boîtes de dialogue, pour expliquer la raison pour laquelle aucun contenu n’est visible.

-   Un volet de description, comme en bas de la **fenêtre Propriétés**.

-   Texte dans un éditeur vide, pour expliquer l’action que l’utilisateur doit entreprendre pour la prise en main de filigrane.
  
### <a name="dialog-helper-text"></a>Texte d’assistance de boîte de dialogue

Un concepteur d’expérience utilisateur peut aider à déterminer quand le texte d’aide est appropriée. Le concepteur peut définir où le texte d’aide s’affiche, ainsi que son contenu général. Assistance utilisateur peut écriture/modification du texte.

### <a name="watermarks"></a>Filigranes

Boîtes de dialogue de tirent parti de recommandations de filigrane légèrement différent. Car une boîte de dialogue peut apparaître occupé avec nombreux éléments d’interface utilisateur (étiquettes, texte d’indication, boutons et autres contrôles conteneurs avec du texte), en particulier quand les s’affichent en noir, filigranes évidence en gris foncé (VSColor : `ButtonShadow`). En règle générale, un filigrane s’affiche à l’intérieur d’un contrôle comme une zone de liste avec un arrière-plan blanc (VSColor : `Window`).

-   Le texte apparaît en gris foncé (VSColor : `ButtonShadow`). Toutefois, si le filigrane s’affiche sur un gris ou une autre couleur (VSColor : `ButtonFace`) en arrière-plan et qu’il existe concernent sur sa lisibilité, accédez avec texte en noir (VSColor : `WindowText`).

-   Les filigranes peuvent être centrés ou aligné à gauche. Appliquer des règles de conception standard lors de la prise de décisions alignement. Impossible de sélectionner le filigrane sur l’arrière-plan.

![Exemple de texte de filigrane](../../extensibility/ux-guidelines/media/WatermarkTextExample.gif)<br />Exemple de texte de filigrane

### <a name="context-specific-dynamic-text"></a>Texte (dynamique) de spécifique au contexte

Texte dynamique peut être utilisé de deux façons dans une boîte de dialogue ou une interface utilisateur non modale : comme étiquette de dynamique ou en tant que contenu dynamique.

-   Étiquette dynamique : une utilisation courante du texte dynamique est dans les panneaux descriptifs qui contiennent des informations supplémentaires pour l’élément sélectionné, comme dans une boîte de dialogue contient une liste d’éléments et les propriétés de ces éléments s’affichés dans une grille située à droite. L’étiquette de la grille des propriétés peut être dynamique pour que lorsqu’un élément est sélectionné sur la gauche, la grille située à droite affiche des informations pour cet élément spécifique.

-   Texte dynamique : peut être utile dans les cas où vous avez besoin afficher des informations spécifiques et non les informations de cette façon, mais doit veiller à n'abusez pas.

Si vous souhaitez que les utilisateurs ont la possibilité de copier les informations, texte dynamique doit être dans un champ de texte en lecture seule.
  
##  <a name="BKMK_ButtonsAndHyperlinks"></a>Boutons et des liens hypertexte  
  
### <a name="overview"></a>Vue d'ensemble  
Contrôles de boutons et de liens (liens) doivent suivre [conseils de bureau Windows de base sur les liens hypertexte](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742406\(v=vs.85\).aspx) pour l’utilisation, formulation de dimensionnement et de l’espacement.  
  
### <a name="choosing-between-buttons-and-links"></a>Choix entre les boutons et les liens  
En règle générale, les boutons ont été utilisées pour les actions et des liens hypertexte qui ont été réservées pour la navigation. Boutons peuvent être utilisés dans tous les cas, mais le rôle de liens a été développé dans Visual Studio afin que les boutons et les liens ne sont plus interchangeables dans certaines conditions.  
  
Quand utiliser les boutons de commande :  
  
-   Commandes principales  
  
-   Affichage de windows utilisée pour recueillir l’entrée ou déterminants, même si elles sont des commandes secondaires  
  
-   Actions de destructeurs ou irréversibles  
  
-   Boutons d’engagement dans les Assistants et les flux de page  
  
Éviter les boutons de commande dans les fenêtres Outil, ou si vous avez besoin de plus de deux mots de l’étiquette. Des liens peuvent avoir des étiquettes de plus de temps.  
  
 Quand utiliser des liens :  
  
-   Navigation vers une autre fenêtre, un document ou page web  
  
-   Situations qui nécessitent une étiquette plus longue ou une phrase pour décrire l’objectif de l’action  
  
-   Espaces étroits où un bouton serait surcharger l’interface utilisateur, à condition que l’action n’est pas destructeur ou irréversible  
  
-   Minimise les commandes secondaires dans les situations où il existe de nombreuses commandes  
  
#### <a name="examples"></a>Exemples  
![Liens utilisés dans la barre d’informations suivant un message d’état de la commande](../../extensibility/ux-guidelines/media/070703-01_commandlinkinfobar.png "070703-01_CommandLinkInfobar")<br />Commandes liens utilisés dans la barre d’informations suivant un message d’état
  
![Liens utilisés dans la fenêtre contextuelle CodeLens](../../extensibility/ux-guidelines/media/070703-02_linksincodelens.png "070703-02_LinksInCodeLens")<br />Liens utilisés dans la fenêtre contextuelle CodeLens
  
![Liens utilisés pour les commandes secondaire où boutons bénéficierait de trop d’attention](../../extensibility/ux-guidelines/media/070703-03_linksassecondarycommands.png "070703-03_LinksAsSecondaryCommands")<br />Liens utilisés pour les commandes secondaire où boutons bénéficierait de trop d’attention
  
### <a name="common-buttons"></a>Boutons courants  
  
#### <a name="text"></a>Texte  
Suivez les instructions de l’écriture de [UI texte et la terminologie](../../extensibility/ux-guidelines/ui-text-and-help-for-visual-studio.md#BKMK_UITextAndTerminology).  
  
#### <a name="visual-style"></a>Style visuel  
  
##### <a name="standard-unthemed"></a>Standard (unthemed)  
La plupart des boutons dans Visual Studio apparaît dans les boîtes de dialogue utilitaire et ne doit pas être appelé. Ils doivent refléter l’apparence standard des boutons comme stipulé par le système d’exploitation.  
  
##### <a name="themed"></a>À thème  
Dans certains cas, boutons peuvent être utilisées dans l’interface utilisateur de style et doivent être un style correctement ces boutons. Consultez [boîtes de dialogue](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs) pour plus d’informations sur les contrôles à thème.  
  
### <a name="special-buttons"></a>Boutons spéciaux  
  
#### <a name="browse-buttons"></a>Boutons de navigation...  
**[Parcourir...]**  boutons sont utilisés dans les grilles, boîtes de dialogue et fenêtres Outil et autres éléments d’interface utilisateur non modales. Ils affichent un sélecteur qui aide l’utilisateur à remplir une valeur dans un contrôle. Il existe deux variantes de ce bouton, long et court.  
  
![Le bouton long [Parcourir...]](../../extensibility/ux-guidelines/media/070703-04_browselong.gif "070703-04_BrowseLong")<br />Le bouton long [Parcourir...]
  
![Le bouton court portant uniquement sur les points de suspension [...]](../../extensibility/ux-guidelines/media/070703-05_browseshort.gif "070703-05_BrowseShort")<br />Le bouton court portant uniquement sur les points de suspension [...]
  
Quand utiliser le bouton court de points de suspension uniquement :  
  
-   S’il existe plusieurs long **[Parcourir...]**  bouton dans une boîte de dialogue, comme lorsque plusieurs champs Autoriser pour l’exploration. Utilisez court **[...]**  bouton pour chacune d’elles éviter les confusion clés d’accès créés par cette situation (**& Parcourir** et **B & taper** dans la même boîte de dialogue).  
  
-   Dans une boîte de dialogue étroite, ou lorsqu’il n’existe aucun emplacement raisonnable pour le bouton long.  
  
-   Si le bouton apparaît dans un contrôle de grille.  
  
Recommandations pour l’aide du bouton :  
  
-   N’utilisez pas une clé d’accès. Pour accéder à l’aide du clavier, l’utilisateur doit de tabulation du contrôle adjacents. Assurez-vous que l’ordre de tabulation est telle que n’importe quel bouton Parcourir immédiatement après le champ qui seront affichés. N’utilisez jamais un trait de soulignement sous la première période.  
  
-   Définir le Microsoft Active Accessibility (MSAA) **nom** propriété **Parcourir...**  (y compris les points de suspension) pour qui écran lecteurs lue en tant que « Parcourir » et pas « point-point-point » ou « période période-période. » Pour les contrôles managés, cela signifie que la **AccessibleName** propriété.  
  
-   N’utilisez jamais de points de suspension **[...]**  bouton pour l’action Parcourir. Par exemple, si vous avez besoin d’un **[nouveau]**  bouton mais n’avez pas assez de place pour le texte, puis la boîte de dialogue doit être redéfinie.  
  
##### <a name="sizing-and-spacing"></a>Dimensionnement et l’espacement  
![Boutons de dimensionnement [Parcourir...] : version de la norme est 75 x 23 pixels et la version courte est 26 x 23 pixels](../../extensibility/ux-guidelines/media/070703-06_browsesizing.png "070703-06_BrowseSizing")<br />Bouton de dimensionnement [Parcourir...]
  
![Boutons d’espacement [Parcourir...] : espacement de contrôle et de pixels de bouton 7 Parcourir standards, l’espacement entre contrôle connexe et parcourir court bouton 5 pixels](../../extensibility/ux-guidelines/media/070703-07_browsespacing.png "070703-07_BrowseSpacing")<br />Bouton d'espacement [Parcourir...]
  
#### <a name="graphical-buttons"></a>Boutons graphiques  
Certains boutons doivent toujours utiliser une image de graphique et n’incluez jamais de texte pour économiser de l’espace et éviter les problèmes de localisation. Ceux-ci sont souvent utilisés dans les sélecteurs de champ et d’autres listes pouvant être triées.  
  
> **Remarque :** les utilisateurs devront TAB pour accéder à ces boutons (il n’y a aucune clé d’accès), par conséquent, les placer dans un ordre cohérent. Mappage du `name` propriété du bouton à l’action nécessaire afin que les lecteurs d’écran interprètent correctement l’action du bouton.  
  
| Fonction | Bouton |  
| --- | --- |  
| Ajouter | ![Graphique bouton « Ajouter »](../../extensibility/ux-guidelines/media/070703-08_buttonadd.png "070703-08_ButtonAdd") |
| Remove | ![Graphique bouton « Supprimer »](../../extensibility/ux-guidelines/media/070703-09_buttonremove.png "070703-09_ButtonRemove") |
| Ajoutez tous les | ![Bouton graphique « Ajouter tout »](../../extensibility/ux-guidelines/media/070703-10_buttonaddall.png "070703-10_ButtonAddAll") |
| Supprimer tous les | ![Bouton graphique « Supprimer tout »](../../extensibility/ux-guidelines/media/070703-11_buttonremoveall.png "070703-11_ButtonRemoveAll") |
| Monter | ![Bouton graphique « Monter »](../../extensibility/ux-guidelines/media/070703-12_buttonmoveup.png "070703-12_ButtonMoveUp") |
| Descendre | ![Bouton graphique « Descendre »](../../extensibility/ux-guidelines/media/070703-13_buttonmovedown.png "070703-13_ButtonMoveDown") |
| Supprimer | ![Graphique bouton « Supprimer »](../../extensibility/ux-guidelines/media/070703-14_buttondelete.png "070703-14_ButtonDelete") |
  
##### <a name="sizing-and-spacing"></a>Dimensionnement et l’espacement  
Dimensionnement des boutons graphiques est identique à la version courte de la **[Parcourir...]**  bouton (26 x 23 pixels) :  
  
![Apparence d’une image graphique sur un bouton, avec et sans affichage de couleur transparente](../../extensibility/ux-guidelines/media/070703-15_graphicalbuttonspacing.png "070703-15_GraphicalButtonSpacing")<br />Apparence d’une image graphique sur un bouton, avec et sans affichage de couleur transparente
  
### <a name="hyperlinks"></a>Liens hypertexte  
Les liens hypertexte sont bien adaptés aux actions de navigation telles que l’ouverture d’une rubrique d’aide, boîte de dialogue modale ou l’Assistant. Si un lien hypertexte est utilisé pour une commande, il doit toujours afficher une modification visible et détectable à l’interface utilisateur. En règle générale, les actions qui sont validées à une action (par exemple, enregistrer, Annuler et supprimer) sont communiquées mieux à l’aide d’un bouton.  
  
#### <a name="writing-style"></a>Style d’écriture  
Suivez les [des conseils de bureau Windows pour le texte de l’interface utilisateur](https://msdn.microsoft.com/en-us/library/windows/desktop/dn742478\(v=vs.85\).aspx). N’utilisez pas « En savoir plus sur, » « Indiquent me plus sur » ou « Obtenir plus d’informations » formulation. Au lieu de cela, une expression texte de lien d’aide en termes de la question principale ayant obtenu une réponse par le contenu d’aide. Par exemple, «**comment ajouter un serveur à l’Explorateur de serveurs ?**»  
  
#### <a name="visual-style"></a>Style visuel  
  
-   Utilisent toujours des liens hypertexte [le VSColor Service](../../extensibility/ux-guidelines/colors-and-styling-for-visual-studio.md#BKMK_TheVSColorService). Si un lien hypertexte n’est pas un style correctement, il clignote en rouge lorsqu’il est actif ou affiche une couleur différente après avoir visité.  
  
-   N’incluez pas soulignements au contrôle plaçant état sauf si le lien est un fragment de phrase au sein d’une phrase complète, comme dans un filigrane.  
  
-   Soulignement ne doit pas apparaître pointage. Au lieu de cela, les commentaires à l’utilisateur que le lien est actif sont une modification de couleur légère et le curseur de lien approprié.  
  
##  <a name="BKMK_TreeViews"></a>Vues de l’arborescence  
  
Vues de l’arborescence fournissent un moyen d’organiser complexe répertorie dans des groupes parent-enfant. Un utilisateur peut développer ou réduire des groupes parents pour afficher ou masquer des éléments enfants sous-jacents. Chaque élément dans une vue d’arborescence peut être sélectionné pour fournir davantage d’action.  
  
###  <a name="BKMK_TreeViewVisualStyle"></a>Style de vue visual  
  
#### <a name="expanders"></a>EXPANSEURS  
Contrôles d’arborescence doivent être conforme à la conception du contrôle expander utilisée par Windows et Visual Studio. Chaque nœud utilise un contrôle expander pour afficher ou masquer les éléments sous-jacents. À l’aide d’un contrôle expander cohérence pour les utilisateurs peuvent rencontrer des arborescences différentes au sein de Windows et Visual Studio.  
  
![Correct : style approprié du nœud d’arborescence à l’aide d’un contrôle expander](../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705-1_TreeViewCorrect")<br />Correct : style approprié du nœud d’arborescence à l’aide d’un contrôle expander
  
![Incorrecte : le style incorrect de nœud d’arborescence](../../extensibility/ux-guidelines/media/070705-2_treeviewincorrect1.png "070705-2_TreeViewIncorrect1")<br />Incorrecte : le style incorrect de nœud d’arborescence
  
#### <a name="selection"></a>Sélection  
Lorsqu’un nœud est sélectionné dans l’arborescence, la mise en surbrillance doit développer sur toute la largeur du contrôle arborescence. Cela permet aux utilisateurs à identifier clairement les éléments qu’ils ont sélectionné. Couleurs de la sélection doivent refléter le thème de Visual Studio en cours.  
  
![Correct : mise en surbrillance du nœud sélectionné correspond à toute la largeur du contrôle arborescence. ] (../../extensibility/ux-guidelines/media/070705-1_treeviewcorrect.png "070705-1_TreeViewCorrect")<br />Correct : mise en surbrillance du nœud sélectionné correspond à toute la largeur du contrôle arborescence.
  
![Incorrecte : mise en surbrillance du nœud sélectionné ne tient pas toute la largeur du contrôle arborescence. ] (../../extensibility/ux-guidelines/media/070705-3_treeviewincorrect2.png "070705-3_TreeViewIncorrect2")<br />Incorrecte : mise en surbrillance du nœud sélectionné ne tient pas toute la largeur du contrôle arborescence.
  
#### <a name="icons"></a>Icônes  
Icônes doivent uniquement être utilisées dans les contrôles d’arborescence si ils permettent d’identifier visuellement les différences entre les éléments. En règle générale, les icônes doivent être utilisées uniquement dans les listes hétérogènes dans lesquels les icônes comportent des informations afin de différencier les types d’éléments. Dans une liste homogène à l’aide des icônes peut souvent être considérée comme bruit et doit être évitée. Dans ce cas, l’icône de groupe (parent) peut transmettre le type d’éléments qu’il contient. L’exception à cette règle est si l’icône est dynamique et est utilisé pour indiquer l’état.  
  
#### <a name="scroll-bars"></a>Barres de défilement  
Barres de défilement doivent toujours être masquées si le contenu tient dans le contrôle arborescence. Il est acceptable pour les barres de défilement à masqué, transparent ou semi-transparent dans une fenêtre de défilement et s’affichent lorsque la fenêtre de l’arborescence a le focus ou lors de pointage de l’arborescence afficher lui-même.  
  
![Les barres de défilement verticale et horizontale sont affichent, car le contenu a dépassé les limites du contrôle arborescence. ] (../../extensibility/ux-guidelines/media/070705-4_scrollbars.png "070705-4_Scrollbars")<br />Les barres de défilement verticale et horizontale sont affichent, car le contenu a dépassé les limites du contrôle arborescence.
  
###  <a name="BKMK_TreeViewInteractions"></a>Interactions de vue d’arborescence  
  
#### <a name="context-menus"></a>Menus contextuels  
Un nœud d’arborescence peut révéler des options de sous-menu dans un menu contextuel. En règle générale, cela se produit lorsqu’un utilisateur a cliqué un élément ou enfoncée la touche de Menu sur un clavier Windows avec l’élément sélectionné. Il est important que le nœud Obtient le focus et est sélectionné. Cela aide l’utilisateur à identifier l’élément auquel appartient le sous-menu.  
  
![L’élément qui a le focus de gains de menu contextuel pour informer l’utilisateur génèrent des élément qui a été sélectionné. ] (../../extensibility/ux-guidelines/media/070705-5_contextmenu.png "070705-5_ContextMenu")<br />L’élément qui a le focus de gains de menu contextuel pour informer l’utilisateur génèrent des élément qui a été sélectionné.
  
#### <a name="keyboard"></a>Clavier  
L’arborescence doit fournir la possibilité de sélectionner les éléments et développer/réduire les nœuds à l’aide du clavier. Cela garantit que la navigation répond aux critères d’accessibilité.  
  
##### <a name="tree-view-control"></a>Contrôle d’arborescence  
Contrôles d’arborescence de Visual Studio doivent suivre la navigation au clavier courants :  
  
-   **Flèche vers le haut :** sélectionner les éléments en remontant l’arborescence  
  
-   **Flèche vers le bas :** sélectionner des éléments à l’arborescence  
  
-   **Flèche droite :** développez un nœud dans l’arborescence  
  
-   **Flèche gauche :** réduire un nœud dans l’arborescence  
  
-   **Entrez la clé :** lancer, charger, exécuter l’élément sélectionné  
  
##### <a name="trid-tree-view-and-grid-view"></a>Grid (vue de l’arborescence et affichage de grille)  
Un contrôle Grid est un contrôle complexe qui contient une arborescence dans une grille. Développement et réduction de parcourir l’arborescence doivent respecter les mêmes commandes clavier comme une arborescence, avec les ajouts suivants :  
  
-   **Flèche droite :** développer un nœud. Une fois que le nœud est développé, il doit continuer accédant à la colonne le plus proche sur la droite. Navigation doit s’arrêter à la fin de la ligne.  
  
-   **Onglet :** permet d’accéder à la cellule la plus proche sur la droite.  À la fin de la ligne, la navigation se poursuit à la ligne suivante.  
  
-   **Maj + Tab :** permet d’accéder à la cellule la plus proche sur la gauche.  Au début de la ligne, la navigation se poursuit à la cellule la plus à droite de la ligne précédente.  
  
![Un contrôle Grid dans Visual Studio](../../extensibility/ux-guidelines/media/070705-6_trid.png "070705-6_Trid")<br />Un contrôle Grid dans Visual Studio