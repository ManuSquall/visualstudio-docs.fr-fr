---
title: Avertissement de code périmé, boîte de dialogue | Microsoft Docs
description: En savoir plus sur la boîte de dialogue d’avertissement relatif au code périmé, qui apparaît lorsque vous avez apporté des modifications au code natif que modifier & Continuer n’a pas pu appliquer immédiatement.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.ENC.stalecode
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Stale Code Warning dialog box
- code, stale code warning
- warnings, Stale Code Warning dialog box
- Edit and Continue, stale code
ms.assetid: 594b894c-e652-4e13-a980-9909473d5712
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f4ea2004680a60fcd2c90a57b19f719c0412ee53
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99861242"
---
# <a name="stale-code-warning-dialog-box"></a>Avertissement : code périmé (boîte de dialogue)

Cette boîte de dialogue s'affiche lorsque vous avez effectué des modifications au code natif que la fonction **Modifier & Continuer** n'a pas pu appliquer immédiatement. Par conséquent, une partie du code natif du frame de pile actif n'est plus à jour ; il est périmé. Pour plus d’informations, consultez [Modifier et continuer (C++)](edit-and-continue-visual-cpp.md).

**Ne plus afficher cette boîte de dialogue**

Si vous activez cette case à cocher, Modifier &amp; Continuer appliquera à l'avenir les modifications de code sans vous en demander l'autorisation. Vous pouvez réactiver cet avertissement à partir de la boîte de dialogue **Options** : dans le dossier **Débogage**, cliquez sur la page **Modifier et Continuer**, puis activez la case à cocher **Signaler le code périmé**.

## <a name="see-also"></a>Voir aussi

- [Modifications de code prises en charge (C++)](supported-code-changes-cpp.md)
- [Modifier & Continuer, Débogage, Boîte de dialogue Options](edit-and-continue.md)