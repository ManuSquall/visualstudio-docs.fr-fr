---
title: Concepteur de flux de travail - débogage de Workflows à partir d’un ordinateur distant (hérité)
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- workflows, debugging remotely
- debugging workflows, remotely
- remote debugging, workflows
- debugging, remote
ms.assetid: 44eaec8f-9959-4ae7-a374-670946f933c1
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 391180cd76fe5e0cccca802ba1cbfb78277dabc1
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
ms.locfileid: "31967906"
---
# <a name="debugging-workflows-from-a-remote-computer-legacy"></a>Débogage de workflows d'un ordinateur distant (hérité)

Cette rubrique décrit comment déboguer des applications de Windows Workflow Foundation (WF) héritées distantes générées avec le Concepteur de flux de travail Windows hérité. Utilisez le Concepteur de flux de travail hérité lorsque votre application doit cibler le .NET Framework version 3.5 ou du WinFX.

 Lorsque vous installez Visual Studio, une des options d’installation de composant doit installer le Visual Studio débogueur pour Windows Workflow Foundation (WF). Cela installe les composants de débogage distant. Ces composants de débogage distant doivent être installés sur l'ordinateur que vous utiliserez pour le débogage distant de workflows.

 En outre, l'assembly qui contient la définition du workflow hérité que vous déboguez sur un ordinateur distant doit être installé dans le Global Assembly Cache (GAC) de l'ordinateur local utilisé pour le débogage. Par exemple, si un workflow hérité est exécuté sur un ordinateur distant A et que vous le déboguez à partir de l'ordinateur local B, la définition de workflow doit être présente dans le GAC de l'ordinateur B. Cela permet au concepteur de désérialiser et d'afficher sur l'ordinateur B le balisage du workflow exécuté à distance sur l'ordinateur A. Pour plus d'informations sur le Global Assembly Cache, consultez MSDN Library.

 Le débogage distant Windows Workflow Foundation fonctionne de la même façon que le débogage distant pour d'autres composants Visual Studio. Pour plus d’informations, consultez Débogage à distance Visual Studio dans MSDN Library.

## <a name="see-also"></a>Voir aussi

- [Débogage de flux de travail hérités](../workflow-designer/debugging-legacy-workflows.md)