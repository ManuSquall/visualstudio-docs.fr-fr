---
title: "Création d’un Kit de développement logiciel | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8496afb4-1573-4585-ac67-c3d58b568a12
caps.latest.revision: "54"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6a301085cd00e20d5c4e931ac144e454718ad152
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="creating-a-software-development-kit"></a>Création d’un Kit de développement logiciel (SDK)
Un kit de développement logiciel (SDK) est un ensemble d’API que vous pouvez référencer comme un seul élément dans Visual Studio. Le **Gestionnaire de références** boîte de dialogue répertorie tous les kits de développement logiciel qui sont pertinents pour le projet. Lorsque vous ajoutez un kit de développement à un projet, les API sont disponibles dans Visual Studio.  
  
 Il existe deux types de kits de développement logiciel :  
  
-   Les kits de développement Platform SDK sont des composants obligatoires pour le développement d’applications pour une plateforme. Par exemple, le [!INCLUDE[win81](../debugger/includes/win81_md.md)] Kit de développement logiciel est requis pour développer [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] applications.  
  
-   SDK d’extension est des composants facultatifs qui étendent une plateforme, mais ne sont pas obligatoires pour le développement d’applications pour cette plateforme.  
  
 Les sections suivantes décrivent l’infrastructure générale de kits de développement logiciel et comment créer un kit de développement logiciel de plateforme et un SDK d’extension.  
  
