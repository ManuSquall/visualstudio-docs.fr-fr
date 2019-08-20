---
title: Création d’un kit de développement logiciel | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 8496afb4-1573-4585-ac67-c3d58b568a12
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 042002b6fddb674c0f1c156be2d992cc96cb9f81
ms.sourcegitcommit: a124076dfd6b4e5aecda4d01984fee7b0c034745
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2019
ms.locfileid: "68787669"
---
# <a name="create-a-software-development-kit"></a>Créer un kit de développement logiciel

Un kit de développement logiciel (SDK) est un ensemble d’API que vous pouvez référencer en tant qu’élément unique dans Visual Studio. La boîte de dialogue **Gestionnaire de références** répertorie tous les kits de développement logiciel (SDK) pertinents pour le projet. Lorsque vous ajoutez un kit de développement logiciel (SDK) à un projet, les API sont disponibles dans Visual Studio.

Il existe deux types de kits de développement logiciel:

- Les kits de développement logiciel de plateforme sont des composants obligatoires pour le développement d’applications pour une plateforme. Par exemple, le [!INCLUDE[win81](../debugger/includes/win81_md.md)] Kit de développement logiciel ( [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] SDK) est requis pour développer des applications.

- Les kits de développement logiciel (SDK) d’extension sont des composants facultatifs qui étendent une plate-forme, mais ne sont pas obligatoires pour le développement d’applications

Les sections suivantes décrivent l’infrastructure générale des kits de développement logiciel (SDK) et expliquent comment créer un SDK de plateforme et un SDK d’extension.

## <a name="platform-sdks"></a>Kits de développement Platform SDK

Les kits de développement logiciel (SDK) de plateforme sont requis pour développer des applications pour une plateforme. Par exemple, le [!INCLUDE[win81](../debugger/includes/win81_md.md)] Kit de développement logiciel (SDK) [!INCLUDE[win81](../debugger/includes/win81_md.md)]est requis pour développer des applications pour.

### <a name="installation"></a>Installation

Tous les kits de développement logiciel de plateforme seront installés dans *HKLM\Software\Microsoft\Microsoft\\SDK [TPI]\\ \v [TPV]@InstallationFolder = [root SDK]* . En conséquence, [!INCLUDE[win81](../debugger/includes/win81_md.md)] le kit de développement logiciel (SDK) est installé sur *HKLM\Software\Microsoft\Microsoft SDKs\Windows\v8.1*.

### <a name="layout"></a>Mise en page

