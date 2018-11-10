---
title: Options de débogage Azure cloud services | Microsoft Docs
description: Débogage des services cloud Azure
author: mikejo5000
manager: douge
ms.assetid: 80755da7-8350-4f5c-97ce-2962beabb36d
ms.topic: conceptual
ms.workload: azure-vs
ms.date: 03/18/2017
ms.author: mikejo
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.openlocfilehash: bd2608371871b7adc925fc11927fe061b00a1ec6
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2018
ms.locfileid: "51001971"
---
# <a name="learn-the-various-ways-to-debug-an-azure-cloud-service"></a>Découvrir les différentes façons de déboguer un service cloud Azure
Cet article fournit des liens vers les différentes façons de déboguer un service cloud Azure. 

## <a name="debugging-an-azure-cloud-service-in-visual-studio"></a>Débogage d’un service cloud Azure dans Visual Studio
Vous pouvez gagner du temps et argent à l’aide d’Azure compute émulateur pour déboguer votre service cloud sur un ordinateur local. Déboguer un service localement avant de le déployer, vous pouvez améliorer la fiabilité et les performances sans devoir payer de temps de calcul. Toutefois, certaines erreurs peuvent se produire uniquement lorsque vous exécutez un service cloud dans Azure. Vous pouvez déboguer les erreurs qui se produisent uniquement lorsque vous exécutez un service cloud dans Azure en activant le débogage à distance lorsque vous publiez votre service et puis d’attacher le débogueur à une instance de rôle. Pour plus d’informations, consultez [déboguer votre service cloud sur votre ordinateur local](vs-azure-tools-debug-cloud-services-virtual-machines.md#debug-your-cloud-service-on-your-local-computer).

## <a name="using-intellitrace"></a>Utilisation d'IntelliTrace 
Si vous utilisez Visual Studio Enterprise pour écrire des rôles ciblés sur .NET Framework 4.5, vous pouvez activer IntelliTrace au moment que vous déployez un service cloud Azure à partir de Visual Studio. IntelliTrace fournit un journal que vous pouvez utiliser avec Visual Studio pour déboguer votre application comme si elle s’exécutait dans Azure. Pour plus d’informations, consultez [débogage d’un service cloud publié avec IntelliTrace et Visual Studio](http://go.microsoft.com/fwlink/p/?LinkId=623016).

## <a name="remote-debugging"></a>Débogage distant 
Vous pouvez activer le débogage à distance sur vos services cloud en temps lorsque vous déployez le service cloud à partir de Visual Studio. Si vous choisissez d’activer le débogage distant pour un déploiement, les services de débogage distant sont installés sur les machines virtuelles qui s’exécutent chaque instance de rôle. Ces services, tels que `msvsmon.exe` - ne pas affecter les performances ou entraîner des coûts supplémentaires. Pour plus d’informations, consultez [déboguer un service cloud dans Azure](vs-azure-tools-debug-cloud-services-virtual-machines.md#debug-a-cloud-service-in-azure).

## <a name="next-steps"></a>Étapes suivantes
- [Débogage d’un service cloud Azure ou une machine virtuelle dans Visual Studio](./vs-azure-tools-debug-cloud-services-virtual-machines.md) -Découvrez les détails nécessaires déboguer les services cloud Azure.