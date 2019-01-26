---
title: Limitations des contrôles Windows Forms sur des documents Office
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office documents [Office development in Visual Studio, Windows Forms controls
- Windows Forms controls [Office development in Visual Studio], ActiveX legacy
- ActiveX controls [Office development in Visual Studio]
- Windows Forms controls [Office development in Visual Studio], limitations
- controls [Office development in Visual Studio], Windows Forms controls
- Windows Forms controls [Office development in Visual Studio], unsupported properties and methods
- Toolbox [Office development in Visual Studio], unsupported controls
- user controls [Office development in Visual Studio], grouping controls
- Windows Forms controls [Office development in Visual Studio], Toolbox
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 610ee5e18054b6da35a3098b851d1585c70b6bc3
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54863550"
---
# <a name="limitations-of-windows-forms-controls-on-office-documents"></a>Limitations des contrôles Windows Forms sur des documents Office

Il existe certaines différences entre les contrôles Windows Forms qui sont ajoutés aux documents Microsoft Office Word ou des feuilles de calcul Microsoft Office Excel et les contrôles Windows Forms qui sont ajoutés à Windows Forms. Par exemple, lorsque vous ajoutez un <xref:Microsoft.Office.Tools.Word.Controls.Button> de contrôle à un document, les propriétés telles que <xref:System.Windows.Forms.Control.Dock>, <xref:System.Windows.Forms.Control.Anchor>, et <xref:System.Windows.Forms.Control.TabIndex> ne se comportent pas comme prévu.

La plupart de ces différences sont dues à la façon que les contrôles sont hébergés les formulaires Windows sur des documents. Lorsqu’un contrôle Windows Forms est ajouté à un document, le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] incorpore un contrôle ActiveX qui héberge le contrôle Windows Forms dans le document. Le contrôle Windows Forms n’est pas incorporé directement dans le document.