-   [Kits de développement Platform SDK](#PlatformSDKs)  
  
-   [SDK d’extension](#ExtensionSDKs)  
  
##  <a name="PlatformSDKs"></a>Kits de développement Platform SDK  
 Les kits de développement Platform SDK sont requis pour développer des applications pour une plateforme. Par exemple, le [!INCLUDE[win81](../debugger/includes/win81_md.md)] Kit de développement logiciel est requis pour développer des applications [!INCLUDE[win81](../debugger/includes/win81_md.md)].  
  
### <a name="installation"></a>Installation  
 Plateforme tous les kits de développement logiciel sera installé à des kits de développement logiciel HKLM\Software\Microsoft\Microsoft\\[TPI] \v [TPV]\\ @InstallationFolder = [racine du Kit de développement logiciel]. En conséquence, le [!INCLUDE[win81](../debugger/includes/win81_md.md)] SDK est installé dans HKLM\Software\Microsoft\Microsoft SDKs\Windows\v8.1.  
  
### <a name="layout"></a>Disposition  
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
|Dossier références|Contient les fichiers binaires qui contiennent des API qui peut être codées sur. Il peut s’agir de fichiers de métadonnées Windows (WinMD) ou des assemblys.|  
|Dossier DesignTime|Contient des fichiers qui sont nécessaires uniquement au moment de pre-exécution/débogage. Il peut inclure les documents XML, bibliothèques, en-têtes, fichiers binaires de boîte à outils au moment du design, les artefacts de MSBuild et ainsi de suite<br /><br /> Les documents XML, dans l’idéal, se trouveraient dans le dossier \DesignTime, mais les documents XML pour les références continuent à être placé en même temps que le fichier de référence dans Visual Studio. Par exemple, le document XML pour une référence de \References\\[configuration]\\[arch]\sample.dll sera \References\\[configuration]\\[arch]\sample.xml et la version localisée de ce document sera \References\\[configuration]\\[arch]\\[locale]\sample.xml.|  
|Dossier de configuration|Il peut y avoir uniquement trois dossiers : debug, vente au détail et CommonConfiguration. Les auteurs de kit de développement logiciel peuvent placer leurs fichiers sous CommonConfiguration si le même ensemble de fichiers du Kit de développement logiciel doit être consommé, quelle que soit la configuration qui cible le consommateur du Kit de développement logiciel.|  
|Dossier de l’architecture|N’importe quel dossier de l’architecture prise en charge peut exister. Visual Studio prend en charge les architectures suivantes : x86, x64, ARM et neutre. Remarque : Win32 est mappé à x86 et AnyCPU mappe à neutre.<br /><br /> MSBuild recherche uniquement sous \CommonConfiguration\neutral de développement logiciel Platform SDK.|  
|SDKManifest.xml|Ce fichier décrit comment Visual Studio doit utiliser le Kit de développement. Examinez le manifeste SDK pour [!INCLUDE[win81](../debugger/includes/win81_md.md)]:<br /><br /> `<FileList             DisplayName = "Windows"             PlatformIdentity = "Windows, version=8.1"             TargetFramework = ".NET for Windows Store apps, version=v4.5.1; .NET Framework, version=v4.5.1"             MinVSVersion = "14.0">              <File Reference = "Windows.winmd">                <ToolboxItems VSCategory = "Toolbox.Default" />             </File> </FileList>`<br /><br /> **Nom d’affichage :** la valeur de l’Explorateur d’objets affiche dans la liste de navigation.<br /><br /> **PlatformIdentity :** l’existence de cet attribut indique à Visual Studio et MSBuild que le Kit de développement est une plateforme du Kit de développement logiciel et que les références ajoutées à partir de celui-ci ne doit pas être copiés localement.<br /><br /> **TargetFramework :** cet attribut est utilisé par Visual Studio pour vous assurer que seuls les projets qui ciblent les mêmes infrastructures comme spécifié dans la valeur de cet attribut peut utiliser le Kit de développement.<br /><br /> **MinVSVersion :** cet attribut est utilisé par Visual Studio pour utiliser uniquement les kits de développement qui s’y appliquent.<br /><br /> **Référence :** cet attribut doit être spécifié pour que les références qui contiennent des contrôles. Pour plus d’informations sur la façon de spécifier si une référence contient des contrôles, voir ci-dessous.|  
  
##  <a name="ExtensionSDKs"></a>SDK d’extension  
 Les sections suivantes décrivent ce que vous devez faire pour déployer un SDK d’extension.  
  
### <a name="installation"></a>Installation  
 SDK d’extension peut être installé pour un utilisateur spécifique ou pour tous les utilisateurs sans spécifier une clé de Registre. Pour installer un kit de développement logiciel pour tous les utilisateurs, utilisez le chemin d’accès suivant :  
  
 `%Program Files%\Microsoft SDKs\<target platform>\v<platform version number>\ExtensionSDKs`  
  
 Pour une installation spécifique à l’utilisateur, utilisez le chemin d’accès suivant :  
  
 `%USERPROFILE%\AppData\Local\Microsoft SDKs\<target platform>\v<platform version number>\ExtensionSDKs`  
  
 Si vous souhaitez utiliser un autre emplacement, vous devez effectuer une des deux choses :  
  
1.  Spécifier dans une clé de Registre :  
  
     `HKLM\Software\Microsoft\Microsoft SDKs\<target platform>\v<platform version number>\ExtensionSDKs\<SDKName>\<SDKVersion>\`  
  
     Ajoutez une sous-clé (par défaut) qui a la valeur `<path to SDK><SDKName><SDKVersion>`.  
  
2.  Ajoutez la propriété MSBuild `SDKReferenceDirectoryRoot` à votre fichier projet. La valeur de cette propriété est une liste de deux-points délimités de semi de répertoires dans lesquels résident le SDK d’Extension que vous souhaitez référencer.  
  
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
  
1.  \\< nom du SDK\>\\< SDKVersion\>: le nom et la version de l’extension du Kit de développement logiciel est dérivé les noms de dossiers correspondants dans le chemin d’accès à la racine du Kit de développement logiciel. MSBuild utilise cette identité pour trouver le Kit de développement sur le disque, et Visual Studio affiche cette identité dans le **propriétés** fenêtre et **Gestionnaire de références** boîte de dialogue.  
  
2.  Le dossier Références : les fichiers binaires qui contiennent les API. Il peut s’agir de fichiers de métadonnées Windows (WinMD) ou des assemblys.  
  
3.  Dossier Redist : les fichiers qui sont nécessaires pour l’exécution et de déboguer et doivent obtenir un package d’application de l’utilisateur. Tous les fichiers binaires doivent être placés sous \redist\\< config\>\\< arch\>, et les noms binaire doivent avoir le format suivant pour garantir l’unicité :  **\<société >.\< produit >. \<objectif >. \<extension >**. Par exemple, Microsoft.Cpp.Build.dll. Tous les fichiers dont le nom peut entrer en conflit avec les noms de fichiers à partir d’autres kits de développement logiciel (par exemple, les fichiers javascript, css, pri, xaml, png et jpg) doivent être placés sous \redist\\< config\>\\< arch\> \\< nom du SDK\>\ sauf les fichiers qui sont associées à XAML contrôle. Ces fichiers doivent être placés sous \redist\\< config\>\\< arch\>\\< componentname\>\\.  
  
4.  Le dossier DesignTime : les fichiers qui sont nécessaires à la seule pre-exécution/débogage temps et ne doit pas être insérés dans le cadre de l’application. Il peut s’agir des documents XML, bibliothèques, en-têtes, fichiers binaires de boîte à outils au moment du design, les artefacts de MSBuild et ainsi de suite. N’importe quel SDK est conçu pour la consommation par un projet natif doit avoir un *nom du SDK*fichier .props. Le code suivant illustre un exemple de ce type de fichier.  
  
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
  
5.  Dossier de configuration : trois sous-dossiers : débogage, commerciale et CommonConfiguration. Les auteurs de kit de développement logiciel peuvent placer leurs fichiers sous CommonConfiguration lorsque le même ensemble de fichiers du Kit de développement logiciel doit être consommé, quelle que soit la configuration ciblée par le consommateur du Kit de développement logiciel.  
  
6.  Dossier de l’architecture : les architectures suivantes sont prises en charge : x86, x64, ARM, neutre. Win32 est mappé à x86 et AnyCPU mappe à neutre.  
  
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
MoreInfo = "http://msdn.microsoft.com/MySDK">  
<File Reference = "MySDK.Sprint.winmd" Implementation = "XNASprintImpl.dll">  
<Registration Type = "Flipper" Implementation = "XNASprintFlipperImpl.dll" />  
<Registration Type = "Flexer" Implementation = "XNASprintFlexerImpl.dll" />  
<ToolboxItems VSCategory = "Toolbox.Default" />  
</File>  
</FileList>  
```  
  
 La liste suivante fournit les éléments du fichier.  
  
1.  Nom d’affichage : la valeur qui apparaît dans le Gestionnaire de références, l’Explorateur de solutions, Explorateur d’objets, ou d’autres emplacements dans l’interface utilisateur pour Visual Studio.  
  
2.  ProductFamilyName : Globale SDK nom de produit. Par exemple, le [!INCLUDE[winjs_long](../debugger/includes/winjs_long_md.md)] SDK est nommé « Microsoft.WinJS.1.0 » et « Microsoft.WinJS.2.0 », qui appartiennent à la même famille de la famille de produits SDK, « Microsoft.WinJS ». Cet attribut permet à Visual Studio et MSBuild établir cette connexion. Si cet attribut n’existe pas, le nom de kit de développement logiciel est utilisé comme nom de famille de produit.  
  
3.  FrameworkIdentity : Spécifie une dépendance sur une ou plusieurs bibliothèques de composants Windows que la valeur de cet attribut est placée dans le manifeste de l’application consommatrice. Cet attribut s’applique uniquement aux bibliothèques de composants Windows.  
  
4.  TargetFramework : Spécifie les kits de développement logiciel qui sont disponibles dans le Gestionnaire de références et de la boîte à outils. Il s’agit d’une liste délimitée par des points-virgules des monikers du framework cible, par exemple « .NET Framework, version = version 2.0 ; .NET Framework, version = v4.5.1 ». Si plusieurs versions de la même infrastructure cible sont spécifiées, le Gestionnaire de références utilise la version la plus ancienne spécifiée pour le filtrage à des fins. Par exemple, si « .NET Framework, version = version 2.0 ; .NET Framework, version = v4.5.1 » est spécifié, Gestionnaire de références utilise « .NET Framework, version = v2.0 ». Si un profil du framework cible spécifique est spécifié, seulement ce profil sera utilisé par le Gestionnaire de références pour le filtrage à des fins. Par exemple, lorsque « Silverlight, version = version 4.0, profil = WindowsPhone » est spécifié, des filtres de gestionnaire de références sur le profil de Windows Phone uniquement ; un projet ciblant le Framework Silverlight 4.0 ne voit pas le Kit de développement dans le Gestionnaire de références.  
  
5.  MinVSVersion : Visual Studio version minimale.  
  
6.  MaxPlatformVerson : La version de la plateforme cible maximale doit être utilisée pour spécifier les versions de la plateforme sur laquelle votre SDK d’Extension ne fonctionnera pas. Par exemple, de Microsoft Visual C++ Runtime Package v11.0 doit être référencée que par les projets Windows 8. Par conséquent, les MaxPlatformVersion du projet Windows 8 est 8.0. Cela signifie que le Gestionnaire de références exclut de Microsoft Visual C++ Runtime Package pour un projet Windows 8.1 et MSBuild génère une erreur lorsqu’un [!INCLUDE[win81](../debugger/includes/win81_md.md)] projet fait référence. Remarque : cet élément est pris en charge depuis [!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)].  
  
7.  AppliesTo : Spécifie les kits de développement logiciel qui sont disponibles dans le Gestionnaire de références en spécifiant les types de projet Visual Studio applicables. Neuf valeurs sont reconnus : WindowsAppContainer VisualC, VB, CSharp, WindowsXAML, JavaScript, managé et natif. L’auteur du Kit de développement logiciel permettre utiliser et (« + »), ou (« &#124; »), pas (« ! ») opérateurs pour spécifier exactement l’étendue des types de projets qui s’appliquent au SDK.  
  
     WindowsAppContainer identifie les projets pour [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] applications.  
  
8.  SupportPrefer32Bit : Les valeurs prises en charge sont « True » et « False ». La valeur par défaut est « True ». Si la valeur est définie sur « False », MSBuild retourne une erreur pour [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] projets (ou un avertissement pour les projets de bureau) si le projet qui référence le Kit de développement a Prefer32Bit activé. Pour plus d’informations sur Prefer32Bit, consultez [Build Page, Project Designer (c#)](../ide/reference/build-page-project-designer-csharp.md) ou [Page Compiler, Concepteur de projets (Visual Basic)](../ide/reference/compile-page-project-designer-visual-basic.md).  
  
9. SupportedArchitectures : un point-virgule des architectures qui prend en charge par le Kit de développement. MSBuild affiche un avertissement si l’architecture du Kit de développement logiciel ciblé dans le projet de consommation n’est pas pris en charge. Si cet attribut n’est pas spécifié, MSBuild affiche jamais ce type d’alerte.  
  
10. SupportsMultipleVersions : si cet attribut est défini **erreur** ou **avertissement**, MSBuild indique que le même projet ne peut pas faire référence à plusieurs versions de la même famille de kit de développement logiciel. Si cet attribut n’existe pas ou a la valeur **autoriser**, MSBuild n’affiche pas ce type d’erreur ou un avertissement.  
  
11. AppX : Spécifie le chemin d’accès pour les packages d’application de la bibliothèque des composants Windows sur le disque. Cette valeur est passée au composant de l’inscription de la bibliothèque des composants Windows pendant le débogage local. La convention d’affectation de noms pour le nom de fichier est  **\<société >.\< Produit >. \<Architecture >. \<Configuration >. \<Version > .aspx**. Architecture et configuration sont facultatives dans le nom d’attribut et la valeur d’attribut si elles ne s’appliquent à la bibliothèque des composants Windows. Cette valeur s’applique uniquement aux bibliothèques de composants Windows.  
  
12. CopyRedistToSubDirectory : Spécifie la copie des fichiers dans le dossier \redist relatif à la racine de package d’application (autrement dit, le **emplacement du Package** choisi dans l’Assistant Création d’un Package App) et racine de disposition de runtime. L’emplacement par défaut est la racine du package d’application et de la mise en page F5.  
  
13. DependsOn : Une liste des identités de kit de développement logiciel qui définissent les kits de développement logiciel dont dépend ce SDK. Cet attribut apparaît dans le volet de détails du Gestionnaire de référence.  
  
14. MoreInfo : l’URL à la page web qui fournit plus d’informations et une aide. Cette valeur est utilisée dans le lien informations supplémentaires dans le volet droit du Gestionnaire de référence.  
  
15. Type d’enregistrement : Spécifie l’inscription WinMD dans le manifeste d’application et est requis pour le WinMD natif, ce qui a une implémentation de l’homologue DLL.  
  
16. Référence de fichier : spécifiée pour que les références qui contiennent des contrôles ou sont des fichiers Winmd natif. Pour plus d’informations sur la façon de spécifier si une référence contient des contrôles, consultez [en spécifiant l’emplacement des éléments de boîte à outils](#ToolboxItems) ci-dessous.  
  
##  <a name="ToolboxItems"></a>En spécifiant l’emplacement des éléments de boîte à outils  
 L’élément ToolBoxItems du schéma SDKManifest.xml spécifie la catégorie et l’emplacement des éléments de boîte à outils de plateforme et de kits SDK d’extension. Les exemples suivants montrent comment spécifier des emplacements différents. Cela s’applique aux références WinMD ou DLL.  
  
1.  Placez des contrôles dans la catégorie par défaut de boîte à outils.  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Toolbox.Default"/>       
    </File>  
    ```  
  
2.  Placez les contrôles sous un nom de catégorie particulier.  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory= "MyCategoryName"/>  
    </File>  
    ```  
  
3.  Placez les contrôles sous des noms de catégorie particulier.  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Graph">  
        <ToolboxItems/>  
        <ToolboxItems VSCategory = "Data">  
        <ToolboxItems />  
    </File>  
    ```  
  
4.  Placez les contrôles sous les noms de catégories différentes dans Blend et Visual Studio.  
  
    ```  
    // Blend accepts a slightly different structure for the category name because it allows a path rather than a single category.  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Graph" BlendCategory = "Controls/sample/Graph">   
        <ToolboxItems />  
    </File>  
    ```  
  
5.  Énumérer des contrôles spécifiques différemment dans Blend et Visual Studio.  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Graph">  
        <ToolboxItems/>  
        <ToolboxItems BlendCategory = "Controls/sample/Graph">  
        <ToolboxItems/>  
    </File>  
    ```  
  
6.  Énumérer des contrôles spécifiques et les placer sous le chemin d’accès de courants de Visual Studio, ou uniquement dans le groupe tous les contrôles.  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Toolbox.Common">  
        <ToolboxItems />  
        <ToolboxItems VSCategory = "Toolbox.All">  
        <ToolboxItems />  
    </File>  
    ```  
  
7.  Énumérer des contrôles spécifiques et afficher uniquement un ensemble spécifique de ChooseItems sans les en cours dans la boîte à outils.  
  
    ```  
    <File Reference = "sample.winmd">  
        <ToolboxItems VSCategory = "Toolbox.ChooseItemsOnly">  
        <ToolboxItems />  
    </File>  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure pas à pas : Création d’un kit de développement à l’aide de C++](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)   
 [Procédure pas à pas : Création d’un kit de développement à l’aide de c# ou Visual Basic](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)   
 [Gestion des références dans un projet](../ide/managing-references-in-a-project.md)