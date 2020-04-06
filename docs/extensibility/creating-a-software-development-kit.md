---
title: Création d’une trousse de développement logiciel (en anglais seulement) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 8496afb4-1573-4585-ac67-c3d58b568a12
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f7cf6cf092edf96280c566018231cc00d34c0994
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739595"
---
# <a name="create-a-software-development-kit"></a>Créer un kit de développement logiciel

Un kit de développement logiciel (SDK) est une collection d’API que vous pouvez référencer en tant qu’élément unique dans Visual Studio. La boîte de dialogue **du gestionnaire de référence** répertorie tous les SDK pertinents au projet. Lorsque vous ajoutez un SDK à un projet, les API sont disponibles dans Visual Studio.

Il existe deux types de SDK :

- Les SDK de la plate-forme sont des composants obligatoires pour le développement d’applications pour une plate-forme. Par exemple, [!INCLUDE[win81](../debugger/includes/win81_md.md)] le SDK [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] est nécessaire pour développer des applications.

- Les SDK d’extension sont des composants optionnels qui étendent une plate-forme mais ne sont pas obligatoires pour le développement d’applications pour cette plate-forme.

Les sections suivantes décrivent l’infrastructure générale des SDK et la façon de créer une plate-forme SDK et une extension SDK.

## <a name="platform-sdks"></a>Kits de développement logiciels (SDK) pour plateformes

Les SDK de la plate-forme sont nécessaires pour développer des applications pour une plate-forme. Par exemple, [!INCLUDE[win81](../debugger/includes/win81_md.md)] le SDK est [!INCLUDE[win81](../debugger/includes/win81_md.md)]nécessaire pour développer des applications pour .

### <a name="installation"></a>Installation

Toutes les plateformes SDK seront installées à *l’adresse HKLM-Software-Microsoft-Microsoft SDKs\\[TPI] -V[TPV]\\ @InstallationFolder - [SDK root]*. En conséquence, le [!INCLUDE[win81](../debugger/includes/win81_md.md)] SDK est installé à *HKLM-Software-Microsoft SDKs-Windows-v8.1*.

### <a name="layout"></a>Mise en page

Les SDK de la plate-forme ont la mise en page suivante :

```
\[InstallationFolder root]
            SDKManifest.xml
            \References
                  \[config]
                        \[arch]
            \DesignTime
                  \[config]
                        \[arch]
```

| Nœud | Description |
|------------------------| - |
| *Dossier de références* | Contient des binaires qui contiennent des API qui peuvent être codées contre. Il peut s’agir de fichiers ou d’assemblages De métadonnées Windows (WinMD). |
| *Dossier DesignTime* | Contient des fichiers qui ne sont nécessaires qu’au moment de la pré-exécution/débogage. Il pourrait s’agir de documents XML, bibliothèques, en-têtes, bacaires de conception toolbox,, artefacts MSBuild, et ainsi de suite<br /><br /> Les documents XML seraient, idéalement, placés dans le dossier *« DesignTime* », mais les documents XML pour les références continueront d’être placés à côté du fichier de référence dans Visual Studio. Par exemple, le doc XML pour une référence<em>\\'References\\[config] [arch] .dll</em> sera *'References\\[config]\\[arch] [arch].xml*, et la version localisée de ce doc sera *'References\\[config]\\[arch]\\[local] [sample.xml]*. |
| *Dossier de configuration* | Il ne peut y avoir que trois dossiers: *Debug*, *Retail* et *CommonConfiguration*. Les auteurs de SDK peuvent placer leurs fichiers sous *CommonConfiguration* si le même ensemble de fichiers SDK doit être consommé, quelle que soit la configuration que le consommateur SDK ciblera. |
| Dossier *d’architecture* | Tout dossier *d’architecture* pris en charge peut exister. Visual Studio prend en charge les architectures suivantes : x86, x64, ARM et neutre. Note: Cartes Win32 à x86, et AnyCPU cartes à neutre.<br /><br /> MSBuild ne semble que sous *'CommonConfiguration’neutre* pour la plate-forme SDKs. |
| *SDKManifest.xml* | Ce fichier décrit comment Visual Studio devrait consommer le SDK. Regardez le Manifeste SDK pour [!INCLUDE[win81](../debugger/includes/win81_md.md)]:<br /><br /> `<FileList             DisplayName = "Windows"             PlatformIdentity = "Windows, version=8.1"             TargetFramework = ".NET for Windows Store apps, version=v4.5.1; .NET Framework, version=v4.5.1"             MinVSVersion = "14.0">              <File Reference = "Windows.winmd">                <ToolboxItems VSCategory = "Toolbox.Default" />             </File> </FileList>`<br /><br /> **DisplayName:** La valeur que le navigateur d’objet affiche dans la liste De navigation.<br /><br /> **PlateformeIdentity:** L’existence de cet attribut indique Visual Studio et MSBuild que le SDK est une plate-forme SDK et que les références ajoutées à partir de lui ne devraient pas être copiés localement.<br /><br /> **TargetFramework:** Cet attribut est utilisé par Visual Studio pour s’assurer que seuls les projets qui ciblent les mêmes cadres que spécifiés dans la valeur de cet attribut peuvent consommer le SDK.<br /><br /> **MinVSVersion:** Cet attribut est utilisé par Visual Studio pour ne consommer que les SDK qui s’appliquent à elle.<br /><br /> **Référence:** Cet attribut doit être spécifié uniquement pour les références qui contiennent des contrôles. Pour plus d’informations sur la façon de spécifier si une référence contient des contrôles, voir ci-dessous. |

