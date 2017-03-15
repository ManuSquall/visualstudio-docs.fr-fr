---
title: "Ordre de g&#233;n&#233;ration des cibles | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "msbuild, ordre de génération"
ms.assetid: f4a26339-9f9a-497a-9aa6-0797183d450d
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 18
---
# Ordre de g&#233;n&#233;ration des cibles
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Les cibles doivent être classées si l'entrée d'une cible dépend de la sortie d'une autre cible.  Vous pouvez utiliser ces attributs pour spécifier l'ordre dans lequel les cibles sont exécutées :  
  
-   `InitialTargets`.  Cet attribut d' `Project` spécifie les cibles qui s'exécutent en premier lieu, même si les cibles sont spécifiées sur la ligne de commande ou dans l'attribut d' `DefaultTargets` .  
  
-   `DefaultTargets`.  Cet atttribute d' `Project` spécifie que les cibles sont exécutées si une cible n'est pas spécifiée explicitement dans la ligne de commande.  
  
-   `DependsOnTargets`.  Cet attribut d' `Target` spécifie les cibles qui doivent s'exécuter pour que cette cible puisse s'exécuter.  
  
-   `BeforeTargets` et `AfterTargets`.  Ces attributs d' `Target` spécifient que cette cible doit s'exécuter avant ou après les cibles spécifiées \(MSBuild 4,0\).  
  
 Une cible n'est jamais exécutée deux fois pendant une build, même si une cible suivante dans la build dépend d'elle.  Une fois qu'une cible a été exécutée, sa contribution à la build est terminée.  
  
 Les cibles peuvent avoir un attribut `Condition`.  Si la condition spécifiée prend la `false`, la cible n'est pas exécutée et n'a aucun effet sur la build.  Pour plus d'informations sur les conditions, consultez [Conditions](../msbuild/msbuild-conditions.md).  
  
## Cibles initiales  
 L'attribut d' `InitialTargets` de l'élément d' [Projet](../msbuild/project-element-msbuild.md) spécifie les cibles qui s'exécutent en premier lieu, même si les cibles sont spécifiées sur la ligne de commande ou dans l'attribut d' `DefaultTargets` .  Les cibles initiales sont généralement utilisées pour la vérification des erreurs.  
  
 La valeur de l'attribut d' `InitialTargets` peut être point\-virgule\-délimité, liste triée de cibles.  L'exemple suivant spécifie que la cible d' `Warm` s'exécute, puis que la cible d' `Eject` s'exécute.  
  
```  
<Project InitialTargets="Warm;Eject" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
```  
  
 Les projets importés peuvent avoir leurs propres attributs `InitialTargets`.  Toutes les cibles initiales sont regroupées et exécutées dans l'ordre indiqué.  
  
 Pour plus d'informations, consultez [How to: Specify Which Target to Build First](../msbuild/how-to-specify-which-target-to-build-first.md).  
  
## Cibles par défaut  
 L'attribut d' `DefaultTargets` de l'élément d' [Projet](../msbuild/project-element-msbuild.md) spécifie qui ciblent le ou les cibles sont générées si une cible n'est pas spécifiée explicitement dans une ligne de commande.  
  
 La valeur de l'attribut d' `DefaultTargets` peut être point\-virgule\-délimité, liste triée de cibles par défaut.  L'exemple suivant spécifie que la cible d' `Clean` s'exécute, puis que la cible d' `Build` s'exécute.  
  
```  
<Project DefaultTargets="Clean;Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
```  
  
 Vous pouvez substituer les cibles par défaut à l'aide de le commutateur d' **\/target** sur la ligne de commande.  L'exemple suivant spécifie que la cible d' `Build` s'exécute, puis que la cible d' `Report` s'exécute.  Lorsque vous spécifiez des cibles de cette manière, les cibles par défaut sont ignorées.  
  
 `msbuild /target:Build;Report`  
  
 Si les cibles initiales et les cibles par défaut sont spécifiées, et si aucune cible de ligne de commande n'est spécifiée, MSBuild exécute les cibles initiales d'abord, puis exécute ensuite les cibles par défaut.  
  
 Les projets importés peuvent avoir leurs propres attributs `DefaultTargets`.  Le premier attribut `DefaultTargets` rencontré détermine les cibles par défaut qui s'exécuteront.  
  
 Pour plus d'informations, consultez [How to: Specify Which Target to Build First](../msbuild/how-to-specify-which-target-to-build-first.md).  
  
## Première cible  
 S'il n'y a pas de cible initiale, de cible par défaut ou de cible de ligne de commande, MSBuild exécute la première cible qu'il rencontre dans le fichier projet ou dans tout fichier projet importé.  
  
## Dépendances cible  
 Les cibles peuvent décrire des relations de dépendance entre elles.  L'attribut `DependsOnTargets` indique qu'une cible dépend d'autres cibles.  Par exemple :  
  
```  
<Target Name="Serve" DependsOnTargets="Chop;Cook" />  
```  
  
 indique à MSBuild que la cible d' `Serve` dépend de la cible d' `Chop` et la cible d' `Cook` .  MSBuild exécute la cible d' `Chop`, puis exécute la cible d' `Cook` avant d'exécuter la cible d' `Serve` .  
  
## Avant de cibles et après les cibles  
 Dans MSBuild 4.0, vous pouvez spécifier l'ordre des cibles à l'aide des attributs `BeforeTargets` et `AfterTargets`.  
  
 Prenons le script suivant :  
  
```  
<Project DefaultTargets="Compile;Link" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="Compile">  
        <Message Text="Compiling" />  
    </Target>  
    <Target Name="Link">  
        <Message Text="Linking" />  
    </Target>  
</Project>  
```  
  
 Pour créer `Optimize` cible intermédiaire qui s'exécute après la cible d' `Compile`, mais avant la cible d' `Link`, ajoutez la cible suivante n'importe où dans l'élément d' `Project` .  
  
```  
<Target Name="Optimize"   
    AfterTargets="Compile" BeforeTargets="Link">  
    <Message Text="Optimizing" />  
</Target>  
```  
  
## Détermination de l'ordre de génération des cibles  
 MSBuild détermine l'ordre de génération des cibles comme suit :  
  
1.  les cibles d'`InitialTargets` sont exécutées.  
  
2.  Les cibles spécifiées sur la ligne de commande par le commutateur **\/target** sont exécutées.  Si vous ne spécifiez aucune cible sur la ligne de commande, les cibles d' `DefaultTargets` sont exécutées.  Si aucune n'est présent, la première cible rencontrée est exécutée.  
  
3.  L'attribut `Condition` de la cible est évalué.  Si l'attribut d' `Condition` est présent et correspond à `false`, la cible n'est pas exécutée et n'a aucun effet supplémentaire sur la build.  
  
4.  Avant qu'une cible soit exécutée, ses cibles `DependsOnTargets` sont exécutées.  
  
5.  Avant qu'une cible soit exécutée, toute cible qui la répertorie dans un attribut `BeforeTargets` est exécutée.  
  
6.  Avant qu'une cible soit exécutée, ses attributs `Inputs` et `Outputs` sont comparés.  Si MSBuild détermine que tous les fichiers de sortie sont obsolètes par rapport à le fichier d'entrée correspondant ou des fichiers, puis MSBuild exécute la cible.  Sinon, MSBuild ignore la cible.  
  
7.  Une fois qu'une cible a été exécutée ou ignorée, toute cible qui la répertorie dans un attribut `AfterTargets` est exécutée.  
  
## Voir aussi  
 [Targets](../msbuild/msbuild-targets.md)