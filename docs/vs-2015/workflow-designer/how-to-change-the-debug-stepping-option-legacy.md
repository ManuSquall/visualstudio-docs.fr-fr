---
title: 'Comment : modifier l’option de débogage pas à pas (héritée) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- branch stepping
- debugging, stepping options
- debugging workflows, stepping options
- stepping, changing options
- instance stepping
ms.assetid: aedc06af-d58a-44d6-aee4-f397f1f923a0
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5126b3dc45d33471080ae154e06f4a327e21fef7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72663439"
---
# <a name="how-to-change-the-debug-stepping-option-legacy"></a>Procédure : modifier l'option de débogage pas à pas (héritée)
Cette rubrique décrit comment modifier l'option de débogage pas à pas pour les applications [!INCLUDE[wf](../includes/wf-md.md)] dans le [!INCLUDE[wfd1](../includes/wfd1-md.md)] hérité qui comportent des actions simultanées. Utilisez le [!INCLUDE[wfd2](../includes/wfd2-md.md)] hérité lorsque vous devez cibler le [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] ou le [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 Lorsque vous déboguez des activités héritées qui ont une exécution simultanée, telle que **ParallelActivity** ou **ConditionedActivityGroup**, vous pouvez utiliser l’une des deux options pour parcourir votre code.

 Procédez comme suit pour modifier l'option de débogage pas à pas dans votre projet de workflow hérité.

## <a name="procedures"></a>Procédures

#### <a name="to-change-the-debug-stepping-option"></a>Pour modifier l'option de débogage pas à pas

1. Démarrez Visual Studio.

2. Ouvrez un projet de workflow hérité existant ou créez un nouveau projet qui fait appel à des activités simultanées et qui cible le [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] ou le [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

3. Dans le menu **Workflow** de l’ancien [!INCLUDE[wfd2](../includes/wfd2-md.md)] , pointez sur **Déboguer**, puis pointez sur **options pas à pas**.

4. Sélectionnez une **instance** ou une **branche**.

## <a name="see-also"></a>Voir aussi
 [Débogage des flux de travail hérités](../workflow-designer/debugging-legacy-workflows.md) [options de débogage pas à pas (hérité)](../workflow-designer/debug-stepping-options-legacy.md)