## <a name="extension-sdks"></a>Kits de développement logiciel (SDK) d’extension

Les sections suivantes décrivent ce que vous devez faire pour déployer une extension SDK.

### <a name="installation"></a>Installation

Les SDK d’extension peuvent être installés pour un utilisateur spécifique ou pour tous les utilisateurs sans spécifier une clé de registre. Pour installer un SDK pour tous les utilisateurs, utilisez le chemin suivant :

*%Fichiers de programme % -Microsoft\<\>SDKs plate-forme\>cible 'v<numéro de version de plate-forme 'ExtensionSDKs*

Pour une installation spécifique à l’utilisateur, utilisez le chemin suivant :

*%USERPROFILE % -AppData-Local-Microsoft SDKs\<plate-forme\>cible 'v<numéro\>de version de plate-forme 'ExtensionSDKs*

Si vous voulez utiliser un endroit différent, vous devez faire l’une des deux choses:

1. Spécifier dans une clé de registre :

     **La\<plate-forme cible HKLM-Software-Microsoft-Microsoft SDKs>-v<\>numéro de version\<de la plate-forme \<'ExtensionSDKs SDKName>SDKVersion>**\

     et ajouter un sous-clé (Par `<path to SDK><SDKName><SDKVersion>`défaut) qui a une valeur de .

2. Ajoutez la propriété `SDKReferenceDirectoryRoot` MSBuild à votre dossier de projet. La valeur de cette propriété est une liste délimitée des points-virgules des répertoires dans lesquels résident les SDK d’extension dans lesquelles résident les SDK d’extension que vous souhaitez référencer.

### <a name="installation-layout"></a>Disposition d’installation

Les SDK d’extension ont la disposition d’installation suivante :

```
\<ExtensionSDKs root>
           \<SDKName>
                 \<SDKVersion>
                        SDKManifest.xml
                        \References
                              \<config>
                                    \<arch>
                        \Redist
                              \<config>
                                    \<arch>
                        \DesignTime
                               \<config>
                                     \<arch>

```

1. \\<SDKName\> \\<SDKVersion\>: le nom et la version de l’extension SDK sont dérivés des noms de dossier correspondants sur le chemin de la racine SDK. MSBuild utilise cette identité pour trouver le SDK sur disque, et Visual Studio affiche cette identité dans la fenêtre **Properties** et le dialogue **Reference Manager.**

2. *Dossier de références* : les binaires qui contiennent les API. Il peut s’agir de fichiers ou d’assemblages Windows Metadata (WinMD).

3. *Dossier Redist:* les fichiers qui sont nécessaires pour le temps d’exécution / débogage et doit être emballé dans le cadre de l’application de l’utilisateur. Tous les binaires doivent être placés en dessous *\\ de la<\> \\ config<\>arche,* et les noms binaires devraient avoir le format suivant pour assurer l’unicité: *]*\<> de l’entreprise. \<> de produits. \<> de but. \<extension><em>. Par exemple, microsoft.Cpp.Build.dll</em>. Tous les fichiers avec des noms qui peuvent entrer en collision avec les noms de fichiers d’autres SDK (par exemple, javascript, css, pri, xaml, png, et jpg fichiers) doivent être placés sous <em>le<\\ 'redist\> \\ \> \\<'arc<sdkname\> \* excepté pour les fichiers qui sont associés aux contrôles XAML. Ces fichiers doivent être placés\\ sous le nom\> \\ de\> \\ composant\><de l'<arc<</em>.

