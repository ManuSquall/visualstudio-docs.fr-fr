---
title: "Porter, migrer et mettre à niveau des projets Visual Studio |Microsoft Docs"
ms.custom: 
ms.date: 11/16/2016
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Win8ExpressDesktopBlock
- w8trefactor
- VS.ReviewProjectAndSolutionChangesDialog.UpgradeRetarget
- ProjectCompatibilityDlgHelpTopic
- VS.ReviewProjectAndSolutionChangesDialog.Upgrade
helpviewer_keywords:
- conversion, projects
- asset compatibility
- projects, conversion
ms.assetid: bee759bd-6ff5-4c2e-913a-ea7d3c906c29
author: TerryGLee
ms.author: tglee
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: ae6564f10ca561853444698665779bd1014d4afd
ms.openlocfilehash: 2915a9ceec638471ac29599992a7ccdff17cefb4
ms.lasthandoff: 02/22/2017

---
# <a name="port-migrate-and-upgrade-visual-studio-projects"></a>Porter, migrer et mettre à niveau des projets Visual Studio
Au moment de passer à une version plus récente de Visual Studio, vous vous demanderez probablement si les solutions, projets, fichiers et autres ressources que vous avez créés dans les versions antérieures doivent être modifiés *avant* de les exécuter dans la version récente.

 Le fait est que la plupart des ressources les plus couramment utilisées se comportent de la même façon dans Visual Studio 2017 RC et dans Visual Studio 2015. Cela vaut aussi pour les versions antérieures, telles que Visual Studio 2013 et Visual Studio 2012.

 Par exemple, dans Visual Studio 2017 RC, vous pouvez ouvrir un projet créé dans Visual Studio 2015 ou Visual Studio 2013, le modifier, puis le rouvrir dans Visual Studio 2017 RC. Vous y retrouverez vos modifications et le projet se comportera de la même façon que dans la version antérieure. Il en va de même pour bon nombre de ressources créées dans Visual Studio 2012.  

 Si vous utilisez Visual Studio 2015 en même temps que Visual Studio 2013, Visual Studio 2012 ou Visual Studio 2010 SP1, vous pouvez créer et modifier des projets et des fichiers dans n’importe laquelle de ces versions. Vous pouvez transférer des projets et des fichiers entre les versions, tant que vous n'ajoutez pas de fonctionnalités non prises en charge par l'une des versions. (Pour plus d’informations sur les fonctionnalités propres à chacune des versions, consultez nos [Notes de publication](https://www.visualstudio.com/vs/release-notes/).)

