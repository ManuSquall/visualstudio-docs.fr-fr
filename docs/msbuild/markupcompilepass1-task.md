---
title: "MarkupCompilePass1 Task | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "converting XAML to binary format [WPF MSBuild]"
  - "MarkupCompilePass1 task [WPF MSBuild], parameters"
  - "converting XAML projects to compiled binary format [WPF MSBuild]"
  - "MarkupCompilePass1 task [WPF MSBuild], converting XAML to binary format"
ms.assetid: 693d6945-fd6f-4698-8f64-9dfcb71052d3
caps.latest.revision: 8
caps.handback.revision: 8
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# MarkupCompilePass1 Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La tâche <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> convertit des fichiers projet [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] non localisables au format binaire compilé.  
  
## Paramètres de la tâche  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`AllGeneratedFiles`|Paramètre de sortie **ITaskItem\[\]** facultatif.<br /><br /> Contient une liste complète des fichiers générés par la tâche <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1>.|  
|`AlwaysCompileMarkupFilesInSeparateDomain`|Paramètre **Boolean** facultatif.<br /><br /> Spécifie s'il faut exécuter la tâche dans un <xref:System.AppDomain> séparé.  Si ce paramètre retourne la valeur **false**, la tâche s'exécute dans le même <xref:System.AppDomain> que [!INCLUDE[TLA#tla_msbuild](../msbuild/includes/tlasharptla_msbuild_md.md)] et s'exécute plus rapidement.  Si le paramètre retourne la valeur **true**, la tâche s'exécute plus lentement dans un deuxième <xref:System.AppDomain> isolé de [!INCLUDE[TLA2#tla_msbuild](../msbuild/includes/tla2sharptla_msbuild_md.md)].|  
|`ApplicationMarkup`|Paramètre **ITaskItem\[\]** facultatif.<br /><br /> Spécifie le nom du fichier [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] de définition d'application.|  
|`AssembliesGeneratedDuringBuild`|Paramètre **String\[\]** facultatif.<br /><br /> Spécifie des références aux assemblys qui sont modifiés lors du processus de génération.  Par exemple, une solution [!INCLUDE[TLA#tla_visualstu2005](../msbuild/includes/tlasharptla_visualstu2005_md.md)] peut contenir un projet qui référence la sortie compilée d'un autre projet.  Dans ce cas, la sortie compilée du deuxième projet peut être ajoutée au paramètre **AssembliesGeneratedDuringBuild**.<br /><br /> Remarque : le paramètre **AssembliesGeneratedDuringBuild** doit contenir des références au jeu complet des assemblys générés par une solution de génération.|  
|`AssemblyName`|Paramètre **string** requis.<br /><br /> Spécifie le nom court de l'assembly généré pour un projet.  Par exemple, si un projet génère un fichier exécutable [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)] dont le nom est **WinExeAssembly.exe**, le paramètre **AssemblyName** a la valeur **WinExeAssembly**.|  
|`AssemblyPublicKeyToken`|Paramètre **String** facultatif.<br /><br /> Spécifie le jeton de clé publique de l'assembly.|  
|`AssemblyVersion`|Paramètre **String** facultatif.<br /><br /> Spécifie le numéro de version de l'assembly.|  
|`ContentFiles`|Paramètre **ITaskItem\[\]** facultatif.<br /><br /> Spécifie la liste des fichiers de contenu libre.|  
|`DefineConstants`|Paramètre **String** facultatif.<br /><br /> Spécifie que la valeur actuelle de **DefineConstants** est conservée,  ce qui affecte la génération de l'assembly cible ; si ce paramètre est modifié, l'API publique de l'assembly cible peut être modifiée et la compilation des fichiers [!INCLUDE[TLA2#tla_titlexaml](../msbuild/includes/tla2sharptla_titlexaml_md.md)] qui référencent des types locaux peut être affectée.|  
|`ExtraBuildControlFiles`|Paramètre **ITaskItem\[\]** facultatif.<br /><br /> Spécifie une liste de fichiers qui contrôlent le déclenchement d'une régénération lorsque la tâche <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> est réexécutée ; une régénération est déclenchée si un de ces fichiers est modifié.|  
|`GeneratedBamlFiles`|Paramètre de sortie **ITaskItem\[\]** facultatif.<br /><br /> Contient la liste des fichiers générés au format binaire [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)].|  
|`GeneratedCodeFiles`|Paramètre de sortie **ITaskItem\[\]** facultatif.<br /><br /> Contient la liste des fichiers de code managé générés.|  
|`GeneratedLocalizationFiles`|Paramètre de sortie **ITaskItem\[\]** facultatif.<br /><br /> Contient la liste des fichiers de localisation générés pour chaque fichier [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] localisable.|  
|`HostInBrowser`|Paramètre **String** facultatif.<br /><br /> Spécifie si l'assembly généré est une [!INCLUDE[TLA#tla_xbap](../msbuild/includes/tlasharptla_xbap_md.md)].  Les options valides sont **true** et **false**.  Si la valeur est **true**, le code est généré pour prendre en charge l'hébergement de navigateur.|  
|`KnownReferencePaths`|Paramètre **String\[\]** facultatif.<br /><br /> Spécifie des références aux assemblys qui ne changent pas lors du processus de génération.  Inclut des assemblys localisés dans le [!INCLUDE[TLA#tla_gac](../msbuild/includes/tlasharptla_gac_md.md)], dans un répertoire d'installation [!INCLUDE[TLA#tla_netframewk](../misc/includes/tlasharptla_netframewk_md.md)], et ainsi de suite.|  
|`Language`|Paramètre **String** requis.<br /><br /> Spécifie le langage managé pris en charge par le compilateur.  les options valides sont **C\#**, **VB**, **JScript**, et **C\+\+**.|  
|`LanguageSourceExtension`|Paramètre **String** facultatif.<br /><br /> Spécifie l'extension qui est ajoutée à l'extension du fichier de code managé généré :<br /><br /> `<Filename>.g<LanguageSourceExtension>`<br /><br /> Si le paramètre **LanguageSourceExtension** n'est pas défini avec une valeur spécifique, on utilise l'extension du nom du fichier source par défaut pour un langage : **.vb** pour [!INCLUDE[TLA#tla_visualb](../msbuild/includes/tlasharptla_visualb_md.md)], **.csharp** pour [!INCLUDE[TLA#tla_cshrp](../msbuild/includes/tlasharptla_cshrp_md.md)].|  
|`LocalizationDirectivesToLocFile`|Paramètre **String** facultatif.<br /><br /> Spécifie comment générer des informations de localisation pour chaque fichier [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] source.  Les options valides sont **None**, **CommentsOnly** et **All**.|  
|`OutputPath`|Paramètre **String** requis.<br /><br /> Spécifie le répertoire dans lequel les fichiers de code managé générés et les fichiers de format binaire [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] sont générés.|  
|`OutputType`|Paramètre **String** requis.<br /><br /> Spécifie le type d'assembly généré par un projet.  Les options valides sont **winexe**, **exe**, **library** et **netmodule**.|  
|`PageMarkup`|Paramètre **ITaskItem\[\]** facultatif.<br /><br /> Spécifie une liste de fichiers [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] à traiter.|  
|`References`|Paramètre **ITaskItem\[\]** facultatif.<br /><br /> Spécifie la liste de références de fichiers aux assemblys qui contiennent les types utilisés dans les fichiers [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)].|  
|`RequirePass2ForMainAssembly`|Paramètre de sortie **Boolean** facultatif.<br /><br /> Indique si le projet contient des fichiers [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] non localisables qui référencent des types locaux incorporés dans l'assembly principal.|  
|`RequirePass2ForSatelliteAssembly`|Paramètre de sortie **Boolean** facultatif.<br /><br /> Indique si le projet contient des fichiers [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] localisables qui référencent des types locaux incorporés dans l'assembly principal.|  
|`RootNamespace`|Paramètre **String** facultatif.<br /><br /> Spécifie l'espace de noms racine pour les classes à l'intérieur du projet.  **RootNamespace** est également utilisé comme espace de noms par défaut d'un fichier de code managé généré lorsque le fichier [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] correspondant n'inclut pas l'attribut `x:Class`.|  
|`SourceCodeFiles`|Paramètre **ITaskItem\[\]** facultatif.<br /><br /> Spécifie la liste de fichiers de code pour le projet actuel.  La liste n'inclut pas les fichiers de code managé spécifiques au langage générés.|  
|`UICulture`|Paramètre **String** facultatif.<br /><br /> Spécifie l'assembly satellite pour la culture d'interface utilisateur dans lequel sont incorporés les fichiers de format binaire [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] générés.  Si **UICulture** n'est pas défini, les fichiers de format binaire [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] générés sont incorporés dans l'assembly principal.|  
|`XAMLDebuggingInformation`|Paramètre **Boolean** facultatif.<br /><br /> Lorsque la valeur est **true**, les informations de diagnostic sont générées et incluses dans le [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] compilé pour faciliter le débogage.|  
  
## Notes  
 La tâche <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> compile en général [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] au format binaire et génère des fichiers de code.  Si un fichier [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] contient des références aux types définis dans le même projet, sa compilation au format binaire est différée par **MarkupCompilePass1** à un deuxième passage de compilation du balisage \(**MarkupCompilePass2**\).  La compilation de ces fichiers doit être différée car ils doivent attendre que les types définis localement référencés soient compilés.  Toutefois, si un fichier [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] dispose d'un attribut `x:Class`, <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> génère le fichier de code spécifique au langage.  
  
 Un fichier [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] est localisable s'il contient des éléments qui utilisent l'attribut `x:Uid` :  
  
```  
<Page x:Class="WPFMSBuildSample.Page1"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    x:Uid="Page1Uid"  
    >  
  ...  
</Page>  
```  
  
 Un fichier [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] référence un type défini localement lorsqu'il déclare un espace de noms [!INCLUDE[TLA#tla_xml](../msbuild/includes/tlasharptla_xml_md.md)] utilisant la valeur `clr-namespace` pour faire référence à un espace de noms dans le projet actuel :  
  
```  
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
  
 Si un fichier [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] est localisable ou référence un type défini localement, un deuxième passage de compilation du balisage est nécessaire, ce qui requiert l'exécution de la [GenerateTemporaryTargetAssembly](../msbuild/generatetemporarytargetassembly-task.md), puis de la [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md).  
  
## Exemple  
 L'exemple suivant indique comment convertir trois fichiers `Page`[!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] en fichiers binaires.  `Page1` contient une référence à un type, `Class1`, qui se trouve dans l'espace de noms racine du projet et par conséquent, n'est pas converti au format binaire dans ce passage de compilation du balisage.  À la place, la [GenerateTemporaryTargetAssembly](../msbuild/generatetemporarytargetassembly-task.md) est exécutée et suivie par la [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md).  
  
```  
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
  
## Voir aussi  
 [WPF MSBuild Reference](../msbuild/wpf-msbuild-reference.md)   
 [Task Reference](../msbuild/wpf-msbuild-task-reference.md)   
 [MSBuild Reference](../msbuild/msbuild-reference.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)   
 [Génération d'une application WPF \(WPF\)](../Topic/Building%20a%20WPF%20Application%20\(WPF\).md)   
 [Vue d'ensemble des applications de navigateur XAML](../Topic/WPF%20XAML%20Browser%20Applications%20Overview.md)