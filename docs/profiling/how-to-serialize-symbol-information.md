---
title: Guide pratique pour sérialiser les informations de symboles | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Performance.General
helpviewer_keywords:
- profiling tools, serializing symbol information
- performance tools, serializing symbol information
ms.assetid: 9e0da706-6325-4073-83d1-aeab3b7c137a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8b608b41ea4fd1b5b7544604e8d04bed02361b06
ms.sourcegitcommit: bccb05b5b4e435f3c1f7c36ba342e7d4031eb398
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/06/2018
ms.locfileid: "51220864"
---
# <a name="how-to-serialize-symbol-information"></a>Guide pratique pour sérialiser les informations de symboles
Vous pouvez sérialiser les symboles nécessaires à l’analyse de votre application. La sérialisation de symboles permet d’ajouter des symboles au fichier .*vsp*. L’ajout d’informations de symboles au fichier .*vsp* permet aux autres utilisateurs d’analyser un rapport de performances sans avoir accès aux symboles d’origine. Si les symboles ne sont pas sérialisés, vous devez disposer des fichiers .*exe* et .*pdb* instrumentés d’origine pour analyser le fichier .*vsp*.  
  
### <a name="to-automatically-serialize-symbol-information"></a>Pour sérialiser automatiquement les informations de symboles  
  
1.  Dans le menu **Outils** , cliquez sur **Options**.  
  
     La boîte de dialogue **Options** s’affiche.  
  
2.  Cliquez sur **Outils d’analyse des performances**.  
  
3.  Sous **Paramètres généraux**, sélectionnez **Sérialiser automatiquement les informations de symboles**.  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer des sessions de performance](../profiling/configuring-performance-sessions.md)   
 [Guide pratique pour référencer les informations de symboles Windows](../profiling/how-to-reference-windows-symbol-information.md)   
 [Guide pratique pour enregistrer des fichiers de rapports analysés](/previous-versions/visualstudio/visual-studio-2010/bb763106\(v\=vs.100\))