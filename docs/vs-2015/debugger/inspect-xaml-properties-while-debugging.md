---
title: Inspecter les propriétés XAML pendant le débogage | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 390edde4-7b8d-4c89-8d69-55106b7e6b11
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 010f9b7b0d77bca8bd264ab8a3561743c616dc1f
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58950755"
---
# <a name="inspect-xaml-properties-while-debugging"></a>Inspecter les propriétés XAML en phase de débogage
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez obtenir une vue en temps réel de votre code XAML en cours d’exécution à l’aide de l’**arborescence d’éléments visuels en direct** et de l’**Explorateur de propriétés en direct**. Ces outils affichent une arborescence des éléments de l'interface utilisateur de votre application XAML en cours d'exécution et montrent les propriétés d'exécution de tout élément d'interface utilisateur que vous sélectionnez.  
  
 Vous pouvez utiliser ces outils dans les configurations suivantes :  
  
|Type d'application|Système d'exploitation et outils|  
|-----------------|--------------------------------|  
|Applications Windows Presentation Foundation (4.0 et versions ultérieures).|Windows 7 et versions ultérieures|  
|Applications Windows Store et Windows Phone 8.1|Windows 10 et versions ultérieures, avec le [Windows 10 SDK](https://dev.windows.com/downloads/windows-10-sdk)|  
|Applications pour la plateforme Windows universelle|Windows 10 et versions ultérieures, avec le [Windows 10 SDK](https://dev.windows.com/downloads/windows-10-sdk)|  
  
## <a name="looking-at-elements-in-the-live-visual-tree"></a>Examen des éléments dans l'arborescence d'éléments visuels dynamique  
 Commençons par une application WPF très simple qui présente une vue Liste et un bouton. Chaque fois que vous cliquez sur le bouton, un autre élément est ajouté à la liste. Les éléments avec un numéro pair sont en gris, tandis que les éléments avec un numéro impair sont en jaune.  
  
 Créez une application WPF C# (Fichier / Nouveau / Projet, puis sélectionnez C# et recherchez Application WPF). Nommez-la **TestXAML**.  
  
 Modifiez MainWindow.xaml comme suit :  
  
```xaml  
<Window x:Class="WpfApplication1.MainWindow"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"  
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
    xmlns:local="clr-namespace:WpfApplication1"  
    mc:Ignorable="d"  
     Title="MainWindow" Height="350" Width="525">  
    <Grid>  
        <Button x:Name="button" Background="LightBlue" Content="Add Item" HorizontalAlignment="Left" Margin="216,206,0,0" VerticalAlignment="Top" Width="75" Click="button_Click"/>  
        <ListBox x:Name="listBox" HorizontalAlignment="Left" Height="100" VerticalAlignment="Top" Width="100" Margin="205,80,0,0"/>  
    </Grid>  
</Window>  
```  
  
 Dans le fichier MainWindow.xaml.cs, ajoutez le gestionnaire de commandes suivant :  
  
```csharp  
private void button_Click(object sender, RoutedEventArgs e)  
{  
    ListBoxItem item = new ListBoxItem();  
    item.Content = "Item" + ++count;  
    if (count % 2 == 0)  
    {  
        item.Background = Brushes.LightGray;  
    }  
    else  
    {  
        item.Background = Brushes.LightYellow;  
    }  
    listBox.Items.Add(item);  
}  
```  
  
 Générez le projet et commencez le débogage. (La configuration de build doit être Debug, et non pas Release. Pour plus d’informations sur les configurations de build, consultez [Présentation des configurations de build](../ide/understanding-build-configurations.md).)  
  
 Quand la fenêtre apparaît, cliquez sur le bouton **Ajouter un élément** deux fois. Vous devez voir quelque chose de similaire à :  
  
 ![Fenêtre principale de l’application](../debugger/media/livevisualtree-app.png "LiveVIsualTree-App")  
  
 Ouvrez maintenant le **Live Visual Tree** fenêtre (**déboguer / Windows / arborescence d’éléments visuels en direct**, ou recherchez-la sur le côté gauche de l’IDE). Faites-la glisser hors de sa position d’ancrage afin de la positionner à côté de la fenêtre **Propriétés dynamiques**. Dans la fenêtre **Arborescence d’éléments visuels en direct**, développez le nœud **ContentPresenter**. Il doit contenir des nœuds pour le bouton et la zone de liste. Développez la zone de liste (puis **ScrollContentPresenter** et **ItemsPresenter**) pour rechercher les éléments de zone de liste. La fenêtre doit ressembler à ceci :  
  
 ![ListBoxItems dans l’arborescence d’éléments visuels en direct](../debugger/media/livevisualtree-listboxitems.png "LiveVisualTree-ListBoxItems")  
  
 Revenez à la fenêtre d'application et ajoutez quelques éléments. Vous devriez voir des éléments de zone de liste supplémentaires dans l’**arborescence d’éléments visuels en direct**.  
  
 À présent, examinons les propriétés d'un des éléments de zone de liste. Sélectionnez le premier élément de zone de liste dans l’**arborescence d’éléments visuels en direct** et cliquez sur l’icône **Afficher les propriétés** dans la barre d’outils. L’**Explorateur de propriétés en direct** doit apparaître. Notez que le **contenu** champ est « Item1 » et le **arrière-plan** champ est **#ffffffe0** (jaune clair). Revenez à l’**arborescence d’éléments visuels en direct** et sélectionnez le deuxième élément de zone de liste. Le **Live Property Explorer** doit montrer que le **contenu** champ est « Item2 » et le **arrière-plan** champ est **#ffd3d3d3** (gris clair ).  
  
 La structure réelle du code XAML inclut de nombreux éléments qui ne vous intéressent probablement pas directement et, si vous ne connaissez pas bien le code, vous pouvez avoir des difficultés à parcourir l’arborescence pour trouver ce que vous recherchez. Par conséquent, le **Live Visual Tree** a deux façons qui vous permettent d’utiliser l’interface utilisateur de l’application pour vous aider à trouver l’élément que vous souhaitez examiner.  
  
 **Activer la sélection dans l’application en cours d’exécution**. Vous pouvez activer ce mode quand vous sélectionnez le bouton le plus à gauche de la barre d’outils de l’**arborescence d’éléments visuels en direct**. Quand ce mode est activé, vous pouvez sélectionner un élément d’interface utilisateur dans l’application et l’**arborescence d’éléments visuels en direct** (ainsi que la **visionneuse de propriétés en direct**) est automatiquement mise à jour pour afficher le nœud dans l’arborescence correspondant à cet élément, et ses propriétés.  
  
 **Afficher les ornements de disposition dans l’application en cours d’exécution**. Vous pouvez activer ce mode quand vous sélectionnez le bouton situé immédiatement à droite du bouton Activer la sélection. Quand l’option **Afficher les ornements de disposition** est activée, la fenêtre d’application affiche des lignes horizontales et verticales le long des limites de l’objet sélectionné pour vous permettre de voir sur quoi il est aligné, ainsi que des rectangles montrant les marges. Par exemple, activez les deux options **Activer la sélection** et **Afficher la disposition**, puis sélectionnez le bloc de texte **Ajouter un élément** dans l’application. Vous devez voir le nœud du bloc de texte dans l’**arborescence d’éléments visuels en direct** et les propriétés du bloc de texte dans la **visionneuse de propriétés en direct**, ainsi que les lignes horizontales et verticales sur les limites du bloc de texte.  
  
 ![LivePropertyViewer dans DisplayLayout](../debugger/media/livevisualtreelivepropertyviewer-displaylayout.png "LiveVisualTreeLivePropertyViewer-DisplayLayout")  
  
 **Aperçu de la sélection**. Vous pouvez activer ce mode en sélectionnant le troisième bouton en partant de la gauche dans la barre d'outils de l'arborescence d'éléments visuels dynamique. Ce mode affiche le code XAML dans lequel l'élément a été déclaré, si vous avez accès au code source de l'application. Sélectionnez **Activer la sélection** et **Aperçu de la sélection**, puis sélectionnez le bouton figurant dans l’application de test. Le fichier MainWindow.xaml s'ouvre dans Visual Studio et le curseur est placé sur la ligne où le bouton est défini.  
  
## <a name="using-xaml-tools-with-running-applications"></a>Utilisation des outils XAML avec les applications en cours d'exécution  
 Vous pouvez utiliser ces outils XAML même quand vous ne disposez pas du code source. Quand vous effectuez l’attachement à une application XAML en cours d’exécution, vous pouvez utiliser l’**arborescence d’éléments visuels en direct** également sur les éléments d’interface utilisateur de cette application. En voici un exemple qui utilise la même application de test WPF que précédemment.  
  
1.  Démarrez l’application **TestXaml** dans la configuration Release. Vous ne pouvez pas attacher à un processus qui s’exécute dans une configuration **Debug**.  
  
2.  Ouvrez une deuxième instance de Visual Studio et cliquez sur **déboguer / attacher au processus**. Recherchez **TestXaml.exe** dans la liste des processus disponibles, puis cliquez sur **Attacher**.  
  
3.  L'application démarre.  
  
4.  Dans la deuxième instance de Visual Studio, ouvrez le **Live Visual Tree** (**déboguer / Windows / arborescence d’éléments visuels en direct**). Vous devez voir les éléments d’interface utilisateur **TestXaml** et vous devez pouvoir les manipuler comme vous l’avez fait lors du débogage direct de l’application.
