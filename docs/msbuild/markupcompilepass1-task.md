---
title: MarkupCompilePass1, tâche | Microsoft Docs
ms.date: 11/04/2016
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a847f096edf5e42623cb2cb32cf4fd871a89aad7
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633510"
---
# <a name="markupcompilepass1-task"></a>MarkupCompilePass1, tâche

La <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> tâche convertit les fichiers de projet XAML non localisables en format binaire compilé.

## <a name="task-parameters"></a>Paramètres de tâche

| Paramètre | Description |
| - | - |
| `AllGeneratedFiles` | Paramètre de sortie **ITaskItem[]** facultatif.<br /><br /> Contient une liste complète des fichiers qui sont générés par la tâche <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1>. |
| `AlwaysCompileMarkupFilesInSeparateDomain` | Paramètre **Boolean** optionnel.<br /><br /> Indique si la tâche doit être exécutée dans un <xref:System.AppDomain> séparé. Si ce paramètre revient **faux,** la tâche s’exécute dans le même <xref:System.AppDomain> que MSBuild et il fonctionne plus vite. Si le paramètre revient **vrai,** la tâche s’exécute en une seconde <xref:System.AppDomain> qui est isolée de MSBuild et fonctionne plus lentement. |
| `ApplicationMarkup` | Paramètre **ITaskItem[]** en option.<br /><br /> Spécifie le nom de la définition d’application fichier XAML. |
| `AssembliesGeneratedDuringBuild` | Paramètre **de chaîne en** option.<br /><br /> Spécifie des références à des assemblys qui changent pendant le processus de génération. Par exemple, une solution Visual Studio peut contenir un projet qui référence la sortie compilée d’un autre projet. Dans ce cas, la sortie compilée du deuxième projet peut être ajoutée au paramètre **AssembliesGeneratedDuringBuild**.<br /><br /> Remarque : Le paramètre **AssembliesGeneratedDuringBuild** doit contenir des références au jeu complet des assemblys générés par une solution de génération. |
| `AssemblyName` | Paramètre **de chaîne** requis.<br /><br /> Spécifie le nom court de l’assembly généré pour un projet. Par exemple, si un projet génère un Windows exécutable dont le nom est *WinExeAssembly.exe*, le paramètre **AssemblyName** a une valeur de **WinExeAssembly**. |
| `AssemblyPublicKeyToken` | Paramètre **de chaîne** facultatif.<br /><br /> Spécifie le jeton de clé publique de l’assembly. |
| `AssemblyVersion` | Paramètre **de chaîne** facultatif.<br /><br /> Spécifie le numéro de version de l’assembly. |
| `ContentFiles` | Paramètre **ITaskItem[]** en option.<br /><br /> Spécifie la liste des fichiers de contenu libre. |
| `DefineConstants` | Paramètre **de chaîne** facultatif.<br /><br /> Indique que la valeur actuelle de **DefineConstants** est conservée, qui affecte la génération d’assemblage cible; si ce paramètre est modifié, l’API publique dans l’assemblage cible peut être modifié et la compilation de fichiers XAML qui font référence aux types locaux peut être affectée. |
| `ExtraBuildControlFiles` | Paramètre **ITaskItem[]** en option.<br /><br /> Spécifie une liste de fichiers qui contrôlent si une régénération est déclenchée quand la tâche <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> est réexécutée ; une régénération est déclenchée si l’un de ces fichiers change. |
| `GeneratedBamlFiles` | Paramètre de sortie **ITaskItem[]** facultatif.<br /><br /> Contient la liste des fichiers générés dans le format binaire XAML. |
| `GeneratedCodeFiles` | Paramètre de sortie **ITaskItem[]** facultatif.<br /><br /> Contient la liste des fichiers de code managé générés. |
| `GeneratedLocalizationFiles` | Paramètre de sortie **ITaskItem[]** facultatif.<br /><br /> Contient la liste des fichiers de localisation qui ont été générés pour chaque fichier XAML localisable. |
| `HostInBrowser` | Paramètre **de chaîne** facultatif.<br /><br /> Précise si l’assemblage généré est une application de navigateur XAML (XBAP). Les options valides sont **true** et **false**. Si **true**, du code est généré pour prendre en charge l’hébergement de navigateur. |
| `KnownReferencePaths` | Paramètre **de chaîne en** option.<br /><br /> Spécifie des références à des assemblys qui ne changent pas pendant le processus de génération. Inclut les assemblages situés dans le cache d’assemblage global (GAC), dans un répertoire d’installation .NET, et ainsi de suite. |
| `Language` | Paramètre **de chaîne** requis.<br /><br /> Spécifie le langage managé pris en charge par le compilateur. Les options valides sont **C#**, **VB**, **JScript** et **C++**. |
| `LanguageSourceExtension` | Paramètre **de chaîne** facultatif.<br /><br /> Spécifie l’extension ajoutée à l’extension du fichier de code managé généré :<br /><br /> `<Filename>.g<LanguageSourceExtension>`<br /><br /> Si le paramètre **LanguageSourceExtension n’est** pas défini avec une valeur spécifique, l’extension de nom de fichier source par défaut pour une langue est utilisée : *.vb* pour Visual Basic, *.csharp* pour C. |
| `LocalizationDirectivesToLocFile` | Paramètre **de chaîne** facultatif.<br /><br /> Précise comment générer des informations de localisation pour chaque fichier XAML source. Les options valides sont **None**, **CommentsOnly** et **All**. |
| `OutputPath` | Paramètre **de chaîne** requis.<br /><br /> Spécifie l’annuaire dans lequel les fichiers de code gérés générés et les fichiers de format binaire XAML sont générés. |
| `OutputType` | Paramètre **de chaîne** requis.<br /><br /> Spécifie le type d’assembly généré par un projet. Les options valides sont **winexe**, **exe**, **library** et **netmodule**. |
| `PageMarkup` | Paramètre **ITaskItem[]** en option.<br /><br /> Spécifie une liste de fichiers XAML à traiter. |
| `References` | Paramètre **ITaskItem[]** en option.<br /><br /> Spécifie la liste des références des fichiers aux assemblages qui contiennent les types qui sont utilisés dans les fichiers XAML. |
| `RequirePass2ForMainAssembly` | Paramètre de sortie **Boolean** facultatif.<br /><br /> Indique si le projet contient des fichiers XAML non localisables qui font référence aux types locaux qui sont intégrés dans l’assemblage principal. |
| `RequirePass2ForSatelliteAssembly` | Paramètre de sortie **Boolean** facultatif.<br /><br /> Indique si le projet contient des fichiers XAML localisables qui font référence aux types locaux qui sont intégrés dans l’assemblage principal. |
| `RootNamespace` | Paramètre **de chaîne** facultatif.<br /><br /> Spécifie l’espace de noms racine pour les classes qui se trouvent dans le projet. **RootNamespace** est également utilisé comme l’espace nom par défaut d’un fichier `x:Class` de code géré généré lorsque le fichier XAML correspondant n’inclut pas l’attribut. |
| `SourceCodeFiles` | Paramètre **ITaskItem[]** en option.<br /><br /> Spécifie la liste des fichiers de code pour le projet actuel. La liste n’inclut pas les fichiers de code managé générés propres au langage. |
| `UICulture` | Paramètre **de chaîne** facultatif.<br /><br /> Spécifie l’assemblage satellite de la culture de l’interface utilisateur dans laquelle les fichiers de format binaire XAML générés sont intégrés. Si **UICulture n’est** pas définie, les fichiers de format binaire XAML générés sont intégrés dans l’assemblage principal. |
| `XAMLDebuggingInformation` | Paramètre **Boolean** optionnel.<br /><br /> Lorsque **c’est vrai,** l’information diagnostique est générée et incluse dans le XAML compilé afin d’aider à débogage. |

