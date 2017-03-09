---
title: "LC Task | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#LC"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild, LC task"
  - "LC task [MSBuild]"
ms.assetid: d5a53472-6f2a-42b8-a6db-593ca99c9790
caps.latest.revision: 15
caps.handback.revision: 15
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# LC Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Encapsule LC.exe, qui génère un fichier .license à partir d'un fichier .licx.  Pour plus d'informations sur LC.exe, consultez [Lc.exe \(License Compiler\)](../Topic/Lc.exe%20\(License%20Compiler\).md).  
  
## Paramètres  
 Le tableau suivant décrit les paramètres de la tâche `LC`.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`LicenseTarget`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem> obligatoire.<br /><br /> Spécifie l'exécutable pour lequel les fichiers .licenses sont générés.|  
|`NoLogo`|Paramètre `Boolean` facultatif.<br /><br /> Supprime l'affichage de la bannière de démarrage Microsoft.|  
|`OutputDirectory`|Paramètre `String` facultatif.<br /><br /> Spécifie le répertoire dans lequel placer les fichiers .licenses de sortie.|  
|`OutputLicense`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem> facultatif.<br /><br /> Spécifie le nom du fichier .licenses.  Si vous ne spécifiez pas de nom, le nom du fichier .licx est utilisé et le fichier .licenses est placé dans le répertoire qui contient le fichier .licx.|  
|`ReferencedAssemblies`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` optionnel.<br /><br /> Spécifie les composants référencés à charger lors de la génération du fichier .license.|  
|`SdkToolsPath`|Paramètre `String` facultatif.<br /><br /> Spécifie le chemin d'accès des outils du Kit de développement logiciel, comme resgen.exe.|  
|`Sources`|Paramètre <xref:Microsoft.Build.Framework.ITaskItem>`[]` obligatoire.<br /><br /> Spécifie les éléments qui contiennent des composants sous licence à inclure dans le fichier .licenses.  Pour plus d'informations, consultez la documentation du commutateur `/complist` dans [Lc.exe \(License Compiler\)](../Topic/Lc.exe%20\(License%20Compiler\).md).|  
  
 En plus des paramètres énumérés ci\-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.ToolTaskExtension>, qui hérite elle\-même de la classe <xref:Microsoft.Build.Utilities.ToolTask>.  Pour obtenir la liste de ces paramètres supplémentaires et de leurs descriptions, consultez [ToolTaskExtension Base Class](../msbuild/tooltaskextension-base-class.md).  
  
## Exemple  
 L'exemple suivant utilise la tâche `LC` pour compiler des licences.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
<!-- Item declarations, etc -->  
  
    <Target Name="CompileLicenses">  
        <LC  
            Sources="@(LicxFile)"  
            LicenseTarget="$(TargetFileName)"  
            OutputDirectory="$(IntermediateOutputPath)"  
            OutputLicenses="$(IntermediateOutputPath)$(TargetFileName).licenses"  
            ReferencedAssemblies="@(ReferencePath);@(ReferenceDependencyPaths)">  
  
            <Output  
                TaskParameter="OutputLicenses"  
                ItemName="CompiledLicenseFile"/>  
        </LC>  
    </Target>  
</Project>  
```  
  
## Voir aussi  
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)