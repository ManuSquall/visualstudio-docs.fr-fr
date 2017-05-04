---
title: "Limitations des contr&#244;les Windows Forms dans les documents Office | Microsoft Docs"
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
  - "contrôles ActiveX (développement Office dans Visual Studio)"
  - "contrôles (développement Office dans Visual Studio), contrôles Windows Forms"
  - "documents Office (développement Office dans Visual Studio), contrôles Windows Forms"
  - "boîte à outils (développement Office dans Visual Studio), contrôles non pris en charge"
  - "contrôles utilisateur (développement Office dans Visual Studio), regrouper les contrôles"
  - "contrôles Windows Forms (développement Office dans Visual Studio), ActiveX hérité (legacy)"
  - "contrôles Windows Forms (développement Office dans Visual Studio), limitations"
  - "contrôles Windows Forms (développement Office dans Visual Studio), boîte à outils"
  - "contrôles Windows Forms (développement Office dans Visual Studio), propriétés et méthodes non prises en charge"
ms.assetid: 95ff473e-4952-4977-bc88-c77289c9fb0b
caps.latest.revision: 56
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 52
---
# Limitations des contr&#244;les Windows Forms dans les documents Office
  Il existe des différences entre les contrôles Windows Forms qui sont ajoutés aux documents Microsoft Office Word ou aux classeurs Microsoft Office Excel et les contrôles Windows Forms qui sont ajoutés à Windows Forms.  Par exemple, lorsque vous ajoutez un contrôle <xref:Microsoft.Office.Tools.Word.Controls.Button> Windows Forms à un document Word, les propriétés telles que <xref:Microsoft.Office.Tools.Word.Controls.Button.Dock%2A>, <xref:Microsoft.Office.Tools.Word.Controls.Button.Anchor%2A> et <xref:Microsoft.Office.Tools.Word.Controls.Button.TabIndex%2A> ne se comportent pas comme prévu.  
  
 Ces différences sont pour beaucoup dues à la façon dont les contrôles Windows Forms sont hébergés sur les documents.  Lorsqu'un contrôle Windows Forms est ajouté à un document, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] incorpore un contrôle ActiveX qui héberge le contrôle Windows Forms dans le document.  Le contrôle Windows Forms n'est pas incorporé directement dans le document.  
  
 [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]  
  
## Limitations des méthodes et des propriétés des contrôles Windows Forms  
 Il existe de nombreuses méthodes et propriétés de contrôles Windows Forms qui ne fonctionnent pas de la même façon sur un document que sur un Windows Form ; il est donc recommandé de ne pas les utiliser.  Par exemple, la définition de propriétés telles que `Dock` et `Anchor` affecte uniquement la position du contrôle Windows Forms par rapport au contrôle ActiveX conteneur, plutôt que le document.  Voici la liste des méthodes et propriétés de contrôles Windows Forms non prises en charge pour Word et Excel :  
  
-   Méthodes et propriétés de contrôles Excel non prises en charge :  
  
    -   `Anchor`  
  
    -   `Dock`  
  
    -   `Location`  
  
    -   `TabIndex`  
  
    -   `TabStop`  
  
    -   `TopLevelControl`  
  
-   Méthodes et propriétés de contrôles Word non prises en charge :  
  
    -   `Hide`  
  
    -   `Show`  
  
    -   `Anchor`  
  
    -   `Dock`  
  
    -   `Location`  
  
    -   `TabIndex`  
  
    -   `TabStop`  
  
    -   `TopLevelControl`  
  
    -   `Visible`  
  
 Vous ne pouvez pas non plus définir la propriété `Left` ou `Top` des contrôles Windows Forms qui sont alignés sur le texte dans un document Word.  Les contrôles Windows Forms sont ajoutés et alignés sur le texte dans les cas suivants :  
  
-   Vous ajoutez par programmation un contrôle à un document Word et utilisez une méthode qui spécifie une plage pour l'emplacement.  
  
