---
title: "Débogage de Workflows à partir d’un ordinateur distant (hérité) | Documents Microsoft"
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- workflows, debugging remotely
- debugging workflows, remotely
- remote debugging, workflows
- debugging, remote
ms.assetid: 44eaec8f-9959-4ae7-a374-670946f933c1
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: be8c1f6a049224cc5b79a82dc6bc100840c72fd0
ms.sourcegitcommit: 37c87118f6f41e832da96f21f6b4cc0cf8fee046
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2018
---
# <a name="debugging-workflows-from-a-remote-computer-legacy"></a>Débogage de workflows d'un ordinateur distant (hérité)
Cette rubrique décrit comment déboguer à distance héritée [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)] les applications générées avec le Concepteur de flux de travail Windows hérité. Utilisez le [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] hérité lorsque votre application doit cibler le [!INCLUDE[netfx35_long](../workflow-designer/includes/netfx35_long_md.md)] ou le [!INCLUDE[vstecwinfx](../workflow-designer/includes/vstecwinfx_md.md)].

 Lorsque vous installez [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)], une des options d’installation de composant consiste à installer le [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] du débogueur pour [!INCLUDE[wf](../workflow-designer/includes/wf_md.md)]. Cela installe les composants de débogage distant. Ces composants de débogage distant doivent être installés sur l'ordinateur que vous utiliserez pour le débogage distant de workflows.

 En outre, l'assembly qui contient la définition du workflow hérité que vous déboguez sur un ordinateur distant doit être installé dans le Global Assembly Cache (GAC) de l'ordinateur local utilisé pour le débogage. Par exemple, si un workflow hérité est exécuté sur un ordinateur distant A et que vous le déboguez à partir de l'ordinateur local B, la définition de workflow doit être présente dans le GAC de l'ordinateur B. Cela permet au concepteur de désérialiser et d'afficher sur l'ordinateur B le balisage du workflow exécuté à distance sur l'ordinateur A. Pour plus d'informations sur le Global Assembly Cache, consultez MSDN Library.

 Le débogage distant [!INCLUDE[wf2](../workflow-designer/includes/wf2_md.md)] fonctionne sur le même principe que débogage distant d'autres composants [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Pour plus d’informations, consultez [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)] le débogage distant dans la bibliothèque MSDN.

## <a name="see-also"></a>Voir aussi

- [Débogage de flux de travail hérités](../workflow-designer/debugging-legacy-workflows.md)