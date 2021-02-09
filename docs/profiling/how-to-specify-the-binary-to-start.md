---
title: Spécifier le fichier binaire à démarrer | Microsoft Docs
description: Découvrez comment vous devez entrer des informations dans la <Target> boîte de dialogue pages de propriétés pour profiler des fichiers binaires, tels que des dll.
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.performance.property.itemlaunch
helpviewer_keywords:
- profiling tools, launching
- performance tools, launching
- performance sessions, launching
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 575a55ae654ada9774abed510d66b94e4ce9d271
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99899541"
---
# <a name="how-to-specify-the-binary-to-start"></a>Guide pratique pour spécifier le binaire à démarrer

Pour profiler des fichiers binaires, tels que des dll, vous devez entrer des informations dans la boîte de dialogue **\<Target> pages de propriétés** . Ces informations indiquent où le projet DLL peut trouver l’application appelante.

1. Dans l’**Explorateur de performances**, cliquez avec le bouton droit sur le fichier binaire cible, puis cliquez sur **Propriétés**.

2. Dans la boîte de dialogue **Pages de propriétés**, cliquez sur les propriétés **Lancer**.

3. Cochez la case **Remplacer les paramètres du projet**.

4. Dans la zone de texte **Exécutable à lancer**, spécifiez l’emplacement du fichier.

5. Dans la zone de texte **Arguments**, spécifiez les arguments nécessaires pour démarrer l’application.

6. Dans la zone de texte **Répertoire de travail**, spécifiez l’emplacement du répertoire.

7. Cliquez sur **OK**.

## <a name="see-also"></a>Voir aussi

[Configurer des sessions de performance](../profiling/configuring-performance-sessions.md)
