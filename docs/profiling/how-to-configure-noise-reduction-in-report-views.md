---
title: "Comment&#160;: configurer la r&#233;duction du bruit dans les vues des rapports d’outils de profilage | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.noisereduction.dialog"
helpviewer_keywords: 
  - "outils de profilage, supprimer"
  - "outils de profilage, rapport de réduction du bruit"
  - "outils de profilage, repli"
ms.assetid: b07e0375-bb73-47e3-8d1d-b9b492fb16c9
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Comment&#160;: configurer la r&#233;duction du bruit dans les vues des rapports d’outils de profilage
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Les rapports de performances peuvent être configurés pour la réduction du bruit en limitant la quantité de données présentée dans les vues Arborescence des appels et Allocation.  L'utilisation de la fonction de réduction du bruit permet de mieux rendre compte des problèmes de performances.  ce qui est utile lors de l'analyse des rapports de performances.  
  
 Les options de configuration de la réduction du bruit incluent les paramètres suivants :  
  
-   **Suppression** Lorsqu'un rapport est analysé, l'affichage omet les fonctions comprises dans les paramètres de valeur et de seuil que vous avez configurés, tel que décrit dans la procédure de suppression qui suit.  La suppression est activée par défaut.  
  
-   **Repli** Si vous activez la fonction de repli, les fonctions suivantes sur un chemin d'accès répondant aux paramètres configurés sont fusionnées comme décrit dans la procédure de repli ci\-après.  Le repli est activé par défaut.  
  
### Pour configurer la suppression pour un rapport de performances  
  
1.  Tandis qu'une vue Arborescence des appels ou Allocation est affichée dans le rapport généré, dans le menu **Développeur**, cliquez sur **Profileur** puis sur **Options de réduction du bruit**.  
  
     La boîte de dialogue **Réduction du bruit** s'ouvre.  
  
2.  Pour activer la suppression, procédez comme suit :  
  
    1.  Sélectionnez **Activer la suppression**.  Il s'agit de l'option par défaut.  
  
        > [!NOTE]
        >  Si la réduction du bruit est activée, une barre d'informations s'affiche dans le rapport.  Pour plus d'informations, consultez [Mode Arborescence des appels](../profiling/call-tree-view.md) et [Mode Allocations](../profiling/dotnet-memory-allocations-view.md).  
  
    2.  Configurez le paramétrage de la valeur à l'aide de la liste déroulante **Valeur** et choisissez le paramétrage applicable.  
  
    3.  Configurez le paramètre de seuil désiré en tapant une valeur en pourcentage dans la zone de texte **Seuil**.  
  
    4.  Pour activer l'avertissement de réduction du bruit dans le rapport généré, sélectionnez **Afficher un avertissement dans le rapport généré lorsque l'option Réduction du bruit est activée**.  Il s'agit de l'option par défaut.  
  
3.  Pour désactiver la suppression, désactivez **Activer la suppression**.  
  
4.  Cliquez sur **OK**.  
  
### Pour configurer le repli pour un rapport de performances  
  
1.  Dans le menu **Développeur**, cliquez sur **Profileur** puis sur **Options de réduction du bruit**.  
  
     La boîte de dialogue **Réduction du bruit** s'ouvre.  
  
2.  Pour activer le repli, procédez comme suit :  
  
    1.  Sélectionnez **Activer le repli**.  Il s'agit de l'option par défaut.  
  
        > [!NOTE]
        >  Si la réduction du bruit est activée, une barre d'informations s'affiche dans le rapport.  Pour plus d'informations, consultez [Mode Arborescence des appels](../profiling/call-tree-view.md) et [Mode Allocations](../profiling/dotnet-memory-allocations-view.md).  
  
    2.  Configurez le paramétrage de la valeur à l'aide de la liste déroulante **Valeur** et choisissez le paramétrage applicable.  
  
    3.  Configurez le paramètre de seuil désiré en tapant une valeur en pourcentage dans la zone de texte **Seuil**.  
  
    4.  Pour activer l'avertissement de réduction du bruit dans le rapport généré, sélectionnez **Afficher un avertissement dans le rapport généré lorsque l'option Réduction du bruit est activée**.  Il s'agit de l'option par défaut.  
  
3.  Pour désactiver le repli, désactivez **Activer le repli**.  
  
4.  Cliquez sur **OK**.  
  
## Voir aussi  
 [Personnalisation des vues des rapports des outils de profilage](../profiling/customizing-performance-tools-report-views.md)   
 [Procédure : exclure ou inclure les fonctions courtes de l’instrumentation](../Topic/How%20to:%20Exclude%20or%20Include%20Short%20Functions%20from%20Instrumentation.md)   
 [Mode Arborescence des appels](../profiling/call-tree-view.md)   
 [Mode Allocations](../profiling/dotnet-memory-allocations-view.md)