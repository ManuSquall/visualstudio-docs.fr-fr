---
title: Présentation du modèle objet de ruban
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Ribbon [Office development in Visual Studio], object model
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 2be8f0ecdb4f2d7a8ea379474c4b5ec0062d2b57
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34692959"
---
# <a name="ribbon-object-model-overview"></a>Présentation du modèle objet de ruban
  Le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] expose un modèle objet fortement typé que vous pouvez utiliser pour obtenir et définir les propriétés des contrôles de ruban au moment de l’exécution. Par exemple, vous pouvez dynamiquement remplir des contrôles de menu, ou afficher et masquer les contrôles en fonction du contexte. Vous pouvez également ajouter des onglets, des groupes et des contrôles à un ruban, mais uniquement avant le chargement du ruban par l’application Office. Pour plus d’informations, consultez [définir des propriétés qui passent en lecture seule](#SettingReadOnlyProperties).  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
 Ce modèle objet de ruban se compose principalement de la [classe du ruban](#RibbonClass), [les événements de ruban](#RibbonEvents), et [les classes de contrôle de ruban](#RibbonControlClasses).  
  
##  <a name="RibbonClass"></a> Classe du ruban  
 Lorsque vous ajoutez un nouveau **ruban (Concepteur visuel)** d’élément à un projet, Visual Studio ajoute un **ruban** classe à votre projet. Le **ruban** classe hérite de la <xref:Microsoft.Office.Tools.Ribbon.RibbonBase> classe.  
  
 Cette classe s’affiche comme une classe partielle qui est partagée entre le fichier de code du ruban et le fichier de code du Concepteur de ruban.  
  
##  <a name="RibbonEvents"></a> Événements de ruban  
 Le **ruban** classe contient les trois événements suivants :  
  
|événement|Description|  
|-----------|-----------------|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.Load>|Déclenché lorsque l’application Office charge la personnalisation du ruban. Le <xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.Load> Gestionnaire d’événements est ajouté automatiquement au fichier de code du ruban. Ce gestionnaire d’événements permet d’exécuter du code personnalisé lors du chargement du ruban.|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.LoadImage>|Vous permet de cache des images dans la personnalisation du ruban lors du chargement du ruban. Vous pouvez obtenir un léger gain de performance si vous écrivez du code pour mettre en cache les images du ruban dans ce gestionnaire d’événements. Pour plus d'informations, consultez <xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.LoadImage>.|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.Close>|Déclenché lorsque l’instance du ruban se ferme.|  
  
##  <a name="RibbonControlClasses"></a> Contrôles de ruban  
 Le <xref:Microsoft.Office.Tools.Ribbon> espace de noms contient un type pour chaque contrôle que vous voyez dans le **contrôles de ruban Office** de la **boîte à outils**.  
  
 Le tableau suivant présente le type pour chaque `Ribbon` contrôle. Pour obtenir une description de chaque contrôle, consultez [vue d’ensemble du ruban](../vsto/ribbon-overview.md).  
  
|Nom du contrôle|Nom de classe|  
|------------------|----------------|  
|**Boîte de**|<xref:Microsoft.Office.Tools.Ribbon.RibbonBox>|  
|**Button**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton>|  
|**Groupe de boutons**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButtonGroup>|  
|**CheckBox**|<xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox>|  
|**ComboBox**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>|  
|**Liste déroulante**|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>|  
|**Zone d’édition**|<xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|  
|**Galerie**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**Groupe**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGroup>|  
|**Label**|<xref:Microsoft.Office.Tools.Ribbon.RibbonLabel>|  
|**Menu**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>|  
|**Separator**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator>|  
|**SplitButton**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|  
|**Tab**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|  
|**Bouton bascule**|<xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|  
  
 Le <xref:Microsoft.Office.Tools.Ribbon> espace de noms utilise le préfixe « Ribbon » pour ces types afin d’éviter une collision de nom avec les noms de classes de contrôle de la <xref:System.Windows.Forms> espace de noms.  
  
 Lorsque vous ajoutez un contrôle au Concepteur de ruban, le Concepteur de ruban déclare la classe pour ce contrôle en tant que champ dans le fichier de code du Concepteur de ruban.  
  
### <a name="common-tasks-using-the-properties-of-ribbon-controls"></a>Tâches courantes en utilisant les propriétés des contrôles de ruban  
 Chaque `Ribbon` contrôle contient les propriétés que vous pouvez utiliser pour effectuer diverses tâches, telles que l’affectation d’une étiquette à un contrôle, ou le masquage et affichage de contrôles.  
  
 Dans certains cas, les propriétés deviennent en lecture seule après le chargement du ruban ou un contrôle est ajouté à un menu dynamique. Pour plus d’informations, consultez [définir des propriétés qui passent en lecture seule](#SettingReadOnlyProperties).  
  
 Le tableau suivant décrit certaines des tâches que vous pouvez effectuer à l’aide de `Ribbon` propriétés du contrôle.  
  
|Pour cette tâche :|Procédez comme suit :|  
|--------------------|--------------|  
|Masquer ou afficher un contrôle.|Utilisez la propriété Visible.|  
|Activer ou désactiver un contrôle.|Utilisez la propriété Enabled.|  
|Définissez la taille d’un contrôle.|Utilisez la propriété ControlSize.|  
|Obtenir l’image qui apparaît sur un contrôle.|Utilisez la propriété d’Image.|  
|Modifier l’étiquette d’un contrôle.|Utilisez la propriété Label.|  
|Ajouter des données définies par l’utilisateur à un contrôle.|Utilisez la propriété Tag.|  
|Obtenir les éléments dans un <xref:Microsoft.Office.Tools.Ribbon.RibbonBox>, <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>, <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>, ou<br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton> contrôle.|Utilisez la propriété Items.|  
|Ajouter des éléments à un <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>, <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>, ou <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> contrôle.|Utilisez la propriété Items.|  
|Ajouter des contrôles à un <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>.|Utilisez la propriété Items.<br /><br /> Pour ajouter des contrôles à la <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu> après le chargement du ruban dans l’application Office, vous devez définir le <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu.Dynamic%2A> propriété **true** avant le chargement du ruban dans l’application Office. Pour plus d’informations, consultez [définir des propriétés qui passent en lecture seule](#SettingReadOnlyProperties).|  
|Obtenir l’élément sélectionné d’un <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>,<br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>, ou <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>.|Utilisez la propriété SelectedItem. Pour un <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>, utilisez le <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.Text%2A> propriété.|  
|Obtenir les groupes un <xref:Microsoft.Office.Tools.Ribbon.RibbonTab>.|Utilisez la propriété <xref:Microsoft.Office.Tools.Ribbon.RibbonTab.Groups%2A>.|  
|Spécifiez le nombre de lignes et de colonnes qui s’affichent dans un <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>.|Utilisez le <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.RowCount%2A> et <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ColumnCount%2A> propriétés.|  
  
##  <a name="SettingReadOnlyProperties"></a> Définir les propriétés qui passent en lecture seule  
 Certaines propriétés peuvent être définies uniquement avant le chargement du ruban. Il existe trois emplacements pour définir ces propriétés :  
  
-   Dans Visual Studio **propriétés** fenêtre.  
  
-   Dans le constructeur de la **ruban** classe.  
  
-   Dans le `CreateRibbonExtensibilityObject` méthode de la `ThisAddin`, `ThisWorkbook`, ou `ThisDocument` classe de votre projet.  
  
 Menus dynamiques fournissent quelques exceptions près. Vous pouvez créer de nouveaux contrôles, définir leurs propriétés et les ajouter à un menu dynamique pendant l’exécution, même après le chargement du ruban qui contient le menu.  
  
 Propriétés des contrôles que vous ajoutez à un menu dynamique peuvent être définies à tout moment.  
  
 Pour plus d’informations, consultez [propriétés en lecture seule](#ReadOnlyProperties).  
  
### <a name="set-properties-in-the-constructor-of-the-ribbon"></a>Définir les propriétés dans le constructeur du ruban  
 Vous pouvez définir les propriétés d’un `Ribbon` contrôle dans le constructeur de la **ruban** classe. Ce code doit apparaître après l’appel à la `InitializeComponent` (méthode). L’exemple suivant ajoute un nouveau bouton à un groupe si l’heure actuelle est 17:00 PST (UTC-8) ou version ultérieure.  
  
 Ajoutez le code suivant.  
  
 [!code-csharp[Trin_Ribbon_ObjectModel#1](../vsto/codesnippet/CSharp/trin_Ribbon_objectmodel_dotnet4/Ribbon1.Designer.cs#1)]
 [!code-vb[Trin_Ribbon_ObjectModel#1](../vsto/codesnippet/VisualBasic/trin_Ribbon_objectmodel_dotnet4/Ribbon1.Designer.vb#1)]  
  
 Dans les projets Visual c# mis à niveau à partir de Visual Studio 2008, le constructeur s’affiche dans le fichier de code du ruban.  
  
 Dans les projets Visual Basic, ou dans les projets Visual c# que vous avez créé dans [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)], le constructeur s’affiche dans le fichier de code du Concepteur de ruban. Ce fichier est nommé *Votreélémentruban*. Designer.cs ou *Votreélémentruban*. Designer.vb. Pour afficher ce fichier dans les projets Visual Basic, vous devez tout d’abord cliquer sur le **afficher tous les fichiers** bouton dans l’Explorateur de solutions.  
  
### <a name="set-properties-in-the-createribbonextensibilityobject-method"></a>Définir les propriétés dans la méthode CreateRibbonExtensibilityObject  
 Vous pouvez définir les propriétés d’un `Ribbon` contrôler lorsque vous remplacez le `CreateRibbonExtensibilityObject` méthode dans le `ThisAddin`, `ThisWorkbook`, ou `ThisDocument` classe de votre projet. Pour plus d’informations sur la `CreateRibbonExtensibilityObject` méthode, consultez [vue d’ensemble du ruban](../vsto/ribbon-overview.md).  
  
 L’exemple suivant définit les propriétés du ruban le `CreateRibbonExtensibilityObject` méthode de la `ThisWorkbook` classe d’un projet de classeur Excel.  
  
 Ajoutez le code suivant.  
  
 [!code-vb[Trin_Ribbon_ObjectModel#2](../vsto/codesnippet/VisualBasic/trin_Ribbon_objectmodel_dotnet4/ThisWorkbook.vb#2)]
 [!code-csharp[Trin_Ribbon_ObjectModel#2](../vsto/codesnippet/CSharp/trin_Ribbon_objectmodel_dotnet4/ThisWorkbook.cs#2)]  
  
###  <a name="ReadOnlyProperties"></a> Propriétés qui passent en lecture seule  
 Le tableau suivant présente les propriétés qui peuvent être définies uniquement avant le chargement du ruban.  
  
> [!NOTE]  
>  Vous pouvez définir les propriétés des contrôles sur les menus dynamiques à tout moment. Cette table ne s’applique pas dans ce cas.  
  
|Propriété|Classe de contrôle du ruban|  
|--------------|--------------------------|  
|**BoxStyle**|<xref:Microsoft.Office.Tools.Ribbon.RibbonBox>|  
|**ButtonType**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|  
|**ColumnCount**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**controlId**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|  
|**DialogLauncher**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGroup>|  
|**Dynamique**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>|  
|**Global**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|  
|**Groupes**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|  
|**ImageName**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDialogLauncher><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|  
|**ItemSize**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|  
|**maxLength**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|  
|**Name**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComponent>|  
|**Position**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGroup><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonTab><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|  
|**RibbonType**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|  
|**Nombre de lignes**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**ShowItemImage**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**ShowItemLabel**|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**ShowItemSelection**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**SizeString**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|  
|**StartFromScratch**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|  
|**Onglets**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|  
|**Titre**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator>|  
  
### <a name="set-properties-for-ribbons-that-appear-in-outlook-inspectors"></a>Définir les propriétés de rubans qui s’affichent dans les inspecteurs Outlook  
 Une nouvelle instance du ruban est créée chaque fois qu’un utilisateur ouvre un inspecteur dans laquelle le ruban s’affiche. Toutefois, vous pouvez définir les propriétés répertoriées dans le tableau ci-dessus uniquement avant la création de la première instance du ruban. Après la première instance est créée, ces propriétés sont en lecture seule, car la première instance définit le fichier XML utilisée par Outlook pour charger le ruban.  
  
 Si vous avez la logique conditionnelle une de ces propriétés définit une valeur différente lorsque d’autres instances du ruban sont créées, ce code n’aura aucun effet.  
  
> [!NOTE]  
>  Vérifiez que le **nom** propriété est définie pour chaque contrôle que vous ajoutez à un ruban Outlook. Si vous ajoutez un contrôle à un ruban Outlook lors de l’exécution, vous devez définir cette propriété dans votre code. Si vous ajoutez un contrôle à un ruban Outlook au moment du design, la propriété Name est définie automatiquement.  
  
## <a name="ribbon-control-events"></a>Événements de contrôle de ruban  
 Chaque classe de contrôle contient un ou plusieurs événements. Le tableau suivant décrit ces événements.  
  
|événement|Description|  
|-----------|-----------------|  
|Clic|Se produit lorsqu’un contrôle est activé.|  
|TextChanged|Se produit lorsque le texte d’une zone d’édition ou de la zone de liste déroulante est modifié.|  
|ItemsLoading|Se produit lorsque la collection d’éléments du contrôle est demandée par Office. Office met en cache la collection d’éléments jusqu'à ce que votre code modifie les propriétés du contrôle ou que vous appelez le <xref:Microsoft.Office.Core.IRibbonUI.InvalidateControl%2A> (méthode).|  
|ButtonClick|Se produit lorsqu’un bouton dans un <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> ou <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> est activé.|  
|SelectionChanged|Se produit lorsque la sélection dans un <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> ou <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> modifications.|  
|DialogLauncherClick|Se produit lorsque l’utilisateur clique sur l’icône du Lanceur de boîte de dialogue dans le coin inférieur droit d’un groupe.|  
  
 Les gestionnaires d’événements pour ces événements ont deux paramètres suivants.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|*Expéditeur*|Un <xref:System.Object> qui représente le contrôle qui a déclenché l’événement.|  
|*e*|A <xref:Microsoft.Office.Tools.Ribbon.RibbonControlEventArgs> qui contient un <xref:Microsoft.Office.Core.IRibbonControl>. Utilisez ce contrôle pour accéder à n’importe quelle propriété qui n’est pas disponible dans le modèle objet de ruban fourni par le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].|  
  
## <a name="see-also"></a>Voir aussi  
 [Accéder au ruban au moment de l’exécution](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Vue d’ensemble du ruban](../vsto/ribbon-overview.md)   
 [Comment : démarrer avec la personnalisation du ruban](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [Concepteur de ruban](../vsto/ribbon-designer.md)   
 [Procédure pas à pas : Création d’un onglet personnalisé à l’aide du Concepteur de ruban](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Procédure pas à pas : Mise à jour les contrôles sur un ruban au moment de l’exécution](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)   
 [Personnaliser un ruban pour Outlook](../vsto/customizing-a-ribbon-for-outlook.md)   
 [Comment : personnaliser un onglet intégré](../vsto/how-to-customize-a-built-in-tab.md)   
 [Comment : ajouter des contrôles pour le mode Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)   
 [Comment : exporter un ruban à partir du Concepteur de ruban vers ruban XML](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)   
 [Comment : ajouter dans l’affichage des erreurs d’interface utilisateur](../vsto/how-to-show-add-in-user-interface-errors.md)  
 