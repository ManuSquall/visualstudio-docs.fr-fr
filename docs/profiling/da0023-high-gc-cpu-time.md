---
title: "DA0023&#160;: temps processeur&#160;GC &#233;lev&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.DA0023"
  - "vs.performance.23"
  - "vs.performance.rules.DA0023"
ms.assetid: aba875fe-9cbc-418d-a2c4-6eb47519a5bb
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DA0023&#160;: temps processeur&#160;GC &#233;lev&#233;
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|Id de règle|DA0023|  
|Catégorie|Utilisation du .NET framework|  
|Méthode de profilage|Tout|  
|Message|% Temps dans le GC est relativement élevé. Cette indication de quantité excessive de traitement de garbage collection pourrait être ayant un impact sur la réactivité de votre application. Vous pouvez collecter .NET allocation de mémoire données et l’objet de durée de vie des informations pour comprendre le modèle de votre application utilise mieux l’allocation de mémoire.|  
|Type de règle|Informations|  
  
 Lorsque vous profilez à l’aide de l’échantillonnage, de mémoire .NET ou méthodes, vous devez collecter au moins 10 échantillons pour déclencher cette règle.  
  
## <a name="cause"></a>Cause  
 Les données des performances système collectées pendant le profilage indiquent que le temps passé dans le garbage collection est significatif comparé au temps total de l’application de traitement.  
  
## <a name="rule-description"></a>Description de la règle  
 Le Microsoft .NET common language runtime (CLR) fournit un mécanisme de gestion automatique de la mémoire qui utilise un garbage collector pour libérer la mémoire des objets que l’application n’utilise plus. Le garbage collector est orienté génération, basée sur l’hypothèse que les nombreuses allocations sont de courte durées. Les variables locales, par exemple, doivent être courtes. Objets nouvellement créés commencent à la génération 0 (gen 0), puis progressent jusqu'à la génération 1 lorsqu’ils survivent à une exécution de garbage collection et enfin la transition à la génération 2 si l’application utilise toujours les.  
  
 Objets dans la génération 0 sont collectés fréquemment et généralement très efficace. Objets de génération 1 sont collectés moins fréquemment et moins efficace. Enfin, les objets durables dans la génération 2 doivent être collectés moins fréquemment encore. Collection de génération 2, qui est un garbage collection complet exécuté, est également l’opération la plus coûteuse.  
  
 Cette règle se déclenche lorsque le temps passé dans le garbage collection est significatif comparé au temps de traitement total de l’application.  
  
> [!NOTE]
>  Lorsque la proportion de temps passé dans le garbage collection est excessive comparé au temps de traitement total de l’application, le [DA0024 : temps de processeur GC excessif](../profiling/da0024-excessive-gc-cpu-time.md) avertissement se déclenche au lieu de cette règle.  
  
## <a name="how-to-investigate-a-warning"></a>Comment examiner un avertissement  
 Double-cliquez sur le message dans la fenêtre liste d’erreurs pour naviguer jusqu'à la [vue marques](../profiling/marks-view.md) des données de profilage. Rechercher les **mémoire CLR .NET\\% de temps dans GC** colonne. Déterminer s’il existe des phases spécifiques de l’exécution du programme où la surcharge de nettoyage de la mémoire managée est plus importante que d’autres phases. Comparer les valeurs du compteur % temps dans le GC au taux de garbage collection de la valeur signalée dans le **nombre de Collections de la génération 0**, **# de collection de la génération 1**, **# de Collections de génération 2** valeurs.  
  
 % Temps dans le GC essaie de signaler la quantité de temps qu’une application garbage collection proportionnellement à la quantité totale de traitement. N’oubliez pas qu’il existe certains cas lorsque la valeur % temps dans le GC peut signaler une valeur très élevée, mais il n’est pas en raison de nettoyage de la mémoire excessive. Pour plus d’informations sur la façon dont la valeur % temps dans le GC est calculée, consultez la [différence entre les données de performance signalées par différents outils – 4](http://go.microsoft.com/fwlink/?LinkId=177863) entrée de **Weblog de Maoni** sur MSDN. Si des défauts de page sont produisent ou que l’application est devancée par d’autres tâches plus prioritaires sur l’ordinateur pendant le garbage collection, % temps dans le compteur de GC reflétera ces délais supplémentaires.