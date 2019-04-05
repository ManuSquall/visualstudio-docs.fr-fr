---
title: Périmées de boîte de dialogue Avertissement de Code | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.ENC.stalecode
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Stale Code Warning dialog box
- code, stale code warning
- warnings, Stale Code Warning dialog box
- Edit and Continue, stale code
ms.assetid: 594b894c-e652-4e13-a980-9909473d5712
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: adb8bfdf5edb4f6aa04a53f051fafa9ef3793e10
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58953785"
---
# <a name="stale-code-warning-dialog-box"></a>Avertissement : code périmé (boîte de dialogue)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette boîte de dialogue s'affiche lorsque vous avez effectué des modifications au code natif que la fonction **Modifier & Continuer** n'a pas pu appliquer immédiatement. Par conséquent, une partie du code natif du frame de pile actif n'est plus à jour ; il est périmé. Pour plus d'informations, voir [Procédure : Travailler avec le Code périmé](http://msdn.microsoft.com/c7536e95-66a6-44a0-995d-3fe5035250b4).  
  
 **Ne plus afficher cette boîte de dialogue**  
 Si vous activez cette case à cocher, Modifier &amp; Continuer appliquera à l'avenir les modifications de code sans vous en demander l'autorisation. Vous pouvez réactiver cet avertissement à partir de la boîte de dialogue **Options** : dans le dossier **Débogage**, cliquez sur la page **Modifier et Continuer**, puis activez la case à cocher **Signaler le code périmé**.  
  
## <a name="see-also"></a>Voir aussi  
 [Modifications de Code prises en charge (C++)](../debugger/supported-code-changes-cpp.md)   
 [Modifier & Continuer, Débogage, Boîte de dialogue Options](http://msdn.microsoft.com/library/009d225f-ef65-463f-a146-e4c518f86103)
