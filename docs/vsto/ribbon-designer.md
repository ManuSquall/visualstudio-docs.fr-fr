---
title: Concepteur de ruban | Documents Microsoft
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: Designer_Microsoft.VisualStudio.Tools.Office.Ribbon.Design.RibbonDesigner
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom Ribbon, about Ribbon Designer
- controls [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio], controls
- customizing the Ribbon, about Ribbon Designer
- Ribbon [Office development in Visual Studio], visual designer
- customizing the Ribbon
- custom Ribbon
- designers [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio], customizing
- Ribbon [Office development in Visual Studio], common tasks
- Ribbon Designer [Office development in Visual Studio]
- read-only properties
- Ribbon [Office development in Visual Studio], shortcut keys
ms.assetid: 26617206-f4da-416f-a18a-d817b2d4872d
caps.latest.revision: "79"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 2655cd8f8c75f9c10063a1b85d2390b153782d85
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ribbon-designer"></a>Concepteur de ruban
  Le Concepteur de ruban est une zone de conception visuelle. Utilisez le Concepteur de ruban pour ajouter des onglets personnalisés, des groupes et des contrôles au ruban d’une application Microsoft Office.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
 Pour ouvrir le Concepteur de ruban, ajoutez un **ruban (Concepteur visuel)** élément à votre projet. Vous pouvez ensuite utiliser les outils de conception pour les tâches suivantes :  
  
