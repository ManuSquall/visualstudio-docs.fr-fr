---
title: Code source L2DBForm.xaml
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: sample
ms.assetid: 624e96d4-6d27-4195-8ac2-2f3835f6c57e
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bd9f7601a7e2a24ec41a12d194aac65445c6d159
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31924325"
---
# <a name="l2dbformxaml-source-code"></a>Code source L2DBForm.xaml

Cette rubrique contient et décrit le fichier source XAML pour [WPF Data Binding Using LINQ to XML Example](../designers/wpf-data-binding-using-linq-to-xml-example.md), L2DBForm.xaml.

## <a name="overall-ui-structure"></a>Structure globale d'interface utilisateur

Comme c'est généralement le cas pour un projet WPF, ce fichier contient un élément parent, un élément XML <xref:System.Windows.Window> associé à la classe dérivée `L2XDBFrom` dans l'espace de noms `LinqToXmlDataBinding` .

La zone cliente est contenue dans un objet <xref:System.Windows.Controls.StackPanel> auquel est affecté un arrière-plan bleu clair. Ce volet contient quatre sections d'interface utilisateur <xref:System.Windows.Controls.DockPanel> séparées par des barres <xref:System.Windows.Controls.Separator> . L'objectif de ces sections est décrit dans les **Remarques** de la [rubrique précédente](../designers/walkthrough-linqtoxmldatabinding-example.md).

Chaque section contient une étiquette qui l'identifie. Dans les deux premières sections, cette étiquette est pivotée de 90 degrés par le biais d'une propriété <xref:System.Windows.FrameworkElement.LayoutTransform%2A>. Le reste de la section contient des éléments d’interface utilisateur adaptés à l’objectif de cette section : blocs de texte, zones de texte, boutons, etc. Parfois, un objet <xref:System.Windows.Controls.StackPanel> enfant est utilisé pour aligner ces contrôles enfants.

## <a name="window-resource-section"></a>Section de ressources de fenêtre

La balise `<Window.Resources>` d'ouverture sur la ligne 9 indique le début de la section de ressources de fenêtre. Cette section se termine par la balise de fermeture sur la ligne 35.

La balise `<ObjectDataProvider>` , qui s'étend de la ligne 11 à la ligne 25, déclare un objet <xref:System.Windows.Data.ObjectDataProvider>, nommé `LoadedBooks`, qui utilise un objet <xref:System.Xml.Linq.XElement> comme source. Le <xref:System.Xml.Linq.XElement> est initialisé par l’analyse d’un document XML incorporé (un élément `CDATA`). Notez que les espaces blancs sont conservés lors de la déclaration et de l’analyse du document XML incorporé. Cela est dû au fait que le contrôle <xref:System.Windows.Controls.TextBlock>, qui est utilisé pour afficher le code XML brut, n’a pas de fonctionnalités spéciales de mise en forme XML.

Pour finir, un objet <xref:System.Windows.DataTemplate> nommé `BookTemplate` est défini sur les lignes 28 à 34. Ce modèle est utilisé pour afficher les entrées dans la section **Book List** de l’interface utilisateur. Il utilise les propriétés dynamiques LINQ to XML et de liaison de données pour récupérer l'ID de livre et le nom de livre par le biais des affectations suivantes :

```
Text="{Binding Path=Attribute[id].Value}"Text="{Binding Path=Value}"
```

## <a name="data-binding-code"></a>Code de liaison de données

En plus de l'élément <xref:System.Windows.DataTemplate> , la liaison de données est utilisée à d'autres emplacements de ce fichier.

Dans la balise `<StackPanel>` d'ouverture sur la ligne 38, le fournisseur de données <xref:System.Windows.FrameworkElement.DataContext%2A> est affecté à la propriété `LoadedBooks` de ce volet.

```
DataContext="{Binding Source={StaticResource LoadedBooks}}
```

La définition du contexte des données permet (sur la ligne 46) à l’objet <xref:System.Windows.Controls.TextBlock> nommé `tbRawXml` d’afficher le code XML brut en effectuant la liaison à la propriété `Xml` de ce fournisseur de données :

```
Text="{Binding Path=Xml}"
```

L'objet <xref:System.Windows.Controls.ListBox> dans la section d'interface utilisateur **Book List** , sur les lignes 58 à 62, définit le modèle pour ses éléments d'affichage au `BookTemplate` défini dans la section de ressources de fenêtre :

```
ItemTemplate ="{StaticResource BookTemplate}"
```