-   Vous ajoutez un contrôle Windows Forms à un document Word au moment du design.  Vous pouvez modifier cela en apportant une modification au contrôle dans le concepteur.  
  
## Différences dans les contrôles Windows Forms de documents Office  
 Les contrôles Windows Forms adoptent généralement le même comportement sur un document Office que sur un Windows Form, mais il existe certaines différences.  Le tableau suivant décrit les différences qui existent pour les contrôles Windows Forms dans des documents Office :  
  
|Fonctionnalité|Différence|  
|--------------------|----------------|  
|Ordre des contrôles|Vous ne pouvez pas vous déplacer par tabulation entre les contrôles placés dans une feuille de calcul Excel ou un document Word.|  
|Regroupement de contrôles|Vous ne pouvez pas utiliser un contrôle <xref:System.Windows.Forms.GroupBox> pour contenir d'autres contrôles sur un document Office.  Lorsque vous ajoutez plusieurs cases d'option directement au document, les cases d'option ne s'excluent pas mutuellement.  Vous pouvez écrire du code afin que les cases d'option s'excluent mutuellement ; toutefois, l'approche par défaut est d'ajouter les cases d'option à un contrôle utilisateur, puis d'ajouter le contrôle utilisateur au document.  Pour plus d'informations, consultez les exemples de contrôles Word et Excel dans [Exemples et procédures pas à pas relatifs au développement Office](../vsto/office-development-samples-and-walkthroughs.md).|  
|Type de contrôle|Les contrôles Windows Forms utilisés dans les documents sont inclus dans un wrapper dans une classe fournie par [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] qui donne aux contrôles des fonctionnalités supplémentaires spécifiques à la feuille de calcul Excel ou au document Word.  Par exemple, si vous avez un contrôle `Button` sur une feuille de calcul Excel, veillez à spécifier le type <xref:Microsoft.Office.Tools.Excel.Controls.Button> plutôt que <xref:System.Windows.Forms.Button> lorsque vous référencez ou caster l'objet.|  
|Position et taille du contrôle|La taille et la position du contrôle sont déterminées par les propriétés qui font partie du contrôle ActiveX conteneur.  Les propriétés du contrôle ActiveX prennent des valeurs différentes de celles des propriétés équivalentes d'un contrôle Windows Forms.  Lorsque vous définissez les propriétés `Top`, `Left`, `Height` ou `Width` d'un contrôle, celles\-ci sont mesurées en points plutôt qu'en pixels.|  
|Position des contrôles sur les documents Word|Si vous ajoutez des contrôles à une présentation basée sur un flux, n'oubliez pas que leur position varie en fonction des modifications apportées au contenu.  Vous ne pouvez pas ancrer un contrôle à un paragraphe lorsque vous l'ajoutez en le faisant glisser à partir de la **Boîte à outils** car il est aligné sur le texte du document Word.  Si vous utilisez une autre méthode pour ajouter le contrôle, en double\-cliquant par exemple sur le contrôle, le contrôle est inséré en fonction de l'option Word que vous avez définie pour insérer des images.<br /><br /> Vous ne pouvez pas définir la propriété `Left` ou `Top` d'un contrôle Word qui est inline avec le texte.<br /><br /> Vous ne pouvez pas placer de contrôles dans un en\-tête ou pied de page, ou dans un sous\-document.|  
|Événements de contrôle|Lorsque le contrôle est sélectionné, il déclenche des événements dans l'ordre suivant :<br /><br /> 1.  `Enter`<br />2.  `GotFocus`<br /><br /> Lorsque le contrôle est désélectionné, il déclenche des événements dans l'ordre suivant :<br /><br /> 1.  `Leave`<br />2.  `Validating`<br />3.  `Validated`<br />4.  `LostFocus`|  
|Mise à l'échelle de contrôle|Lorsque vous attribuez une valeur différente de 100 % au paramètre de zoom d'un document, les contrôles sont désactivés même si leur taille semble s'ajuster en fonction du document.  Par exemple, si vous cliquez sur un bouton lorsque le zoom de votre document est de 130 %, un message indique que le contrôle est désactivé jusqu'à ce que le zoom ait la valeur 100 %.  Les contrôles fonctionnent correctement lorsque vous attribuez au zoom la valeur 100 %.|  
|Valeurs de propriété de contrôle|Bien qu'une valeur entière soit affectée aux propriétés de contrôles sur un Windows Form, une valeur unique leur est affectée pour les contrôles sur un document Word.  Dans Excel, une valeur double est affectée aux valeurs de propriété de contrôle.  Si les propriétés `Height` et `Width` d'un contrôle sur une feuille de calcul dépassent la taille de la feuille de calcul ou de l'écran, la valeur est tronquée.|  
|Redimensionnement des contrôles|Si vous redimensionnez un contrôle sur le document à l'aide de l'une des huit poignées de redimensionnement, les nouvelles dimensions du contrôle ne sont pas répercutées dans la fenêtre **Propriétés** tant que le contrôle n'est pas de nouveau activé.|  
|Comportement des contrôles|Les contrôles sur une feuille de calcul Excel peuvent se comporter de façon imprévisible lorsque la fenêtre de la feuille de calcul est fractionnée.  Par exemple, l'accès à une <xref:Microsoft.Office.Tools.Excel.Controls.TextBox> sur la feuille de calcul peut être disponible uniquement dans l'une des fenêtres.|  
|Attribution des noms des contrôles|Vous ne pouvez pas utiliser de mots réservés pour nommer des contrôles.  Par exemple, si vous ajoutez un <xref:Microsoft.Office.Tools.Excel.Controls.Button> à une feuille de calcul et remplacez son nom par **Système**, des erreurs se produisent lorsque vous générez le projet.|  
|Ajout de contrôles par programmation|N'utilisez pas le constructeur du contrôle pour ajouter un contrôle à votre document au moment de l'exécution.  Utilisez plutôt les méthodes d'assistance fournies par [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].  Par exemple, utilisez la méthode <xref:Microsoft.Office.Tools.Excel.ControlExtensions.AddButton%2A> pour ajouter un bouton à une feuille de calcul.  Si vous souhaitez ajouter un contrôle qui n'est pas pris en charge par ces méthodes d'assistance, vous pouvez utiliser la méthode AddControl.  Pour plus d’informations, consultez [Ajout de contrôles à des documents Office au moment de l'exécution](../vsto/adding-controls-to-office-documents-at-run-time.md).|  
|Copie des contrôles|Si vous copiez un contrôle Windows Forms et que vous le collez dans un document au moment de l'exécution, un contrôle ActiveX conteneur vide est collé dans le document.  Le contrôle Windows Forms n'apparaît pas au nouvel emplacement et le code\-behind du contrôle d'origine n'est pas copié vers le contrôle ActiveX conteneur.|  
  
