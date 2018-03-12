---
title: "Suspension de la fonctionnalité automatique | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- full solution analysis
- performance
- low-memory
ms.assetid: 572c15aa-1fd0-468c-b6be-9fa50e170914
caps.latest.revision: "6"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-ide-code-analysis
ms.workload: multiple
ms.openlocfilehash: 0bb8155f2ec1ed6815ac37f1124dfbf57cf838b2
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="automatic-feature-suspension"></a>Suspension de la fonctionnalité automatique
Si votre mémoire système disponible est inférieure ou égale à 200 Mo, Visual Studio affiche le message suivant dans l’éditeur de code.  
  
 ![Texte d’alerte la suspension de l’analyse complète de la solution](../code-quality/media/fsa_alert.png "FSA_Alert")  
  
 Lorsque Visual Studio détecte une condition de mémoire insuffisante, il interrompt automatiquement certaines fonctionnalités avancées pour aider à rester stable. Lorsque cela avancé fonctionnalité suspension avertissement s’affiche, Visual Studio continueront de fonctionner comme avant, mais son va légèrement réduire les performances.  
  
 Dans une condition de mémoire insuffisante, les événements suivants se produisent :  
  
-   Analyse de la solution complète pour Visual c# et Visual Basic est désactivée.  
  
-   [Le Garbage Collection](/dotnet/standard/garbage-collection/index) en mode de faible latence (GC) pour Visual c# et Visual Basic sont désactivées.  
  
-   Les caches de Visual Studio sont vidées.  
  
## <a name="improve-visual-studio-performance"></a>Améliorer les performances de Visual Studio  
 Pour obtenir des conseils et astuces sur la façon d’améliorer les performances de Visual Studio lorsque vous traitez des solutions de grande taille ou des conditions de mémoire insuffisante, consultez [considérations relatives aux performances pour les solutions volumineuses](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions).  
  
## <a name="full-solution-analysis-suspended"></a>Analyse complète de la solution suspendu  
 Par défaut, l’analyse complète de la solution est activée pour Visual Basic et désactivée pour Visual c#. Toutefois, dans une condition de mémoire insuffisante, analyse complète de la solution est automatiquement désactivé pour Visual Basic et Visual c#, quels que soient leurs paramètres dans la boîte de dialogue Options. Toutefois, vous pouvez réactiver l’analyse complète de la solution en choisissant le **réactiver** bouton dans les informations de la barre lorsqu’il apparaît, en sélectionnant le **activer l’analyse de la solution complète** case à cocher dans la boîte de dialogue Options, ou le redémarrage de Visual Studio. La boîte de dialogue Options affiche toujours les paramètres d’analyse à la solution complète en cours. Pour plus d’informations, consultez [Comment : activer et désactiver l’analyse de Solution complète](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md).  
  
## <a name="gc-low-latency-disabled"></a>Dans le catalogue global à faible latence désactivée  
 Pour réactiver le mode de faible latence GC, redémarrez Visual Studio.  Par défaut, Visual Studio active le mode de faible latence GC chaque fois que vous tapez pour vous assurer que votre saisie ne bloque pas les opérations de catalogue global. Toutefois, si une condition de mémoire insuffisante entraîne Visual Studio afficher l’avertissement de la suspension automatique, en mode de faible latence GC est désactivé pour cette session. Le redémarrage de Visual Studio activer de nouveau le comportement de catalogue global par défaut. Pour plus d’informations, consultez [GCLatencyMode énumération](http://msdn.microsoft.com/Library/057757a5-cd62-4d13-8a40-370eb7f47c87).  
  
## <a name="visual-studio-caches-flushed"></a>Caches de Visual Studio vidés  
 Tous les caches de Visual Studio sont vidées immédiatement, mais commencent à remplir à nouveau si vous continuez votre session en cours de développement ou redémarrez Visual Studio. Les caches vidées incluent des caches pour les fonctionnalités suivantes.  
  
-   Rechercher toutes les références  
  
-   Boîte de dialogue Naviguer vers  
  
-   Ajouter Using  
  
 En outre, les caches utilisés pour des opérations internes de Visual Studio sont également désélectionnés.  
  
> [!NOTE]
>  L’avertissement de suspension de fonctionnalité automatique se produit une seule fois sur une base par solution, pas sur une base par session. Cela signifie que si vous basculez à partir de Visual Basic, Visual c# (ou vice versa) et s’exécuter dans une autre condition de mémoire insuffisante, vous pouvez éventuellement obtenir une autre avertissement de suspension automatique de fonctionnalité.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : activer et désactiver l’analyse complète de la Solution](../code-quality/how-to-enable-and-disable-full-solution-analysis-for-managed-code.md)   
 [Notions de base du Garbage Collection](/dotnet/standard/garbage-collection/fundamentals)   
 [Considérations relatives aux performances pour les solutions volumineuses](https://github.com/dotnet/roslyn/wiki/Performance-considerations-for-large-solutions)