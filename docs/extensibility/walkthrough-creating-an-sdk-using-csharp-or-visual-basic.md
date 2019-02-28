---
title: 'Procédure pas à pas : Création d’un à l’aide du Kit de développement logiciel C# ou Visual Basic | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ef96a249-5eef-402a-a8d5-d74cb49239bd
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bc41b980b012254ac263e027f1dd0361405c8366
ms.sourcegitcommit: cea6187005f8a0cdf44e866a1534a4cf5356208c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/27/2019
ms.locfileid: "56954006"
---
# <a name="walkthrough-create-an-sdk-using-c-or-visual-basic"></a>Procédure pas à pas : Créer un à l’aide du Kit de développement logiciel C# ou Visual Basic
Dans cette procédure pas à pas, vous allez apprendre à créer un kit de développement de bibliothèque mathématique simple à l’aide de Visual c#, puis d’empaqueter le Kit de développement logiciel en tant qu’une Extension Visual Studio (VSIX). Vous allez effectuer les procédures suivantes :

-   [Pour créer le composant SimpleMath Windows Runtime](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createClassLibrary)

-   [Pour créer le projet d’extension SimpleMathVSIX](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createVSIX)
-   [Pour créer un exemple d’application qui utilise la bibliothèque de classes](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createSample)

## <a name="prerequisites"></a>Prérequis
 Pour suivre cette procédure pas à pas, vous devez installer le Kit de développement logiciel (SDK) Visual Studio. Pour plus d’informations, consultez [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

##  <a name="createClassLibrary"></a> Pour créer le composant SimpleMath Windows Runtime

1. Dans la barre de menus, choisissez **fichier** > **New** > **nouveau projet**.

2. Dans la liste des modèles, développez **Visual C#** ou **Visual Basic**, choisissez le **Windows Store** nœud, puis choisissez le **composant d’exécution Windows** modèle.

3. Dans le **nom** , spécifiez **SimpleMath**, puis choisissez le **OK** bouton.

4. Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour le **SimpleMath** nœud de projet, puis choisissez **propriétés**.

5. Renommer **Class1.cs** à **Arithmetic.cs** et mettre à jour pour correspondre à ce qui suit :

    [!code-csharp[CreatingAnSDKUsingWinRT#3](../extensibility/codesnippet/CSharp/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_1.cs)]
    [!code-vb[CreatingAnSDKUsingWinRT#3](../extensibility/codesnippet/VisualBasic/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_1.vb)]

6. Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour le **Solution 'SimpleMath'** nœud, puis choisissez **Configuration Manager**.

    Le **Configuration Manager** boîte de dialogue s’ouvre.

7. Dans le **configuration de solution Active** , choisissez **version**.

8. Dans le **Configuration** colonne, vérifiez que **SimpleMath** ligne est définie sur **version**, puis choisissez le **fermer** bouton pour accepter le modifier.

   > [!IMPORTANT]
   >  Le Kit de développement pour le composant SimpleMath ne comprend qu’une seule configuration. Cette configuration doit être la version Release, ou les applications qui utilisent le composant ne sont pas passer la certification le[!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)].

9. Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour le **SimpleMath** nœud de projet, puis choisissez **Build**.

##  <a name="createVSIX"></a> Pour créer le projet d’extension SimpleMathVSIX

1.  Dans le menu contextuel pour le **Solution 'SimpleMath'** nœud, choisissez **ajouter** > **nouveau projet**.

2.  Dans la liste des modèles, développez **Visual C#** ou **Visual Basic**, choisissez le **extensibilité** nœud, puis choisissez le **projet VSIX** modèle.

3.  Dans le **nom** , spécifiez **SimpleMathVSIX**, puis choisissez le **OK** bouton.

4.  Dans **l’Explorateur de solutions**, choisissez le **source.extension.vsixmanifest** élément.

5.  Dans la barre de menus, sélectionnez **Afficher** > **Code**.

6.  Remplacez le code XML existant par le code XML suivant :

     [!code-xml[CreatingAnSDKUsingWinRT#1](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_2.xml)]

7.  Dans **l’Explorateur de solutions**, choisissez le **SimpleMathVSIX** projet.

8.  Dans la barre de menus, choisissez **Projet** > **Ajouter un nouvel élément**.

9. Dans la liste des **éléments communs**, développez **données**, puis choisissez **fichier XML**.

10. Dans le **nom** , spécifiez `SDKManifest.xml`, puis choisissez le **ajouter** bouton.

11. Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour `SDKManifest.xml`, choisissez **propriétés**, puis modifiez la valeur de la **inclure dans VSIX** propriété **True**.

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

13. Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour le **SimpleMathVSIX** de projet, choisissez **ajouter**, puis choisissez **nouveau dossier**.

14. Renommez le dossier `references`.

15. Ouvrez le menu contextuel pour le **références** dossier, choisissez **ajouter**, puis choisissez **nouveau dossier**.

16. Renommez le sous-dossier à `commonconfiguration`, créez un sous-dossier qu’il contient et nommez le sous-dossier `neutral`.

17. Répétez les quatre étapes précédentes, cette fois le premier dossier à renommé `redist`.

     Le projet contient maintenant la structure de dossiers suivante :

    ```xml
    references\commonconfiguration\neutral
    redist\commonconfiguration\neutral
    ```

18. Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour le **SimpleMath** de projet, puis choisissez **ouvrir le dossier dans l’Explorateur de fichiers**.

19. Dans **Explorateur de fichiers**, accédez à la *bin\Release* dossier, ouvrez le menu contextuel pour le **SimpleMath.winmd** de fichiers, puis choisissez **copier**.

20. Dans **l’Explorateur de solutions**, collez le fichier dans le *references\commonconfiguration\neutral* dossier dans le **SimpleMathVSIX** projet.

21. Répétez l’étape précédente, coller le **SimpleMath.pri** de fichiers dans le *redist\commonconfiguration\neutral* dossier dans le **SimpleMathVSIX** projet.

22. Dans **l’Explorateur de solutions**, choisissez **SimpleMath.winmd**.

23. Dans la barre de menus, choisissez **vue** > **propriétés** (clavier : Choisissez le **F4** clé).

24. Dans le **propriétés** fenêtre, la modification la **Action de génération** propriété **contenu**, puis modifiez le **inclure dans VSIX** propriété  **True**.

25. Dans **l’Explorateur de solutions**, répétez ce processus pour **SimpleMath.pri**.

26. Dans **l’Explorateur de solutions**, choisissez le **SimpleMathVSIX** projet.

27. Dans la barre de menus, choisissez **Build** > **SimpleMathVSIX Build**.

28. Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour le **SimpleMathVSIX** de projet, puis choisissez **ouvrir le dossier dans l’Explorateur de fichiers**.

29. Dans **Explorateur de fichiers**, accédez à *\bin\Release* dossier, puis exécutez *SimpleMathVSIX.vsix* pour l’installer.

30. Choisissez le **installer** bouton, attendez que l’installation se termine, puis redémarrez Visual Studio.

##  <a name="createSample"></a> Pour créer un exemple d’application qui utilise la bibliothèque de classes

1. Dans la barre de menus, choisissez **fichier** > **New** > **nouveau projet**.

2. Dans la liste des modèles, développez **Visual C#** ou **Visual Basic**, puis choisissez le **Windows Store** nœud.

3. Choisissez le **application vide** modèle, nommez le projet **ArithmeticUI**, puis choisissez le **OK** bouton.

4. Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour le **ArithmeticUI** de projet, puis choisissez **ajouter** > **référence**.

5. Dans la liste des types référence, développez **Windows**, puis choisissez **Extensions**.

6. Dans le volet de détails, choisissez le **Simple mathématiques SDK** extension.

    Des informations supplémentaires sur votre Kit de développement logiciel s’affiche. Vous pouvez choisir le **plus d’informations** lien pour ouvrir https://msdn.microsoft.com/, que vous avez spécifié dans le fichier SDKManifest.xml plus haut dans cette procédure pas à pas.

7. Dans le **Gestionnaire de références** boîte de dialogue, sélectionnez le **Simple mathématiques SDK** case à cocher, puis choisissez le **OK** bouton.

8. Dans la barre de menus, choisissez **vue** > **Explorateur d’objets**.

9. Dans le **Parcourir** , choisissez **mathématiques simples**.

     Vous pouvez maintenant Explorer Nouveautés dans le Kit de développement.

10. Dans **l’Explorateur de solutions**, ouvrez **MainPage.xaml**et remplacez son contenu par le XAML suivant :

    **C#**
    ```xml
    <Page
        x:Class="WinRTMathTestCS.MainPage"
        IsTabStop="False"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:local="using:WinRTMathTestCS"
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
        x:Class="WinRTMathTest.MainPage"
        IsTabStop="False"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:local="using:WinRTMathTest"
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

11. Mise à jour **MainPage.xaml.cs** pour faire correspondre le code suivant :

     [!code-csharp[CreatingAnSDKUsingWinRTDemoApp#2](../extensibility/codesnippet/CSharp/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_5.cs)]
     [!code-vb[CreatingAnSDKUsingWinRTDemoApp#2](../extensibility/codesnippet/VisualBasic/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_5.vb)]

12. Choisissez le **F5** touche pour exécuter l’application.

13. Dans l’application, entrez tous les deux numéros, choisissez une opération, puis le **=** bouton.

     Le résultat correct apparaît.

    Vous avez correctement créé et utilisé un SDK d’Extension.

## <a name="see-also"></a>Voir aussi
- [Procédure pas à pas : Créer un kit de développement à l’aide de C++](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)
- [Procédure pas à pas : Créer un kit de développement à l’aide de JavaScript](../extensibility/walkthrough-creating-an-sdk-using-javascript.md)
- [Création d’un Kit de développement logiciel](../extensibility/creating-a-software-development-kit.md)