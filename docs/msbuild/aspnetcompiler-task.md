---
title: "AspNetCompiler Task | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/msbuild/2003#AspNetCompiler"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild, AspNetCompiler task"
  - "AspNetCompiler task [MSBuild]"
ms.assetid: f811c019-a67b-4d54-82e6-e29549496f6e
caps.latest.revision: 11
caps.handback.revision: 11
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# AspNetCompiler Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La tâche `AspNetCompiler` inclut aspnet\_compiler.exe, un utilitaire servant à précompiler des applications [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], dans un wrapper.  
  
## Paramètres de la tâche  
 Le tableau suivant décrit les paramètres de la tâche `AspNetCompiler`.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`AllowPartiallyTrustedCallers`|Paramètre `Boolean` facultatif.<br /><br /> Si ce paramètre a la valeur `true`, l'assembly avec un nom fort autorisera les appelants dotés d'un niveau de confiance partielle.|  
|`Clean`|Paramètre `Boolean` facultatif.<br /><br /> Si ce paramètre a la valeur `true`, l'application précompilée générée est nettoyée.  Tout composant précédemment compilé est recompilé.  La valeur par défaut est `false`.  Ce paramètre correspond au commutateur **\-c** dans aspnet\_compiler.exe.|  
|`Debug`|Paramètre `Boolean` facultatif.<br /><br /> Si ce paramètre a la valeur `true`, des informations de débogage \(fichier .PDB\) sont publiées pendant la compilation.  La valeur par défaut est `false`.  Ce paramètre correspond au commutateur **\-d** dans aspnet\_compiler.exe.|  
|`DelaySign`|Paramètre `Boolean` facultatif.<br /><br /> Si ce paramètre a la valeur `true`, l'assembly n'est pas complètement signé lors de sa création.|  
|`FixedNames`|Paramètre `Boolean` facultatif.<br /><br /> Si ce paramètre a la valeur `true`, des noms fixes sont attribués aux assemblys compilés.|  
|`Force`|Paramètre `Boolean` facultatif.<br /><br /> Si ce paramètre a la valeur `true`, la tâche remplace le répertoire cible s'il existe déjà.  Le contenu existant est perdu.  La valeur par défaut est `false`.  Ce paramètre correspond au commutateur **\-f** dans aspnet\_compiler.exe.|  
|`KeyContainer`|Paramètre `String` facultatif.<br /><br /> Spécifie un conteneur de clé de nom fort.|  
|`KeyFile`|Paramètre `String` facultatif.<br /><br /> Spécifie le chemin d'accès physique au fichier de clé de nom fort.|  
|`MetabasePath`|Paramètre `String` facultatif.<br /><br /> Spécifie le chemin d'accès complet à la métabase IIS de l'application.  Ce paramètre ne peut pas être combiné avec les paramètres `VirtualPath` ou `PhysicalPath`.  Ce paramètre correspond au commutateur **\-m** dans aspnet\_compiler.exe.|  
|`PhysicalPath`|Paramètre `String` facultatif.<br /><br /> Spécifie le chemin d'accès physique de l'application à compiler.  Si ce paramètre est manquant, la métabase IIS est utilisée pour localiser l'application.  Ce paramètre correspond au commutateur **\-p** dans aspnet\_compiler.exe.|  
|`TargetFrameworkMoniker`|Paramètre `String` facultatif.<br /><br /> Spécifie le TargetFrameworkMoniker indiquant quelle version du .NET Framework d'aspnet\_compiler.exe doit être utilisée.  Uniquement accepte des monikers .NET Framework.|  
|`TargetPath`|Paramètre `String` facultatif.<br /><br /> Spécifie le chemin d'accès physique à l'emplacement dans lequel l'application est compilée.  S'il n'est pas spécifié, l'application est précompilée sur place.|  
|`Updateable`|Paramètre `Boolean` facultatif.<br /><br /> Si ce paramètre a la valeur `true`, l'application précompilée peut être mise à jour.  La valeur par défaut est `false`.  Ce paramètre correspond au commutateur **\-u** dans aspnet\_compiler.exe.|  
|`VirtualPath`|Paramètre `String` facultatif.<br /><br /> Chemin d'accès virtuel de l'application à compiler.  Si `PhysicalPath` est spécifié, le chemin d'accès physique est utilisé pour localiser l'application.  Sinon, la métabase IIS est utilisée et l'application est supposée être hébergée dans le site par défaut.  Ce paramètre correspond au commutateur **\-v** dans aspnet\_compiler.exe.|  
  
## Notes  
 En plus des paramètres énumérés ci\-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.ToolTaskExtension>, qui hérite elle\-même de la classe <xref:Microsoft.Build.Utilities.ToolTask>.  Pour obtenir la liste de ces paramètres supplémentaires et de leurs descriptions, consultez [ToolTaskExtension Base Class](../msbuild/tooltaskextension-base-class.md).  
  
## Exemple  
 L'exemple de code suivant utilise la tâche `AspNetCompiler` pour précompiler une application [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="PrecompileWeb">  
        <AspNetCompiler  
            VirtualPath="/MyWebSite"  
            PhysicalPath="c:\inetpub\wwwroot\MyWebSite\"  
            TargetPath="c:\precompiledweb\MyWebSite\"  
            Force="true"  
            Debug="true"  
        />  
    </Target>  
</Project>  
```  
  
## Voir aussi  
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)