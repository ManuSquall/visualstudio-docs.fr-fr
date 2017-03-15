---
title: "Proc&#233;dure&#160;: modifier l&#39;option de d&#233;bogage pas &#224; pas (h&#233;rit&#233;e) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "débogage de branches pas à pas"
  - "débogage de workflows, options pas à pas"
  - "débogage, options pas à pas"
  - "débogage d'instances pas à pas"
  - "pas à pas, modifier les options"
ms.assetid: aedc06af-d58a-44d6-aee4-f397f1f923a0
caps.latest.revision: 5
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# Proc&#233;dure&#160;: modifier l&#39;option de d&#233;bogage pas &#224; pas (h&#233;rit&#233;e)
Cette rubrique décrit comment modifier l'option de débogage pas à pas pour les applications [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] dans le [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] hérité qui comportent des actions simultanées.Utilisez le [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] hérité lorsque vous devez cibler le [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou le [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 Lorsque vous déboguez des activités héritées exécutées simultanément \(telles que **ParallelActivity** ou **ConditionedActivityGroup**\), vous pouvez utiliser deux options pour progresser pas à pas dans le code.  
  
 Procédez comme suit pour modifier l'option de débogage pas à pas dans votre projet de workflow hérité.  
  
## Procédures  
  
#### Pour modifier l'option de débogage pas à pas  
  
1.  Lancez Visual Studio.  
  
2.  Ouvrez un projet de workflow hérité existant ou créez un nouveau projet qui fait appel à des activités simultanées et qui cible le [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou le [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
3.  Dans le menu **Workflow** du [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] hérité, pointez sur **Déboguer**, puis sur **Options pas à pas**.  
  
4.  Sélectionnez **Instance** ou **Branche**.  
  
## Voir aussi  
 [Débogage de workflows hérités](../workflow-designer/debugging-legacy-workflows.md)   
 [Options de débogage pas à pas \(héritées\)](../workflow-designer/debug-stepping-options-legacy.md)