Les kits de développement Platform SDK présentent la disposition suivante:

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
| Dossier *références* | Contient des fichiers binaires qui contiennent des API qui peuvent être codées. Celles-ci peuvent inclure des fichiers ou des assemblys de métadonnées Windows (WinMD). |
| Dossier *designtime* | Contient les fichiers qui sont nécessaires uniquement au moment de la pré-exécution/du débogage. Il peut s’agir d’un document XML, de bibliothèques, d’en-têtes, de fichiers binaires au moment du design de la boîte à outils, d’artefacts MSBuild, etc.<br /><br /> Dans l’idéal, les documents XML sont placés dans le dossier *\DesignTime* , mais les documents XML pour les références continueront d’être placés avec le fichier de référence dans Visual Studio. Par exemple, le document XML pour une référence<em>\References\\[config]\\[Arch] \Sample.dll</em> sera *\References\\[config]\\[Arch] \Sample.xml*, et la version localisée de ce document sera *\\\References\\[config]\\[Arch] [paramètres régionaux] \Sample.xml*. |
| Dossier de *configuration* | Il ne peut y avoir que trois dossiers: *Débogage*, *détail* et *CommonConfiguration*. Les auteurs du SDK peuvent placer leurs fichiers sous *CommonConfiguration* si le même jeu de fichiers du kit de développement logiciel (SDK) doit être consommé, quelle que soit la configuration ciblée par le consommateur du kit de développement logiciel (SDK). |
| Dossier d' *architecture* | Tout dossier d' *architecture* pris en charge peut exister. Visual Studio prend en charge les architectures suivantes: x86, x64, ARM et neutre. Remarque : Win32 est mappé à x86 et AnyCPU est mappé à Neutral.<br /><br /> MSBuild regarde uniquement sous *\CommonConfiguration\neutral* pour les kits de développement logiciel de plateforme. |
| *SDKManifest.xml* | Ce fichier décrit la façon dont Visual Studio doit utiliser le kit de développement logiciel (SDK). Examinez le manifeste du SDK [!INCLUDE[win81](../debugger/includes/win81_md.md)]pour:<br /><br /> `<FileList             DisplayName = "Windows"             PlatformIdentity = "Windows, version=8.1"             TargetFramework = ".NET for Windows Store apps, version=v4.5.1; .NET Framework, version=v4.5.1"             MinVSVersion = "14.0">              <File Reference = "Windows.winmd">                <ToolboxItems VSCategory = "Toolbox.Default" />             </File> </FileList>`<br /><br /> **DisplayName :** Valeur que l’Explorateur d’objets affiche dans la liste de navigation.<br /><br /> **PlatformIdentity:** L’existence de cet attribut indique à Visual Studio et à MSBuild que le kit de développement logiciel (SDK) est un kit de développement logiciel (SDK) de plate-forme et que les références ajoutées ne doivent pas être copiées localement.<br /><br /> **TargetFramework** Cet attribut est utilisé par Visual Studio pour s’assurer que seuls les projets qui ciblent les mêmes frameworks que ceux spécifiés dans la valeur de cet attribut peuvent utiliser le kit de développement logiciel (SDK).<br /><br /> **MinVSVersion** Cet attribut est utilisé par Visual Studio pour consommer uniquement les kits de développement logiciel (SDK) qui s’y appliquent.<br /><br /> **Faire** Cet attribut doit être spécifié uniquement pour les références qui contiennent des contrôles. Pour plus d’informations sur la façon de spécifier si une référence contient des contrôles, voir ci-dessous. |

## <a name="extension-sdks"></a>SDK d’extension

Les sections suivantes décrivent ce que vous devez faire pour déployer un kit de développement logiciel (SDK) d’extension.

### <a name="installation"></a>Installation

Les kits de développement logiciel (SDK) d’extension peuvent être installés pour un utilisateur spécifique ou pour tous les utilisateurs sans spécifier de clé de registre. Pour installer un kit de développement logiciel (SDK) pour tous les utilisateurs, utilisez le chemin d’accès suivant:

*% Program Files%\Microsoft SDK\<cible plateforme\>\v < numéro\>de version de la plateforme \ExtensionSDKs*

Pour une installation spécifique à l’utilisateur, utilisez le chemin d’accès suivant:

*SDK\<%UserProfile%\AppData\Local\Microsoft plateforme\>cible \v < numéro\>de version de la plateforme \ExtensionSDKs*

Si vous souhaitez utiliser un autre emplacement, vous devez effectuer l’une des deux opérations suivantes:

1. Spécifiez-le dans une clé de Registre:

     **Kit de\<développement logiciel (SDK) HKLM\Software\Microsoft\Microsoft plateforme cible\>> \v <\<numéro de version de la plateforme \ExtensionSDKs\<SDKName > SDKVersion >** \

     et ajoutez une sous-clé (par défaut) qui a `<path to SDK><SDKName><SDKVersion>`la valeur.

2. Ajoutez la propriété `SDKReferenceDirectoryRoot` MSBuild à votre fichier projet. La valeur de cette propriété est une liste délimitée par des points-virgules des répertoires dans lesquels se trouvent les kits de développement logiciel (SDK) d’extension que vous souhaitez référencer.

### <a name="installation-layout"></a>Disposition de l’installation

Les kits de développement logiciel (SDK) d’extension présentent la disposition d’installation suivante:

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

1. \\< SDKName\>\\<SDKVersion\>: le nom et la version du kit de développement logiciel (SDK) d’extension sont dérivés des noms de dossiers correspondants dans le chemin d’accès à la racine du kit de développement logiciel (SDK). MSBuild utilise cette identité pour rechercher le kit de développement logiciel (SDK) sur le disque, et Visual Studio affiche cette identité dans la fenêtre **Propriétés** et dans la boîte de dialogue **Gestionnaire de références** .

