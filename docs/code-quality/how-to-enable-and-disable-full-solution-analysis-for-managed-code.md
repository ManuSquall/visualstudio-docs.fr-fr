---
title: "Comment : activer et désactiver l’analyse de la Solution complète pour le Code managé | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: full solution analysis
ms.assetid: 04315147-5792-47f0-8b5f-9ac8413c6a57
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-code-analysis
ms.openlocfilehash: 94cda949a713a773e5586e5b1ef284c6ba54839c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-enable-and-disable-full-solution-analysis-for-managed-code"></a>Comment : activer et désactiver l’analyse de la Solution complète pour le Code managé
> [!NOTE]
>  Cette rubrique s’applique uniquement à Visual Studio 2015 Update 3 RC et versions ultérieures.  
  
 *L’analyse complète* est une fonctionnalité de Visual Studio qui vous permet de choisir si vous voyez des problèmes d’analyse de code uniquement dans les fichiers ouverts Visual c# ou Visual Basic dans votre solution ou dans les fichiers Visual c# ou Visual Basic ouvertes et fermées dans votre solution.  
  
 S’il est utile de pouvoir voir tous les problèmes dans tous les fichiers, il peut être perturbante et même ralentir Visual Studio si votre solution est très volumineux ou possède un grand nombre de fichiers.  Pour limiter le nombre de problèmes indiqué et améliorer les performances de Visual Studio, vous pouvez désactiver l’analyse complète de la solution. Vous pouvez facilement réactiver cette fonctionnalité si vous le souhaitez.  
  
#### <a name="to-toggle-full-solution-analysis"></a>Pour activer/désactiver l’analyse complète de la solution  
  
1.  Dans le menu principal dans Visual Studio, choisissez **outils** &#124; **Options** pour afficher les **Options** boîte de dialogue.  
  
2.  Dans le **Options** boîte de dialogue, choisissez **éditeur de texte** &#124; **C#** ou **base** &#124; **Avancé**.  
  
3.  Sélectionnez le **activer l’analyse de la solution complète** case à cocher pour activer l’analyse complète de la solution, ou désactivez la case pour le désactiver. Choisissez le **OK** bouton lorsque vous avez terminé.  
  
     ![Activez la case à cocher analyse complète de la solution. ] (../code-quality/media/fsa_toolsoptions.png "FSA_ToolsOptions")  
  
## <a name="results-of-enabling-and-disabling-full-solution-analysis"></a>Résultats de l’activation et désactivation de l’analyse complète de la solution  
 Dans la capture d’écran suivante, vous pouvez voir les résultats lorsque l’analyse complète de la solution est activée. Toutes les erreurs et problèmes d’analyse de code dans *tous les* des fichiers dans la solution apparaissent, indépendamment de si les fichiers sont ouverts ou non.  
  
 ![Analyse de la solution complète activée. ] (../code-quality/media/fsa_enabled.png "FSA_Enabled")  
  
 La capture d’écran suivante montre les résultats à partir de la même solution après la désactivation de l’analyse complète de la solution. Uniquement les erreurs et les problèmes d’analyse de code dans ouvrent solution fichiers s’affichent dans la liste d’erreurs.  
  
 ![Analyse complète de la solution désactivé. ] (../code-quality/media/fsa_disabled.png "FSA_Disabled")  
  
## <a name="automatically-disabling-full-solution-analysis"></a>Désactivant l’analyse complète de la solution  
 Si Visual Studio détecte que 200 Mo ou moins de mémoire système disponible à ce dernier, il désactive automatiquement l’analyse complète de la solution (ainsi que d’autres fonctionnalités) s’il est activé. Si cela se produit, une alerte s’affiche pour vous en informe. Un bouton vous permet de réactiver l’analyse complète de la solution si vous souhaitez le faire.  
  
 ![Texte d’alerte la suspension de l’analyse complète de la solution](../code-quality/media/fsa_alert.png "FSA_Alert")  
  
## <a name="additional-details"></a>Détails supplémentaires  
 Par défaut, l’analyse complète de la solution est activée pour Visual Basic et désactivée pour Visual c#.  
  
 Visual Studio Update 3 RC inclut un moteur de diagnostic v2 d’Analyseur de code améliorée considérablement réduit l’utilisation de la mémoire et réduit le temps processeur pour des temps d’inactivité, même si l’analyse complète de la solution est activée.