---
title: Avertissement de code périmé, boîte de dialogue | Microsoft Docs
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
ms.openlocfilehash: a89738446bf8c08680835ddccb7efa30c2f740f5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65694701"
---
# <a name="stale-code-warning-dialog-box"></a>Avertissement : code périmé (boîte de dialogue)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette boîte de dialogue s'affiche lorsque vous avez effectué des modifications au code natif que la fonction **Modifier & Continuer** n'a pas pu appliquer immédiatement. Par conséquent, une partie du code natif du frame de pile actif n'est plus à jour ; il est périmé. Pour plus d’informations, consultez [Comment : utiliser du code périmé](https://msdn.microsoft.com/c7536e95-66a6-44a0-995d-3fe5035250b4).  
  
 **Ne plus afficher cette boîte de dialogue**  
 Si vous activez cette case à cocher, Modifier &amp; Continuer appliquera à l'avenir les modifications de code sans vous en demander l'autorisation. Vous pouvez réactiver cet avertissement à partir de la boîte de dialogue **Options** : dans le dossier **Débogage**, cliquez sur la page **Modifier et Continuer**, puis activez la case à cocher **Signaler le code périmé**.  
  
## <a name="see-also"></a>Voir aussi  
 [Modifications du code prises en charge (C++)](../debugger/supported-code-changes-cpp.md)   
 [Modifier & Continuer, Débogage, Boîte de dialogue Options](https://msdn.microsoft.com/library/009d225f-ef65-463f-a146-e4c518f86103)
