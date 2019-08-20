---
title: Résolution des problèmes liés aux métriques du code | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: troubleshooting
ms.assetid: f2fdb995-4888-4246-85dc-7bacadd45968
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1567715a8f944eb10c2728caa9fc1edd43beda8e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62580581"
---
# <a name="troubleshooting-code-metrics-issues"></a>Résolution des problèmes liés à la métrique du code
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez rencontrer certains des problèmes suivants quand vous collectez des métriques du code :  
  
- [Modifications dans les calculs de complexité du code dans Visual Studio 2010](#Changes_in_Visual_Studio_2010_code_complexity_calculations)  
  
## <a name="Changes_in_Visual_Studio_2010_code_complexity_calculations"></a> Modifications dans les calculs de complexité du code dans Visual Studio 2010  
 Pour la même fonction, la métrique de complexité du code calculée dans [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] peut être différente de la métrique calculée par les versions antérieures de [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] dans les situations suivantes :  
  
- La fonction contient un ou plusieurs blocs catch. Dans les versions précédentes de [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)], les blocs catch n’étaient pas inclus dans le calcul. Dans [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)], la complexité de chaque bloc catch est ajoutée à la complexité de la fonction.  
  
- La fonction contient une instruction switch (Select Case dans VB). Des différences de compilateur entre [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] et les versions antérieures peuvent générer un code MSIL différent pour certaines instructions switch qui contiennent des éléments case avec fallthrough.  
  
## <a name="see-also"></a>Voir aussi  
 [Mesures de la complexité et de la facilité de maintenance du code managé](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)
