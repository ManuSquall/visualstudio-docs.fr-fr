---
title: 'Procédure : Modifier une valeur de Registre | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.register.edit
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- Registers window, editing register values
- register values
ms.assetid: e27b6bd8-e6d4-4f1d-8a86-9f4047bb1167
caps.latest.revision: 29
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0ea1e932f7651439dcb9a1ff85094bd30e5239bb
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60116149"
---
# <a name="how-to-edit-a-register-value"></a>Procédure : Modifier une valeur de Registre
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La fenêtre Registres est disponible uniquement si le débogage au niveau des adresses est activé dans la boîte de dialogue **Options**, nœud **Débogage**.  
  
### <a name="to-change-the-value-of-a-register"></a>Pour modifier la valeur d'un Registre  
  
1. Dans la fenêtre **Registres**, utilisez la touche Tab ou la souris pour placer le point d’insertion sur la valeur à modifier. Quand vous commencez à taper, le curseur doit se trouver en face de la valeur à remplacer.  
  
2. Tapez la nouvelle valeur.  
  
    > [!CAUTION]
    >  Modifier des valeurs de registres (principalement des registres EIP et EBP) peut affecter l'exécution du programme.  
  
    > [!CAUTION]
    >  Modifier des valeurs à virgule flottante risque d’entraîner quelques légères imprécisions, dues à la conversion en binaire de la partie décimale des composants fractionnaires. Dans un Registre en virgule flottante, même une modification apparemment anodine risque d'entraîner des changements de certains bits de poids faible.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour utiliser la fenêtre Registres](../debugger/how-to-use-the-registers-window.md)
