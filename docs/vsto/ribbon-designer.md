---
title: "Concepteur de ruban"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Designer_Microsoft.VisualStudio.Tools.Office.Ribbon.Design.RibbonDesigner"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "contrôles (développement Office dans Visual Studio), ruban"
  - "ruban personnalisé"
  - "ruban personnalisé, à propos du Concepteur de ruban"
  - "personnaliser le ruban"
  - "personnaliser le ruban, à propos du Concepteur de ruban"
  - "concepteurs (développement Office dans Visual Studio), ruban"
  - "lecture seule (propriétés en)"
  - "ruban (développement Office dans Visual Studio), tâches courantes"
  - "ruban (développement Office dans Visual Studio), contrôles"
  - "ruban (développement Office dans Visual Studio), personnaliser"
  - "ruban (développement Office dans Visual Studio), touches de raccourci"
  - "ruban (développement Office dans Visual Studio), concepteur visuel"
  - "Concepteur de ruban (développement Office dans Visual Studio)"
ms.assetid: 26617206-f4da-416f-a18a-d817b2d4872d
caps.latest.revision: 79
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 78
---
# Concepteur de ruban
  Le Concepteur de ruban est une zone de conception visuelle.  Il permet d'ajouter des onglets, groupes et contrôles personnalisés au ruban d'une application Microsoft Office.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
 Pour ouvrir le Concepteur de ruban, ajoutez un élément **Ruban \(Concepteur visuel\)** à votre projet.  Vous pouvez ensuite utiliser les outils de conception pour les tâches suivantes :  
  
