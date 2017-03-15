---
title: "Incremental Builds | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "msbuild, incremental builds"
ms.assetid: 325e28c7-4838-4e3f-b672-4586adc7500c
caps.latest.revision: 8
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 8
---
# Incremental Builds
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Les builds incrémentielles sont des builds optimisées afin que les cibles possédant des fichiers de sortie à jour par rapport à leurs fichiers d'entrée correspondants ne soient pas exécutées.  Un élément cible peut avoir à la fois un attribut `Inputs`, indiquant les éléments que la cible attend comme entrée, et un attribut `Outputs`, indiquant les éléments produits comme sortie.  MSBuild tente de rechercher un mappage 1 à 1 entre les valeurs de ces attributs.  Si un mappage 1 à 1 existe, MSBuild compare l'horodatage de chaque élément d'entrée à l'horodatage de son élément de sortie correspondant.  Les fichiers de sortie qui n'ont pas de mappage 1 à 1 sont comparés à tous les fichiers d'entrée.  Un élément est considéré comme à jour si son fichier de sortie a la même ancienneté ou est plus récent que son ou ses fichier\(s\) d'entrée.  
  
 Si tous les éléments de sortie sont à jour, MSBuild ignore la cible.  Cette *build incrémentielle* de la cible peut considérablement améliorer la vitesse de génération.  Si certains fichiers seulement sont à jour, MSBuild exécute la cible mais ignore les éléments à jour ; de cette façon, il met tous les éléments à jour.  Il s'agit d'une *build incrémentielle partielle*.  
  
 En général, les mappages 1 à 1 sont réalisés par des transformations d'élément.  Pour plus d'informations, consultez [Transforms](../msbuild/msbuild-transforms.md).  
  
 Prenons comme exemple la cible suivante :  
  
```  
<Target Name="Backup" Inputs="@(Compile)"   
    Outputs="@(Compile->'$(BackupFolder)%(Identity).bak')">  
    <Copy SourceFiles="@(Compile)" DestinationFiles=  
        "@(Compile->'$(BackupFolder)%(Identity).bak')" />  
</Target>  
```  
  
 Le jeu de fichiers représenté par le type d'élément `Compile` est copié vers un répertoire de sauvegarde.  Les fichiers de sauvegarde portent l'extension de nom de fichier .bak.  Si les fichiers représentés par le type d'élément `Compile` ou les fichiers de sauvegarde correspondants ne sont pas supprimés ou modifiés après l'exécution de la cible de sauvegarde, celle\-ci est ignorée dans les builds suivantes.  
  
## Inférence de sortie  
 MSBuild compare les attributs `Inputs` et `Outputs` d'une cible pour déterminer si la cible doit s'exécuter.  Idéalement, le jeu de fichiers qui existe après l'exécution d'une build incrémentielle doit rester le même, que les cibles associées aient été ou non exécutées.  Étant donné que les propriétés et les éléments créés ou modifiés par les tâches peuvent affecter la build, MSBuild doit déduire leurs valeurs, même si la cible associée est ignorée.  Il s'agit de *inférence de sortie*.  
  
 Il existe trois cas :  
  
-   La cible a un attribut `Condition` qui a la valeur `false`.  Dans ce cas, la cible n'est pas exécutée et n'a aucun effet sur la build.  
  
-   La cible a des sorties obsolètes et est exécutée pour les mettre à jour.  
  
-   La cible n'a pas de sorties obsolètes et est ignorée.  MSBuild évalue la cible et apporte des modifications aux éléments et aux propriétés comme si la cible avait été exécutée.  
  
 Pour prendre en charge la compilation incrémentielle, les tâches doivent vérifier que la valeur d'attribut `TaskParameter` de tout élément `Output` est égale à un paramètre d'entrée de tâche.  Voici quelques exemples :  
  
```  
<CreateProperty Value="123">  
    <Output PropertyName="Easy" TaskParameter="Value" />  
</CreateProperty>  
```  
  
 Cela crée la propriété Easy avec la valeur « 123 », que la cible ait été exécutée ou ignorée.  
  
```  
<CreateItem Include="a.cs;b.cs">  
    <Output ItemName="Simple" TaskParameter="Include" />  
</CreateItem>  
```  
  
 Cela crée le type d'élément Simple, avec deux éléments, « a.cs » et « b.cs », que la cible ait été exécutée ou ignorée.  
  
 A partir de MSBuild 3.5, l'inférence de sortie est exécutée automatiquement sur les groupes d'éléments et de propriétés dans une cible.  Les tâches `CreateItem` ne sont pas requises dans une cible et doivent être évitées.  De plus, les tâches `CreateProperty` doivent être utilisées uniquement dans une cible pour déterminer si une cible a été exécutée.  
  
## Déterminer si une cible a été exécutée  
 En raison de l'inférence de sortie, vous devez ajouter une tâche `CreateProperty` à une cible pour examiner les propriétés et les éléments afin de pouvoir déterminer si la cible a été exécutée.  Ajoutez la tâche `CreateProperty` à la cible et donnez\-lui un élément `Output` dont `TaskParameter` correspond à « ValueSetByTask ».  
  
```  
<CreateProperty Value="true">  
    <Output TaskParameter="ValueSetByTask" PropertyName="CompileRan" />  
</CreateProperty>  
```  
  
 Cela crée la propriété CompileRan et lui affecte la valeur `true`, mais uniquement si la cible est exécutée.  Si la cible est ignorée, CompileRan n'est pas créée.  
  
## Voir aussi  
 [Targets](../msbuild/msbuild-targets.md)