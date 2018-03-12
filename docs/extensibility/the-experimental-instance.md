---
title: "L’Instance expérimentale | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- experimental builds
- VSPackages, experimental builds
- VSIP, experimental builds
ms.assetid: ead0df4e-6f88-4b42-9297-581b7902f050
caps.latest.revision: "36"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: a656baf951e573a5913960b19c1b583797de090f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="the-experimental-instance"></a>L’Instance expérimentale
Pour protéger votre environnement de développement Visual Studio à partir d’applications non testées susceptible du modifier, l’extensibilité Visual Studio fournit un espace d’expérimentation que vous pouvez utiliser pour faire des essais. Vous développez des applications à l’aide de Visual Studio comme d’habitude, mais les exécuter à l’aide de cette instance expérimentale.  
  
 Chaque application qui dispose d’un package VSIX démarre l’instance expérimentale de Visual Studio en mode débogage.  
  
 Si vous souhaitez démarrer l’instance expérimentale de Visual Studio en dehors d’une solution spécifique, exécutez la commande suivante dans la fenêtre de commande :  
  
 «*\<Chemin d’installation de visual studio >*\Common7\IDE\devenv.exe « RootSuffix Exp  
  
> [!NOTE]
>  L’instance expérimentale est écrit dans le Registre sous le `<version number>Exp` et `<version number>Exp_Config` nœuds. Par exemple la zone de Registre expérimentale de Visual Studio 2015 est  
>   
>  `HKCU\Software\Microsoft\VisualStudio\14.0Exp` et `HKCU\Software\Microsoft\VisualStudio\14.0Exp_Config`  
  
 Nous vous conseillons d’exécuter votre extension dans l’instance expérimentale pendant que vous le développez. Lorsque vous déployez l’extension, elle s’exécute dans l’instance de développement. Pour plus d’informations sur l’inscription des applications, consultez [l’inscription de VSPackages](../extensibility/internals/registering-vspackages.md).