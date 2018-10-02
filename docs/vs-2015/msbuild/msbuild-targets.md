---
title: Cibles de MSBuild | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MSBuild, targets
ms.assetid: 8060b4d2-e4a9-48cf-a437-852649ceb417
caps.latest.revision: 29
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 68a596eaf744649047ae912e4b9aac00922e2360
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47494114"
---
# <a name="msbuild-targets"></a>Cibles de MSBuild
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [cibles MSBuild](https://docs.microsoft.com/visualstudio/msbuild/msbuild-targets).  
  
  
Les cibles regroupent les tâches dans un ordre particulier et permet au processus de génération d’être factorisé en unités plus petites. Par exemple, une cible peut supprimer tous les fichiers du répertoire de sortie pour préparer la génération, pendant qu’une autre compile les entrées pour le projet et les place dans le répertoire vide. Pour plus d’informations sur les tâches, consultez [Tâches MSBuild](../msbuild/msbuild-tasks.md).  
  
## <a name="declaring-targets-in-the-project-file"></a>Déclaration des cibles dans le fichier projet  
 Les cibles sont déclarées dans le fichier projet avec l’élément [Target](../msbuild/target-element-msbuild.md). Par exemple, le code XML suivant crée une cible nommée Construct, qui appelle ensuite la tâche Csc avec le type d’élément Compile.  
  
```  
<Target Name="Construct">  
    <Csc Sources="@(Compile)" />  
</Target>  
```  
  
 Tout comme les propriétés MSBuild, les cibles peuvent être redéfinies. Par exemple :  
  
```  
<Target Name="AfterBuild" >  
    <Message Text="First occurrence" />  
</Target>  
<Target Name="AfterBuild" >  
    <Message Text="Second occurrence" />  
</Target>  
```  
  
 Si AfterBuild s’exécute, il affiche uniquement « Second occurrence ».  
  
## <a name="target-build-order"></a>Ordre de génération des cibles  
 Les cibles doivent être classées si l’entrée d’une cible dépend de la sortie d’une autre. Il existe plusieurs façons de spécifier l’ordre d’exécution des cibles.  
  
-   Cibles initiales  
  
-   Cibles par défaut  
  
-   Première cible  
  
-   Dépendances de cible  
  
-   `BeforeTargets` et `AfterTargets` (MSBuild 4.0)  
  
 Une cible n’est jamais exécutée deux fois au cours d’une même génération, même si une cible suivante de la génération en dépend. Une fois qu’une cible est exécutée, sa contribution à la génération est terminée.  
  
 Pour plus d’informations sur l’ordre de génération des cibles, consultez [Ordre de génération des cibles](../msbuild/target-build-order.md).  
  
## <a name="target-batching"></a>Traitement par lot des cibles  
 Un élément cible peut avoir un attribut `Outputs` qui spécifie des métadonnées au format suivant : %(métadonnées). Dans ce cas, MSBuild exécute la cible une fois pour chaque valeur unique de métadonnées, en regroupant par lot les éléments qui ont cette valeur de métadonnées. Par exemple :  
  
```  
<ItemGroup>  
    <Reference Include="System.Core">  
      <RequiredTargetFramework>3.5</RequiredTargetFramework>  
    </Reference>  
    <Reference Include="System.Xml.Linq">  
      <RequiredTargetFramework>3.5</RequiredTargetFramework>  
    </Reference>  
    <Reference Include="Microsoft.CSharp">  
      <RequiredTargetFramework>4.0</RequiredTargetFramework>  
    </Reference>  
</ItemGroup>  
<Target Name="AfterBuild"  
    Outputs="%(Reference.RequiredTargetFramework)">  
    <Message Text="Reference:  
      @(Reference->'%(RequiredTargetFramework)')" />  
</Target>  
```  
  
 regroupe les éléments Reference selon leurs métadonnées RequiredTargetFramework. La sortie de la cible ressemble à ceci :  
  
```  
Reference: 3.5;3.5  
Reference: 4.0  
```  
  
 Le traitement par lot des cibles est rarement utilisé dans les scénarios de génération réels. Le traitement par lot des tâches, en revanche, est plus courant. Pour plus d’informations, consultez l’article [Batching (Traitement par lot MSBuild)](../msbuild/msbuild-batching.md).  
  
## <a name="incremental-builds"></a>Builds incrémentielles  
 Les builds incrémentielles sont des builds optimisées qui permettent de ne pas exécuter les cibles dont les fichiers de sortie sont à jour par rapport à leurs fichiers d’entrée correspondants. Un élément cible peut avoir à la fois un attribut `Inputs`, qui indique les éléments que la cible attend comme entrée, et un attribut `Outputs` qui indique les éléments qu’il produit comme sortie.  
  
 Si tous les éléments de sortie sont à jour, MSBuild ignore la cible, ce qui accélère considérablement le processus de génération. C’est ce qu’on appelle une build incrémentielle de la cible. Si seuls certains fichiers sont à jour, MSBuild exécute la cible, sans exécuter ces fichiers. C’est ce qu’on appelle une build incrémentielle partielle de la cible. Pour plus d’informations, consultez l’article [Incremental Builds (Générations incrémentielles)](../msbuild/incremental-builds.md) .  
  
## <a name="see-also"></a>Voir aussi  
 [Concepts MSBuild](../msbuild/msbuild-concepts.md)   
 [Guide pratique pour utiliser la même cible dans plusieurs fichiers projet](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md)