## Limitations dans les projets au niveau du document  
 Certaines limitations relatives à l'utilisation de contrôles Windows Forms sur les documents sont spécifiques aux projets au niveau du document.  
  
### Prise en charge des contrôles au moment du design  
 Certains contrôles Windows Forms sont supprimés de la **Boîte à outils** lorsqu'une feuille de calcul Excel ou un document Word est ouvert dans le concepteur Visual Studio.  Ceci est dû à des limitations techniques ou au fait que des fonctionnalités sont déjà disponibles dans Word ou Excel.  Les projets Excel et Word prennent en charge tous les contrôles Windows Forms et d'autres composants qui apparaissent dans la **Boîte à outils** lorsque le document est actif et il est possible d'ajouter des contrôles tiers aux feuilles de calcul et aux documents.  
  
> [!NOTE]  
>  Tous les contrôles sont supprimés de la **Boîte à outils** lorsqu'un document est protégé.  Pour plus d'informations sur la protection de document, consultez [Protection des documents dans les solutions au niveau du document](../vsto/document-protection-in-document-level-solutions.md).  
  
> [!NOTE]  
>  Les contrôles tiers doivent avoir l'attribut <xref:System.Runtime.InteropServices.ComVisibleAttribute> défini à **true** pour être utilisés dans une solution Office.  
  
 Les contrôles et les composants suivants ne sont pas disponibles dans la **Boîte à outils** :  
  
