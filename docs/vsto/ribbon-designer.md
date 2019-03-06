---
title: Concepteur de ruban
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- Designer_Microsoft.VisualStudio.Tools.Office.Ribbon.Design.RibbonDesigner
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f923c4762a78f43d2d9b1ba3df990c148a074e68
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54867258"
---
# <a name="ribbon-designer"></a>Concepteur de ruban
  Le Concepteur de ruban est une zone de conception visuelle. Utilisez le Concepteur de ruban pour ajouter des onglets, groupes et contrôles personnalisés au ruban d’une application Microsoft Office.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

 Pour ouvrir le Concepteur de ruban, ajoutez un **ruban (Concepteur visuel)** élément à votre projet. Vous pouvez ensuite utiliser les outils de conception pour les tâches suivantes :

-   [Concevoir la disposition du ruban](#DesigningRibbonLayout)

-   [Gérer les événements et définir les propriétés de contrôle](#HandleEventsSetProperties)

-   [Ajouter des contrôles au mode Backstage](#CustomizingMicrosoftOfficeButton)

> [!NOTE]
>  Il existe certaines tâches que vous ne pouvez pas accomplir à l’aide du Concepteur de ruban. Pour plus d’informations sur ces tâches et comment vous pouvez les réaliser, consultez [vue d’ensemble du ruban](../vsto/ribbon-overview.md).

 ![lien vers la vidéo](../vsto/media/playvideo.gif "lien vers la vidéo") pour une démonstration vidéo connexe, consultez [How do I: Utiliser le Concepteur de ruban pour personnaliser le ruban dans Outlook ? ](http://go.microsoft.com/fwlink/?LinkID=130312).

## <a name="add-a-ribbon-visual-designer-item-to-a-project"></a>Ajouter un élément Ruban (Concepteur visuel) à un projet
 Pour utiliser le Concepteur de ruban, ajoutez un nouveau **ruban (Concepteur visuel)** élément à votre projet. Pour plus d'informations, voir [Procédure : Commencer la personnalisation du ruban](../vsto/how-to-get-started-customizing-the-ribbon.md).

 Lorsque vous ajoutez un nouveau **ruban (Concepteur visuel)** élément, Visual Studio ajoute automatiquement les fichiers suivants à votre projet :

- Un fichier de code du ruban. Ce fichier porte le nom que vous spécifiez pour le **ruban (Concepteur visuel)** d’élément dans le **ajouter un nouvel élément** boîte de dialogue. Ajoutez du code pour gérer les événements de ruban pour ce fichier.

- Un fichier de code concepteur de ruban. Ce fichier contient le code généré par le Concepteur de ruban et ne doit pas être modifié directement.

- Un fichier de ressources. Ce fichier contient les valeurs de propriété de chaque contrôle sur le ruban.

  Si vous avez déjà un **ruban (Concepteur visuel)** élément à partir d’un autre projet, vous pouvez le réutiliser dans votre projet actuel à l’aide de la **ajouter un élément existant** boîte de dialogue.

##  <a name="DesigningRibbonLayout"></a> Concevoir un ruban
 Il existe trois façons d’ouvrir le Concepteur de ruban :

- Dans **l’Explorateur de solutions**, double-cliquez sur le fichier de code du ruban.

- Dans **l’Explorateur de solutions**, cliquez sur le fichier de code de ruban, puis cliquez sur **Concepteur de vues**.

- Dans **l’Explorateur de solutions**, sélectionnez le fichier de code de ruban, puis cliquez sur **concepteur** sur le **vue** menu.

  Le Concepteur de ruban contient un onglet par défaut et un groupe. Vous pouvez supprimer l’onglet par défaut et le groupe à partir du Concepteur de ruban. Pour supprimer le groupe par défaut, avec le bouton droit **Group1**, puis cliquez sur **supprimer**. Pour supprimer l’onglet par défaut, cliquez sur une zone vide de l’aire de conception, puis cliquez sur **onglet supprimer un ruban**.

  Vous pouvez également ajouter des onglets personnalisés, des groupes et des contrôles au Concepteur de ruban. Vous pouvez rechercher ces contrôles dans le **boîte à outils**, dans le **contrôles de ruban Office** groupe. Il existe trois façons d’ajouter des contrôles à partir de la **contrôles de ruban Office** groupe au Concepteur de ruban :

- Faites glisser un contrôle à une zone appropriée sur le Concepteur de ruban.

- Cliquez sur un contrôle, puis sur une zone appropriée du Concepteur de ruban.

- Sélectionnez une zone appropriée dans le concepteur, puis double-cliquez sur un contrôle dans le **boîte à outils**.

### <a name="ribbon-design-workflow"></a>Flux de travail de conception du ruban
 Suivez ces étapes de base pour concevoir la disposition du ruban :

1. [Ajouter un onglet personnalisé au ruban](#AddTabToRibbon).

2. [Ajouter des groupes à l’onglet](#AddGroupsToTab).

3. [Ajouter des contrôles aux groupes](#AddControlsToGroups).

   Les contrôles peuvent uniquement être déplacés sur des groupes ; Vous ne peut pas faire glisser un contrôle directement à un onglet ou vers le ruban. Les groupes peuvent être déplacés uniquement sur des onglets ; Vous ne pouvez pas faire glisser un groupe directement à un ruban.

   Organiser les contrôles en les faisant glisser vers les positions appropriées. Vous pouvez définir les propriétés d’un contrôle à l’aide de la **propriétés** fenêtre.

   Vous ne pouvez pas faire glisser des contrôles d’un onglet à un autre sur le ruban. Si vous souhaitez déplacer un contrôle vers un autre onglet, vous devez utiliser le **couper** commande pour supprimer le contrôle d’un onglet, puis collez le contrôle sur un autre onglet. Si vous coupez le contrôle et le coller, le Gestionnaire d’événements cesse de fonctionner. Vous pouvez vous reconnecter le Gestionnaire d’événements dans le **propriétés** fenêtre. Pour plus d’informations, consultez [fenêtre Propriétés](../ide/reference/properties-window.md).

###  <a name="AddTabToRibbon"></a> Ajouter des onglets personnalisés au ruban
 Il existe trois façons d’ajouter un onglet personnalisé au ruban :

- Ajouter un onglet à partir de la **boîte à outils**.

- Cliquez sur le Concepteur de ruban, puis cliquez sur **ajouter un onglet de ruban**.

- Ouvrez le **éditeur de collections Tab**, puis cliquez sur **ajouter**.

   Pour ouvrir le **éditeur de collections Tab**, dans le **propriétés** fenêtre, sélectionnez le **onglets** propriété, puis cliquez sur le bouton de sélection ![ASP.NET Mobile Ellipse concepteur](../sharepoint/media/mwellipsis.gif "ellipse de concepteur ASP.NET Mobile").

  Après avoir ajouté un onglet, vous pouvez ajouter des groupes qui contiendront des contrôles.

#### <a name="remove-custom-tabs-from-the-ribbon"></a>Supprimer des onglets personnalisés du ruban
 Il existe trois façons de supprimer un onglet personnalisé du ruban :

-   Cliquez sur le concepteur, puis cliquez sur **onglet supprimer un ruban**.

-   Dans le **commandes** volet de la **propriétés** fenêtre, cliquez sur **onglet supprimer un ruban**.

-   Ouvrez le **éditeur de collections Tab**, sélectionnez l’onglet, puis cliquez sur **supprimer**.

#### <a name="change-the-position-of-a-tab-on-the-ribbon"></a>Modifier la position d’un onglet dans le ruban
 Vous pouvez modifier l’ordre des onglets personnalisés sur un ruban. Vous pouvez également positionner les onglets personnalisés avant ou après un onglet prédéfini du ruban. Pour plus d'informations, voir [Procédure : Modifier la position d’un onglet dans le ruban](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md).

#### <a name="customize-built-in-tabs-on-the-ribbon"></a>Personnaliser des onglets intégrés sur le ruban
 Un onglet intégré est un onglet qui se trouve déjà sur le ruban d’une application Microsoft Office. Par exemple, le **données** onglet est un onglet intégré dans Excel.

 Vous pouvez ajouter des groupes et des contrôles à un onglet intégré. Par défaut, un groupe personnalisé apparaît comme le dernier groupe sur un onglet intégré, bien que vous pouvez le déplacer avant ou après tout groupe prédéfini sur l’onglet.

 Vous ne pouvez pas supprimer les groupes intégrés.

 Pour plus d’informations sur la façon de personnaliser un onglet intégré, consultez [Comment : Personnaliser un onglet intégré](../vsto/how-to-customize-a-built-in-tab.md).

###  <a name="AddGroupsToTab"></a> Ajouter des groupes à un onglet
 Groupes d’organiser logiquement les contrôles sur le ruban. Ajouter des groupes à onglets. Ajouter tous les autres contrôles au groupe.

###  <a name="AddControlsToGroups"></a> Ajouter des contrôles aux groupes
 Ajouter un ou plusieurs contrôles à un groupe. Le tableau suivant décrit chaque contrôle.

|Contrôle|Description|
|-------------|-----------------|
|**Box**|Un conteneur qui organise des contrôles dans un groupe. Vous pouvez ajouter n’importe quel contrôle à une zone à l’exception d’un séparateur, d’un groupe ou d’un onglet. Une zone peut être horizontale ou verticale.|
|**Button**|Un bouton qui démarre une action. Vous pouvez ajouter un bouton à un groupe, un groupe de boutons, une liste déroulante, une galerie, un menu ou un bouton partagé.|
|**ButtonGroup**|Un groupe qui contient un ou plusieurs boutons, boutons bascule, menus, boutons partagés et galeries. Vous pouvez ajouter un groupe de boutons à un groupe ou un menu.|
|**CheckBox**|Une zone qui est activée ou désactivée pour activer ou désactiver une option.|
|**ComboBox**|Une zone d’édition avec une zone de liste. Les utilisateurs peuvent soit taper ou sélectionner leur choix. La zone affiche la sélection actuelle. Utilisez le <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.Items%2A> propriété à ajouter et supprimer des éléments lors de l’exécution avant ou après le chargement du ruban dans l’application Office.|
|**DropDown**|Une liste d’éléments que l’utilisateur peut sélectionner. L’utilisateur ne peut pas entrer de nouvel élément dans une liste déroulante.<br /><br /> Utilisez le <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.Items%2A> propriété à ajouter des éléments à la liste. Vous pouvez ajouter et supprimer des éléments lors de l’exécution.<br /><br /> Utilisez le <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.Buttons%2A> propriété pour ajouter des boutons à la liste. Toutefois, vous ne pouvez pas ajouter et supprimer des boutons au moment de l’exécution après le chargement du ruban dans l’application Office.|
|**EditBox**|Une zone dans laquelle l’utilisateur peut taper le texte.|
|**Galerie**|Un menu qui présente un tableau ou une grille de choix visuels à partir de laquelle les utilisateurs peuvent sélectionner. Vous pouvez contrôler la disposition des sélections dans le menu. Utilisez le <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ColumnCount%2A> et <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.RowCount%2A> propriétés pour spécifier le nombre de lignes et colonnes qui afficheront les éléments et les boutons de la galerie.|
|**Label**|Texte que vous pouvez utiliser pour identifier des contrôles sur le ruban.|
|**Menu**|Une liste déroulante qui peut contenir l’un des contrôles suivants :<br /><br /> -   Button<br />-Case à cocher<br />-Galerie<br />-   Menu<br />-Bouton partagé<br />-Bouton bascule<br />-Séparateur<br /><br /> Pour ajouter un contrôle à un menu dans le Concepteur de ruban, cliquez sur la flèche bas dans le menu pour exposer l’aire de conception de menu. Vous pouvez ensuite faire glisser des contrôles de ruban à partir de la **boîte à outils** sur le menu. Pour réorganiser des contrôles, faites-les glisser aux emplacements souhaités.<br /><br /> Pour ajouter des contrôles à la <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu> après le chargement du ruban dans l’application Office, vous devez définir le <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu.Dynamic%2A> propriété **true** avant le chargement du ruban. Pour savoir comment procéder, consultez [présentation du modèle objet de ruban](../vsto/ribbon-object-model-overview.md).|
|**Separator**|Barre mince utilisée pour séparer des éléments dans une liste. Lors de l’ajout à un groupe, la barre est verticale. Lors de l’ajout à un menu, la barre est horizontale.|
|**SplitButton**|Un bouton avec un menu joint. Un bouton partagé peut contenir les contrôles suivants :<br /><br /> -   Button<br />-Case à cocher<br />-Galerie<br />-   Menu<br />-Bouton partagé<br />-Bouton bascule<br />-Séparateur<br /><br /> Comme le menu, le bouton partagé a sa propre aire de conception. Toutefois, contrairement à un menu, vous pouvez uniquement mettre à jour les éléments dans un bouton partagé avant que le ruban soit chargé dans l’application Office. Pour plus d’informations sur comment mettre à jour les éléments dans un bouton partagé, consultez [présentation du modèle objet de ruban](../vsto/ribbon-object-model-overview.md).|
|**ToggleButton**|Un bouton apparaît enfoncé ou non activé.|

##  <a name="HandleEventsSetProperties"></a> Gérer les événements et les propriétés du paramètre
 Le Concepteur de ruban vous permet de définir les propriétés de contrôle au moment du design à l’aide de la **propriétés** fenêtre. En outre, le ruban expose un modèle objet fortement typé que vous pouvez utiliser pour obtenir et définir les propriétés des contrôles de ruban lors de l’exécution.

 Vous pouvez double-cliquer sur n’importe quel contrôle dans le concepteur pour ouvrir le Gestionnaire d’événements pour l’événement du contrôle par défaut. Vous pouvez créer des gestionnaires d’événements pour tous les autres événements de contrôle à l’aide de la **propriétés** fenêtre.

 Propriétés et événements de ruban sont situées dans le <xref:Microsoft.Office.Tools.Ribbon> espace de noms. Le **ruban (Concepteur visuel)** élément ajoute automatiquement une référence à cet assembly dans le projet et insère le texte approprié **à l’aide de** ou **importations** instruction en haut du fichier de code du ruban.

 Pour plus d’informations sur la gestion des événements de ruban et la définition des propriétés de contrôles de ruban lors de l’exécution, consultez [présentation du modèle objet de ruban](../vsto/ribbon-object-model-overview.md).

##  <a name="CustomizingMicrosoftOfficeButton"></a> Personnaliser le mode Backstage
 Vous pouvez utiliser le Concepteur de ruban pour ajouter des contrôles au menu qui s’ouvre lorsque vous cliquez sur le **fichier** onglet. Ce menu est appelé mode Backstage.

 Vous ne pouvez pas placer des contrôles avant ou après les contrôles prédéfinis à l’aide du Concepteur de ruban. Un contrôle intégré est un contrôle qui figure déjà dans le mode Backstage. Si vous souhaitez positionner des contrôles avant ou après les contrôles prédéfinis, vous devez utiliser ruban XML. Pour plus d’informations sur **ruban (XML)**, consultez [ruban XML](../vsto/ribbon-xml.md). Pour plus d’informations sur la personnalisation du mode Backstage, consultez [Introduction à la Backstage Office 2010 pour les développeurs](http://go.microsoft.com/fwlink/?LinkId=182189) et [personnaliser la Backstage Office 2010 pour les développeurs](http://go.microsoft.com/fwlink/?LinkId=182188).

 [!INCLUDE[appliesto_ribbon_2010](../vsto/includes/appliesto-ribbon-2010-md.md)]

 Pour plus d’informations sur l’ajout de contrôles au mode Backstage, consultez [Comment : Ajouter des contrôles au mode Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md).

##  <a name="Accessibility"></a> Accessibilité dans le Concepteur de ruban
 Vous pouvez utiliser des raccourcis clavier pour déplacer des contrôles dans le Concepteur de ruban. Certains raccourcis clavier s’appliquent à tous les contrôles, d’autres s’appliquent uniquement aux contrôles qui ont des menus.

 Les raccourcis clavier qui s’appliquent à tous les contrôles sont affichés dans le tableau suivant.

|Action|Raccourci clavier|
|------------|-----------------------|
|Déplacer un contrôle avant le contrôle précédent dans la liste.|**CTRL**+**haut**<br /><br /> **Ctrl**+**Left**|
|Déplacer un contrôle après le contrôle suivant dans la liste.|**Ctrl**+**Down**<br /><br /> **Ctrl**+**Right**|
|Déplacer la sélection d’un contrôle à un autre dans le même groupe. Pour un panneau déroulant, déplacer entre le contrôle parent et les contrôles dans le panneau de liste déroulante.|**À distance**<br /><br /> **Vers le bas**|
|Itérer dans tous les contrôles.|**Tab**|
|Effectuer une itération dans le sens inverse via tous les contrôles.|**Maj**+**Tab**|
|Supprimez le contrôle sélectionné ou un ensemble de contrôles.|**Supprimer**|
|Copier les contrôles sélectionnés.|**Ctrl**+**C**|
|Couper les contrôles sélectionnés.|**Ctrl**+**X**|
|Coller les contrôles à partir du Presse-papiers.|**Ctrl**+**V**|
|Sélectionnez le **boîte à outils**.|**Ctrl**+**Alt**+**X**|
|Sélectionnez le composant parent.|**Échap**|

 Les raccourcis clavier qui s’appliquent uniquement au Menu Microsoft Office, <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>, et <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton> sont affichés dans le tableau suivant.

|Action|Raccourci clavier|
|------------|-----------------------|
|Sélectionnez le contrôle parent si le panneau déroulant est ouvert et qu’un contrôle est sélectionné dans le panneau de liste déroulante.|**Gauche**|
|Fermez le panneau déroulant si le panneau déroulant est ouvert et le contrôle parent est sélectionné.|**Gauche**|
|Ouvrez le panneau de liste déroulante.|**Droite**|
|Sélectionnez le premier contrôle sur le panneau déroulant si le panneau déroulant est ouvert.|**Droite**|
|Fermer un panneau déroulant.|**Échap**|

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble du ruban](../vsto/ribbon-overview.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
- [Procédure pas à pas : Créer un onglet personnalisé à l’aide du Concepteur de ruban](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Guide pratique pour Exporter un ruban à partir du Concepteur de ruban vers ruban XML](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)
- [Guide pratique pour Commencer la personnalisation du ruban](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Accéder au ruban lors de l’exécution](../vsto/accessing-the-ribbon-at-run-time.md)
