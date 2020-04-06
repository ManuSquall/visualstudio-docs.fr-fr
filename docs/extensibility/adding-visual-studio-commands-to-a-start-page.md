---
title: Ajout de commandes de studio visuel à une page de démarrage (fr) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- start page commands
- vs:VSCommands
ms.assetid: a8e2765c-cfb5-47b5-a414-6e48b434e0c2
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 13dd40006039209b06cc6a71760fdbaa240db4fe
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740115"
---
# <a name="add-visual-studio-commands-to-a-start-page"></a>Ajoutez des commandes Visual Studio à une page de démarrage

Lorsque vous créez une page de démarrage personnalisée, vous pouvez y ajouter des commandes Visual Studio. Ce document traite des différentes façons de lier les commandes Visual Studio aux objets XAML sur une page de démarrage.

Pour plus d’informations sur les commandes dans XAML, voir [Aperçu de commande](/dotnet/framework/wpf/advanced/commanding-overview)

## <a name="add-commands-from-the-command-well"></a>Ajouter bien les commandes de la commande

La page de démarrage créée dans <xref:Microsoft.VisualStudio.PlatformUI?displayProperty=fullName> Créer <xref:Microsoft.VisualStudio.Shell?displayProperty=fullName> une page de [démarrage personnalisée](../extensibility/creating-a-custom-start-page.md) a ajouté les espaces et les espaces de noms, comme suit.

```xml
xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"
xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"
```

Ajouter un autre namespace pour Microsoft.VisualStudio.Shell de l’assemblage *Microsoft.VisualStudio.Shell.Immutable.11.0.dll*. (Vous devrez peut-être ajouter une référence à cet assemblage dans votre projet.)

```xml
xmlns:vscom="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.Immutable.11.0"
```

Vous pouvez `vscom:` utiliser le pseudonyme pour lier les commandes Visual <xref:System.Windows.Controls.Primitives.ButtonBase.Command%2A> Studio aux commandes `vscom:VSCommands.ExecuteCommand`XAML sur la page en définissant la propriété du contrôle à . Vous pouvez ensuite <xref:System.Windows.Controls.Primitives.ButtonBase.CommandParameter%2A> définir la propriété au nom de la commande pour exécuter, comme indiqué dans l’exemple suivant.

```xml
<Button Name="btnNewProj" Content="New Project"
    Command="{x:Static vscom:VSCommands.ExecuteCommand}"
    CommandParameter="File.NewProject" >
</Button>
```

> [!NOTE]
> L’alias, `x:` qui se réfère au schéma XAML, est nécessaire au début de toutes les commandes.

 Vous pouvez définir la `Command` valeur de la propriété à n’importe quelle commande qui peut être consultée à partir de la fenêtre **de commande.** Pour une liste de commandes disponibles, voir [visual Studio alias de commande](../ide/reference/visual-studio-command-aliases.md).

 Si la commande à ajouter nécessite un paramètre supplémentaire, `CommandParameter` vous pouvez l’ajouter à la valeur de la propriété. Séparer les paramètres des commandes en utilisant des espaces, comme le montre l’exemple suivant.

```xml
<Button Content="Web Search"
        Command="{x:Static vscom:VSCommands.ExecuteCommand}"
        CommandParameter="View.WebBrowser www.bing.com" />
```

### <a name="call-extensions-from-the-command-well"></a>Étendre les extensions de commande bien
 Vous pouvez appeler les commandes de VSPackages enregistrés en utilisant la même syntaxe qui est utilisée pour appeler d’autres commandes Visual Studio. Par exemple, si un VSPackage installé ajoute une commande **de page d’accueil** au menu **View,** vous pouvez appeler cette commande en définissant `CommandParameter` `View.HomePage`à .

> [!NOTE]
> Si vous appelez une commande associée à un VSPackage, le paquet doit être chargé lorsque la commande est invoquée.

## <a name="add-commands-from-assemblies"></a>Ajouter les commandes des assemblages
 Pour appeler une commande d’une assemblée, ou pour accéder au code dans un VSPackage qui n’est pas associé à une commande de menu, vous devez créer un alias pour l’assemblage, puis appeler l’alias.

### <a name="to-call-a-command-from-an-assembly"></a>Appeler une commande d’une assemblée

1. Dans votre solution, ajoutez une référence à l’assemblage.

2. En haut du fichier *StartPage.xaml,* ajoutez une directive namespace pour l’assemblée, comme le montre l’exemple suivant.

    ```xml
    xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"
    ```

3. Invoquez la `Command` commande en définissant la propriété d’un objet XAML, comme le montre l’exemple suivant.

     Xaml

    ```
    <vs:Button Text="Hide me" Command="{x:Static vsc:HideControl}" .../>
    ```

> [!NOTE]
> Vous devez copier votre assemblage et ensuite le coller dans . \\Dossier d’installation visual studio 'Common7'IDE’PrivateAssemblies\* pour s’assurer qu’il est chargé avant qu’il ne soit appelé.

## <a name="add-commands-with-the-dte-object"></a>Ajouter des commandes avec l’objet DTE
 Vous pouvez accéder à l’objet DTE à partir d’une page de démarrage, tant en marge qu’en code.

 En balisage, vous pouvez y accéder en utilisant la <xref:EnvDTE.DTE> syntaxe [Binding Markup Extension](/dotnet/framework/wpf/advanced/binding-markup-extension) pour appeler l’objet. Vous pouvez utiliser cette approche pour vous lier à des propriétés simples telles que celles qui retournent les collections, mais vous ne pouvez pas vous lier aux méthodes ou aux services. L’exemple suivant <xref:System.Windows.Controls.TextBlock> montre un contrôle <xref:EnvDTE._DTE.Name%2A> qui se <xref:System.Windows.Controls.ListBox> lie à la <xref:EnvDTE.Window.Caption%2A> propriété, et un contrôle <xref:EnvDTE._DTE.Windows%2A> qui énumère les propriétés de la collection qui est retournée par la propriété.

```xml
<TextBlock Text="{Binding Path=DTE.Name}" FontSize="12" HorizontalAlignment="Center"/>
<ListBox ItemsSource="{Binding Path=DTE.Windows}">
    <ListBox.ItemTemplate>
        <DataTemplate>
            <TextBlock Text="{Binding Path=Caption}"/>
        </DataTemplate>
    </ListBox.ItemTemplate>
</ListBox
```

 Par exemple, voir [Procédure pas à pas : Enregistrer les paramètres de l’utilisateur sur une page de démarrage](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md).

## <a name="see-also"></a>Voir aussi

- [Ajout du contrôle utilisateur à la page de démarrage](../extensibility/adding-user-control-to-the-start-page.md)
