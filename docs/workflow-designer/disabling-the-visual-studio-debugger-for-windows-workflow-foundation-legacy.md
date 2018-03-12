---
title: "La désactivation du débogueur de Visual Studio pour Windows Workflow Foundation (hérité) | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- workflows, disabling debugger
- debugging workflows, disabling debugger
- workflow debugger, disabling
ms.assetid: 9da96d0e-f941-4fa9-a1a5-6bab50adfec9
caps.latest.revision: "6"
author: ErikRe
ms.author: erikre
manager: erikre
ms.workload: multiple
ms.openlocfilehash: 47572d28467d3df8f1ea409eb08a9f37c536eae0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="disabling-the-visual-studio-debugger-for-windows-workflow-foundation-legacy"></a>Désactivation du débogueur Visual Studio pour Windows Workflow Foundation (hérité)
Cette rubrique décrit comment désactiver le débogueur [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] à l'aide du fichier de configuration lors de la génération d'applications [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] dans le [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] hérité. Utilisez le [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] hérité lorsque vous devez cibler le [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou le [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 Par défaut, le débogueur [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] pour [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] est activé pour un processus hôte. Pour désactiver le débogage de flux de travail, vous devez explicitement désactiver en ajoutant une entrée disableworkflowdebugging » à « le  **\<commutateurs >** élément dans le  **\<system.diagnostics >**section du fichier de configuration hôte.  
  
 L 'exemple suivant indique comment modifier le fichier de configuration hôte pour désactiver le débogage de workflow.  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
   <system.diagnostics>  
      <switches>  
         <add name="DisableWorkflowDebugging" value="true"/>  
      </switches>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Appel du débogueur Visual Studio pour Windows Workflow Foundation (hérité)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)   
 [Débogage de flux de travail hérités](../workflow-designer/debugging-legacy-workflows.md)