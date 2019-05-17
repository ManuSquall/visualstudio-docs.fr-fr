---
title: 'Procédure : Modifier une valeur de Registre | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.register.edit
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Registers window, editing register values
- register values
ms.assetid: e27b6bd8-e6d4-4f1d-8a86-9f4047bb1167
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 58094d505cf2fd3621b801040f0f71904796d86b
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63388419"
---
# <a name="how-to-edit-a-register-value-c-c-visual-basic-f"></a>Procédure : Modifier une valeur de Registre (C#, C++, Visual Basic, F#)

La fenêtre Registres est disponible uniquement si le débogage au niveau des adresses est activé dans la boîte de dialogue **Options**, nœud **Débogage**.

### <a name="to-change-the-value-of-a-register"></a>Pour modifier la valeur d'un Registre

1. Dans la fenêtre **Registres**, utilisez la touche Tab ou la souris pour placer le point d’insertion sur la valeur à modifier. Quand vous commencez à taper, le curseur doit se trouver en face de la valeur à remplacer.

2. Tapez la nouvelle valeur.

    > [!CAUTION]
    > Modifier des valeurs de registres (principalement des registres EIP et EBP) peut affecter l'exécution du programme.

    > [!CAUTION]
    > Modifier des valeurs à virgule flottante risque d’entraîner quelques légères imprécisions, dues à la conversion en binaire de la partie décimale des composants fractionnaires. Dans un Registre en virgule flottante, même une modification apparemment anodine risque d'entraîner des changements de certains bits de poids faible.

## <a name="see-also"></a>Voir aussi
- [Guide pratique pour utiliser la fenêtre Registres](../debugger/how-to-use-the-registers-window.md)