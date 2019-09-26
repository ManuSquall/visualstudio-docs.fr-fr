---
title: Limitations des contrôles de Windows Forms sur les documents Office
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
ms.openlocfilehash: 81a7da585f49b2a2d1f7df4df11d0c78b7a35d69
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71251915"
---
# <a name="limitations-of-windows-forms-controls-on-office-documents"></a>Limitations des contrôles de Windows Forms sur les documents Office

Il existe des différences entre les contrôles de Windows Forms ajoutés aux documents Word Microsoft Office ou Microsoft Office les feuilles de calcul Excel, ainsi que les contrôles Windows Forms ajoutés à Windows Forms. Par exemple, lorsque vous ajoutez un <xref:Microsoft.Office.Tools.Word.Controls.Button> contrôle à un document, les propriétés telles <xref:System.Windows.Forms.Control.Dock>que <xref:System.Windows.Forms.Control.Anchor>, et <xref:System.Windows.Forms.Control.TabIndex> ne se comportent pas comme vous le souhaitez.

La plupart de ces différences sont dues à la façon dont Windows Forms contrôles sont hébergés sur des documents. Lorsqu’un contrôle Windows Forms est ajouté à un document, le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] incorpore un contrôle ActiveX qui héberge ensuite le contrôle Windows Forms dans le document. Le contrôle Windows Forms n’est pas incorporé directement dans le document.