-   <xref:System.Windows.Forms.BindingNavigator>  
  
-   <xref:System.Windows.Forms.ContextMenuStrip>  
  
-   <xref:System.Windows.Forms.DataGrid>  
  
-   <xref:System.DirectoryServices.DirectoryEntry>  
  
-   <xref:System.DirectoryServices.DirectorySearcher>  
  
-   <xref:System.Windows.Forms.ErrorProvider>  
  
-   <xref:System.Diagnostics.EventLog>  
  
-   <xref:System.IO.FileSystemWatcher>  
  
-   <xref:System.Windows.Forms.FlowLayoutPanel>  
  
-   <xref:System.Windows.Forms.GroupBox>  
  
-   <xref:System.Windows.Forms.MainMenu>  
  
-   <xref:System.Windows.Forms.MenuStrip>  
  
-   <xref:System.Messaging.MessageQueue>  
  
-   <xref:System.Windows.Forms.NotifyIcon>  
  
-   <xref:System.Windows.Forms.PageSetupDialog>  
  
-   <xref:System.Windows.Forms.Panel>  
  
-   <xref:System.Diagnostics.PerformanceCounter>  
  
-   <xref:System.Windows.Forms.PrintDialog>  
  
-   <xref:System.Drawing.Printing.PrintDocument>  
  
-   <xref:System.Windows.Forms.PrintPreviewControl>  
  
-   <xref:System.Diagnostics.Process>  
  
-   <xref:System.Windows.Forms.RichTextBox>  
  
-   <xref:System.IO.Ports.SerialPort>  
  
-   <xref:System.ServiceProcess.ServiceController>  
  
-   <xref:System.Windows.Forms.SplitContainer>  
  
-   <xref:System.Windows.Forms.Splitter>  
  
-   <xref:System.Windows.Forms.StatusBar>  
  
-   <xref:System.Windows.Forms.StatusStrip>  
  
-   <xref:System.Windows.Forms.TabControl>  
  
-   <xref:System.Windows.Forms.TableLayoutPanel>  
  
-   <xref:System.Timers.Timer>  
  
-   <xref:System.Windows.Forms.Timer>  
  
-   <xref:System.Windows.Forms.ToolBar>  
  
-   <xref:System.Windows.Forms.ToolStrip>  
  
-   <xref:System.Windows.Forms.ToolStripContainer>  
  
-   <xref:System.Windows.Forms.ToolStripDropDown>  
  
-   <xref:System.Windows.Forms.ToolStripDropDownMenu>  
  
-   <xref:System.Windows.Forms.ToolStripPanel>  
  
### Prise en charge pour les contrôles ActiveX hérités \(legacy\)  
 Si vous créez un projet Office au niveau du document qui utilise un document Word ou un classeur Excel existant contenant des contrôles ActiveX, les fonctionnalités des contrôles ActiveX ne seront pas perdues ; toutefois, l'ajout de nouveaux contrôles ActiveX à vos documents dans Visual Studio n'est pas pris en charge.  Par exemple, si votre document Word inclut un bouton de la boîte à outils **Contrôles** qui exécute une macro VBA, il continuera à exécuter la macro après l'utilisation du document dans un projet Office.  Toutefois, il est recommandé de supprimer les contrôles ActiveX et les macros VBA, et de les remplacer par des contrôles Windows Forms et du code managé.  
  
## Voir aussi  
 [Contrôles sur des documents Office](../vsto/controls-on-office-documents.md)   
 [Vue d'ensemble des contrôles Windows Forms dans les documents Office](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Ajout de contrôles à des documents Office au moment de l'exécution](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Comment : ajouter des contrôles Windows Forms à des documents Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)  
  
  