-   [Concevoir la disposition du ruban](#DesigningRibbonLayout)  
  
-   [Gérer les événements et définir les propriétés de contrôle](#HandleEventsSetProperties)  
  
-   [Ajouter des contrôles au mode Backstage](#CustomizingMicrosoftOfficeButton)  
  
> [!NOTE]  
>  Il existe certaines tâches que vous ne pouvez pas effectuer à l’aide du Concepteur de ruban. Pour plus d’informations sur ces tâches et comment y répondre, consultez [vue d’ensemble du ruban](../vsto/ribbon-overview.md).  
  
 ![lien vers la vidéo](../vsto/media/playvideo.gif "lien vidéo") pour une démonstration vidéo connexe, consultez [comment faire : utiliser le Concepteur de ruban pour personnaliser le ruban dans Outlook ?](http://go.microsoft.com/fwlink/?LinkID=130312).  
  
## <a name="adding-a-ribbon-visual-designer-item-to-a-project"></a>Ajout d’un élément Ruban (Concepteur visuel) à un projet  
 Pour utiliser le Concepteur de ruban, ajoutez un nouveau **ruban (Concepteur visuel)** élément à votre projet. Pour plus d'informations, consultez [How to: Get Started Customizing the Ribbon](../vsto/how-to-get-started-customizing-the-ribbon.md).  
  
 Lorsque vous ajoutez un nouveau **ruban (Concepteur visuel)** article, Visual Studio ajoute automatiquement les fichiers suivants à votre projet :  
  
-   Un fichier de code du ruban. Ce fichier porte le nom que vous spécifiez pour le **ruban (Concepteur visuel)** d’élément dans le **ajouter un nouvel élément** boîte de dialogue. Ajoutez du code pour gérer les événements de ruban pour ce fichier.  
  
-   Fichier de code du Concepteur de ruban. Ce fichier contient le code généré par le Concepteur de ruban et ne doit pas être modifié directement.  
  
-   Un fichier de ressources. Ce fichier contient les valeurs de propriété de chaque contrôle sur le ruban.  
  
 Si vous avez déjà un **ruban (Concepteur visuel)** élément à partir d’un autre projet, vous pouvez la réutiliser dans votre projet actuel à l’aide de la **ajouter un élément existant** boîte de dialogue.  
  
##  <a name="DesigningRibbonLayout"></a>Conception d’un ruban  
 Il existe trois façons d’ouvrir le Concepteur de ruban :  
  
-   Dans **l’Explorateur de solutions**, double-cliquez sur le fichier de code du ruban.  
  
-   Dans **l’Explorateur de solutions**, cliquez sur le fichier de code du ruban, puis cliquez sur **Concepteur de vue**.  
  
-   Dans **l’Explorateur de solutions**, sélectionnez le fichier de code du ruban, puis cliquez sur **concepteur** sur la **vue** menu.  
  
 Le Concepteur de ruban contient un onglet par défaut et un groupe. Vous pouvez supprimer l’onglet par défaut et le groupe à partir du Concepteur de ruban. Pour supprimer le groupe par défaut, avec le bouton droit **Group1**, puis cliquez sur **supprimer**. Pour supprimer l’onglet par défaut, cliquez sur une zone vide de l’aire de conception, puis cliquez sur **supprimer un onglet de ruban**.  
  
 Vous pouvez également ajouter des onglets personnalisés, des groupes et des contrôles au Concepteur de ruban. Vous pouvez rechercher ces contrôles dans le **boîte à outils**, dans le **contrôles de ruban Office** groupe. Il existe trois façons d’ajouter des contrôles à partir de la **contrôles de ruban Office** groupe au Concepteur de ruban :  
  
-   Faites glisser un contrôle à une zone appropriée sur le Concepteur de ruban.  
  
-   Cliquez sur un contrôle, puis sur une zone appropriée dans le Concepteur de ruban.  
  
-   Sélectionnez une zone appropriée dans le concepteur, puis double-cliquez sur un contrôle dans le **boîte à outils**.  
  
### <a name="ribbon-design-workflow"></a>Flux de travail de conception du ruban  
 Suivez ces étapes de base pour concevoir la disposition de ruban :  
  
1.  [Ajouter un onglet personnalisé au ruban](#AddTabToRibbon).  
  
2.  [Ajouter des groupes à l’onglet](#AddGroupsToTab).  
  
3.  [Ajouter des contrôles aux groupes](#AddControlsToGroups).  
  
 Les contrôles peuvent être supprimés uniquement sur des groupes ; Vous ne peut pas faire glisser un contrôle directement à un onglet ou au ruban. Les groupes peuvent être supprimés uniquement sur des onglets ; Vous ne pouvez pas faire glisser un groupe de directement à un ruban.  
  
 Organiser les contrôles en les faisant glisser vers les positions appropriées. Vous pouvez définir les propriétés d’un contrôle à l’aide de la **propriétés** fenêtre.  
  
 Vous ne peut pas faire glisser des contrôles à partir d’un onglet à un autre sur le ruban. Si vous souhaitez déplacer un contrôle vers un autre onglet, vous devez utiliser le **couper** commande pour supprimer le contrôle d’un onglet, puis collez le contrôle sur un autre onglet. Si vous le contrôle de couper et coller, le Gestionnaire d’événements cesse de fonctionner. Vous pouvez vous reconnecter le Gestionnaire d’événements dans le **propriétés** fenêtre. Pour plus d’informations, consultez [fenêtre Propriétés](/visualstudio/ide/reference/properties-window).  
  
###  <a name="AddTabToRibbon"></a>Ajouter des onglets personnalisés au ruban  
 Il existe trois façons d’ajouter un onglet personnalisé au ruban :  
  
-   Ajouter un onglet à partir de la **boîte à outils**.  
  
-   Cliquez sur le Concepteur de ruban, puis cliquez sur **ajouter un onglet de ruban**.  
  
-   Ouvrez le **éditeur de collections Tab**, puis cliquez sur **ajouter**.  
  
     Pour ouvrir la **éditeur de collections Tab**, dans le **propriétés** fenêtre, sélectionnez le **onglets** propriété, puis cliquez sur le bouton de sélection ![Mobile ASP.NET Ellipse concepteur](../sharepoint/media/mwellipsis.gif "ellipse de concepteur ASP.NET Mobile").  
  
 Après avoir ajouté un onglet, vous pouvez ajouter des groupes pour contenir des contrôles.  
  
#### <a name="removing-custom-tabs-from-the-ribbon"></a>Suppression des onglets personnalisés du ruban  
 Il existe trois façons de supprimer un onglet personnalisé à partir du ruban :  
  
-   Cliquez sur le concepteur, puis cliquez sur **supprimer un onglet de ruban**.  
  
-   Dans le **commandes** volet de la **propriétés** fenêtre, cliquez sur **supprimer un onglet de ruban**.  
  
-   Ouvrez le **éditeur de collections Tab**, sélectionnez l’onglet, puis cliquez sur **supprimer**.  
  
#### <a name="changing-the-position-of-a-tab-on-the-ribbon"></a>Modification de la Position d’un onglet sur le ruban  
 Vous pouvez modifier l’ordre des onglets personnalisés sur un ruban. Vous pouvez également placer des onglets personnalisés avant ou après un onglet intégré du ruban. Pour plus d’informations, consultez [Comment : modifier la Position d’un onglet sur le ruban](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md).  
  
#### <a name="customizing-built-in-tabs-on-the-ribbon"></a>Personnalisation des onglets intégrés sur le ruban  
 Un onglet intégré est un onglet qui existe déjà sur le ruban d’une application Microsoft Office. Par exemple, le **données** onglet est un onglet intégré dans Excel.  
  
 Vous pouvez ajouter des groupes et des contrôles à un onglet intégré. Par défaut, un groupe personnalisé apparaît comme le dernier groupe sur un onglet intégré, bien que vous pouvez le déplacer avant ou après un groupe intégré sur l’onglet.  
  
 Vous ne pouvez pas supprimer les groupes intégrés.  
  
 Pour plus d’informations sur la façon de personnaliser un onglet intégré, consultez [Comment : personnaliser un onglet intégré](../vsto/how-to-customize-a-built-in-tab.md).  
  
###  <a name="AddGroupsToTab"></a>L’ajout des groupes à un onglet  
 Groupes organisent logiquement les contrôles sur le ruban. Ajouter des groupes à onglets. Ajoutez tous les autres contrôles au groupe.  
  
###  <a name="AddControlsToGroups"></a>Ajout de contrôles à des groupes  
 Ajouter un ou plusieurs contrôles à un groupe. Le tableau suivant décrit chaque contrôle.  
  
|Contrôle|Description|  
|-------------|-----------------|  
|**Boîte de**|Un conteneur qui organise des contrôles dans un groupe. Vous pouvez ajouter n’importe quel contrôle à une zone à l’exception d’un séparateur, un groupe ou une tabulation. Une zone peut être horizontale ou verticale.|  
|**Button**|Bouton qui lance une action. Vous pouvez ajouter un bouton à un groupe, un groupe de boutons, une liste déroulante, une galerie, un menu ou un bouton partagé.|  
|**Groupe de boutons**|Un groupe qui contient un ou plusieurs boutons, boutons bascule, menus, boutons partagés et des galeries. Vous pouvez ajouter un groupe à un groupe ou un menu.|  
|**CheckBox**|Une zone est activée ou désactivée pour activer ou désactiver une option.|  
|**ComboBox**|Une zone d’édition avec une zone de liste. Les utilisateurs peuvent tapez ou sélectionnez de leur choix. La zone affiche la sélection actuelle. Utilisez le <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.Items%2A> propriété à ajouter et supprimer des éléments au moment de l’exécution avant ou après le chargement du ruban dans l’application Office.|  
|**Liste déroulante**|Une liste d’éléments que l’utilisateur peut sélectionner. L’utilisateur ne peut pas entrer un nouvel élément dans une liste déroulante.<br /><br /> Utilisez le <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.Items%2A> propriété à ajouter des éléments à la liste. Vous pouvez ajouter et supprimer des éléments au moment de l’exécution.<br /><br /> Utilisez le <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.Buttons%2A> propriété pour ajouter des boutons à la liste. Toutefois, vous ne pouvez pas ajouter et supprimer des boutons au moment de l’exécution après le chargement du ruban dans l’application Office.|  
|**Zone d’édition**|Une zone dans laquelle l’utilisateur peut taper le texte.|  
|**Galerie**|Un menu qui présente un tableau ou une grille de choix visuels à partir de laquelle les utilisateurs peuvent sélectionner. Vous pouvez contrôler la disposition des sélections dans le menu. Utilisez le <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ColumnCount%2A> et <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.RowCount%2A> des propriétés pour spécifier le nombre de lignes et colonnes qui affichent les éléments et les boutons de la galerie.|  
|**Label**|Texte que vous pouvez utiliser pour identifier les contrôles sur le ruban.|  
|**Menu**|Une liste déroulante qui peut contenir l’un des contrôles suivants :<br /><br /> -Bouton<br />-Case à cocher<br />-La galerie<br />-Menu<br />-Bouton Fractionner<br />-Bouton bascule<br />-Séparateur<br /><br /> Pour ajouter un contrôle à un menu dans le Concepteur de ruban, cliquez sur la flèche vers le bas dans le menu pour exposer l’aire de conception de menu. Vous pouvez ensuite faire glisser des contrôles de ruban à partir de la **boîte à outils** sur le menu. Pour réorganiser des contrôles, faites-les glisser vers la position souhaitée.<br /><br /> Pour ajouter des contrôles à la <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu> après le chargement du ruban dans l’application Office, vous devez définir le <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu.Dynamic%2A> propriété **true** avant le chargement du ruban. Pour plus d’informations sur la procédure à suivre, consultez [présentation du modèle objet de ruban](../vsto/ribbon-object-model-overview.md).|  
|**Separator**|Une fine barre utilisée pour séparer les éléments d’une liste. Lors de l’ajout à un groupe, la barre est verticale. Lors de l’ajout à un menu, la barre est horizontale.|  
|**SplitButton**|Un bouton avec un menu joint. Un bouton partagé peut contenir les contrôles suivants :<br /><br /> -Bouton<br />-Case à cocher<br />-La galerie<br />-Menu<br />-Bouton Fractionner<br />-Bouton bascule<br />-Séparateur<br /><br /> Comme le menu, le bouton partagé possède sa propre aire de conception. Toutefois, contrairement à un menu, vous pouvez uniquement mettre à jour les éléments dans un bouton partagé avant le chargement du ruban dans l’application Office. Pour plus d’informations sur la façon de mettre à jour les éléments dans un bouton partagé, consultez [présentation du modèle objet de ruban](../vsto/ribbon-object-model-overview.md).|  
|**Bouton bascule**|Un bouton apparaît activé ou désactivé.|  
  
##  <a name="HandleEventsSetProperties"></a>La gestion des événements et en définissant des propriétés  
 Le Concepteur de ruban vous permet de définir des propriétés du contrôle au moment du design à l’aide du **propriétés** fenêtre. En outre, le ruban expose un modèle objet fortement typé que vous pouvez utiliser pour obtenir et définir les propriétés des contrôles de ruban au moment de l’exécution.  
  
 Vous pouvez double-cliquer sur n’importe quel contrôle sur le concepteur pour ouvrir le Gestionnaire d’événements pour l’événement du contrôle par défaut. Vous pouvez créer des gestionnaires d’événements pour tous les autres événements de contrôle à l’aide de la **propriétés** fenêtre.  
  
 Les événements de ruban et les propriétés se trouvent dans le <xref:Microsoft.Office.Tools.Ribbon> espace de noms. Le **ruban (Concepteur visuel)** élément ajoute automatiquement une référence à cet assembly dans le projet et insère les **à l’aide de** ou **importations** instruction en haut du fichier de code du ruban.  
  
 Pour plus d’informations sur la gestion des événements de ruban et la définition des propriétés des contrôles de ruban au moment de l’exécution, consultez [présentation du modèle objet de ruban](../vsto/ribbon-object-model-overview.md).  
  
##  <a name="CustomizingMicrosoftOfficeButton"></a>Personnalisation du mode Backstage  
 Vous pouvez utiliser le Concepteur de ruban pour ajouter des contrôles au menu qui s’ouvre lorsque vous cliquez sur le **fichier** onglet. Ce menu est appelé le mode Backstage.  
  
 Vous ne pouvez pas positionner des contrôles avant ou après les contrôles prédéfinis à l’aide du Concepteur de ruban. Un contrôle intégré est un contrôle qui figure déjà dans le mode Backstage. Si vous souhaitez positionner des contrôles avant ou après les contrôles intégrés, vous devez utiliser XML du ruban. Pour plus d’informations sur **ruban (XML)**, consultez [ruban XML](../vsto/ribbon-xml.md). Pour plus d’informations sur la personnalisation du mode Backstage, consultez [présentation du mode Backstage Office 2010 pour les développeurs](http://go.microsoft.com/fwlink/?LinkId=182189) et [personnalisation du mode Backstage Office 2010 pour les développeurs](http://go.microsoft.com/fwlink/?LinkId=182188).  
  
 [!INCLUDE[appliesto_ribbon_2010](../vsto/includes/appliesto-ribbon-2010-md.md)]  
  
 Pour plus d’informations sur l’ajout de contrôles pour le mode Backstage, consultez [Comment : ajouter des contrôles au mode Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md).  
  
##  <a name="Accessibility"></a>Accessibilité dans le Concepteur de ruban  
 Vous pouvez utiliser les raccourcis clavier pour déplacer les contrôles dans le Concepteur de ruban. Certains raccourcis clavier s’appliquent à tous les contrôles, et certains s’appliquent uniquement aux contrôles qui ont des menus.  
  
 Les raccourcis clavier qui s’appliquent à tous les contrôles sont affichés dans le tableau suivant.  
  
|Action|Raccourci clavier|  
|------------|-----------------------|  
|Déplacer un contrôle avant que le contrôle précédent dans la liste.|CTRL + HAUT<br /><br /> CTRL + GAUCHE|  
|Déplacer un contrôle après le contrôle suivant dans la liste.|CTRL + BAS<br /><br /> CTRL + DROITE|  
|Déplacer la sélection d’un contrôle à un autre dans le même groupe. Pour un panneau déroulant, déplacer entre le contrôle parent et les contrôles dans le volet de la liste déroulante.|HAUT<br /><br /> BAS|  
|Itérer dans tous les contrôles.|TAB|  
|Effectuer une itération dans le sens inverse à tous les contrôles.|MAJ+TAB|  
|Supprimer le contrôle sélectionné ou l’ensemble de contrôles.|SUPPR|  
|Copiez les contrôles sélectionnés.|CTRL+C|  
|Couper les contrôles sélectionnés.|Ctrl+X|  
|Coller les contrôles à partir du Presse-papiers.|CTRL+V|  
|Sélectionnez le **boîte à outils**.|CTRL+ALT+X|  
|Sélectionnez le composant parent.|ÉCHAP|  
  
 Les raccourcis clavier qui s’appliquent uniquement au Menu Microsoft Office, <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>, et <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton> sont affichées dans le tableau suivant.  
  
|Action|Raccourci clavier|  
|------------|-----------------------|  
|Sélectionnez le contrôle parent si le panneau déroulant est ouvert et un contrôle sélectionné dans le volet de la liste déroulante.|LEFT|  
|Fermez le panneau déroulant si le panneau déroulant est ouvert et le contrôle parent est sélectionné.|LEFT|  
|Ouvrez le panneau de la liste déroulante.|RIGHT|  
|Sélectionnez le premier contrôle dans le volet de la liste déroulante si le panneau déroulant est ouvert.|RIGHT|  
|Fermer un panneau déroulant.|ÉCHAP|  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble du ruban](../vsto/ribbon-overview.md)   
 [Élément XML Ribbon](../vsto/ribbon-xml.md)   
 [Procédure pas à pas : Création d’un onglet personnalisé à l’aide du Concepteur de ruban](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Comment : exporter un ruban à partir du Concepteur de ruban vers ruban XML](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)   
 [Comment : démarrer avec la personnalisation du ruban](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [Accès au ruban au moment de l’exécution](../vsto/accessing-the-ribbon-at-run-time.md)  
  
  