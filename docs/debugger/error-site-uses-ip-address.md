---
title: 'Erreur : le site utilise l’adresse IP | Microsoft Docs'
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
ms.openlocfilehash: 96786efad0349dec7c9e8e9a02cca40af3668341
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72737498"
---
# <a name="error-site-uses-ip-address"></a>Erreur : le site utilise l'adresse IP
Cette erreur se produit lorsque le débogueur essaie de s'auto-attacher à une application Web qui utilise une adresse IP. C’est le cas si vous transformez **Identification de site web** en **Utiliser une adresse IP spécifique** dans IIS.

 Pour que l'auto-attachement fonctionne, vous devez créer le projet avec l'adresse IP spécifique plutôt qu'avec seulement le nom de l'ordinateur. Sinon, le débogueur transformera le nom de l'ordinateur en localhost, ce qui empêchera d'envoyer le verbe de débogage à IIS.

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

1. Utilisez plutôt la procédure d’attachement manuel (dans le menu Déboguer, choisissez **Attacher au processus**).

     - ou -

2. Modifiez le paramètre **Identification de site web d’IIS**.

## <a name="see-also"></a>Voir aussi
- [Débogage d’applications web : erreurs et dépannage](../debugger/debugging-web-applications-errors-and-troubleshooting.md)