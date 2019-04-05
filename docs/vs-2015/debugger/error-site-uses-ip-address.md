---
title: 'Erreur : Site utilise l’adresse IP | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.webdbg_siteusesipaddress
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
ms.assetid: b2b8ddc8-746d-46e3-87a6-b956b1ee048d
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e040c45079c9e4b82337cbd1e4b5d7d8306e1a32
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58947776"
---
# <a name="error-site-uses-ip-address"></a>Erreur : le site utilise l’adresse IP
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette erreur se produit lorsque le débogueur essaie de s'auto-attacher à une application Web qui utilise une adresse IP. C’est le cas si vous transformez **Identification de site web** en **Utiliser une adresse IP spécifique** dans IIS.  
  
 Pour que l'auto-attachement fonctionne, vous devez créer le projet avec l'adresse IP spécifique plutôt qu'avec seulement le nom de l'ordinateur. Sinon, le débogueur transformera le nom de l'ordinateur en localhost, ce qui empêchera d'envoyer le verbe de débogage à IIS.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1.  Utilisez plutôt la procédure d’attachement manuel (dans le menu Déboguer, choisissez **Attacher au processus**).  
  
     - ou -  
  
2.  Modifiez le paramètre **Identification de site web d’IIS**.  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage d’applications web : erreurs et dépannage](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