2. Dossier de *références* : fichiers binaires qui contiennent les API. Il peut s’agir de fichiers de métadonnées Windows (WinMD) ou d’assemblys.

3. Dossier Redist: fichiers nécessaires à l’exécution/au débogage et qui doivent être empaquetés dans le cadre de l’application de l’utilisateur. Tous les fichiers binaires doivent être placés sous *\Redist\>\\< config\>\\< Arch*, et les noms binaires doivent avoir le format suivant pour garantir l’unicité: *]* \<société >. \<> du produit. \<> d’objectif. \<><em>d’extension. Par exemple, * Microsoft. cpp. Build. dll</em>. Tous les fichiers dont le nom peut être en conflit avec les noms de fichiers d’autres kits de développement logiciel (par exemple, les fichiers JavaScript, CSS, PRI, XAML, png <em>et\\jpg)\>doivent être placés sous \Redist < config\\< arch\>< sdkname,à\> l’exception des fichiers qui sont associés aux contrôles XAML.\* \\ Ces fichiers doivent être placés sous * \Redist\\< config\>\\< arch\>\\< ComponentName\>\\.</em>

4. Dossier *designtime* : les fichiers qui sont nécessaires uniquement au moment de la pré-exécution ou du débogage, et ne doivent pas être empaquetés dans le cadre de l’application de l’utilisateur. Il peut s’agir de documents XML, de bibliothèques, d’en-têtes, de fichiers binaires au moment de la conception de la boîte à outils, d’artefacts MSBuild, etc. Tout kit de développement logiciel (SDK) destiné à être consommé par un projet natif doit avoir un fichier *SDKName. props* . L’exemple suivant montre un exemple de ce type de fichier.

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

    Les documents de référence XML sont placés à côté du fichier de référence. Par exemple, le document de référence XML pour l’assembly *\References\\<\>config\>\\< Arch \Sample.dll* est *\\\References\> < config\\<arch\>\Sample.xml*et la version localisée de ce document est *\\\References <\>configuration\\< arch\>\\< paramètres régionaux\>\Sample.xml*.

5. Dossier de *configuration* : trois sous-dossiers: *Debug*, *Retail*et *CommonConfiguration*. Les auteurs du SDK peuvent placer leurs fichiers sous *CommonConfiguration* lorsque le même jeu de fichiers du kit de développement logiciel (SDK) doit être consommé, quelle que soit la configuration ciblée par le consommateur du kit de développement logiciel (SDK).

6. Dossier d' *architecture* : les architectures suivantes sont prises en charge: x86, x64, ARM, neutre. Win32 est mappé à x86 et AnyCPU est mappé à Neutral.

### <a name="sdkmanifestxml"></a>SDKManifest.xml

Le fichier *SDKManifest. xml* décrit la façon dont Visual Studio doit utiliser le kit de développement logiciel (SDK). Voici un exemple :

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

La liste suivante indique les éléments du fichier:

1. DisplayName: valeur qui apparaît dans le gestionnaire de références, Explorateur de solutions, l’Explorateur d’objets et d’autres emplacements dans l’interface utilisateur de Visual Studio.

2. ProductFamilyName: Nom complet du produit SDK. Par exemple, le [!INCLUDE[winjs_long](../debugger/includes/winjs_long_md.md)] Kit de développement logiciel (SDK) est nommé «Microsoft. WinJS. 1.0» et «Microsoft. WinJS. 2.0», qui appartiennent à la même famille de produits SDK, «Microsoft. WinJS». Cet attribut permet à Visual Studio et à MSBuild d’établir cette connexion. Si cet attribut n’existe pas, le nom du kit de développement logiciel (SDK) est utilisé comme nom de famille de produits.

3. FrameworkIdentity Spécifie une dépendance sur une ou plusieurs bibliothèques de composants Windows. La valeur de cet attribut est placée dans le manifeste de l’application consommatrice. Cet attribut s’applique uniquement aux bibliothèques de composants Windows.

