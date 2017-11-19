---
title: "Mise à jour des projets Excel et Word que vous migrez vers le .NET Framework 4 ou .NET Framework 4.5 | Documents Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords: Office projects [Office development in Visual Studio], migrating to .NET Framework 4
ms.assetid: 282c8876-fd49-462e-875b-4a0a79ad951c
caps.latest.revision: "25"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7d3783eb2bd87decc0e01bb589b08f3d0c05803e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="updating-excel-and-word-projects-that-you-migrate-to-the-net-framework-4-or-the-net-framework-45"></a>Mise à jour des projets Excel et Word qui font l'objet d'une migration vers .NET Framework 4 ou .NET Framework 4.5
  Si vous avez un projet Excel ou Word qui utilise l'une des fonctionnalités suivantes, vous devez modifier votre code si la version cible de .NET Framework est remplacée par le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou version ultérieure :  
  
-   [Méthodes GetVstoObject et HasVstoObject](#GetVstoObject)  
  
-   [Classes générées dans les projets au niveau du document](#generatedclasses)  
  
-   [Contrôles Windows Forms sur les documents](#winforms)  
  
-   [Événements de contrôle de contenu Word](#ccevents)  
  
-   [Classes OLEObject et OLEControl](#ole)  
  
-   [Controls.Item (Object), propriété](#itemproperty)  
  
-   [Collections dérivant de CollectionBase](#collections)  
  
 Vous devez également supprimer les Microsoft.Office.Tools.Excel.ExcelLocale1033Attribute et les références à la classe Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy des projets Excel reciblés vers le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou version ultérieure. Visual Studio ne supprime pas cet attribut ou la référence de classe pour vous.  
  
## <a name="removing-the-excellocale1033-attribute-from-excel-projects"></a>Suppression de l'attribut ExcelLocale1033 des projets Excel  
 Microsoft.Office.Tools.Excel.ExcelLocale1033Attribute a été supprimé de la partie de Visual Studio 2010 Tools pour Office Runtime qui est utilisé pour les solutions qui ciblent le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou version ultérieure. Le common language runtime (CLR) dans le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] et version ultérieure transmet toujours l'ID de paramètres régionaux 1033 au modèle objet Excel, et vous ne pouvez plus utiliser cet attribut pour désactiver ce comportement. Pour plus d'informations, consultez [Globalization and Localization of Excel Solutions](../vsto/globalization-and-localization-of-excel-solutions.md).  
  
#### <a name="to-remove-the-excellocale1033attribute"></a>Pour supprimer l'attribut ExcelLocale1033  
  
1.  Le projet étant ouvert dans Visual Studio, ouvrez l' **Explorateur de solutions**.  
  
2.  Sous le nœud **Propriétés** (pour C#) ou le nœud **My Project** (pour Visual Basic), double-cliquez sur le fichier de code AssemblyInfo pour l'ouvrir dans l'éditeur de code.  
  
    > [!NOTE]  
    >  Dans les projets Visual Basic, vous devez cliquer sur le bouton **Afficher tous les fichiers** de l' **Explorateur de solutions** pour afficher le fichier de code AssemblyInfo.  
  
3.  Recherchez Microsoft.Office.Tools.Excel.ExcelLocale1033Attribute et le supprimer à partir du fichier ou commentez-le.  
  
    ```vb  
    <Assembly: ExcelLocale1033Proxy(True)>  
    ```  
  
    ```csharp  
    [assembly: ExcelLocale1033Proxy(true)]  
    ```  
  
## <a name="removing-a-reference-to-the-excellocal1033proxy-class"></a>Suppression d'une référence à la classe ExcelLocal1033Proxy  
 Les projets qui ont été créés à l’aide de Microsoft Visual Studio 2005 Tools pour Microsoft Office System instancient Excel <xref:Microsoft.Office.Interop.Excel.Application> objet à l’aide de la classe Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy. Cette classe a été supprimée de la partie de Visual Studio 2010 Tools pour Office Runtime utilisée pour les solutions qui ciblent le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou version ultérieure. Par conséquent, vous devez supprimer ou commenter la ligne de code qui fait référence à cette classe.  
  
#### <a name="to-remove-the-reference-to-the-excellocal1033proxy-class"></a>Pour supprimer la référence à la classe ExcelLocal1033Proxy  
  
1.  Ouvrez le projet dans Visual Studio, puis ouvrez l' **Explorateur de solutions**.  
  
2.  Dans l' **Explorateur de solutions**, ouvrez le menu contextuel de ThisAddin.cs (en C#) ou ThisAddin.vb (en Visual Basic), puis choisissez **Afficher le Code**.  
  
3.  Dans l'éditeur de code, dans la région `VSTO generated code` , supprimez ou commentez la ligne de code suivante.  
  
    ```vb  
    Me.Application = CType(Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy.Wrap(GetType(Excel.Application), Me.Application), Excel.Application)  
  
    ```  
  
    ```csharp  
    this.Application = (Excel.Application)Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy.Wrap(typeof(Excel.Application), this.Application);  
  
    ```  
  
##  <a name="GetVstoObject"></a> Mise à jour du code qui utilise les méthodes GetVstoObject et HasVstoObject  
 Dans les projets qui ciblent le .NET Framework 3.5, les méthodes GetVstoObject ou HasVstoObject sont disponibles en tant que méthodes d’extension sur l’un des objets natifs suivants de votre projet : <xref:Microsoft.Office.Interop.Word.Document>, <xref:Microsoft.Office.Interop.Excel.Workbook>, <xref:Microsoft.Office.Interop.Excel.Worksheet>, ou <xref:Microsoft.Office.Interop.Excel.ListObject>. Lorsque vous appelez ces méthodes, il est inutile de passer un paramètre. L’exemple de code suivant montre comment utiliser la méthode GetVstoObject dans un complément VSTO Word-qui cible le .NET Framework 3.5.  
  
```vb  
Dim vstoDocument as Microsoft.Office.Tools.Word.Document = _  
    Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject()  
```  
  
```csharp  
Microsoft.Office.Tools.Word.Document vstoDocument =   
    Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject();  
```  
  
 Dans les projets qui ciblent le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou version ultérieure, vous devez modifier votre code pour accéder à ces méthodes selon l'une des manières suivantes :  
  
-   Vous pouvez toujours accéder à ces méthodes comme méthodes d'extension sur les objets <xref:Microsoft.Office.Interop.Word.Document>, <xref:Microsoft.Office.Interop.Excel.Workbook>, <xref:Microsoft.Office.Interop.Excel.Worksheet>ou <xref:Microsoft.Office.Interop.Excel.ListObject> . Toutefois, vous devez maintenant passer l’objet retourné par la propriété Globals.Factory à ces méthodes.  
  
    ```vb  
    Dim vstoDocument as Microsoft.Office.Tools.Word.Document = _  
        Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject(Globals.Factory)  
    ```  
  
    ```csharp  
    Microsoft.Office.Tools.Word.Document vstoDocument =   
        Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject(Globals.Factory);  
    ```  
  
-   Vous pouvez également accéder à ces méthodes sur l’objet qui est retourné par la propriété Globals.Factory. Lorsque vous accédez à ces méthodes de cette façon, vous devez passer l'objet natif que vous souhaitez étendre à la méthode.  
  
    ```vb  
    Dim vstoDocument as Microsoft.Office.Tools.Word.Document = _  
        Globals.Factory.GetVstoObject(Globals.ThisAddIn.Application.ActiveDocument)  
    ```  
  
    ```csharp  
    Microsoft.Office.Tools.Word.Document vstoDocument =   
        Globals.Factory.GetVstoObject(Globals.ThisAddIn.Application.ActiveDocument);  
    ```  
  
 Pour plus d'informations, consultez [Extending Word Documents and Excel Workbooks in VSTO Add-ins at Run Time](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
##  <a name="generatedclasses"></a> Mise à jour du code qui utilise les instances des classes générées dans les projets au niveau du document  
 Dans les projets au niveau du document qui ciblent le .NET Framework 3.5, les classes générées dans les projets dérivent des classes suivantes dans le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]:  
  
-   `ThisDocument`: <xref:Microsoft.Office.Tools.Word.Document>  
  
-   `ThisWorkbook`: <xref:Microsoft.Office.Tools.Excel.Workbook>  
  
-   `Sheet` *n*: <xref:Microsoft.Office.Tools.Excel.Worksheet>  
  
-   `Chart` *n*: <xref:Microsoft.Office.Tools.Excel.ChartSheet>  
  
 Dans les projets qui ciblent le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou version ultérieure, les types répertoriés dans la liste [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] ci-dessus sont des interfaces, et non des classes. Les classes générées dans les projets qui ciblent le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou version ultérieure dérivent des nouvelles classes suivantes dans le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]:  
  
-   `ThisDocument`: <xref:Microsoft.Office.Tools.Word.DocumentBase>  
  
-   `ThisWorkbook`: <xref:Microsoft.Office.Tools.Excel.WorkbookBase>  
  
-   `Sheet` *n*: <xref:Microsoft.Office.Tools.Excel.WorksheetBase>  
  
-   `Chart` *n*: <xref:Microsoft.Office.Tools.Excel.ChartSheetBase>  
  
 Si le code de votre projet fait référence à une instance de l'une des classes générées comme classe de base dont il dérive, vous devez modifier le code.  
  
 Par exemple, dans un projet de classeur Excel qui cible le .NET Framework 3.5, vous pouvez avoir une méthode d'assistance qui effectue des opérations sur les instances des classes `Sheet`*n* générées dans votre projet.  
  
```vb  
Private Sub DoSomethingToSheet(ByVal worksheet As Microsoft.Office.Tools.Excel.Worksheet)  
    ' Do something to the worksheet object.  
End Sub  
```  
  
```csharp  
private void DoSomethingToSheet(Microsoft.Office.Tools.Excel.Worksheet worksheet)  
{  
    // Do something to the worksheet object.  
}  
```  
  
 Si vous reciblez le projet vers le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou version ultérieure, vous devez effectuer l'une des modifications suivantes de votre code :  
  
-   Modifiez le code qui appelle la méthode `DoSomethingToSheet` pour passer la propriété <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Base%2A> d'un objet <xref:Microsoft.Office.Tools.Excel.WorksheetBase> dans votre projet. La propriété retourne un objet <xref:Microsoft.Office.Tools.Excel.Worksheet> .  
  
    ```vb  
    DoSomethingToSheet(Globals.Sheet1.Base)  
    ```  
  
    ```csharp  
    DoSomethingToSheet(Globals.Sheet1.Base);  
    ```  
  
-   Modifiez le paramètre de la méthode `DoSomethingToSheet` pour attendre un objet <xref:Microsoft.Office.Tools.Excel.WorksheetBase> à la place.  
  
    ```vb  
    Private Sub DoSomethingToSheet(ByVal worksheet As Microsoft.Office.Tools.Excel.WorksheetBase)  
        ' Do something to the worksheet object.  
    End Sub  
    ```  
  
    ```csharp  
    private void DoSomethingToSheet (Microsoft.Office.Tools.Excel.WorksheetBase worksheet)  
    {  
        // Do something to the worksheet object.  
    }  
    ```  
  
##  <a name="winforms"></a> Mise à jour du code qui utilise les contrôles Windows Forms sur les documents  
 Vous devez ajouter un **à l’aide de** (c#) ou **importations** instruction (Visual Basic) pour le <xref:Microsoft.Office.Tools.Excel> ou <xref:Microsoft.Office.Tools.Word> espace de noms en haut d’un fichier de code qui utilise la propriété de contrôles pour ajouter des Windows Forms par programmation des contrôles au document ou feuille de calcul.  
  
 Dans les projets qui ciblent le .NET Framework 3.5, les méthodes qui ajoutent des contrôles Windows Forms (par exemple, la méthode AddButton) sont définies dans le <xref:Microsoft.Office.Tools.Excel.ControlCollection> et <xref:Microsoft.Office.Tools.Word.ControlCollection> classes.  
  
 Dans les projets qui ciblent le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou version ultérieure, ces méthodes sont des méthodes d’extension qui sont disponibles sur la propriété de contrôles. Pour utiliser ces méthodes d'extension, le fichier de code dans lequel vous utilisez les méthodes doit avoir une instruction **using** ou **Imports** pour l'espace de noms <xref:Microsoft.Office.Tools.Excel> ou <xref:Microsoft.Office.Tools.Word> . Cette instruction est générée automatiquement dans les nouveaux projets qui ciblent le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou version ultérieure. Toutefois, comme cette instruction n'est pas ajoutée automatiquement aux projets qui ciblent le .NET Framework 3.5, vous devez l'ajouter lorsque vous reciblez le projet.  
  
 Pour plus d'informations, consultez [Adding Controls to Office Documents at Run Time](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
##  <a name="ccevents"></a> Mise à jour du code qui gère les événements de contrôle de contenu Word  
 Dans les projets qui ciblent le .NET Framework 3.5, les événements de contrôles de contenu Word sont contrôlés par le délégué générique <xref:System.EventHandler%601> . Dans les projets qui ciblent le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou version ultérieure, ces événements sont gérés par d'autres délégués.  
  
 Le tableau suivant répertorie les événements de contrôle de contenu Word et les délégués qui leur sont associés dans les projets qui ciblent le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou version ultérieure.  
  
|Événement|Délégué à utiliser dans les projets [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] et version ultérieure|  
|-----------|---------------------------------------------------------------------------------------------------|  
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Added>|<xref:Microsoft.Office.Tools.Word.ContentControlAddedEventHandler>|  
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.ContentUpdating>|<xref:Microsoft.Office.Tools.Word.ContentControlContentUpdatingEventHandler>|  
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Deleting>|<xref:Microsoft.Office.Tools.Word.ContentControlDeletingEventHandler>|  
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Entering>|<xref:Microsoft.Office.Tools.Word.ContentControlEnteringEventHandler>|  
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Exiting>|<xref:Microsoft.Office.Tools.Word.ContentControlExitingEventHandler>|  
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.StoreUpdating>|<xref:Microsoft.Office.Tools.Word.ContentControlStoreUpdatingEventHandler>|  
  
##  <a name="ole"></a> Mise à jour du code qui utilise les classes OLEObject et OLEControl  
 Dans les projets qui ciblent le .NET Framework 3.5, vous pouvez ajouter des contrôles personnalisés (tels que les contrôles utilisateur Windows Forms) à un document ou une feuille de calcul en utilisant les classes Microsoft.Office.Tools.Excel.OLEObject et Microsoft.Office.Tools.Word.OLEControl.  
  
 Dans les projets qui ciblent le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou version ultérieure, ces classes ont été remplacées par les interfaces <xref:Microsoft.Office.Tools.Excel.ControlSite> et <xref:Microsoft.Office.Tools.Word.ControlSite> . Vous devez modifier le code qui fait référence à Microsoft.Office.Tools.Excel.OLEObject et Microsoft.Office.Tools.Word.OLEControl faire référence à la place à <xref:Microsoft.Office.Tools.Excel.ControlSite> et <xref:Microsoft.Office.Tools.Word.ControlSite>. En dehors des nouveaux noms, ces contrôles se comportent de la même façon que dans les projets qui ciblent le .NET Framework 3.5.  
  
 Pour plus d'informations, consultez [Adding Controls to Office Documents at Run Time](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
##  <a name="itemproperty"></a> Mise à jour du code qui utilise la propriété Controls.Item (Object)  
 Dans les projets qui ciblent le .NET Framework 3.5, vous pouvez utiliser la propriété Item (Object) de la collection Microsoft.Office.Tools.Word.Document.Controls ou Microsoft.Office.Tools.Excel.Worksheet.Controls pour déterminer si un document ou une feuille de calcul possède un contrôle spécifié.  
  
 Dans les projets qui ciblent le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou une version ultérieure, la propriété Item (Object) a été supprimée de ces collections. Pour déterminer si un document ou une feuille de calcul contient un contrôle spécifié, utilisez la méthode Contains (System.Object) de la <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> ou <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A> collection à la place.  
  
 Pour plus d’informations sur la collection de contrôles de documents et feuilles de calcul, consultez [Ajout de contrôles aux Documents Office au moment de l’exécution](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
##  <a name="collections"></a> Mise à jour du code qui utilise les collections dérivant de CollectionBase  
 Dans les projets qui ciblent le .NET Framework 3.5, plusieurs types de collections dans le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] dérivent la <xref:System.Collections.CollectionBase> classe, tels que Microsoft.Office.Tools.SmartTagCollection, Microsoft.Office.Tools.Excel.ControlCollection, et Microsoft.Office.Tools.Word.ControlCollection.  
  
 Dans les projets qui ciblent le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou version ultérieure, ces types de collections sont maintenant des interfaces qui ne dérivent pas de <xref:System.Collections.CollectionBase>. Certains membres ne sont plus disponibles sur ces types de collections, comme <xref:System.Collections.CollectionBase.Capacity%2A>, <xref:System.Collections.CollectionBase.List%2A>et <xref:System.Collections.CollectionBase.InnerList%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 [Migrating Office Solutions to the .NET Framework 4 or later](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)   
 [Contrôles de contenu](../vsto/content-controls.md)   
 [Extension de Documents Word et classeurs Excel dans des Compléments VSTO au moment de l’exécution](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)   
 [Ajout de contrôles aux Documents Office au moment de l’exécution](../vsto/adding-controls-to-office-documents-at-run-time.md)   
 [Accès global aux objets dans les projets Office](../vsto/global-access-to-objects-in-office-projects.md)  
  
  