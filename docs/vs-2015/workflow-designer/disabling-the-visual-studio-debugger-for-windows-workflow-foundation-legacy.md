---
title: Désactivation du débogueur pour Windows Workflow Foundation (hérité) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- workflows, disabling debugger
- debugging workflows, disabling debugger
- workflow debugger, disabling
ms.assetid: 9da96d0e-f941-4fa9-a1a5-6bab50adfec9
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: eddd72d648e7349f51096a21131f38c2e370a277
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656784"
---
# <a name="disabling-the-visual-studio-debugger-for-windows-workflow-foundation-legacy"></a>Désactivation du débogueur Visual Studio pour Windows Workflow Foundation (hérité)
Cette rubrique décrit comment désactiver le débogueur [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] à l'aide du fichier de configuration lors de la génération d'applications [!INCLUDE[wf](../includes/wf-md.md)] dans le [!INCLUDE[wfd1](../includes/wfd1-md.md)] hérité. Utilisez le [!INCLUDE[wfd2](../includes/wfd2-md.md)] hérité lorsque vous devez cibler le [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] ou le [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 Par défaut, le débogueur [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)] pour [!INCLUDE[wf](../includes/wf-md.md)] est activé pour un processus hôte. Pour désactiver le débogage de workflow, vous devez le désactiver explicitement en ajoutant une entrée « DisableWorkflowDebugging » **\<switches élément >** dans la section **\<system. Diagnostics >** du fichier de configuration hôte.

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
 [Appel du débogueur Visual Studio pour le débogage Windows Workflow Foundation (hérité) des flux de](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md) [travail hérités](../workflow-designer/debugging-legacy-workflows.md)