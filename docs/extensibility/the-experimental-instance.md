---
title: L’instance expérimentale | Microsoft Docs
description: Découvrez comment le kit de développement logiciel (SDK) Visual Studio fournit un espace expérimental pour exécuter des applications non testées en mode débogage.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- experimental builds
- VSPackages, experimental builds
- VSIP, experimental builds
ms.assetid: ead0df4e-6f88-4b42-9297-581b7902f050
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4786f450b108c8a6c1eaefc6f86f7adf57e9269e
ms.sourcegitcommit: 94a57a7bda3601b83949e710a5ca779c709a6a4e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2020
ms.locfileid: "97715858"
---
# <a name="the-experimental-instance"></a>Instance expérimentale
Pour protéger votre environnement de développement Visual Studio des applications non testées susceptibles de le modifier, VSSDK fournit un espace expérimental que vous pouvez utiliser pour expérimenter. Vous développez de nouvelles applications à l’aide de Visual Studio comme d’habitude, mais vous les exécutez à l’aide de cette instance expérimentale.

 Chaque application dotée d’un package VSIX lance l’instance expérimentale de Visual Studio en mode débogage.

 Si vous souhaitez démarrer l’instance expérimentale de Visual Studio à l’extérieur d’une solution spécifique, exécutez la commande suivante dans la fenêtre de commande :

 « *\<Visual studio installation path>* \Common7\IDE\devenv.exe »/RootSuffix exp

> [!NOTE]
> L’instance expérimentale est écrite dans le Registre sous les `<version number>Exp` `<version number>Exp_Config` nœuds et. Par exemple, la zone de Registre expérimentale de Visual Studio 2015 est
>
> `HKCU\Software\Microsoft\VisualStudio\14.0Exp` et `HKCU\Software\Microsoft\VisualStudio\14.0Exp_Config`

 Nous vous recommandons d’exécuter votre extension dans l’instance expérimentale pendant que vous la développez. Lorsque vous déployez l’extension, elle s’exécute dans l’instance de développement. Pour plus d’informations sur l’inscription des applications, consultez [inscription de VSPackages](../extensibility/internals/registering-vspackages.md).