[!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

## <a name="limitations-of-methods-and-properties-of-windows-forms-controls"></a>Limitations des méthodes et propriétés des contrôles Windows Forms

Il existe un nombre de méthodes et propriétés de contrôles Windows Forms qui ne fonctionnent pas de la même façon sur un document comme ils le feraient sur un formulaire Windows et, par conséquent, il est recommandé qu’elles ne pas être utilisées. Par exemple, définissant les propriétés telles que <xref:System.Windows.Forms.Control.Dock> et <xref:System.Windows.Forms.Control.Anchor> affecte uniquement la position du contrôle en ce qui concerne le contrôle ActiveX de conteneur, plutôt que le document. Voici une liste de méthodes non prises en charge et les propriétés des contrôles Windows Forms pour Word et Excel :

- Non pris en charge des propriétés de contrôles Excel :

    - <xref:System.Windows.Forms.Control.Anchor>
    - <xref:System.Windows.Forms.Control.Dock>
    - <xref:System.Windows.Forms.Control.Location>
    - <xref:System.Windows.Forms.Control.TabIndex>
    - <xref:System.Windows.Forms.Control.TabStop>
    - <xref:System.Windows.Forms.Control.TopLevelControl>

- Non pris en charge des méthodes et propriétés de contrôles Word :

    - <xref:System.Windows.Forms.Control.Hide%2A>
    - <xref:System.Windows.Forms.Control.Show%2A>
    - <xref:System.Windows.Forms.Control.Anchor>
    - <xref:System.Windows.Forms.Control.Dock>
    - <xref:System.Windows.Forms.Control.Location>
    - <xref:System.Windows.Forms.Control.TabIndex>
    - <xref:System.Windows.Forms.Control.TabStop>
    - <xref:System.Windows.Forms.Control.TopLevelControl>
    - <xref:System.Windows.Forms.Control.Visible>

Vous ne pouvez pas définir le <xref:System.Windows.Forms.Control.Left> ou <xref:System.Windows.Forms.Control.Top> propriété des contrôles Windows Forms qui sont alignés avec le texte dans un document Word. Contrôles Windows Forms sont ajoutés alignés avec le texte dans les cas suivants :

- Par programmation, vous ajoutez un contrôle à un document Word et que vous utilisez une méthode qui spécifie une plage pour l’emplacement.

- Vous ajoutez un contrôle Windows Forms à un document Word au moment du design. Vous pouvez le modifier en modifiant le contrôle dans le concepteur.

## <a name="differences-in-windows-forms-controls-on-office-documents"></a>Différences dans les contrôles Windows Forms sur des documents Office

Contrôles Windows Forms ont généralement le même comportement sur un document Office comme sur un formulaire Windows, mais il existe certaines différences. Le tableau suivant décrit les différences qui existent pour les contrôles Windows Forms sur des documents Office.

|Fonctionnalité|Différence|
|-------------------|----------------|
|Contrôle l’ordre de tabulation|Vous ne pouvez pas l’onglet via les contrôles placés sur une feuille de calcul Excel ou un document Word.|
|Regroupement de contrôle|Vous ne pouvez pas utiliser un <xref:System.Windows.Forms.GroupBox> contrôle pour contenir d’autres contrôles sur un document Office. Lorsque vous ajoutez plusieurs boutons radio directement au document, les boutons radio ne sont pas mutuellement exclusives. Vous pouvez écrire du code pour que les boutons de case d’option mutuellement ; Toutefois, la meilleure approche consiste à ajouter des boutons radio à un contrôle utilisateur, puis ajouter le contrôle utilisateur au document. Pour plus d’informations, consultez les exemples de contrôles Word et Excel dans [exemples de développement Office et des procédures pas à pas](../vsto/office-development-samples-and-walkthroughs.md).|
|Type de contrôle|Contrôles Windows Forms utilisés sur des documents sont encapsulées dans une classe fournie par le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] qui permet des contrôles des fonctionnalités supplémentaires spécifiques à la feuille de calcul Excel ou un document Word. Par exemple, si vous avez un **bouton** control sur une feuille de calcul Excel, veillez à spécifier le type en tant que <xref:Microsoft.Office.Tools.Excel.Controls.Button> plutôt que <xref:System.Windows.Forms.Button> lorsque vous référencez ou cast de l’objet.|
|Position du contrôle et la taille|La taille et la position du contrôle est déterminée par les propriétés qui font partie du conteneur de contrôle ActiveX. Les propriétés du contrôle ActiveX prennent des valeurs différentes de celles des propriétés équivalentes d’un contrôle Windows Forms. Lorsque vous définissez la `Top`, `Left`, `Height`, ou `Width` propriétés d’un contrôle, elle est mesurée en points, plutôt que de pixels.|
|Position du contrôle dans les documents Word|Si vous ajoutez des contrôles à une disposition basée sur les flux, n’oubliez pas que les contrôles de flux avec le contenu en tant que les modifications de contenu. Vous ne pouvez pas ancrer un contrôle à un paragraphe lorsque vous faites glisser à partir du **boîte à outils** , car le contrôle est ajouté au document Word alignés avec le texte. Si vous utilisez une autre méthode pour ajouter le contrôle, par exemple en double-cliquant sur le contrôle, le contrôle est inséré en fonction de l’option de Word que vous avez défini pour l’insertion d’images.<br /><br /> Vous ne pouvez pas définir le `Left` ou `Top` propriété d’un contrôle qui est inclus avec le texte.<br /><br /> Vous ne pouvez pas placer des contrôles dans un en-tête ou un pied de page, ou dans un sous-document.|
|Événements de contrôle|Lorsque le contrôle est sélectionné, il déclenche des événements dans l’ordre suivant :<br /><br /> 1.  `Enter`<br />2.  `GotFocus`<br /><br /> Lorsque le contrôle est désélectionné, il déclenche des événements dans l’ordre suivant :<br /><br /> 1.  `Leave`<br />2.  `Validating`<br />3.  `Validated`<br />4.  `LostFocus`|
|Mise à l’échelle du contrôle|Lorsque vous modifiez le paramètre du zoom d’un document sur n’importe quelle autre que 100 %, les contrôles sont désactivés, même si elles apparaissent à l’échelle avec le document. Par exemple, si vous cliquez sur un bouton lorsque votre document est de 130 % zoom, il affiche un message que le contrôle a été désactivé jusqu'à ce que le zoom est défini sur 100 %. Les contrôles ne fonctionnent pas correctement lorsque vous modifiez le zoom à 100 %.|
|Valeurs de propriété de contrôle|Bien que les propriétés des contrôles sur un formulaire Windows sont définies sur une valeur entière, elles sont définies pour un seul pour les contrôles sur un document Word. Dans Excel, les valeurs de propriété des contrôles sont définies en double. Si le `Height` et `Width` propriété d’un contrôle sur une feuille de calcul dépasse la taille de la feuille de calcul ou d’un écran, la valeur est tronquée.|
|Redimensionnement du contrôle|Si vous redimensionnez un contrôle sur le document à l’aide d’une des huit poignées de redimensionnement, les nouvelles dimensions du contrôle ne sont pas répercutées dans le **propriétés** fenêtre jusqu'à ce que le contrôle est de nouveau activé.|
|Contrôler le comportement|Contrôles sur une feuille de calcul Excel peuvent se comporter de façon imprévisible lorsque la fenêtre de feuille de calcul est fractionnée. Par exemple, l’accès à un <xref:Microsoft.Office.Tools.Excel.Controls.TextBox> sur la feuille de calcul peut être disponible uniquement dans une des fenêtres.|
|Contrôle d’affectation de noms|Vous ne pouvez pas utiliser les mots réservés pour nommer des contrôles. Par exemple, si vous ajoutez un <xref:Microsoft.Office.Tools.Excel.Controls.Button> à une feuille de calcul et remplacez le nom par **système**, erreurs se produisent lorsque vous générez le projet.|
|Ajout de contrôles par programmation|N’utilisez pas le constructeur du contrôle pour ajouter un contrôle à votre document au moment de l’exécution. Au lieu de cela, utilisez les méthodes d’assistance fournies par le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]. Par exemple, utilisez le <xref:Microsoft.Office.Tools.Excel.ControlExtensions.AddButton%2A> pour ajouter un bouton à une feuille de calcul. Si vous souhaitez ajouter un contrôle qui n’est pas pris en charge par ces méthodes d’assistance, vous pouvez utiliser le `AddControl` (méthode). Pour plus d’informations, consultez [ajouter des contrôles aux documents Office au moment de l’exécution](../vsto/adding-controls-to-office-documents-at-run-time.md).|
|Copie les contrôles|Si vous copiez un contrôle Windows Forms et collez dans un document lors de l’exécution, un contrôle ActiveX conteneur vide est collé dans le document. Le contrôle Windows Forms n’apparaît pas dans le nouvel emplacement et code-behind du contrôle d’origine n’est pas copié dans le conteneur de contrôle ActiveX.|

