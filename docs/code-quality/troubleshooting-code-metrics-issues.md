---
title: "Résolution des problèmes des métriques de Code | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f2fdb995-4888-4246-85dc-7bacadd45968
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: ea1e787c1d509123a650cf2bd20e5fa8bffd5b4e
ms.openlocfilehash: 9f3f41548412d84cd1219aae45b7c87ea5383de9
ms.contentlocale: fr-fr
ms.lasthandoff: 09/26/2017

---
# <a name="troubleshooting-code-metrics-issues"></a>Résolution des problèmes liés à la métrique du code
Vous pouvez rencontrer certains des problèmes suivants lorsque vous collectez des métriques de code :  
  
-   [Modifications dans les calculs de complexité de code Visual Studio 2010](#Changes_in_Visual_Studio_2010_code_complexity_calculations)  
  
##  <a name="Changes_in_Visual_Studio_2010_code_complexity_calculations"></a>Modifications dans les calculs de complexité de code Visual Studio 2010  
 Pour la même fonction, la métrique de complexité du code calculée dans [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] peut être différente de la métrique calculée par les versions antérieures de [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] dans les situations suivantes :  
  
-   La fonction contient un ou plusieurs blocs catch. Dans les versions précédentes de [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)], catch blocs n’étaient pas incluses dans le calcul. Dans [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)], la complexité de chaque bloc catch est ajoutée à la complexité de la fonction.  
  
-   La fonction contient une instruction switch (Select Case dans VB). Différences de compilateur entre [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] et les versions antérieures peuvent générer un code MSIL différent pour certaines instructions switch qui contiennent des cas de passage.  
  
## <a name="see-also"></a>Voir aussi  
 [Mesures de la complexité et de la facilité de maintenance du code managé](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)
