---
title: Impossible d’initier la communication DCOM | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.unmarshal_server_failed
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 00846f0ef0593ec7d12c657a40079ff1cdfb0bb5
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90851435"
---
# <a name="error-unable-to-initiate-dcom-communication"></a>Erreur : Impossible d'initier les communications DCOM
Une erreur DCOM s'est produite lorsque l'ordinateur local a tenté de communiquer avec l'ordinateur distant. Cette erreur est provoquée par un pare-feu sur le serveur distant ou une authentification Windows interrompue sur l'ordinateur distant.

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Si le pare-feu Windows est activé sur l’ordinateur distant, consultez [débogage distant](../debugger/remote-debugging.md) pour obtenir des instructions sur la configuration du pare-feu pour le débogage local.

- Pour restaurer l'authentification Windows, tentez de redémarrer les deux ordinateurs. Vérifiez si les journaux des événements de l'ordinateur local ou distant contiennent des erreurs Kerberos et contactez les administrateurs de domaines pour les problèmes connus.

## <a name="see-also"></a>Voir aussi
- [Débogage à distance](../debugger/remote-debugging.md)