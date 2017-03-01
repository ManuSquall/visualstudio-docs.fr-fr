---
title: "Ajout de commandes de Visual Studio à une Page de démarrage | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- start page commands
- vs:VSCommands
ms.assetid: a8e2765c-cfb5-47b5-a414-6e48b434e0c2
caps.latest.revision: 20
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: c75d9b41d0e51d6db2e78d0afa0e1ddf37e87b8a
ms.lasthandoff: 02/22/2017

---
# <a name="adding-visual-studio-commands-to-a-start-page"></a>Ajout de commandes de Visual Studio à une Page de démarrage
Lorsque vous créez une page de démarrage personnalisée, vous pouvez ajouter des commandes de Visual Studio à celui-ci. Ce document décrit les différentes façons de lier des commandes de Visual Studio pour les objets XAML sur une page de démarrage.  
  
 Pour plus d’informations sur les commandes dans XAML, consultez [vue d’ensemble de l’exécution des commandes](http://msdn.microsoft.com/Library/bc208dfe-367d-426a-99de-52b7e7511e81)  
  
## <a name="adding-commands-from-the-command-well"></a>Ajout de commandes et de la commande  
 La page de démarrage créé dans [création d’une Page de démarrage personnalisée](../extensibility/creating-a-custom-start-page.md) ajouté le <xref:Microsoft.VisualStudio.PlatformUI?displayProperty=fullName>et <xref:Microsoft.VisualStudio.Shell?displayProperty=fullName>espaces de noms, comme suit.</xref:Microsoft.VisualStudio.Shell?displayProperty=fullName> </xref:Microsoft.VisualStudio.PlatformUI?displayProperty=fullName>  
  
```  
xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"  
```  
  
 Ajouter un autre espace de noms pour Microsoft.VisualStudio.Shell à partir de l’assembly Microsoft.VisualStudio.Shell.Immutable.11.0.dll. (Vous devrez peut-être ajouter une référence à cet assembly dans votre projet.)  
  
```xml  
xmlns:vscom="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.Immutable.11.0"  
```  
  
 Vous pouvez utiliser la `vscom:` alias pour lier des commandes de Visual Studio à XAML contrôle sur la page en définissant le <xref:System.Windows.Controls.Primitives.ButtonBase.Command%2A>propriété du contrôle `vscom:VSCommands.ExecuteCommand`.</xref:System.Windows.Controls.Primitives.ButtonBase.Command%2A> Vous pouvez ensuite définir la <xref:System.Windows.Controls.Primitives.ButtonBase.CommandParameter%2A>le nom de la commande à exécuter, comme illustré dans l’exemple suivant.</xref:System.Windows.Controls.Primitives.ButtonBase.CommandParameter%2A>  
  
```xml  
<Button Name="btnNewProj" Content="New Project"   
    Command="{x:Static vscom:VSCommands.ExecuteCommand}"  
    CommandParameter="File.NewProject" >  
</Button>  
```  
  
> [!NOTE]
>  Le `x:` alias, qui fait référence au schéma XAML, est requis au début de toutes les commandes.  
  
 Vous pouvez définir la valeur de la `Command` propriété à toutes les commandes qui sont accessibles à partir de la **commande** fenêtre. Pour obtenir la liste des commandes disponibles, consultez la page [alias de commande Visual Studio](../ide/reference/visual-studio-command-aliases.md).  
  
 Si la commande Ajouter nécessite un paramètre supplémentaire, vous pouvez l’ajouter à la valeur de la `CommandParameter` propriété. Paramètres distincts à partir des commandes à l’aide d’espaces, comme indiqué dans l’exemple suivant.  
  
```xml  
<Button Content="Web Search"   
        Command="{x:Static vscom:VSCommands.ExecuteCommand}"  
        CommandParameter="View.WebBrowser www.bing.com" />  
```  
  
### <a name="calling-extensions-from-the-command-well"></a>Appel également des Extensions à partir de la commande  
 Vous pouvez appeler des commandes de packages VS inscrits à l’aide de la même syntaxe qui est utilisée pour appeler d’autres commandes de Visual Studio. Par exemple, si un VSPackage installé ajoute un **Page d’accueil** commande le **affichage** menu, vous pouvez appeler cette commande en définissant `CommandParameter` à `View.HomePage`.  
  
> [!NOTE]
>  Si vous appelez une commande qui est associée à un VSPackage, le package doit être chargé lorsque la commande est appelée.  
  
## <a name="adding-commands-from-assemblies"></a>Ajout de commandes à partir d’assemblys  
 Pour appeler une commande à partir d’un assembly ou d’accéder au code dans un VSPackage qui n’est pas associé à une commande de menu, vous devez créer un alias pour l’assembly, puis appelez l’alias.  
  
#### <a name="to-call-a-command-from-an-assembly"></a>Pour appeler une commande à partir d’un assembly  
  
1.  Dans votre solution, ajoutez une référence à l’assembly.  
  
2.  En haut du fichier StartPage.xaml, ajoutez une directive d’espace de noms pour l’assembly, comme illustré dans l’exemple suivant.  
  
    ```xml  
    xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"  
    ```  
  
3.  Appelez la commande en définissant le `Command` propriété d’un objet XAML, comme indiqué dans l’exemple suivant.  
  
     XAML  
  
    ```  
    <vs:Button Text="Hide me" Command="{x:Static vsc:HideControl}" .../>  
    ```  
  
> [!NOTE]
>  Vous devez copier votre assembly, puis collez-le dans... \\ *Dossier d’installation de visual Studio*\Common7\IDE\PrivateAssemblies\ pour vous assurer qu’il est chargé avant qu’elle est appelée.  
  
## <a name="adding-commands-with-the-dte-object"></a>Ajout de commandes à l’objet DTE  
 Vous pouvez accéder à l’objet DTE à partir d’une Page de démarrage, à la fois dans le balisage et code.  
  
 Dans le balisage, vous pouvez y accéder à l’aide de la [Extension de balisage Binding](http://msdn.microsoft.com/Library/83d6e2a4-1b0c-4fc8-bd96-b5e98800ab63) syntaxe pour appeler le <xref:EnvDTE.DTE>objet.</xref:EnvDTE.DTE> Vous pouvez utiliser cette approche pour lier à de simples propriétés telles que celles qui retournent des collections, mais vous ne pouvez pas lier à des méthodes ou des services. L’exemple suivant montre un <xref:System.Windows.Controls.TextBlock>contrôle qui est lié à la <xref:EnvDTE._DTE.Name%2A>propriété et un <xref:System.Windows.Controls.ListBox>contrôle qui énumère les <xref:EnvDTE.Window.Caption%2A>Propriétés de la collection retournée par la <xref:EnvDTE._DTE.Windows%2A>propriété.</xref:EnvDTE._DTE.Windows%2A> </xref:EnvDTE.Window.Caption%2A> </xref:System.Windows.Controls.ListBox> </xref:EnvDTE._DTE.Name%2A> </xref:System.Windows.Controls.TextBlock>  
  
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
