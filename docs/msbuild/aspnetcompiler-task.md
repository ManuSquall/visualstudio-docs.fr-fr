---
title: "Utilisation de la tâche AspNetCompiler pour précompiler des applications ASP.NET | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: msbuild
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#AspNetCompiler
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, AspNetCompiler task
- AspNetCompiler task [MSBuild]
ms.assetid: f811c019-a67b-4d54-82e6-e29549496f6e
caps.latest.revision: 
author: Mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- aspnet
ms.openlocfilehash: b1528cd71c689876cd2c496e9cfdaaf0a97f0186
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="aspnetcompiler-task"></a>AspNetCompiler, tâche
La tâche `AspNetCompiler` inclut dans un wrapper aspnet_compiler.exe, un utilitaire permettant de précompiler des applications [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  
  
## <a name="task-parameters"></a>Paramètres de tâche  
 Le tableau ci-dessous décrit les paramètres de la tâche `AspNetCompiler`.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`AllowPartiallyTrustedCallers`|Paramètre `Boolean` facultatif.<br /><br /> Si ce paramètre a la valeur `true`, l’assembly à nom fort autorise les appelants partiellement fiables.|  
|`Clean`|Paramètre `Boolean` facultatif.<br /><br /> Si ce paramètre a la valeur `true`, l’application précompilée est générée après nettoyage. Tout composant précédemment compilé est recompilé. La valeur par défaut est `false`. Ce paramètre correspond au commutateur **-c** dans aspnet_compiler.exe.|  
|`Debug`|Paramètre `Boolean` facultatif.<br /><br /> Si ce paramètre a la valeur `true`, des informations de débogage (fichier .PDB) sont émises pendant la compilation. La valeur par défaut est `false`. Ce paramètre correspond au commutateur **-d** dans aspnet_compiler.exe.|  
|`DelaySign`|Paramètre `Boolean` facultatif.<br /><br /> Si ce paramètre a la valeur `true`, l’assembly n’est pas complètement signé quand il est créé.|  
|`FixedNames`|Paramètre `Boolean` facultatif.<br /><br /> Si ce paramètre a la valeur `true`, des noms fixes sont attribués aux assemblys compilés.|  
|`Force`|Paramètre `Boolean` facultatif.<br /><br /> Si ce paramètre a la valeur `true`, la tâche remplace le répertoire cible s’il existe déjà. Le contenu existant est perdu. La valeur par défaut est `false`. Ce paramètre correspond au commutateur **-f** dans aspnet_compiler.exe.|  
|`KeyContainer`|Paramètre `String` facultatif.<br /><br /> Spécifie un conteneur de clé de nom fort.|  
|`KeyFile`|Paramètre `String` facultatif.<br /><br /> Spécifie le chemin physique au fichier de clé de nom fort.|  
|`MetabasePath`|Paramètre `String` facultatif.<br /><br /> Spécifie le chemin complet à la métabase IIS de l’application. Vous ne pouvez pas combiner ce paramètre avec les paramètres `VirtualPath` ou `PhysicalPath`. Ce paramètre correspond au commutateur **-m** dans aspnet_compiler.exe.|  
|`PhysicalPath`|Paramètre `String` facultatif.<br /><br /> Spécifie le chemin physique de l’application à compiler. Si ce paramètre est manquant, la métabase IIS est utilisée pour localiser l’application. Ce paramètre correspond au commutateur **-p** dans aspnet_compiler.exe.|  
|`TargetFrameworkMoniker`|Paramètre `String` facultatif.<br /><br /> Spécifie le TargetFrameworkMoniker indiquant la version du .NET Framework d’aspnet_compiler.exe à utiliser. Accepte uniquement des monikers .NET Framework.|  
|`TargetPath`|Paramètre `String` facultatif.<br /><br /> Spécifie le chemin physique à l’emplacement dans lequel l’application est compilée. S’il n’est pas spécifié, l’application est précompilée sur place.|  
|`Updateable`|Paramètre `Boolean` facultatif.<br /><br /> Si ce paramètre a la valeur `true`, l’application précompilée peut être mise à jour.  La valeur par défaut est `false`. Ce paramètre correspond au commutateur **-u** dans aspnet_compiler.exe.|  
|`VirtualPath`|Paramètre `String` facultatif.<br /><br /> Chemin virtuel de l’application à compiler. Si `PhysicalPath` est spécifié, le chemin physique est utilisé pour localiser l’application. Sinon, la métabase IIS est utilisée et l’application se trouve théoriquement dans le site par défaut. Ce paramètre correspond au commutateur **-v** dans aspnet_compiler.exe.|  
  
## <a name="remarks"></a>Notes  
 En plus des paramètres énumérés ci-dessus, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.ToolTaskExtension>, qui elle-même hérite de la classe <xref:Microsoft.Build.Utilities.ToolTask>. Pour obtenir la liste de ces paramètres supplémentaires et de leurs descriptions, consultez l’article [ToolTaskExtension Base Class (Classe de base ToolTaskExtension)](../msbuild/tooltaskextension-base-class.md).  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant utilise la tâche `AspNetCompiler` pour précompiler une application [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  
  
```xml  
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
  
## <a name="see-also"></a>Voir aussi  
 [Tâches](../msbuild/msbuild-tasks.md)   
 [Task Reference (Informations de référence sur les tâches MSBuild)](../msbuild/msbuild-task-reference.md)
