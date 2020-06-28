---
title: 'Erreur : le site utilise l’adresse IP | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: error-reference
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
ms.openlocfilehash: 58db12ba9dbbc9526ac86262a6be5b2c0a7f765e
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85460544"
---
# <a name="error-site-uses-ip-address"></a>Erreur : le site utilise l'adresse IP
Cette erreur se produit lorsque le débogueur essaie de s'auto-attacher à une application Web qui utilise une adresse IP. C’est le cas si vous transformez **Identification de site web** en **Utiliser une adresse IP spécifique** dans IIS.

 Pour que l'auto-attachement fonctionne, vous devez créer le projet avec l'adresse IP spécifique plutôt qu'avec seulement le nom de l'ordinateur. Sinon, le débogueur transformera le nom de l'ordinateur en localhost, ce qui empêchera d'envoyer le verbe de débogage à IIS.

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

1. Utilisez plutôt la procédure d’attachement manuel (dans le menu Déboguer, choisissez **Attacher au processus**).

     Ou

2. Modifiez le paramètre **Identification de site web d’IIS**.

## <a name="see-also"></a>Voir aussi
- [Débogage d'applications Web : erreurs et dépannage](../debugger/debugging-web-applications-errors-and-troubleshooting.md)