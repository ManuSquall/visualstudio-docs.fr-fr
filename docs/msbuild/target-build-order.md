---
title: Ordre de génération des cibles | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- msbuild, build order
ms.assetid: f4a26339-9f9a-497a-9aa6-0797183d450d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f5c54fd6406350f5d0ad9620f10eef4fb9a546b4
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2018
---
# <a name="target-build-order"></a>Ordre de génération des cibles
Les cibles doivent être classées si l’entrée d’une cible dépend de la sortie d’une autre. Vous pouvez utiliser les attributs suivants pour spécifier l’ordre d’exécution des cibles :  
  
-   `InitialTargets`. L’attribut `Project` spécifie les cibles qui sont exécutées en premier, même si des cibles sont spécifiées sur la ligne de commande ou dans l’attribut `DefaultTargets`.  
  
-   `DefaultTargets`. Cet attribut `Project` spécifie les cibles qui sont exécutées si aucune cible n’est spécifiée explicitement sur la ligne de commande.  
  
-   `DependsOnTargets`. Cet attribut `Target` spécifie les cibles qui doivent s’exécuter avant que cette cible puisse s’exécuter.  
  
-   Voir `BeforeTargets` et `AfterTargets`. Ces attributs `Target` indiquent que cette cible doit s’exécuter avant ou après les cibles spécifiées (MSBuild 4.0).  
  
 Une cible n’est jamais exécutée deux fois pendant une génération, même si une cible suivante de la génération en dépend. Une fois qu’une cible a été exécutée, sa contribution à la génération est terminée.  
  
 Les cibles peuvent posséder un attribut `Condition`. Si la condition spécifiée a la valeur `false`, la cible n’est pas exécutée et n’a aucun effet sur la génération. Pour plus d’informations sur les conditions, consultez l’article [Conditions (Conditions MSBuild)](../msbuild/msbuild-conditions.md).  
  
## <a name="initial-targets"></a>Cibles initiales  
 L’attribut `InitialTargets` de l’élément [Project](../msbuild/project-element-msbuild.md) spécifie les cibles qui sont exécutées en premier, même si des cibles sont spécifiées sur la ligne de commande ou dans l’attribut `DefaultTargets`. En règle générale, les cibles initiales sont utilisées pour la vérification des erreurs.  
  
 La valeur de l’attribut `InitialTargets` peut être une liste ordonnée de cibles séparées par des points-virgules. Dans l’exemple suivant, la cible `Warm` est exécutée avant la cible `Eject`.  
  
```xml  
<Project InitialTargets="Warm;Eject" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
```  
  
 Les projets importés peuvent posséder leurs propres attributs `InitialTargets`. Toutes les cibles initiales sont agrégées et exécutées dans l’ordre.  
  
 Pour plus d’informations, consultez l’article [Comment : spécifier la cible à générer en premier](../msbuild/how-to-specify-which-target-to-build-first.md).  
  
## <a name="default-targets"></a>Cibles par défaut  
 L’attribut `DefaultTargets` de l’élément [Project](../msbuild/project-element-msbuild.md) spécifie la ou les cibles qui sont générées si aucune cible n’est spécifiée explicitement sur une ligne de commande.  
  
 La valeur de l’attribut `DefaultTargets` peut être une liste ordonnée de cibles par défaut séparées par des points-virgules. Dans l’exemple suivant, la cible `Clean` est exécutée avant la cible `Build`.  
  
```xml  
<Project DefaultTargets="Clean;Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
```  
  
 Vous pouvez remplacer les cibles par défaut en utilisant le commutateur **/target** sur la ligne de commande. Dans l’exemple suivant, la cible `Build` est exécutée avant la cible `Report`. Si vous spécifiez des cibles de cette manière, les cibles par défaut sont ignorées.  
  
 `msbuild /target:Build;Report`  
  
 Si des cibles initiales et des cibles par défaut sont spécifiées et si aucune cible de ligne de commande n’est indiquée, MSBuild exécute d’abord les cibles initiales, puis les cibles par défaut.  
  
 Les projets importés peuvent posséder leurs propres attributs `DefaultTargets`. Le premier attribut `DefaultTargets` rencontré détermine les cibles par défaut qui s’exécuteront.  
  
 Pour plus d’informations, consultez l’article [Comment : spécifier la cible à générer en premier](../msbuild/how-to-specify-which-target-to-build-first.md).  
  
