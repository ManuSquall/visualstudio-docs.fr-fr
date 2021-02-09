---
title: Vue d’ensemble du modèle objet de ruban
description: Découvrez comment le Visual Studio Tools pour Office Runtime expose un modèle objet fortement typé que vous pouvez utiliser pour obtenir et définir les propriétés des contrôles de ruban au moment de l’exécution.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Ribbon [Office development in Visual Studio], object model
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 6306b13cc40d8b93de734168fe1e6df92c256d21
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99888691"
---
# <a name="ribbon-object-model-overview"></a>Vue d’ensemble du modèle objet de ruban
  [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]Expose un modèle objet fortement typé que vous pouvez utiliser pour obtenir et définir les propriétés des contrôles de ruban au moment de l’exécution. Par exemple, vous pouvez remplir dynamiquement des contrôles de menu ou afficher et masquer des contrôles en contexte. Vous pouvez également ajouter des onglets, des groupes et des contrôles à un ruban, mais uniquement avant que le ruban soit chargé par l’application Office. Pour plus d’informations, consultez [définir les propriétés qui passent en lecture seule](#SettingReadOnlyProperties).

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

 Ce modèle d’objet de ruban se compose principalement de la [classe de ruban](#RibbonClass), des [événements de ruban](#RibbonEvents)et des classes de [contrôle de ruban](#RibbonControlClasses).

## <a name="ribbon-class"></a><a name="RibbonClass"></a> Ribbon (classe)
 Quand vous ajoutez un nouvel élément **Ruban (concepteur visuel)** à un projet, Visual Studio ajoute une classe de **ruban** à votre projet. La classe **Ribbon** hérite de la <xref:Microsoft.Office.Tools.Ribbon.RibbonBase> classe.

 Cette classe apparaît sous la forme d’une classe partielle qui est fractionnée entre le fichier de code du ruban et le fichier de code du concepteur de ruban.

## <a name="ribbon-events"></a><a name="RibbonEvents"></a> Événements de ruban
 La classe **Ribbon** contient les trois événements suivants :

|Événement|Description|
|-----------|-----------------|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.Load>|Déclenché lorsque l’application Office charge la personnalisation du ruban. Le <xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.Load> Gestionnaire d’événements est ajouté automatiquement au fichier de code du ruban. Utilisez ce gestionnaire d’événements pour exécuter du code personnalisé lors du chargement du ruban.|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.LoadImage>|Vous permet de mettre en cache des images dans la personnalisation du ruban lors du chargement du ruban. Vous pouvez obtenir un léger gain de performances si vous écrivez du code pour mettre en cache les images du ruban dans ce gestionnaire d’événements. Pour plus d’informations, consultez <xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.LoadImage>.|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.Close>|Déclenché lorsque l’instance de ruban se ferme.|

## <a name="ribbon-controls"></a><a name="RibbonControlClasses"></a> Contrôles de ruban
 L' <xref:Microsoft.Office.Tools.Ribbon> espace de noms contient un type pour chaque contrôle que vous voyez dans le groupe **contrôles de ruban Office** de la **boîte à outils**.

 Le tableau suivant indique le type de chaque `Ribbon` contrôle. Pour obtenir une description de chaque contrôle, consultez [vue d’ensemble du ruban](../vsto/ribbon-overview.md).

|Nom du contrôle|Nom de classe|
|------------------|----------------|
|**Box**|<xref:Microsoft.Office.Tools.Ribbon.RibbonBox>|
|**Button**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton>|
|**ButtonGroup**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButtonGroup>|
|**CheckBox**|<xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox>|
|**ComboBox**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>|
|**Liste déroulante**|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>|
|**EditBox**|<xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|
|**Office**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**Groupe**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGroup>|
|**Étiquette**|<xref:Microsoft.Office.Tools.Ribbon.RibbonLabel>|
|**Menu**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>|
|**Séparateur**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator>|
|**SplitButton**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|
|**Tab**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|
|**ToggleButton**|<xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|

 L' <xref:Microsoft.Office.Tools.Ribbon> espace de noms utilise le préfixe « Ribbon » pour ces types afin d’éviter une collision de noms avec les noms des classes de contrôle dans l' <xref:System.Windows.Forms> espace de noms.

 Quand vous ajoutez un contrôle au concepteur de ruban, le concepteur de ruban déclare la classe pour ce contrôle sous la forme d’un champ dans le fichier de code du concepteur de ruban.

### <a name="common-tasks-using-the-properties-of-ribbon-controls"></a>Tâches courantes à l’aide des propriétés des contrôles de ruban
 Chaque `Ribbon` contrôle contient des propriétés que vous pouvez utiliser pour effectuer diverses tâches, telles que l’assignation d’une étiquette à un contrôle, ou le masquage et l’indication de contrôles.

 Dans certains cas, les propriétés sont en lecture seule après le chargement du ruban ou après l’ajout d’un contrôle à un menu dynamique. Pour plus d’informations, consultez [définir les propriétés qui passent en lecture seule](#SettingReadOnlyProperties).

 Le tableau suivant décrit certaines des tâches que vous pouvez effectuer à l’aide des `Ribbon` Propriétés de contrôle.

|Pour cette tâche :|Procédez comme suit :|
|--------------------|--------------|
|Masquer ou afficher un contrôle.|Utilisez la propriété visible.|
|Activez ou désactivez un contrôle.|Utilisez la propriété Enabled.|
|Définit la taille d’un contrôle.|Utilisez la propriété de contrôle.|
|Obtient l’image qui apparaît sur un contrôle.|Utilisez la propriété image.|
|Modifier l’étiquette d’un contrôle.|Utilisez la propriété étiquette.|
|Ajouter des données définies par l’utilisateur à un contrôle.|Utilisez la propriété Tag.|
|Obtenir les éléments dans un <xref:Microsoft.Office.Tools.Ribbon.RibbonBox> , <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> , <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> ou<br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton> régulation.|Utilisez la propriété Items.|
|Ajoutez des éléments à <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox> un <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> contrôle, ou <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> .|Utilisez la propriété Items.|
|Ajoutez des contrôles à un <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu> .|Utilisez la propriété Items.<br /><br /> Pour ajouter des contrôles au <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu> après le chargement du ruban dans l’application Office, vous devez affecter la <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu.Dynamic%2A> **valeur true** à la propriété avant le chargement du ruban dans l’application Office. Pour plus d’informations, consultez [définir les propriétés qui passent en lecture seule](#SettingReadOnlyProperties).|
|Obtient l’élément sélectionné d’un <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox> ,<br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>, ou <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> .|Utilisez la propriété SelectedItem. Pour un <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox> , utilisez la <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.Text%2A> propriété.|
|Obtenir les groupes sur un <xref:Microsoft.Office.Tools.Ribbon.RibbonTab> .|Utilisez la propriété <xref:Microsoft.Office.Tools.Ribbon.RibbonTab.Groups%2A>.|
|Spécifiez le nombre de lignes et de colonnes qui s’affichent dans un <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> .|Utilisez les <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.RowCount%2A> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ColumnCount%2A> Propriétés et.|

## <a name="set-properties-that-become-read-only"></a><a name="SettingReadOnlyProperties"></a> Définir les propriétés qui passent en lecture seule
 Certaines propriétés ne peuvent être définies qu’avant le chargement du ruban. Il existe trois emplacements pour définir ces propriétés :

- Dans la fenêtre **Propriétés** de Visual Studio.

- Dans le constructeur de la classe **Ribbon** .

- Dans la `CreateRibbonExtensibilityObject` méthode de la `ThisAddin` `ThisWorkbook` classe, ou `ThisDocument` de votre projet.

  Les menus dynamiques fournissent quelques exceptions. Vous pouvez créer des contrôles, définir leurs propriétés, puis les ajouter à un menu dynamique au moment de l’exécution, même après le chargement du ruban qui contient le menu.

  Les propriétés des contrôles que vous ajoutez à un menu dynamique peuvent être définies à tout moment.

  Pour plus d’informations, consultez [propriétés qui passent en lecture seule](#ReadOnlyProperties).

### <a name="set-properties-in-the-constructor-of-the-ribbon"></a>Définir des propriétés dans le constructeur du ruban
 Vous pouvez définir les propriétés d’un `Ribbon` contrôle dans le constructeur de la classe **Ribbon** . Ce code doit apparaître après l’appel à la `InitializeComponent` méthode. L’exemple suivant ajoute un nouveau bouton à un groupe si l’heure actuelle est 17:00 heure du Pacifique (UTC-8) ou version ultérieure.

 Ajoutez le code ci-dessous.

 [!code-csharp[Trin_Ribbon_ObjectModel#1](../vsto/codesnippet/CSharp/trin_Ribbon_objectmodel_dotnet4/Ribbon1.Designer.cs#1)]
 [!code-vb[Trin_Ribbon_ObjectModel#1](../vsto/codesnippet/VisualBasic/trin_Ribbon_objectmodel_dotnet4/Ribbon1.Designer.vb#1)]

 Dans les projets Visual C# que vous avez mis à niveau à partir de Visual Studio 2008, le constructeur apparaît dans le fichier de code du ruban.

 Dans Visual Basic projets, ou dans les projets Visual C# que vous avez créés dans [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] , le constructeur apparaît dans le fichier de code du concepteur de ruban. Ce fichier est nommé *votreélémentruban*. Designer.cs ou *votreélémentruban*. Designer. vb. Pour afficher ce fichier dans Visual Basic projets, vous devez d’abord cliquer sur le bouton **Afficher tous les fichiers** dans Explorateur de solutions.

### <a name="set-properties-in-the-createribbonextensibilityobject-method"></a>Définir des propriétés dans la méthode CreateRibbonExtensibilityObject
 Vous pouvez définir les propriétés d’un `Ribbon` contrôle lorsque vous substituez la `CreateRibbonExtensibilityObject` méthode dans la `ThisAddin` `ThisWorkbook` classe, ou `ThisDocument` de votre projet. Pour plus d’informations sur la `CreateRibbonExtensibilityObject` méthode, consultez [vue d’ensemble du ruban](../vsto/ribbon-overview.md).

 L’exemple suivant définit les propriétés de ruban dans la `CreateRibbonExtensibilityObject` méthode de la `ThisWorkbook` classe d’un projet de classeur Excel.

 Ajoutez le code ci-dessous.

 [!code-vb[Trin_Ribbon_ObjectModel#2](../vsto/codesnippet/VisualBasic/trin_Ribbon_objectmodel_dotnet4/ThisWorkbook.vb#2)]
 [!code-csharp[Trin_Ribbon_ObjectModel#2](../vsto/codesnippet/CSharp/trin_Ribbon_objectmodel_dotnet4/ThisWorkbook.cs#2)]

### <a name="properties-that-become-read-only"></a><a name="ReadOnlyProperties"></a> Propriétés qui passent en lecture seule
 Le tableau suivant indique les propriétés qui peuvent être définies avant le chargement du ruban.

> [!NOTE]
> Vous pouvez définir les propriétés des contrôles sur des menus dynamiques à tout moment. Ce tableau ne s’applique pas dans ce cas.

|Propriété|Classe de contrôle Ribbon|
|--------------|--------------------------|
|**BoxStyle**|<xref:Microsoft.Office.Tools.Ribbon.RibbonBox>|
|**P :System.Web.UI.WebControls.ButtonFieldBase.ButtonType**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|
|**ColumnCount**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**ControlId**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|
|**DialogLauncher**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGroup>|
|**Dynamique**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>|
|**Global**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|
|**Groupes**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|
|**ImageName**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDialogLauncher><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|
|**Éléments**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|
|**MaxLength**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|
|**Nom**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComponent>|
|**Position**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGroup><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonTab><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|
|**RibbonType**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|
|**Stopp**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**ShowItemImage**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**ShowItemLabel**|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**ShowItemSelection**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|
|**SizeString**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|
|**StartFromScratch**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|
|**Tabulations**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|
|**Titre**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator>|

### <a name="set-properties-for-ribbons-that-appear-in-outlook-inspectors"></a>Définir les propriétés des rubans qui s’affichent dans les inspecteurs Outlook
 Une nouvelle instance du ruban est créée chaque fois qu’un utilisateur ouvre un inspecteur dans lequel apparaît le ruban. Toutefois, vous ne pouvez définir les propriétés indiquées dans le tableau ci-dessus qu’avant la création de la première instance du ruban. Une fois la première instance créée, ces propriétés sont en lecture seule, car la première instance définit le fichier XML qu’Outlook utilise pour charger le ruban.

 Si vous avez une logique conditionnelle qui affecte une valeur différente à l’une de ces propriétés lors de la création d’autres instances du ruban, ce code n’aura aucun effet.

> [!NOTE]
> Assurez-vous que la propriété **nom** est définie pour chaque contrôle que vous ajoutez à un ruban Outlook. Si vous ajoutez un contrôle à un ruban Outlook au moment de l’exécution, vous devez définir cette propriété dans votre code. Si vous ajoutez un contrôle à un ruban Outlook au moment du design, la propriété Name est définie automatiquement.

## <a name="ribbon-control-events"></a>Événements de contrôle du ruban
 Chaque classe de contrôle contient un ou plusieurs événements. Le tableau suivant décrit ces événements.

|Événement|Description|
|-----------|-----------------|
|Cliquez sur|Se produit lors d’un clic sur un contrôle.|
|TextChanged|Se produit lorsque le texte d’une zone d’édition ou d’une zone de liste déroulante est modifié.|
|ItemsLoading|Se produit lorsque la collection d’éléments du contrôle est demandée par Office. Office met en cache la collection d’éléments jusqu’à ce que votre code modifie les propriétés du contrôle ou que vous appeliez la <xref:Microsoft.Office.Core.IRibbonUI.InvalidateControl%2A> méthode.|
|ButtonClick|Se produit suite à un clic sur un bouton d’un <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> ou <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> .|
|SelectionChanged|Se produit lorsque la sélection dans un <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> ou <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> change.|
|DialogLauncherClick|Se produit lorsque l’utilisateur clique sur l’icône du lanceur de boîte de dialogue dans le coin inférieur droit d’un groupe.|

 Les gestionnaires d’événements pour ces événements ont les deux paramètres suivants.

|Paramètre|Description|
|---------------|-----------------|
|*expéditeur*|<xref:System.Object> qui représente le contrôle qui a déclenché l'événement.|
|*Envoyer*|<xref:Microsoft.Office.Tools.Ribbon.RibbonControlEventArgs> qui contient <xref:Microsoft.Office.Core.IRibbonControl>. Utilisez ce contrôle pour accéder à toute propriété qui n’est pas disponible dans le modèle d’objet de ruban fourni par le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] .|

## <a name="see-also"></a>Voir aussi
- [Accéder au ruban au moment de l’exécution](../vsto/accessing-the-ribbon-at-run-time.md)
- [Vue d’ensemble du ruban](../vsto/ribbon-overview.md)
- [Comment : prendre en main la personnalisation du ruban](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Concepteur de ruban](../vsto/ribbon-designer.md)
- [Procédure pas à pas : création d’un onglet personnalisé à l’aide du concepteur de ruban](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Procédure pas à pas : mettre à jour les contrôles sur un ruban au moment de l’exécution](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)
- [Personnaliser un ruban pour Outlook](../vsto/customizing-a-ribbon-for-outlook.md)
- [Comment : personnaliser un onglet intégré](../vsto/how-to-customize-a-built-in-tab.md)
- [Comment : ajouter des contrôles au mode Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)
- [Comment : exporter un ruban à partir du concepteur de ruban vers le ruban XML](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)
- [Comment : afficher les erreurs d’interface utilisateur du complément](../vsto/how-to-show-add-in-user-interface-errors.md)
