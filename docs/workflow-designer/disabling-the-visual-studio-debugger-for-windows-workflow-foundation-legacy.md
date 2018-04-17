---
title: La désactivation du débogueur de Visual Studio pour Windows Workflow Foundation (hérité) | Documents Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- workflows, disabling debugger
- debugging workflows, disabling debugger
- workflow debugger, disabling
ms.assetid: 9da96d0e-f941-4fa9-a1a5-6bab50adfec9
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a609062f3f84538f7c1655cd5ca82971fc608f62
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="disabling-the-visual-studio-debugger-for-windows-workflow-foundation-legacy"></a>Désactivation du débogueur Visual Studio pour Windows Workflow Foundation (hérité)

Cette rubrique décrit comment désactiver le [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] à l’aide du fichier de configuration lors de la génération du débogueur [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] applications dans le Concepteur de flux de travail Windows hérité. Utilisez le [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] hérité lorsque vous devez cibler le [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou le [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].

 Par défaut, le débogueur [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] pour [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] est activé pour un processus hôte. Pour désactiver le débogage de flux de travail, vous devez explicitement désactiver en ajoutant une entrée disableworkflowdebugging » à « le  **\<commutateurs >** élément dans le  **\<system.diagnostics >**section du fichier de configuration hôte.

 L 'exemple suivant indique comment modifier le fichier de configuration hôte pour désactiver le débogage de workflow.

```xml
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

- [Appel du débogueur Visual Studio pour Windows Workflow Foundation (hérité)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md)
- [Débogage de flux de travail hérités](../workflow-designer/debugging-legacy-workflows.md)