---
title: Guide pratique pour spécifier des options d’instrumentation supplémentaires | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.property.advanced
helpviewer_keywords:
- instrumentation, options
- profiling tools, session options
- performance sessions, options
ms.assetid: 639afe26-8335-4bd4-8aa5-f2c607b81f07
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d4bc6eeb208ab6d80168431f110f0f6169abbc82
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839510"
---
# <a name="how-to-specify-additional-instrumentation-options"></a>Guide pratique pour spécifier des options d’instrumentation supplémentaires
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez instrumenter des fichiers binaires à partir de l’environnement de développement intégré (IDE) de [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] ou à l’aide d’outils en ligne de commande. Si vous instrumentez un fichier binaire à partir de l’IDE, vous pouvez contrôler le volume de données collectées lors de l’instrumentation en spécifiant des options d’instrumentation supplémentaires dans l’outil [VSInstr](../profiling/vsinstr.md). Ces options sont disponibles au niveau de la session ou de la cible. Par exemple, pour inclure ou exclure des fonctions spécifiques lors du processus d’instrumentation, utilisez l’option d’instrumentation supplémentaire au niveau de la cible.  
  
 **Configuration requise**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
> [!IMPORTANT]
> Chaque sonde insérée modifie légèrement le comportement du programme d’origine. Cette modification provoque une surcharge au moment de l’analyse. Même si une approximation de cette surcharge est soustraite, elle produit toujours des effets de minutage subtils sur les applications multithread. Les options de l’outil [VSInstr](../profiling/vsinstr.md) permettent de contrôler la collecte des données lors du profilage.  
  
### <a name="to-specify-additional-instrumentation-option"></a>Pour spécifier des options d’instrumentation supplémentaires  
  
1. Dans l’**Explorateur de performances**, sélectionnez **Session de performance**, puis cliquez avec le bouton droit et sélectionnez **Propriétés**.  
  
2. Dans les **Pages de propriétés**, cliquez sur les propriétés **Avancées**.  
  
3. Tapez les options souhaitées dans la zone **Options d’instrumentation supplémentaires**.  
  
     Par exemple, utilisez /CONTROL:THREAD pour spécifier le niveau de profilage. Pour obtenir la liste complète des options, consultez [VSInstr](../profiling/vsinstr.md).  
  
4. Cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des sessions de performance](../profiling/configuring-performance-sessions.md)   
 [Profilage à partir de la ligne de commande](../profiling/using-the-profiling-tools-from-the-command-line.md)
