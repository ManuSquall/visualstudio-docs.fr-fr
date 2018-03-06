---
title: "Guide pratique pour spécifier des options d’instrumentation supplémentaires | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.performance.property.advanced
helpviewer_keywords:
- instrumentation, options
- profiling tools, session options
- performance sessions, options
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 8052c0538619588f60fd21802209d57bd7fdf80d
ms.sourcegitcommit: 36ab8429333b31f03992a9fe8fc669db8e09c968
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2018
---
# <a name="how-to-specify-additional-instrumentation-options"></a>Comment : spécifier des options d’instrumentation supplémentaires

Vous pouvez instrumenter des binaires à l’aide de l’IDE de Visual Studio ou d’outils en ligne de commande. Si vous instrumentez un fichier binaire à partir de l’IDE, vous pouvez contrôler le volume de données collectées lors de l’instrumentation en spécifiant des options d’instrumentation supplémentaires dans l’outil [VSInstr](../profiling/vsinstr.md). Ces options sont disponibles au niveau de la session ou de la cible. Par exemple, pour inclure ou exclure des fonctions spécifiques lors du processus d’instrumentation, utilisez l’option d’instrumentation supplémentaire au niveau de la cible.

> [!IMPORTANT]
> Chaque sonde insérée modifie légèrement le comportement du programme d’origine. Cette modification provoque une surcharge au moment de l’analyse. Même si une approximation de cette surcharge est soustraite, elle produit toujours des effets de minutage subtils sur les applications multithread. Les options de l’outil [VSInstr](../profiling/vsinstr.md) permettent de contrôler la collecte des données lors du profilage.

## <a name="to-specify-additional-instrumentation-option"></a>Pour spécifier des options d’instrumentation supplémentaires

1. Dans l’**Explorateur de performances**, sélectionnez **Session de performance**, puis cliquez avec le bouton droit et sélectionnez **Propriétés**.

2. Dans les **Pages de propriétés**, cliquez sur les propriétés **Avancées**.

3. Tapez les options souhaitées dans la zone **Options d’instrumentation supplémentaires**.

     Par exemple, utilisez /CONTROL:THREAD pour spécifier le niveau de profilage. Pour obtenir la liste complète des options, consultez [VSInstr](../profiling/vsinstr.md).

4. Cliquez sur **OK**.

## <a name="see-also"></a>Voir aussi

[Configuration de sessions de performances](../profiling/configuring-performance-sessions.md)  
[Profilage à partir de la ligne de commande](../profiling/using-the-profiling-tools-from-the-command-line.md)