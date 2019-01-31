---
title: Options de débogage des services cloud Azure | Microsoft Docs
description: Débogage des services cloud Azure
author: mikejo5000
manager: jillfra
ms.assetid: 80755da7-8350-4f5c-97ce-2962beabb36d
ms.topic: conceptual
ms.workload: azure-vs
ms.date: 03/18/2017
ms.author: mikejo
ms.prod: visual-studio-dev15
ms.technology: vs-ide-debug
ms.openlocfilehash: 43e866a6ee1a9d7e63d6e9fa85374d7efb972f9f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55139828"
---
# <a name="learn-the-various-ways-to-debug-an-azure-cloud-service"></a>Découvrez différentes méthodes de débogage d’un service cloud Azure.
Cet article fournit des liens menant vers différentes méthodes de débogage d’un service cloud Azure.

## <a name="debugging-an-azure-cloud-service-in-visual-studio"></a>Débogage d’un service cloud Azure dans Visual Studio
L’utilisation de l’émulateur de calcul Azure pour déboguer votre service cloud sur une machine locale constitue un gain de temps et d’argent. Déboguer un service localement avant de le déployer vous permet d’améliorer la fiabilité et les performances, tout en évitant les coûts de temps de calcul. Certaines erreurs peuvent toutefois se produire quand vous exécutez un service cloud directement dans Azure. Vous pouvez déboguer les erreurs qui surviennent seulement lorsque vous exécutez un service cloud dans Azure en activant le débogage à distance lors de la publication de votre service, puis en associant le débogueur à une instance de rôle. Pour plus d’informations, consultez [Déboguer votre service cloud sur votre ordinateur local](vs-azure-tools-debug-cloud-services-virtual-machines.md#debug-your-cloud-service-on-your-local-computer).

## <a name="using-intellitrace"></a>Utilisation d'IntelliTrace
Si vous utilisez Visual Studio Enterprise pour écrire des rôles ciblés sur .NET Framework 4.5, vous pouvez activer IntelliTrace au moment où vous déployez un service cloud Azure depuis Visual Studio. IntelliTrace fournit un journal que vous pouvez utiliser avec Visual Studio pour déboguer votre application comme si elle s’exécutait dans Azure. Pour plus d’informations, consultez [Débogage d’un service cloud publié avec IntelliTrace et Visual Studio](http://go.microsoft.com/fwlink/p/?LinkId=623016).

## <a name="remote-debugging"></a>Débogage distant
Vous pouvez activer le débogage distant sur vos services cloud au moment où vous les déployez depuis Visual Studio. Si vous choisissez d’activer le débogage distant pour un déploiement, les services de débogage distant sont installés sur les machines virtuelles qui exécutent chaque instance de rôle. Ces services, tels que `msvsmon.exe`, n’affectent pas les performances et n’entraînent pas de coûts supplémentaires. Pour plus d’informations, consultez [Déboguer un service cloud dans Azure](vs-azure-tools-debug-cloud-services-virtual-machines.md#debug-a-cloud-service-in-azure).

## <a name="next-steps"></a>Étapes suivantes
- [Débogage d’un service cloud ou d’une machine virtuelle Azure dans Visual Studio](./vs-azure-tools-debug-cloud-services-virtual-machines.md) : découvrez en détail la méthode de débogage de services cloud Azure.