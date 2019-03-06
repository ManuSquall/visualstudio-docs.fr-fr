---
title: 'Procédure : Spécifier le fichier binaire à démarrer | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.property.itemlaunch
helpviewer_keywords:
- profiling tools, launching
- performance tools, launching
- performance sessions, launching
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a03bf203e5078bdbdf6327ec7bda186613a25c03
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56622655"
---
# <a name="how-to-specify-the-binary-to-start"></a>Procédure : Spécifier le binaire à démarrer

Pour profiler des fichiers binaires, tels que les DLL, vous devez entrer des informations dans la boîte de dialogue **Pages de propriétés de \<Cible>**. Ces informations indiquent où le projet DLL peut trouver l’application appelante.

1. Dans l’**Explorateur de performances**, cliquez avec le bouton droit sur le fichier binaire cible, puis cliquez sur **Propriétés**.

2. Dans la boîte de dialogue **Pages de propriétés**, cliquez sur les propriétés **Lancer**.

3. Cochez la case **Remplacer les paramètres du projet**.

4. Dans la zone de texte **Exécutable à lancer**, spécifiez l’emplacement du fichier.

5. Dans la zone de texte **Arguments**, spécifiez les arguments nécessaires pour démarrer l’application.

6. Dans la zone de texte **Répertoire de travail**, spécifiez l’emplacement du répertoire.

7. Cliquez sur **OK**.

## <a name="see-also"></a>Voir aussi

[Configurer des sessions de performances](../profiling/configuring-performance-sessions.md)