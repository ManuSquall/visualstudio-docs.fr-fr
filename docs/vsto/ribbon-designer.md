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
ms.openlocfilehash: e1c2941b0c088a832540fd3380c993fe2c380b44
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72985629"
---
# <a name="ribbon-designer"></a>Concepteur de ruban
  Le concepteur de ruban est une zone de conception visuelle. Utilisez le concepteur de ruban pour ajouter des onglets, des groupes et des contrôles personnalisés au ruban d’une application Microsoft Office.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

 Pour ouvrir le concepteur de ruban, ajoutez un élément **Ruban (concepteur visuel)** à votre projet. Vous pouvez ensuite utiliser les outils de conception pour les tâches suivantes :

- [Concevoir la disposition du ruban](#DesigningRibbonLayout)

- [Gérer les événements et définir les propriétés de contrôle](#HandleEventsSetProperties)

- [Ajouter des contrôles au mode Backstage](#CustomizingMicrosoftOfficeButton)

> [!NOTE]
> Vous ne pouvez pas effectuer certaines tâches à l’aide du concepteur de ruban. Pour plus d’informations sur ces tâches et sur la façon dont vous pouvez les accomplir, consultez [vue d’ensemble du ruban](../vsto/ribbon-overview.md).

## <a name="add-a-ribbon-visual-designer-item-to-a-project"></a>Ajouter un élément Ruban (concepteur visuel) à un projet
 Pour utiliser le concepteur de ruban, ajoutez un nouvel élément **Ruban (concepteur visuel)** à votre projet. Pour plus d’informations, consultez [Comment : prendre en main la personnalisation du ruban](../vsto/how-to-get-started-customizing-the-ribbon.md).

 Quand vous ajoutez un nouvel élément **Ruban (concepteur visuel)** , Visual Studio ajoute automatiquement les fichiers suivants à votre projet :

- Un fichier de code du ruban. Ce fichier porte le nom que vous spécifiez pour l’élément **Ruban (concepteur visuel)** dans la boîte de dialogue **Ajouter un nouvel élément** . Ajoutez du code pour gérer les événements de ruban dans ce fichier.

- Fichier de code du concepteur de ruban. Ce fichier contient le code généré par le concepteur de ruban et ne doit pas être modifié directement.

- Fichier de ressources. Ce fichier contient les valeurs de propriété de chaque contrôle sur le ruban.

  Si vous disposez déjà d’un élément **Ruban (concepteur visuel)** d’un autre projet, vous pouvez le réutiliser dans votre projet actuel à l’aide de la boîte de dialogue **Ajouter un élément existant** .

## <a name="design-a-ribbon"></a><a name="DesigningRibbonLayout"></a> Concevoir un ruban
 Il existe trois façons d’ouvrir le concepteur de ruban :

- Dans **Explorateur de solutions**, double-cliquez sur le fichier de code du ruban.

- Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le fichier de code du ruban, puis cliquez sur **Concepteur de vues**.

- Dans **Explorateur de solutions**, sélectionnez le fichier de code du ruban, puis cliquez sur **Concepteur** dans le menu **affichage** .

  Le concepteur de ruban contient un onglet et un groupe par défaut. Vous pouvez supprimer l’onglet et le groupe par défaut du concepteur de ruban. Pour supprimer le groupe par défaut, cliquez avec le bouton droit sur **Group1**, puis cliquez sur **supprimer**. Pour supprimer l’onglet par défaut, cliquez avec le bouton droit sur une zone vide de l’aire de conception, puis cliquez sur l' **onglet supprimer un ruban**.

  Vous pouvez également ajouter des onglets, des groupes et des contrôles personnalisés au concepteur de ruban. Vous pouvez trouver ces contrôles dans la **boîte à outils**, dans le groupe **contrôles de ruban Office** . Il existe trois façons d’ajouter des contrôles du groupe **contrôles de ruban Office** au concepteur de ruban :

- Faites glisser un contrôle vers une zone appropriée sur le concepteur de ruban.

- Cliquez sur un contrôle, puis cliquez sur une zone appropriée dans le concepteur de ruban.

- Sélectionnez une zone appropriée dans le concepteur, puis double-cliquez sur un contrôle dans la **boîte à outils**.

### <a name="ribbon-design-workflow"></a>Flux de travail de conception de ruban
 Pour concevoir la disposition du ruban, suivez les étapes de base suivantes :

1. [Ajoutez un onglet personnalisé au ruban](#AddTabToRibbon).

2. [Ajoutez des groupes à l’onglet](#AddGroupsToTab).

3. [Ajoutez des contrôles aux groupes](#AddControlsToGroups).

   Les contrôles ne peuvent être supprimés que sur des groupes ; vous ne pouvez pas faire glisser un contrôle directement sur un onglet ou sur le ruban. Les groupes ne peuvent être supprimés que sur les onglets ; vous ne pouvez pas faire glisser un groupe directement sur un ruban.

   Organisez les contrôles en les faisant glisser vers les positions appropriées. Vous pouvez définir les propriétés d’un contrôle à l’aide de la fenêtre **Propriétés** .

   Vous ne pouvez pas faire glisser des contrôles d’un onglet à un autre sur le ruban. Si vous souhaitez déplacer un contrôle vers un autre onglet, vous devez utiliser la commande **couper** pour supprimer le contrôle d’un onglet, puis coller le contrôle sur un autre onglet. Si vous coupez et collez le contrôle, le gestionnaire d’événements cesse de fonctionner. Vous pouvez reconnecter le gestionnaire d’événements dans la fenêtre **Propriétés** . Pour plus d’informations, consultez [fenêtre Propriétés](../ide/reference/properties-window.md).

### <a name="add-custom-tabs-to-the-ribbon"></a><a name="AddTabToRibbon"></a> Ajouter des onglets personnalisés au ruban
 Il existe trois façons d’ajouter un onglet personnalisé au ruban :

- Ajoutez un onglet à partir de la **boîte à outils**.

- Cliquez avec le bouton droit sur le concepteur de ruban, puis cliquez sur l' **onglet ajouter un ruban**.

- Ouvrez l **'éditeur de collections Tab**, puis cliquez sur **Ajouter**.

   Pour ouvrir l' **éditeur de collections Tab**, dans la fenêtre **Propriétés** , sélectionnez la propriété **Tabs** , puis cliquez sur le bouton de sélection ![ASP.net Mobile designer ellipse](../sharepoint/media/mwellipsis.gif "Bouton de sélection du concepteur ASP.NET mobile").

  Après avoir ajouté un onglet, vous pouvez ajouter des groupes pour contenir des contrôles.

#### <a name="remove-custom-tabs-from-the-ribbon"></a>Supprimer les onglets personnalisés du ruban
 Il existe trois façons de supprimer un onglet personnalisé du ruban :

- Cliquez avec le bouton droit sur le concepteur, puis cliquez sur l' **onglet supprimer un ruban**.

- Dans le volet **commandes** de la fenêtre **Propriétés** , cliquez sur l' **onglet supprimer un ruban**.

- Ouvrez l' **éditeur de collections Tab**, sélectionnez l’onglet, puis cliquez sur **supprimer**.

#### <a name="change-the-position-of-a-tab-on-the-ribbon"></a>Modifier la position d’un onglet sur le ruban
 Vous pouvez modifier l’ordre des onglets personnalisés sur un ruban. Vous pouvez également positionner les onglets personnalisés avant ou après un onglet intégré sur le ruban. Pour plus d’informations, consultez [Comment : modifier la position d’un onglet sur le ruban](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md).

#### <a name="customize-built-in-tabs-on-the-ribbon"></a>Personnaliser les onglets intégrés sur le ruban
 Un onglet intégré est un onglet qui se trouve déjà sur le ruban d’une application Microsoft Office. Par exemple, l’onglet **données** est un onglet intégré dans Excel.

 Vous pouvez ajouter des groupes et des contrôles à un onglet intégré. Par défaut, un groupe personnalisé apparaît en tant que dernier groupe sur un onglet intégré, même si vous pouvez le déplacer avant ou après un groupe intégré sur l’onglet.

 Vous ne pouvez pas supprimer des groupes prédéfinis.

 Pour plus d’informations sur la personnalisation d’un onglet intégré, consultez [Comment : personnaliser un onglet intégré](../vsto/how-to-customize-a-built-in-tab.md).

### <a name="add-groups-to-a-tab"></a><a name="AddGroupsToTab"></a> Ajouter des groupes à un onglet
 Les groupes organisent logiquement les contrôles sur le ruban. Ajoutez des groupes aux onglets. Ajoutez tous les autres contrôles au groupe.

### <a name="add-controls-to-groups"></a><a name="AddControlsToGroups"></a> Ajouter des contrôles à des groupes
 Ajoutez un ou plusieurs contrôles à un groupe. Le tableau suivant décrit chaque contrôle.

|Contrôler|Description|
|-------------|-----------------|
|**Box**|Conteneur qui organise les contrôles dans un groupe. Vous pouvez ajouter n’importe quel contrôle à une zone, à l’exception d’un séparateur, d’un groupe ou d’un onglet. Une zone peut être horizontale ou verticale.|
|**Button**|Bouton qui démarre une action. Vous pouvez ajouter un bouton à un groupe, un groupe de boutons, une liste déroulante, une galerie, un menu ou un bouton partagé.|
|**ButtonGroup**|Groupe qui contient un ou plusieurs boutons, boutons bascule, menus, boutons partagés et galeries. Vous pouvez ajouter un groupe de boutons à un groupe ou à un menu.|
|**CheckBox**|Zone sélectionnée ou décochée pour activer ou désactiver une option.|
|**ComboBox**|Zone d’édition avec une zone de liste jointe. Les utilisateurs peuvent taper ou sélectionner leur choix. La zone affiche la sélection actuelle. Utilisez la <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.Items%2A> propriété pour ajouter et supprimer des éléments au moment de l’exécution avant ou après le chargement du ruban dans l’application Office.|
|**Liste déroulante**|Liste des éléments que l’utilisateur peut sélectionner. L’utilisateur ne peut pas taper un nouvel élément dans une liste déroulante.<br /><br /> Utilisez la <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.Items%2A> propriété pour ajouter des éléments à la liste. Vous pouvez ajouter et supprimer des éléments au moment de l’exécution.<br /><br /> Utilisez la <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.Buttons%2A> propriété pour ajouter des boutons à la liste. Toutefois, vous ne pouvez pas ajouter ni supprimer des boutons au moment de l’exécution après le chargement du ruban dans l’application Office.|
|**EditBox**|Zone dans laquelle l’utilisateur peut taper du texte.|
|**Office**|Menu qui présente un tableau ou une grille de choix visuels à partir de laquelle les utilisateurs peuvent sélectionner. Vous pouvez contrôler la disposition des sélections dans le menu. Utilisez les <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ColumnCount%2A> Propriétés et <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.RowCount%2A> pour spécifier le nombre de lignes et de colonnes qui afficheront les éléments et les boutons de la Galerie.|
|**Étiquette**|Texte que vous pouvez utiliser pour identifier les contrôles sur le ruban.|
|**Menu**|Liste déroulante qui peut contenir l’un des contrôles suivants :<br /><br /> -Button<br />-Case à cocher<br />-Galerie<br />-Menu<br />-Bouton partagé<br />-Bouton bascule<br />-Séparateur<br /><br /> Pour ajouter un contrôle à un menu dans le concepteur de ruban, cliquez sur la flèche vers le bas dans le menu pour exposer l’aire de conception de menu. Vous pouvez ensuite faire glisser des contrôles du ruban de la **boîte à outils** vers le menu. Pour réorganiser les contrôles, faites-les glisser vers les positions souhaitées.<br /><br /> Pour ajouter des contrôles au <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu> après le chargement du ruban dans l’application Office, vous devez affecter <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu.Dynamic%2A> à la propriété la **valeur true** avant le chargement du ruban. Pour plus d’informations sur la façon de procéder, consultez [vue d’ensemble du modèle d’objet de ruban](../vsto/ribbon-object-model-overview.md).|
|**Séparateur**|Barre fine utilisée pour séparer des éléments dans une liste. En cas d’ajout à un groupe, la barre est verticale. En cas d’ajout à un menu, la barre est horizontale.|
|**SplitButton**|Bouton avec un menu attaché. Un bouton partagé peut contenir l’un des contrôles suivants :<br /><br /> -Button<br />-Case à cocher<br />-Galerie<br />-Menu<br />-Bouton partagé<br />-Bouton bascule<br />-Séparateur<br /><br /> À l’instar du menu, le bouton partagé a sa propre aire de conception. Toutefois, contrairement à un menu, vous pouvez uniquement mettre à jour les éléments d’un bouton partagé avant le chargement du ruban dans l’application Office. Pour plus d’informations sur la façon de mettre à jour les éléments d’un bouton partagé, consultez [vue d’ensemble du modèle d’objet de ruban](../vsto/ribbon-object-model-overview.md).|
|**ToggleButton**|Bouton qui apparaît enfoncé ou non enfoncé.|

## <a name="handle-events-and-setting-properties"></a><a name="HandleEventsSetProperties"></a> Gérer les événements et les propriétés de définition
 Le concepteur de ruban vous permet de définir les propriétés du contrôle au moment du design à l’aide de la fenêtre **Propriétés** . En outre, le ruban expose un modèle objet fortement typé que vous pouvez utiliser pour obtenir et définir les propriétés des contrôles de ruban au moment de l’exécution.

 Vous pouvez double-cliquer sur n’importe quel contrôle du concepteur pour ouvrir un gestionnaire d’événements pour l’événement par défaut du contrôle. Vous pouvez créer des gestionnaires d’événements pour tous les autres événements de contrôle à l’aide de la fenêtre **Propriétés** .

 Les événements et les propriétés du ruban se trouvent dans l' <xref:Microsoft.Office.Tools.Ribbon> espace de noms. L’élément **Ruban (concepteur visuel)** ajoute automatiquement une référence à cet assembly dans le projet et insère l’instruction **using** ou **Imports** appropriée en haut du fichier de code du ruban.

 Pour plus d’informations sur la gestion des événements de ruban et la définition des propriétés des contrôles de ruban au moment de l’exécution, consultez [vue d’ensemble du modèle d’objet de ruban](../vsto/ribbon-object-model-overview.md).

## <a name="customize-backstage-view"></a><a name="CustomizingMicrosoftOfficeButton"></a> Personnaliser le mode Backstage
 Vous pouvez utiliser le concepteur de ruban pour ajouter des contrôles au menu qui s’ouvre lorsque vous cliquez sur l’onglet **fichier** . Ce menu est appelé mode Backstage.

 Vous ne pouvez pas positionner les contrôles avant ou après les contrôles prédéfinis à l’aide du concepteur de ruban. Un contrôle intégré est un contrôle qui est déjà affiché en mode Backstage. Si vous souhaitez positionner les contrôles avant ou après les contrôles prédéfinis, vous devez utiliser le ruban XML. Pour plus d’informations sur le **Ruban (XML)**, consultez [Ruban XML](../vsto/ribbon-xml.md). Pour plus d’informations sur la personnalisation du mode Backstage, consultez [Introduction au mode Backstage office 2010 pour les développeurs](/previous-versions/office/developer/office-2010/ee691833(v=office.14)) et [Personnalisation du mode backstage d’Office 2010 pour les développeurs](/previous-versions/office/developer/office-2010/ee815851(v=office.14)).

 [!INCLUDE[appliesto_ribbon_2010](../vsto/includes/appliesto-ribbon-2010-md.md)]

 Pour plus d’informations sur la façon d’ajouter des contrôles au mode Backstage, consultez [Comment : ajouter des contrôles au mode Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md).

## <a name="accessibility-in-the-ribbon-designer"></a><a name="Accessibility"></a> Accessibilité dans le concepteur de ruban
 Vous pouvez utiliser les raccourcis clavier pour déplacer des contrôles dans le concepteur de ruban. Certains raccourcis clavier s’appliquent à tous les contrôles, et certains s’appliquent uniquement aux contrôles qui ont des menus.

 Les raccourcis clavier qui s’appliquent à tous les contrôles sont présentés dans le tableau suivant.

|Action|Raccourci clavier|
|------------|-----------------------|
|Déplacer un contrôle avant le contrôle précédent dans la liste.|**CTRL** + **Vers le haut**<br /><br /> **CTRL** + À **gauche**|
|Déplacer un contrôle après le contrôle suivant dans la liste.|**CTRL** + **Vers le**<br /><br /> **CTRL** + À **droite**|
|Déplacer la sélection d’un contrôle à un autre dans le même groupe. Pour un panneau déroulant, déplacez-vous entre le contrôle parent et les contrôles dans le panneau déroulant.|**Haut**<br /><br /> **Descendre**|
|Itérer au sein de tous les contrôles.|**Onglet**|
|Itérez à l’inverse de tous les contrôles.|**MAJ** + **Onglet**|
|Supprimer le contrôle ou l’ensemble de contrôles sélectionné (e).|**Supprimer**|
|Copiez les contrôles sélectionnés.|**CTRL** + **C**|
|Coupez les contrôles sélectionnés.|**CTRL** + **X**|
|Collez les contrôles à partir du presse-papiers.|**CTRL** + **V**|
|Sélectionnez la **boîte à outils**.|**CTRL** + **ALT** + **X**|
|Sélectionnez le composant parent.|**Échap**|

 Les raccourcis clavier qui s’appliquent uniquement au menu Microsoft Office, <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu> et <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton> sont présentés dans le tableau suivant.

|Action|Raccourci clavier|
|------------|-----------------------|
|Sélectionnez le contrôle parent si le panneau déroulant est ouvert et qu’un contrôle est sélectionné dans le panneau déroulant.|**Left**|
|Fermer le panneau déroulant si le panneau déroulant est ouvert et que le contrôle parent est sélectionné.|**Left**|
|Ouvrez le panneau déroulant.|**Right**|
|Sélectionnez le premier contrôle dans le panneau déroulant si le panneau déroulant est ouvert.|**Right**|
|Fermer un panneau déroulant.|**Échap**|

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble du ruban](../vsto/ribbon-overview.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
- [Procédure pas à pas : création d’un onglet personnalisé à l’aide du concepteur de ruban](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Comment : exporter un ruban à partir du concepteur de ruban vers le ruban XML](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)
- [Comment : prendre en main la personnalisation du ruban](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Accéder au ruban au moment de l’exécution](../vsto/accessing-the-ribbon-at-run-time.md)
