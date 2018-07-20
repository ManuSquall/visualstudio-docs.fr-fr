---
title: Ajout de commandes de Visual Studio à une Page de démarrage | Microsoft Docs
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
ms.openlocfilehash: 22ae9ebb5e9acb3fa1787f2af3b0fbb159c1485d
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/19/2018
ms.locfileid: "39153629"
---
# <a name="add-visual-studio-commands-to-a-start-page"></a>Ajouter des commandes de Visual Studio à une Page de démarrage
Lorsque vous créez une Page de démarrage personnalisée, vous pouvez ajouter des commandes de Visual Studio à ce dernier. Ce document présente les différentes méthodes pour lier des commandes de Visual Studio à des objets XAML sur une Page de démarrage.  
  
 Pour plus d’informations sur les commandes dans XAML, consultez [Commanding overview](/dotnet/framework/wpf/advanced/commanding-overview)  
  
## <a name="add-commands-from-the-command-well"></a>Ajouter des commandes à partir de la commande bien  
 La Page de démarrage créé dans [créer une Page de démarrage personnalisée](../extensibility/creating-a-custom-start-page.md) ajouté le <xref:Microsoft.VisualStudio.PlatformUI?displayProperty=fullName> et <xref:Microsoft.VisualStudio.Shell?displayProperty=fullName> espaces de noms, comme suit.  
  
```  
xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"  
```  
  
 Ajouter un autre espace de noms pour Microsoft.VisualStudio.Shell à partir de l’assembly *Microsoft.VisualStudio.Shell.Immutable.11.0.dll*. (Vous devrez peut-être ajouter une référence à cet assembly dans votre projet.)  
  
```xml  
xmlns:vscom="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.Immutable.11.0"  
```  
  
 Vous pouvez utiliser la `vscom:` alias pour lier des commandes de Visual Studio à XAML des contrôles de la page en définissant le <xref:System.Windows.Controls.Primitives.ButtonBase.Command%2A> propriété du contrôle à `vscom:VSCommands.ExecuteCommand`. Vous pouvez ensuite définir le <xref:System.Windows.Controls.Primitives.ButtonBase.CommandParameter%2A> propriété le nom de la commande à exécuter, comme indiqué dans l’exemple suivant.  
  
```xml  
<Button Name="btnNewProj" Content="New Project"   
    Command="{x:Static vscom:VSCommands.ExecuteCommand}"  
    CommandParameter="File.NewProject" >  
</Button>  
```  
  
> [!NOTE]
>  Le `x:` alias, ce qui fait référence au schéma XAML, est requis au début de toutes les commandes.  
  
 Vous pouvez définir la valeur de la `Command` propriété à toute commande qui est accessible à partir de la **commande** fenêtre. Pour obtenir la liste des commandes disponibles, consultez [alias de commande Visual Studio](../ide/reference/visual-studio-command-aliases.md).  
  
 Si la commande pour ajouter nécessite un paramètre supplémentaire, vous pouvez l’ajouter à la valeur de la `CommandParameter` propriété. Paramètres distinct à partir des commandes à l’aide des espaces, comme indiqué dans l’exemple suivant.  
  
```xml  
<Button Content="Web Search"   
        Command="{x:Static vscom:VSCommands.ExecuteCommand}"  
        CommandParameter="View.WebBrowser www.bing.com" />  
```  
  
### <a name="call-extensions-from-the-command-well"></a>Appeler également des extensions à partir de la commande  
 Vous pouvez appeler des commandes à partir de VSPackages enregistrés à l’aide de la même syntaxe que celle qui est utilisée pour appeler d’autres commandes de Visual Studio. Par exemple, si un VSPackage installé ajoute un **Page d’accueil** commande le **vue** menu, vous pouvez appeler cette commande en définissant `CommandParameter` à `View.HomePage`.  
  
> [!NOTE]
>  Si vous appelez une commande qui est associée à un VSPackage, le package doit être chargé lors de la commande est appelée.  
  
## <a name="add-commands-from-assemblies"></a>Ajouter des commandes provenant d’assemblys  
 Pour appeler une commande à partir d’un assembly, ou d’accéder au code dans un VSPackage qui n’est pas associé à une commande de menu, vous devez créer un alias pour l’assembly, puis appelez l’alias.  
  
### <a name="to-call-a-command-from-an-assembly"></a>Pour appeler une commande à partir d’un assembly  
  
1.  Dans votre solution, ajoutez une référence à l’assembly.  
  
2.  En haut de la *StartPage.xaml* de fichiers, ajoutez une directive d’espace de noms pour l’assembly, comme indiqué dans l’exemple suivant.  
  
    ```xml  
    xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"  
    ```  
  
3.  Appelez la commande en définissant le `Command` propriété d’un objet XAML, comme indiqué dans l’exemple suivant.  
  
     XAML  
  
    ```  
    <vs:Button Text="Hide me" Command="{x:Static vsc:HideControl}" .../>  
    ```  
  
> [!NOTE]
>  Vous devez copier votre assembly et collez-la dans *... \\{Dossier d’installation de visual Studio} \Common7\IDE\PrivateAssemblies\* pour vous assurer qu’il est chargé avant qu’elle est appelée.  
  
## <a name="add-commands-with-the-dte-object"></a>Ajouter des commandes à l’objet DTE  
 Vous pouvez accéder à l’objet DTE à partir d’une Page de démarrage, à la fois dans le balisage et code.  
  
 Dans le balisage, vous pouvez y accéder à l’aide de la [Extension de balisage Binding](/dotnet/framework/wpf/advanced/binding-markup-extension) syntaxe pour appeler le <xref:EnvDTE.DTE> objet. Vous pouvez utiliser cette approche pour lier aux propriétés simples telles que celles qui retournent des collections, mais vous ne pouvez pas lier à des méthodes ou des services. L’exemple suivant montre un <xref:System.Windows.Controls.TextBlock> contrôle qui est lié à la <xref:EnvDTE._DTE.Name%2A> propriété et un <xref:System.Windows.Controls.ListBox> contrôle qui énumère la <xref:EnvDTE.Window.Caption%2A> propriétés de la collection retournée par la <xref:EnvDTE._DTE.Windows%2A> propriété.  
  
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
 [Ajout du contrôle utilisateur à la Page de démarrage](../extensibility/adding-user-control-to-the-start-page.md)