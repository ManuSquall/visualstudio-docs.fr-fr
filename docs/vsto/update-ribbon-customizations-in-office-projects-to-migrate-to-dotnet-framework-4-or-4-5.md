---
title: Mettre à jour les personnalisations de ruban dans les projets Office migrés vers .NET Framework 4, 4,5
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
ms.openlocfilehash: c7d7ab5755f592e57e76dcd68f3dcb9dc2a7eab9
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71254349"
---
# <a name="update-ribbon-customizations-in-office-projects-that-you-migrate-to-the-net-framework-4-or-the-net-framework-45"></a>Mettre à jour les personnalisations de ruban dans les projets Office que vous migrez vers le .NET Framework 4 ou le .NET Framework 4,5
  Si votre projet contient une personnalisation de ruban qui a été créée à l’aide de l’élément de projet **Ruban (concepteur visuel)** , vous devez apporter les modifications suivantes à votre code de projet si la version [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] cible de .NET Framework est remplacée par ou une version ultérieure.

- Modifiez le code de ruban généré.

- Modifiez tout code qui instancie des contrôles de ruban au moment de l’exécution, qui gère les événements de ruban ou qui définit la position d’un composant de ruban par programmation.

## <a name="update-the-generated-ribbon-code"></a>Mettre à jour le code de ruban généré
 Si la version cible de .NET Framework du projet est remplacée par [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou une version ultérieure, vous devez changer le code généré pour l'élément Ruban en procédant comme suit. Vous devez mettre à jour les fichiers de code en fonction du langage de programmation utilisé et de la façon dont vous avez créé le projet :

- Dans Visual Basic projets, ou dans des C# projets visuels que vous avez créés [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] dans [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)] ou effectuez toutes les étapes dans le fichier code-behind du ruban (*votreélémentruban*. Designer.cs ou *votreélémentruban*. Designer. vb). Pour afficher le fichier code-behind dans Visual Basic projets, cliquez sur le bouton **Afficher tous les fichiers** dans **Explorateur de solutions**.

- Dans les C# projets visuels que vous avez créés dans Visual Studio 2008, puis mis à [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)]niveau vers, effectuez les deux premières étapes dans le fichier de code du ruban (*votreélémentruban*. cs ou *votreélémentruban*. vb) et effectuez les étapes restantes dans le Fichier code-behind du ruban.

### <a name="to-change-the-generated-ribbon-code"></a>Pour changer le code de ruban généré

1. Modifiez la déclaration de la classe Ribbon pour qu'elle dérive de <xref:Microsoft.Office.Tools.Ribbon.RibbonBase> au lieu de `Microsoft.Office.Tools.Ribbon.OfficeRibbon`.

2. Modifiez le constructeur de la classe Ribbon, comme indiqué ci-dessous. Si vous avez ajouté votre propre code au constructeur, ne modifiez pas votre code. Dans les projets Visual Basic, modifiez uniquement le constructeur sans paramètre. Ignorez l'autre constructeur.

     L'exemple de code suivant montre le constructeur par défaut d'une classe Ribbon dans un projet qui cible .NET Framework 3.5.

    ```vb
    Public Sub New()
        MyBase.New()
        InitializeComponent()
    End Sub
    ```

    ```csharp
    public Ribbon1()
    {
        InitializeComponent();
    }
    ```

     L'exemple de code suivant montre le constructeur par défaut d'une classe Ribbon dans un projet qui cible [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou une version ultérieure.

    ```vb
    Public Sub New()
        MyBase.New(Globals.Factory.GetRibbonFactory())
        InitializeComponent()
    End Sub
    ```

    ```csharp
    public Ribbon1()
        : base(Globals.Factory.GetRibbonFactory())
    {
        InitializeComponent();
    }
    ```

3. Dans la méthode `InitializeComponent`, modifiez tout code qui construit un contrôle de ruban pour que le code utilise à la place l'une des méthodes d'assistance de l'objet <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory>.

    > [!NOTE]
    > Dans les projets Visual C#, vous devez développer la zone nommée `Component Designer generated code` pour voir la méthode `InitializeComponent`.

     Par exemple, supposons que votre fichier contienne la ligne de code suivante qui instancie un <xref:Microsoft.Office.Tools.Ribbon.RibbonButton> nommé `button1` dans un projet qui cible .NET Framework 3.5.

    ```vb
    Me.button1 = New Microsoft.Office.Tools.Ribbon.RibbonButton()
    ```

    ```csharp
    this.button1 = new Microsoft.Office.Tools.Ribbon.RibbonButton();
    ```

     Dans un projet qui cible [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou une version ultérieure, vous devez utiliser le code suivant à la place.

    ```vb
    Me.button1 = Me.Factory.CreateRibbonButton()
    ```

    ```csharp
    this.button1 = this.Factory.CreateRibbonButton();
    ```

     Pour obtenir la liste complète des méthodes d’assistance pour les contrôles du ruban, consultez [instancier des contrôles de ruban](#ribboncontrols).

4. Dans les projets Visual C#, modifiez les lignes de code de la méthode `InitializeComponent` qui utilisent un délégué <xref:System.EventHandler%601> pour utiliser un délégué de ruban spécifique à la place.

     Par exemple, supposons que votre fichier contienne la ligne de code suivante qui gère l'événement <xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click> dans un projet qui cible .NET Framework 3.5.

    \<CodeContentPlaceHolder > 8</CodeContentPlaceHolder> dans un projet qui cible le [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou version ultérieure, vous devez utiliser le code suivant à la place.

    \<CodeContentPlaceHolder > 9</CodeContentPlaceHolder> pour obtenir une liste complète des délégués du ruban, consultez [gérer les événements du ruban](#ribbonevents).

5. Dans les projets Visual Basic, localisez la classe `ThisRibbonCollection` à la fin du fichier. Modifiez la déclaration de cette classe pour qu'elle n'hérite plus de `Microsoft.Office.Tools.Ribbon.RibbonReadOnlyCollection`.

## <a name="ribboncontrols"></a>Instancier des contrôles de ruban
 Vous devez modifier tout code qui instancie dynamiquement des contrôles de ruban. Dans les projets qui ciblent .NET Framework 3.5, les contrôles de ruban sont des classes que vous pouvez instancier directement dans certains scénarios. Dans les projets qui ciblent [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou une version ultérieure, ces contrôles sont des interfaces que vous ne pouvez pas instancier directement. Vous devez créer les contrôles à l'aide des méthodes fournies par l'objet <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory>.

 Il existe deux façons d'accéder à l'objet <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory> :

- À l’aide de la propriété Factory de la classe Ribbon. Utilisez cette approche basée sur le code dans votre classe Ribbon.

- À l'aide de la méthode `Globals.Factory.GetRibbonFactory`. Utilisez cette approche basée sur le code hors de votre classe Ribbon. Pour plus d’informations sur la classe Globals, consultez [accès global aux objets dans les projets Office](../vsto/global-access-to-objects-in-office-projects.md).

  L'exemple de code suivant montre comment créer <xref:Microsoft.Office.Tools.Ribbon.RibbonButton> dans une classe Ribbon, au sein d'un projet qui cible [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou une version ultérieure.

\<CodeContentPlaceHolder > 10</CodeContentPlaceHolder> \<CodeContentPlaceHolder > 11</CodeContentPlaceHolder> le tableau suivant répertorie les contrôles que vous pouvez créer par programmation et la méthode à utiliser pour créer les contrôles dans les projetsquiciblent[!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou version ultérieure.

|Contrôle|Méthode RibbonFactory à utiliser dans les projets [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] et version ultérieure|
|-------------| - |
|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonButton%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonButtonGroup>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonButtonGroup%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonCheckBox%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonComboBox%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonDialogLauncher>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonDialogLauncher%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown>:|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonDropDown%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonDropDownItem>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonDropDownItem%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonEditBox%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonGallery>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonGallery%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonGroup>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonGroup%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonLabel>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonLabel%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonManager>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonManager%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonMenu%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonSeparator>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonSeparator%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonSplitButton%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonTab>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonTab%2A>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton>|<xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.CreateRibbonToggleButton%2A>|

## <a name="ribbonevents"></a>Gérer les événements de ruban
 Vous devez modifier tout code qui gère les événements liés aux contrôles de ruban. Dans les projets qui ciblent .NET Framework 3.5, ces événements sont gérés par le délégué <xref:System.EventHandler%601> générique. Dans les projets qui ciblent [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou une version ultérieure, ces événements sont désormais gérés par d'autres délégués.

 Le tableau suivant répertorie les événements de ruban et les délégués qui leur sont associés dans les projets qui ciblent [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou une version ultérieure.

|événement|Délégué à utiliser dans les projets [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] et version ultérieure|
|-----------| - |
|Événement <xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.LoadImage> dans une classe Ribbon générée|<xref:Microsoft.Office.Tools.Ribbon.RibbonLoadImageEventHandler>|
|<xref:Microsoft.Office.Tools.Ribbon.OfficeRibbon.Load>|<xref:Microsoft.Office.Tools.Ribbon.RibbonUIEventHandler>|
|<xref:Microsoft.Office.Tools.Ribbon.RibbonButton.Click><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonCheckBox.Click><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.ItemsLoading><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.TextChanged><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.ButtonClick><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.ItemsLoading><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.SelectionChanged><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonEditBox.TextChanged><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ButtonClick><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.Click><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ItemsLoading><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonGroup.DialogLauncherClick><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu.ItemsLoading><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton.Click><br /><br /> <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click>|<xref:Microsoft.Office.Tools.Ribbon.RibbonControlEventHandler>|

## <a name="set-the-position-of-a-ribbon-component-programmatically"></a>Définir la position d’un composant de ruban par programmation
 Vous devez modifier tout code qui définit la position des groupes, onglets ou contrôles de ruban. Dans les projets qui ciblent .NET Framework 3.5, vous pouvez utiliser les méthodes `AfterOfficeId` et `BeforeOfficeId` de la classe `Microsoft.Office.Tools.Ribbon.RibbonPosition` statique pour assigner la propriété `Position` d'un groupe, d'un onglet ou d'un contrôle. Dans les projets qui ciblent [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ou une version ultérieure, vous devez accéder à ces méthodes à l'aide de la propriété <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory.RibbonPosition%2A> fournie par l'objet <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory>.

 Il existe deux façons d'accéder à l'objet <xref:Microsoft.Office.Tools.Ribbon.RibbonFactory> :

- À l'aide de la propriété `Factory` de la classe Ribbon. Utilisez cette approche basée sur le code dans votre classe Ribbon.

- À l'aide de la méthode `Globals.Factory.GetRibbonFactory`. Utilisez cette approche basée sur le code hors de votre classe Ribbon. Pour plus d’informations sur la classe Globals, consultez [accès global aux objets dans les projets Office](../vsto/global-access-to-objects-in-office-projects.md).

  L'exemple de code suivant montre comment définir la propriété `Position` d'un onglet dans une classe Ribbon, au sein d'un projet qui cible .NET Framework 3.5.

```vb
Me.tab1.Position = RibbonPosition.AfterOfficeId("TabHome")
```

```csharp
this.tab1.Position = RibbonPosition.AfterOfficeId("TabHome");
```

 L’exemple de code suivant montre la même tâche dans un projet qui cible [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)].

```vb
Me.tab1.Position = Me.Factory.RibbonPosition.AfterOfficeId("TabHome")
```

```csharp
this.tab1.Position = this.Factory.RibbonPosition.AfterOfficeId("TabHome");
```

## <a name="see-also"></a>Voir aussi
- [Migrer des solutions Office vers le .NET Framework 4 ou version ultérieure](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)
- [Concepteur de ruban](../vsto/ribbon-designer.md)
