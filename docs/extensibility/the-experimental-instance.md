---
title: L’instance expérimentale (en anglais) Microsoft Docs
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
ms.openlocfilehash: 8e2284767a0aa6be58c0f7e38c912783728914cb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699037"
---
# <a name="the-experimental-instance"></a>Instance expérimentale
Pour protéger votre environnement de développement Visual Studio contre les applications non testées qui pourraient le modifier, le VSSDK fournit un espace expérimental que vous pouvez utiliser pour expérimenter. Vous développez de nouvelles applications en utilisant Visual Studio comme d’habitude, mais vous les exécutez en utilisant cette instance expérimentale.

 Chaque application qui dispose d’un package VSIX lance l’instance expérimentale Visual Studio en mode débogé.

 Si vous souhaitez commencer l’instance expérimentale de Visual Studio en dehors d’une solution spécifique, exécutez la commande suivante à la fenêtre de commande :

 "*\<Visual studio installation path>*'Common7'IDE’devenv.exe" /RootSuffix Exp

> [!NOTE]
> L’instance expérimentale est écrite `<version number>Exp` au `<version number>Exp_Config` registre sous les nœuds et les nœuds. Par exemple, la zone de registre expérimental Visual Studio 2015 est
>
> `HKCU\Software\Microsoft\VisualStudio\14.0Exp` et `HKCU\Software\Microsoft\VisualStudio\14.0Exp_Config`

 Nous vous recommandons d’exécuter votre extension dans l’instance expérimentale pendant que vous la développez. Lorsque vous déployez l’extension, elle s’exécute dans l’instance de développement. Pour plus d’informations sur l’enregistrement des applications, voir [L’enregistrement vsPackages](../extensibility/internals/registering-vspackages.md).
