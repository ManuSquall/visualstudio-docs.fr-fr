---
title: MarkupCompilePass1, tâche | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- converting XAML to binary format [WPF MSBuild]
- MarkupCompilePass1 task [WPF MSBuild], parameters
- converting XAML projects to compiled binary format [WPF MSBuild]
- MarkupCompilePass1 task [WPF MSBuild], converting XAML to binary format
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0abf8f5b2c77281325853f744f54513fb897ecc6
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2018
---
# <a name="markupcompilepass1-task"></a>MarkupCompilePass1, tâche

La tâche <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> convertit des fichiers projet [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] non localisables au format binaire compilé.

## <a name="task-parameters"></a>Paramètres de tâche

|Paramètre|Description|
|---------------|-----------------|
|`AllGeneratedFiles`|Paramètre de sortie **ITaskItem[]** facultatif.<br /><br /> Contient une liste complète des fichiers qui sont générés par la tâche <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1>.|
|`AlwaysCompileMarkupFilesInSeparateDomain`|Paramètre **booléen** facultatif.<br /><br /> Indique si la tâche doit être exécutée dans un <xref:System.AppDomain> séparé. Si ce paramètre retourne **false**, la tâche s’exécute dans le même <xref:System.AppDomain> que [!INCLUDE[TLA#tla_msbuild](../msbuild/includes/tlasharptla_msbuild_md.md)], et plus rapidement. Si le paramètre retourne **true**, la tâche s’exécute dans un deuxième <xref:System.AppDomain> isolé de [!INCLUDE[TLA2#tla_msbuild](../msbuild/includes/tla2sharptla_msbuild_md.md)], et plus lentement.|
|`ApplicationMarkup`|Paramètre **ITaskItem[]** facultatif.<br /><br /> Spécifie le nom du fichier [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] de définition d’application.|
|`AssembliesGeneratedDuringBuild`|Paramètre **String[]** facultatif.<br /><br /> Spécifie des références à des assemblys qui changent pendant le processus de génération. Par exemple, une solution Visual Studio peut contenir un projet qui référence la sortie compilée d’un autre projet. Dans ce cas, la sortie compilée du deuxième projet peut être ajoutée au paramètre **AssembliesGeneratedDuringBuild**.<br /><br /> Remarque : Le paramètre **AssembliesGeneratedDuringBuild** doit contenir des références au jeu complet des assemblys générés par une solution de génération.|
|`AssemblyName`|Paramètre **String** obligatoire.<br /><br /> Spécifie le nom court de l’assembly généré pour un projet. Par exemple, si un projet génère un exécutable [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)] dont le nom est **WinExeAssembly.exe**, le paramètre **AssemblyName** a la valeur **WinExeAssembly**.|
|`AssemblyPublicKeyToken`|Paramètre **String** facultatif.<br /><br /> Spécifie le jeton de clé publique de l’assembly.|
|`AssemblyVersion`|Paramètre **String** facultatif.<br /><br /> Spécifie le numéro de version de l’assembly.|
|`ContentFiles`|Paramètre **ITaskItem[]** facultatif.<br /><br /> Spécifie la liste des fichiers de contenu libre.|
|`DefineConstants`|Paramètre **String** facultatif.<br /><br /> Indique que la valeur actuelle de **DefineConstants** est conservée, ce qui affecte la génération de l’assembly cible. Si ce paramètre est modifié, l’API publique dans l’assembly cible peut être modifiée et la compilation des fichiers [!INCLUDE[TLA2#tla_titlexaml](../msbuild/includes/tla2sharptla_titlexaml_md.md)] qui référencent des types locaux peut être affectée.|
|`ExtraBuildControlFiles`|Paramètre **ITaskItem[]** facultatif.<br /><br /> Spécifie une liste de fichiers qui contrôlent si une régénération est déclenchée quand la tâche <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> est réexécutée ; une régénération est déclenchée si l’un de ces fichiers change.|
|`GeneratedBamlFiles`|Paramètre de sortie **ITaskItem[]** facultatif.<br /><br /> Contient la liste des fichiers générés au format binaire [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)].|
|`GeneratedCodeFiles`|Paramètre de sortie **ITaskItem[]** facultatif.<br /><br /> Contient la liste des fichiers de code managé générés.|
|`GeneratedLocalizationFiles`|Paramètre de sortie **ITaskItem[]** facultatif.<br /><br /> Contient la liste des fichiers de localisation générés pour chaque fichier [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] localisable.|
|`HostInBrowser`|Paramètre **String** facultatif.<br /><br /> Spécifie si l’assembly généré est un [!INCLUDE[TLA#tla_xbap](../msbuild/includes/tlasharptla_xbap_md.md)]. Les options valides sont **true** et **false**. Si **true**, du code est généré pour prendre en charge l’hébergement de navigateur.|
|`KnownReferencePaths`|Paramètre **String[]** facultatif.<br /><br /> Spécifie des références à des assemblys qui ne changent pas pendant le processus de génération. Inclut les assemblys qui se trouvent dans le [!INCLUDE[TLA#tla_gac](../msbuild/includes/tlasharptla_gac_md.md)], dans un répertoire d’installation [!INCLUDE[TLA#tla_netframewk](../misc/includes/tlasharptla_netframewk_md.md)], et ainsi de suite.|
|`Language`|Paramètre **String** obligatoire.<br /><br /> Spécifie le langage managé pris en charge par le compilateur. Les options valides sont **C#**, **VB**, **JScript** et **C++**.|
|`LanguageSourceExtension`|Paramètre **String** facultatif.<br /><br /> Spécifie l’extension ajoutée à l’extension du fichier de code managé généré :<br /><br /> `<Filename>.g<LanguageSourceExtension>`<br /><br /> Si le paramètre **LanguageSourceExtension** n’est pas défini avec une valeur spécifique, l’extension de nom de fichier source par défaut pour un langage est utilisée : **.vb** pour [!INCLUDE[TLA#tla_visualb](../msbuild/includes/tlasharptla_visualb_md.md)], **.csharp** pour [!INCLUDE[TLA#tla_cshrp](../data-tools/includes/tlasharptla_cshrp_md.md)].|
|`LocalizationDirectivesToLocFile`|Paramètre **String** facultatif.<br /><br /> Spécifie comment générer des informations de localisation pour chaque fichier [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] source. Les options valides sont **None**, **CommentsOnly** et **All**.|
|`OutputPath`|Paramètre **String** obligatoire.<br /><br /> Spécifie le répertoire dans lequel les fichiers de code managé générés et les fichiers au format binaire [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] sont générés.|
|`OutputType`|Paramètre **String** obligatoire.<br /><br /> Spécifie le type d’assembly généré par un projet. Les options valides sont **winexe**, **exe**, **library** et **netmodule**.|
|`PageMarkup`|Paramètre **ITaskItem[]** facultatif.<br /><br /> Spécifie une liste de fichiers [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] à traiter.|
|`References`|Paramètre **ITaskItem[]** facultatif.<br /><br /> Spécifie la liste des références des fichiers aux assemblys qui contiennent les types qui sont utilisés dans les fichiers [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)].|
|`RequirePass2ForMainAssembly`|Paramètre de sortie **Boolean** facultatif.<br /><br /> Indique si le projet contient des fichiers [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] non localisables qui référencent des types locaux incorporés dans l’assembly principal.|
|`RequirePass2ForSatelliteAssembly`|Paramètre de sortie **Boolean** facultatif.<br /><br /> Indique si le projet contient des fichiers [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] localisables qui référencent des types locaux incorporés dans l’assembly principal.|
|`RootNamespace`|Paramètre **String** facultatif.<br /><br /> Spécifie l’espace de noms racine pour les classes qui se trouvent dans le projet. **RootNamespace** est également utilisé comme espace de noms par défaut d’un fichier de code managé généré quand le fichier [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] correspondant n’inclut pas l’attribut `x:Class`.|
|`SourceCodeFiles`|Paramètre **ITaskItem[]** facultatif.<br /><br /> Spécifie la liste des fichiers de code pour le projet actuel. La liste n’inclut pas les fichiers de code managé générés propres au langage.|
|`UICulture`|Paramètre **String** facultatif.<br /><br /> Spécifie l’assembly satellite pour la culture d’interface utilisateur dans lequel les fichiers au format binaire [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] sont incorporés. Si **UICulture** n’est pas défini, les fichiers au format binaire [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] sont incorporés dans l’assembly principal.|
|`XAMLDebuggingInformation`|Paramètre **booléen** facultatif.<br /><br /> Quand la valeur est **true**, des informations de diagnostic sont générées et incluses dans le [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] compilé pour faciliter le débogage.|

## <a name="remarks"></a>Notes

La tâche <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> compile généralement [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] au format binaire et génère des fichiers de code. Si un fichier [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] contient des références à des types définis dans le même projet, sa compilation au format binaire est différée par **MarkupCompilePass1** à une deuxième passe de compilation du balisage (**MarkupCompilePass2**). La compilation de ces fichiers doit être différée car ils doivent attendre que les types référencés définis localement soient compilés. Toutefois, si un fichier [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] a un attribut `x:Class`, <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> génère le fichier de code spécifique au langage de celui-ci.

Un fichier [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] est localisable s’il contient des éléments qui utilisent l’attribut `x:Uid` :

```xml
<Page x:Class="WPFMSBuildSample.Page1"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Uid="Page1Uid"
    >
  ...
</Page>
```

Un fichier [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] référence un type défini localement quand il déclare un espace de noms [!INCLUDE[TLA#tla_xml](../msbuild/includes/tlasharptla_xml_md.md)] qui utilise la valeur `clr-namespace` pour faire référence à un espace de noms dans le projet actuel :

```xml
<Page x:Class="WPFMSBuildSample.Page1"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:localNamespace="clr-namespace:WPFMSBuildSample"
    >
    <Grid>
      <Grid.Resources>
        <localNameSpace:LocalType x:Key="localType" />
      </Grid.Resources>
      ...
    </Grid>
</Page>
```

Si un fichier [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] est localisable ou référence un type défini localement, une deuxième passe de compilation du balisage est nécessaire, et exige l’exécution de [GenerateTemporaryTargetAssembly](../msbuild/generatetemporarytargetassembly-task.md), puis de [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md).

## <a name="example"></a>Exemple

L’exemple suivant montre comment convertir trois fichiers `Page`[!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] au format binaire. `Page1` contient une référence à un type, `Class1`, qui se trouve dans l’espace de noms racine du projet et n’est donc pas convertie au format binaire lors de cette passe de compilation du balisage. Au lieu de cela, [GenerateTemporaryTargetAssembly](../msbuild/generatetemporarytargetassembly-task.md) est exécutée et suivie par [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md).

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <UsingTask 
    TaskName="Microsoft.Build.Tasks.Windows.MarkupCompilePass1" 
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />
  <Target Name="MarkupCompilePass1Task">
    <MarkupCompilePass1 
      AssemblyName="WPFMSBuildSample"
      Language="C#"
      OutputType="WinExe"
      OutputPath="obj\Debug\"
      ApplicationMarkup="App.xaml"
      PageMarkup="Page1.xaml;Page2.xaml;Page3.xaml"
      SourceCodeFiles="Class1.cs"
      References="c:\windows\Microsoft.net\Framework\v2.0.50727\System.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationCore.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationFramework.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\WindowsBase.dll" />
  </Target>
</Project>
```

## <a name="see-also"></a>Voir aussi

[Informations de référence sur MSBuild WPF](../msbuild/wpf-msbuild-reference.md)  
[Task Reference (Informations de référence sur les tâches MSBuild)](../msbuild/wpf-msbuild-task-reference.md)  
[Informations de référence sur MSBuild](../msbuild/msbuild-reference.md)  
[Task Reference (Informations de référence sur les tâches MSBuild)](../msbuild/msbuild-task-reference.md)  
[Génération d’une application WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)  
[Vue d’ensemble des applications du navigateur XAML WPF](/dotnet/framework/wpf/app-development/wpf-xaml-browser-applications-overview)