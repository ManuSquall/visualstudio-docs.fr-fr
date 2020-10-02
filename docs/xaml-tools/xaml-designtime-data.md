---
title: Utiliser des données au moment du design avec les Concepteur XAML dans Visual Studio
description: Découvrez comment utiliser des données au moment du design en XAML.
ms.date: 09/29/2020
ms.topic: overview
author: alihamie
ms.author: tglee
manager: jillfra
monikerRange: vs-2019
ms.openlocfilehash: 6957c1c7d64918e91a95bf569c210c146fec1339
ms.sourcegitcommit: c025a5e2013c4955ca685092b13e887ce64aaf64
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2020
ms.locfileid: "91659412"
---
# <a name="use-design-time-data-with-the-xaml-designer-in-visual-studio"></a>Utiliser des données au moment du design avec les Concepteur XAML dans Visual Studio

Certaines dispositions sont difficiles à visualiser sans données. Dans ce document, nous allons examiner une des approches que les développeurs qui travaillent sur des projets de bureau peuvent utiliser pour simuler des données dans le concepteur XAML. Cette approche est effectuée à l’aide de l’espace de noms « d : » pouvant être ignoré. Grâce à cette approche, vous pouvez ajouter rapidement des données au moment de la conception à vos pages ou contrôles sans avoir à créer un ViewModel factice complet, ou simplement tester la manière dont une modification de propriété peut affecter votre application sans vous préoccuper de l’impact de ces modifications sur vos versions release. Toutes les données d : ne sont utilisées que par le Concepteur XAML et aucune valeur d’espace de noms ignorée n’est compilée dans l’application.

> [!NOTE]
> Si vous utilisez Xamarin. Forms, consultez [données au moment de la conception de Xamarin. Forms](/xamarin/xamarin-forms/xaml/xaml-previewer/design-time-data)

## <a name="design-time-data-basics"></a>Notions de base des données au moment du design

Les données au moment de la conception sont des données fictives que vous définissez pour faciliter la visualisation de vos contrôles dans le Concepteur XAML. Pour commencer, ajoutez les lignes de code suivantes à l’en-tête de votre document XAML s’ils ne sont pas déjà présents :

```xml 
xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
mc:Ignorable="d"
```

Après avoir ajouté les espaces de noms, vous pouvez placer `d:` devant n’importe quel attribut ou contrôle pour les afficher uniquement dans le concepteur XAML, mais pas au moment de l’exécution.

Par exemple, vous pouvez ajouter du texte à un TextBlock qui est généralement lié à des données.

```xml
<TextBlock Text="{Binding Name}" d:Text="Name!" />
```