## <a name="first-target"></a>Première cible  
 En l’absence de cibles initiales, cibles par défaut ou cibles de ligne de commande, MSBuild exécute la première cible qu’il rencontre dans le fichier projet ou dans les fichiers projet importés.  
  
## <a name="target-dependencies"></a>Dépendances de cible  
 Les cibles peuvent décrire les relations de dépendance existant les unes avec les autres. L’attribut `DependsOnTargets` indique qu’une cible dépend d’autres cibles. Par exemple :  
  
```xml  
<Target Name="Serve" DependsOnTargets="Chop;Cook" />  
```  
  
 indique à MSBuild que la cible `Serve` dépend des cibles `Chop` et `Cook`. MSBuild exécute la cible `Chop`, puis la cible `Cook`, avant la cible `Serve`.  
  
## <a name="beforetargets-and-after-targets"></a>BeforeTargets et AfterTargets  
 Dans MSBuild 4.0, vous pouvez spécifier l’ordre des cibles à l’aide des attributs `BeforeTargets` et `AfterTargets`.  
  
 Examinez le script ci-dessous.  
  
```xml  
<Project DefaultTargets="Compile;Link" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="Compile">  
        <Message Text="Compiling" />  
    </Target>  
    <Target Name="Link">  
        <Message Text="Linking" />  
    </Target>  
</Project>  
```  
  
 Pour créer une cible intermédiaire `Optimize` s’exécutant après la cible `Compile`, mais avant la cible `Link`, ajoutez la cible suivante n’importe où dans l’élément `Project`.  
  
```xml  
<Target Name="Optimize"   
    AfterTargets="Compile" BeforeTargets="Link">  
    <Message Text="Optimizing" />  
</Target>  
```  
  
## <a name="determining-the-target-build-order"></a>Détermination de l’ordre de génération des cibles  
 MSBuild détermine l’ordre de génération des cibles comme suit :  
  
1.  Les cibles `InitialTargets` sont exécutées.  
  
2.  Les cibles spécifiées sur la ligne de commande par le commutateur **/target** sont exécutées. Si vous n’indiquez aucune cible sur la ligne de commande, les cibles `DefaultTargets` sont alors exécutées. En l’absence de ces cibles, la première cible rencontrée est exécutée.  
  
3.  L’attribut `Condition` de la cible est évalué. Si l’attribut `Condition` est indiqué et défini sur la valeur `false`, la cible n’est pas exécutée et n’a aucun effet sur la génération.

    Les cibles qui listent la cible conditionnelle dans `BeforeTargets` ou `AfterTargets` s’exécutent toujours dans l’ordre indiqué
  
4.  Avant l’exécution d’une cible, ses cibles `DependsOnTargets` sont exécutées.  
  
5.  Avant l’exécution d’une cible, toute cible qui la répertorie dans un attribut `BeforeTargets` est exécutée.  
  
6.  Avant l’exécution d’une cible, ses attributs `Inputs` et `Outputs` sont comparés. Si MSBuild détermine que des fichiers de sortie sont obsolètes en ce qui concerne le ou les fichiers d’entrée correspondants, MSBuild exécute la cible. Sinon, MSBuild ignore la cible.  
  
7.  Une fois qu’une cible est exécutée ou ignorée, toute cible qui la répertorie dans un attribut `AfterTargets` est exécutée.  
  
## <a name="see-also"></a>Voir aussi  
 [Targets (Cibles MSBuild)](../msbuild/msbuild-targets.md)