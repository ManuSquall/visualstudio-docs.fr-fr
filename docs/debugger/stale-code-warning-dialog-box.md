---
title: Avertissement de code périmé, boîte de dialogue | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dba38e5b5d9f7a2be710cad58d6f2297dd03a412
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72729543"
---
# <a name="stale-code-warning-dialog-box"></a>Avertissement : code périmé (boîte de dialogue)

Cette boîte de dialogue s'affiche lorsque vous avez effectué des modifications au code natif que la fonction **Modifier & Continuer** n'a pas pu appliquer immédiatement. Par conséquent, une partie du code natif du frame de pile actif n'est plus à jour ; il est périmé. Pour plus d’informations, consultez [Modifier et continuer (C++)](edit-and-continue-visual-cpp.md).

**Ne plus afficher cette boîte de dialogue**

Si vous activez cette case à cocher, Modifier &amp; Continuer appliquera à l'avenir les modifications de code sans vous en demander l'autorisation. Vous pouvez réactiver cet avertissement à partir de la boîte de dialogue **Options** : dans le dossier **Débogage**, cliquez sur la page **Modifier et Continuer**, puis activez la case à cocher **Signaler le code périmé**.

## <a name="see-also"></a>Voir aussi

- [Modifications du code prises en charge (C++)](supported-code-changes-cpp.md)
- [Modifier & Continuer, Débogage, Boîte de dialogue Options](edit-and-continue.md)