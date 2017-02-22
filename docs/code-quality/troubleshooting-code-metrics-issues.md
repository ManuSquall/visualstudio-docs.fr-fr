---
title: "R&#233;solution des probl&#232;mes li&#233;s &#224; la m&#233;trique du code | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f2fdb995-4888-4246-85dc-7bacadd45968
caps.latest.revision: 4
author: "erickson-doug"
ms.author: "douge"
manager: "douge"
caps.handback.revision: 4
---
# R&#233;solution des probl&#232;mes li&#233;s &#224; la m&#233;trique du code
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous pouvez rencontrer quelques\-uns des problèmes suivants lorsque vous collectez des métriques de code :  
  
-   [Modifications dans les calculs de complexité du code Visual Studio 2010](#Changes_in_Visual_Studio_2010_code_complexity_calculations)  
  
##  <a name="Changes_in_Visual_Studio_2010_code_complexity_calculations"></a> Modifications dans les calculs de complexité du code Visual Studio 2010  
 Pour la même fonction, la métrique de complexité du code calculée dans [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] peut être différente de la métrique calculée par les versions antérieures de [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] pour les situations suivantes :  
  
-   La fonction contient un ou plusieurs blocs catch.  Dans les versions antérieures de [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)], les blocs catch n'étaient pas inclus dans le calcul.  Dans [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)], la complexité de chaque bloc catch est ajoutée à la complexité de la fonction.  
  
-   La fonction contient une instruction switch \(Select Case dans VB\).  Les différences de compilateur entre [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] et les versions antérieures peuvent générer un code MSIL différent pour certaines instructions switch qui contiennent des cas de passage.  
  
## Voir aussi  
 [Mesures de la complexité et de la facilité de maintenance du code managé](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)