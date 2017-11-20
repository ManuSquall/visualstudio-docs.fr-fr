---
title: "Erreur : Impossible de se connecter à l’ordinateur &lt;nom&gt;. Impossible de trouver l’ordinateur sur le réseau. | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.remote.dcom_disabled
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords: DCOM, unable to connect error
ms.assetid: b584b5db-ef52-45ed-8561-1314da3cc5b8
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e8ed30ca3baeb29f92c4d5f02b64c581ef9a37a7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="error-unable-to-connect-to-the-machine-ltnamegt-the-machine-cannot-be-found-on-the-network"></a>Erreur : Impossible de se connecter à l’ordinateur &lt;nom&gt;. Impossible de trouver l’ordinateur sur le réseau.
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