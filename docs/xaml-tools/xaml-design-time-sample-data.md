---
title: Utiliser des exemples de données au moment du design avec les Concepteur XAML dans Visual Studio
description: Découvrez comment utiliser des exemples de données au moment du design en XAML.
ms.date: 06/01/2021
ms.topic: conceptual
author: alihamie
ms.author: tglee
manager: jmartens
monikerRange: vs-2019
ms.openlocfilehash: 8303e1150db7c12c404e8f67bce52418fbd05b9d
ms.sourcegitcommit: ab5735d64a6ad7aecabf5d6df159888e3246bff5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2021
ms.locfileid: "111433790"
---
# <a name="use-design-time-sample-data-with-the-xaml-designer-in-visual-studio"></a>Utiliser des exemples de données au moment du design avec les Concepteur XAML dans Visual Studio

Certains contrôles dépendant des données, tels que ListView, ListBox ou DataGrid, sont difficiles à visualiser sans données. Dans ce document, nous allons passer en revue une nouvelle approche qui permet aux développeurs qui travaillent sur des projets **.net Core WPF** ou des projets de **.NET Framework WPF** avec le nouveau concepteur d’activer des exemples de données dans ces contrôles. 

## <a name="sample-data-feature-basics"></a>Notions de base des fonctionnalités des exemples de données

Les exemples de données sont destinés uniquement à la visualisation au moment du design, ce qui signifie qu’ils apparaissent uniquement dans le concepteur XAML, et non dans l’application en cours d’exécution. En tant que tel, il est appliqué à la version au moment du design de la propriété ItemsSource `d:ItemsSource` . Les exemples de données ont besoin de l’espace de noms au moment du design pour fonctionner. Pour commencer, ajoutez les lignes de code suivantes à l’en-tête de votre document XAML s’ils ne sont pas déjà présents :

> [!NOTE]
> Visitez [les propriétés au moment du design XAML](../xaml-tools/xaml-designtime-data.md) pour en savoir plus sur les propriétés au moment du design en XAML.

```xml
xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
mc:Ignorable="d"
```

Après avoir ajouté les espaces de noms, vous pouvez utiliser `d:ItemsSource="{d:SampleData}"` pour activer des exemples de données dans votre ListView, ListBox ou DataGrid. Par exemple :

```xml
<DataGrid d:ItemsSource="{d:SampleData}"/>
```

[![Exemples de données avec DataGrid](media\xaml-sample-data-empty-datagrid.png "Exemple de données activées sur un DataGrid")](media\xaml-sample-data-empty-datagrid.png#lightbox)

Dans cet exemple, sans `d:ItemsSource="{d:SampleData}"` le concepteur XAML afficherait un DataGrid vide. Au lieu de `d:SampleData` cela, il affiche à présent les exemples de données générés par défaut.

Par défaut, cinq éléments sont affichés. Toutefois, vous pouvez utiliser la propriété **ItemCount** pour spécifier le nombre d’éléments que vous souhaitez afficher. par exemple : `d:ItemsSource="{d:SampleData ItemCount=2}"`

## <a name="sample-data-works-with-datatemplates"></a>Les exemples de données fonctionnent avec des DataTemplate

Les exemples de données fonctionnent pour les contrôles ListBox, ListView ou DataGrid lorsque vous utilisez des modèles de données. La fonctionnalité exemples de données analyse le DataTemplate et tente de générer les données appropriées pour celui-ci. Les exemples de données ne seront générés que pour les éléments des DataTemplate qui utilisent des liaisons. Des exemples de données seront générés même si les liaisons n’ont pas encore de source.
Par exemple :

```xml
<ListView d:ItemsSource="{d:SampleData ItemCount=3}">
     <ListView.ItemTemplate>
        <DataTemplate>
            <StackPanel Orientation="Horizontal">
                <Image Width="50" Source="{Binding ProfilePicture}"/>
                <StackPanel Orientation="Vertical">
                    <TextBlock Text="{Binding FirstName}" Margin="5"/>
                    <Label Content="{Binding LastName}"/>
                </StackPanel>
            </StackPanel>
        </DataTemplate>
    </ListView.ItemTemplate>
</ListView>
```

[![Exemple de liste de données avec un DataTemplate](media\xaml-sample-data-templated-listview.png "Exemples de données utilisés dans un ListView avec un DataTemplate")](media\xaml-sample-data-templated-listview.png#lightbox)

## <a name="enable-sample-data-with-suggested-actions"></a>Activer les exemples de données avec les actions suggérées

Pour activer ou désactiver facilement les exemples de données d’un contrôle à partir du concepteur, vous pouvez utiliser la fonctionnalité actions suggérées. Les actions suggérées sont une ampoule sur le concepteur qui s’affiche en haut à droite lorsque vous sélectionnez un contrôle. Vous pouvez activer les exemples de données en sélectionnant votre contrôle, en cliquant sur l’ampoule, puis en cliquant sur activé `Show Sample Data` . Par exemple :

[![Actions suggérées pour les exemples de données](media\xaml-sample-data-suggested-actions.png "Activer les exemples de données avec les actions suggérées")](media\xaml-sample-data-suggested-actions.png#lightbox)

## <a name="sample-data-with-ivalueconverters"></a>Exemples de données avec IValueConverters 

Les convertisseurs ne sont pas entièrement pris en charge par la fonctionnalité exemples de données. Toutefois, vous pouvez faire en sorte qu’il fonctionne de l’une des façons suivantes :
- Assurez-vous que votre `Convert` fonction peut gérer un scénario dans lequel la valeur est déjà votre TargetType.

- Implémentez la `ConvertBack` fonction qui reconvertira votre valeur vers le type d’origine. 

## <a name="troubleshooting"></a>Dépannage

Si vos exemples de données n’affichent rien ou ne parvient pas à afficher le type correct, vous pouvez essayer d’actualiser le concepteur ou de fermer et rouvrir la page.

Si vous rencontrez un problème qui n’est pas mentionné dans cette section ou si vous ne pouvez pas le résoudre en actualisant la page, faites-le nous savoir en utilisant l’outil [signaler un problème](../ide/how-to-report-a-problem-with-visual-studio.md) .

### <a name="requirements"></a>Spécifications

- Les exemples de données requièrent Visual Studio 2019 version [16,10](/visualstudio/releases/2019/release-notes-v16.10) ou ultérieure.

- Prend en charge les projets de bureau Windows qui ciblent Windows Presentation Foundation (WPF) pour .NET Core ou .NET Framework lors de l’utilisation du nouveau concepteur. Pour activer le nouveau concepteur pour .NET Framework accédez à outils > options > environnement > fonctionnalités préliminaires, sélectionnez nouveau Concepteur XAML WPF pour .NET Framework, puis redémarrez Visual Studio.

## <a name="see-also"></a>Voir aussi

- [Propriétés au moment du design XAML](../xaml-tools/xaml-designtime-data.md)
- [XAML dans les applications WPF](/dotnet/framework/wpf/advanced/xaml-in-wpf)
- [XAML dans les applications UWP](/windows/uwp/xaml-platform/xaml-overview)
- [XAML dans les applications Xamarin.Forms](/xamarin/xamarin-forms/xaml/)