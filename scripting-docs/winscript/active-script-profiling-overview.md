---
title: "Profilage de script actif, pr&#233;sentation | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Profilage de script actif"
ms.assetid: eec2f413-6605-4df4-a86f-4919755e9358
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Profilage de script actif, pr&#233;sentation
[Profilage de script actif, interfaces](../winscript/reference/active-script-profiler-interfaces.md) active le profilage d'un moteur de script.  Le profilage de script actif inclut des parties suivantes :  
  
-   Moteur de langage  
  
-   Hôte  
  
-   Profileur  
  
## Moteur de langage  
 Le moteur de langage exécute le script.  Il fournit des méthodes qui permettent le profilage de code de script lorsqu'il est exécuté.  Lorsque le profilage est activé, le moteur de langage prend l'identificateur de classe \(CLSID\) de l'objet COM de profileur comme argument.  Il crée une instance de l'objet COM puis les appels du profileur dans le profileur lorsque des événements se produisent.  
  
 Le moteur de langage implémente [IActiveScriptProfilerControl, interface](../winscript/reference/iactivescriptprofilercontrol-interface.md).  
  
> [!NOTE]
>  Le langage runtime d' [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] contrôle la variable d'environnement de JS\_PROFILER sur la création pour déterminer si le profilage doit être activé.  Si cette variable a la valeur CLSID du profileur, le langage runtime crée une instance de l'objet COM de profileur, à l'aide de la valeur de la variable pour déterminer le profileur à créer.  
  
## Hôte  
 L'hôte crée le moteur de langage et fournit au moteur de langue des scripts à exécuter.  Intelligent un hôte fournit également le contexte de document qui peut être utilisé par un débogueur ou un profileur pour fournir de meilleures informations lorsque vous déboguez ou profiler.  
  
## Profileur  
 Le profileur reçoit les appels du moteur de langage lorsque des événements se produisent.  Le profileur doit être inscrit en tant qu'objet COM et doit implémenter l'interface d' [IActiveScriptProfilerCallback, interface](../winscript/reference/iactivescriptprofilercallback-interface.md) .  
  
## Voir aussi  
 [Profilage de script actif, interfaces](../winscript/reference/active-script-profiler-interfaces.md)