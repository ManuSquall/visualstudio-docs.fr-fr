---
title: Guide pratique pour configurer les cibles et les tâches | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
ms.assetid: 92814100-392a-471d-96fd-e26f637d6cc2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7a09f2ec1af511cb789f2101e2df0a675dd065e8
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2018
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
```  
  
 Contrairement à d’autres paramètres de tâche, `MSBuildRuntime` et `MSBuildArchitecture` ne sont pas visibles pour la tâche elle-même.  Pour écrire une tâche qui tient compte du contexte dans lequel elle s’exécute, vous devez tester le contexte en appelant le .NET Framework ou utiliser les propriétés de la build pour passer les informations de contexte avec d’autres paramètres de la tâche.  
  
> [!NOTE]
>  Les attributs `UsingTask` peuvent être définis à partir des propriétés d’ensemble d’outils et d’environnement.  
  
 Les paramètres `MSBuildRuntime` et `MSBuildArchitecture` représentent le moyen le plus simple de définir le contexte cible, mais également le plus limité en portée.  D’une part, comme ils sont définis sur l’instance de tâche et ne sont pas évalués tant que la tâche n’est pas sur le point d’être exécutée, ils peuvent dériver leur valeur à partir de la portée complète des propriétés disponibles au moment de l’évaluation et au moment de la génération.  D’autre part, ces paramètres s’appliquent uniquement à une instance particulière d’une tâche dans une cible particulière.  
  
> [!NOTE]
>  Les paramètres de tâche sont évalués dans le contexte du nœud parent et non dans le contexte de l’hôte de tâche. Les variables d’environnement qui dépendent du runtime ou de l’architecture (par exemple, l’emplacement des fichiers programme) correspond à la valeur associée au nœud parent.  Toutefois, si la même variable d’environnement est lue directement par la tâche, elle est correctement évaluée dans le contexte de l’hôte de tâche.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des cibles et des tâches](../msbuild/configuring-targets-and-tasks.md)
