---
title: Afficher et masquer les groupes de registres | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.debug.registergroups
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Registers window, displaying and hiding register groups
- register groups, displaying and hiding
ms.assetid: 6be5dfb4-4cfe-4daf-b538-60405640857d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0a75af7d7ef279fdd3ca82ea9dced941106f0275
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90852359"
---
# <a name="how-to-display-and-hide-register-groups-c-c-visual-basic-f"></a>Comment : afficher et masquer des groupes de registres (C#, C++, Visual Basic, F #)

La fenêtre **Registres** est disponible uniquement si le débogage au niveau des adresses est activé dans la boîte de dialogue **Options**, nœud **Débogage**, catégorie **Général**.

Pour des raisons de clarté, la fenêtre **Registres** classe les registres par groupes. Si vous cliquez avec le bouton droit sur la fenêtre **Registres**, un menu contextuel contenant ces groupes s’affiche. Vous pouvez afficher ou masquer les groupes selon vos besoins en suivant la procédure ci-dessous.

> [!NOTE]
> Les boîtes de dialogue et les commandes de menu affichées peuvent différer de celles décrites dans l'Aide selon les paramètres actifs ou le mode d'édition. Pour modifier vos paramètres, choisissez **Paramètres d'importation et d'exportation** dans le menu **Outils** . Pour plus d’informations, consultez [Réinitialiser les paramètres](../ide/environment-settings.md#reset-settings).

## <a name="display-or-hide-register-groups"></a>Afficher ou masquer les groupes de registres

1. Cliquez avec le bouton droit sur la fenêtre **Registres**.

2. Dans le menu contextuel, sélectionnez les groupes de registres à afficher ou masquer.

     Les groupes de registres qui ne sont pas pris en charge par le matériel sur lequel vous effectuez le débogage sont désactivés dans le menu contextuel et ne peuvent pas être sélectionnés.

## <a name="see-also"></a>Voir aussi

- [Comment : utiliser la fenêtre Registres](../debugger/how-to-use-the-registers-window.md)