---
title: Inspecter les propriétés XAML pendant le débogage | Microsoft Docs
description: Découvrez comment utiliser l’arborescence d’éléments visuels en direct et les outils de l’Explorateur de propriétés en direct pendant le débogage pour inspecter les propriétés XAML et obtenir une arborescence des éléments d’interface utilisateur.
ms.custom: SEO-VS-2020
ms.date: 03/02/2021
ms.topic: how-to
ms.assetid: 390edde4-7b8d-4c89-8d69-55106b7e6b11
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- uwp
ms.openlocfilehash: 86310346566e8c937c2769a9fcc9f0d4e98b3ae2
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2021
ms.locfileid: "112308439"
---
# <a name="inspect-xaml-properties-while-debugging"></a>Inspecter les propriétés XAML en phase de débogage

Vous pouvez obtenir une vue en temps réel de votre code XAML en cours d’exécution à l’aide de l’**arborescence d’éléments visuels en direct** et de l’**Explorateur de propriétés en direct**. Ces outils affichent une arborescence des éléments de l'interface utilisateur de votre application XAML en cours d'exécution et montrent les propriétés d'exécution de tout élément d'interface utilisateur que vous sélectionnez.

Vous pouvez utiliser ces outils dans les configurations suivantes :

|Type d’application|Système d'exploitation et outils|
|-----------------|--------------------------------|
|Applications Windows Presentation Foundation (4.0 et versions ultérieures).|Windows 7 et versions ultérieures|
|Applications Windows universelles|Windows 10 et versions ultérieures, avec le [Kit de développement logiciel (SDK) Windows 10](https://dev.windows.com/downloads/windows-10-sdk)|

## <a name="look-at-elements-in-the-live-visual-tree"></a>Examiner les éléments dans l’arborescence d’éléments visuels dynamique

Commençons par une application WPF très simple qui présente une vue Liste et un bouton. Chaque fois que vous cliquez sur le bouton, un autre élément est ajouté à la liste. Les éléments avec un numéro pair sont en gris, tandis que les éléments avec un numéro impair sont en jaune.

### <a name="create-the-project"></a>Créer le projet

::: moniker range=">=vs-2019"

1. Créez une application WPF c# (**fichier** > **nouveau** > **projet**, tapez « C# WPF », choisissez le modèle de projet **application WPF** , nommez le **projet TestXAML**, puis vérifiez que **.net Core 3,1** s’affiche dans la liste déroulante **Framework cible** .

::: moniker-end

::: moniker range="vs-2017"

1. Créez une application WPF c# (**fichier**  >  **nouveau**  >  **projet**, tapez « C# WPF », puis choisissez **application WPF (.NET Framework)**). Nommez-la **TestXAML**.

::: moniker-end

1. Modifiez MainWindow.xaml comme suit :

   ```xaml
   <Window x:Class="TestXAML.MainWindow"
      xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
      xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
      xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
      xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
      xmlns:local="clr-namespace:TestXAML"
      mc:Ignorable="d"
      Title="MainWindow" Height="350" Width="525">
      <Grid>
         <Button x:Name="button" Background="LightBlue" Content="Add Item" HorizontalAlignment="Left" Margin="216,206,0,0" VerticalAlignment="Top" Width="75" Click="button_Click"/>
         <ListBox x:Name="listBox" HorizontalAlignment="Left" Height="100" VerticalAlignment="Top" Width="100" Margin="205,80,0,0"/>
      </Grid>
   </Window>
   ```

1. Dans le fichier MainWindow.xaml.cs, ajoutez le gestionnaire de commandes suivant :

   ```csharp
   int count;

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

1. Générez le projet et commencez le débogage. (La configuration de build doit être Debug, et non pas Release. Pour plus d’informations sur les configurations de build, consultez [Présentation des configurations de build](../ide/understanding-build-configurations.md).)

   Quand la fenêtre s’affiche, la barre d’outils dans l’application s’affiche dans votre application en cours d’exécution.

   ::: moniker range=">= vs-2019"
   ![Fenêtre principale de l'application](../debugger/media/vs-2019/livevisualtree-app.png "LiveVIsualTree-App")
   ::: moniker-end
   ::: moniker range="vs-2017"
   ![Fenêtre principale de l'application](../debugger/media/livevisualtree-app.png "LiveVIsualTree-App")
   ::: moniker-end

1. Maintenant, cliquez sur le bouton **Ajouter un élément** plusieurs fois pour ajouter de nouveaux éléments à la liste.

### <a name="inspect-xaml-properties"></a>Inspecter les propriétés XAML

1. Ensuite, ouvrez la fenêtre arborescence d’éléments **visuels en direct** en cliquant sur le bouton très à gauche de la barre d’outils dans l’application (ou en accédant à **déboguer > arborescence d’éléments visuels en direct de Windows >**). Une fois qu’elle est ouverte, faites-la glisser en dehors de sa position d’ancrage pour que nous puissions examiner cette fenêtre et la fenêtre de **Propriétés en direct** côte à côte.

1. Dans la fenêtre **Arborescence d’éléments visuels en direct**, développez le nœud **ContentPresenter**. Il doit contenir des nœuds pour le bouton et la zone de liste. Développez la zone de liste (puis **ScrollContentPresenter** et **ItemsPresenter**) pour rechercher les éléments de zone de liste.

   ::: moniker range=">= vs-2019"
   Si vous ne voyez pas le nœud **ContentPresenter** , activez/désactivez l’icône **afficher uniquement mon code XAML** dans la barre d’outils. À compter de Visual Studio 2019 version 16,4, la vue des éléments XAML est simplifiée par défaut à l’aide de la fonctionnalité juste mon XAML. Vous pouvez également [désactiver ce paramètre](../debugger/general-debugging-options-dialog-box.md) dans les options pour toujours afficher tous les éléments XAML.
   ::: moniker-end

   La fenêtre doit ressembler à ceci :

   ::: moniker range=">= vs-2019"
   ![ListBoxItems dans l'arborescence d'éléments visuels dynamique](../debugger/media/vs-2019/livevisualtree-listboxitems.png "LiveVisualTree-ListBoxItems")
   ::: moniker-end
   ::: moniker range="vs-2017"
   ![ListBoxItems dans l'arborescence d'éléments visuels dynamique](../debugger/media/livevisualtree-listboxitems.png "LiveVisualTree-ListBoxItems")
   ::: moniker-end

1. Revenez à la fenêtre d'application et ajoutez quelques éléments. Vous devriez voir des éléments de zone de liste supplémentaires dans l’**arborescence d’éléments visuels en direct**.

1. À présent, examinons les propriétés de l’un des éléments de la zone de liste.

   Sélectionnez le premier élément de zone de liste dans l’**arborescence d’éléments visuels en direct** et cliquez sur l’icône **Afficher les propriétés** dans la barre d’outils. L’**Explorateur de propriétés en direct** doit apparaître. Notez que le champ de **contenu** est « Item1 » et que le champ de couleur d' **arrière-plan**  >   est **#FFFFFFE0**.

1. Revenez à l’**arborescence d’éléments visuels en direct** et sélectionnez le deuxième élément de zone de liste. L' **Explorateur de propriétés en direct** doit indiquer que le champ de **contenu** est « Item2 » et que le champ de couleur d' **arrière-plan**  >   est **#FFD3D3D3** (selon le thème).

   > [!NOTE]
   > Une bordure jaune autour d’une propriété dans l **'Explorateur de propriétés en direct** signifie que la valeur de propriété est définie via une liaison, telle que `Color = {BindingExpression}` . Une bordure verte signifie que la valeur est définie à l’aide d’une ressource, telle que `Color = {StaticResource MyBrush}` .

   La structure réelle du code XAML inclut de nombreux éléments qui ne vous intéressent probablement pas directement et, si vous ne connaissez pas bien le code, vous pouvez avoir des difficultés à parcourir l’arborescence pour trouver ce que vous recherchez. Par conséquent, l’**arborescence d’éléments visuels en direct** propose quelques méthodes vous permettant d’utiliser l’interface utilisateur de l’application pour rechercher plus facilement l’élément que vous souhaitez examiner.

   ::: moniker range=">= vs-2019"
   **Sélectionnez l’élément dans l’application en cours d’exécution**. Vous pouvez activer ce mode quand vous sélectionnez le bouton le plus à gauche de la barre d’outils de l’**arborescence d’éléments visuels en direct**. Quand ce mode est activé, vous pouvez sélectionner un élément d’interface utilisateur dans l’application et l’**arborescence d’éléments visuels en direct** (ainsi que la **visionneuse de propriétés en direct**) est automatiquement mise à jour pour afficher le nœud dans l’arborescence correspondant à cet élément, et ses propriétés. À compter de Visual Studio 2019 version 16,4, vous pouvez [configurer le comportement de la sélection des éléments](../debugger/general-debugging-options-dialog-box.md).

   **Afficher les ornements de disposition dans l’application en cours d’exécution**. Vous pouvez activer ce mode quand vous sélectionnez le bouton situé immédiatement à droite du bouton Activer la sélection. Quand l’option **Afficher les ornements de disposition** est activée, la fenêtre d’application affiche des lignes horizontales et verticales le long des limites de l’objet sélectionné pour vous permettre de voir sur quoi il est aligné, ainsi que des rectangles montrant les marges. Par exemple, activez à la fois l' **élément de sélection** et la **disposition d’affichage** sur, puis sélectionnez le bloc de texte ajouter un **élément** dans l’application. Vous devez voir le nœud du bloc de texte dans l’**arborescence d’éléments visuels en direct** et les propriétés du bloc de texte dans la **visionneuse de propriétés en direct**, ainsi que les lignes horizontales et verticales sur les limites du bloc de texte.

   ![LivePropertyViewer dans DisplayLayout](../debugger/media/vs-2019/livevisualtreelivepropertyviewer-displaylayout.png "LiveVisualTreeLivePropertyViewer-DisplayLayout")

   **Aperçu de la sélection**. Vous pouvez activer ce mode en sélectionnant le troisième bouton en partant de la gauche dans la barre d'outils de l'arborescence d'éléments visuels dynamique. Ce mode affiche le code XAML dans lequel l'élément a été déclaré, si vous avez accès au code source de l'application. Sélectionnez **Sélectionner un élément** et **prévisualiser la sélection**, puis sélectionnez le bouton dans notre application de test. Le fichier MainWindow.xaml s'ouvre dans Visual Studio et le curseur est placé sur la ligne où le bouton est défini.
   ::: moniker-end

   ::: moniker range="vs-2017"
   **Activer la sélection dans l’application en cours d’exécution**. Vous pouvez activer ce mode quand vous sélectionnez le bouton le plus à gauche de la barre d’outils de l’**arborescence d’éléments visuels en direct**. Quand ce mode est activé, vous pouvez sélectionner un élément d’interface utilisateur dans l’application et l’**arborescence d’éléments visuels en direct** (ainsi que la **visionneuse de propriétés en direct**) est automatiquement mise à jour pour afficher le nœud dans l’arborescence correspondant à cet élément, et ses propriétés.

   **Afficher les ornements de disposition dans l’application en cours d’exécution**. Vous pouvez activer ce mode quand vous sélectionnez le bouton situé immédiatement à droite du bouton Activer la sélection. Quand l’option **Afficher les ornements de disposition** est activée, la fenêtre d’application affiche des lignes horizontales et verticales le long des limites de l’objet sélectionné pour vous permettre de voir sur quoi il est aligné, ainsi que des rectangles montrant les marges. Par exemple, activez les deux options **Activer la sélection** et **Afficher la disposition**, puis sélectionnez le bloc de texte **Ajouter un élément** dans l’application. Vous devez voir le nœud du bloc de texte dans l’**arborescence d’éléments visuels en direct** et les propriétés du bloc de texte dans la **visionneuse de propriétés en direct**, ainsi que les lignes horizontales et verticales sur les limites du bloc de texte.

   ![LivePropertyViewer dans DisplayLayout](../debugger/media/livevisualtreelivepropertyviewer-displaylayout.png "LiveVisualTreeLivePropertyViewer-DisplayLayout")

   **Aperçu de la sélection**. Vous pouvez activer ce mode en sélectionnant le troisième bouton en partant de la gauche dans la barre d'outils de l'arborescence d'éléments visuels dynamique. Ce mode affiche le code XAML dans lequel l'élément a été déclaré, si vous avez accès au code source de l'application. Sélectionnez **Activer la sélection** et **Aperçu de la sélection**, puis sélectionnez le bouton figurant dans l’application de test. Le fichier MainWindow.xaml s'ouvre dans Visual Studio et le curseur est placé sur la ligne où le bouton est défini.
   ::: moniker-end

## <a name="use-xaml-tools-with-running-applications"></a>Utiliser les outils XAML avec les applications en cours d’exécution

Vous pouvez utiliser ces outils XAML même quand vous ne disposez pas du code source. Quand vous effectuez l’attachement à une application XAML en cours d’exécution, vous pouvez utiliser l’**arborescence d’éléments visuels en direct** également sur les éléments d’interface utilisateur de cette application. En voici un exemple qui utilise la même application de test WPF que précédemment.

1. Démarrez l’application **TestXaml** dans la configuration Release. Vous ne pouvez pas attacher à un processus qui s’exécute dans une configuration **Debug**.

2. Ouvrez une deuxième instance de Visual Studio et cliquez sur **Déboguer > Attacher au processus**. Recherchez **TestXaml.exe** dans la liste des processus disponibles, puis cliquez sur **Attacher**.

3. L'application démarre.

4. Dans la deuxième instance de Visual Studio, ouvrez l’**arborescence d’éléments visuels en direct** (**Déboguer > Fenêtres > Arborescence d’éléments visuels en direct**). Vous devez voir les éléments d’interface utilisateur **TestXaml** et vous devez pouvoir les manipuler comme vous l’avez fait lors du débogage direct de l’application.

## <a name="see-also"></a>Voir aussi

[Écrire et déboguer du code XAML en cours d’exécution avec le rechargement à chaud XAML](xaml-hot-reload.md)
