---
title: L’Instance expérimentale | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- experimental builds
- VSPackages, experimental builds
- VSIP, experimental builds
ms.assetid: ead0df4e-6f88-4b42-9297-581b7902f050
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 493ab672322db2826f8f7e7675decdda0a531538
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63435069"
---
# <a name="the-experimental-instance"></a>Instance expérimentale
Afin de préserver votre environnement de développement Visual Studio à partir d’applications non testées susceptible du modifier, l’extensibilité Visual Studio fournit un espace expérimental que vous pouvez utiliser pour faire des essais. Développer de nouvelles applications à l’aide de Visual Studio comme d’habitude, mais les exécuter à l’aide de cette instance expérimentale.

 Chaque application qui dispose d’un package VSIX lance l’instance expérimentale de Visual Studio en mode débogage.

 Si vous souhaitez démarrer l’instance expérimentale de Visual Studio en dehors d’une solution spécifique, exécutez la commande suivante dans la fenêtre de commande :

 «*\<Chemin d’installation de visual studio >* \Common7\IDE\devenv.exe » RootSuffix Exp

> [!NOTE]
> L’instance expérimentale est écrite dans le Registre sous le `<version number>Exp` et `<version number>Exp_Config` nœuds. Par exemple la zone de Registre expérimentale de Visual Studio 2015 est
>
> `HKCU\Software\Microsoft\VisualStudio\14.0Exp` et `HKCU\Software\Microsoft\VisualStudio\14.0Exp_Config`

 Nous vous recommandons d’exécuter votre extension dans l’instance expérimentale pendant que vous le développez. Lorsque vous déployez l’extension, elle s’exécute dans l’instance de développement. Pour plus d’informations sur l’inscription des applications, consultez [l’inscription de VSPackages](../extensibility/internals/registering-vspackages.md).