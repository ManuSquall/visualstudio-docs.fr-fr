---
title: Modifier une valeur de Registre | Microsoft Docs
description: Apprenez à modifier le contenu d’un registre en modifiant sa valeur dans la fenêtre registres (disponible uniquement si le débogage au niveau de l’adresse est activé).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4187be3bd4d5d2099374acea58d86bd093538ef7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99917378"
---
# <a name="how-to-edit-a-register-value-c-c-visual-basic-f"></a>Comment : modifier une valeur de Registre (C#, C++, Visual Basic, F #)

La fenêtre Registres est disponible uniquement si le débogage au niveau des adresses est activé dans la boîte de dialogue **Options**, nœud **Débogage**.

### <a name="to-change-the-value-of-a-register"></a>Pour modifier la valeur d'un Registre

1. Dans la fenêtre **Registres**, utilisez la touche Tab ou la souris pour placer le point d’insertion sur la valeur à modifier. Quand vous commencez à taper, le curseur doit se trouver en face de la valeur à remplacer.

2. Tapez la nouvelle valeur.

    > [!CAUTION]
    > Modifier des valeurs de registres (principalement des registres EIP et EBP) peut affecter l'exécution du programme.

    > [!CAUTION]
    > Modifier des valeurs à virgule flottante risque d’entraîner quelques légères imprécisions, dues à la conversion en binaire de la partie décimale des composants fractionnaires. Dans un Registre en virgule flottante, même une modification apparemment anodine risque d'entraîner des changements de certains bits de poids faible.

## <a name="see-also"></a>Voir aussi
- [Comment : utiliser la fenêtre Registres](../debugger/how-to-use-the-registers-window.md)