4. TargetFramework Spécifie les kits de développement logiciel (SDK) disponibles dans le gestionnaire de références et la boîte à outils. Il s’agit d’une liste délimitée par des points-virgules des monikers du Framework cible, par exemple «.NET Framework, version = v 2.0; .NET Framework, version = v 4.5.1». Si plusieurs versions de la même version cible du .NET Framework sont spécifiées, le gestionnaire de références utilise la version spécifiée la plus faible à des fins de filtrage. Par exemple, si «.NET Framework, version = v 2.0; .NET Framework, version = v 4.5.1» est spécifié, le gestionnaire de références utilise «.NET Framework, version = v 2.0». Si un profil de Framework cible spécifique est spécifié, seul ce profil sera utilisé par le gestionnaire de références à des fins de filtrage. Par exemple, quand «Silverlight, version = v 4.0, Profile = WindowsPhone» est spécifié, le gestionnaire de références filtre uniquement sur le profil Windows Phone; un projet ciblant l’infrastructure Silverlight 4,0 complète ne voit pas le kit de développement logiciel (SDK) dans le gestionnaire de références.

5. MinVSVersion Version minimale de Visual Studio.

6. MaxPlatformVerson: La version maximale de la plateforme cible doit être utilisée pour spécifier les versions de plateforme sur lesquelles votre kit de développement logiciel d’extension ne fonctionnera pas. Par exemple, le package Microsoft C++ Visual Runtime v 11.0 doit être référencé uniquement par les projets Windows 8. Ainsi, le MaxPlatformVersion du projet Windows 8 est 8,0. Cela signifie que le gestionnaire de références filtre le package C++ Microsoft Visual Runtime pour un projet Windows 8.1 et que MSBuild génère une erreur lorsqu’un [!INCLUDE[win81](../debugger/includes/win81_md.md)] projet y fait référence. Remarque: cet élément est pris en charge [!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)]à partir de.

7. AppliesTo Spécifie les kits de développement logiciel (SDK) disponibles dans le gestionnaire de références en spécifiant les types de projets Visual Studio applicables. Neuf valeurs sont reconnues: WindowsAppContainer, VisualC, VB, CSharp, WindowsXAML, JavaScript, Managed et Native. L’auteur du SDK peut utiliser et ("+") ou ("&#124;"), et non ("!") les opérateurs pour spécifier exactement l’étendue des types de projets qui s’appliquent au kit de développement logiciel (SDK).

    WindowsAppContainer identifie les projets [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] pour les applications.

