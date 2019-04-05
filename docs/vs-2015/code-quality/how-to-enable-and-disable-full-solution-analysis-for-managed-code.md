---
title: 'Procédure : Activer et désactiver l’analyse de la Solution complète pour le Code managé | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- full solution analysis
ms.assetid: 04315147-5792-47f0-8b5f-9ac8413c6a57
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 6b9efdb5ea3e7ccbee9aefb724e847db6a37c2a0
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58938659"
---
# <a name="how-to-enable-and-disable-full-solution-analysis-for-managed-code"></a>Procédure : Activer et désactiver l’analyse de la Solution complète pour le Code managé
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

REMARQUE]
>  Cette rubrique s’applique uniquement à Visual Studio 2015 Update 3 RC et versions ultérieures.  
  
 *Complète l’analyse de la solution* est une fonctionnalité de Visual Studio qui vous permet de choisir si vous voyez des problèmes d’analyse de code uniquement dans les fichiers ouverts Visual c# ou Visual Basic dans votre solution, ou dans les fichiers Visual c# ou Visual Basic ouvertes et fermées dans votre solution.  
  
 S’il est utile de pouvoir voir tous les problèmes dans tous les fichiers, il peut être gênant, voire de ralentir Visual Studio si votre solution est très volumineuse ou a un grand nombre de fichiers.  Pour limiter le nombre de problèmes indiqué et améliorer les performances de Visual Studio, vous pouvez désactiver l’analyse complète de la solution. Vous pouvez facilement réactiver cette fonctionnalité si vous le souhaitez.  
  
#### <a name="to-toggle-full-solution-analysis"></a>Pour activer/désactiver l’analyse complète de la solution  
  
1.  Dans le menu principal dans Visual Studio, choisissez **outils** &#124; **Options** pour afficher le **Options** boîte de dialogue.  
  
2.  Dans le **Options** boîte de dialogue, sélectionnez **éditeur de texte** &#124; **c#** ou **base** &#124; **avancé**.  
  
3.  Sélectionnez le **activer l’analyse complète de la solution** case à cocher pour activer l’analyse complète de la solution, ou désactivez la case pour le désactiver. Choisissez le **OK** bouton lorsque vous avez terminé.  
  
     ![Activez la case à cocher analyse complète de la solution. ](../code-quality/media/fsa-toolsoptions.png "FSA_ToolsOptions")  
  
## <a name="results-of-enabling-and-disabling-full-solution-analysis"></a>Résultats de l’activation et désactivation de l’analyse complète de la solution  
 Dans la capture d’écran suivante, vous pouvez voir les résultats lorsque l’analyse complète de la solution est activée. Toutes les erreurs et problèmes d’analyse de code dans *tous les* des fichiers dans la solution apparaissent, indépendamment de si les fichiers sont ouverts ou non.  
  
 ![Analyse complète de la solution est activée. ](../code-quality/media/fsa-enabled.png "FSA_Enabled")  
  
 La capture d’écran suivante montre les résultats à partir de la même solution après la désactivation de l’analyse complète de la solution. Uniquement les erreurs et les problèmes d’analyse de code dans ouvrent solution fichiers apparaissent dans la liste d’erreurs.  
  
 ![L’analyse est désactivée. ](../code-quality/media/fsa-disabled.png "FSA_Disabled")  
  
## <a name="automatically-disabling-full-solution-analysis"></a>Désactivant l’analyse complète de la solution  
 Si Visual Studio détecte que 200 Mo ou moins de mémoire système disponible à ce dernier, il désactive automatiquement l’analyse complète de la solution (ainsi que d’autres fonctionnalités) s’il est activé. Si cela se produit, une alerte s’affiche pour vous en informe. Un bouton vous permet de réactiver l’analyse complète de la solution si vous souhaitez faire.  
  
 ![Texte de l’alerte la suspension de l’analyse complète de la solution](../code-quality/media/fsa-alert.png "FSA_Alert")  
  
## <a name="additional-details"></a>Détails supplémentaires  
 Par défaut, l’analyse complète de la solution est activée pour Visual Basic et désactivée pour Visual c#.  
  
 Visual Studio Update 3 RC inclut un moteur de diagnostic v2 analyseur code améliorée qui réduit l’utilisation de la mémoire de manière significative et diminue les temps de processeur à inactif, même si l’analyse complète de la solution est activée.