-   [Concevoir la disposition du Ruban](#DesigningRibbonLayout)  
  
-   [Gérer des événements et définir des propriétés de contrôle](#HandleEventsSetProperties)  
  
-   [Ajoutez les contrôles au mode Backstage](#CustomizingMicrosoftOfficeButton)  
  
> [!NOTE]  
>  Certaines tâches ne sont pas réalisables avec le Concepteur de ruban.  Pour plus d'informations sur ces tâches et la façon de les réaliser, consultez [Vue d'ensemble du ruban](../vsto/ribbon-overview.md).  
  
 ![lien vers la vidéo](../vsto/media/playvideo.png "lien vers la vidéo") Pour une démonstration vidéo connexe, consultez la page expliquant [Comment utiliser le Concepteur de ruban pour personnaliser le ruban dans Outlook ?](http://go.microsoft.com/fwlink/?LinkID=130312).  
  
## Ajout d'un élément de ruban \(Concepteur visuel\) à un Projet  
 Pour utiliser le Concepteur de ruban, ajoutez un élément **Ruban \(Concepteur visuel\)** à votre projet.  Pour plus d'informations, consultez [Comment : démarrer avec la personnalisation du ruban](../vsto/how-to-get-started-customizing-the-ribbon.md).  
  
 Lorsque vous ajoutez un nouvel élément **Ruban \(Concepteur visuel\)**, Visual Studio ajoute automatiquement les fichiers suivants à votre projet :  
  
-   Un fichier de code du ruban.  Ce fichier porte le nom que vous spécifiez pour l'élément **Ruban \(Concepteur visuel\)** dans la boîte de dialogue **Ajouter un nouvel élément**.  Ajoutez le code à ce fichier pour gérer des événements Ruban.  
  
-   Fichier de code du Concepteur de ruban.  Ce fichier contient le code généré par le Concepteur de ruban et ne doit pas être modifié directement.  
  
-   Fichier de ressources.  Ce fichier contient les valeurs de propriété de chaque contrôle sur le Ruban.  
  
 Si vous possédez déjà un élément **Ruban \(Concepteur visuel\)** d'un autre projet, vous pouvez le réutiliser dans votre projet actuel à l'aide de la boîte de dialogue **Ajouter un élément existant**.  
  
##  <a name="DesigningRibbonLayout"></a> Conception d'un ruban  
 Il existe trois façons d'ouvrir le Concepteur de ruban :  
  
-   Dans l'**Explorateur de solutions**, double\-cliquez sur le fichier de code du ruban.  
  
-   Dans l'**Explorateur de solutions**, cliquez avec le bouton droit sur le fichier de code du ruban, puis cliquez sur **Concepteur de vues**.  
  
-   Dans l'**Explorateur de solutions**, sélectionnez le fichier du code de ruban, puis cliquez sur **Concepteur** dans le menu **Affichage**.  
  
 Le Concepteur de ruban contient un onglet et un groupe par défaut.  Vous pouvez supprimer l'onglet et le groupe par défaut du Concepteur de ruban.  Pour supprimer le groupe par défaut, cliquez avec le bouton droit sur **Group1**, puis cliquez sur **Supprimer**.  Pour supprimer l'onglet par défaut, cliquez avec le bouton droit sur une zone vide de l'aire de conception, puis cliquez sur **Onglet Supprimer un ruban**.  
  
 Vous pouvez également ajouter de nouveaux onglets, groupes et contrôles personnalisés au Concepteur de ruban.  Vous pouvez rechercher ces contrôles dans la **Boîte à outils**, dans le groupe **Contrôles de ruban Office**.  Il existe trois façons d'ajouter des contrôles au Concepteur de ruban à partir du groupe **Contrôles de ruban Office** :  
  
-   Faites glisser un contrôle vers une zone appropriée du Concepteur de ruban.  
  
-   Cliquez sur un contrôle, puis sur une zone appropriée du Concepteur de ruban.  
  
-   Sélectionnez une zone appropriée du le concepteur, puis double\-cliquez sur un contrôle de la **Boîte à outils**.  
  
### Flux de travail de conception du ruban  
 Pour concevoir la disposition de Ruban, exécutez les étapes de base suivantes :  
  
1.  [Ajouter un onglet personnalisé au ruban](#AddTabToRibbon).  
  
2.  [Ajoutez des groupes à l'onglet](#AddGroupsToTab).  
  
3.  [Ajoutez des contrôles aux groupes](#AddControlsToGroups).  
  
 Les contrôles peuvent uniquement être déplacés sur des groupes ; vous ne pouvez pas faire glisser de contrôle directement vers un onglet ou vers le ruban.  Les groupes peuvent uniquement être déplacés sur des onglets ; vous ne pouvez pas faire glisser de groupe directement vers un ruban.  
  
 Réorganisez des contrôles en les faisant glisser aux emplacements corrects.  Vous pouvez également définir les propriétés d'un contrôle à l'aide de la fenêtre **Propriétés**.  
  
 Vous ne pouvez pas faire glisser de contrôles d'un onglet vers un autre sur le ruban.  Si vous souhaitez déplacer un contrôle vers un autre onglet, vous devez utiliser la commande **Couper** pour supprimer le contrôle d'un onglet, puis le collez sur un autre onglet.  Si vous coupez le contrôle et le collez, le gestionnaire d'événements s'interrompt.  Vous pouvez reconnecter le gestionnaire d'événements dans la fenêtre **Propriétés**.  Pour plus d'informations, consultez [Propriétés &#40;fenêtre&#41;](../ide/reference/properties-window.md).  
  
###  <a name="AddTabToRibbon"></a> Ajout d'onglets personnalisés au ruban  
 Il existe trois façons d'ajouter un onglet personnalisé au ruban :  
  
-   Ajoutez un onglet à partir de la **Boîte à outils**.  
  
-   Cliquez avec le bouton droit sur le Concepteur de ruban, puis cliquez sur **Onglet Ajouter un ruban**.  
  
-   Ouvrez l'**Éditeur de collections Tab**, puis cliquez sur **Ajouter**.  
  
     Pour ouvrir l'**Éditeur de collections Tab**, dans la fenêtre **Propriétés**, sélectionnez la propriété **Tabs**, puis cliquez sur le bouton de sélection ![Bouton de sélection du concepteur ASP.NET mobile](../sharepoint/media/mwellipsis.png "Bouton de sélection du concepteur ASP.NET mobile").  
  
 Après avoir ajouté un onglet, vous pouvez ajouter des groupes qui contiendront des contrôles.  
  
#### Suppression d'onglets personnalisés du ruban  
 Il existe trois façons de supprimer un onglet personnalisé du ruban :  
  
-   Cliquez avec le bouton droit sur le concepteur, puis cliquez sur **Onglet Supprimer un ruban**.  
  
-   Dans le volet **Commandes** de la fenêtre **Propriétés**, cliquez sur **Onglet Supprimer un ruban**.  
  
-   Ouvrez l'**Éditeur de collections Tab**, sélectionnez l'onglet, puis cliquez sur **Supprimer**.  
  
#### Modification de la position d'un onglet dans le ruban  
 Vous pouvez modifier l'ordre des onglets personnalisés dans le ruban.  Vous pouvez également positionner les onglets personnalisés avant ou après un onglet prédéfini du ruban.  Pour plus d'informations, consultez [Comment : modifier la position d'un onglet dans le ruban](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md).  
  
#### Personnalisation des onglets intégrés sur le ruban  
 Un onglet intégré est un onglet qui figure déjà sur le ruban d'une application Microsoft Office.  Par exemple, l'onglet **Données** est un onglet intégré dans Excel.  
  
 Vous pouvez ajouter des groupes et des contrôles à un onglet intégré.  Par défaut, un groupe personnalisé apparaît comme le dernier groupe sur un onglet intégré, même si vous pouvez le déplacer avant ou après tout groupe prédéfini sur l'onglet.  
  
 Vous ne pouvez pas supprimer de groupes prédéfinis.  
  
 Pour plus d'informations sur la personnalisation d'un onglet intégré, consultez [Comment : personnaliser un onglet intégré](../vsto/how-to-customize-a-built-in-tab.md).  
  
###  <a name="AddGroupsToTab"></a> Ajout de groupes à un onglet  
 Les groupes organisent de façon logique les contrôles sur le ruban.  Ajoutez des groupes à des onglets.  Ajoutez tous les autres contrôles au groupe.  
  
###  <a name="AddControlsToGroups"></a> Ajout de contrôles aux groupes  
 Ajoutez un ou plusieurs contrôles à un groupe.  Le tableau suivant décrit chaque contrôle.  
  
|Contrôle|Description|  
|--------------|-----------------|  
|**Box**|Conteneur qui organise des contrôles dans un groupe.  Vous pouvez ajouter n'importe quel contrôle à une zone, à l'exception d'un séparateur, d'un groupe ou d'un onglet.  Une zone peut être horizontale ou verticale.|  
|**Button**|Bouton qui démarre une action.  Vous pouvez ajouter un bouton à un groupe, un groupe de boutons, une liste déroulante, une galerie, un menu ou un bouton partagé.|  
|**Buttongroup**|Groupe qui contient un ou plusieurs boutons, boutons bascule, menus, boutons partagés et galeries.  Vous pouvez ajouter un groupe de boutons à un groupe ou un menu.|  
|**CheckBox**|Zone sélectionnée ou désactivée pour activer ou désactiver une option.|  
|**ComboBox**|Zone d'édition avec une zone de liste jointe.  Les utilisateurs peuvent taper ou sélectionner leur choix.  La zone affiche la sélection actuelle.  Utilisez la propriété <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.Items%2A> pour ajouter et supprimer des éléments au moment de l'exécution avant ou après que le ruban soit chargé dans l'application Office.|  
|**DropDown**|Liste des éléments que l'utilisateur peut sélectionner.  L'utilisateur ne peut pas entrer de nouvel élément dans une liste déroulante.<br /><br /> Utilisez la méthode <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.Items%2A> pour ajouter des éléments à la liste.  Vous pouvez ajouter et supprimer des éléments au moment de l'exécution.<br /><br /> Utilisez la propriété <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.Buttons%2A> pour ajouter des boutons à la liste.  Toutefois, vous ne pouvez pas ajouter et supprimer des boutons au moment de l'exécution après que le ruban a été chargé dans l'application Office.|  
|**EditBox**|Zone dans laquelle l'utilisateur peut entrer du texte.|  
|**Gallery**|Menu qui contient un tableau ou une grille de choix visuels sélectionnables par les utilisateurs.  Vous pouvez contrôler la disposition des sélections dans le menu.  Utilisez les propriétés <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ColumnCount%2A> et <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.RowCount%2A> pour spécifier le nombre de lignes et de colonnes qui afficheront les éléments et les boutons de la galerie.|  
|**Étiquette**|Texte que vous pouvez utiliser pour identifier des contrôles sur le ruban.|  
|**Menu**|Liste déroulante qui peut contenir chacun des contrôles suivants :<br /><br /> -   Button<br />-   Check Box<br />-   Gallery<br />-   Menu<br />-   Split Button<br />-   Toggle button<br />-   Separator<br /><br /> Pour ajouter un contrôle à un menu dans le Concepteur de ruban, cliquez sur la flèche bas dans le menu pour exposer l'aire de conception de menu.  Vous pouvez ensuite faire glisser des contrôles du ruban de la **Boîte à outils** vers le menu.  Pour réorganiser des contrôles, faites\-les glisser aux emplacements souhaités.<br /><br /> Pour ajouter des contrôles au <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu> après que le ruban a été chargé dans l'application Office, vous devez affecter la valeur **true** à la propriété <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu.Dynamic%2A> avant que le ruban soit chargé.  Pour plus d'informations sur la procédure à suivre, consultez [Vue d'ensemble du modèle objet de ruban](../vsto/ribbon-object-model-overview.md).|  
|**Separator**|Barre mince utilisée pour séparer des éléments d'une liste.  En cas d'ajout à un groupe, la barre est verticale.  En cas d'ajout à un menu, la barre est horizontale.|  
|**SplitButton**|Bouton avec un menu joint.  Bouton partagé pouvant contenir chacun des contrôles suivants :<br /><br /> -   Button<br />-   Check Box<br />-   Gallery<br />-   Menu<br />-   Split Button<br />-   Toggle button<br />-   Separator<br /><br /> À l'instar du menu, le bouton partagé a sa propre aire de conception.  Toutefois, contrairement à un menu, vous pouvez uniquement mettre à jour les éléments dans un bouton partagé avant que le ruban soit chargé dans l'application Office.  Pour plus d'informations sur la mise à jour des éléments dans un bouton partagé, consultez [Vue d'ensemble du modèle objet de ruban](../vsto/ribbon-object-model-overview.md).|  
|**ToggleButton**|Bouton qui s'affiche comme activé ou non activé.|  
  
##  <a name="HandleEventsSetProperties"></a> Gestion des événements et définition des propriétés  
 Le Concepteur de ruban vous permet de définir des propriétés de contrôle au moment de la conception en utilisant la fenêtre **Propriétés**.  De plus, le ruban expose un modèle objet fortement typé que vous pouvez utiliser pour obtenir et définir les propriétés de contrôles de ruban au moment de l'exécution.  
  
 Vous pouvez double\-cliquer sur un contrôle du concepteur pour ouvrir un gestionnaire pour l'événement par défaut du contrôle.  Vous pouvez créer des gestionnaires d'événements pour toues les autres événements du contrôle à l'aide de la fenêtre **Propriétés**.  
  
 Les événements et les propriétés du ruban sont situés dans l'espace de noms <xref:Microsoft.Office.Tools.Ribbon>.  L'élément **Ruban \(Concepteur visuel\)** ajoute automatiquement une référence à cet assembly dans le projet et insère l'instruction  **using** ou **Imports** approprié en haut du fichier de code du ruban.  
  
 Pour plus d'informations sur la gestion d'événements du ruban et la définition des propriétés de contrôles du ruban au moment de l'exécution, consultez [Vue d'ensemble du modèle objet de ruban](../vsto/ribbon-object-model-overview.md).  
  
##  <a name="CustomizingMicrosoftOfficeButton"></a> Personnalisation du mode Backstage  
 Vous pouvez utiliser le concepteur de ruban pour ajouter des contrôles au menu qui s'ouvre lorsque vous cliquez sur l'onglet **Fichier**.  Ce menu est appelé mode Backstage.  
  
 Vous ne pouvez pas placer de contrôles avant ou après les contrôles prédéfinis en utilisant le concepteur de ruban.  Un contrôle intégré est un contrôle apparaissant déjà en mode Backstage.  Si vous souhaitez positionner des contrôles avant ou après les contrôles prédéfinis, vous devez utiliser Ruban XML.  Pour plus d'informations sur **Ruban \(XML\)**, consultez [Élément XML Ribbon](../vsto/ribbon-xml.md).  Pour plus d'informations sur la personnalisation du mode Backstage, consultez [Introduction au mode Backstage Office 2010 pour les développeurs](http://go.microsoft.com/fwlink/?LinkId=182189) et [Personnalisation du mode Backstage Office 2010 pour les développeurs](http://go.microsoft.com/fwlink/?LinkId=182188).  
  
 [!INCLUDE[appliesto_ribbon_2010](../vsto/includes/appliesto-ribbon-2010-md.md)]  
  
 Pour plus d'informations sur la façon d'ajouter des contrôles au mode Backstage, consultez [Comment : ajouter des contrôles au mode Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md).  
  
##  <a name="Accessibility"></a> Accessibilité dans le Concepteur de ruban  
 Vous pouvez utiliser des raccourcis clavier pour déplacer des contrôles dans le Concepteur de ruban.  Certains raccourcis clavier s'appliquent à tous les contrôles, d'autres s'appliquent à uniquement à des contrôles qui ont des menus.  
  
 Les raccourcis clavier qui s'appliquent à tous les contrôles sont présentés dans le tableau suivant.  
  
|Action|Raccourci clavier|  
|------------|-----------------------|  
|Déplacer un contrôle avant le contrôle précédent dans la liste.|CTRL\+HAUT<br /><br /> CTRL\+GAUCHE|  
|Déplacer un contrôle après le contrôle suivant dans la liste.|CTRL\+BAS<br /><br /> CTRL\+DROITE|  
|Déplacer la sélection d'un contrôle vers un autre dans le même groupe.  Dans le cas d'un panneau déroulant, déplacer entre le contrôle parent et les contrôles dans le panneau déroulant.|HAUT<br /><br /> DOWN|  
|Itérer dans le sens normal au sein de tous les contrôles.|TAB|  
|Itérer dans le sens inverse au sein de tous les contrôles.|MAJ\+TAB|  
|Supprimer le contrôle ou le jeu de contrôles sélectionné.|DELETE|  
|Copier les contrôles sélectionnés.|Ctrl\+C|  
|Couper les contrôles sélectionnés.|Ctrl\+X|  
|Coller les contrôles à partir du Presse\-papiers.|Ctrl\+V|  
|Sélectionner la **Boîte à outils**.|CTRL\+ALT\+X|  
|Sélectionner le composant parent.|ÉCHAP|  
  
 Les raccourcis clavier qui s'appliquent uniquement au Menu Microsoft Office, <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu> et <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton> sont présentés dans le tableau suivant.  
  
|Action|Raccourci clavier|  
|------------|-----------------------|  
|Sélectionner le contrôle parent si le panneau déroulant est ouvert et un contrôle est sélectionné sur le panneau déroulant.|GAUCHE|  
|Fermer le panneau déroulant si le panneau déroulant est ouvert et le contrôle parent est sélectionné.|GAUCHE|  
|Ouvrir le panneau déroulant.|DROIT|  
|Sélectionner le premier contrôle sur le panneau déroulant si le panneau déroulant est ouvert.|DROIT|  
|Fermer un panneau déroulant.|ÉCHAP|  
  
## Voir aussi  
 [Vue d'ensemble du ruban](../vsto/ribbon-overview.md)   
 [Élément XML Ribbon](../vsto/ribbon-xml.md)   
 [Procédure pas à pas : création d'un onglet personnalisé à l'aide du Concepteur de ruban](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Comment : exporter un ruban à partir du Concepteur de ruban vers l'élément XML Ribbon](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)   
 [Comment : démarrer avec la personnalisation du ruban](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [Accès au ruban au moment de l'exécution](../vsto/accessing-the-ribbon-at-run-time.md)  
  
  