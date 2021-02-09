---
title: Impossible de se connecter au nom de l’ordinateur &lt; &gt; . L’ordinateur est introuvable sur le réseau. | Microsoft Docs
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
ms.openlocfilehash: dcf52a258a46f44afaf6e890531496f57b11fc24
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99871063"
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