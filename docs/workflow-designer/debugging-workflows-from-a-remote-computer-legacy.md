---
title: "D&#233;bogage de workflows d&#39;un ordinateur distant (h&#233;rit&#233;) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "débogage de workflows, à distance"
  - "débogage, distant"
  - "débogage distant, workflows"
  - "workflows, déboguer à distance"
ms.assetid: 44eaec8f-9959-4ae7-a374-670946f933c1
caps.latest.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# D&#233;bogage de workflows d&#39;un ordinateur distant (h&#233;rit&#233;)
Cette rubrique décrit comment déboguer des applications [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] héritées distantes générées avec le [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] hérité.Utilisez le [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] hérité lorsque votre application doit cibler le [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou le [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 Lorsque vous installez [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)], l'une des options d'installation du composant consiste à installer le débogueur [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] pour [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)].Cela installe les composants de débogage distant.Ces composants de débogage distant doivent être installés sur l'ordinateur que vous utiliserez pour le débogage distant de workflows.  
  
 En outre, l'assembly qui contient la définition du workflow hérité que vous déboguez sur un ordinateur distant doit être installé dans le Global Assembly Cache \(GAC\) de l'ordinateur local utilisé pour le débogage.Par exemple, si un workflow hérité s'exécute sur un ordinateur distant A, et vous le déboguer à partir de l'ordinateur local B, la définition de workflow doit être présente dans le GAC d'ordinateur B.Cela permet au concepteur de désérialiser et d'afficher sur l'ordinateur B le balisage du workflow qui s'exécute à distance sur l'ordinateur A.Pour plus d'informations sur le Global Assembly Cache, consultez MSDN Library.  
  
 Le débogage distant [!INCLUDE[wf2](../workflow-designer/includes/wf2_md.md)] fonctionne sur le même principe que débogage distant d'autres composants [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].Pour plus d'informations, consultez les informations sur le débogage distant [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] dans MSDN Library.  
  
## Voir aussi  
 [Débogage de workflows hérités](../workflow-designer/debugging-legacy-workflows.md)