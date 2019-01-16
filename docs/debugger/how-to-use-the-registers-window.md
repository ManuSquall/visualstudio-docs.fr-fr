---
title: Vue inscrire des valeurs dans le débogueur | Microsoft Docs
ms.custom: seodec18
ms.date: 11/19/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.registers
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- registers, debugging
- register contents
- flags, Registers window
- register groups
- debugging [Visual Studio], Registers window
- Registers window
ms.assetid: 2918ffa2-562f-40d6-9053-ef321bbeb767
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8622bb1288324429ad346834930559d1435ac6d5
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53867577"
---
# <a name="view-register-values-in-the-registers-window-c-c-visual-basic-f"></a>Vue inscrire des valeurs dans la fenêtre Registres (C#, C++, Visual Basic, F#)

Le **inscrit** fenêtre affiche le contenu du Registre lors du débogage de Visual Studio. Pour une introduction avancée aux concepts qui sous-tendent les registres et la **inscrit** fenêtre, consultez [éléments fondamentaux du débogage : la fenêtre Registres](../debugger/debugging-basics-registers-window.md).

> [!NOTE]
> Informations de Registre ne sont pas disponibles pour le script ou des applications SQL.

Pendant le débogage, inscrire la modification des valeurs pendant l’exécution de code dans votre application. Les valeurs qui ont été modifiés récemment s’affichent en rouge dans le **inscrit** fenêtre.

Pour réduire l’encombrement, la fenêtre **Registres** classe les registres en groupes, lesquels varient en fonction de la plateforme et du type de processeur. Vous pouvez afficher ou masquer des groupes de registres. Pour plus d'informations, voir [Procédure : Afficher et masquer les groupes de registres](../debugger/how-to-display-and-hide-register-groups.md).

Il est possible de modifier les valeurs des registres. Pour plus d'informations, voir [Procédure : Modifier une valeur de registre](../debugger/how-to-edit-a-register-value.md).

**Pour ouvrir la fenêtre Registres**

1. Activer le débogage au niveau des adresses, en sélectionnant **activer le débogage au niveau des adresses** dans **outils** (ou **déboguer**) > **Options**  >  **Débogage**.

1. Pendant le débogage en cours d’exécution ou à un point d’arrêt, sélectionnez **déboguer** > **Windows** > **inscrit**, ou appuyez sur **Alt** + **5**.

>[!NOTE]
>Boîtes de dialogue et les commandes de menu peuvent différer selon votre édition de Visual Studio ou ses paramètres. Pour modifier vos paramètres, sélectionnez **importation et exportation de paramètres** sur Visual Studio **outils** menu. Pour plus d’informations, consultez [Réinitialiser les paramètres](../ide/environment-settings.md#reset-settings).

### <a name="see-also"></a>Voir aussi

- [Principes de base pour le débogage : fenêtre Registres](../debugger/debugging-basics-registers-window.md)
- [Affichage des données dans le débogueur](../debugger/viewing-data-in-the-debugger.md)
