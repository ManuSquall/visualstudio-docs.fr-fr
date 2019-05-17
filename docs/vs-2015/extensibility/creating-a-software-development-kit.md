---
title: Création d’un Kit de développement logiciel | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 8496afb4-1573-4585-ac67-c3d58b568a12
caps.latest.revision: 55
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 791400746247d71c06e133d10469132f38544b21
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65689994"
---
# <a name="creating-a-software-development-kit"></a>Création d’un Kit de développement logiciel (SDK)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un kit de développement logiciel (SDK) est une collection d’API que vous pouvez référencer en tant qu’un seul élément dans Visual Studio. Le **Gestionnaire de références** boîte de dialogue répertorie tous les kits de développement logiciel qui sont pertinents pour le projet. Lorsque vous ajoutez un kit SDK à un projet, les API sont disponibles dans Visual Studio.  
  
 Il existe deux types de kits de développement logiciel :  
  
- Les kits de développement Platform SDK sont les composants obligatoires pour le développement d’applications pour une plateforme. Par exemple, le [!INCLUDE[win81](../includes/win81-md.md)] SDK est requis pour développer [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] applications.  
  
- SDK d’extension est des composants facultatifs qui étendent une plateforme, mais ne sont pas obligatoires pour le développement d’applications pour cette plateforme.  
  
  Les sections suivantes décrivent l’infrastructure générale de kits de développement logiciel et comment créer un kit platform SDK et un SDK d’extension.  
  