## <a name="remarks"></a>Notes 

La <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> tâche compile généralement XAML en format binaire et génère des fichiers de code. Si un fichier XAML contient des références à des types qui sont définis dans le même projet, sa compilation au format binaire est reportée par **MarkupCompilePass1** à un deuxième pass de compilation de balisage (**MarkupCompilePass2**). La compilation de ces fichiers doit être différée car ils doivent attendre que les types référencés définis localement soient compilés. Toutefois, si un fichier XAML a un `x:Class` attribut, <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> génère le fichier de code spécifique à la langue pour elle.

Un fichier XAML est localisable s’il contient des éléments qui utilisent l’attribut `x:Uid` :

```xml
<Page x:Class="WPFMSBuildSample.Page1"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Uid="Page1Uid"
    >
  ...
</Page>
```

Un fichier XAML fait référence à un type défini localement lorsqu’il déclare un espace de nom XML qui utilise la `clr-namespace` valeur pour désigner un espace de nom dans le projet en cours :

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

Si un fichier XAML est localisable, ou fait référence à un type défini localement, un deuxième laissez-passer de compilation de balisage est nécessaire, ce qui nécessite l’exécution de la [GenerateTemporaryTargetAssembly,](../msbuild/generatetemporarytargetassembly-task.md) puis le [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md).

## <a name="example"></a> Exemple

L’exemple suivant montre comment convertir trois fichiers *Page* XAML en fichiers format binaire. *Page1* contient une référence à un type, `Class1`, qui se trouve dans l’espace de noms racine du projet et n’est donc pas convertie au format binaire lors de cette passe de compilation du balisage. Au lieu de cela, [GenerateTemporaryTargetAssembly](../msbuild/generatetemporarytargetassembly-task.md) est exécutée et suivie par [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md).

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

- [WPF MSBuild référence](../msbuild/wpf-msbuild-reference.md)
- [Référence de tâche WPF MSBuild](../msbuild/wpf-msbuild-task-reference.md)
- [Référence MSBuild](../msbuild/msbuild-reference.md)
- [Référence de tâche MSBuild](../msbuild/msbuild-task-reference.md)
- [Générer une application WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
- [Vue d’ensemble des applications du navigateur XAML WPF](/dotnet/framework/wpf/app-development/wpf-xaml-browser-applications-overview)