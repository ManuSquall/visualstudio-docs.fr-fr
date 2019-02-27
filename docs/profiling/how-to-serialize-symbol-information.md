---
title: 'Procédure : Sérialiser les informations de symboles | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Performance.General
helpviewer_keywords:
- profiling tools, serializing symbol information
- performance tools, serializing symbol information
ms.assetid: 9e0da706-6325-4073-83d1-aeab3b7c137a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 72a634bd83a55d4e646874cce5546e2a7310afb2
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56617845"
---
# <a name="how-to-serialize-symbol-information"></a>Procédure : Sérialiser les informations de symbole
Vous pouvez sérialiser les symboles nécessaires à l’analyse de votre application. La sérialisation de symboles permet d’ajouter des symboles au fichier .*vsp*. L’ajout d’informations de symboles au fichier .*vsp* permet aux autres utilisateurs d’analyser un rapport de performances sans avoir accès aux symboles d’origine. Si les symboles ne sont pas sérialisés, vous devez disposer des fichiers .*exe* et .*pdb* instrumentés d’origine pour analyser le fichier .*vsp*.

### <a name="to-automatically-serialize-symbol-information"></a>Pour sérialiser automatiquement les informations de symboles

1.  Dans le menu **Outils** , cliquez sur **Options**.

     La boîte de dialogue **Options** s’affiche.

2.  Cliquez sur **Outils d’analyse des performances**.

3.  Sous **Paramètres généraux**, sélectionnez **Sérialiser automatiquement les informations de symboles**.

## <a name="see-also"></a>Voir aussi
- [Configurer des sessions de performances](../profiling/configuring-performance-sessions.md)
- [Guide pratique pour référencer les informations de symboles Windows](../profiling/how-to-reference-windows-symbol-information.md)
- [Guide pratique pour Enregistrer des fichiers de rapports analysés](/previous-versions/visualstudio/visual-studio-2010/bb763106\(v\=vs.100\))