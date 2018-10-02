---
title: Guide pratique pour sérialiser les informations de symboles | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Performance.General
helpviewer_keywords:
- profiling tools, serializing symbol information
- performance tools, serializing symbol information
ms.assetid: 9e0da706-6325-4073-83d1-aeab3b7c137a
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 04bce9383142ee6916fa7ade50feda072019f530
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47505232"
---
# <a name="how-to-serialize-symbol-information"></a>Procédure : sérialiser les informations de symboles
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [Comment : sérialiser les informations de symboles](https://docs.microsoft.com/visualstudio/profiling/how-to-serialize-symbol-information).  
  
Vous pouvez sérialiser les symboles nécessaires à l’analyse de votre application. La sérialisation de symboles ajoute des symboles au fichier .vsp. L’ajout d’informations de symboles au fichier .vsp permet aux autres utilisateurs d’analyser un rapport de performances sans avoir accès aux symboles d’origine. Si les symboles ne sont pas sérialisés, vous devez disposer des fichiers .exe et .pdb instrumentés d’origine pour analyser le fichier .vsp.  
  
### <a name="to-automatically-serialize-symbol-information"></a>Pour sérialiser automatiquement les informations de symboles  
  
1.  Dans le menu **Outils** , cliquez sur **Options**.  
  
     La boîte de dialogue **Options** s’affiche.  
  
2.  Cliquez sur **Outils d’analyse des performances**.  
  
3.  Sous **Paramètres généraux**, sélectionnez **Sérialiser automatiquement les informations de symboles**.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration de sessions de performance](../profiling/configuring-performance-sessions.md)   
 [Guide pratique pour référencer les informations de symboles Windows](../profiling/how-to-reference-windows-symbol-information.md)   
 [Guide pratique pour enregistrer des fichiers de rapports enregistrés](http://msdn.microsoft.com/en-us/0340ddde-caf4-48ac-8af3-d15dcdade556)



