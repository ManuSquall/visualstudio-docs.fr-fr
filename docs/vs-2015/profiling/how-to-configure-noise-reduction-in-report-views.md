---
title: Guide pratique pour configurer la réduction du bruit dans les vues Rapports | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.noisereduction.dialog
helpviewer_keywords:
- profiling tools, trimming
- profiling tools, report noise reduction
- profiling tools, folding
ms.assetid: b07e0375-bb73-47e3-8d1d-b9b492fb16c9
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a532a4ddf877e49a6cf355d182d41ed723b2f5d0
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54800327"
---
# <a name="how-to-configure-noise-reduction-in-report-views"></a>Comment : configurer la réduction du bruit dans les vues des rapports
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez configurer la réduction du bruit dans les rapports de performances en limitant la quantité de données affichées dans la vue Arborescence des appels et la vue Allocation. La réduction du bruit vous permet de repérer plus rapidement les problèmes de performances. Cette fonctionnalité est utile lorsque vous analysez des rapports de performances.  
  
 Les options de configuration de la réduction de bruit sont les suivantes :  
  
-   **Suppression** Lorsqu’un rapport est analysé, la vue n’affiche pas les fonctions qui correspondent aux valeurs et au seuil que vous avez configurés, comme le décrit la procédure de suppression qui suit. La suppression est activée par défaut.  
  
-   **Repli** Si vous activez le repli, les fonctions consécutives d’un chemin qui répondent aux paramètres que vous avez configurés seront fusionnées, comme le décrit la procédure de repli qui suit. Le repli est activé par défaut.  
  
### <a name="to-configure-trimming-for-a-performance-report"></a>Pour configurer la suppression dans un rapport de performances  
  
1.  Lorsqu’une vue Arborescence des appels ou une vue Allocation s’affiche dans le rapport généré, dans le menu **Développeur**, cliquez sur **Profileur**, puis sur **Options de réduction du bruit**.  
  
     La boîte de dialogue **Réduction du bruit** apparaît.  
  
2.  Pour activer la suppression, effectuez les étapes suivantes :  
  
    1.  Sélectionnez **Activer la suppression**. Il s'agit du paramètre par défaut.  
  
        > [!NOTE]
        >  Si la réduction du bruit est activée, une barre d’informations s’affiche dans le rapport. Pour plus d’informations, consultez [Arborescence des appels, vue](../profiling/call-tree-view.md) et [Allocations, vue](../profiling/dotnet-memory-allocations-view.md).  
  
    2.  Pour configurer le paramètre de valeur, accédez à la liste déroulante **Valeur** et sélectionnez le paramètre applicable.  
  
    3.  Configurez le paramètre de seuil de votre choix en tapant un pourcentage dans la zone de texte **Seuil**.  
  
    4.  Pour activer l’avertissement de réduction du bruit dans le rapport généré, sélectionnez **Afficher un avertissement dans le rapport généré lorsque l’option Réduction du bruit est activée**. Il s'agit du paramètre par défaut.  
  
3.  Pour désactiver la suppression, décochez l’option **Activer la suppression**.  
  
4.  Cliquez sur **OK**.  
  
### <a name="to-configure-folding-for-a-performance-report"></a>Pour configurer le repli dans un rapport de performances  
  
1.  Dans le menu **Développeur**, cliquez sur **Profileur**, puis sur **Options de réduction du bruit**.  
  
     La boîte de dialogue **Réduction du bruit** apparaît.  
  
2.  Pour activer le repli, effectuez les étapes suivantes :  
  
    1.  Sélectionnez **Activer le repli**. Il s'agit du paramètre par défaut.  
  
        > [!NOTE]
        >  Si la réduction du bruit est activée, une barre d’informations s’affiche dans le rapport. Pour plus d’informations, consultez [Arborescence des appels, vue](../profiling/call-tree-view.md) et [Allocations, vue](../profiling/dotnet-memory-allocations-view.md).  
  
    2.  Pour configurer le paramètre de valeur, accédez à la liste déroulante **Valeur** et sélectionnez le paramètre applicable.  
  
    3.  Configurez le paramètre de seuil de votre choix en tapant un pourcentage dans la zone de texte **Seuil**.  
  
    4.  Pour activer l’avertissement de réduction du bruit dans le rapport généré, sélectionnez **Afficher un avertissement dans le rapport généré lorsque l’option Réduction du bruit est activée**. Il s'agit du paramètre par défaut.  
  
3.  Pour désactiver le repli, décochez l’option **Activer le repli**.  
  
4.  Cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Personnalisation des vues des rapports des outils d’analyse des performances](../profiling/customizing-performance-tools-report-views.md)   
 [Guide pratique pour exclure ou inclure les fonctions courtes de l’instrumentation](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md)   
 [Arborescence des appels, vue](../profiling/call-tree-view.md)   
 [Allocations, vue](../profiling/dotnet-memory-allocations-view.md)
