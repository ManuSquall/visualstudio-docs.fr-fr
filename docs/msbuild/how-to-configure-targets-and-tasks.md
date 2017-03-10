---
title: "Guide pratique pour configurer les cibles et les tâches | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 92814100-392a-471d-96fd-e26f637d6cc2
caps.latest.revision: 5
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 79460291e91f0659df0a4241e17616e55187a0e2
ms.openlocfilehash: ac979e7287046164db37848778f648656f7230a6
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-configure-targets-and-tasks"></a>Guide pratique pour configurer les cibles et les tâches
Des tâches MSBuild sélectionnées peuvent être définies pour s’exécuter dans l’environnement qu’elles ciblent, quel que soit l’environnement de l’ordinateur de développement. Par exemple, quand vous utilisez un ordinateur 64 bits pour générer une application ciblant une architecture 32 bits, les tâches sélectionnées sont exécutées dans un processus 32 bits.  
  
> [!NOTE]
>  Si une tâche de génération est écrite dans un langage .NET, comme Visual C# ou Visual Basic, et qu’elle n’utilise pas des ressources natives ou des outils natifs, elle est exécutée dans un contexte cible sans adaptation.  
  
## <a name="usingtask-attributes-and-task-parameters"></a>Attributs UsingTask et paramètres de tâche  
 Les attributs `UsingTask` suivants affectent toutes les opérations d’une tâche dans un processus de génération spécifique :  
  
-   L’attribut `Runtime`, s’il est présent, définit la version du common language runtime (CLR) et peut prendre une des valeurs suivantes : `CLR2`, `CLR4`, `CurrentRuntime` ou `*` (n’importe quel runtime).  
  
-   L’attribut `Architecture`, s’il est présent, définit la plateforme et le nombre de bits, et peut prendre une des valeurs suivantes : `x86`, `x64`, `CurrentArchitecture` ou `*` (n’importe quelle architecture).  
  
-   L’attribut `TaskFactory`, s’il est présent, définit la fabrique de tâches qui crée et exécute l’instance de tâche, et il prend uniquement la valeur `TaskHostFactory`. Pour plus d’informations, consultez la section « Fabriques de tâches » plus loin dans ce document.  
  
```xml  
<UsingTask TaskName="SimpleTask"   
   Runtime="CLR2"  
   Architecture="x86"  
   AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v3.5.dll" />  
```  
  
 Vous pouvez également utiliser les paramètres `MSBuildRuntime` et `MSBuildArchitecture` pour définir le contexte cible d’une tâche spécifique.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
   <Target Name="MyTarget">  
      <SimpleTask MSBuildRuntime="CLR2" MSBuildArchitecture= "x86"/>  
   </Target>  
</Project>  
```  
  
 Avant que MSBuild exécute une tâche, il recherche un attribut `UsingTask` qui a le même contexte cible.  Les paramètres spécifiés dans l’attribut `UsingTask` mais qui ne sont pas dans la tâche correspondante sont considérés comme étant en correspondance.  Les paramètres spécifiés dans la tâche mais qui ne sont pas dans l’attribut `UsingTask` correspondant sont également considérés comme étant en correspondance. Si des valeurs de paramètre ne sont pas spécifiées dans l’attribut `UsingTask` ou dans la tâche, leur valeur par défaut est `*` (n’importe quel paramètre).  
  
> [!WARNING]
>  S’il existe plusieurs attributs `UsingTask` et que tous ont des attributs `TaskName`, `Runtime` et `Architecture` correspondants, le dernier à être évalué remplace les autres.  
  
 Si des paramètres sont définis sur la tâche, MSBuild tente de trouver un attribut `UsingTask` qui correspond à ces paramètres ou qui au moins n’est pas en conflit avec ceux-ci.  Plusieurs attributs `UsingTask` peuvent spécifier le contexte cible de la même tâche.  Par exemple, une tâche qui a des exécutables différents pour des environnements cibles différents peut se présenter comme ceci :  
  
```xml  
<UsingTask TaskName="MyTool"   
   Runtime="CLR2"  
   Architecture="x86"  
   AssemblyFile="$(MyToolsPath)\MyTool.v2.0.dll" />  
  
<UsingTask TaskName="MyTool"   
   Runtime="CLR4"  
   Architecture="x86"  
   AssemblyFile="$(MyToolsPath)\MyTool.4.0.dll" />  
  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
   <Target Name="MyTarget">  
      <MyTool MSBuildRuntime="CLR2" MSBuildArchitecture= "x86"/>  
   </Target>  
</Project>  
  
```  
  
## <a name="task-factories"></a>Fabriques de tâches  
 Avant d’exécuter une tâche, MSBuild vérifie si elle est désignée pour s’exécuter dans le contexte logiciel actif.  Si la tâche est bien désignée pour cela, MSBuild la passe à AssemblyTaskFactory, qui s’exécute dans le processus actif ; dans le cas contraire, MSBuild passe la tâche à TaskHostFactory, qui exécute la tâche dans un processus qui correspond au contexte cible. Même si le contexte actif et le contexte cible correspondent, vous pouvez forcer une tâche à s’exécuter hors processus (pour l’isolation, la sécurité ou pour d’autres raisons) en définissant `TaskFactory` sur `TaskHostFactory`.  
  
```xml  
<UsingTask TaskName="MisbehavingTask"   
   TaskFactory="TaskHostFactory"  
   AssemblyFile="$(MSBuildToolsPath)\MyTasks.dll">  
</UsingTask>  
```  
  
## <a name="phantom-task-parameters"></a>Paramètres de tâche fantôme  
 Comme tous les autres paramètres de tâche, `MSBuildRuntime` et `MSBuildArchitecture` peuvent être définis à partir de propriétés de génération.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
   <PropertyGroup>  
      <FrameworkVersion>3.0</FrameworkVersion>  
   </PropertyGroup>  
   <Target Name="MyTarget">  
      <SimpleTask MSBuildRuntime="$(FrameworkVerion)" MSBuildArchitecture= "x86"/>  
   </Target>  
</Project>  
```xml  
  
 Unlike other task parameters, `MSBuildRuntime` and `MSBuildArchitecture` are not apparent to the task itself.  To write a task that is aware of the context in which it runs, you must either test the context by calling the .NET Framework, or use build properties to pass the context information through other task parameters.  
  
> [!NOTE]
>  `UsingTask` attributes can be set from toolset and environment properties.  
  
 The `MSBuildRuntime` and `MSBuildArchitecture` parameters provide the most flexible way to set the target context, but also the most limited in scope.  On the one hand, because they are set on the task instance itself and are not evaluated until the task is about to run, they can derive their value from the full scope of properties available at both evaluation-time and build-time.  On the other hand, these parameters only apply to a particular instance of a task in a particular target.  
  
> [!NOTE]
>  Task parameters are evaluated in the context of the parent node, not in the context of the task host.Environment variables that are runtime- or architecture- dependent (such as the Program files location) will evaluate to the value that matches the parent node.  However, if the same environment variable is read directly by the task, it will correctly be evaluated in the context of the task host.  
  
## See Also  
 [Configuring Targets and Tasks](../msbuild/configuring-targets-and-tasks.md)