8. SupportPrefer32Bit: Les valeurs prises en charge sont «true» et «false». La valeur par défaut est «true». Si la valeur est définie sur «false», MSBuild retourne une erreur [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] pour les projets (ou un avertissement pour les projets de bureau) si Prefer32Bit est activé dans le projet qui fait référence au kit de développement logiciel (SDK). Pour plus d’informations sur Prefer32Bit, consultez [Générer, page du concepteurC#de projets ()](../ide/reference/build-page-project-designer-csharp.md) ou [page compiler, concepteur de projets (Visual Basic)](../ide/reference/compile-page-project-designer-visual-basic.md).

9. SupportedArchitectures: Liste délimitée par des points-virgules des architectures prises en charge par le SDK. MSBuild affiche un avertissement si l’architecture du kit de développement logiciel (SDK) ciblé dans le projet de consommation n’est pas prise en charge. Si cet attribut n’est pas spécifié, MSBuild n’affiche jamais ce type d’avertissement.

10. SupportsMultipleVersions: Si cet attribut est défini sur **erreur** ou **Avertissement**, MSBuild indique que le même projet ne peut pas faire référence à plusieurs versions de la même famille de kits de développement logiciel (SDK). Si cet attribut n’existe pas ou est défini sur **autoriser**, MSBuild n’affiche pas ce type d’erreur ou d’avertissement.

11. AppX Spécifie le chemin d’accès aux packages d’application pour la bibliothèque de composants Windows sur le disque. Cette valeur est passée au composant d’inscription de la bibliothèque de composants Windows pendant le débogage local. La Convention d’affectation de noms pour le nom de fichier est  *\<Company >.\< > Du produit. \<> D’architecture. \<> De configuration. Version\<>. AppX*. La configuration et l’architecture sont facultatives dans le nom d’attribut et la valeur d’attribut si elles ne s’appliquent pas à la bibliothèque de composants Windows. Cette valeur s’applique uniquement aux bibliothèques de composants Windows.

12. CopyRedistToSubDirectory: Spécifie l’emplacement où les fichiers figurant dans le dossier *\Redist* doivent être copiés par rapport à la racine du package d’application (autrement dit, l' **emplacement du package** choisi dans l’Assistant Création d’un **package d’application** ) et la racine de la disposition du Runtime. L’emplacement par défaut est la racine du package d’application et la mise en page **F5** .

13. DependsOn Liste des identités du kit de développement logiciel (SDK) qui définissent les kits de développement logiciel dont ce SDK dépend. Cet attribut s’affiche dans le volet d’informations du gestionnaire de références.

14. MoreInfo: URL de la page Web qui fournit de l’aide et des informations supplémentaires. Cette valeur est utilisée dans le lien plus d’informations dans le volet droit du gestionnaire de références.

15. Type d’inscription: Spécifie l’inscription WinMD dans le manifeste de l’application et est requis pour le WinMD natif, qui a une DLL d’implémentation équivalente.

16. Référence de fichier: Spécifié uniquement pour les références qui contiennent des contrôles ou qui sont des Winmd natifs. Pour plus d’informations sur la façon de spécifier si une référence contient des contrôles, consultez [spécifier l’emplacement des éléments de boîte à outils](#ToolboxItems) ci-dessous.

## <a name="ToolboxItems"></a>Spécifier l’emplacement des éléments de la boîte à outils

L’élément **ToolBoxItems** du schéma *SDKManifest. xml* spécifie la catégorie et l’emplacement des éléments de boîte à outils dans les kits de développement logiciel (SDK) de plateforme et d’extension. Les exemples suivants montrent comment spécifier des emplacements différents. Cela s’applique aux références WinMD ou DLL.

1. Placez les contrôles dans la catégorie par défaut de la boîte à outils.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Toolbox.Default"/>
    </File>
    ```

2. Placez les contrôles sous un nom de catégorie particulier.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory= "MyCategoryName"/>
    </File>
    ```

3. Placez les contrôles sous des noms de catégories particuliers.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Graph">
        <ToolboxItems/>
        <ToolboxItems VSCategory = "Data">
        <ToolboxItems />
    </File>
    ```

4. Placez les contrôles sous des noms de catégorie différents dans Blend et Visual Studio.

    ```xml
    // Blend accepts a slightly different structure for the category name because it allows a path rather than a single category.
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Graph" BlendCategory = "Controls/sample/Graph">
        <ToolboxItems />
    </File>
    ```

5. Énumérez les contrôles spécifiques différemment dans Blend et Visual Studio.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Graph">
        <ToolboxItems/>
        <ToolboxItems BlendCategory = "Controls/sample/Graph">
        <ToolboxItems/>
    </File>
    ```

6. Énumérez des contrôles spécifiques et placez-les sous le chemin d’accès commun de Visual Studio ou uniquement dans le groupe tous les contrôles.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Toolbox.Common">
        <ToolboxItems />
        <ToolboxItems VSCategory = "Toolbox.All">
        <ToolboxItems />
    </File>
    ```

7. Énumérer des contrôles spécifiques et afficher uniquement un jeu spécifique dans ChooseItems sans qu’ils ne soient dans la boîte à outils.

    ```xml
    <File Reference = "sample.winmd">
        <ToolboxItems VSCategory = "Toolbox.ChooseItemsOnly">
        <ToolboxItems />
    </File>
    ```

## <a name="see-also"></a>Voir aussi

- [Procédure pas à pas : Créer un SDK à l’aide deC++](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)
- [Procédure pas à pas : Créer un kit de C# développement logiciel à l’aide de ou Visual Basic](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)
- [Gérer les références dans un projet](../ide/managing-references-in-a-project.md)