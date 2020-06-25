---
title: Afficher les valeurs de Registre dans le débogueur | Microsoft Docs
ms.custom: seodec18
ms.date: 11/19/2018
ms.topic: how-to
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ed60b21d7c8e90e18b389a29c3343713ac8ece3d
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2020
ms.locfileid: "85348572"
---
# <a name="view-register-values-in-the-registers-window-c-c-visual-basic-f"></a>Afficher les valeurs de Registre dans la fenêtre registres (C#, C++, Visual Basic, F #)

La fenêtre **registres** affiche le contenu du registre lors du débogage de Visual Studio. Pour une introduction avancée aux concepts qui sous-tendent les registres et la **inscrit** fenêtre, consultez [éléments fondamentaux du débogage : la fenêtre Registres](../debugger/debugging-basics-registers-window.md).

> [!NOTE]
> Les informations de registre ne sont pas disponibles pour les applications script ou SQL.

Pendant le débogage, les valeurs de Registre sont modifiées au fur et à mesure que le code s’exécute dans votre application. Les valeurs qui ont changé récemment s’affichent en rouge dans la fenêtre **registres** .

Pour réduire l’encombrement, la fenêtre **Registres** classe les registres en groupes, lesquels varient en fonction de la plateforme et du type de processeur. Vous pouvez afficher ou masquer des groupes de registres. Pour plus d’informations, consultez [Comment : afficher et masquer les groupes de registres](../debugger/how-to-display-and-hide-register-groups.md).

Pour plus d’informations sur les indicateurs que vous voyez dans la fenêtre **registres** , consultez [à propos de la fenêtre registres](../debugger/debugging-basics-registers-window.md)

Il est possible de modifier les valeurs des registres. Pour plus d’informations, consultez [Comment : modifier une valeur de Registre](../debugger/how-to-edit-a-register-value.md).

**Pour ouvrir la fenêtre registres**

1. Activez le débogage au niveau de l’adresse, en sélectionnant **activer le débogage au niveau** de l’adresse dans **Outils** (ou **débogage**) > **options**de  >  **débogage**.

1. Pendant que le débogage est en cours d’exécution ou à un point d’arrêt, sélectionnez **Déboguer**les  >  **Windows**  >  **registres**Windows ou appuyez sur **ALT** + **5**.

>[!NOTE]
>Les boîtes de dialogue et les commandes de menu peuvent différer en fonction de votre édition ou de vos paramètres Visual Studio. Pour modifier vos paramètres, sélectionnez **importation et exportation de paramètres** dans le menu **Outils** de Visual Studio. Pour plus d’informations, consultez [Réinitialiser les paramètres](../ide/environment-settings.md#reset-settings).

### <a name="see-also"></a>Voir aussi

- [Concepts de base du débogage : fenêtre registres](../debugger/debugging-basics-registers-window.md)
- [Affichage des données dans le débogueur](../debugger/viewing-data-in-the-debugger.md)
