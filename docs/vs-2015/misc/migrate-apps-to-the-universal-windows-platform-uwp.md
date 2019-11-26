---
title: Migrer des applications vers le plateforme Windows universelle (UWP) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
ms.assetid: 5279ab9b-71d9-4be5-81f6-a1f24b06f5fb
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5794aa5ab7dc14932c65a9156ea9252e71731155
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299476"
---
# <a name="migrate-apps-to-the-universal-windows-platform-uwp"></a>Migrer des applications vers la plateforme Windows universelle (UWP)
Apportez les modifications manuelles nécessaires à vos fichiers de projet existants pour les applications Windows Store 8.1, les applications Windows Phone 8.1 ou les applications Windows universelles créées avec Visual Studio 2015 RC pour pouvoir les utiliser avec Visual Studio 2015 RTM. (Si vous disposez d’une application Windows 8.1 universelle avec un projet d’application Windows et un projet Windows Phone, vous devez suivre les étapes de migration de chaque projet.)

 Avec la plateforme Windows universelle, vous ciblez désormais avec votre application une ou plusieurs familles d’appareils. Pour plus d’informations sur les applications Windows universelles, consultez ce [guide de plateforme](https://msdn.microsoft.com/library/windows/apps/dn894631.aspx).

- [Migrez vos applications Windows Store 8.1 ou Windows Phone 8.1 C#/VB existantes](#MigrateCSharp) pour utiliser la plateforme Windows universelle.

- [Migrez vos applications Windows Store 8.1 ou Windows Phone 8.1 C++ existantes](#MigrateCPlusPlus) pour utiliser la plateforme Windows universelle.

- [Modifications requises pour les applications Windows universelles existantes créées avec Visual Studio 2015 RC](#PreviousVersions).

- [Modifications requises pour des projets de test unitaire pour des applications Windows universelles créées avec Visual Studio 2015 RC](#MigrateUnitTest).

  Si vous ne voulez pas apporter toutes ces modifications, découvrez comment [porter vos applications existantes](https://msdn.microsoft.com/library/windows/apps/xaml/mt238321.aspx) dans un nouveau projet Windows universel.

## <a name="MigrateCSharp"></a>Migrez C#vos applications/VB Windows Store 8,1 ou Windows Phone 8,1 pour utiliser le plateforme Windows universelle

#### <a name="migrate-your-cvb-project-files"></a>Migrer vos fichiers projet C#/VB

1. Pour déterminer quelle plateforme Windows universelle vous avez installée, ouvrez ce dossier : **\Program Files (x86)\Windows Kits\10\Platforms\UAP**. Il contient une liste de dossiers pour chaque plateforme Windows universelle installée. Le nom du dossier correspond à la version de la plateforme Windows universelle que vous avez installée. Par exemple, cet appareil Windows 10 est équipé de la version 10.0.10240.0 de la plateforme Windows universelle.

     ![Ouvrir le dossier pour afficher les versions installées](../misc/media/uap-uwpversions.png "UAP_UWPVersions")

     Plusieurs versions de la plateforme Windows universelle peuvent être installées. Nous vous recommandons d’utiliser la version la plus récente pour votre application.

2. Dans l’Explorateur de fichiers, accédez au dossier où votre projet de plateforme Windows universelle est stocké. Créez un fichier .json dans ce dossier. Nommez le fichier : project.json, puis ajoutez le contenu suivant à ce fichier :

    ```json
    {
      "dependencies": {
        "Microsoft.ApplicationInsights": "1.0.0",
        "Microsoft.ApplicationInsights.PersistenceChannel": "1.0.0",
        "Microsoft.ApplicationInsights.WindowsApps": "1.0.0",
        "Microsoft.NETCore.UniversalWindowsPlatform": "5.0.0"
      },
      "frameworks": {
        "uap10.0": {}
      },
      "runtimes": {
        "win10-arm": {},
        "win10-arm-aot": {},
        "win10-x86": {},
        "win10-x86-aot": {},
        "win10-x64": {},
        "win10-x64-aot": {}
      }
    }

    ```

3. Créez un fichier nommé default.rd.xml avec le contenu ci-dessous. Si vous disposez d’un projet Visual Basic, ajoutez ce fichier au répertoire My Project pour ce projet. Si vous disposez d’un projet C#, ajoutez ce fichier dans le répertoire Properties pour ce projet.

    ```xml
    <?xml version="1.0"?>
    <!-- This file contains Runtime Directives used by .NET Native. The defaults here are suitable for most developers. However, you can modify these parameters to modify the behavior of the .NET Native optimizer. Runtime Directives are documented at http://go.microsoft.com/fwlink/?LinkID=391919 To fully enable reflection for App1.MyClass and all of its public/private members <Type Name="App1.MyClass" Dynamic="Required All"/> To enable dynamic creation of the specific instantiation of AppClass<T> over System.Int32 <TypeInstantiation Name="App1.AppClass" Arguments="System.Int32" Activate="Required Public" /> Using the Namespace directive to apply reflection policy to all the types in a particular namespace <Namespace Name="DataClasses.ViewModels" Seralize="All" /> -->
    <Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata"><Application>
    <!-- An Assembly element with Name="*Application*" applies to all assemblies in the application package. The asterisks are not wildcards. -->
    <Assembly Dynamic="Required All" Name="*Application*"/>
    <!-- Add your application specific runtime directives here. -->
    </Application></Directives>
    ```

4. Ouvrez votre solution qui contient votre application Windows Store 8.1 ou Windows Phone 8.1 existante dans Visual Studio.

5. Cliquez avec le bouton droit sur votre projet existant pour votre application dans l’Explorateur de solutions, puis sélectionnez **Décharger le projet**. Une fois le projet déchargé, cliquez de nouveau avec le bouton droit sur le fichier projet et choisissez de modifier le fichier .csproj ou .vbproj.

     ![Cliquez avec le bouton droit sur le projet, puis choisissez Modifier.](../misc/media/uap-editproject.png "UAP_EditProject")

6. Recherchez l’élément \<PropertyGroup > contenant l’élément \<TargetPlatformVersion > avec la valeur 8,1. Procédez comme suit pour cet élément \<PropertyGroup >:

    1. Définissez la valeur de l’élément de > de plateforme \<sur : **x86**.

    2. Ajoutez un élément \<TargetPlatformIdentifier > et affectez-lui la valeur : **UAP**.

    3. Remplacez la valeur existante de l’élément \<TargetPlatformVersion > par la valeur de la version plateforme Windows universelle que vous avez installée. Ajoutez également un élément \<TargetPlatformMinVersion > et donnez-lui la même valeur.

    4. Remplacez la valeur de l’élément \<MinimumVisualStudioVersion > par : **14**.

    5. Remplacez l’élément \<ProjectTypeGuids > comme indiqué ci-dessous :

         Pour C# :

        ```xml
        <ProjectTypeGuids>{A5A43C5B-DE2A-4C0C-9213-0A381AF9435A};{FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}</ProjectTypeGuids>
        ```

         Pour Visual Basic :

        ```xml
        <ProjectTypeGuids>{A5A43C5B-DE2A-4C0C-9213-0A381AF9435A};{F184B08F-C81C-45F6-A57F-5ABD9991F28F}</ProjectTypeGuids>
        ```

    6. Ajoutez un élément \<EnableDotNetNativeCompatibleProfile > et affectez-lui la valeur : **true**.

    7. L’échelle par défaut des ressources pour les applications Windows universelles est 200. Si votre projet comprend des ressources qui ne sont pas mises à l’échelle à 200, vous devez ajouter un élément \<UapDefaultAssetScale > avec la valeur de l’échelle de vos ressources à ce PropertyGroup. En savoir plus sur les [ressources et échelles](https://msdn.microsoft.com/library/jj679352.aspx).

         Votre \<élément PropertyGroup > doit maintenant ressembler à cet exemple :

        ```xml
        <PropertyGroup>
            …
             <Platform Condition=" '$(Platform)' == '' ">x86</Platform>
             <TargetPlatformVersion>10.0.10240.0</TargetPlatformVersion>
             <TargetPlatformMinVersion>10.0.10240.0</TargetPlatformMinVersion>
             <TargetPlatformIdentifier>UAP</TargetPlatformIdentifier>
             <MinimumVisualStudioVersion>14</MinimumVisualStudioVersion>
             <ProjectTypeGuids>{A5A43C5B-DE2A-4C0C-9213-0A381AF9435A};{FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}</ProjectTypeGuids>
        <EnableDotNetNativeCompatibleProfile>true</EnableDotNetNativeCompatibleProfile>
             <UapDefaultAssetScale>100</UapDefaultAssetScale>
             …
        </PropertyGroup>
        ```

7. Remplacez toutes les instances de 12.0 par 14.0 pour refléter la version de Visual Studio que vous utilisez à présent. Comme les instances suivantes :

    ```xml
    <Project Tools Version="14.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    ```

    ```
    <PropertyGroup Condition=" '$(VisualStudioVersion)' == '' or '$(VisualStudioVersion)' < '14.0' ">
        <VisualStudioVersion>14.0</VisualStudioVersion>
    ```

8. Recherchez \<éléments de > PropertyGroup configurés pour la plateforme AnyCPU dans le cadre de l’attribut condition. Supprimez ces éléments et tous leurs enfants. La plateforme AnyCPU n’est pas prise en charge pour les applications Windows 10 dans Visual Studio 2015. Par exemple, vous devez supprimer \<éléments PropertyGroup > comme ceux-ci :

    ```xml
    <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">
        <PlatformTarget>AnyCPU</PlatformTarget>
        <DebugSymbols>true</DebugSymbols>
        <DebugType>full</DebugType>
        <Optimize>false</Optimize>
        <OutputPath>bin\Debug\</OutputPath>
        <DefineConstants>DEBUG;TRACE;NETFX_CORE;WINDOWS_UAP</DefineConstants>
        <ErrorReport>prompt</ErrorReport>
        <WarningLevel>4</WarningLevel>
      </PropertyGroup>
      <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Release|AnyCPU' ">
        <PlatformTarget>AnyCPU</PlatformTarget>
        <DebugType>pdbonly</DebugType>
        <Optimize>true</Optimize>
        <OutputPath>bin\Release\</OutputPath>
        <DefineConstants>TRACE;NETFX_CORE;WINDOWS_UAP</DefineConstants>
        <ErrorReport>prompt</ErrorReport>
        <WarningLevel>4</WarningLevel>
      </PropertyGroup>
    ```

9. Pour chaque élément \<PropertyGroup > restant, vérifiez si l’élément a un attribut condition avec une configuration Release. Si c’est le cas, mais qu’il ne contient pas d’élément \<UseDotNetNativeToolchain >, ajoutez-en un. Définissez la valeur de l’élément \<UseDotNetNativeToolchain > sur true, comme suit :

    ```xml
    <PropertyGroup Condition="'$(Configuration)|$(Platform)' == 'Release|x64'">
        <OutputPath>bin\x64\Release\</OutputPath>
        <DefineConstants>TRACE;NETFX_CORE;WINDOWS_UAP</DefineConstants>
        <Optimize>true</Optimize>
        <NoWarn>;2008</NoWarn>
        <DebugType>pdbonly</DebugType>
        <PlatformTarget>x64</PlatformTarget>
        <UseVSHostingProcess>false</UseVSHostingProcess>
        <ErrorReport>prompt</ErrorReport>
        <Prefer32Bit>true</Prefer32Bit>
        <UseDotNetNativeToolchain>true</UseDotNetNativeToolchain>
      </PropertyGroup>
    ```

10. Pour les projets Windows Phone uniquement, supprimez l’élément \<PropertyGroup > qui contient un élément \<TargetPlatformIdentifier > avec la valeur WindowsPhoneApp. De même, supprimez tous les enfants de cet élément :

    ```xml
    <PropertyGroup Condition=" '$(TargetPlatformIdentifier)' == '' ">
      <TargetPlatformIdentifier>WindowsPhoneApp</TargetPlatformIdentifier>
    </PropertyGroup>
    ```

11. Recherchez l' \<élément ItemGroup > contenant l’élément \<AppxManifest >. Ajoutez les éléments suivants \<aucun > en tant qu’enfant de l’élément \<ItemGroup >:

    ```xml
    <None Include="project.json" />
    ```

12. Recherchez l’élément \<ItemGroup > qui contient d’autres ressources ajoutées à votre projet, telles que les fichiers logo. png (le contenu\<include = "Assets\Logo.scale-100.png"/>). Ajoutez le contenu \<suivant > élément enfant à cet \<élément ItemGroup >:

     **Pour C#:**

    ```xml
    <Content Include="Properties\default.rd.xml" />
    ```

     **Pour VB :**

    ```xml
    <Content Include="My Project\default.rd.xml" />
    ```

13. Recherchez l' \<élément ItemGroup > qui comprend \<référence > éléments enfants dans les packages NuGet. Notez les packages NuGet que vous utilisez, car vous devez les télécharger avec le gestionnaire de package NuGet, une fois que votre projet est rechargé. Supprimez cette \<ItemGroup > avec ses enfants. Par exemple, un projet de plateforme Windows universelle peut inclure les packages NuGet suivants qu’il convient de supprimer :

    ```xml
    <ItemGroup>
        <Reference Include="Microsoft.ApplicationInsights, Version=0.14.3.177, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL">
          <HintPath>..\packages\Microsoft.ApplicationInsights.0.14.3-build00177\lib\portable-win81+wpa81\Microsoft.ApplicationInsights.dll</HintPath>
          <Private>True</Private>
        </Reference>
        <Reference Include="Microsoft.ApplicationInsights.Extensibility.Windows, Version=0.14.3.177, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL">
          <HintPath>..\packages\Microsoft.ApplicationInsights.WindowsApps.0.14.3-build00177\lib\win81\Microsoft.ApplicationInsights.Extensibility.Windows.dll</HintPath>
          <Private>True</Private>
        </Reference>
        <Reference Include="Microsoft.ApplicationInsights.PersistenceChannel, Version=0.14.3.186, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL">
          <HintPath>..\packages\Microsoft.ApplicationInsights.PersistenceChannel.0.14.3-build00177\lib\portable-win81+wpa81\Microsoft.ApplicationInsights.PersistenceChannel.dll</HintPath>
          <Private>True</Private>
        </Reference>
        <Reference Include="System.Numerics.Vectors, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL">
          <HintPath>..\packages\System.Numerics.Vectors.4.0.0\lib\win8\System.Numerics.Vectors.dll</HintPath>
          <Private>True</Private>
        </Reference>
        <Reference Include="System.Numerics.Vectors.WindowsRuntime, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL">
          <HintPath>..\packages\System.Numerics.Vectors.4.0.0\lib\win8\System.Numerics.Vectors.WindowsRuntime.dll</HintPath>
          <Private>True</Private>
        </Reference>
      </ItemGroup>
    ```

14. Enregistrez les modifications apportées.

15. Fermez le fichier .csproj ou .vbproj.

16. Cliquez avec le bouton droit sur votre projet dans l’Explorateur de solutions et choisissez Recharger le projet dans le menu contextuel. Tous les fichiers de votre projet doivent désormais être affichés dans l’Explorateur de solutions.

17. Utilisez le gestionnaire NuGet pour ajouter à nouveau les packages que vous avez supprimés dans une étape antérieure.

     À présent, vous devez suivre la procédure permettant de [mettre à jour les fichiers manifeste du package](#PackageManifest) pour tous vos projets Windows Store 8.1 et Windows Phone 8.1.

## <a name="MigrateCPlusPlus"></a>Migrez C++ vos applications Windows Store 8,1 ou Windows Phone 8,1 pour utiliser le plateforme Windows universelle

#### <a name="migrate-your-c-project-files"></a>Migrer vos fichiers projet C++

1. Pour déterminer quelle plateforme Windows universelle vous avez installée, ouvrez ce dossier : **\Program Files (x86)\Windows Kits\10\Platforms\UAP**. Il contient une liste de dossiers pour chaque plateforme Windows universelle installée. Le nom du dossier correspond à la version de la plateforme Windows universelle que vous avez installée. Par exemple, cet appareil Windows 10 est équipé de la version 10.0.10240.0 de la plateforme Windows universelle.

     ![Ouvrir le dossier pour afficher les versions installées](../misc/media/uap-uwpversions.png "UAP_UWPVersions")

     Plusieurs versions de la plateforme Windows universelle peuvent être installées. Nous vous recommandons d’utiliser la version la plus récente pour votre application.

2. Ouvrez votre solution qui contient votre application Windows Store 8.1 ou Windows Phone 8.1 C++ existante dans Visual Studio.

     Cliquez avec le bouton droit sur votre projet existant dans l’Explorateur de solutions, puis sélectionnez **Décharger le projet**. Une fois le projet déchargé, cliquez de nouveau avec le bouton droit sur le fichier projet et choisissez de modifier le fichier .vcxproj.

     ![Cliquez&#45;avec le bouton droit sur le fichier projet, puis choisissez Modifier.](../misc/media/uap-editcplusproject.png "UAP_EditCPlusProject")

3. Recherchez l’élément \<PropertyGroup > contenant l’élément \<Applicationtyperevision, > avec la valeur 8,1. Procédez comme suit pour cet élément \<PropertyGroup >:

    1. Ajoutez un élément \<WindowsTargetPlatformVersion > et un élément > \<WindowsTargetPlatformMinVersion et attribuez-lui la valeur de la plateforme Windows universelle version que vous avez installée.

    2. Mettez à jour la valeur de l’élément ApplicationTypeRevision, de 8.1 à 10.0.

    3. Remplacez la valeur de l’élément \<MinimumVisualStudioVersion > par : 14.

    4. Ajoutez un élément \<EnableDotNetNativeCompatibleProfile > et affectez-lui la valeur : true.

    5. L’échelle par défaut des ressources pour les applications Windows universelles est 200. Si votre projet comprend des ressources qui ne sont pas mises à l’échelle à 200, vous devez ajouter un élément \<UapDefaultAssetScale > avec la valeur de l’échelle de vos ressources à ce PropertyGroup. En savoir plus sur les [ressources et échelles](https://msdn.microsoft.com/library/jj679352.aspx).

    6. Pour les projets de Windows Phone uniquement, remplacez la valeur de \<ApplicationType > de Windows Phone par Windows Store.

         Votre \<élément PropertyGroup > doit maintenant ressembler à cet exemple :

        ```xml
        <PropertyGroup>
            …
                  <WindowsTargetPlatformVersion>10.0.10240.0</WindowsTargetPlatformVersion>
        <WindowsTargetPlatformMinVersion>10.0.10240.0</WindowsTargetPlatformMinVersion>
             <ApplicationType>Windows Store</ApplicationType>
             <ApplicationTypeRevision>10.0</ApplicationTypeRevision>
             <MinimumVisualStudioVersion>14</MinimumVisualStudioVersion>
             <EnableDotNetNativeCompatibleProfile>true</EnableDotNetNativeCompatibleProfile>
             <UapDefaultAssetScale>100</UapDefaultAssetScale>
             …
        </PropertyGroup>
        ```

4. Remplacez toutes les instances de l’élément \<PlatformToolset > par la valeur V140. Exemple :

    ```xml
    <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|Win32'" Label="Configuration">
        <ConfigurationType>Application</ConfigurationType>
        <UseDebugLibraries>false</UseDebugLibraries>
        <WholeProgramOptimization>true</WholeProgramOptimization>
        <PlatformToolset>v140</PlatformToolset>
        <UseDotNetNativeToolchain>true</UseDotNetNativeToolchain>
      </PropertyGroup>
    ```

5. Pour chaque élément \<PropertyGroup > restant, vérifiez si l’élément a un attribut condition avec une configuration Release. Si c’est le cas, mais qu’il ne contient pas d’élément \<UseDotNetNativeToolchain >, ajoutez-en un. Définissez la valeur de l’élément \<UseDotNetNativeToolchain > sur true, comme suit :

    ```xml
    <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|X64'" Label="Configuration">
        <ConfigurationType>Application</ConfigurationType>
        <UseDebugLibraries>false</UseDebugLibraries>
        <WholeProgramOptimization>true</WholeProgramOptimization>
        <PlatformToolset>v140</PlatformToolset>
        <UseDotNetNativeToolchain>true</UseDotNetNativeToolchain>
      </PropertyGroup>

    ```

6. Enregistrez les modifications apportées. Ensuite, fermez le fichier projet.

7. Cliquez avec le bouton droit sur votre fichier projet dans l’Explorateur de solutions et choisissez Recharger le projet dans le menu contextuel. Tous les fichiers de votre projet doivent désormais être affichés dans l’Explorateur de solutions.

     À présent, vous devez suivre la procédure permettant de [mettre à jour les fichiers manifeste du package](#PackageManifest) pour tous vos projets Windows Store 8.1 et Windows Phone 8.1.

## <a name="PackageManifest"></a>Mettre à jour votre fichier manifeste de package pour tous vos projets Windows Store 8,1 ou Windows Phone 8,1
 Vous devez mettre à jour le fichier manifeste du package pour chaque projet figurant dans votre solution.

#### <a name="update-your-package-manifest-file"></a>Mettre à jour votre fichier manifeste de package

1. Ouvrez le fichier Package.appxmanifest dans votre projet. Vous devez modifier le fichier Package.AppxManifest pour chacun de vos projets Windows Store et Windows Phone.

2. Vous devez mettre à jour l’élément de > de package \<avec les nouveaux schémas en fonction de votre type de projet existant. Tout d’abord, supprimez les schémas ci-dessous selon que vous disposez d’un projet Windows Store ou Windows Phone.

    **Ancien pour le projet du Windows Store :** Votre package d' \<> élément sera semblable à celui-ci.

   ```xml
   <Package
       xmlns="http://schemas.microsoft.com/appx/2010/manifest"
       xmlns:m2="http://schemas.microsoft.com/appx/2013/manifest">

   ```

    **Ancien pour Windows Phone projet :** Votre package d' \<> élément sera semblable à celui-ci.

   ```xml
   <Package
       xmlns="http://schemas.microsoft.com/appx/2010/manifest"
   xmlns:m2="http://schemas.microsoft.com/appx/2013/manifest"
   xmlns:m3="http://schemas.microsoft.com/appx/2014/manifest"
   xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest">
   ```

    **Nouveauté de plateforme Windows universelle :** Ajoutez les schémas ci-dessous à votre élément de > de package \<. Supprimez tous les préfixes d’identificateur d’espace de noms associés dans les éléments pour les schémas que vous venez de supprimer. Mettez à jour la propriété IgnorableNamespaces en spécifiant la valeur uap mp. Votre nouvel élément de > de package \<doit ressembler à celui-ci.

   ```xml
   <Package
       xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
       xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10"
       xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest"
      IgnorableNamespaces= "uap mp">

   ```

3. Ajoutez un \<des dépendances > élément enfant à l’élément du package de \<>. Ajoutez ensuite un élément enfant \<TargetDeviceFamily > à ce \<dépendances > élément avec les attributs Name, MinVersion et MaxVersionTested. Affectez à l’attribut Name la valeur Windows.Universal. Affectez aux attributs MinVersion et MaxVersionTested la valeur de la version de la plateforme Windows universelle que vous avez installée. Cet élément doit ressembler à celui-ci :

   ```xml
   <Dependencies>
   <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10069.0" MaxVersionTested="10.0.10069.0" />
   </Dependencies>
   ```

4. **Pour Windows Store uniquement :** Vous devez ajouter un élément enfant \<MP : PhoneIdentity > à l’élément de > \<package. Ajoutez un attribut PhoneProductId et un attribut PhonePublisherId. Affectez à PhoneProductId la même valeur que l’attribut Name dans l’élément \<Identity >. Affectez à l’attribut PhonePublishedId la valeur 00000000-0000-0000-0000-000000000000. Comme ceci :

   ```xml
   <Identity Name="aa3815a1-2d97-4c71-8c99-578135b28cd8" Publisher="CN=xxxxxxxx" Version="1.0.0.0" />
   <mp:PhoneIdentity PhoneProductId="aa3815a1-2d97-4c71-8c99-578135b28cd8" PhonePublisherId="00000000-0000-0000-0000-000000000000"/>
   ```

5. Recherchez la \<composants requis > élément et supprimez cet élément et tous les éléments enfants qu’il contient.

6. Ajoutez l’espace de noms **UAP** aux éléments de > de ressource \<suivants : Scale, DXFeatureLevel. Exemple :

   ```xml
   <Resources>
     <Resource Language="en-us"/>
    <Resource uap:Scale="180"/>
    <Resource uap:DXFeatureLevel="dx11"/>
   </Resources>

   ```

7. Ajoutez l’espace de noms **UAP** aux éléments suivants \<> fonctionnalité : DocumentsLibrary, PicturesLibrary, VideosLibrary, MusicLibrary, EnterpriseAuthentication, SharedUserCertificates, removableStorage, rendez-vous et contacts. Exemple :

   ```xml
   <Capabilities>
     <uap:Capability Name="documentsLibrary"/>
     <uap:Capability Name="removableStorage"/>
   </Capabilities>

   ```

8. Ajoutez l’espace de noms **UAP** à l’élément \<VisualElements > et à l’un de ses éléments enfants. Exemple :

   ```xml
   <uap:VisualElements
       DisplayName="My WWA App"
       Square150x150Logo="images/150x150.png"
       Square44x44Logo="images/44x44.png"
       Description="My WWA App"
       BackgroundColor="#777777">
     <uap:SplashScreen Image="images/splash.png"/>
   </uap:VisualElements>

   ```

    **S’applique uniquement à Windows Store :** les noms de tailles de vignettes ont changé. Modifiez les attributs dans l’élément \<VisualElements > pour refléter les nouvelles tailles de vignette convergées. 70x70 devient 71x71 et 30x30 devient 44x44.

    **ANCIEN :** noms de tailles de vignettes

   ```xml
   <m2:VisualElements
       …
       Square30x30Logo="Assets\SmallLogo.png"
       …>
    <m2:DefaultTile
         …
         Square70x70Logo="images/70x70.png">
   </m2:VisualElements>

   ```

    **NOUVEAU :** noms de tailles de vignettes

   ```xml
   <uap:VisualElements
       …
       Square44x44Logo="Assets\SmallLogo.png"
       …>
    <uap:DefaultTile
         …
         Square71x71Logo="images/70x70.png">
   </uap:VisualElements>

   ```

9. Ajoutez l’espace de noms **UAP** au \<ApplicationContentUriRules > et tous ses éléments enfants. Exemple :

    ```xml
    <uap:ApplicationContentUriRules>
      <uap:Rule Type="include" Match="https://www.microsoft.com/"/>
      <uap:Rule Type="exclude" Match="*.pdf"/>
    </uap:ApplicationContentUriRules>

    ```

10. Ajoutez l’espace de noms **UAP** à l’Extension de \<suivante > éléments et tous ses éléments enfants : Windows. accountPictureProvide, Windows. Alarm, Windows. appointmentsProvider Windows. autoPlayContent, Windows. autoPlayDevice, Windows. cachedFileUpdate, Windows. cameraSettings, Windows. fileOpenPicker, Windows. fileTypeAssociation, Windows. fileSavePicke, Windows. lockScreenCall, Windows. printTaskSettings, Windows. Protocol, Windows. Search, Windows. shareTarget. Exemple :

    ```xml
    <Extensions>
      <uap:Extension Category="windows.alarm"/>
      <uap:Extension Category="windows.search" EntryPoint="MyActivateableClassId.baz"/>
      <uap:Extension Category="windows.protocol">
        <uap:Protocol Name="mailto" DesiredView="useHalf">
         <uap:DisplayName>MailTo Protocol</uap:DisplayName>
        </uap:Protocol>
      </uap:Extension>
    </Extensions>

    ```

11. Ajoutez l’espace de noms **uap** aux tâches en arrière-plan de type chatMessageNotification. Exemple :

    ```xml
    <Extension Category="windows.backgroundTasks" EntryPoint="Fabrikam.BackgroundTask" Executable="MyBackground.exe">
     <BackgroundTasks ServerName="MyBackgroundTasks">
        <uap:Task Type="chatMessageNotification"/>
      </BackgroundTasks>
    </Extension>

    ```

12. Modifiez les dépendances d’infrastructure. Ajoutez un nom d’éditeur à tous les éléments \<PackageDependency > et spécifiez un MinVersion s’il n’est pas déjà spécifié.

     **Ancien :** \<élément PackageDependency >

    ```xml
    <Dependencies>
     <PackageDependency Name="Microsoft.VCLibs.120.00" />
    </Dependencies>

    ```

     **Nouveau :** \<élément PackageDependency >

    ```xml
    <Dependencies>
     <PackageDependency
          Name="Microsoft.VCLibs.120.00"
          Publisher="CN=Microsoft Corporation, O=Microsoft Corporation, L=Redmond, S=Washington, C=US"
          MinVersion="12.0.30113.0" />
    </Dependencies>

    ```

     Utilisez les valeurs appropriées de Publisher et MinVersion pour l’infrastructure réelle que vous utilisez. N’oubliez pas que ces noms peuvent changer pour Windows 10.

13. Remplacez les tâches de type gattCharacteristicNotification et rfcommConnection en arrière-plan par une tâche de type Bluetooth. Exemple :

     **ANCIEN**

    ```xml
    <Extension Category="windows.backgroundTasks" EntryPoint="Fabrikam.BackgroundTask" Executable="MyBackground.exe">
    <BackgroundTasks ServerName="MyBackgroundTasks">
                <Task Type="rfcommConnection"/>
               <Task Type="gattCharacteristicNotification"/>
    </BackgroundTasks>
    </Extension>
    ```

     **NOUVEAU :** avec la tâche de type Bluetooth.

    ```xml
    <Extension Category="windows.backgroundTasks" EntryPoint="Fabrikam.BackgroundTask" Executable="MyBackground.exe">
    <BackgroundTasks ServerName="MyBackgroundTasks">
               <Task Type="bluetooth"/>
    </BackgroundTasks>
    </Extension>
    ```

14. Remplacez les fonctionnalités d’appareil Bluetooth bluetooth.rfcomm et bluetooth.genericAttributeProfile par une fonctionnalité Bluetooth générique. Exemple :

     **ANCIEN**

    ```xml
    <Capabilities>
      <m2:DeviceCapability Name="bluetooth.rfcomm">
        <m2:Device Id="any">
         <m2:Function Type="serviceId:34B1CF4D-1069-4AD6-89B6-E161D79BE4D8"/>
        </m2:Device>
      </m2:DeviceCapability>
      <m2:DeviceCapability Name="bluetooth.genericAttributeProfile">
        <m2:Device Id="any">
         <m2:Function Type="name:heartRate"/>
        </m2:Device>
      </m2:DeviceCapability>
    </Capabilities>
    ```

     **NOUVEAU :** après remplacement par une fonctionnalité Bluetooth générique.

    ```xml
    <Capabilities>
      <uap:DeviceCapability Name="bluetooth"/>
    </Capabilities>

    ```

15. Supprimez tout élément déconseillé.

    1. Ces attributs pour \<> VisualElements sont déconseillés et doivent être supprimés :

       - \<VisualElements > attributs : ForegroundText, ToastCapable

       - L’attribut \<DefaultTile > default

       - Élément \<ApplicationView >

         Exemple :

       ```xml
       <m2:VisualElements
           …
           ForegroundText="dark"
           ToastCapable="true">
       <m2:DefaultTile DefaultSize="square150x150Logo"/>
         <m2:ApplicationView MinWidth="width320"/>
       </m2:VisualElements>

       ```

    2. Supprimez les extensions Windows.contact et windows.contactPicker et tous les éléments figurant sous ces extensions.

16. Enregistrez le fichier Package.appxmanifest. Fermez ensuite Visual Studio.

17. Vous devez supprimer certains fichiers cachés avant de rouvrir votre solution.

    1. Ouvrez l’Explorateur de fichiers, cliquez sur **Affichage** dans la barre d’outils, puis sélectionnez **Éléments masqués** et **Extensions de noms de fichiers**. Ouvrez ce dossier sur votre ordinateur : \<chemin d’accès de l’emplacement de votre solution >\\. vs\\{nom du projet} \v14. S’il existe un fichier avec une extension .suo, supprimez-le.

    2. Retournez à présent dans le dossier où se trouve votre solution. Ouvrez tous les dossiers des projets figurant dans votre solution. Si un fichier figurant dans l’un de ces dossiers de projet a une extension .csproj.user ou .vbproj.user, supprimez-le.

         Vous pouvez à présent rouvrir votre solution dans Visual Studio. Vous êtes prêt à coder, générer et déboguer votre application à l’aide de la plateforme Windows universelle.

         Découvrez comment [adapter votre code](https://msdn.microsoft.com/library/windows/apps/dn954974.aspx) pour tirer parti des nouveautés de la plateforme Windows universelle.

## <a name="PreviousVersions"></a>Modifications requises pour les applications Windows universelles existantes créées avec Visual Studio 2015 RC
 Si vous avez créé des applications Windows 10 universelles à l’aide de Visual Studio 2015 RC, vous devez recibler votre projet pour utiliser la version de la plateforme Windows universelle installée avec la dernière version de Visual Studio 2015. Aucune version antérieure n’est prise en charge. Les modifications requises sont différentes selon le langage que vous avez utilisé pour créer votre application :

- [C#Applications/VB](#RCUpdate10CSharp)

- [C++applications](#RCUpdate10CPlusPlus)

### <a name="RCUpdate10CSharp"></a>Mettez à C#jour vos projets/VB pour utiliser la dernière plateforme Windows universelle
 Quand vous ouvrez votre solution pour votre application existante, vous voyez que votre application nécessite une mise à jour :

 ![Afficher votre projet dans Explorateur de solutions](../misc/media/uwp-updaterequired.png "UWP_UpdateRequired")

 Si vous choisissez de recharger ce projet à partir de l’Explorateur de solutions, cette boîte de dialogue s’affiche :

 ![Reciblez votre application pour utiliser le kit de développement logiciel (SDK) approprié](../misc/media/missingsdkforuap.png "MissingSDKforUAP")

 Comme le Kit de développement logiciel (SDK) de la plateforme Windows universelle pour votre projet n’est plus pris en charge, vous ne pouvez pas l’installer. Cliquez simplement sur OK et suivez la procédure ci-dessous.

##### <a name="update-your-cvb-projects-to-use-the-latest-universal-windows-platform"></a>Mettre à jour vos projets C#/Visual Basic pour utiliser la plateforme Windows universelle la plus récente

1. Pour déterminer quelle plateforme Windows universelle vous avez installée, ouvrez ce dossier : **\Program Files (x86)\Windows Kits\10\Platforms\UAP**. Il contient une liste de dossiers pour chaque plateforme Windows universelle installée. Le nom du dossier correspond à la version de la plateforme Windows universelle que vous avez installée. Par exemple, cet appareil Windows 10 est équipé de la version 10.0.10240.0 de la plateforme Windows universelle.

    ![Ouvrir le dossier pour afficher les versions installées](../misc/media/uap-uwpversions.png "UAP_UWPVersions")

    Plusieurs versions de la plateforme Windows universelle peuvent être installées. Nous vous recommandons d’utiliser la version la plus récente pour votre application.

2. Dans l’Explorateur de fichiers, accédez au dossier où votre projet de plateforme Windows universelle est stocké. Supprimez le fichier packages.config et créez un nouveau fichier .json dans ce dossier. Nommez le fichier : project.json, puis ajoutez le contenu suivant à ce fichier :

   ```json

   {
     "dependencies": {
       "Microsoft.ApplicationInsights": "1.0.0",
       "Microsoft.ApplicationInsights.PersistenceChannel": "1.0.0",
       "Microsoft.ApplicationInsights.WindowsApps": "1.0.0",
       "Microsoft.NETCore.UniversalWindowsPlatform": "5.0.0"
     },
     "frameworks": {
       "uap10.0": {}
     },
     "runtimes": {
       "win10-arm": {},
       "win10-arm-aot": {},
       "win10-x86": {},
       "win10-x86-aot": {},
       "win10-x64": {},
       "win10-x64-aot": {}
     }
   }

   ```

3. Utilisez Visual Studio pour ouvrir votre solution contenant votre application Windows universelle C#/VB. Vous verrez que votre fichier projet (fichier .csproj ou .vbproj) doit être mis à jour. Cliquez avec le bouton droit sur le fichier projet et choisissez de modifier ce fichier.

    ![Cliquez avec le bouton droit sur le projet, puis choisissez Modifier.](../misc/media/uap-editproject.png "UAP_EditProject")

4. Recherchez l’élément \<PropertyGroup > qui contient les éléments \<TargetPlatformVersion > et \<TargetPlatformMinVersion >. Modifiez la valeur existante des éléments \<TargetPlatformVersion > et \<TargetPlatformMinVersion > pour qu’ils soient identiques à ceux de la plateforme Windows universelle que vous avez installée.

    L’échelle par défaut des ressources pour les applications Windows universelles est 200. Les projets créés avec Visual Studio 2015 RC comprenaient les ressources mises à l’échelle à 100, vous devez ajouter un élément \<UapDefaultAssetScale > avec une valeur de 100 à ce PropertyGroup. En savoir plus sur les [ressources et échelles](https://msdn.microsoft.com/library/jj679352.aspx).

5. Si vous avez ajouté des références aux Kits de développement logiciel (SDK) d’extension de la plateforme Windows universelle (par exemple, au Kit de développement logiciel Windows Mobile), vous devez mettre à jour la version du Kit de développement logiciel (SDK). Par exemple, cet \<élément SDKReference >:

   ```xml
   <SDKReference Include="WindowsMobile, Version=10.0.0.1">
         <Name>Microsoft Mobile Extension SDK for Universal App Platform</Name>
   </SDKReference>

   ```

    doit être remplacé par :

   ```xml
   <SDKReference Include="WindowsMobile, Version=10.0.10240.0">
         <Name>Microsoft Mobile Extension SDK for Universal App Platform</Name>
   </SDKReference>

   ```

6. Recherchez l’élément \<target > avec un attribut name ayant la valeur : EnsureNuGetPackageBuildImports. Supprimez cet élément et tous ses enfants.

   ```xml
   <Target Name="EnsureNuGetPackageBuildImports" BeforeTargets="PrepareForBuild">
       <PropertyGroup>
         <ErrorText>This project references NuGet package(s) that are missing on this computer. Use NuGet Package Restore to download them.  For more information, see http://go.microsoft.com/fwlink/?LinkID=322105. The missing file is {0}.</ErrorText>
       </PropertyGroup>
       <Error Condition="!Exists('..\packages\Microsoft.Diagnostics.Tracing.EventSource.Redist.1.1.16-beta\build\portable-net45+win8+wpa81\Microsoft.Diagnostics.Tracing.EventSource.Redist.targets')" Text="$([System.String]::Format('$(ErrorText)', '..\packages\Microsoft.Diagnostics.Tracing.EventSource.Redist.1.1.16-beta\build\portable-net45+win8+wpa81\Microsoft.Diagnostics.Tracing.EventSource.Redist.targets'))" />
       <Error Condition="!Exists('..\packages\Microsoft.ApplicationInsights.0.14.3-build00177\build\portable-win81+wpa81\Microsoft.ApplicationInsights.targets')" Text="$([System.String]::Format('$(ErrorText)', '..\packages\Microsoft.ApplicationInsights.0.14.3-build00177\build\portable-win81+wpa81\Microsoft.ApplicationInsights.targets'))" />
   </Target>
   ```

7. Recherchez et supprimez les éléments de > \<importer avec les attributs de projet et de condition qui font référence à Microsoft. Diagnostics. Tracing. EventSource et Microsoft. ApplicationInsights, comme suit :

   ```xml
   <Import Project="..\packages\Microsoft.Diagnostics.Tracing.EventSource.Redist.1.1.16-beta\build\portable-net45+win8+wpa81\Microsoft.Diagnostics.Tracing.EventSource.Redist.targets" Condition="Exists('..\packages\Microsoft.Diagnostics.Tracing.EventSource.Redist.1.1.16-beta\build\portable-net45+win8+wpa81\Microsoft.Diagnostics.Tracing.EventSource.Redist.targets')" />
   <Import Project="..\packages\Microsoft.ApplicationInsights.0.14.3-build00177\build\portable-win81+wpa81\Microsoft.ApplicationInsights.targets" Condition="Exists('..\packages\Microsoft.ApplicationInsights.0.14.3-build00177\build\portable-win81+wpa81\Microsoft.ApplicationInsights.targets')" />

   ```

8. Recherchez la \<ItemGroup > qui a \<référencer > éléments enfants dans des packages NuGet. Notez les packages NuGet référencés, car vous avez besoin de ces informations pour une prochaine étape. Une différence importante concernant le format de projet Windows 10 entre Visual Studio 2015 RC et Visual Studio 2015 RTM est que le format RTM utilise [NuGet](https://docs.microsoft.com/nuget/) version 3.

    Supprimez le \<ItemGroup > et tous ses enfants. Par exemple, un projet de plateforme Windows universelle créé à l’aide de Visual Studio RC inclut les packages NuGet suivants qu’il convient de supprimer :

   ```xml
   <ItemGroup>
       <Reference Include="Microsoft.ApplicationInsights, Version=0.14.3.177, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL">
         <HintPath>..\packages\Microsoft.ApplicationInsights.0.14.3-build00177\lib\portable-win81+wpa81\Microsoft.ApplicationInsights.dll</HintPath>
         <Private>True</Private>
       </Reference>
       <Reference Include="Microsoft.ApplicationInsights.Extensibility.Windows, Version=0.14.3.177, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL">
         <HintPath>..\packages\Microsoft.ApplicationInsights.WindowsApps.0.14.3-build00177\lib\win81\Microsoft.ApplicationInsights.Extensibility.Windows.dll</HintPath>
         <Private>True</Private>
       </Reference>
       <Reference Include="Microsoft.ApplicationInsights.PersistenceChannel, Version=0.14.3.186, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL">
         <HintPath>..\packages\Microsoft.ApplicationInsights.PersistenceChannel.0.14.3-build00177\lib\portable-win81+wpa81\Microsoft.ApplicationInsights.PersistenceChannel.dll</HintPath>
         <Private>True</Private>
       </Reference>
       <Reference Include="System.Numerics.Vectors, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL">
         <HintPath>..\packages\System.Numerics.Vectors.4.0.0\lib\win8\System.Numerics.Vectors.dll</HintPath>
         <Private>True</Private>
       </Reference>
       <Reference Include="System.Numerics.Vectors.WindowsRuntime, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL">
         <HintPath>..\packages\System.Numerics.Vectors.4.0.0\lib\win8\System.Numerics.Vectors.WindowsRuntime.dll</HintPath>
         <Private>True</Private>
       </Reference>
     </ItemGroup>

   ```

9. Recherchez l' \<élément ItemGroup > contenant un élément \<AppxManifest >. S’il existe un élément \<aucun > avec un attribut include défini sur : packages. config, supprimez-le. Ajoutez également un élément \<aucun > avec un attribut include et affectez-lui la valeur : Project. JSON.

10. Enregistrez les modifications apportées. Ensuite, fermez le fichier projet.

11. Cliquez avec le bouton droit sur votre fichier projet dans l’Explorateur de solutions et choisissez Recharger le projet dans le menu contextuel. Tous les fichiers de votre projet doivent désormais être affichés dans l’Explorateur de solutions.

12. Sélectionnez le fichier ApplicationInsights.config dans l’Explorateur de solutions et ouvrez ses propriétés. Attribuez à la propriété Action de génération la valeur « Contenu » et à la propriété Copier dans le répertoire de sortie la valeur « Copier si plus récent ».

13. Ouvrez le fichier Package.appxmanifest dans votre projet.

    1. Recherchez l’élément \<TargetDeviceFamily >. Modifiez ses attributs MinVersion et MaxVersionTested pour qu’ils correspondent à la version de la plateforme Windows universelle que vous avez installée. Comme ceci :

        ```xml
        <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10240.0" />
        ```

    2. Enregistrez les modifications apportées.

14. Utilisez le gestionnaire NuGet pour ajouter les packages que vous avez supprimés à l’étape précédente. Une différence importante concernant le format de projet Windows 10 entre Visual Studio 2015 RC et Visual Studio 2015 RTM est que le format RTM utilise [NuGet](https://docs.microsoft.com/nuget/) version 3.

    Vous pouvez désormais coder, générer et déboguer votre application.

    Si vous avez des projets de test unitaire pour vos applications Windows universelles, vous devez aussi suivre [cette procédure](#MigrateUnitTest).

### <a name="RCUpdate10CPlusPlus"></a>Mettez à C++ jour vos projets pour utiliser la dernière plateforme Windows universelle

1. Pour déterminer quelle plateforme Windows universelle vous avez installée, ouvrez ce dossier : **\Program Files (x86)\Windows Kits\10\Platforms\UAP**. Il contient une liste de dossiers pour chaque plateforme Windows universelle installée. Le nom du dossier correspond à la version de la plateforme Windows universelle que vous avez installée. Par exemple, cet appareil Windows 10 est équipé de la version 10.0.10240.0 de la plateforme Windows universelle.

     ![Ouvrir le dossier pour afficher les versions installées](../misc/media/uap-uwpversions.png "UAP_UWPVersions")

     Plusieurs versions de la plateforme Windows universelle peuvent être installées. Nous vous recommandons d’utiliser la version la plus récente pour votre application.

2. Ouvrez votre solution qui contient votre application Windows universelle C++. Cliquez avec le bouton droit sur le fichier projet .vcxproj et choisissez de décharger le fichier projet. Une fois le projet déchargé, cliquez de nouveau avec le bouton droit sur le fichier projet et choisissez de le modifier.

     ![Décharger le projet, puis modifier le fichier projet](../misc/media/uap-editearliercplus.png "UAP_EditEarlierCPlus")

3. Recherchez des éléments \<PropertyGroup > qui ne contiennent pas d’attribut condition mais qui contiennent un élément \<Applicationtyperevision, >. Mettez à jour la valeur ApplicationTypeRevision, de 8.2 à 10.0. Ajoutez un \<WindowsTargetPlatformVersion > et un élément \<WindowsTargetPlatformMinVersion > et définissez leurs valeurs sur la valeur de la version de plateforme Windows universelle que vous avez installée.

     Ajoutez un élément \<EnableDotNetNativeCompatibleProfile > et définissez sa valeur sur true si l’élément n’existe pas encore.

     L’échelle par défaut des ressources pour les applications Windows universelles est 200. Les projets créés avec Visual Studio 2015 RC comprenaient les ressources mises à l’échelle à 100, vous devez ajouter un élément \<UapDefaultAssetScale > avec une valeur de 100 à ce PropertyGroup. En savoir plus sur les [ressources et échelles](https://msdn.microsoft.com/library/jj679352.aspx).

     Ainsi, cet élément \<PropertyGroup > sera à présent similaire à ce qui suit :

    ```xml
    <PropertyGroup Label="Globals">
        …
        <MinimumVisualStudioVersion>14.0</MinimumVisualStudioVersion>
        <ApplicationType>Windows Store</ApplicationType>
        <ApplicationTypeRevision>10.0</ApplicationTypeRevision>
        <WindowsTargetPlatformVersion>10.0.10240.0</WindowsTargetPlatformVersion>
        <WindowsTargetPlatformMinVersion>10.0.10240.0</WindowsTargetPlatformMinVersion>
        <EnableDotNetNativeCompatibleProfile>true</EnableDotNetNativeCompatibleProfile>
        <UapDefaultAssetScale>100</UapDefaultAssetScale>
      </PropertyGroup>

    ```

4. Pour chaque élément \<PropertyGroup > restant, vérifiez si l’élément a un attribut condition avec une configuration Release. Si c’est le cas, mais qu’il ne contient pas d’élément \<UseDotNetNativeToolchain >, ajoutez-en un. Définissez la valeur de l’élément \<UseDotNetNativeToolchain > sur true, comme suit :

    ```xml
    <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|Win32'" Label="Configuration">
        <ConfigurationType>Application</ConfigurationType>
        <UseDebugLibraries>false</UseDebugLibraries>
        <WholeProgramOptimization>true</WholeProgramOptimization>
        <PlatformToolset>v140</PlatformToolset>
        <UseDotNetNativeToolchain>true</UseDotNetNativeToolchain>
      </PropertyGroup>

    ```

5. Vous devez mettre à jour l’élément \<EnableDotNetNativeCompatibleProfile > et l’élément \<UseDotNetNativeToolchain > pour activer .NET Native, mais .NET Native n’est pas activé C++ dans les modèles.

     Enregistrez les modifications apportées. Ensuite, fermez le fichier projet.

6. Cliquez avec le bouton droit sur votre fichier projet dans l’Explorateur de solutions et choisissez Recharger le projet dans le menu contextuel. Tous les fichiers de votre projet doivent désormais être affichés dans l’Explorateur de solutions.

7. Ouvrez le fichier Package.appxmanifest dans votre projet.

    1. Recherchez l’élément \<TargetDeviceFamily >. Modifiez ses attributs MinVersion et MaxVersionTested pour qu’ils correspondent à la version de la plateforme Windows universelle que vous avez installée. Comme ceci :

        ```xml
        <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10240.0" />
        ```

    2. Enregistrez les modifications apportées.

         Vous pouvez désormais coder, générer et déboguer votre application.

         Si vous avez des projets de test unitaire pour vos applications Windows universelles, vous devez aussi suivre [cette procédure](#MigrateUnitTest).

## <a name="MigrateUnitTest"></a>Modifications requises pour les projets de test unitaire existants pour les applications Windows universelles créées avec Visual Studio 2015 RC
 Si vous avez créé des projets de test unitaire pour des applications universelles Windows 10 à l’aide de Visual Studio 2015 RC, vous devez apporter ces modifications supplémentaires à vos fichiers de projet pour utiliser ces projets de test avec la dernière version de Visual Studio 2015. Les modifications requises sont différentes selon le langage que vous avez utilisé pour créer votre application :

- [C#Applications/VB](#UnitTestRCUpdate10CSharp)

- [C++applications](#UnitTestRCUpdate10CPlusPlus)

### <a name="UnitTestRCUpdate10CSharp"></a>Mettre à C#jour vos projets de test unitaire/VB

1. Utilisez Visual Studio pour ouvrir votre solution contenant votre projet de test unitaire C#/VB. Remplacez la valeur de l’élément \<OuttputType > par : AppContainerExe.

   ```xml

   <OutputType>AppContainerExe</OutputType>

   ```

2. Remplacez cet élément \<EnableCoreRuntime > false\<>/EnableCoreRuntime par l’élément suivant :

   ```xml

   <EnableDotNetNativeCompatibleProfile>true</EnableDotNetNativeCompatibleProfile>

   ```

3. Supprimez les lignes suivantes :

   ```xml

   <PropertyGroup>
       <AppXPackage>True</AppXPackage>
       <AppxPackageIncludePrivateSymbols>true</AppxPackageIncludePrivateSymbols>
    </PropertyGroup>
    <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">
    <PlatformTarget>AnyCPU</PlatformTarget>
    <DebugSymbols>true</DebugSymbols>
    <DebugType>full</DebugType>
    <Optimize>false</Optimize>
    <OutputPath>bin\Debug\</OutputPath>
    <DefineConstants>DEBUG;TRACE;NETFX_CORE;WINDOWS_UAP</DefineConstants>
    <ErrorReport>prompt</ErrorReport>
    <WarningLevel>4</WarningLevel>
    </PropertyGroup>
    <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Release|AnyCPU' ">
       <PlatformTarget>AnyCPU</PlatformTarget>
       <DebugType>pdbonly</DebugType>
       <Optimize>true</Optimize>
       <OutputPath>bin\Release\</OutputPath>
       <DefineConstants>TRACE;NETFX_CORE;WINDOWS_UAP</DefineConstants>
       <ErrorReport>prompt</ErrorReport>
       <WarningLevel>4</WarningLevel>
    </PropertyGroup>

   ```

4. Ajoutez cet élément \<UseDotNetNativeToolchain > true\</UseDotNetNativeToolchain > en tant qu’élément enfant à ces groupes de propriétés :

   ```xml

   <PropertyGroup Condition="'$(Configuration)|$(Platform)' == 'Release|ARM'">
   <PropertyGroup Condition="'$(Configuration)|$(Platform)' == 'Release|X86'">
   <PropertyGroup Condition="'$(Configuration)|$(Platform)' == 'Release|X64'">

   ```

5. Supprimez les éléments suivants \<ItemGroup >:

   ```xml

   <ItemGroup>
      <Compile Include="Properties\AssemblyInfo.cs" />
      <Compile Include="UnitTest.cs" />
   </ItemGroup>
   <ItemGroup>
      <AppxManifest Include="Package.appxmanifest">
         <SubType>Designer</SubType>
      </AppxManifest>
      <None Include="packages.config" />
      <None Include="UnitTestProject1_TemporaryKey.pfx" />
   </ItemGroup>
   <ItemGroup>
      <Content Include="Properties\Default.rd.xml" />
      <Content Include="Assets\Logo.scale-240.png" />
      <Content Include="Assets\SmallLogo.scale-240.png" />
      <Content Include="Assets\SplashScreen.scale-240.png" />
      <Content Include="Assets\Square71x71Logo.scale-240.png" />
      <Content Include="Assets\StoreLogo.scale-240.png" />
      <Content Include="Assets\WideLogo.scale-240.png" />
   </ItemGroup>

   ```

    Remplacez-les par ces éléments :

   ```xml

   <ItemGroup>
      <Compile Include="Properties\AssemblyInfo.cs" />
      <Compile Include="UnitTestApp.xaml.cs">
         <DependentUpon>UnitTestApp.xaml</DependentUpon>
      </Compile>
      <Compile Include="UnitTest.cs" />
   </ItemGroup>
   <ItemGroup>
      <ApplicationDefinition Include="UnitTestApp.xaml">
         <Generator>MSBuild:Compile</Generator>
         <SubType>Designer</SubType>
      </ApplicationDefinition>
   </ItemGroup>
   <ItemGroup>
      <AppxManifest Include="Package.appxmanifest">
         <SubType>Designer</SubType>
      </AppxManifest>
      <None Include="UnitTestProject1_TemporaryKey.pfx" />
   </ItemGroup>
   <ItemGroup>
      <Content Include="Properties\UnitTestApp.rd.xml" />
      <Content Include="Assets\LockScreenLogo.scale-200.png" />
      <Content Include="Assets\SplashScreen.scale-200.png" />
      <Content Include="Assets\Square150x150Logo.scale-200.png" />
      <Content Include="Assets\Square44x44Logo.scale-200.png" />
      <Content Include="Assets\Square44x44Logo.targetsize-24_altform-unplated.png" />
      <Content Include="Assets\StoreLogo.png" />
      <Content Include="Assets\Wide310x150Logo.scale-200.png" />
   </ItemGroup>
   ```

6. Créez un nouveau projet Test unitaire et copiez les fichiers UnitTestApp.xaml et UnitTestApp.xaml.cs de ce nouveau projet vers le projet de test unitaire existant que vous mettez à jour.

7. Copiez le fichier UnitTestApp.rd.xml du dossier Properties du nouveau projet Test unitaire vers le dossier Properties du projet de test unitaire existant que vous mettez à jour.

8. Ouvrez le fichier Package.appxmanifest dans votre projet. Ensuite, supprimez ces éléments de celui-ci :

   ```xml

   <Applications>
      <Application Id="vstest.executionengine.universal.App"
            Executable="vstest.executionengine.appcontainer.uap.exe"
            EntryPoint="Microsoft.VisualStudio.TestPlatform.TestExecutor.AppContainer.App">
         <uap:VisualElements
            DisplayName="UnitTestProject1"
            Square150x150Logo="Assets\Logo.png"
            Square44x44Logo="Assets\SmallLogo.png"
            Description="UnitTestProject1"
            BackgroundColor="#464646">
            <uap:SplashScreen Image="Assets\SplashScreen.png" />
         </uap:VisualElements>
      </Application>
   </Applications>
   <Capabilities>
      <Capability Name="internetClientServer" />
   </Capabilities>
   ```

    Remplacez les éléments supprimés par les éléments suivants. Utilisez la valeur appropriée pour ProjectName en fonction du nom de votre projet, à la place de UnitTestProject1 dans les éléments suivants :

   ```xml

   <Applications>
      <Application Id="vstest.executionengine.universal.App"
            Executable="$targetnametoken$.exe"
            EntryPoint="UnitTestProject1.App">
         <uap:VisualElements
               DisplayName="UnitTestProject1"
               Square150x150Logo="Assets\Square150x150Logo.png"
               Square44x44Logo="Assets\Square44x44Logo.png"
               Description="UnitTestProject1"
               BackgroundColor="transparent">
            <uap:DefaultTile Wide310x150Logo="Assets\Wide310x150Logo.png"/>
            <uap:SplashScreen Image="Assets\SplashScreen.png" />
         </uap:VisualElements>
      </Application>
   </Applications>
   <Capabilities>
      <Capability Name="internetClient" />
   </Capabilities>
   ```

   Vous pouvez à présent exécuter vos tests unitaires.

### <a name="UnitTestRCUpdate10CPlusPlus"></a>Mettez à C++ jour vos projets pour utiliser la dernière plateforme Windows universelle

1. Utilisez Visual Studio pour ouvrir votre solution contenant votre projet de test unitaire C++. Supprimez les éléments suivants :

    ```xml

    <TestApplication>true</TestApplication>
    <AppxPackage>True</AppxPackage>
    <CppWindowsStoreUnitTestLibraryType>true</CppWindowsStoreUnitTestLibraryType>
    <EnableCoreRuntime>false</EnableCoreRuntime>

    ```

2. Ajoutez les éléments suivants \<ProjectConfiguration > sous cet élément \<ItemGroup label = "ProjectConfigurations" > s’ils ne se trouvent pas déjà dans ce remplissage du :

    ```xml

    <ProjectConfiguration Include="Debug|x64">
       <Configuration>Debug</Configuration>
       <Platform>x64</Platform>
    </ProjectConfiguration>
    <ProjectConfiguration Include="Release|x64">
       <Configuration>Release</Configuration>
       <Platform>x64</Platform>
    </ProjectConfiguration>

    ```

3. Remplacez chaque occurrence de cet élément :

    ```xml

    <ConfigurationType>DynamicLibrary</ConfigurationType>

    ```

     Par le code :

    ```xml

    <ConfigurationType>Application</ConfigurationType>

    ```

4. Ajoutez ces éléments \<PropertyGroup > s’ils ne se trouvent pas déjà dans le fichier :

    ```xml

    <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Debug|x64'" Label="Configuration">
       <ConfigurationType>Application</ConfigurationType>
       <UseDebugLibraries>true</UseDebugLibraries>
       <PlatformToolset>v140</PlatformToolset>
    </PropertyGroup>
    <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|x64'" Label="Configuration">
       <ConfigurationType>Application</ConfigurationType>
       <UseDebugLibraries>false</UseDebugLibraries>
       <WholeProgramOptimization>true</WholeProgramOptimization>
       <PlatformToolset>v140</PlatformToolset>
       <UseDotNetNativeToolchain>true</UseDotNetNativeToolchain>
    </PropertyGroup>

    ```

5. Remplacez chaque occurrence de cet élément :

    ```xml

    <AdditionalIncludeDirectories>$(VCInstallDir)UnitTest\include;$(ProjectDir);$(IntermediateOutputPath);%(AdditionalIncludeDirectories)</AdditionalIncludeDirectories>
    ```

     Par le code :

    ```xml

    <AdditionalIncludeDirectories>$(VCInstallDir)UnitTest\include\UWP;$(ProjectDir);$(IntermediateOutputPath);%(AdditionalIncludeDirectories)</AdditionalIncludeDirectories>

    ```

6. Remplacez chaque occurrence de cet élément :

    ```xml

    <AdditionalLibraryDirectories>$(VCInstallDir)UnitTest\Lib;%(AdditionalLibraryDirectories)</AdditionalLibraryDirectories>

    ```

     Par le code :

    ```xml

    <AdditionalLibraryDirectories>$(VCInstallDir)UnitTest\lib\UWP;%(AdditionalLibraryDirectories)</AdditionalLibraryDirectories>

    ```

7. Ajoutez ces éléments \<ItemDefinitionGroup > dans la section qui contient déjà d’autres éléments \<ItemDefinitionGroup >:

    ```xml

    <ItemDefinitionGroup Condition="'$(Configuration)|$(Platform)'=='Debug|x64'">
       <ClCompile>
          <AdditionalOptions>/bigobj %(AdditionalOptions)</AdditionalOptions>
          <DisableSpecificWarnings>4453;28204</DisableSpecificWarnings>
          <AdditionalIncludeDirectories>$(VCInstallDir)UnitTest\include\UWP;$(ProjectDir);$(IntermediateOutputPath);%     (AdditionalIncludeDirectories)</AdditionalIncludeDirectories>
       </ClCompile>
    <Link>
       <AdditionalLibraryDirectories>$(VCInstallDir)UnitTest\lib\UWP;%(AdditionalLibraryDirectories)</AdditionalLibraryDirectories>
    </Link>
    </ItemDefinitionGroup>
    <ItemDefinitionGroup Condition="'$(Configuration)|$(Platform)'=='Release|x64'">
       <ClCompile>
          <AdditionalOptions>/bigobj %(AdditionalOptions)</AdditionalOptions>
          <DisableSpecificWarnings>4453;28204</DisableSpecificWarnings>
          <AdditionalIncludeDirectories>$(VCInstallDir)UnitTest\include\UWP;$(ProjectDir);$(IntermediateOutputPath);%(AdditionalIncludeDirectories)</AdditionalIncludeDirectories>
       </ClCompile>
       <Link>
          <AdditionalLibraryDirectories>$(VCInstallDir)UnitTest\lib\UWP;%(AdditionalLibraryDirectories)</AdditionalLibraryDirectories>
       </Link>
    </ItemDefinitionGroup>

    ```

8. Supprimez le \< élément ItemGroup > suivant :

    ```xml

    <ItemGroup>
       <Image Include="Assets\Logo.scale-100.png" />
       <Image Include="Assets\SmallLogo.scale-100.png" />
       <Image Include="Assets\StoreLogo.scale-100.png" />
       <Image Include="Assets\SplashScreen.scale-100.png" />
       <Image Include="Assets\WideLogo.scale-100.png" />
    </ItemGroup>

    ```

     Remplacez-le par ce \<élément ItemGroup >:

    ```xml

    <ItemGroup>
       <Image Include="Assets\LockScreenLogo.scale-200.png" />
       <Image Include="Assets\SplashScreen.scale-200.png" />
       <Image Include="Assets\Square44x44Logo.scale-200.png" />
       <Image Include="Assets\Square44x44Logo.targetsize-24_altform-unplated.png" />
       <Image Include="Assets\Square150x150Logo.scale-200.png" />
       <Image Include="Assets\StoreLogo.png" />
       <Image Include="Assets\Wide310x150Logo.scale-200.png" />
    </ItemGroup>

    ```

9. Supprimez le \< élément ItemGroup > suivant :

    ```xml

    <ItemGroup>
       <ClInclude Include="pch.h" />
    </ItemGroup>
    ```

     Remplacez-le par ces \<éléments ItemGroup >:

    ```xml

    <ItemGroup>
       <ClInclude Include="pch.h" />
       <ClInclude Include="UnitTestApp.xaml.h">
          <DependentUpon>UnitTestApp.xaml</DependentUpon>
       </ClInclude>
    </ItemGroup>
    <ItemGroup>
       <ApplicationDefinition Include="UnitTestApp.xaml">
          <SubType>Designer</SubType>
       </ApplicationDefinition>
    </ItemGroup>

    ```

10. Supprimez l’élément suivant :

    ```xml
    <ClCompile Include="UnitTest.cpp"/>
    ```

     Remplacez-le par les éléments \<CICompile > suivants :

    ```xml

    <ClCompile Include="UnitTestApp.xaml.cpp">
       <DependentUpon>UnitTestApp.xaml</DependentUpon>
    </ClCompile>
    <ClCompile Include="UnitTest.cpp"/>

    ```

11. Ajoutez cet élément :

    ```xml
    <Import Project="$(VCTargetsPath)\Microsoft.Cpp.targets" />
    ```

     Au-dessus de cet élément dans le fichier :

    ```xml

    <ItemGroup>
       <Xml Include="UnitTestApp.rd.xml" />
    </ItemGroup>
    ```

12. Créez un nouveau projet C++ Test unitaire et copiez les fichiers UnitTestApp.xaml, UnitTestApp.xaml.cs, UnitTestApp.xaml.h et UnitTestApp.rd.xml de ce projet vers le projet existant que vous mettez à jour.

13. Ouvrez le fichier Package.appxmanifest dans votre projet. Ensuite, supprimez ces éléments de celui-ci :

    ```xml

    <Applications>
       <Application Id="vstest.executionengine.universal.App"
             Executable="vstest.executionengine.appcontainer.uap.exe"
             EntryPoint="Microsoft.VisualStudio.TestPlatform.TestExecutor.AppContainer.App">
          <uap:VisualElements
             DisplayName="UnitTestProject1"
             Square150x150Logo="Assets\Logo.png"
             Square44x44Logo="Assets\SmallLogo.png"
             Description="UnitTestProject1"
             BackgroundColor="#464646">
             <uap:SplashScreen Image="Assets\SplashScreen.png" />
          </uap:VisualElements>
       </Application>
    </Applications>
    <Capabilities>
       <Capability Name="internetClientServer" />
    </Capabilities>

    ```

     Remplacez les éléments supprimés par les éléments suivants. Utilisez la valeur appropriée pour ProjectName en fonction du nom de votre projet, à la place de UnitTestProject1 dans les éléments suivants :

    ```xml

    <Applications>
       <Application Id="vstest.executionengine.universal.App"
                Executable="$targetnametoken$.exe"
                EntryPoint="UnitTestProject1.App">
          <uap:VisualElements
                DisplayName="UnitTestProject1"
                Square150x150Logo="Assets\Square150x150Logo.png"
                Square44x44Logo="Assets\Square44x44Logo.png"
                Description="UnitTestProject1"
                BackgroundColor="transparent">
                <uap:DefaultTile Wide310x150Logo="Assets\Wide310x150Logo.png"/>
                <uap:SplashScreen Image="Assets\SplashScreen.png" />
          </uap:VisualElements>
       </Application>
    </Applications>
    <Capabilities>
       <Capability Name="internetClient" />
    </Capabilities>

    ```