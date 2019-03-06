---
title: 'Comment : modifier une valeur de Registre | Microsoft Docs'
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
ms.openlocfilehash: 430ee5d0b36196c85d7c81b63503bfcc471d7664
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56717108"
---
# <a name="how-to-edit-a-register-value-c-c-visual-basic-f"></a>Comment : modifier une valeur de Registre (C#, C++, Visual Basic, F#)

La fenêtre Registres est disponible uniquement si le débogage au niveau des adresses est activé dans la boîte de dialogue **Options**, nœud **Débogage**.

### <a name="to-change-the-value-of-a-register"></a>Pour modifier la valeur d'un Registre

1.  Dans la fenêtre **Registres**, utilisez la touche Tab ou la souris pour placer le point d’insertion sur la valeur à modifier. Quand vous commencez à taper, le curseur doit se trouver en face de la valeur à remplacer.

2.  Tapez la nouvelle valeur.

    > [!CAUTION]
    >  Modifier des valeurs de registres (principalement des registres EIP et EBP) peut affecter l'exécution du programme.

    > [!CAUTION]
    >  Modifier des valeurs à virgule flottante risque d’entraîner quelques légères imprécisions, dues à la conversion en binaire de la partie décimale des composants fractionnaires. Dans un Registre en virgule flottante, même une modification apparemment anodine risque d'entraîner des changements de certains bits de poids faible.

## <a name="see-also"></a>Voir aussi
- [Guide pratique pour utiliser la fenêtre Registres](../debugger/how-to-use-the-registers-window.md)