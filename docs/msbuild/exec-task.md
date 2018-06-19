---
title: Exec, tâche | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Exec
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Exec task [MSBuild]
- MSBuild, Exec task
ms.assetid: c9b7525a-b1c9-40fc-8bce-77a5b8f960d8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ecb590c4562c79853c86ee65e9c5d4e3c059d5da
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2018
ms.locfileid: "31569685"
---
# <a name="exec-task"></a>Exec, tâche
Exécute la commande ou le programme spécifié en utilisant les arguments spécifiés.  
  
## <a name="parameters"></a>Paramètres  
 Le tableau ci-dessous décrit les paramètres de la tâche `Exec`.  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`Command`|Paramètre `String` requis.<br /><br /> Commande(s) à exécuter. Il peut s’agir de commandes système, par exemple attrib, ou d’un fichier exécutable, comme program.exe, runprogram.bat ou setup.msi.<br /><br /> Ce paramètre peut contenir plusieurs lignes de commandes. Vous pouvez également placer plusieurs commandes dans un fichier de commandes et l’exécuter à l’aide de ce paramètre.|  
|`ConsoleOutput`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Chaque sortie d’élément est une ligne de la sortie standard ou du flux d’erreur standard émise par l’outil. Celle-ci est uniquement capturée si `ConsoleToMsBuild` a la valeur `true`.|
|`ConsoleToMsBuild`|Paramètre `Boolean` facultatif.<br /><br /> Si la valeur est `true`, la tâche capture l’erreur standard et la sortie standard de l’outil pour les rendre disponibles dans le paramètre de sortie `ConsoleOutput`. La valeur par défaut est `false`.|
|`CustomErrorRegularExpression`|Paramètre `String` facultatif.<br /><br /> Spécifie une expression régulière utilisée pour détecter les lignes d’erreur dans la sortie de l’outil. C’est utile pour les outils qui produisent une sortie à la mise en forme inhabituelle.|  
|`CustomWarningRegularExpression`|Paramètre `String` facultatif.<br /><br /> Spécifie une expression régulière utilisée pour détecter les lignes d’avertissement dans la sortie de l’outil. C’est utile pour les outils qui produisent une sortie à la mise en forme inhabituelle.|  
|`EchoOff`|Paramètre `Boolean` facultatif.<br /><br /> Si la valeur est `true`, la tâche n’émet pas la forme développée de `Command` dans le journal MSBuild. La valeur par défaut est `false`.|
|`ExitCode`|Paramètre en lecture seule de sortie `Int32` facultatif.<br /><br /> Spécifie le code de sortie fourni par la commande exécutée.|  
|`IgnoreExitCode`|Paramètre `Boolean` facultatif.<br /><br /> Si la valeur est `true`, la tâche ignore le code de sortie fourni par la commande exécutée. Sinon, la tâche retourne `false` si la commande exécutée retourne un code de sortie différent de zéro.|  
|`IgnoreStandardErrorWarningFormat`|Paramètre `Boolean` facultatif.<br /><br /> Si la valeur est `false`, sélectionne des lignes dans la sortie qui correspondent au format d’erreur/avertissement standard, et les enregistre en tant qu’erreurs/avertissements. Si la valeur est `true`, désactiver ce comportement. La valeur par défaut est `false`.|  
|`Outputs`|Paramètre de sortie <xref:Microsoft.Build.Framework.ITaskItem>`[]` facultatif.<br /><br /> Contient les éléments de sortie de la tâche. La tâche `Exec` ne les définit pas elle-même. Au lieu de cela, vous pouvez les fournir comme si elle les définissait, pour qu’ils puissent être utilisés ultérieurement dans le projet.|  
|`StdErrEncoding`|Paramètre de sortie `String` facultatif.<br /><br /> Spécifie l’encodage du flux d’erreurs standard de tâche capturé. La valeur par défaut est l’encodage de sortie de la console actuelle.|  
|`StdOutEncoding`|Paramètre de sortie `String` facultatif.<br /><br /> Spécifie l’encodage du flux de sortie standard de tâche capturé. La valeur par défaut est l’encodage de sortie de la console actuelle.|  
|`WorkingDirectory`|Paramètre `String` facultatif.<br /><br /> Spécifie le répertoire dans lequel la commande sera exécutée.|  
  
## <a name="remarks"></a>Notes  
 Cette tâche est utile quand une tâche [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] spécifique pour le travail que vous voulez effectuer n’est pas disponible. Toutefois, la tâche `Exec`, contrairement à une tâche plus spécifique, ne peut pas effectuer de traitement ou d’opérations conditionnelles supplémentaires en fonction du résultat de l’outil ou de la commande exécutée.
  
 La tâche `Exec` appelle cmd.exe au lieu d’appeler directement un processus.  
  
 En plus des paramètres énumérés dans ce document, cette tâche hérite des paramètres de la classe <xref:Microsoft.Build.Tasks.ToolTaskExtension>, qui elle-même hérite de la classe <xref:Microsoft.Build.Utilities.ToolTask>. Pour obtenir la liste de ces paramètres supplémentaires et de leurs descriptions, consultez l’article [ToolTaskExtension Base Class (Classe de base ToolTaskExtension)](../msbuild/tooltaskextension-base-class.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise la tâche `Exec` pour exécuter une commande.  
  
```xml  
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
  
## <a name="see-also"></a>Voir aussi  
 [Tâches](../msbuild/msbuild-tasks.md)   
 [Task Reference (Informations de référence sur les tâches MSBuild)](../msbuild/msbuild-task-reference.md)
