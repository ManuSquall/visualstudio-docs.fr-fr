---
title: 'Procédure pas à pas : création d’un SDK à l’aide de C++ | Microsoft Docs'
description: découvrez comment créer un kit de développement logiciel (sdk) de bibliothèque mathématique C++ natif, empaqueter le kit de développement logiciel (sdk) en tant qu’Extension Visual Studio, puis l’utiliser pour créer une application à l’aide de cette procédure pas à pas.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 36ea793b-3832-41a1-b906-69e680ad5e1d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6a52322e575dc201a6bf1648af93d813828e0b17
ms.sourcegitcommit: 8b75524dc544e34d09ef428c3ebbc9b09f14982d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2021
ms.locfileid: "113223005"
---
# <a name="walkthrough-create-an-sdk-using-c"></a>Procédure pas à pas : création d’un SDK à l’aide de C++
cette procédure pas à pas montre comment créer un kit de développement logiciel (sdk) de bibliothèque mathématique C++ natif, empaqueter le kit de développement logiciel (sdk) en tant qu’Extension de Visual Studio (VSIX), puis l’utiliser pour créer une application. La procédure pas à pas est divisée en étapes :

- [pour créer les bibliothèques natives et Windows Runtime](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createClassLibrary)

- [Pour créer le projet d’extension NativeMathVSIX](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createVSIX)

- [Pour créer un exemple d’application qui utilise la bibliothèque de classes](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createSample)