Ensuite, sur les lignes 59 à 62, les valeurs réelles des livres sont liées à cette zone de texte :

```
<ListBox.ItemsSource>
    <Binding Path="Elements[{http://www.mybooks.com}book]"/>
</ListBox.ItemsSource>
```

La troisième section d'interface utilisateur, **Edit Selected Book**, lie d'abord la propriété <xref:System.Windows.FrameworkElement.DataContext%2A> de l'objet <xref:System.Windows.Controls.StackPanel> parent à l'élément actuellement sélectionné dans la section d'interface utilisateur **Book List** (ligne 82) :

```
DataContext="{Binding ElementName=lbBooks, Path=SelectedItem}"
```

Elle utilise ensuite la liaison de données bidirectionnelle, de sorte que les valeurs actuelles des éléments de livre soient affichées dans et mises à jour à partir des deux zones de texte de ce volet. La liaison de données aux propriétés dynamiques est similaire à celle utilisée dans le modèle de données `BookTemplate` :

```
Text="{Binding Path=Attribute[id].Value}"...Text="{Binding Path=Value}"
```

La dernière section de l’interface utilisateur, **Add New Book**, n’utilise pas la liaison de données dans son code XAML. Au lieu de cela, la liaison de données est dans le code de son gestionnaire d’événements, dans le fichier *L2DBForm.xaml.cs*.

## <a name="example"></a>Exemple

### <a name="description"></a>Description

> [!NOTE]
> Nous vous recommandons de copier le code ci-dessous dans un éditeur de code, tel que l'éditeur de code source C# fourni avec Visual Studio, afin de faciliter le suivi des numéros de lignes.

### <a name="code"></a>Code

