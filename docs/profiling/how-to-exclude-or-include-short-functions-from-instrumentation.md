---
title: Guide pratique pour exclure ou inclure les fonctions courtes de l’instrumentation | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, instrument events
- profiling tools, include short functions
- profiling tools, exclude short functions
ms.assetid: eaeead79-aafe-4490-86ff-6ed4cad9c15f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6c6234db781925e8c0558513cb7e8bc608b5cfea
ms.sourcegitcommit: 1b9c1e333c2f096d35cfc77e846116f8e5054557
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2018
ms.locfileid: "34814682"
---
# <a name="how-to-exclude-or-include-short-functions-from-instrumentation"></a>Guide pratique pour exclure ou inclure les fonctions courtes de l’instrumentation
Par défaut, les outils de profilage excluent les *petites fonctions* de l’instrumentation. Les petites fonctions sont des fonctions courtes qui n’effectuent pas d’appels de fonction. L’exclusion de ces petites fonctions permet de réduire la surcharge d’instrumentation, et donc d’accélérer la vitesse d’instrumentation. L’exclusion des petites fonctions a également pour effet de réduire la taille du fichier de données de profilage de performances (.*vsp*) et de raccourcir le temps nécessaire à l’analyse. Si les petites fonctions sont exclues, le temps qui leur est consacré sera soustrait du temps exclusif et inclusif de leurs fonctions parents. Les petites fonctions peuvent être exclues ou incluses dans l’instrumentation, comme le décrit la procédure suivante.  
  
### <a name="to-exclude-or-include-short-functions-from-instrumentation"></a>Pour exclure ou inclure les fonctions courtes de l’instrumentation  
  
1.  Dans l’**Explorateur de performances**, sélectionnez **Session de performance**, puis cliquez avec le bouton droit et sélectionnez **Propriétés**.  
  
     La boîte de dialogue **Pages de propriétés** s’affiche.  
  
2.  Dans les **Pages de propriétés**, cliquez sur les propriétés **Instrumentation**.  
  
3.  Pour exclure les fonctions courtes de l’instrumentation, sélectionnez **Exclure les petites fonctions de l’instrumentation**. Il s'agit du paramètre par défaut.  
  
     - ou -  
  
     Pour inclure les fonctions courtes dans l’instrumentation, décochez la case **Exclure les petites fonctions de l’instrumentation**.  
  
4.  Cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Contrôler la collecte des données](../profiling/controlling-data-collection.md)   
 [Propriétés d’une session de performance](../profiling/performance-session-properties.md)