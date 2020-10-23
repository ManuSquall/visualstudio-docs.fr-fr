---
title: 'Comment : spécifier la cible à générer en premier | Microsoft Docs'
description: En savoir plus sur la façon de spécifier les cibles initiales ou les cibles par défaut à générer en premier dans les fichiers projet MSBuild.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- DefaultTargets attribute [MSBuild]
- MSBuild, specifying the defalut target
- MSBuild, DefaultTargets attribute
ms.assetid: a580ba5b-2919-42d2-ae38-1af991e0205a
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a9ce8f17e70344445f95e8b4742838e40a92fe88
ms.sourcegitcommit: c4927ef8fe239005d7feff6c5a7707c594a7a05c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2020
ms.locfileid: "92436182"
---
# <a name="how-to-specify-which-target-to-build-first"></a>Guide pratique pour spécifier la cible à générer en premier

Un fichier projet peut contenir un ou plusieurs éléments `Target` qui définissent le mode de génération du projet. Le moteur de Microsoft Build Engine (MSBuild) crée la première cible qu’il trouve, et toutes les dépendances, sauf si le fichier projet contient un `DefaultTargets` attribut, un `InitialTargets` attribut ou une cible est spécifié sur la ligne de commande à l’aide du commutateur **-target** .
## <a name="use-the-initialtargets-attribute"></a>Utiliser l’attribut InitialTargets

L’attribut `InitialTargets` de l’élément `Project` spécifie une cible qui est exécutée en premier, même si des cibles sont spécifiées sur la ligne de commande ou dans l’attribut `DefaultTargets`.

#### <a name="to-specify-one-initial-target"></a>Pour spécifier une cible initiale

- Spécifiez la cible par défaut dans l’attribut `InitialTargets` de l’élément `Project`. Par exemple :

   `<Project InitialTargets="Clean">`

  Vous pouvez spécifier plusieurs cibles initiales dans l’attribut `InitialTargets` en classant les cibles dans l’ordre et en utilisant un point-virgule pour séparer chaque cible. Les cibles de la liste seront exécutées séquentiellement.

#### <a name="to-specify-more-than-one-initial-target"></a>Pour spécifier plusieurs cibles initiales

- Répertoriez les cibles initiales, séparées par des points-virgules, dans l’attribut `InitialTargets` de l’élément `Project`. Par exemple, pour exécuter la cible `Clean`, puis la cible `Compile`, tapez :

     `<Project InitialTargets="Clean;Compile">`

## <a name="use-the-defaulttargets-attribute"></a>Utiliser l’attribut DefaultTargets

 L’attribut `DefaultTargets` de l’élément `Project` spécifie la ou les cibles qui sont générées si une cible n’est pas spécifiée explicitement sur la ligne de commande. Si des cibles sont spécifiées à la fois dans les `InitialTargets` `DefaultTargets` attributs et et si aucune cible n’est spécifiée sur la ligne de commande, MSBuild exécute les cibles spécifiées dans l' `InitialTargets` attribut, suivies des cibles spécifiées dans l' `DefaultTargets` attribut.

#### <a name="to-specify-one-default-target"></a>Pour spécifier une cible par défaut

- Spécifiez la cible par défaut dans l’attribut `DefaultTargets` de l’élément `Project`. Par exemple :

   `<Project DefaultTargets="Compile">`

  Vous pouvez spécifier plusieurs cibles par défaut dans l’attribut `DefaultTargets` en classant les cibles dans l’ordre et en utilisant un point-virgule pour séparer chaque cible. Les cibles de la liste seront exécutées séquentiellement.

#### <a name="to-specify-more-than-one-default-target"></a>Pour spécifier plusieurs cibles par défaut

- Répertoriez les cibles par défaut, séparées par des points-virgules, dans l’attribut `DefaultTargets` de l’élément `Project`. Par exemple, pour exécuter la cible `Clean`, puis la cible `Compile`, tapez :

     `<Project DefaultTargets="Clean;Compile">`

## <a name="use-the--target-switch"></a>Utiliser le commutateur -target

 Si une cible par défaut n’est pas définie dans le fichier projet, ou si vous ne souhaitez pas utiliser cette cible par défaut, vous pouvez utiliser le commutateur de ligne de commande **-target** pour spécifier une autre cible. La ou les cibles spécifiées avec le commutateur **-target** sont exécutées à la place des cibles spécifiées par l' `DefaultTargets` attribut. Les cibles spécifiées dans l’attribut `InitialTargets` sont toujours exécutées en premier.

#### <a name="to-use-a-target-other-than-the-default-target-first"></a>Pour utiliser en premier une cible autre que la cible par défaut

- Spécifiez la cible comme première cible à l’aide du commutateur **de ligne de commande-Target** . Par exemple :

     `msbuild file.proj -target:Clean`

#### <a name="to-use-several-targets-other-than-the-default-targets-first"></a>Pour utiliser en premier plusieurs cibles autres que les cibles par défaut

- Répertoriez les cibles, séparées par des points-virgules ou des virgules, à l’aide du commutateur **de ligne de commande-Target** . Par exemple :

     `msbuild <file name>.proj -t:Clean;Compile`

## <a name="see-also"></a>Voir aussi

- [MSBuild](../msbuild/msbuild.md)
- [Cibles](../msbuild/msbuild-targets.md)
- [Comment : nettoyer une build](../msbuild/how-to-clean-a-build.md)
