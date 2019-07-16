---
title: 'Procédure : Spécifier la cible à générer en premier | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- DefaultTargets attribute [MSBuild]
- MSBuild, specifying the defalut target
- MSBuild, DefaultTargets attribute
ms.assetid: a580ba5b-2919-42d2-ae38-1af991e0205a
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7d7d47746aed2e663eb1fa25e3bb9ca2c6bed2c9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "68178338"
---
# <a name="how-to-specify-which-target-to-build-first"></a>Procédure : Spécifier la cible à générer en premier
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un fichier projet peut contenir un ou plusieurs éléments `Target` qui définissent le mode de génération du projet. Le moteur [!INCLUDE[vstecmsbuildengine](../includes/vstecmsbuildengine-md.md)] ([!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]) génère le premier projet trouvé, et toutes les dépendances, à moins que le fichier projet ne contienne un attribut `DefaultTargets`, un attribut `InitialTargets` ou qu’une cible ne soit spécifiée sur la ligne de commande à l’aide du commutateur **/target**.  
  
## <a name="using-the-initialtargets-attribute"></a>Utilisation de l’attribut InitialTargets  
 L’attribut `InitialTargets` de l’élément `Project` spécifie une cible qui est exécutée en premier, même si des cibles sont spécifiées sur la ligne de commande ou dans l’attribut `DefaultTargets`.  
  
#### <a name="to-specify-one-initial-target"></a>Pour spécifier une cible initiale  
  
- Spécifiez la cible par défaut dans l’attribut `InitialTargets` de l’élément `Project`. Par exemple :  
  
   `<Project InitialTargets="Clean">`  
  
  Vous pouvez spécifier plusieurs cibles initiales dans l’attribut `InitialTargets` en classant les cibles dans l’ordre et en utilisant un point-virgule pour séparer chaque cible. Les cibles de la liste seront exécutées séquentiellement.  
  
#### <a name="to-specify-more-than-one-initial-target"></a>Pour spécifier plusieurs cibles initiales  
  
- Répertoriez les cibles initiales, séparées par des points-virgules, dans l’attribut `InitialTargets` de l’élément `Project`. Par exemple, pour exécuter la cible `Clean`, puis la cible `Compile`, tapez :  
  
     `<Project InitialTargets="Clean;Compile">`  
  
## <a name="using-the-defaulttargets-attribute"></a>Utilisation de l’attribut DefaultTargets  
 L’attribut `DefaultTargets` de l’élément `Project` spécifie la ou les cibles qui sont générées si une cible n’est pas spécifiée explicitement sur la ligne de commande. Si des cibles sont spécifiées dans les deux attributs `InitialTargets` et `DefaultTargets` et qu’aucune cible n’est spécifiée sur la ligne de commande, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] exécute les cibles spécifiées dans l’attribut `InitialTargets` suivies par les cibles spécifiées dans l’attribut `DefaultTargets`.  
  
#### <a name="to-specify-one-default-target"></a>Pour spécifier une cible par défaut  
  
- Spécifiez la cible par défaut dans l’attribut `DefaultTargets` de l’élément `Project`. Par exemple :  
  
   `<Project DefaultTargets="Compile">`  
  
  Vous pouvez spécifier plusieurs cibles par défaut dans l’attribut `DefaultTargets` en classant les cibles dans l’ordre et en utilisant un point-virgule pour séparer chaque cible. Les cibles de la liste seront exécutées séquentiellement.  
  
#### <a name="to-specify-more-than-one-default-target"></a>Pour spécifier plusieurs cibles par défaut  
  
- Répertoriez les cibles par défaut, séparées par des points-virgules, dans l’attribut `DefaultTargets` de l’élément `Project`. Par exemple, pour exécuter la cible `Clean`, puis la cible `Compile`, tapez :  
  
     `<Project DefaultTargets="Clean;Compile">`  
  
## <a name="using-the-target-switch"></a>Utilisation du commutateur /target  
 Si aucune cible par défaut n’est définie dans le fichier projet ou si vous ne voulez pas utiliser cette cible par défaut, vous pouvez utiliser le commutateur de ligne de commande **/target** pour spécifier une autre cible. La ou les cibles spécifiées avec le commutateur **/target** sont exécutées à la place des cibles spécifiées par l’attribut `DefaultTargets`. Les cibles spécifiées dans l’attribut `InitialTargets` sont toujours exécutées en premier.  
  
#### <a name="to-use-a-target-other-than-the-default-target-first"></a>Pour utiliser en premier une cible autre que la cible par défaut  
  
- Spécifiez la cible comme première cible à l’aide du commutateur de ligne de commande **/target**. Par exemple :  
  
     `msbuild file.proj /target:Clean`  
  
#### <a name="to-use-several-targets-other-than-the-default-targets-first"></a>Pour utiliser en premier plusieurs cibles autres que les cibles par défaut  
  
- Répertoriez les cibles, séparées par des points-virgules ou des virgules, à l’aide du commutateur de ligne de commande **/target**. Par exemple :  
  
     `msbuild <file name>.proj /t:Clean;Compile`  
  
## <a name="see-also"></a>Voir aussi
  [MSBuild](msbuild.md)  
 [Targets (Cibles MSBuild)](../msbuild/msbuild-targets.md)   
 [Guide pratique pour nettoyer une build](../msbuild/how-to-clean-a-build.md)
