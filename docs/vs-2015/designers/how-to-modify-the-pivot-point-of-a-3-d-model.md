---
title: 'Procédure : Modifier le Point Pivot d’un modèle 3D | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: c20b4ec8-29f5-4ca5-bc39-d4548ca6f573
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f63c271e096793a03616356b9eb7229e4f823fbd
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60071783"
---
# <a name="how-to-modify-the-pivot-point-of-a-3-d-model"></a>Procédure : Modifier le Point Pivot d’un modèle 3D
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ce document montre comment utiliser l’éditeur de modèle pour modifier le *point pivot* d’un modèle 3D. Le point pivot est le point dans l’espace qui définit le centre de l’objet pour sa rotation et sa mise à l’échelle.  
  
 Ce document illustre cette activité :  
  
- Modification du point pivot d’un objet  
  
## <a name="modifying-the-pivot-point-of-a-3-d-model"></a>Modification du point pivot d’un modèle 3D  
 Vous pouvez redéfinir l’origine d’un modèle 3D en modifiant son point pivot.  
  
 Assurez-vous que la fenêtre **Propriétés** et la **Boîte à outils** sont affichées.  
  
#### <a name="to-modify-the-pivot-point-of-a-3-d-model"></a>Pour modifier le point pivot d’un modèle 3D  
  
1. Commencez par un modèle 3D existant, tel que celui qui est décrit dans [Comment : Créer un modèle 3D de base](../designers/how-to-create-a-basic-3-d-model.md).  
  
2. Passez en mode Pivot. Dans la barre d’outils **Mode de l’éditeur de modèle**, choisissez le bouton **Mode Pivot** pour activer le mode Pivot. Une zone apparaît autour du bouton **Mode Pivot** pour indiquer que l’éditeur de modèle est maintenant en mode Pivot. En mode Pivot, des opérations telles que la translation affectent le point pivot de l’objet et non la structure de l’objet dans l’espace universel.  
  
3. Modifiez le point pivot de l’objet. En mode **Sélection**, sélectionnez l’objet, puis, dans la barre d’outils **Visionneuse de modèle**, choisissez l’outil **Translater**. Une zone représentant le point pivot s’affiche sur l’aire de conception. Déplacez la zone pour modifier le point pivot de l’objet.  
  
    En déplaçant la zone, vous pouvez déplacer le point pivot dans les trois dimensions. Pour translater le point pivot sur un axe, déplacez la flèche correspondant à cet axe. La zone et les flèches deviennent jaunes pour indiquer l’axe concerné par la translation.  
  
    Vous pouvez également spécifier le point pivot à l’aide de la propriété **Translation du pivot** de la fenêtre **Propriétés**.  
  
   > [!TIP]
   >  Vous pouvez visionner l’effet du nouveau point pivot en pivotant l’objet. Pour le faire pivoter, utilisez l’outil **Rotation** ou modifiez la propriété **Rotation**.  
  
   Voici un modèle dont un point pivot est modifié :  
  
   ![Modèle de maison ayant un point pivot modifié](../designers/media/digit-modified-model.png "Digit-Modified-Model")  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour Créer un modèle 3D de base](../designers/how-to-create-a-basic-3-d-model.md)   
 [Éditeur de modèle](../designers/model-editor.md)