## <a name="prerequisites"></a>Prérequis
 Pour suivre cette procédure pas à pas, vous devez installer le Kit de développement logiciel (SDK) Visual Studio. pour plus d’informations, consultez [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="to-create-the-native-and-windows-runtime-libraries"></a><a name="createClassLibrary"></a>pour créer les bibliothèques natives et Windows Runtime

1. dans la barre de menus, choisissez **fichier**  >  **nouveau**  >  **Project**.

2. dans la liste des modèles, développez **Visual C++**  >  **Windows universel**, puis sélectionnez le modèle **DLL (Windows universal apps)** . Dans la zone **nom** , spécifiez `NativeMath` , puis choisissez le bouton **OK** .

3. Mettez à jour *NativeMath. h* pour qu’il corresponde au code suivant.

     :::code language="cpp" source="../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemath/nativemath.h" id="Snippet1":::

4. Mettez à jour *NativeMath. cpp* pour qu’il corresponde à ce code :

     :::code language="cpp" source="../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemath/nativemath.cpp" id="Snippet2":::

5. dans **Explorateur de solutions**, ouvrez le menu contextuel de la **Solution’NativeMath'**, puis choisissez **ajouter**  >  **un nouveau Project**.

6. dans la liste des modèles, développez **Visual C++**, puis sélectionnez le modèle de **composant Windows Runtime** . Dans la zone **nom** , spécifiez `NativeMathWRT` , puis choisissez le bouton **OK** .

7. Mettez à jour *Class1. h* pour qu’il corresponde à ce code :

     :::code language="cpp" source="../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathwrt/class1.h" id="Snippet3":::

8. Mettez à jour *Class1. cpp* pour qu’il corresponde à ce code :

     :::code language="cpp" source="../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathwrt/class1.cpp" id="Snippet4":::

9. Dans la barre de menus, choisissez **générer**  >  **générer la solution**.

## <a name="to-create-the-nativemathvsix-extension-project"></a><a name="createVSIX"></a> Pour créer le projet d’extension NativeMathVSIX

1. dans **Explorateur de solutions**, ouvrez le menu contextuel de la **Solution’NativeMath'**, puis choisissez **ajouter**  >  **un nouveau Project**.

2. dans la liste des modèles, développez extensibilité **Visual C#**  >  , puis sélectionnez **Project VSIX**. Dans la zone **nom** , spécifiez **NativeMathVSIX**, puis choisissez le bouton **OK** .

3. Dans **Explorateur de solutions**, ouvrez le menu contextuel de **source. extension. vsixmanifest**, puis choisissez **afficher le code**.

4. Utilisez le code XML suivant pour remplacer le XML existant.

    ```xml
    <PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011" xmlns:d="http://schemas.microsoft.com/developer/vsx-schema-design/2011">
      <Metadata>
        <Identity Id="NativeMathVSIX..c6b3cae1-e7e2-4e71-90f6-21017ea0dff7" Version="1.0" Language="en-US" Publisher="MyName" />
        <DisplayName>Native Math SDK</DisplayName>
        <Description>Native Math Library w/ Windows Runtime Additions</Description>
      </Metadata>
      <Installation Scope="Global" AllUsers="true">
        <InstallationTarget Id="Microsoft.ExtensionSDK" TargetPlatformIdentifier="Windows" TargetPlatformVersion="v8.0" SdkName="NativeMathSDK" SdkVersion="1.0" />
      </Installation>
      <Dependencies>
      </Dependencies>
      <Assets>
        <Asset Type="Microsoft.ExtensionSDK" d:Source="File" Path="SDKManifest.xml" />
      </Assets>
    </PackageManifest>
    ```

5. Dans **Explorateur de solutions**, ouvrez le menu contextuel du projet **NativeMathVSIX** , puis choisissez **Ajouter**  >  **un nouvel élément**.

6. Dans la liste des **éléments Visual C#**, développez **données**, puis sélectionnez **fichier XML**. Dans la zone **nom** , spécifiez `SDKManifest.xml` , puis choisissez le bouton **OK** .

7. Utilisez ce code XML pour remplacer le contenu du fichier :

    :::code language="xml" source="../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcpp/cpp/nativemathvsix/sdkmanifest.xml" id="Snippet5":::

8. Dans **Explorateur de solutions**, sous le projet **NativeMathVSIX** , créez la structure de dossiers suivante :

    ```xml
    \DesignTime
          \CommonConfiguration
                \Neutral
                      \Include
          \Debug
                \x86
    \Redist
          \Debug
                \x86
    \References
          \CommonConfiguration
                \Neutral
    ```

9. Dans **Explorateur de solutions**, ouvrez le menu contextuel de la **solution’NativeMath'**, puis choisissez **ouvrir le dossier dans l’Explorateur de fichiers**.

10. Dans l' **Explorateur de fichiers**, copiez *$SolutionRoot $ \NativeMath\NativeMath.h*, puis dans **Explorateur de solutions**, sous le projet **NativeMathVSIX** , collez-le dans le dossier *\\ $SolutionRoot $ \NativeMathVSIX\DesignTime\CommonConfiguration\Neutral\Include*

     Copiez *$SolutionRoot $ \Debug\NativeMath\NativeMath.lib*, puis collez-le dans le dossier *\\ $SolutionRoot $ \NativeMathVSIX\DesignTime\Debug\x86* .

     Copiez *$SolutionRoot $\Debug\NativeMath\NativeMath.dll* et collez-le dans le dossier *\\ $SolutionRoot $ \NativeMathVSIX\Redist\Debug\x86*

     Copiez *$SolutionRoot $\Debug\NativeMathWRT\NativeMathWRT.dll* et collez-le dans le dossier *$SolutionRoot $ \NativeMathVSIX\Redist\Debug\x86*
     Copiez *$SolutionRoot $ \Debug\NativeMathWRT\NativeMathWRT.winmd* et collez-le dans le dossier *$SolutionRoot $ \NativeMathVSIX\References\CommonConfiguration\Neutral* .

     Copiez *$SolutionRoot $ \Debug\NativeMathWRT\NativeMathWRT.pri* et collez-le dans le dossier *$SolutionRoot $ \NativeMathVSIX\References\CommonConfiguration\Neutral* .

11. Dans le dossier *$SolutionRoot $ \\ \NativeMathVSIX\DesignTime\Debug\x86* , créez un fichier texte nommé *NativeMathSDK. props*, puis collez-y le contenu suivant :
   
    ```xml
    <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
      <PropertyGroup>
        <NativeMathSDKPath>$(FrameworkSDKRoot)\..\..\UAP\v0.8.0.0\ExtensionSDKs\NativeMathSDK\1.0\</NativeMathSDKPath>
        <IncludePath>$(NativeMathSDKPath)DesignTime\CommonConfiguration\Neutral\Include;$(IncludePath)</IncludePath>
        <LibraryPath>$(NativeMathSDKPath)DesignTime\Debug\x86;$(LibraryPath)</LibraryPath>
      </PropertyGroup>
      <ItemDefinitionGroup Condition="'$(Configuration)|$(Platform)'=='Debug|Win32'">
         <Link>
           <AdditionalDependencies>NativeMath.lib;%(AdditionalDependencies)</AdditionalDependencies>
         </Link>
      </ItemDefinitionGroup>
    </Project>
    ```

12. dans la barre de menus, choisissez **afficher**  >  **autres Windows**  >  **fenêtre propriétés** (clavier : appuyez sur la touche **F4** ).

13. Dans **Explorateur de solutions**, sélectionnez le fichier **NativeMathWRT. winmd** . Dans la fenêtre **Propriétés** , affectez à la propriété **action de génération** la valeur **contenu**, puis remplacez la propriété **inclure dans VSIX** par **true**.

     Répétez ce processus pour le fichier **NativeMath. h** .

     Répétez ce processus pour le fichier **NativeMathWRT. pri** .

     Répétez ce processus pour le fichier **NativeMath. lib** .

     Répétez ce processus pour le fichier **NativeMathSDK. props** .

14. Dans **Explorateur de solutions**, sélectionnez le fichier **NativeMath. h** . Dans la fenêtre **Propriétés** , affectez à la propriété **inclure dans VSIX** la **valeur true**.

     Répétez ce processus pour le fichier **NativeMath.dll** .

     Répétez ce processus pour le fichier **NativeMathWRT.dll** .

     Répétez ce processus pour le fichier **SDKManifest.xml** .

15. Dans la barre de menus, choisissez **générer**  >  **générer la solution**.

16. Dans **Explorateur de solutions**, ouvrez le menu contextuel du projet **NativeMathVSIX** , puis choisissez **ouvrir le dossier dans l’Explorateur de fichiers**.

17. Dans l' **Explorateur de fichiers**, accédez au dossier *$SolutionRoot $ \NativeMathVSIX\bin\Debug* , puis exécutez *NativeMathVSIX. vsix* pour commencer l’installation.

18. Choisissez le bouton **installer** , attendez que l’installation se termine, puis ouvrez Visual Studio.

## <a name="to-create-a-sample-app-that-uses-the-class-library"></a><a name="createSample"></a> Pour créer un exemple d’application qui utilise la bibliothèque de classes

1. dans la barre de menus, choisissez **fichier**  >  **nouveau**  >  **Project**.

2. dans la liste des modèles, développez **Visual C++**  >  **Windows universel** , puis sélectionnez **application vide**. Dans la zone **nom** , spécifiez **NativeMathSDKSample**, puis choisissez le bouton **OK** .

3. Dans **Explorateur de solutions**, ouvrez le menu contextuel du projet **NativeMathSDKSample** , puis choisissez **Ajouter** une  >  **référence**.

4. dans la boîte de dialogue **ajouter une référence** , dans la liste des types de référence, développez **Universal Windows**, puis sélectionnez **Extensions**. Enfin, activez la case à cocher **Kit de développement logiciel (SDK) Math natif** , puis choisissez le bouton **OK** .

5. Affichez les propriétés du projet pour NativeMathSDKSample.

    Les propriétés que vous avez définies dans *NativeMathSDK. props* ont été appliquées lorsque vous avez ajouté la référence. vous pouvez vérifier que les propriétés ont été appliquées en examinant la propriété **VC++ directories** des **propriétés de Configuration** du projet.

6. Dans **Explorateur de solutions**, ouvrez **MainPage. Xaml**, puis utilisez le code XAML suivant pour remplacer son contenu :

    :::code language="xml" source="../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcppdemoapp/cpp/mainpage.xaml" id="Snippet1":::

7. Mettez à jour *MainPage. Xaml. h* pour qu’il corresponde à ce code :

    :::code language="cpp" source="../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcppdemoapp/cpp/mainpage.xaml.h" id="Snippet2":::

8. Mettez à jour *MainPage. Xaml. cpp* pour qu’il corresponde à ce code :

    :::code language="cpp" source="../snippets/cpp/VS_Snippets_VSSDK/creatingansdkusingcppdemoapp/cpp/mainpage.xaml.cpp" id="Snippet3":::

9. Appuyez sur la touche **F5** pour exécuter l’application.

10. Dans l’application, entrez deux nombres, sélectionnez une opération, puis cliquez sur le **=** bouton.

     Le résultat correct s’affiche.

    Cette procédure pas à pas a montré comment créer et utiliser un kit de développement logiciel (SDK) d’extension pour appeler une [!INCLUDE[wrt](../extensibility/includes/wrt_md.md)] bibliothèque et une non- [!INCLUDE[wrt](../extensibility/includes/wrt_md.md)] bibliothèque.

## <a name="next-steps"></a>Étapes suivantes

## <a name="see-also"></a>Voir aussi
- [Procédure pas à pas : création d’un kit de développement logiciel à l’aide de C# ou Visual Basic](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)
- [Créer un kit de développement logiciel](../extensibility/creating-a-software-development-kit.md)
