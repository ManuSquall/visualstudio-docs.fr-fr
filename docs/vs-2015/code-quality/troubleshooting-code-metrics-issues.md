---
title: Résolution des problèmes liés aux métriques du code | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f2fdb995-4888-4246-85dc-7bacadd45968
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 2cc5c586e1e994ff2e14710b39c04bb424b770d2
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51800638"
---
# <a name="troubleshooting-code-metrics-issues"></a>Résolution des problèmes liés à la métrique du code
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez rencontrer certains des problèmes suivants quand vous collectez des métriques du code :  
  
-   [Modifications dans les calculs de complexité du code dans Visual Studio 2010](#Changes_in_Visual_Studio_2010_code_complexity_calculations)  
  
##  <a name="Changes_in_Visual_Studio_2010_code_complexity_calculations"></a> Modifications dans les calculs de complexité du code dans Visual Studio 2010  
 Pour la même fonction, la métrique de complexité du code calculée dans [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] peut être différente de la métrique calculée par les versions antérieures de [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] dans les situations suivantes :  
  
-   La fonction contient un ou plusieurs blocs catch. Dans les versions précédentes de [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)], les blocs catch n’étaient pas inclus dans le calcul. Dans [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)], la complexité de chaque bloc catch est ajoutée à la complexité de la fonction.  
  
-   La fonction contient une instruction switch (Select Case dans VB). Des différences de compilateur entre [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] et les versions antérieures peuvent générer un code MSIL différent pour certaines instructions switch qui contiennent des éléments case avec fallthrough.  
  
## <a name="see-also"></a>Voir aussi  
 [Mesures de la complexité et de la facilité de maintenance du code managé](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)



