---
title: "Guide pratique pour spécifier le fichier binaire à démarrer | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.performance.property.itemlaunch
helpviewer_keywords:
- profiling tools, launching
- performance tools, launching
- performance sessions, launching
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 94dbedfaa008b83ac45cea9afaa6bac2a254e77e
ms.sourcegitcommit: 36ab8429333b31f03992a9fe8fc669db8e09c968
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2018
---
# <a name="how-to-specify-the-binary-to-start"></a>Guide pratique pour spécifier le fichier binaire à démarrer

Pour profiler des fichiers binaires, tels que les DLL, vous devez entrer des informations dans la boîte de dialogue **Pages de propriétés de \<Cible>**. Ces informations indiquent où le projet DLL peut trouver l’application appelante.

1. Dans l’**Explorateur de performances**, cliquez avec le bouton droit sur le fichier binaire cible, puis cliquez sur **Propriétés**.

2. Dans la boîte de dialogue **Pages de propriétés**, cliquez sur les propriétés **Lancer**.

3. Cochez la case **Remplacer les paramètres du projet**.

4. Dans la zone de texte **Exécutable à lancer**, spécifiez l’emplacement du fichier.

5. Dans la zone de texte **Arguments**, spécifiez les arguments nécessaires pour démarrer l’application.

6. Dans la zone de texte **Répertoire de travail**, spécifiez l’emplacement du répertoire.

7. Cliquez sur **OK**.

## <a name="see-also"></a>Voir aussi

[Configuration de sessions de performances](../profiling/configuring-performance-sessions.md)