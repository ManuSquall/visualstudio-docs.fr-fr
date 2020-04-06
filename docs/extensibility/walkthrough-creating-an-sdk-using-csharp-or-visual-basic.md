---
title: 'Procédure pas à pas : Création d’un SDK à l’aide de CMD ou de Visual Basic (en anglais seulement) Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ef96a249-5eef-402a-a8d5-d74cb49239bd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CSharp
- VB
ms.openlocfilehash: 16eb20452601a65c498ff112ea996f2d93559940
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697559"
---
# <a name="walkthrough-create-an-sdk-using-c-or-visual-basic"></a>Procédure pas à pas : Créez un SDK à l’aide de CMD ou de Visual Basic
Dans cette procédure pas à pas, vous apprendrez à créer un simple Math Library SDK en utilisant Visual C’et emballerez ensuite le SDK comme extension de studio visuel (VSIX). Vous compléterez les procédures suivantes :

- [Pour créer le composant SimpleMath Windows Runtime](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createClassLibrary)

- [Créer le projet d’extension SimpleMathVSIX](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createVSIX)
- [Pour créer une application d’échantillon qui utilise la bibliothèque de classe](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createSample)

## <a name="prerequisites"></a>Prérequis
 Pour suivre cette procédure pas à pas, vous devez installer le Kit de développement logiciel (SDK) Visual Studio. Pour plus d’informations, voir [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="to-create-the-simplemath-windows-runtime-component"></a><a name="createClassLibrary"></a>Pour créer le composant SimpleMath Windows Runtime

1. Sur la barre de menu, choisissez **File** > **New** > **Project**.

2. Dans la liste des modèles, élargissez **Visual C ou** Visual **Basic,** choisissez le nœud **Windows Store,** puis choisissez le modèle **de composant Windows Runtime.**

3. Dans la boîte **nom,** spécifiez **SimpleMath,** puis choisissez le bouton **OK.**

4. Dans **Solution Explorer**, ouvrez le menu raccourci pour le nœud du projet **SimpleMath,** puis choisissez **Propriétés**.

5. Renommer **Class1.cs** pour **Arithmetic.cs** et mettre à jour pour correspondre au code suivant :

    [!code-csharp[CreatingAnSDKUsingWinRT#3](../extensibility/codesnippet/CSharp/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_1.cs)]
    [!code-vb[CreatingAnSDKUsingWinRT#3](../extensibility/codesnippet/VisualBasic/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_1.vb)]

6. Dans **Solution Explorer**, ouvrez le menu raccourci pour le nœud Solution **'SimpleMath',** puis choisissez Configuration **Manager**.

    La boîte de dialogue **Configuration Manager** s’ouvre.

7. Dans la liste de configuration active de **la solution,** choisissez **Release**.

8. Dans la colonne **Configuration,** vérifiez que la ligne **SimpleMath** est définie pour **libérer,** puis choisissez le bouton **Close** pour accepter la modification.

   > [!IMPORTANT]
   > Le SDK pour le composant SimpleMath ne comprend qu’une seule configuration. Cette configuration doit être la version build, ou les applications qui [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)]utilisent le composant ne passera pas la certification pour le .

9. Dans **Solution Explorer**, ouvrez le menu raccourci pour le nœud du projet **SimpleMath,** puis choisissez **Build**.

## <a name="to-create-the-simplemathvsix-extension-project"></a><a name="createVSIX"></a>Créer le projet d’extension SimpleMathVSIX

1. Sur le menu raccourci pour le nœud **Solution 'SimpleMath',** choisissez **Add** > **New Project**.

2. Dans la liste des modèles, élargissez **Visual C ou** Visual **Basic,** choisissez le nœud **Extensibility,** puis choisissez le modèle **de projet VSIX.**

3. Dans la boîte **nomin,** spécifiez **SimpleMathVSIX**, puis choisissez le bouton **OK.**

4. Dans **Solution Explorer**, choisissez l’élément **source.extension.vsixmanifest.**

5. Sur la barre de menu, choisissez **View** > **Code**.

6. Remplacer le XML existant par le XML suivant :

     [!code-xml[CreatingAnSDKUsingWinRT#1](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_2.xml)]

7. Dans **Solution Explorer**, choisissez le projet **SimpleMathVSIX.**

8. Sur la barre de menu, choisissez **Project** > **Ajouter un nouvel article**.

9. Dans la liste des **éléments communs**, d’élargir **les données**, puis de choisir **XML File**.

10. Dans la boîte `SDKManifest.xml` **nom,** spécifiez, puis choisissez le bouton **Ajouter.**

11. Dans **Solution Explorer**, ouvrir `SDKManifest.xml`le menu raccourci pour , choisir **propriétés**, puis changer la valeur de la **propriété Inclure dans VSIX** à **True**.

12. Remplacez le contenu du fichier par le code XML suivant :

    **C#**

    ```xml
    <FileList
      DisplayName="WinRT Math Library (CS)"
      MinVSVersion="11.0"
      TargetFramework=".NETCore,version=v4.5"
      AppliesTo="WindowsAppContainer"
      SupportsMultipleVersions="Error"
      MoreInfo="https://msdn.microsoft.com/">
    </FileList>
    ```

    **Visual Basic**

    ```xml
    <FileList
      DisplayName="WinRT Math Library (VB)"
      MinVSVersion="11.0"
      TargetFramework=".NETCore,version=v4.5"
      AppliesTo="WindowsAppContainer"
      SupportsMultipleVersions="Error"
      MoreInfo="https://msdn.microsoft.com/">
    </FileList>
    ```

13. Dans **Solution Explorer**, ouvrez le menu raccourci pour le projet **SimpleMathVSIX,** choisissez **Ajouter,** puis choisissez **New Folder**.

14. Renommer le dossier `references`pour .

15. Ouvrez le menu raccourci pour le dossier **Références,** choisissez **Ajouter,** puis choisissez **New Folder**.

16. Renommer le sous-plieur à `commonconfiguration`, créer un sous-plieur `neutral`en elle, et nommer le sous-plieur .

17. Répétez les quatre étapes précédentes, cette fois `redist`renommer le premier dossier à .

     Le projet contient maintenant la structure du dossier suivant :

    ```xml
    references\commonconfiguration\neutral
    redist\commonconfiguration\neutral
    ```

18. Dans **Solution Explorer**, ouvrez le menu raccourci pour le projet **SimpleMath,** puis choisissez **Open Folder dans File Explorer**.

19. Dans **File Explorer**, naviguez vers le dossier *bin-Release,* ouvrez le menu raccourci pour le fichier **SimpleMath.winmd,** puis choisissez **Copy**.

20. Dans **Solution Explorer**, coller le fichier dans le dossier neutre de *référence-commonconfiguration* dans le projet **SimpleMathVSIX.**

21. Répétez l’étape précédente, en collé le fichier **SimpleMath.pri** dans le dossier *redist-commonconfiguration neutre* dans le projet **SimpleMathVSIX.**

22. Dans **Solution Explorer**, choisissez **SimpleMath.winmd**.

23. Sur la barre de menu, choisissez **View** > **Properties** (Clavier: Choisissez la touche **F4).**

24. Dans la fenêtre **propriété,** changer la propriété **Build Action** en **Contenu**, puis changer **l’inclure dans la** propriété VSIX à **True**.

25. Dans **Solution Explorer**, répétez ce processus pour **SimpleMath.pri**.

26. Dans **Solution Explorer**, choisissez le projet **SimpleMathVSIX.**

27. Sur la barre de menu, choisissez **Build** > **Build SimpleMathVSIX**.

28. Dans **Solution Explorer**, ouvrez le menu raccourci pour le projet **SimpleMathVSIX,** puis choisissez **Open Folder dans File Explorer**.

29. Dans **File Explorer**, naviguez vers le dossier *'bin’Release,* puis exécutez *SimpleMathVSIX.vsix* pour l’installer.

30. Choisissez le bouton **Installer,** attendez la fin de l’installation, puis redémarrez Visual Studio.

## <a name="to-create-a-sample-app-that-uses-the-class-library"></a><a name="createSample"></a>Pour créer une application d’échantillon qui utilise la bibliothèque de classe

1. Sur la barre de menu, choisissez **File** > **New** > **Project**.

2. Dans la liste des modèles, élargissez **Visual C ou** Visual **Basic,** puis choisissez le nœud **Windows Store.**

3. Choisissez le modèle **Blank App,** nommez le projet **ArithmeticUI,** puis choisissez le bouton **OK.**

4. Dans **Solution Explorer**, ouvrez le menu raccourci pour le projet **ArithmeticUI,** puis choisissez **Add** > **Reference**.

5. Dans la liste des types de référence, étendre **Windows**, puis choisir **Extensions**.

6. Dans le volet détails, choisissez l’extension **WinRT Math Library.**

    Des informations supplémentaires sur votre SDK apparaissent. Vous pouvez choisir le lien https://msdn.microsoft.com/ **Plus d’informations** pour ouvrir, comme vous l’avez spécifié dans le fichier SDKManifest.xml plus tôt dans cette procédure pas à pas.

7. Dans la boîte de dialogue **du gestionnaire de référence,** sélectionnez la case à cocher **winRT Math Library,** puis choisissez le bouton **OK.**

8. Sur la barre de menu, choisissez **View** > **Object Browser**.

9. Dans la liste **Parcourir,** choisissez **Simple Math**.

     Vous pouvez maintenant explorer ce qu’il y a dans le SDK.

10. Dans **Solution Explorer**, ouvrez **MainPage.xaml**, et remplacez son contenu par le XAML suivant :

    **C#**

    ```xml
    <Page
        x:Class="ArithmeticUI.MainPage"
        IsTabStop="False"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:local="using:SimpleMath"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        mc:Ignorable="d">

        <Grid Background="{StaticResource ApplicationPageBackgroundThemeBrush}">
            <TextBox x:Name="_firstNumber" HorizontalAlignment="Left" Margin="414,370,0,0" TextWrapping="Wrap" Text="First Number" VerticalAlignment="Top" Height="32" Width="135" TextAlignment="Center"/>
            <TextBox x:Name="_secondNumber" HorizontalAlignment="Left" Margin="613,370,0,0" TextWrapping="Wrap" Text="Second Number" VerticalAlignment="Top" Height="32" Width="135" TextAlignment="Center"/>
            <Button Content="+" HorizontalAlignment="Left" Margin="557,301,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="-" HorizontalAlignment="Left" Margin="557,345,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="*" HorizontalAlignment="Left" Margin="557,389,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="/" HorizontalAlignment="Left" Margin="557,433,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="=" HorizontalAlignment="Left" Margin="755,367,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnResultsClick"/>
            <TextBox x:Name="_result" HorizontalAlignment="Left" Margin="809,370,0,0" TextWrapping="Wrap" Text="Result" VerticalAlignment="Top" Height="32" Width="163" TextAlignment="Center" IsReadOnly="True"/>
        </Grid>
    </Page>
    ```

    **Visual Basic**

    ```xml
    <Page
        x:Class="ArithmeticUI.MainPage"
        IsTabStop="False"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:local="using:SimpleMath"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        mc:Ignorable="d">

        <Grid Background="{StaticResource ApplicationPageBackgroundThemeBrush}">
            <TextBox x:Name="_firstNumber" HorizontalAlignment="Left" Margin="414,370,0,0" TextWrapping="Wrap" Text="First Number" VerticalAlignment="Top" Height="32" Width="135" TextAlignment="Center"/>
            <TextBox x:Name="_secondNumber" HorizontalAlignment="Left" Margin="613,370,0,0" TextWrapping="Wrap" Text="Second Number" VerticalAlignment="Top" Height="32" Width="135" TextAlignment="Center"/>
            <Button Content="+" HorizontalAlignment="Left" Margin="557,301,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="-" HorizontalAlignment="Left" Margin="557,345,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="*" HorizontalAlignment="Left" Margin="557,389,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="/" HorizontalAlignment="Left" Margin="557,433,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="=" HorizontalAlignment="Left" Margin="755,367,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnResultsClick"/>
            <TextBox x:Name="_result" HorizontalAlignment="Left" Margin="809,370,0,0" TextWrapping="Wrap" Text="Result" VerticalAlignment="Top" Height="32" Width="163" TextAlignment="Center" IsReadOnly="True"/>
        </Grid>
    </Page>
    ```

11. Mise à jour **MainPage.xaml.cs** pour correspondre au code suivant :

     [!code-csharp[CreatingAnSDKUsingWinRTDemoApp#2](../extensibility/codesnippet/CSharp/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_5.cs)]
     [!code-vb[CreatingAnSDKUsingWinRTDemoApp#2](../extensibility/codesnippet/VisualBasic/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_5.vb)]

12. Choisissez la clé **F5** pour exécuter l’application.

13. Dans l’application, entrez deux numéros, choisissez **=** une opération, puis choisissez le bouton.

     Le résultat correct apparaît.

    Vous avez réussi à créer et à utiliser un SDK Extension.

## <a name="see-also"></a>Voir aussi
- [Procédure pas à pas : Créez un SDK à l’aide de C](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)
- [Procédure pas à pas : Créez un SDK à l’aide de JavaScript](../extensibility/walkthrough-creating-an-sdk-using-javascript.md)
- [Créer un Kit de développement logiciel](../extensibility/creating-a-software-development-kit.md)
