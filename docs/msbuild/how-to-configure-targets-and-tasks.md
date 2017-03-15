---
title: "How to: Configure Targets and Tasks | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 92814100-392a-471d-96fd-e26f637d6cc2
caps.latest.revision: 5
caps.handback.revision: 5
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# How to: Configure Targets and Tasks
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Les tâches sélectionnées MSBuild peuvent être configurées pour s'exécuter dans l'environnement qu'elles ciblent le, indépendamment de l'environnement de l'ordinateur de développement.  Par exemple, lorsque vous utilisez un ordinateur 64 bits pour générer une application qui cible une architecture 32 bits, les tâches sélectionnées sont exécutées dans un processus 32 bits.  
  
> [!NOTE]
>  Si une tâche de génération est écrite dans un langage.NET, tel que Visual c\# ou Visual Basic, et n'utilise pas les ressources natives ou des outils, elle s'exécutera dans n'importe quel contexte cible sans adaptation.  
  
## Attributs d'UsingTask et paramètres de tâche  
 Les attributs suivants d' `UsingTask` affectent toutes les opérations d'une tâche dans un processus de génération particulier :  
  
-   L'attribut d' `Runtime` , s'il est présent, définit la version \(CLR\) du common langage runtime, et peut prendre de l'une de ces valeurs : `CLR2`, `CLR4`, `CurrentRuntime`, ou `*` \(tout moment de l'exécution\).  
  
-   L'attribut d' `Architecture` , s'il est présent, définit la plateforme et le nombre de bits, et peut prendre de l'une de ces valeurs : `x86`, `x64`, `CurrentArchitecture`, ou `*` \(toute architecture\).  
  
-   L'attribut d' `TaskFactory` , le cas échéant, définit la fabrique de tâches qui crée et exécute l'instance de tâche, et prend uniquement la valeur `TaskHostFactory`.  Pour plus d'informations, consultez la section des fabriques de tâche plus loin dans ce document.  
  
```  
<UsingTask TaskName="SimpleTask"   
   Runtime="CLR2"  
   Architecture="x86"  
   AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v3.5.dll" />  
```  
  
 Vous pouvez également utiliser les paramètres d' `MSBuildRuntime` et d' `MSBuildArchitecture` pour définir le contexte cible d'une tâche individuelle.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
   <Target Name="MyTarget">  
      <SimpleTask MSBuildRuntime="CLR2" MSBuildArchitecture= "x86"/>  
   </Target>  
</Project>  
```  
  
 Avant que MSBuild exécute une tâche, il trouve une correspondance `UsingTask` qui a le même contexte cible.  Les paramètres spécifiés dans `UsingTask` mais pas dans la tâche correspondante sont considérés comme être mis en correspondance.  Les paramètres ayant spécifié dans la tâche mais pas dans `UsingTask` correspondant sont également considérés comme être mis en correspondance.  Si les valeurs de paramètre ne sont pas spécifiées dans `UsingTask` ou la tâche, les valeurs ont comme valeur par défaut à `*` \(tout paramètre\).  
  
> [!WARNING]
>  Si plusieurs `UsingTask` existe et ont toutes `TaskName`correspondant, `Runtime`, les attributs et d' `Architecture` , derniers à évaluer remplacent les autres.  
  
 Si les paramètres sont définis sur la tâche, MSBuild tente de rechercher `UsingTask` correspondant à ces paramètres ou, au moins, ne sont pas en conflit avec eux.  Plusieurs `UsingTask` peut spécifier le contexte cible de la même tâche.  Par exemple, une tâche qui contient différents fichiers exécutables pour différents environnements cible peut ressembler à celui\-ci :  
  
```  
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
  
## Fabriques de tâche  
 Avant d'exécuter une tâche, MSBuild vérifie s'il est indiqué pour s'exécuter dans le contexte actuel de logiciel.  Si la tâche est pas indiqué, MSBuild la passe à l'AssemblyTaskFactory, qui l'exécute dans le processus actuel ; sinon, MSBuild passe la tâche au TaskHostFactory, qui exécute la tâche dans un processus qui correspond au contexte cible.  Même si le contexte actuel et le contexte cible correspondent, vous pouvez forcer une tâche à exécuter hors processus \(pour l'isolement, la sécurité, ou d'autres raisons\) en définissant `TaskFactory` à `TaskHostFactory`.  
  
```  
<UsingTask TaskName="MisbehavingTask"   
   TaskFactory="TaskHostFactory"  
   AssemblyFile="$(MSBuildToolsPath)\MyTasks.dll">  
</UsingTask>  
```  
  
## Paramètres fantômes de tâche  
 Comme tous les autres paramètres de tâche, `MSBuildRuntime` et `MSBuildArchitecture` peuvent être définis les propriétés de génération.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
   <PropertyGroup>  
      <FrameworkVersion>3.0</FrameworkVersion>  
   </PropertyGroup>  
   <Target Name="MyTarget">  
      <SimpleTask MSBuildRuntime="$(FrameworkVerion)" MSBuildArchitecture= "x86"/>  
   </Target>  
</Project>  
```  
  
 Contrairement à d'autres paramètres de tâche, `MSBuildRuntime` et `MSBuildArchitecture` ne sont pas évidents à la tâche.  Pour écrire une tâche qui reconnaît le contexte dans lequel elle s'exécute, vous devez tester le contexte en appelant le.NET Framework, ou utiliser les propriétés de génération pour passer des informations de contexte via d'autres paramètres de tâche.  
  
> [!NOTE]
>  Les attributs d'`UsingTask` peuvent être définis des propriétés d'ensemble d'outils et d'environnement.  
  
 Les paramètres d' `MSBuildRuntime` et d' `MSBuildArchitecture` fournissent la méthode la plus flexible de définir le contexte de la cible, mais également le plus limité dans la portée.  D'une part, car ils sont définis sur l'instance de tâche et ne sont pas évalués jusqu'à ce que la tâche est sur le point d'exécution, ils peuvent dériver leur valeur de la portée complète des propriétés disponibles pour l'évaluation\-fois et de la génération.  En revanche, ces paramètres s'appliquent uniquement à une instance particulière d'une tâche dans une cible particulière.  
  
> [!NOTE]
>  Les paramètres de tâche sont évalués dans le contexte du nœud parent, pas dans le contexte de l'hôte de tâche. Les variables d'environnement qui sont runtime ou le dépendant de l'architecture \(tel que l'emplacement de fichiers programme\) est évalué à la valeur qui correspond au nœud parent.  Toutefois, si une même variable d'environnement est lue directement par la tâche, elle sera correctement évaluée dans le contexte de l'hôte de tâche.  
  
## Voir aussi  
 [Configuring Targets and Tasks](../msbuild/configuring-targets-and-tasks.md)