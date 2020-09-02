---
title: Ajout de commandes Visual Studio à une page de démarrage | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- start page commands
- vs:VSCommands
ms.assetid: a8e2765c-cfb5-47b5-a414-6e48b434e0c2
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0a2042ef9a96eed99636ea0a2f5f09d99cd35ea2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65699153"
---
# <a name="adding-visual-studio-commands-to-a-start-page"></a>Ajout de commandes Visual Studio à une page de démarrage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Lorsque vous créez une page de démarrage personnalisée, vous pouvez y ajouter des commandes Visual Studio. Ce document décrit les différentes façons de lier des commandes Visual Studio à des objets XAML sur une page de démarrage.  
  
 Pour plus d’informations sur les commandes en XAML, consultez [vue d’ensemble](https://msdn.microsoft.com/library/bc208dfe-367d-426a-99de-52b7e7511e81) des commandes  
  
## <a name="adding-commands-from-the-command-well"></a>Ajout de commandes à partir de la commande  
 La page de démarrage créée lors de la [création d’une page de démarrage personnalisée a](../extensibility/creating-a-custom-start-page.md) ajouté les <xref:Microsoft.VisualStudio.PlatformUI?displayProperty=fullName> <xref:Microsoft.VisualStudio.Shell?displayProperty=fullName> espaces de noms et, comme suit.  
  
```  
xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"  
xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"  
```  
  
 Ajoutez un autre espace de noms pour Microsoft. VisualStudio. Shell à partir de l’assembly Microsoft.VisualStudio.Shell.Immutable.11.0.dll. (Vous devrez peut-être ajouter une référence à cet assembly dans votre projet.)  
  
```xml  
xmlns:vscom="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.Immutable.11.0"  
```  
  
 Vous pouvez utiliser l' `vscom:` alias pour lier des commandes Visual Studio à des contrôles XAML sur la page en affectant <xref:System.Windows.Controls.Primitives.ButtonBase.Command%2A> à la propriété du contrôle la valeur `vscom:VSCommands.ExecuteCommand` . Vous pouvez ensuite affecter <xref:System.Windows.Controls.Primitives.ButtonBase.CommandParameter%2A> à la propriété le nom de la commande à exécuter, comme indiqué dans l’exemple suivant.  
  
```xml  
<Button Name="btnNewProj" Content="New Project"   
    Command="{x:Static vscom:VSCommands.ExecuteCommand}"  
    CommandParameter="File.NewProject" >  
</Button>  
```  
  
> [!NOTE]
> L' `x:` alias, qui fait référence au schéma XAML, est requis au début de toutes les commandes.  
  
 Vous pouvez définir la valeur de la `Command` propriété sur n’importe quelle commande accessible à partir de la fenêtre **commande** . Pour obtenir la liste des commandes disponibles, consultez [alias de commandes Visual Studio](../ide/reference/visual-studio-command-aliases.md).  
  
 Si la commande à ajouter nécessite un paramètre supplémentaire, vous pouvez l’ajouter à la valeur de la `CommandParameter` propriété. Séparez les paramètres des commandes à l’aide d’espaces, comme indiqué dans l’exemple suivant.  
  
```xml  
<Button Content="Web Search"   
        Command="{x:Static vscom:VSCommands.ExecuteCommand}"  
        CommandParameter="View.WebBrowser www.bing.com" />  
```  
  
### <a name="calling-extensions-from-the-command-well"></a>Appel d’extensions à partir de la commande  
 Vous pouvez appeler des commandes à partir de VSPackages inscrits en utilisant la même syntaxe que celle utilisée pour appeler d’autres commandes Visual Studio. Par exemple, si un VSPackage installé ajoute une commande de **page d’hébergement** au menu **affichage** , vous pouvez appeler cette commande en affectant à la valeur `CommandParameter` `View.HomePage` .  
  
> [!NOTE]
> Si vous appelez une commande associée à un VSPackage, le package doit être chargé lorsque la commande est appelée.  
  
## <a name="adding-commands-from-assemblies"></a>Ajout de commandes à partir d’assemblys  
 Pour appeler une commande à partir d’un assembly, ou pour accéder au code d’un VSPackage qui n’est pas associé à une commande de menu, vous devez créer un alias pour l’assembly, puis appeler l’alias.  
  
#### <a name="to-call-a-command-from-an-assembly"></a>Pour appeler une commande à partir d’un assembly  
  
1. Dans votre solution, ajoutez une référence à l’assembly.  
  
2. En haut du fichier StartPage. xaml, ajoutez une directive d’espace de noms pour l’assembly, comme indiqué dans l’exemple suivant.  
  
    ```xml  
    xmlns:vsc="clr-namespace:WebUserControl;assembly=WebUserControl"  
    ```  
  
3. Appelez la commande en définissant la `Command` propriété d’un objet XAML, comme indiqué dans l’exemple suivant.  
  
     Langage  
  
    ```  
    <vs:Button Text="Hide me" Command="{x:Static vsc:HideControl}" .../>  
    ```  
  
> [!NOTE]
> Vous devez copier votre assembly, puis le coller dans.. \\ *Dossier d’installation de Visual Studio*\Common7\IDE\PrivateAssemblies\ pour vérifier qu’il est chargé avant d’être appelé.  
  
## <a name="adding-commands-with-the-dte-object"></a>Ajout de commandes avec l’objet DTE  
 Vous pouvez accéder à l’objet DTE à partir d’une page de démarrage, à la fois dans le balisage et dans le code.  
  
 Dans le balisage, vous pouvez y accéder à l’aide de la syntaxe d' [extension de balisage de liaison](https://msdn.microsoft.com/library/83d6e2a4-1b0c-4fc8-bd96-b5e98800ab63) pour appeler l' <xref:EnvDTE.DTE> objet. Vous pouvez utiliser cette approche pour effectuer une liaison à des propriétés simples telles que celles qui retournent des collections, mais vous ne pouvez pas lier à des méthodes ou des services. L’exemple suivant montre un <xref:System.Windows.Controls.TextBlock> contrôle qui crée une liaison avec la <xref:EnvDTE._DTE.Name%2A> propriété, et un <xref:System.Windows.Controls.ListBox> contrôle qui énumère les <xref:EnvDTE.Window.Caption%2A> Propriétés de la collection retournée par la <xref:EnvDTE._DTE.Windows%2A> propriété.  
  
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
  
 Pour obtenir un exemple, consultez [procédure pas à pas : enregistrement des paramètres utilisateur sur une page de démarrage](../extensibility/walkthrough-saving-user-settings-on-a-start-page.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Ajout d’un contrôle utilisateur à la page de démarrage](../extensibility/adding-user-control-to-the-start-page.md)
