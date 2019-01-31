---
title: 'Erreur : Site utilise l’adresse IP | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.webdbg_siteusesipaddress
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d8aa34553f4fb6d4524357f830dbbeabe3296354
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "54981114"
---
# <a name="error-site-uses-ip-address"></a>Erreur : le site utilise l’adresse IP
Cette erreur se produit lorsque le débogueur essaie de s'auto-attacher à une application Web qui utilise une adresse IP. C’est le cas si vous transformez **Identification de site web** en **Utiliser une adresse IP spécifique** dans IIS.  
  
 Pour que l'auto-attachement fonctionne, vous devez créer le projet avec l'adresse IP spécifique plutôt qu'avec seulement le nom de l'ordinateur. Sinon, le débogueur transformera le nom de l'ordinateur en localhost, ce qui empêchera d'envoyer le verbe de débogage à IIS.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1.  Utilisez plutôt la procédure d’attachement manuel (dans le menu Déboguer, choisissez **Attacher au processus**).  
  
     - ou -  
  
2.  Modifiez le paramètre **Identification de site web d’IIS**.  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage d’applications web : erreurs et dépannage](../debugger/debugging-web-applications-errors-and-troubleshooting.md)