4. *Dossier DesignTime* : les fichiers qui sont nécessaires à l’heure de pré-exécution/débogage et ne devraient pas être emballés dans le cadre de l’application de l’utilisateur. Il peut s’agir de documents XML, de bibliothèques, d’en-têtes, de binaires de conception-temps de boîte à outils, d’artefacts MSBuild, et ainsi de suite. Tout SDK destiné à la consommation par un projet natif doit disposer d’un fichier *SDKName.props.* Ce qui suit montre un échantillon de ce type de fichier.

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
     <PropertyGroup>
       <ExecutablePath>C:\Temp\ExecutablePath;$(ExecutablePath)</ExecutablePath>
       <IncludePath>$(FrameworkSDKRoot)\..\v8.1\ExtensionSDKs\cppimagingsdk\1.0\DesignTime\CommonConfiguration\Neutral\include;$(IncludePath)</IncludePath>
       <AssemblyReferencePath>C:\Temp\AssemblyReferencePath;(AssemblyReferencePath)</AssemblyReferencePath>
       <LibraryPath>$(FrameworkSDKRoot)\..\v8.1\ExtensionSDKs\cppimagingsdk\1.0\DesignTime\Debug\ARM;$(LibraryPath)</LibraryPath>
       <SourcePath>C:\Temp\SourcePath\X64;$(SourcePath)</SourcePath>
       <ExcludePath>C:\Temp\ExcludePath\X64;$(ExcludePath)</ExcludePath>
       <_PropertySheetDisplayName>DevILSDK, 1.0</_PropertySheetDisplayName>
     </PropertyGroup>
   </Project>

   ```

    Les documents de référence XML sont placés à côté du fichier de référence. Par exemple, le document de référence XML pour les *«Références\\<config\> \\<'assemblage\>arch.dll* est *«Références\\<config\> \\<arch\>.xml*, et la version localisée de ce doc est *«Références\\<config\> \\<arc\> \\<local\>.sample.xml*.

5. *Dossier de configuration* : trois sous-plis : *Debug*, *Retail,* et *CommonConfiguration*. Les auteurs de SDK peuvent placer leurs fichiers sous *CommonConfiguration* lorsque le même ensemble de fichiers SDK doit être consommé, quelle que soit la configuration ciblée par le consommateur SDK.

6. Dossier *d’architecture* : les architectures suivantes sont prises en charge : x86, x64, ARM, neutre. Cartes Win32 à x86, et AnyCPU cartes à neutre.

### <a name="sdkmanifestxml"></a>SDKManifest.xml

Le fichier *SDKManifest.xml* décrit comment Visual Studio devrait consommer le SDK. Par exemple :

```
<FileList>
DisplayName = "My SDK"
ProductFamilyName = "My SDKs"
TargetFramework = ".NETCore, version=v4.5.1; .NETFramework, version=v4.5.1"
MinVSVersion = "14.0"
MaxPlatformVersion = "8.1"
AppliesTo = "WindowsAppContainer + WindowsXAML"
SupportPrefer32Bit = "True"
SupportedArchitectures = "x86;x64;ARM"
SupportsMultipleVersions = "Error"
CopyRedistToSubDirectory = "."
DependsOn = "SDKB, version=2.0"
MoreInfo = "https://msdn.microsoft.com/MySDK">
<File Reference = "MySDK.Sprint.winmd" Implementation = "XNASprintImpl.dll">
<Registration Type = "Flipper" Implementation = "XNASprintFlipperImpl.dll" />
<Registration Type = "Flexer" Implementation = "XNASprintFlexerImpl.dll" />
<ToolboxItems VSCategory = "Toolbox.Default" />
</File>
</FileList>
```

La liste suivante donne les éléments du fichier :

1. DisplayName : la valeur qui apparaît dans le gestionnaire de référence, l’explorateur de solution, le navigateur d’objets et d’autres emplacements dans l’interface utilisateur pour Visual Studio.

2. ProductFamilyName: Le nom global du produit SDK. Par exemple, [!INCLUDE[winjs_long](../debugger/includes/winjs_long_md.md)] le SDK est nommé "Microsoft.WinJS.1.0" et "Microsoft.WinJS.2.0", qui appartiennent à la même famille de produits SDK famille, "Microsoft.WinJS". Cet attribut permet à Visual Studio et MSBuild de faire cette connexion. Si cet attribut n’existe pas, le nom SDK est utilisé comme nom de famille du produit.

3. FrameworkIdentity: Specifie une dépendance à l’égard d’une ou plusieurs bibliothèques de composants Windows. La valeur de cet attribut est mise dans le manifeste de l’application consommatrice. Cet attribut ne s’applique qu’aux bibliothèques de composants Windows.

4. TargetFramework : Specifie les SDK disponibles dans le gestionnaire de référence et la boîte à outils. Il s’agit d’une liste de surnoms de cadres cibles, par exemple ".NET Framework, version-v2.0; .NET Framework, version-v4.5.1". Si plusieurs versions d’un même cadre cible sont spécifiées, le gestionnaire de référence utilise la version spécifiée la plus basse à des fins de filtrage. Par exemple, si ".NET Framework, version-v2.0; .NET Framework, version v4.5.1" est spécifié, Le gestionnaire de référence utilisera ".NET Framework, version’v2.0". Si un profil-cadre cible spécifique est spécifié, seul ce profil sera utilisé par le gestionnaire de référence à des fins de filtrage. Par exemple, lorsque «Silverlight, version v4.0, profil WindowsPhone» est spécifié, Le gestionnaire de référence filtre uniquement sur le profil Windows Phone; un projet ciblant l’ensemble du cadre Silverlight 4.0 ne voit pas le SDK dans le gestionnaire de référence.

5. MinVSVersion: La version minimum Visual Studio.

6. MaxPlatformVerson: La version maximale de la plate-forme cible doit être utilisée pour spécifier les versions de la plate-forme sur lesquelles votre Extension SDK ne fonctionnera pas. Par exemple, le forfait Runtime Microsoft Visual CMD v11.0 ne doit être référencé que par les projets Windows 8. Ainsi, le projet Windows 8 MaxPlatformVersion est 8.0. Cela signifie que le gestionnaire de référence filtre le forfait Runtime Microsoft Visual CMD pour un projet Windows [!INCLUDE[win81](../debugger/includes/win81_md.md)] 8.1, et MSBuild lance une erreur lorsqu’un projet la fait référence. Remarque : cet élément [!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)]est pris en charge à partir de .

7. ApplicableTo: Specifie les SDK qui sont disponibles dans le gestionnaire de référence en spécifiant les types de projets Visual Studio applicables. Neuf valeurs sont reconnues : WindowsAppContainer, VisualC, VB, CSharp, WindowsXAML, JavaScript, Managed et Native. L’auteur SDK peut utiliser et ("'), ou ("&#124;"), pas ("!") de spécifier exactement la portée des types de projets qui s’appliquent au SDK.

    WindowsAppContainer identifie des [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] projets pour les applications.

8. SupportPrefer32Bit: Les valeurs prises en charge sont "Vraies" et "Fausses". La valeur par défaut est "True". Si la valeur est définie à "Faux", MSBuild renvoie une erreur pour [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] les projets (ou un avertissement pour les projets de bureau) si le projet qui fait référence à la SDK a Activé Prefer32Bit. Pour plus d’informations sur Prefer32Bit, voir [Page Build, Concepteur de projets (C)](../ide/reference/build-page-project-designer-csharp.md) ou [Compile page, Concepteur de projet (Visual Basic)](../ide/reference/compile-page-project-designer-visual-basic.md).

9. Archives soutenues : Une liste d’architectures délimitées par les semi-remorques que le SDK prend en charge. MSBuild affiche un avertissement si l’architecture SDK ciblée dans le projet de consommation n’est pas pris en charge. Si cet attribut n’est pas spécifié, MSBuild n’affiche jamais ce type d’avertissement.

10. SupportsMultipleVersions: Si cet attribut est défini à **l’erreur** ou **l’avertissement**, MSBuild indique que le même projet ne peut pas référencer plusieurs versions de la même famille SDK. Si cet attribut n’existe pas ou est configuré pour **autoriser,** MSBuild n’affiche pas ce type d’erreur ou d’avertissement.

11. AppX: Specifie le chemin vers les paquets d’applications pour la bibliothèque de composants Windows sur le disque. Cette valeur est transmise au composant d’enregistrement de la bibliothèque de composants Windows lors du débogage local. La convention de nommage du nom de fichier est * \<> de la\< Société. Produit>. \<Architecture>. \<Configuration>. Version \<>.appx*. Configuration et Architecture sont facultatifs dans le nom d’attribut et la valeur d’attribut si elles ne s’appliquent pas à la bibliothèque de composants Windows. Cette valeur ne s’applique qu’aux bibliothèques de composants Windows.

12. CopyRedistToSubDirectory: Précise où les fichiers sous le dossier *de redist* doivent être copiés par rapport à la racine du paquet d’application (c’est-à-dire, **l’emplacement du paquet** choisi dans **l’assistant Create App Package)** et la racine de mise en page runtime. L’emplacement par défaut est la racine du paquet d’applications et de la mise en page **F5.**

13. DependsOn: Une liste d’identités SDK qui définissent les SDK dont dépend ce SDK. Cet attribut apparaît dans le volet détails du gestionnaire de référence.

14. MoreInfo: L’URL de la page web qui fournit de l’aide et plus d’informations. Cette valeur est utilisée dans le lien Plus d’informations dans le volet droit du gestionnaire de référence.

15. Type d’inscription: Specifie l’enregistrement WinMD dans le manifeste de l’application et est nécessaire pour le natif WinMD, qui a une mise en œuvre de contrepartie DLL.

16. Référence de fichier : Spécifiée uniquement pour les références qui contiennent des contrôles ou qui sont des WinMD natifs. Pour plus d’informations sur la façon de spécifier si une référence contient des contrôles, voir [Spécifier l’emplacement des éléments de boîte à outils](#ToolboxItems) ci-dessous.

## <a name="specify-the-location-of-toolbox-items"></a><a name="ToolboxItems"></a>Spécifier l’emplacement des éléments de boîte à outils

**L’élément ToolBoxItems** du schéma *SDKManifest.xml* spécifie la catégorie et l’emplacement des éléments de boîte à outils dans les SDK de plate-forme et d’extension. Les exemples suivants montrent comment spécifier différents endroits. Ceci s’applique aux références WinMD ou DLL.

1. Placez les commandes dans la catégorie par défaut de boîte à outils.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Toolbox.Default"/>
    </File>
    ```

