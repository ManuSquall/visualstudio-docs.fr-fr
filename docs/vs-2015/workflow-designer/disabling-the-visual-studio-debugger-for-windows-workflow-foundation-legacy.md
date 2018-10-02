---
title: Désactivation du débogueur de Visual Studio pour Windows Workflow Foundation (hérité) | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- workflows, disabling debugger
- debugging workflows, disabling debugger
- workflow debugger, disabling
ms.assetid: 9da96d0e-f941-4fa9-a1a5-6bab50adfec9
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: 9fd51e47ff92e231507e56bb3eacad212a47c90d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47505624"
---
# <a name="disabling-the-visual-studio-debugger-for-windows-workflow-foundation-legacy"></a>Désactivation du débogueur Visual Studio pour Windows Workflow Foundation (hérité)
Cette rubrique décrit comment désactiver le débogueur [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] à l'aide du fichier de configuration lors de la génération d'applications [!INCLUDE[wf](../includes/wf-md.md)] dans le [!INCLUDE[wfd1](../includes/wfd1-md.md)] hérité. Utilisez le [!INCLUDE[wfd2](../includes/wfd2-md.md)] hérité lorsque vous devez cibler le [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] ou le [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].  
  
 Par défaut, le débogueur [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)] pour [!INCLUDE[wf](../includes/wf-md.md)] est activé pour un processus hôte. Pour désactiver le débogage de flux de travail, vous devez explicitement désactiver en ajoutant une entrée « DisableWorkflowDebugging »  **\<commutateurs >** élément dans le  **\<system.diagnostics >** section du fichier de configuration hôte.  
  
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