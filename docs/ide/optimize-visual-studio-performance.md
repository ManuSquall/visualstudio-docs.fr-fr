---
title: Améliorer les performances si Visual Studio est lent
titleSuffix: ''
description: Découvrez comment améliorer les performances de Visual Studio si vous constatez qu’il s’exécute lentement.
ms.custom: SEO-VS-2020
ms.date: 04/11/2018
ms.topic: conceptual
helpviewer_keywords:
- performance [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jmartens
f1_keywords:
- vs.performancecenter
ms.workload:
- multiple
ms.openlocfilehash: e1c1be9ef034f4c11fde22e8aa811785631321f5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99909120"
---
# <a name="optimize-visual-studio-performance"></a>Optimiser le niveau de performance de Visual Studio

Cet article contient des suggestions à essayer si vous trouvez que Visual Studio s’exécute lentement. Vous pouvez aussi consulter [Conseils et astuces pour améliorer les performances de Visual Studio](../ide/visual-studio-performance-tips-and-tricks.md) pour d’autres suggestions sur la façon d’améliorer les performances.

## <a name="upgrade-visual-studio"></a>Mettre à niveau Visual Studio

Si vous utilisez Visual Studio 2015, téléchargez gratuitement [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) ou [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) pour bénéficier de ses performances améliorées. Les solutions se chargent deux ou trois fois plus rapidement que dans Visual Studio 2015, les performances d’autres opérations ayant également été améliorées. Visual Studio 2017 et Visual Studio 2019 étant compatibles côte à côte avec Visual Studio 2015, vous ne perdrez rien en les essayant.

::: moniker range="vs-2017"

Si vous utilisez déjà Visual Studio 2017, veillez à exécuter la version 15.6 ou ultérieure. Les données montrent que les solutions se chargent à deux ou trois fois plus rapidement dans la version 15.6. Téléchargez-le [ici](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download).

::: moniker-end

## <a name="extensions-and-tool-windows"></a>Extensions et fenêtres Outil

Vous pouvez avoir des extensions installées qui ralentissent Visual Studio. Pour obtenir de l’aide sur la gestion des extensions visant à améliorer les performances, consultez [Modifier les paramètres d’extension pour améliorer les performances](../ide/optimize-visual-studio-startup-time.md#extensions).

De la même façon, vous pouvez avoir des fenêtres Outil qui ralentissent Visual Studio. Pour obtenir de l’aide sur la gestion des fenêtres Outil, consultez [Modifier les paramètres des fenêtres Outil pour améliorer les performances](../ide/optimize-visual-studio-startup-time.md#tool-windows).

## <a name="hardware"></a>Matériel

Si vous envisagez de mettre à niveau votre matériel, notez qu’un disque SSD a plus d’effet sur les performances que de la mémoire RAM supplémentaire ou un processeur plus rapide.

Si vous ajoutez un disque SSD, pour des performances optimales, installez Windows sur ce lecteur plutôt que sur un disque dur classique. Le lecteur sur lequel vous placez vos solutions Visual Studio ne semble pas avoir beaucoup d’importance.

N’exécutez pas non plus votre solution à partir d’un lecteur USB. Copiez-la sur votre disque dur classique ou votre disque SSD.

## <a name="help-us-improve"></a>Aidez-nous à améliorer le produit

Vos commentaires nous aident à améliorer le produit. Utilisez la fonctionnalité **Signaler un problème** pour « enregistrer » une trace et nous l’envoyer. Sélectionnez l’icône de commentaires à côté de **Lancement rapide**, ou sélectionnez **Aide** > **Envoyer des commentaires** > **Signaler un problème** dans la barre de menus. Pour plus d’informations, consultez Guide pratique [pour signaler un problème avec Visual Studio](../ide/how-to-report-a-problem-with-visual-studio.md).

## <a name="see-also"></a>Voir aussi

- [Trucs et astuces pour les performances](../ide/visual-studio-performance-tips-and-tricks.md)
- [Visual Studio blog - Load solutions faster with Visual Studio 2017 version 15.6](https://devblogs.microsoft.com/visualstudio/load-solutions-faster-with-visual-studio-2017-version-15-6/)
