---
title: "Vue d&#39;ensemble du mod&#232;le objet de ruban | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "ruban (développement Office dans Visual Studio), modèle objet"
ms.assetid: cae24f66-e980-41ee-a915-d4c8e03efbc1
caps.latest.revision: 75
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 74
---
# Vue d&#39;ensemble du mod&#232;le objet de ruban
  [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] expose un modèle objet fortement typé que vous pouvez utiliser pour obtenir et définir les propriétés du ruban contrôle au moment de l'exécution.  Par exemple, vous pouvez remplir dynamiquement des contrôles de menu ou afficher et masquer des contrôles en fonction du contexte.  Vous pouvez également ajouter des onglets, des groupes, et des contrôles à un ruban, mais uniquement avant le chargement du ruban par l'application Office.  Pour plus d'informations, consultez [Définition de propriétés qui passent en lecture seule](#SettingReadOnlyProperties).  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
 Ce modèle objet de ruban se compose principalement de la [classe du ruban](#RibbonClass), des [événements du ruban](#RibbonEvents) et des [classes de contrôle du ruban](#RibbonControlClasses).  
  
##  <a name="RibbonClass"></a> Classe du ruban  
 Lorsque vous ajoutez un nouvel élément **Ruban \(Concepteur visuel\)** à un projet, Visual Studio ajoute une classe **Ribbon** à votre projet.  La classe **Ribbon** hérite de la classe <xref:Microsoft.Office.Tools.Ribbon.RibbonBase>.  
  
 Cette classe apparaît comme une classe partielle répartie entre le fichier de code du ruban et le fichier de code du Concepteur de ruban.  
  
##  <a name="RibbonEvents"></a> Événements du ruban  
 La classe **Ribbon** contient les trois événements suivants :  
  
|Événement|Description|  
|---------------|-----------------|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.Load>|Déclenché lorsque l'application Office charge la personnalisation du ruban.  Le gestionnaire d'événements <xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.Load> est ajouté automatiquement au fichier de code du ruban.  Utilisez ce gestionnaire d'événements pour exécuter du code personnalisé lors du chargement du ruban.|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.LoadImage>|Permet de mettre en cache des images dans la personnalisation du ruban lors du chargement du ruban.  Vous améliorerez légèrement les performances si vous écrivez du code pour mettre en cache les images du ruban dans ce gestionnaire d'événements.  Pour plus d'informations, consultez <xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.LoadImage>.|  
|<xref:Microsoft.Office.Tools.Ribbon.RibbonBase.Close>|Déclenché lorsque l'instance du ruban se ferme.|  
  
##  <a name="RibbonControlClasses"></a> Contrôles du ruban  
 L'espace de noms <xref:Microsoft.Office.Tools.Ribbon> contient un type pour chaque contrôle inclus dans le groupe **Contrôles de ruban Office** de la **Boîte à outils**.  
  
 Le tableau suivant décrit le type de chaque contrôle `Ribbon`.  Pour obtenir une description de chaque contrôle, consultez [Vue d'ensemble du ruban](../vsto/ribbon-overview.md).  
  
|Nom du contrôle|Nom de classe|  
|---------------------|-------------------|  
|**Box**|<xref:Microsoft.Office.Tools.Ribbon.RibbonBox>|  
|**Button**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton>|  
|**Buttongroup**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButtonGroup>|  
|**CheckBox**|<xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox>|  
|**ComboBox**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>|  
|**DropDown**|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>|  
|**EditBox**|<xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|  
|**Gallery**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**Regrouper**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGroup>|  
|**Étiquette**|<xref:Microsoft.Office.Tools.Ribbon.RibbonLabel>|  
|**Menu**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>|  
|**Separator**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator>|  
|**SplitButton**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|  
|**Onglet**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|  
|**ToggleButton**|<xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|  
  
 L'espace de noms <xref:Microsoft.Office.Tools.Ribbon> utilise le préfixe « Ribbon » pour ces types afin d'éviter une collision de nom avec les classes de contrôle de l'espace de noms <xref:System.Windows.Forms>.  
  
 Lorsque vous ajoutez un contrôle au Concepteur de ruban, ce dernier déclare la classe pour ce contrôle comme un champ dans son fichier de code.  
  
### Réalisation de tâches courantes à l'aide des propriétés des contrôles du ruban  
 Chaque contrôle `Ribbon` contient les propriétés que vous pouvez utiliser pour effectuer différentes tâches, telles que l'assignation d'une étiquette à un contrôle, ou masquer et afficher des contrôles.  
  
 Dans certains cas, les propriétés passent en lecture seule après le chargement du ruban ou l'ajout d'un contrôle à un menu dynamique.  Pour plus d'informations, consultez [Définition de propriétés qui passent en lecture seule](#SettingReadOnlyProperties).  
  
 Le tableau suivant décrit certaines tâches que vous pouvez effectuer à l'aide de propriétés de contrôle `Ribbon`.  
  
|Pour cette tâche :|Procédez comme suit :|  
|------------------------|---------------------------|  
|Masquer ou afficher un contrôle.|Utilisez la propriété Visible.|  
|Activer ou désactiver un contrôle.|Utilisez la propriété Enabled.|  
|Définir la taille d'un contrôle.|Utilisez la propriété ControlSize.|  
|Obtenir l'image qui s'affiche sur un contrôle.|Utilisez la propriété Image.|  
|Modifier l'étiquette d'un contrôle.|Utilisez la propriété Label.|  
|Ajouter des données définies par l'utilisateur à un contrôle.|Utilisez la propriété Tag.|  
|Obtenir les éléments d'un contrôle <xref:Microsoft.Office.Tools.Ribbon.RibbonBox>, <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>, <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> ou<br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>.|Utilisez la propriété Items.|  
|Ajouter des éléments à un contrôle <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>, <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> ou <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>.|Utilisez la propriété Items.|  
|Ajouter des contrôles à un <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>.|Utilisez la propriété Items.<br /><br /> Pour ajouter des contrôles au <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu> après le chargement du ruban dans l'application Office, vous devez définir la propriété <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu.Dynamic%2A> à **true** avant que le ruban soit chargé dans l'application Office.  Pour plus d'informations, consultez [Définition de propriétés qui passent en lecture seule](#SettingReadOnlyProperties).|  
|Obtenir l'élément sélectionné d'un <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>,<br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> ou <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>.|Utilisez la propriété SelectedItem.  Pour un <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>, utilisez la propriété <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.Text%2A>.|  
|Obtenir les groupes d'un <xref:Microsoft.Office.Tools.Ribbon.RibbonTab>.|Utilisez la propriété <xref:Microsoft.Office.Tools.Ribbon.RibbonTab.Groups%2A>.|  
|Spécifier le nombre de lignes et de colonnes apparaissant dans un <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>.|Utilisez les propriétés <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.RowCount%2A> et <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ColumnCount%2A>.|  
  
##  <a name="SettingReadOnlyProperties"></a> Définition de propriétés qui passent en lecture seule  
 Certaines propriétés peuvent être définies uniquement avant le chargement du ruban.  Elles peuvent être définies depuis trois emplacements :  
  
-   Dans la fenêtre **Propriétés** de Visual Studio.  
  
-   Dans le constructeur de la classe **Ribbon**.  
  
-   Dans la méthode CreateRibbonExtensibilityObject de la classe `ThisAddin`, `ThisWorkbook` ou `ThisDocument` de votre projet.  
  
 Les menus dynamiques comportent certaines exceptions.  Vous pouvez créer des contrôles, définissez leurs propriétés, puis les ajouter à un menu dynamique au moment de l'exécution, même après que le ruban qui contient le menu est chargé.  
  
 Les propriétés des contrôles que vous ajoutez à un menu dynamique peuvent être définies à tout moment.  
  
 Pour plus d'informations, consultez [Propriétés qui passent en lecture seule](#ReadOnlyProperties).  
  
### Définition des propriétés dans le constructeur du ruban  
 Vous pouvez définir les propriétés d'un contrôle `Ribbon` dans le constructeur de la classe **Ribbon**.  Ce code doit apparaître après l'appel à la méthode `InitializeComponent`.  L'exemple suivant ajoute un nouveau bouton à un groupe s'il est actuellement 17 heures \(heure du Pacifique\) \(UTC\-8\) au moins.  
  
 Ajoutez le code ci\-dessous.  
  
 [!code-csharp[Trin_Ribbon_ObjectModel#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_ObjectModel/CS/Ribbon1.Designer.cs#1)]
 [!code-vb[Trin_Ribbon_ObjectModel#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_ObjectModel/VB/Ribbon1.Designer.vb#1)]  
  
 Dans les projets Visual C\# que vous avez mis à niveau depuis Visual Studio 2008, le constructeur s'affiche dans le fichier code du ruban.  
  
 Dans les projets Visual Basic, ou Visual C\# que vous avez créés dans [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)], le constructeur s'affiche dans le fichier de code.  Ce fichier est nommé *YourRibbonItem*. Designer.cs ou *YourRibbonItem*. Designer.vb.  Pour afficher ce fichier dans les projets Visual Basic, vous devez au préalable cliquer sur le bouton **Afficher tous les fichiers** de l'Explorateur de solutions.  
  
### Définition des propriétés dans la méthode CreateRibbonExtensibilityObject  
 Vous pouvez définir les propriétés d'un contrôle `Ribbon` lorsque vous substituez la méthode CreateRibbonExtensibilityObject dans `ThisAddin`, `ThisWorkbook`, ou la classe `ThisDocument` de votre projet.  Pour plus d'informations sur la méthode CreateRibbonExtensibilityObject, consultez [Vue d'ensemble du ruban](../vsto/ribbon-overview.md).  
  
 L'exemple suivant définit les propriétés du ruban dans la méthode CreateRibbonExtensibilityObject de la classe `ThisWorkbook` d'un projet de classeur Excel.  
  
 Ajoutez le code ci\-dessous.  
  
 [!code-csharp[Trin_Ribbon_ObjectModel#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_ObjectModel/CS/ThisWorkbook.cs#2)]
 [!code-vb[Trin_Ribbon_ObjectModel#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_ObjectModel/VB/ThisWorkbook.vb#2)]  
  
###  <a name="ReadOnlyProperties"></a> Propriétés qui passent en lecture seule  
 Le tableau suivant décrit des propriétés qui peuvent être définies uniquement avant le chargement du ruban.  
  
> [!NOTE]  
>  Vous pouvez définir à tout moment les propriétés des contrôles sur les menus dynamiques.  Dans ce cas, le tableau suivant ne s'applique pas.  
  
|Propriété|Classe de contrôle du ruban|  
|---------------|---------------------------------|  
|**BoxStyle**|<xref:Microsoft.Office.Tools.Ribbon.RibbonBox>|  
|**ButtonType**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|  
|**ColumnCount**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**ControlId**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|  
|**DialogLauncher**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGroup>|  
|**Dynamique**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>|  
|**Global**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|  
|**Groups**|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|  
|**ImageName**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDialogLauncher><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|  
|**ItemSize**|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|  
|**MaxLength**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|  
|**Nom**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComponent>|  
|**Position**|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGroup><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonTab><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|  
|**RibbonType**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|  
|**RowCount**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**ShowItemImage**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**ShowItemLabel**|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**ShowItemSelection**|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|  
|**SizeString**|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|  
|**StartFromScratch**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|  
|**Tabulations**|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon>|  
|**Titre**|<xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator>|  
  
### Définition des propriétés des rubans qui apparaissent dans les Inspecteurs Outlook  
 Une nouvelle instance du ruban est créée chaque fois qu'un utilisateur ouvre un Inspecteur dans lequel le ruban apparaît.  Toutefois, vous pouvez définir les propriétés répertoriées dans le tableau ci\-dessus uniquement avant la première instance du ruban.  Après la première instance créée, ces propriétés passent en lecture seule car l'instance définit le fichier XML qu'Outlook pour charger le ruban.  
  
 Si votre logique conditionnelle affecte l'un de ces propriétés à une valeur différente lorsque d'autres instances du ruban sont créées, ce code n'aura aucun effet.  
  
> [!NOTE]  
>  Assurez\-vous que la propriété **Nom** est définie pour chaque contrôle que vous ajoutez à un ruban Outlook.  Si vous ajoutez un contrôle à un ruban Outlook au moment de l'exécution, vous devez définir cette propriété dans votre code.  Si vous ajoutez un contrôle à un ruban Outlook au moment du design, la propriété Name est définie automatiquement.  
  
## Événements de contrôle du ruban  
 Chaque classe de contrôle contient un ou plusieurs événements.  Le tableau suivant décrit ces événements.  
  
|Événement|Description|  
|---------------|-----------------|  
|Click|Se produit suite à un clic sur un contrôle.|  
|TextChanged|Se produit lors de la modification du texte d'une zone d'édition ou d'une zone de liste déroulante.|  
|ItemsLoading|Se produit lorsqu'Office demande la collection Items du contrôle.  Office met la collection Items en cache jusqu'à ce que votre code modifie les propriétés du contrôle ou que vous appeliez la méthode <xref:Microsoft.Office.Core.IRibbonUI.InvalidateControl%2A>.|  
|ButtonClick|Se produit suite à un clic sur un bouton dans un contrôle <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery> ou <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>.|  
|SelectionChanged|Se produit lors de la modification de la sélection d'un <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown> ou d'un <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>.|  
|DialogLauncherClick|Se produit suite à un clic sur l'icône du lanceur de boîte de dialogue dans l'angle inférieur droit d'un groupe.|  
  
 Les gestionnaires d'événements pour ces événements présentent les deux paramètres suivants.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|*sender*|<xref:System.Object> qui représente le contrôle qui a déclenché l'événement.|  
|*e*|<xref:Microsoft.Office.Tools.Ribbon.RibbonControlEventArgs> qui contient <xref:Microsoft.Office.Core.IRibbonControl>.  Utilisez ce contrôle pour accéder à des propriétés qui ne sont pas disponibles dans le modèle objet de ruban fourni par le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].|  
  
## Voir aussi  
 [Accès au ruban au moment de l'exécution](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Vue d'ensemble du ruban](../vsto/ribbon-overview.md)   
 [Comment : démarrer avec la personnalisation du ruban](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [Concepteur de ruban](../vsto/ribbon-designer.md)   
 [Procédure pas à pas : création d'un onglet personnalisé à l'aide du Concepteur de ruban](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Procédure pas à pas : mise à niveau des contrôles sur un ruban au moment de l'exécution](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)   
 [Personnalisation d'un ruban pour Outlook](../vsto/customizing-a-ribbon-for-outlook.md)   
 [Comment : personnaliser un onglet intégré](../vsto/how-to-customize-a-built-in-tab.md)   
 [Comment : ajouter des contrôles au mode Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)   
 [Comment : exporter un ruban à partir du Concepteur de ruban vers l'élément XML Ribbon](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)   
 [Comment : afficher les erreurs de l'interface utilisateur du complément](../vsto/how-to-show-add-in-user-interface-errors.md)  
  
  