```xml
<Window x:Class="LinqToXmlDataBinding.L2XDBForm"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:system="clr-namespace:System;assembly=mscorlib"
    xmlns:xlinq="clr-namespace:System.Xml.Linq;assembly=System.Xml.Linq"
    xmlns:local="clr-namespace:LinqToXmlDataBinding"
    Title="WPF Data Binding using LINQ-to-XML" Height="665" Width="500" ResizeMode="NoResize">

    <Window.Resources>
        <!-- Books provider and inline data -->
        <ObjectDataProvider x:Key="LoadedBooks" ObjectType="{x:Type xlinq:XElement}" MethodName="Parse">
            <ObjectDataProvider.MethodParameters>
                <system:String xml:space="preserve">
<![CDATA[
<books xmlns="http://www.mybooks.com">
  <book id="0">book zero</book>
  <book id="1">book one</book>
  <book id="2">book two</book>
  <book id="3">book three</book>
</books>
]]>
                </system:String>
                <xlinq:LoadOptions>PreserveWhitespace</xlinq:LoadOptions>
            </ObjectDataProvider.MethodParameters>
        </ObjectDataProvider>

        <!-- Template for use in Books List listbox. -->
        <DataTemplate x:Key="BookTemplate">
            <StackPanel Orientation="Horizontal">
                <TextBlock Margin="3" Text="{Binding Path=Attribute[id].Value}"/>
                <TextBlock Margin="3" Text="-"/>
                <TextBlock Margin="3" Text="{Binding Path=Value}"/>
            </StackPanel>
        </DataTemplate>
    </Window.Resources>

    <!-- Main visual content container -->
    <StackPanel Background="lightblue" DataContext="{Binding Source={StaticResource LoadedBooks}}">
        <!-- Raw XML display section -->
        <DockPanel Margin="5">
            <Label  Background="Gray" FontSize="12" BorderBrush="Black" BorderThickness="1" FontWeight="Bold">XML
            <Label.LayoutTransform>
                <RotateTransform Angle="90"/>
            </Label.LayoutTransform>
            </Label>
            <TextBlock Name="tbRawXml" Height="200" Background="LightGray" Text="{Binding Path=Xml}" TextTrimming="CharacterEllipsis" />
        </DockPanel>

        <Separator Height="4" Margin="5" />

        <!-- List box to display all books section -->
        <DockPanel Margin="5">
            <Label  Background="Gray" FontSize="12" BorderBrush="Black" BorderThickness="1" FontWeight="Bold">Book List
                <Label.LayoutTransform>
                    <RotateTransform Angle="90"/>
                </Label.LayoutTransform>
            </Label>
            <ListBox Name="lbBooks" Height="200" Width="415" ItemTemplate ="{StaticResource BookTemplate}">
                <ListBox.ItemsSource>
                    <Binding Path="Elements[{http://www.mybooks.com}book]"/>
                </ListBox.ItemsSource>
            </ListBox>
            <Button Margin="5" DockPanel.Dock="Right" Height="30" Width ="130" Content="Remove Selected Book" Click="OnRemoveBook">
            <Button.LayoutTransform>
                <RotateTransform Angle="90"/>
            </Button.LayoutTransform>
            </Button>
        </DockPanel>

        <Separator Height="4" Margin="5" />

        <!-- Edit current selection section -->
        <DockPanel Margin="5">
            <TextBlock Margin="5" Height="30" Width="65" DockPanel.Dock="Right" Background="LightGray" TextWrapping="Wrap" TextAlignment="Center">
                    Changes are live!
                <TextBlock.LayoutTransform>
                    <RotateTransform Angle="90"/>
                </TextBlock.LayoutTransform>
            </TextBlock>
            <StackPanel>
                <Label Width="450" Background="Gray" FontSize="12" BorderBrush="Black" BorderThickness="1" HorizontalAlignment="Left" FontWeight="Bold">Edit Selected Book</Label>
                <StackPanel Margin="1" DataContext="{Binding ElementName=lbBooks, Path=SelectedItem}">
                    <StackPanel Orientation="Horizontal">
                        <Label Width="40">ID:</Label>
                        <TextBox Name="editAttributeTextBox" Width="410" Text="{Binding Path=Attribute[id].Value}">
                            <TextBox.ToolTip>
                                <TextBlock FontWeight="Bold" TextAlignment="Center">
                                    <Label>Edit the selected book ID and see it changed.</Label>
                                </TextBlock>
                            </TextBox.ToolTip>
                        </TextBox>
                    </StackPanel>
                    <StackPanel Orientation="Horizontal">
                        <Label Width="40">Value:</Label>
                        <TextBox Name="editValueTextBox" Width="410" Text="{Binding Path=Value}" Height="25">
                            <TextBox.ToolTip>
                                <TextBlock FontWeight="Bold" TextAlignment="Center">
                                    <Label>Edit the selected book Value and see it changed.</Label>
                                </TextBlock>
                            </TextBox.ToolTip>
                        </TextBox>
                    </StackPanel>
                </StackPanel>
            </StackPanel>
        </DockPanel>

        <Separator Height="4" Margin="5" />

        <!-- Add new book section -->
        <DockPanel Margin="5">
            <Button Margin="5" Height="30" DockPanel.Dock="Right" Click ="OnAddBook">Add Book
                <Button.LayoutTransform>
                    <RotateTransform Angle="90"/>
                </Button.LayoutTransform>
            </Button>
            <StackPanel>
                <Label Width="450" Background="Gray" FontSize="12" BorderBrush="Black" BorderThickness="1" HorizontalAlignment="Left" FontWeight="Bold">Add New Book</Label>
                <StackPanel Margin="1">
                    <StackPanel Orientation="Horizontal">
                        <Label Width="40">ID:</Label>
                        <TextBox Name="tbAddID" Width="410">
                            <TextBox.ToolTip>
                                <TextBlock FontWeight="Bold" TextAlignment="Center">
                                    <Label>Enter a book ID and Value pair, then click Add Book.</Label>
                                </TextBlock>
                            </TextBox.ToolTip>
                        </TextBox>
                    </StackPanel>
                    <StackPanel Orientation="Horizontal">
                        <Label Width="40">Value:</Label>
                        <TextBox Name="tbAddValue" Width="410" Height="25">
                            <TextBox.ToolTip>
                                <TextBlock FontWeight="UltraBold" TextAlignment="Center">
                                    <Label>Enter a book ID and Value pair, then click Add Book.</Label>
                                </TextBlock>
                            </TextBox.ToolTip>
                        </TextBox>
                    </StackPanel>
                </StackPanel>
            </StackPanel>
        </DockPanel>
    </StackPanel>
</Window>

```

### <a name="comments"></a>Commentaires

Pour obtenir le code source C# pour les gestionnaires d’événements associés aux éléments d’interface utilisateur WPF, consultez [L2DBForm.xaml.cs Source Code](../designers/l2dbform-xaml-cs-source-code.md).

## <a name="see-also"></a>Voir aussi

- [Procédure pas à pas : exemple LinqToXmlDataBinding](../designers/walkthrough-linqtoxmldatabinding-example.md)
- [Code source L2DBForm.xaml.cs](../designers/l2dbform-xaml-cs-source-code.md)