2. Placer les commandes sous un nom de catégorie particulier.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory= "MyCategoryName"/>
    </File>
    ```

3. Placer les commandes sous des noms de catégories particuliers.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Graph">
        <ToolboxItems/>
        <ToolboxItems VSCategory = "Data">
        <ToolboxItems />
    </File>
    ```

4. Placez les commandes sous différents noms de catégorie dans Blend et Visual Studio.

    ```xml
    // Blend accepts a slightly different structure for the category name because it allows a path rather than a single category.
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Graph" BlendCategory = "Controls/sample/Graph">
        <ToolboxItems />
    </File>
    ```

5. Énumérer les contrôles spécifiques différemment dans Blend et Visual Studio.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Graph">
        <ToolboxItems/>
        <ToolboxItems BlendCategory = "Controls/sample/Graph">
        <ToolboxItems/>
    </File>
    ```

6. Énumérer des contrôles spécifiques et les placer sous le Visual Studio Common Path ou uniquement dans le groupe All Controls.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Toolbox.Common">
        <ToolboxItems />
        <ToolboxItems VSCategory = "Toolbox.All">
        <ToolboxItems />
    </File>
    ```

7. Énumérer des contrôles spécifiques et afficher seulement un ensemble spécifique dans ChooseItems sans qu’ils soient dans la boîte à outils.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Toolbox.ChooseItemsOnly">
        <ToolboxItems />
    </File>
    ```

## <a name="see-also"></a>Voir aussi

- [Procédure pas à pas : Créez un SDK à l’aide de C](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)
- [Procédure pas à pas : Créez un SDK à l’aide de CMD ou de Visual Basic](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)
- [Gérer les références dans un projet](../ide/managing-references-in-a-project.md)
