---
title: "Exec Task | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#Exec"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "Exec task [MSBuild]"
  - "MSBuild, Exec task"
ms.assetid: c9b7525a-b1c9-40fc-8bce-77a5b8f960d8
caps.latest.revision: 20
caps.handback.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Exec Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Exécute la commande ou le programme spécifié à l'aide des arguments indiqués.  
  
## Paramètres  
 Le tableau suivant décrit les paramètres de la tâche `Exec`.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`Command`|Paramètre `String` obligatoire.<br /><br /> Commande\(s\) à exécuter.  Il peut s'agir de commandes système, par exemple attrib, ou d'un fichier exécutable, comme program.exe, runprogram.bat ou setup.msi.<br /><br /> Ce paramètre peut contenir plusieurs lignes de commandes.  Vous pouvez également placer plusieurs commandes dans un fichier de commandes et l'exécuter à l'aide de ce paramètre.|  
|`CustomErrorRegularExpression`|Paramètre `String` facultatif.<br /><br /> Spécifie une expression régulière permettant de repérer les lignes d'erreur dans la sortie de l'outil.  Cela est utile pour les outils qui produisent une sortie dans un format inhabituel.|  
|`CustomWarningRegularExpression`|Paramètre `String` facultatif.<br /><br /> Spécifie une expression régulière permettant de repérer les lignes d'avertissement dans la sortie de l'outil.  Cela est utile pour les outils qui produisent une sortie dans un format inhabituel.|  
|`ExitCode`|Paramètre de sortie en lecture seule `Int32` facultatif.<br /><br /> Spécifie le code de sortie fourni par la commande exécutée.|  
|`IgnoreExitCode`|Paramètre `Boolean` facultatif.<br /><br /> Si la valeur est `true`, la tâche ignore le code de sortie fourni par la commande exécutée.  Sinon, la tâche retourne `false` si la commande exécutée retourne un code de sortie différent de zéro.|  
|`IgnoreStandardErrorWarningFormat`|Paramètre `Boolean` facultatif.<br /><br /> Si la valeur est `false`, les lignes dans la sortie qui correspondent au format d'erreur\/avertissement standard sont sélectionnées et journalisées en tant qu'erreurs\/avertissements.  Si la valeur est `true`, désactiver ce comportement.|  
|`Outputs`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Contient les éléments de sortie de la tâche.  La tâche `Exec` ne les définit pas elle\-même.  Au lieu de cela, vous pouvez les fournir comme si la tâche les avait définis, afin qu'ils puissent être utilisés ultérieurement dans le projet.|  
|`StdErrEncoding`|Paramètre de sortie `String` facultatif.<br /><br /> Spécifie l'encodage du flux d'erreur standard de la tâche capturé.  La valeur par défaut est l'encodage de sortie de la console active.|  
|`StdOutEncoding`|Paramètre de sortie `String` facultatif.<br /><br /> Spécifie l'encodage du flux de sortie standard de la tâche capturé.  La valeur par défaut est l'encodage de sortie de la console active.|  
|`WorkingDirectory`|Paramètre `String` facultatif.<br /><br /> Spécifie le répertoire dans lequel la commande doit s'exécuter.|  
  
## Notes  
 Cette tâche est utile lorsqu'une tâche [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] spécifique au travail à effectuer n'est pas disponible.  Cependant, contrairement à une tâche plus spécifique, la tâche `Exec` ne peut recueillir la sortie de l'outil ou de la commande qu'elle exécute.  
  
 La tâche `Exec` appelle cmd.exe au lieu d'appeler directement un processus.  
  
 En plus des paramètres énumérés dans ce document, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.ToolTaskExtension>, qui hérite elle\-même de la classe <xref:Microsoft.Build.Utilities.ToolTask>.  Pour obtenir la liste de ces paramètres supplémentaires et de leurs descriptions, consultez [ToolTaskExtension Base Class](../msbuild/tooltaskextension-base-class.md).  
  
## Exemple  
 L'exemple suivant utilise la tâche `Exec` pour exécuter une commande.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <Binaries Include="*.dll;*.exe"/>  
    </ItemGroup>  
  
    <Target Name="SetACL">  
        <!-- set security on binaries-->  
        <Exec Command="echo y| cacls %(Binaries.Identity) /G everyone:R"/>  
    </Target>  
  
</Project>  
```  
  
## Voir aussi  
 [Tasks](../msbuild/msbuild-tasks.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)