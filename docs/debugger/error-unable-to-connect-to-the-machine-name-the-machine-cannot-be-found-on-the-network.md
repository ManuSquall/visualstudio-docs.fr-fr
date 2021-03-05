---
title: Impossible de se connecter au nom de l’ordinateur &lt; &gt; . L’ordinateur est introuvable sur le réseau. | Microsoft Docs
description: 'Ce comportement se produit si l’une des conditions suivantes est vraie : (1) votre connexion à l’ordinateur distant a été interrompue. (2) votre compte d’utilisateur sur l’ordinateur distant est désactivé. (3) votre mot de passe sur l’ordinateur distant a expiré.'
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.remote.dcom_disabled
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- DCOM, unable to connect error
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5e0d83f043e020ad3c65ac0f986ec174fac95585
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102146429"
---
# <a name="error-unable-to-connect-to-the-machine-ltnamegt-the-machine-cannot-be-found-on-the-network"></a>Erreur : impossible de se connecter au nom de l’ordinateur &lt; &gt; . L’ordinateur est introuvable sur le réseau.
Ce problème se produit si l'une des conditions suivantes est remplie :

- Votre connexion à l'ordinateur distant a été interrompue.

- Votre compte d'utilisateur sur l'ordinateur distant est désactivé.

- Votre mot de passe sur l'ordinateur distant a expiré.

### <a name="to-resolve-this-behavior"></a>Pour résoudre ce problème

- Assurez-vous que l'ordinateur local et l'ordinateur distant se trouvent dans le même réseau. Pour cela, à l'aide de l'Explorateur Microsoft Windows (ou de l'Explorateur de fichiers), tentez d'accéder à l'ordinateur distant.

     — et —

- Assurez-vous que le compte d'utilisateur que vous utilisez pour vous connecter à l'ordinateur distant est activé.

     — et —

- Assurez-vous que le mot de passe que vous utilisez pour vous connecter à l'ordinateur distant est valide et n'a pas expiré.

## <a name="see-also"></a>Voir aussi
- [Débogage à distance](../debugger/remote-debugging.md)
- [Paramètres et préparation du débogueur](../debugger/debugger-settings-and-preparation.md)
