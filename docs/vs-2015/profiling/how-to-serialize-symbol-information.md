---
title: 'Procédure : Sérialiser les informations de symboles | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Performance.General
helpviewer_keywords:
- profiling tools, serializing symbol information
- performance tools, serializing symbol information
ms.assetid: 9e0da706-6325-4073-83d1-aeab3b7c137a
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b29ddb0e88a58fbfd924c40134305cf33a3e170b
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60103795"
---
# <a name="how-to-serialize-symbol-information"></a>Procédure : Sérialiser les informations de symbole
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez sérialiser les symboles nécessaires à l’analyse de votre application. La sérialisation de symboles ajoute des symboles au fichier .vsp. L’ajout d’informations de symboles au fichier .vsp permet aux autres utilisateurs d’analyser un rapport de performances sans avoir accès aux symboles d’origine. Si les symboles ne sont pas sérialisés, vous devez disposer des fichiers .exe et .pdb instrumentés d’origine pour analyser le fichier .vsp.  
  
### <a name="to-automatically-serialize-symbol-information"></a>Pour sérialiser automatiquement les informations de symboles  
  
1. Dans le menu **Outils**, cliquez sur **Options**.  
  
     La boîte de dialogue **Options** s’affiche.  
  
2. Cliquez sur **Outils d’analyse des performances**.  
  
3. Sous **Paramètres généraux**, sélectionnez **Sérialiser automatiquement les informations de symboles**.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration de sessions de performance](../profiling/configuring-performance-sessions.md)   
 [Guide pratique pour Informations de symbole de référence Windows](../profiling/how-to-reference-windows-symbol-information.md)   
 [Guide pratique pour Enregistrer les fichiers de rapports analysés](http://msdn.microsoft.com/0340ddde-caf4-48ac-8af3-d15dcdade556)