[![Données au moment du design avec du texte dans un TextBlock](media\xaml-design-time-textblock.png "Données au moment du design avec texte d’une étiquette")](media\xaml-design-time-textblock.png#lightbox)

Dans cet exemple, sans `d:Text` , le concepteur XAML n’affichera rien pour le TextBlock. Au lieu de cela, il affiche « Name ! » où le TextBlock aura des données réelles au moment de l’exécution.

Vous pouvez utiliser `d:` avec des attributs pour tout contrôle .net Core UWP ou WPF, comme les couleurs, les tailles de police et l’espacement. Vous pouvez même l’ajouter au contrôle lui-même.

```xml
<d:Button Content="Design Time Button" />
```

[![Données au moment du design avec un contrôle Button](media\xaml-design-time-button.png "Données au moment du design avec un contrôle Button")](media\xaml-design-time-button.png#lightbox)

Dans cet exemple, le bouton s’affiche uniquement au moment du Design. Utilisez cette méthode pour placer un espace réservé dans pour un contrôle personnalisé ou pour tester différents contrôles. Tous les `d:` attributs et les contrôles seront ignorés lors de l’exécution.

## <a name="preview-images-at-design-time"></a>Aperçu des images au moment du design

Vous pouvez définir une source au moment de la conception pour les images qui sont liées à la page ou chargées dans dynamiquement. Ajoutez l’image que vous souhaitez afficher dans le Concepteur XAML à votre projet. Vous pouvez ensuite afficher cette image dans le Concepteur XAML au moment de la conception :

```xml
<Image Source={Binding ProfilePicture} d:Source="DesignTimePicture.jpg" />
```

> [!NOTE]
> L’image dans cet exemple doit exister dans la solution.

## <a name="design-time-data-for-listviews"></a>Données au moment du design pour les ListView

Les ListViews sont un moyen couramment utilisé pour afficher des données dans votre application de bureau. Toutefois, ils sont difficiles à visualiser sans aucune donnée. Vous pouvez utiliser cette fonctionnalité pour créer un ItemSource de données au moment de la conception en ligne. Le Concepteur XAML affiche ce qui se trouve dans ce tableau dans votre ListView au moment du Design. Il s’agit d’un exemple pour WPF .NET Core. Pour utiliser le type System : String, veillez à inclure `xmlns:system="clr-namespace:System;assembly=mscorlib` dans votre en-tête XAML.

```xml
<StackPanel>
    <ListView ItemsSource="{Binding Items}">
        <d:ListView.ItemsSource>
            <x:Array Type="{x:Type system:String}">
                <system:String>Item One</system:String>
                <system:String>Item Two</system:String>
                <system:String>Item Three</system:String>
            </x:Array>
        </d:ListView.ItemsSource>
    <ListView.ItemTemplate>
        <DataTemplate>
            <TextBlock Text="{Binding ItemName}" d:Text="{Binding .}" />
        </DataTemplate>
    </ListView.ItemTemplate>
   </ListView>
</StackPanel>
```

[![Données au moment du design avec un ListView](media\xaml-design-time-listview-strings.png "Données au moment du design avec un ListView")](media\xaml-design-time-listview-strings.png#lightbox)

L’exemple précédent montre un ListView avec trois TextBlocks dans le Concepteur XAML.

Vous pouvez également créer un tableau d’objets de données. Par exemple, les propriétés publiques d’un `City` objet de données peuvent être construites en tant que données au moment de la conception.

```csharp
namespace Cities.Models
{
    public class City
    {
        public string Name { get; set; }
        public string Country { get; set; }
    }
}
```

Pour utiliser la classe en XAML, vous devez importer l’espace de noms dans le nœud racine.

```xaml
xmlns:models="clr-namespace:Cities.Models"
```

```xml
<StackPanel>
    <ListView ItemsSource="{Binding Items}">
        <d:ListView.ItemsSource>
            <x:Array Type="{x:Type models:City}">
                <models:City Name="Seattle" Country="United States"/>
                <models:City Name="London" Country="United Kingdom"/>
                <models:City Name="Panama City" Country="Panama"/>
            </x:Array>
        </d:ListView.ItemsSource>
        <ListView.ItemTemplate>
            <DataTemplate>
                 <StackPanel Orientation="Horizontal" >
                    <TextBlock Text="{Binding Name}" Margin="0,0,5,0" />
                    <TextBlock Text="{Binding Country}" />
                 </StackPanel>
            </DataTemplate>
        </ListView.ItemTemplate>
    </ListView>
</StackPanel>
```

[![Modèle réel dans les données au moment du design avec un ListView](media\xaml-design-time-listview-models.png "Données de conception de modèle réelles avec un ListView")](media\xaml-design-time-listview-models.png#lightbox)

L’avantage ici est que vous pouvez lier vos contrôles à une version statique au moment du design de votre modèle.

## <a name="troubleshooting"></a>Dépannage

Si vous rencontrez un problème qui n’est pas mentionné dans cette section, faites-le nous savoir en utilisant l’outil [signaler un problème](../ide/how-to-report-a-problem-with-visual-studio.md) .

### <a name="requirements"></a>Spécifications

- Les données au moment du design nécessitent Visual Studio 2019 version [16,7](/visualstudio/releases/2019/release-notes) ou ultérieure.

- Prend en charge les projets de bureau Windows ciblant Windows Presentation Foundation (WPF) pour .NET Core et UWP. Cette fonctionnalité est également disponible pour .NET Framework si la fonctionnalité « nouvelle Concepteur XAML WPF pour .NET Framework » est activée.

- À compter de Visual Studio 2019 version 16,7, cette fonctionnalité fonctionne avec tous les contrôles intégrés des frameworks WPF et UWP. La prise en charge des contrôles tiers est désormais disponible dans la version préliminaire de 16,8.

### <a name="the-xaml-designer-stopped-working"></a>La Concepteur XAML a cessé de fonctionner

Essayez de fermer et de rouvrir le fichier XAML, puis de nettoyer et de reconstruire votre projet.

## <a name="see-also"></a>Voir aussi

- [Données au moment de la conception avec le générateur d’aperçu Xamarin. Forms](/xamarin/xamarin-forms/xaml/xaml-Designer/design-time-data/)
- [XAML dans les applications WPF](/dotnet/framework/wpf/advanced/xaml-in-wpf)
- [XAML dans les applications UWP](/windows/uwp/xaml-platform/xaml-overview)
- [XAML dans les applications Xamarin.Forms](/xamarin/xamarin-forms/xaml/)