## <a name="limitations-in-document-level-projects"></a>Limitations dans les projets au niveau du document

Certaines limitations de l’utilisation de contrôles Windows Forms sur les documents sont uniques pour les projets au niveau du document.

### <a name="control-support-at-design-time"></a>Prise en charge du contrôle au moment du design

Certains contrôles Windows Forms sont supprimés de la **boîte à outils** lorsqu’une feuille de calcul Excel ou un document Word est ouvert dans le concepteur Visual Studio. Il s’agit en raison des limitations techniques ou parce que les fonctionnalités sont déjà disponibles dans Word ou Excel. Projets Excel et Word prennent en charge tous les contrôles Windows Forms et d’autres composants qui s’affichent dans le **boîte à outils** lorsque le document a le focus, et vous pouvez également ajouter des contrôles tiers à un document ou une feuille de calcul.

> [!NOTE]
> Tous les contrôles sont supprimés de la **boîte à outils** quand un document est protégé. Pour plus d’informations sur la protection de document, consultez [protection dans les solutions au niveau du document dans les documents](../vsto/document-protection-in-document-level-solutions.md).

> [!NOTE]
> Les contrôles tiers doivent avoir le <xref:System.Runtime.InteropServices.ComVisibleAttribute> attribut la valeur **true** pour pouvoir être utilisé dans une solution Office.

