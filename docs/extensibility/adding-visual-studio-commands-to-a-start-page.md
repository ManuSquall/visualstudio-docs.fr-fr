---
title: Ajout de commandes de Visual Studio à une Page de démarrage | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- start page commands
- vs:VSCommands
ms.assetid: a8e2765c-cfb5-47b5-a414-6e48b434e0c2
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 87a5e6d29877efb857b846a7b3fac5f19f790d7c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
ms.locfileid: "31101792"
---
# <a name="adding-visual-studio-commands-to-a-start-page"></a>Ajout de commandes de Visual Studio à une Page de démarrage
Lorsque vous créez une page de démarrage personnalisée, vous pouvez ajouter des commandes de Visual Studio à celui-ci. Ce document décrit les différentes façons de lier des commandes de Visual Studio à des objets XAML dans une page de démarrage.  
  
 Pour plus d’informations sur les commandes en XAML, consultez [vue d’ensemble de l’exécution des commandes](/dotnet/framework/wpf/advanced/commanding-overview)  
  
## <a name="adding-commands-from-the-command-well"></a>Ajout de commandes à partir de la commande bien  
 La page de démarrage créé dans [création d’une Page de démarrage personnalisée](../extensibility/creating-a-custom-start-page.md) ajouté le <xref:Microsoft.VisualStudio.PlatformUI?displayProperty=fullName> et <xref:Microsoft.VisualStudio.Shell?displayProperty=fullName> espaces de noms, comme suit.  
  
```  
xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"  
```  
  
 Ajoutez un autre espace de noms pour Microsoft.VisualStudio.Shell à partir de l’assembly Microsoft.VisualStudio.Shell.Immutable.11.0.dll. (Vous devrez peut-être ajouter une référence à cet assembly dans votre projet.)  
  
```xml  
xmlns:vscom="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.Immutable.11.0"  
```  
  
 Vous pouvez utiliser la `vscom:` alias pour lier des commandes de Visual Studio à XAML contrôle sur la page en définissant le <xref:System.Windows.Controls.Primitives.ButtonBase.Command%2A> propriété du contrôle à `vscom:VSCommands.ExecuteCommand`. Vous pouvez ensuite définir le <xref:System.Windows.Controls.Primitives.ButtonBase.CommandParameter%2A> propriété le nom de la commande à exécuter, comme indiqué dans l’exemple suivant.  
  
```xml  
<Button Name="btnNewProj" Content="New Project"   
    Command="{x:Static vscom:VSCommands.ExecuteCommand}"  
    CommandParameter="File.NewProject" >  
</Button>  
```  
  
> [!NOTE]
>  Le `x:` alias, qui fait référence au schéma XAML, est requis au début de toutes les commandes.  
  
 Vous pouvez définir la valeur de la `Command` propriété à toutes les commandes qui sont accessibles à partir de la **commande** fenêtre. Pour obtenir la liste des commandes disponibles, consultez [Visual Studio Command Aliases](../ide/reference/visual-studio-command-aliases.md).  
  
 Si la commande pour ajouter nécessite un paramètre supplémentaire, vous pouvez l’ajouter à la valeur de la `CommandParameter` propriété. Paramètres distincts à partir des commandes à l’aide des espaces, comme indiqué dans l’exemple suivant.  
  
```xml  
<Button Content="Web Search"   
        Command="{x:Static vscom:VSCommands.ExecuteCommand}"  
        CommandParameter="View.WebBrowser www.bing.com" />  
```  
  
### <a name="calling-extensions-from-the-command-well"></a>Appel des Extensions à partir de la commande bien  
 Vous pouvez appeler des commandes à partir des VSPackages à l’aide de la même syntaxe qui est utilisée pour appeler d’autres commandes de Visual Studio. Par exemple, si un VSPackage installé ajoute un **Page d’accueil** commande le **vue** menu, vous pouvez appeler cette commande en définissant `CommandParameter` à `View.HomePage`.  
  
> [!NOTE]
>  Si vous appelez une commande qui est associée à un VSPackage, le package doit être chargé lors de la commande est appelée.  
  
## <a name="adding-commands-from-assemblies"></a>Ajout de commandes à partir des assemblys  
 Pour appeler une commande à partir d’un assembly ou d’accéder au code dans un VSPackage qui n’est pas associé à une commande de menu, vous devez créer un alias pour l’assembly, puis appelez l’alias.  
  
#### <a name="to-call-a-command-from-an-assembly"></a>Pour appeler une commande à partir d’un assembly  
  
1.  Dans votre solution, ajoutez une référence à l’assembly.  
  
2.  En haut du fichier StartPage.xaml, ajoutez une directive d’espace de noms pour l’assembly, comme indiqué dans l’exemple suivant.  
  
    ```xml  
    xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"  
    ```  
  
3.  Appelez la commande en définissant le `Command` propriété d’un objet XAML, comme indiqué dans l’exemple suivant.  
  
     XAML  
  
    ```  
    <vs:Button Text="Hide me" Command="{x:Static vsc:HideControl}" .../>  
    ```  
  
> [!NOTE]
>  Vous devez copier votre assembly et collez-le dans... \\ *Dossier d’installation de visual Studio*\Common7\IDE\PrivateAssemblies\ pour vous assurer qu’il est chargé avant qu’elle est appelée.  
  
## <a name="adding-commands-with-the-dte-object"></a>Ajout de commandes avec l’objet DTE  
 Vous pouvez accéder à l’objet DTE à partir d’une Page de démarrage, à la fois dans le balisage et dans le code.  
  
 Dans le balisage, vous pouvez y accéder à l’aide de la [Extension de balisage de liaison](/dotnet/framework/wpf/advanced/binding-markup-extension) syntaxe pour appeler le <xref:EnvDTE.DTE> objet. Vous pouvez utiliser cette approche pour lier à des propriétés simples telles que celles qui retournent des collections, mais vous ne pouvez pas lier à des méthodes ou des services. L’exemple suivant montre un <xref:System.Windows.Controls.TextBlock> contrôle qui est lié à la <xref:EnvDTE._DTE.Name%2A> propriété et un <xref:System.Windows.Controls.ListBox> contrôle qui énumère la <xref:EnvDTE.Window.Caption%2A> propriétés de la collection retournée par la <xref:EnvDTE._DTE.Windows%2A> propriété.  
  
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
  
 Pour obtenir un exemple, consultez [procédure pas à pas : enregistrement des paramètres utilisateur sur une Page de démarrage](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Ajout d’un contrôle utilisateur à la page de démarrage](../extensibility/adding-user-control-to-the-start-page.md)