[!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

## <a name="limitations-of-methods-and-properties-of-windows-forms-controls"></a>Limitations des méthodes et des propriétés des contrôles Windows Forms

Il existe plusieurs méthodes et propriétés de Windows Forms les contrôles qui ne fonctionnent pas de la même manière sur un document que sur un Windows Form et, par conséquent, il est recommandé de ne pas les utiliser. Par exemple, la définition de propriétés <xref:System.Windows.Forms.Control.Dock> telles <xref:System.Windows.Forms.Control.Anchor> que et affecte uniquement la position du contrôle par rapport au contrôle ActiveX conteneur, plutôt que le document. La liste suivante répertorie les propriétés et méthodes non prises en charge des contrôles Windows Forms pour Word et Excel :

- Propriétés de contrôles Excel non prises en charge :

  - <xref:System.Windows.Forms.Control.Anchor>
  - <xref:System.Windows.Forms.Control.Dock>
  - <xref:System.Windows.Forms.Control.Location>
  - <xref:System.Windows.Forms.Control.TabIndex>
  - <xref:System.Windows.Forms.Control.TabStop>
  - <xref:System.Windows.Forms.Control.TopLevelControl>

- Méthodes et propriétés de contrôles Word non prises en charge :

  - <xref:System.Windows.Forms.Control.Hide%2A>
  - <xref:System.Windows.Forms.Control.Show%2A>
  - <xref:System.Windows.Forms.Control.Anchor>
  - <xref:System.Windows.Forms.Control.Dock>
  - <xref:System.Windows.Forms.Control.Location>
  - <xref:System.Windows.Forms.Control.TabIndex>
  - <xref:System.Windows.Forms.Control.TabStop>
  - <xref:System.Windows.Forms.Control.TopLevelControl>
  - <xref:System.Windows.Forms.Control.Visible>

Vous ne pouvez pas non <xref:System.Windows.Forms.Control.Left> plus <xref:System.Windows.Forms.Control.Top> définir la propriété ou de Windows Forms contrôles qui sont alignés sur le texte d’un document Word. Les contrôles Windows Forms sont ajoutés en ligne avec le texte dans les cas suivants :

- Vous ajoutez par programmation un contrôle à un document Word et utilisez une méthode qui spécifie une plage pour l’emplacement.

- Vous ajoutez un contrôle de Windows Forms à un document Word au moment du Design. Vous pouvez modifier cela en modifiant le contrôle dans le concepteur.

## <a name="differences-in-windows-forms-controls-on-office-documents"></a>Différences dans les contrôles de Windows Forms sur les documents Office

Les contrôles Windows Forms ont généralement le même comportement sur un document Office que sur un formulaire Windows, mais il existe quelques différences. Le tableau suivant décrit les différences qui existent pour les contrôles de Windows Forms sur les documents Office.

|Fonctionnalité|Différence|
|-------------------|----------------|
|Ordre de tabulation du contrôle|Vous ne pouvez pas parcourir les contrôles placés dans une feuille de calcul Excel ou un document Word.|
|Groupe de contrôles|Vous ne pouvez pas <xref:System.Windows.Forms.GroupBox> utiliser un contrôle pour contenir d’autres contrôles sur un document Office. Lorsque vous ajoutez plusieurs cases d’option directement au document, les cases d’option ne s’excluent pas mutuellement. Vous pouvez écrire du code pour que les cases d’option s’excluent mutuellement ; Toutefois, l’approche recommandée consiste à ajouter les cases d’option à un contrôle utilisateur, puis à ajouter le contrôle utilisateur au document. Pour plus d’informations, consultez l’exemple contrôles Word ou contrôles Excel dans [exemples de développement Office et procédures pas à pas](../vsto/office-development-samples-and-walkthroughs.md).|
|Type de contrôle|Les contrôles Windows Forms utilisés sur les documents sont encapsulés dans une classe [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] fournie par qui donne aux contrôles des fonctionnalités supplémentaires spécifiques à la feuille de calcul Excel ou au document Word. Par exemple, si vous avez un contrôle **bouton** sur une feuille de calcul Excel, veillez à spécifier le <xref:Microsoft.Office.Tools.Excel.Controls.Button> type comme <xref:System.Windows.Forms.Button> au lieu de référencer ou de caster l’objet.|
|Position et taille du contrôle|La taille et la position du contrôle sont déterminées par les propriétés qui font partie du contrôle ActiveX conteneur. Les propriétés du contrôle ActiveX prennent des valeurs différentes de celles des propriétés équivalentes d’un contrôle de Windows Forms. Lorsque vous définissez les `Top`propriétés `Left`, `Height`, ou `Width` d’un contrôle, elles sont mesurées en points, plutôt que en pixels.|
|Position du contrôle dans les documents Word|Si vous ajoutez des contrôles à une disposition basée sur le workflow, gardez à l’esprit que les contrôles circuleront avec le contenu lorsque le contenu sera modifié. Vous ne pouvez pas ancrer le contrôle à un paragraphe quand vous le faites glisser à partir de la **boîte à outils** , car le contrôle est ajouté au document Word en ligne avec le texte. Si vous utilisez une autre méthode pour ajouter le contrôle, par exemple en double-cliquant sur le contrôle, le contrôle est inséré en fonction de l’option de mot que vous avez définie pour l’insertion d’images.<br /><br /> Vous ne pouvez pas `Left` définir `Top` la propriété ou d’un contrôle qui est inséré avec du texte.<br /><br /> Vous ne pouvez pas placer de contrôles dans un en-tête ou un pied de page, ni dans un sous-document.|
|Événements de contrôle|Lorsque le contrôle est sélectionné, il déclenche des événements dans l’ordre suivant :<br /><br /> 1.  `Enter`<br />2.  `GotFocus`<br /><br /> Lorsque le contrôle est désélectionné, les événements sont déclenchés dans l’ordre suivant :<br /><br /> 1.  `Leave`<br />2.  `Validating`<br />3.  `Validated`<br />4.  `LostFocus`|
|Mise à l’échelle du contrôle|Lorsque vous modifiez le paramètre de zoom d’un document sur une valeur autre que 100%, les contrôles sont désactivés, même s’ils semblent être mis à l’échelle avec le document. Par exemple, si vous cliquez sur un bouton lorsque votre document est à 130% zoom, un message s’affiche pour indiquer que le contrôle a été désactivé jusqu’à ce que le zoom soit défini sur 100%. Les contrôles fonctionnent correctement lorsque vous modifiez le zoom sur 100%.|
|Valeurs des propriétés du contrôle|Bien que les propriétés des contrôles d’un Windows Form soient définies sur une valeur entière, elles sont définies sur un seul pour les contrôles d’un document Word. Dans Excel, les valeurs de propriété des contrôles sont définies sur un double. Si la `Height` propriété `Width` et d’un contrôle sur une feuille de calcul dépasse la taille de la feuille de calcul ou de l’écran, la valeur est tronquée.|
|Redimensionnement des contrôles|Si vous redimensionnez un contrôle sur le document à l’aide de l’une des huit poignées de redimensionnement, les nouvelles dimensions de contrôle ne sont pas reflétées dans la fenêtre **Propriétés** tant que le contrôle n’est pas resélectionné.|
|Comportement du contrôle|Les contrôles sur une feuille de calcul Excel peuvent se comporter de façon imprévisible lorsque la fenêtre de feuille de calcul est fractionnée. Par exemple, l’accès à <xref:Microsoft.Office.Tools.Excel.Controls.TextBox> un sur la feuille de calcul peut ne pas être disponible dans l’une des fenêtres.|
|Nommer le contrôle|Vous ne pouvez pas utiliser de mots réservés pour nommer des contrôles. Par exemple, si vous ajoutez un <xref:Microsoft.Office.Tools.Excel.Controls.Button> à une feuille de calcul et que vous remplacez le nom par **système**, des erreurs se produisent lorsque vous générez le projet.|
|Ajout de contrôles par programmation|N’utilisez pas le constructeur du contrôle pour ajouter un contrôle à votre document au moment de l’exécution. Au lieu de cela, utilisez les méthodes d’assistance [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]fournies par le. Par exemple, utilisez la <xref:Microsoft.Office.Tools.Excel.ControlExtensions.AddButton%2A> méthode pour ajouter un bouton à une feuille de calcul. Si vous souhaitez ajouter un contrôle qui n’est pas pris en charge par ces méthodes d’assistance, vous pouvez `AddControl` utiliser la méthode. Pour plus d’informations, consultez [Ajouter des contrôles aux documents Office au moment de l’exécution](../vsto/adding-controls-to-office-documents-at-run-time.md).|
|Copier des contrôles|Si vous copiez un contrôle Windows Forms et que vous le collez dans un document au moment de l’exécution, un contrôle ActiveX conteneur vide est collé dans le document. Le contrôle Windows Forms n’apparaît pas dans le nouvel emplacement et le code derrière le contrôle d’origine n’est pas copié dans le contrôle ActiveX conteneur.|

## <a name="limitations-in-document-level-projects"></a>Limitations dans les projets au niveau du document

Certaines limitations de l’utilisation de Windows Forms contrôles sur les documents sont uniques aux projets au niveau du document.

### <a name="control-support-at-design-time"></a>Contrôler la prise en charge au moment du design

Certains contrôles Windows Forms sont supprimés de la **boîte à outils** lorsqu’une feuille de calcul Excel ou un document Word est ouvert dans le concepteur Visual Studio. Cela est dû à des limitations techniques ou au fait que les fonctionnalités sont déjà disponibles dans Word ou Excel. Les projets Excel et Word prennent en charge tous les contrôles Windows Forms et d’autres composants qui s’affichent dans la **boîte à outils** lorsque le document a le focus, et vous pouvez également ajouter des contrôles tiers à une feuille de calcul ou à un document.

> [!NOTE]
> Tous les contrôles sont supprimés de la **boîte à outils** lorsqu’un document est protégé. Pour plus d’informations sur la protection des documents, consultez [protection des documents dans les solutions au niveau du document](../vsto/document-protection-in-document-level-solutions.md).

> [!NOTE]
> L’attribut des contrôles tiers doit avoir <xref:System.Runtime.InteropServices.ComVisibleAttribute> la valeur **true** pour pouvoir être utilisés dans une solution Office.

Les contrôles et les composants suivants ne sont pas disponibles dans la **boîte à outils**:

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

### <a name="support-for-legacy-activex-controls"></a>Prise en charge des contrôles ActiveX hérités

Si vous créez un projet Office au niveau du document qui utilise un document Word ou un classeur Excel existant qui contient des contrôles ActiveX, les fonctionnalités des contrôles ActiveX ne sont pas perdues. Toutefois, il n’existe aucune prise en charge pour l’ajout de nouveaux contrôles ActiveX à vos documents dans Visual Studio. Par exemple, si votre document Word a un bouton de la boîte à outils de **contrôle** qui exécute une macro Visual Basic pour applications (VBA), il continue à exécuter la macro une fois que le document a été utilisé dans un projet Office. Toutefois, il est recommandé de supprimer les contrôles ActiveX et les macros VBA et de les remplacer par des contrôles Windows Forms et du code managé.

## <a name="see-also"></a>Voir aussi

- [Contrôles sur les documents Office](../vsto/controls-on-office-documents.md)
- [Vue d’ensemble des contrôles de Windows Forms sur les documents Office](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Ajouter des contrôles aux documents Office au moment de l’exécution](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Guide pratique pour Ajouter des contrôles de Windows Forms aux documents Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