Les contrôles et les composants suivants ne sont pas disponibles dans le **boîte à outils**:

- <xref:System.Windows.Forms.BindingNavigator>

- <xref:System.Windows.Forms.ContextMenuStrip>

- <xref:System.Windows.Forms.DataGrid>

- <xref:System.DirectoryServices.DirectoryEntry>

- <xref:System.DirectoryServices.DirectorySearcher>

- <xref:System.Windows.Forms.ErrorProvider>

- <xref:System.Diagnostics.EventLog>

- <xref:System.IO.FileSystemWatcher>

- <xref:System.Windows.Forms.FlowLayoutPanel>

- <xref:System.Windows.Forms.GroupBox>

- <xref:System.Windows.Forms.MainMenu>

- <xref:System.Windows.Forms.MenuStrip>

- <xref:System.Messaging.MessageQueue>

- <xref:System.Windows.Forms.NotifyIcon>

- <xref:System.Windows.Forms.PageSetupDialog>

- <xref:System.Windows.Forms.Panel>

- <xref:System.Diagnostics.PerformanceCounter>

- <xref:System.Windows.Forms.PrintDialog>

- <xref:System.Drawing.Printing.PrintDocument>

- <xref:System.Windows.Forms.PrintPreviewControl>

- <xref:System.Diagnostics.Process>

- <xref:System.Windows.Forms.RichTextBox>

- <xref:System.IO.Ports.SerialPort>

- <xref:System.ServiceProcess.ServiceController>

- <xref:System.Windows.Forms.SplitContainer>

- <xref:System.Windows.Forms.Splitter>

- <xref:System.Windows.Forms.StatusBar>

- <xref:System.Windows.Forms.StatusStrip>

- <xref:System.Windows.Forms.TabControl>

- <xref:System.Windows.Forms.TableLayoutPanel>

- <xref:System.Timers.Timer>

- <xref:System.Windows.Forms.Timer>

- <xref:System.Windows.Forms.ToolBar>

- <xref:System.Windows.Forms.ToolStrip>

- <xref:System.Windows.Forms.ToolStripContainer>

- <xref:System.Windows.Forms.ToolStripDropDown>

- <xref:System.Windows.Forms.ToolStripDropDownMenu>

- <xref:System.Windows.Forms.ToolStripPanel>

### <a name="support-for-legacy-activex-controls"></a>Prise en charge pour les contrôles ActiveX hérités

Si vous créez un projet Office au niveau du document qui utilise un document Word existant ou un classeur Excel qui contient des contrôles ActiveX, les fonctionnalités des contrôles ActiveX ne sont pas perdues ; Toutefois, il n’existe aucune prise en charge pour l’ajout de nouveaux contrôles ActiveX à vos documents à partir de Visual Studio. Par exemple, si votre document Word possède un bouton à partir de la **contrôle** boîte à outils qui s’exécute une macro Visual Basic pour Applications (VBA), il continue de s’exécuter la macro après le document a été utilisé dans un projet Office. Toutefois, il est recommandé de supprimer les contrôles ActiveX et les macros VBA et remplacez-les par les contrôles Windows Forms et le code managé.

## <a name="see-also"></a>Voir aussi

- [Contrôles sur des documents Office](../vsto/controls-on-office-documents.md)
- [Contrôles Windows Forms dans les documents Office](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Ajouter des contrôles aux documents Office au moment de l’exécution](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Guide pratique pour Ajouter des contrôles Windows Forms aux documents Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)