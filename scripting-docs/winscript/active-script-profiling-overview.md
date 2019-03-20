---
title: Présentation du profilage de script actif | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Active Script Profiling
ms.assetid: eec2f413-6605-4df4-a86f-4919755e9358
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d03ab4df7a41fe6513a18446d26e33e9856d1183
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2019
ms.locfileid: "58149612"
---
# <a name="active-script-profiling-overview"></a>Profilage de script actif, présentation
Les [Interfaces de profiler de script actif](../winscript/reference/active-script-profiler-interfaces.md) permettent de profiler un moteur de script. Le profilage de script actif se compose des éléments suivants :  
  
-   Moteur de langage  
  
-   Hôte  
  
-   Profiler  
  
## <a name="language-engine"></a>Moteur de langage  
 Le moteur de langage exécute le script. Il fournit des méthodes qui autorisent le profilage du code de script quand il est exécuté. Quand le profilage est activé, le moteur de langage prend l’identificateur de classe (CLSID) de l’objet COM du profileur en tant qu’argument. Il crée une instance de l’objet COM du profileur et appelle ensuite le profileur quand certains événements se produisent.  
  
 Le moteur de langage implémente [l’interface IActiveScriptProfilerControl](../winscript/reference/iactivescriptprofilercontrol-interface.md).  
  
> [!NOTE]
>  Le runtime du langage [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] vérifie la variable d’environnement JS_PROFILER lors de la création afin de déterminer si le profilage doit être activé. Si cette variable a comme valeur le CLSID du profileur, le runtime du langage crée une instance de l’objet COM du profileur, en utilisant la valeur de la variable pour déterminer le profileur à créer.  
  
## <a name="host"></a>Hôte  
 L’hôte crée le moteur de langage et lui fournit les scripts à exécuter. Un hôte intelligent fournit également le contexte de document qui peut être utilisé par un débogueur ou par le profileur pour fournir des informations enrichies quand vous déboguez ou profilez.  
  
## <a name="profiler"></a>Profiler  
 Le profileur reçoit les appels du moteur de langage quand certains événements se produisent. Le profileur doit être inscrit en tant qu’objet COM et doit implémenter l’interface [IActiveScriptProfilerCallback](../winscript/reference/iactivescriptprofilercallback-interface.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces de profiler de script actif](../winscript/reference/active-script-profiler-interfaces.md)