- [Kits SDK de plateforme](#PlatformSDKs)  
  
- [SDK d’extension](#ExtensionSDKs)  
  
## <a name="PlatformSDKs"></a> Kits SDK de plateforme  
 Les kits de développement Platform SDK sont requis pour développer des applications pour une plateforme. Par exemple, le [!INCLUDE[win81](../includes/win81-md.md)] SDK est nécessaire pour développer des applications pour [!INCLUDE[win81](../includes/win81-md.md)].  
  
### <a name="installation"></a>Installation  
 Plateforme tous les kits de développement logiciel sera installé à des kits de développement logiciel HKLM\Software\Microsoft\Microsoft\\[TPI] \v [TPV]\\ @InstallationFolder = [racine SDK]. En conséquence, le [!INCLUDE[win81](../includes/win81-md.md)] SDK est installé dans HKLM\Software\Microsoft\Microsoft SDKs\Windows\v8.1.  
  
### <a name="layout"></a>Mise en page  
 Kits de développement logiciel Platform aura la disposition suivante :  
  
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
  
|Nœud|Description|  
|----------|-----------------|  
|Dossier références|Contient les fichiers binaires qui contiennent des API qui peuvent être codées. Il peut s’agir de fichiers de métadonnées Windows (WinMD) ou des assemblys.|  
|Dossier DesignTime|Contient les fichiers qui sont nécessaires uniquement au moment de pré-exécution et de débogage. Il peut inclure des documents XML, bibliothèques, en-têtes, les fichiers binaires de boîte à outils au moment du design, les artefacts de MSBuild, etc.<br /><br /> Documents XML sont, dans l’idéal, placés dans le dossier \DesignTime, mais les documents XML pour les références continueront à être placé en même temps que le fichier de référence dans Visual Studio. Par exemple, le document XML pour une référence de \References\\[configuration]\\[arch]\sample.dll sera \References\\[configuration]\\[arch]\sample.xml et la version localisée de ce document sera \References\\[configuration]\\[arch]\\[locale]\sample.xml.|  
|Dossier de configuration|Il peut y avoir uniquement trois dossiers : débogage, de vente au détail et CommonConfiguration. Les auteurs de kit de développement logiciel peuvent placer leurs fichiers sous CommonConfiguration si le même ensemble de fichiers SDK doit être utilisé, quelle que soit la configuration qui cible le consommateur du Kit de développement logiciel.|  
|Dossier de l’architecture|N’importe quel dossier de l’architecture prise en charge peut exister. Visual Studio prend en charge les architectures suivantes : x86, x64, ARM et neutre. Remarque : Win32 est mappé à x86 et AnyCPU mappe à neutre.<br /><br /> MSBuild recherche uniquement sous \CommonConfiguration\neutral de développement logiciel Platform SDK.|  
|SDKManifest.xml|Ce fichier décrit comment Visual Studio doit utiliser le Kit de développement. Examinez le manifeste SDK pour [!INCLUDE[win81](../includes/win81-md.md)]:<br /><br /> `<FileList             DisplayName = "Windows"             PlatformIdentity = "Windows, version=8.1"             TargetFramework = ".NET for Windows Store apps, version=v4.5.1; .NET Framework, version=v4.5.1"             MinVSVersion = "14.0">              <File Reference = "Windows.winmd">                <ToolboxItems VSCategory = "Toolbox.Default" />             </File> </FileList>`<br /><br /> **DisplayName :** La valeur que l’Explorateur d’objets affiche dans la liste de navigation.<br /><br /> **PlatformIdentity :** L’existence de cet attribut indique à Visual Studio et MSBuild que le SDK est un kit platform SDK et que les références ajoutées à partir de celui-ci ne doit pas être copiés localement.<br /><br /> **TargetFramework :** Cet attribut est utilisé par Visual Studio pour vous assurer qu’uniquement les projets qui ciblent les Frameworks mêmes tel que spécifié dans la valeur de cet attribut peut consommer le Kit de développement.<br /><br /> **MinVSVersion :** Cet attribut est utilisé par Visual Studio pour utiliser uniquement les kits de développement logiciel qui s’y appliquent.<br /><br /> **Référence :** Cet attribut doit être spécifié pour que les références qui contiennent des contrôles. Pour plus d’informations sur la façon de spécifier si une référence contient des contrôles, voir ci-dessous.|  
  
## <a name="ExtensionSDKs"></a> SDK d’extension  
 Les sections suivantes décrivent ce que vous devez faire pour déployer un kit SDK d’extension.  
  
### <a name="installation"></a>Installation  
 SDK d’extension peut être installé pour un utilisateur spécifique ou pour tous les utilisateurs sans spécifier une clé de Registre. Pour installer un kit de développement logiciel pour tous les utilisateurs, utilisez le chemin d’accès suivant :  
  
 `%Program Files%\Microsoft SDKs\<target platform>\v<platform version number>\ExtensionSDKs`  
  
 Pour une installation spécifique à l’utilisateur, utilisez le chemin d’accès suivant :  
  
 `%USERPROFILE%\AppData\Local\Microsoft SDKs\<target platform>\v<platform version number>\ExtensionSDKs`  
  
 Si vous souhaitez utiliser un autre emplacement, vous devez effectuer une des deux opérations :  
  
1. Spécifier dans une clé de Registre :  
  
     `HKLM\Software\Microsoft\Microsoft SDKs\<target platform>\v<platform version number>\ExtensionSDKs\<SDKName>\<SDKVersion>\`  
  
     et ajoutez une sous-clé (par défaut) qui a la valeur `<path to SDK><SDKName><SDKVersion>`.  
  
2. Ajoutez la propriété MSBuild `SDKReferenceDirectoryRoot` à votre fichier projet. La valeur de cette propriété est une liste de deux-points délimités semi de répertoires dans lesquels résident le SDK d’Extension que vous souhaitez référencer.  
  
### <a name="installation-layout"></a>Disposition d’installation  
 SDK d’extension ont la disposition d’installation suivantes :  
  
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
  
1. \\< SDKName\>\\< SDKVersion\>: le nom et la version de l’extension SDK est dérivé des noms de dossiers correspondants dans le chemin d’accès à la racine du Kit de développement logiciel. MSBuild utilise cette identité pour trouver le Kit de développement sur le disque, et Visual Studio affiche cette identité dans le **propriétés** fenêtre et **Gestionnaire de références** boîte de dialogue.  
  
2. Dossier Références : les fichiers binaires qui contiennent les API. Il peut s’agir de fichiers de métadonnées Windows (WinMD) ou des assemblys.  
  
3. Dossier Redist : les fichiers qui sont nécessaires pour l’exécution et de débogage et doivent obtenir un package d’application de l’utilisateur. Tous les fichiers binaires doivent être placés sous \redist\\< config\>\\< arch\>, et les noms binaire doivent avoir le format suivant pour garantir l’unicité :  **\<société >.\< produit >. \<usage >. \<extension >**. Par exemple, Microsoft.Cpp.Build.dll. Tous les fichiers portant des noms qui peuvent entrer en conflit avec les noms de fichiers à partir d’autres kits de développement logiciel (par exemple, les fichiers javascript, css, pri, xaml, png et jpg) doivent être placés sous \redist\\< config\>\\< arch\> \\< sdkname\>\ sauf les fichiers qui sont associés à XAML contrôle. Ces fichiers doivent être placés sous \redist\\< config\>\\< arch\>\\< componentname\>\\.  
  
4. Le dossier DesignTime : les fichiers qui sont nécessaires au seul pré-exécution et de débogage de temps et ne doit pas être un package d’application de l’utilisateur. Il peut s’agir de documents XML, bibliothèques, en-têtes, les fichiers binaires de boîte à outils au moment du design, les artefacts de MSBuild et ainsi de suite. N’importe quel SDK est conçue pour la consommation par un projet natif doit avoir un *SDKName*fichier .props. L’exemple suivant montre un exemple de ce type de fichier.  
  
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
  
     Documents de référence XML sont placés en même temps que le fichier de référence. Par exemple, le document de référence XML pour le **\References\\< config\>\\< arch\>\sample.dll** assembly est **\References\\ < config\>\\< arch\>\sample.xml**, et la version localisée de ce document est **\References\\< config\>\\< arch\>\\< paramètres régionaux\>\sample.xml**.  
  
5. Dossier de configuration : trois sous-dossiers : Débogage, de vente au détail et CommonConfiguration. Les auteurs de kit de développement logiciel peuvent placer leurs fichiers sous CommonConfiguration lorsque le même ensemble de fichiers SDK doit être utilisé, quelle que soit la configuration ciblée par le consommateur du Kit de développement logiciel.  
  
6. Dossier de l’architecture : les architectures suivantes sont prises en charge : x86, x64, ARM, neutre. Win32 est mappé à x86 et AnyCPU mappe à neutre.  
  
### <a name="sdkmanifestxml"></a>SDKManifest.xml  
 Ce fichier décrit comment Visual Studio doit utiliser le Kit de développement. Voici un exemple.  
  
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
  
 La liste suivante donne les éléments du fichier.  
  
1. DisplayName : la valeur qui apparaît dans le Gestionnaire de références, l’Explorateur de solutions, Explorateur d’objets et autres emplacements dans l’interface utilisateur pour Visual Studio.  
  
2. ProductFamilyName: Le nom de produit SDK global. Par exemple, le [!INCLUDE[winjs_long](../includes/winjs-long-md.md)] SDK est nommé « Microsoft.WinJS.1.0 » et « Microsoft.WinJS.2.0 », qui appartiennent à la même famille de la famille de produits de kit de développement logiciel, « Microsoft.WinJS ». Cet attribut permet à Visual Studio et MSBuild établir cette connexion. Si cet attribut n’existe pas, le nom du SDK est utilisé comme nom de famille de produit.  
  
3. FrameworkIdentity : Spécifie une dépendance sur un ou plusieurs bibliothèques de composants de Windows que la valeur de cet attribut est placée dans le manifeste de l’application consommatrice. Cet attribut s’applique uniquement aux bibliothèques de composants Windows.  
  
4. TargetFramework : Spécifie les kits SDK qui sont disponibles dans le Gestionnaire de références et de la boîte à outils. Il s’agit d’une liste délimitée par des points-virgules des monikers du framework cible, par exemple « .NET Framework, version = v2.0 ; .NET Framework, version = v4.5.1 ». Si plusieurs versions du même framework cible sont spécifiées, le Gestionnaire de références utilise la version la plus basse spécifiée pour le filtrage à des fins. Par exemple, si « .NET Framework, version = v2.0 ; .NET Framework, version = v4.5.1 » est spécifié, Gestionnaire de références utilisera « .NET Framework, version = v2.0 ». Si un profil de framework cible spécifique est spécifié, uniquement ce profil sera utilisé par le Gestionnaire de références pour le filtrage à des fins. Par exemple, lorsque « Silverlight, version = v4.0, profil = WindowsPhone » est spécifié, les filtres de gestionnaire de références sur uniquement le profil Windows Phone ; un projet qui cible le Framework Silverlight 4.0 ne voit pas le Kit de développement dans le Gestionnaire de références.  
  
5. MinVSVersion : version minimale de Visual Studio.  
  
6. MaxPlatformVerson : La version de la plateforme cible maximale doit être utilisée pour spécifier les versions de la plateforme sur laquelle votre SDK d’Extension ne fonctionnera pas. Par exemple, de Microsoft Visual C++ Runtime Package v11.0 doivent être référencés que par les projets Windows 8. Par conséquent, MaxPlatformVersion du projet Windows 8 est 8.0. Cela signifie que le Gestionnaire de références exclut Microsoft Visual C++ Runtime Package pour un projet Windows 8.1 et MSBuild génère une erreur lorsqu’un [!INCLUDE[win81](../includes/win81-md.md)] projet y fait référence. Remarque : cet élément est pris en charge dans [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)].  
  
7. AppliesTo : Spécifie les kits SDK qui sont disponibles dans le Gestionnaire de références en spécifiant les types de projet Visual Studio applicables. Neuf valeurs sont reconnus : WindowsAppContainer, VisualC, VB, CSharp, WindowsXAML, JavaScript, gérés et Native. L’auteur du Kit de développement logiciel permettre utiliser et (« + »), ou («&#124;»), et non (« ! ») opérateurs pour spécifier exactement l’étendue des types de projets qui s’appliquent au kit SDK.  
  
     WindowsAppContainer identifie les projets pour [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] applications.  
  
8. SupportPrefer32Bit : Valeurs prises en charge sont « True » et « False ». La valeur par défaut est « True ». Si la valeur est définie sur « False », MSBuild retourne une erreur pour [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] projets (ou un avertissement pour les projets de bureau) si le projet qui référence le SDK Prefer32Bit activé. Pour plus d’informations sur Prefer32Bit, consultez [générer, Page du Concepteur de projets (c#)](../ide/reference/build-page-project-designer-csharp.md) ou [Page Compiler, Concepteur de projets (Visual Basic)](../ide/reference/compile-page-project-designer-visual-basic.md).  
  
9. SupportedArchitectures : un point-virgule liste délimitée par des architectures prenant en charge le Kit de développement. MSBuild affiche un avertissement si l’architecture SDK ciblé dans le projet de consommation n’est pas pris en charge. Si cet attribut n’est pas spécifié, MSBuild affiche jamais ce type d’alerte.  
  
10. SupportsMultipleVersions : si cet attribut est défini **erreur** ou **avertissement**, MSBuild indique que le même projet ne peut pas référencer plusieurs versions de la même famille de kit de développement logiciel. Si cet attribut n’existe pas ou est défini sur **autoriser**, MSBuild n’affiche pas ce type d’erreur ou un avertissement.  
  
11. AppX : Spécifie le chemin d’accès aux packages d’application pour la bibliothèque de composant de Windows sur le disque. Cette valeur est passée au composant d’inscription de la bibliothèque de composant Windows pendant le débogage local. La convention d’affectation de noms pour le nom de fichier est  **\<société >.\< Produit >. \<Architecture >. \<Configuration >. \<Version > .appx**. Configuration et Architecture sont facultatives dans le nom d’attribut et la valeur d’attribut si elles ne s’appliquent pas à la bibliothèque de composant de Windows. Cette valeur s’applique uniquement aux bibliothèques de composants Windows.  
  
12. CopyRedistToSubDirectory : Spécifie où les fichiers sous le dossier \redist doivent être copiés par rapport à la racine de package d’application (autrement dit, le **emplacement du Package** choisi dans l’Assistant Création d’un Package App) et la racine de disposition de runtime. L’emplacement par défaut est la racine du package d’application et la disposition de F5.  
  
13. DependsOn : Une liste d’identités de kit de développement logiciel qui définissent les kits de développement logiciel dont dépend ce SDK. Cet attribut apparaît dans le volet de détails du Gestionnaire de référence.  
  
14. MoreInfo : l’URL vers la page web qui fournit une aide et des informations supplémentaires. Cette valeur est utilisée dans le lien informations supplémentaires dans le volet droit du Gestionnaire de référence.  
  
15. Type d’enregistrement : Spécifie l’inscription WinMD dans le manifeste d’application et est requis pour les WinMD natif, ce qui a une implémentation équivalent DLL.  
  
16. Référence de fichier : spécifiée pour que les références qui contiennent des contrôles ou sont les Winmd natifs. Pour plus d’informations sur la façon de spécifier si une référence contient des contrôles, consultez [spécifiant l’emplacement des éléments de boîte à outils](#ToolboxItems) ci-dessous.  
  
## <a name="ToolboxItems"></a> En spécifiant l’emplacement des éléments de boîte à outils  
 L’élément ToolBoxItems du schéma SDKManifest.xml spécifie la catégorie et l’emplacement des éléments de boîte à outils dans la plateforme et le SDK d’extension. Les exemples suivants montrent comment spécifier des emplacements différents. Cela s’applique aux références WinMD ou DLL.  
  
1. Placer des contrôles dans la catégorie par défaut de boîte à outils.  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Toolbox.Default"/>       
    </File>  
    ```  
  
2. Placez les contrôles sous un nom de catégorie particulier.  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory= "MyCategoryName"/>  
    </File>  
    ```  
  
3. Placez les contrôles sous les noms de catégorie particulière.  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Graph">  
        <ToolboxItems/>  
        <ToolboxItems VSCategory = "Data">  
        <ToolboxItems />  
    </File>  
    ```  
  
4. Placer des contrôles sous les noms de catégorie différente dans Blend et Visual Studio.  
  
    ```  
    // Blend accepts a slightly different structure for the category name because it allows a path rather than a single category.  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Graph" BlendCategory = "Controls/sample/Graph">   
        <ToolboxItems />  
    </File>  
    ```  
  
5. Énumérer des contrôles spécifiques différemment dans Blend et Visual Studio.  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Graph">  
        <ToolboxItems/>  
        <ToolboxItems BlendCategory = "Controls/sample/Graph">  
        <ToolboxItems/>  
    </File>  
    ```  
  
6. Énumérer des contrôles spécifiques et les placer sous le chemin d’accès de courants de Visual Studio, ou uniquement dans le groupe tous les contrôles.  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Toolbox.Common">  
        <ToolboxItems />  
        <ToolboxItems VSCategory = "Toolbox.All">  
        <ToolboxItems />  
    </File>  
    ```  
  
7. Énumérer des contrôles spécifiques et afficher uniquement un ensemble spécifique de ChooseItems sans les en cours dans la boîte à outils.  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Toolbox.ChooseItemsOnly">  
        <ToolboxItems />  
    </File>  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure pas à pas : Création d’un kit de développement à l’aide de C++](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)   
 [Procédure pas à pas : Création d’un à l’aide du Kit de développement logiciel C# ou Visual Basic](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)   
 [Gestion des références dans un projet](../ide/managing-references-in-a-project.md)
