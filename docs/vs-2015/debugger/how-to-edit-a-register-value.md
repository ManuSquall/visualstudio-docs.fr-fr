---
title: 'Comment : modifier une valeur de Registre | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c6846fc8ae093f3f63a0b9caceee7d0a0c23767f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49196155"
---
# <a name="how-to-edit-a-register-value"></a>Comment : modifier une valeur de Registre
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La fenêtre Registres est disponible uniquement si le débogage au niveau des adresses est activé dans le **Options** boîte de dialogue, **débogage** nœud.  
  
### <a name="to-change-the-value-of-a-register"></a>Pour modifier la valeur d'un Registre  
  
1.  Dans le **inscrit** fenêtre, utilisez la touche TAB ou la souris pour déplacer l’insertion de point à la valeur que vous souhaitez modifier. Quand vous commencez à taper, le curseur doit se trouver en face de la valeur à remplacer.  
  
2.  Tapez la nouvelle valeur.  
  
    > [!CAUTION]
    >  Modifier des valeurs de registres (principalement des registres EIP et EBP) peut affecter l'exécution du programme.  
  
    > [!CAUTION]
    >  Modifier des valeurs à virgule flottante risque d'entraîner quelques légères imprécisions, dues à la conversion en binaire de la partie décimale des composants fractionnaires. Dans un Registre en virgule flottante, même une modification apparemment anodine risque d'entraîner des changements de certains bits de poids faible.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour utiliser la fenêtre Registres](../debugger/how-to-use-the-registers-window.md)





