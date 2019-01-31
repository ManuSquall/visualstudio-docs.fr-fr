---
title: 'Erreur : Impossible de se connecter à la machine &lt;nom&gt;. L’ordinateur est introuvable sur le réseau. | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9531151402b5070aaa3a680e09e0082b4e1237f0
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54972038"
---
# <a name="error-unable-to-connect-to-the-machine-ltnamegt-the-machine-cannot-be-found-on-the-network"></a>Erreur : Impossible de se connecter à la machine &lt;nom&gt;. L’ordinateur est introuvable sur le réseau.
Ce problème se produit si l'une des conditions suivantes est remplie :  
  
-   Votre connexion à l'ordinateur distant a été interrompue.  
  
-   Votre compte d'utilisateur sur l'ordinateur distant est désactivé.  
  
-   Votre mot de passe sur l'ordinateur distant a expiré.  
  
### <a name="to-resolve-this-behavior"></a>Pour résoudre ce problème  
  
-   Assurez-vous que l'ordinateur local et l'ordinateur distant se trouvent dans le même réseau. Pour cela, à l'aide de l'Explorateur Microsoft Windows (ou de l'Explorateur de fichiers), tentez d'accéder à l'ordinateur distant.  
  
     — et —  
  
-   Assurez-vous que le compte d'utilisateur que vous utilisez pour vous connecter à l'ordinateur distant est activé.  
  
     — et —  
  
-   Assurez-vous que le mot de passe que vous utilisez pour vous connecter à l'ordinateur distant est valide et n'a pas expiré.  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage distant](../debugger/remote-debugging.md)   
 [Paramètres et préparation du débogueur](../debugger/debugger-settings-and-preparation.md)