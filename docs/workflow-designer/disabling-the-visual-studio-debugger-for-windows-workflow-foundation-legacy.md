---
title: "D&#233;sactivation du d&#233;bogueur Visual Studio pour Windows Workflow Foundation (h&#233;rit&#233;) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "débogage de workflows, désactivation du débogueur"
  - "débogueur de workflows, désactiver"
  - "workflows, désactiver le débogueur"
ms.assetid: 9da96d0e-f941-4fa9-a1a5-6bab50adfec9
caps.latest.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# D&#233;sactivation du d&#233;bogueur Visual Studio pour Windows Workflow Foundation (h&#233;rit&#233;)
Cette rubrique décrit comment désactiver le débogueur [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] à l'aide du fichier de configuration lors de la génération d'applications [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] dans le [!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] hérité.Utilisez le [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] hérité lorsque vous devez cibler le [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou le [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].  
  
 Par défaut, le débogueur [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] pour [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] est activé pour un processus hôte.Pour désactiver le débogage de workflow, vous devez explicitement le désactiver via l'ajout de l'entrée « DisableWorkflowDebugging » à l'élément **\<switches\>** de la section **\<system.diagnostics\>** du fichier de configuration hôte.  
  
 L'exemple suivant indique comment modifier le fichier de configuration hôte pour désactiver le débogage de workflow.  
  
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
  
## Voir aussi  
 [Appel du débogueur Visual Studio pour Windows Workflow Foundation \(hérité\)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)   
 [Débogage de workflows hérités](../workflow-designer/debugging-legacy-workflows.md)