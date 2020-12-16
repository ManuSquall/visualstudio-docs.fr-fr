---
title: Mettre à jour le projet Excel ou Word migré vers .NET Framework 4,5
description: Vous devez modifier votre code si la version cible de .NET Framework est remplacée par la .NET Framework 4 ou ultérieure quand vous avez un projet Excel ou Word qui utilise des fonctionnalités spécifiques.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office projects [Office development in Visual Studio], migrating to .NET Framework 4
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7bc79a53b62cf9fb0ca0ba533a2ce0d542b08c72
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97528434"
---
# <a name="update-excel-and-word-projects-that-you-migrate-to-the-net-framework-45"></a>Mettre à jour les projets Excel et Word que vous migrez vers le .NET Framework 4,5
  Si vous avez un projet Excel ou Word qui utilise l'une des fonctionnalités suivantes, vous devez modifier votre code si la version cible de .NET Framework est remplacée par le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou version ultérieure :

- [Méthodes GetVstoObject et HasVstoObject](#GetVstoObject)

- [Classes générées dans les projets au niveau du document](#generatedclasses)

- [Contrôles Windows Forms sur les documents](#winforms)

- [Événements de contrôle de contenu Word](#ccevents)

- [Classes OLEObject et OLEControl](#ole)

- [Controls.Item (Object), propriété](#itemproperty)

- [Collections dérivant de CollectionBase](#collections)

  Vous devez également supprimer les `Microsoft.Office.Tools.Excel.ExcelLocale1033Attribute` références et à la `Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy` classe des projets Excel qui sont reciblés vers le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou version ultérieure. Visual Studio ne supprime pas cet attribut ou la référence de classe pour vous.

## <a name="remove-the-excellocale1033-attribute-from-excel-projects"></a>Supprimer l’attribut Excellocale1033 des des projets Excel
 `Microsoft.Office.Tools.Excel.ExcelLocale1033Attribute`A été supprimé de la partie de Visual Studio 2010 Tools pour Office Runtime utilisée pour les solutions qui ciblent le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou version ultérieure. Le common language runtime (CLR) dans le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] et version ultérieure transmet toujours l'ID de paramètres régionaux 1033 au modèle objet Excel, et vous ne pouvez plus utiliser cet attribut pour désactiver ce comportement. Pour plus d’informations, consultez [globalisation and localization of Excel solutions](../vsto/globalization-and-localization-of-excel-solutions.md).

### <a name="to-remove-the-excellocale1033attribute"></a>Pour supprimer l'attribut ExcelLocale1033

1. Le projet étant ouvert dans Visual Studio, ouvrez l' **Explorateur de solutions**.

2. Sous le nœud **Propriétés** (pour C#) ou le nœud **My Project** (pour Visual Basic), double-cliquez sur le fichier de code AssemblyInfo pour l'ouvrir dans l'éditeur de code.

    > [!NOTE]
    > Dans les projets Visual Basic, vous devez cliquer sur le bouton **Afficher tous les fichiers** de l' **Explorateur de solutions** pour afficher le fichier de code AssemblyInfo.

3. Recherchez le `Microsoft.Office.Tools.Excel.ExcelLocale1033Attribute` et supprimez-le du fichier ou commentez-le.

    ```vb
    <Assembly: ExcelLocale1033Proxy(True)>
    ```

    ```csharp
    [assembly: ExcelLocale1033Proxy(true)]
    ```

## <a name="remove-a-reference-to-the-excellocal1033proxy-class"></a>Supprimer une référence à la classe ExcelLocal1033Proxy
 Les projets qui ont été créés à l'aide de Microsoft Visual Studio 2005 Tools pour Microsoft Office System instancient l'objet Excel <xref:Microsoft.Office.Interop.Excel.Application> à l'aide de la classe `Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy`. Cette classe a été supprimée de la partie de Visual Studio 2010 Tools pour Office Runtime utilisée pour les solutions qui ciblent le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou version ultérieure. Par conséquent, vous devez supprimer ou commenter la ligne de code qui fait référence à cette classe.

### <a name="to-remove-the-reference-to-the-excellocal1033proxy-class"></a>Pour supprimer la référence à la classe ExcelLocal1033Proxy

1. Ouvrez le projet dans Visual Studio, puis ouvrez l' **Explorateur de solutions**.

2. Dans **Explorateur de solutions**, ouvrez le menu contextuel de *ThisAddIn.cs* (pour C#) ou *ThisAddin. vb* (pour Visual Basic), puis choisissez **afficher le code**.

3. Dans l'éditeur de code, dans la région `VSTO generated code` , supprimez ou commentez la ligne de code suivante.

    ```vb
    Me.Application = CType(Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy.Wrap(GetType(Excel.Application), Me.Application), Excel.Application)

    ```

    ```csharp
    this.Application = (Excel.Application)Microsoft.Office.Tools.Excel.ExcelLocale1033Proxy.Wrap(typeof(Excel.Application), this.Application);

    ```

## <a name="update-code-that-uses-the-getvstoobject-and-hasvstoobject-methods"></a><a name="GetVstoObject"></a> Mettre à jour le code qui utilise les méthodes GetVstoObject et HasVstoObject
 Dans les projets qui ciblent le .NET Framework 3.5, les méthodes `GetVstoObject` ou `HasVstoObject` sont disponibles en tant que méthodes d’extension sur l’un des objets natifs suivants de votre projet : <xref:Microsoft.Office.Interop.Word.Document>, <xref:Microsoft.Office.Interop.Excel.Workbook>, <xref:Microsoft.Office.Interop.Excel.Worksheet> ou <xref:Microsoft.Office.Interop.Excel.ListObject>. Lorsque vous appelez ces méthodes, il est inutile de passer un paramètre. L’exemple de code suivant montre comment utiliser la méthode GetVstoObject dans un complément VSTO Word qui cible le .NET Framework 3,5.

```vb
Dim vstoDocument as Microsoft.Office.Tools.Word.Document = _
    Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject()
```

```csharp
Microsoft.Office.Tools.Word.Document vstoDocument =
    Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject();
```

 Dans les projets qui ciblent le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou version ultérieure, vous devez modifier votre code pour accéder à ces méthodes selon l'une des manières suivantes :

- Vous pouvez toujours accéder à ces méthodes comme méthodes d'extension sur les objets <xref:Microsoft.Office.Interop.Word.Document>, <xref:Microsoft.Office.Interop.Excel.Workbook>, <xref:Microsoft.Office.Interop.Excel.Worksheet>ou <xref:Microsoft.Office.Interop.Excel.ListObject> . Toutefois, vous devez maintenant passer l'objet retourné par la propriété `Globals.Factory` à ces méthodes.

  ```vb
  Dim vstoDocument as Microsoft.Office.Tools.Word.Document = _
      Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject(Globals.Factory)
  ```

  ```csharp
  Microsoft.Office.Tools.Word.Document vstoDocument =
      Globals.ThisAddIn.Application.ActiveDocument.GetVstoObject(Globals.Factory);
  ```

- Vous pouvez également accéder à ces méthodes sur l'objet retourné par la propriété `Globals.Factory`. Lorsque vous accédez à ces méthodes de cette façon, vous devez passer l'objet natif que vous souhaitez étendre à la méthode.

  ```vb
  Dim vstoDocument as Microsoft.Office.Tools.Word.Document = _
      Globals.Factory.GetVstoObject(Globals.ThisAddIn.Application.ActiveDocument)
  ```

  ```csharp
  Microsoft.Office.Tools.Word.Document vstoDocument =
      Globals.Factory.GetVstoObject(Globals.ThisAddIn.Application.ActiveDocument);
  ```

  Pour plus d’informations, consultez [extension de documents Word et de classeurs Excel dans des compléments VSTO au moment](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)de l’exécution.

## <a name="update-code-that-uses-instances-of-the-generated-classes-in-document-level-projects"></a><a name="generatedclasses"></a> Mettre à jour le code qui utilise des instances des classes générées dans les projets au niveau du document
 Dans les projets au niveau du document qui ciblent le .NET Framework 3.5, les classes générées dans les projets dérivent des classes suivantes dans le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]:

- `ThisDocument`: <xref:Microsoft.Office.Tools.Word.Document>

- `ThisWorkbook`: <xref:Microsoft.Office.Tools.Excel.Workbook>

- `Sheet`*n*:<xref:Microsoft.Office.Tools.Excel.Worksheet>

- `Chart`*n*:<xref:Microsoft.Office.Tools.Excel.ChartSheet>

  Dans les projets qui ciblent le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou version ultérieure, les types répertoriés dans la liste [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] ci-dessus sont des interfaces, et non des classes. Les classes générées dans les projets qui ciblent le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou version ultérieure dérivent des nouvelles classes suivantes dans le [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]:

- `ThisDocument`: <xref:Microsoft.Office.Tools.Word.DocumentBase>

- `ThisWorkbook`: <xref:Microsoft.Office.Tools.Excel.WorkbookBase>

- `Sheet`*n*:<xref:Microsoft.Office.Tools.Excel.WorksheetBase>

- `Chart`*n*:<xref:Microsoft.Office.Tools.Excel.ChartSheetBase>

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

- Modifiez le code qui appelle la méthode `DoSomethingToSheet` pour passer la propriété <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Base%2A> d'un objet <xref:Microsoft.Office.Tools.Excel.WorksheetBase> dans votre projet. La propriété retourne un objet <xref:Microsoft.Office.Tools.Excel.Worksheet> .

    ```vb
    DoSomethingToSheet(Globals.Sheet1.Base)
    ```

    ```csharp
    DoSomethingToSheet(Globals.Sheet1.Base);
    ```

- Modifiez le paramètre de la méthode `DoSomethingToSheet` pour attendre un objet <xref:Microsoft.Office.Tools.Excel.WorksheetBase> à la place.

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

## <a name="update-code-that-uses-windows-forms-controls-on-documents"></a><a name="winforms"></a> Mettre à jour le code qui utilise Windows Forms contrôles sur les documents
 Vous devez ajouter une instruction **using** (C#) ou **Imports** (Visual Basic) pour l' <xref:Microsoft.Office.Tools.Excel> espace de noms ou <xref:Microsoft.Office.Tools.Word> en haut de tout fichier de code qui utilise la propriété Controls pour ajouter Windows Forms contrôles au document ou à la feuille de calcul par programmation.

 Dans les projets qui ciblent le .NET Framework 3.5, les méthodes qui ajoutent des contrôles Windows Forms (tels que la méthode `AddButton`) sont définies dans les classes <xref:Microsoft.Office.Tools.Excel.ControlCollection> et <xref:Microsoft.Office.Tools.Word.ControlCollection>.

 Dans les projets qui ciblent le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou version ultérieure, ces méthodes sont des méthodes d’extension disponibles sur la propriété contrôles. Pour utiliser ces méthodes d'extension, le fichier de code dans lequel vous utilisez les méthodes doit avoir une instruction **using** ou **Imports** pour l'espace de noms <xref:Microsoft.Office.Tools.Excel> ou <xref:Microsoft.Office.Tools.Word> . Cette instruction est générée automatiquement dans les nouveaux projets qui ciblent le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou version ultérieure. Toutefois, comme cette instruction n'est pas ajoutée automatiquement aux projets qui ciblent le .NET Framework 3.5, vous devez l'ajouter lorsque vous reciblez le projet.

 Pour plus d’informations, consultez [Ajouter des contrôles aux documents Office au moment de l’exécution](../vsto/adding-controls-to-office-documents-at-run-time.md).

## <a name="update-code-that-handles-word-content-control-events"></a><a name="ccevents"></a> Mettre à jour le code qui gère les événements de contrôle de contenu Word
 Dans les projets qui ciblent le .NET Framework 3.5, les événements de contrôles de contenu Word sont contrôlés par le délégué générique <xref:System.EventHandler%601> . Dans les projets qui ciblent le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou version ultérieure, ces événements sont gérés par d'autres délégués.

 Le tableau suivant répertorie les événements de contrôle de contenu Word et les délégués qui leur sont associés dans les projets qui ciblent le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou version ultérieure.

|Événement|Délégué à utiliser dans les projets [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] et version ultérieure|
|-----------| - |
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Added>|<xref:Microsoft.Office.Tools.Word.ContentControlAddedEventHandler>|
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.ContentUpdating>|<xref:Microsoft.Office.Tools.Word.ContentControlContentUpdatingEventHandler>|
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Deleting>|<xref:Microsoft.Office.Tools.Word.ContentControlDeletingEventHandler>|
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Entering>|<xref:Microsoft.Office.Tools.Word.ContentControlEnteringEventHandler>|
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Exiting>|<xref:Microsoft.Office.Tools.Word.ContentControlExitingEventHandler>|
|<xref:Microsoft.Office.Tools.Word.ContentControlBase.StoreUpdating>|<xref:Microsoft.Office.Tools.Word.ContentControlStoreUpdatingEventHandler>|

## <a name="update-code-that-uses-the-oleobject-and-olecontrol-classes"></a><a name="ole"></a> Mettre à jour le code qui utilise les classes OLEObject et OLEControl
 Dans les projets qui ciblent le .NET Framework 3.5, vous pouvez ajouter des contrôles personnalisés (tels que les contrôles utilisateur Windows Forms) à un document ou à une feuille de calcul à l'aide des classes `Microsoft.Office.Tools.Excel.OLEObject` et `Microsoft.Office.Tools.Word.OLEControl`.

 Dans les projets qui ciblent le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou version ultérieure, ces classes ont été remplacées par les interfaces <xref:Microsoft.Office.Tools.Excel.ControlSite> et <xref:Microsoft.Office.Tools.Word.ControlSite> . Vous devez modifier le code qui fait référence à `Microsoft.Office.Tools.Excel.OLEObject` et `Microsoft.Office.Tools.Word.OLEControl` pour faire référence à la place à <xref:Microsoft.Office.Tools.Excel.ControlSite> et <xref:Microsoft.Office.Tools.Word.ControlSite>. En dehors des nouveaux noms, ces contrôles se comportent de la même façon que dans les projets qui ciblent le .NET Framework 3.5.

 Pour plus d’informations, consultez [Ajouter des contrôles aux documents Office au moment de l’exécution](../vsto/adding-controls-to-office-documents-at-run-time.md).

## <a name="update-code-that-uses-the-controlsitemobject-property"></a><a name="itemproperty"></a> Mettre à jour le code qui utilise la propriété Controls. Item (Object)
 Dans les projets qui ciblent le .NET Framework 3,5, vous pouvez utiliser la propriété Item (Object) de l' Microsoft.Office.Tools.Word.Document. Contrôles ou `Microsoft.Office.Tools.Excel.Worksheet.Controls` collections pour déterminer si un document ou une feuille de calcul possède un contrôle spécifié.

 Dans les projets qui ciblent le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou version ultérieure, la propriété Item (Object) a été supprimée de ces collections. Pour déterminer si un document ou une feuille de calcul contient un contrôle spécifié, utilisez la méthode Contains (System. Object) de la <xref:Microsoft.Office.Tools.Word.Document.Controls%2A> collection ou à la <xref:Microsoft.Office.Tools.Excel.Worksheet.Controls%2A> place.

 Pour plus d’informations sur la collection de contrôles de documents et de feuilles de calcul, consultez [Ajouter des contrôles aux documents Office au moment de l’exécution](../vsto/adding-controls-to-office-documents-at-run-time.md).

## <a name="update-code-that-uses-collections-that-derive-from-collectionbase"></a><a name="collections"></a> Mettre à jour le code qui utilise des collections dérivant de CollectionBase
 Dans les projets qui ciblent le .NET Framework 3,5, plusieurs types de collections dans [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] dérivent de la <xref:System.Collections.CollectionBase> classe, tels que `Microsoft.Office.Tools.SmartTagCollection` , `Microsoft.Office.Tools.Excel.ControlCollection` et `Microsoft.Office.Tools.Word.ControlCollection` .

 Dans les projets qui ciblent le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou version ultérieure, ces types de collections sont maintenant des interfaces qui ne dérivent pas de <xref:System.Collections.CollectionBase>. Certains membres ne sont plus disponibles sur ces types de collections, comme <xref:System.Collections.CollectionBase.Capacity%2A>, <xref:System.Collections.CollectionBase.List%2A>et <xref:System.Collections.CollectionBase.InnerList%2A>.

## <a name="see-also"></a>Voir aussi
- [Migrer des solutions Office vers le .NET Framework 4 ou version ultérieure](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)
- [Contrôles de contenu](../vsto/content-controls.md)
- [Étendre des documents Word et des classeurs Excel dans des compléments VSTO au moment de l’exécution](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Ajouter des contrôles aux documents Office au moment de l’exécution](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Accès global aux objets dans les projets Office](../vsto/global-access-to-objects-in-office-projects.md)
