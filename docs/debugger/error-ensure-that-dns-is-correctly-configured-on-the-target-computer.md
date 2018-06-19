---
title: 'Erreur : Assurez-vous que DNS est correctement configuré sur l’ordinateur cible | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.callback_dns_failed
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d50eed9a4c769b2e8b58cbdf35c6e10b57ae9b0c
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31479635"
---
# <a name="error-ensure-that-dns-is-correctly-configured-on-the-target-computer"></a>Erreur : Assurez-vous que DNS est correctement configuré sur l'ordinateur cible
Si vous essayez d'effectuer un débogage distant, vous risquez de recevoir ce message d'erreur :  
  
```  
Error: The Visual Studio Remote Debugger on the target computer cannot connect back to this computer. Ensure that DNS is correctly configured on the target computer.  
```  
  
 Cette erreur se produit lorsque l'ordinateur cible ne peut pas résoudre le nom de l'ordinateur hôte du débogueur Visual Studio. Vérifiez les paramètres DNS sur l'ordinateur cible.  
  
-   Pour plus d’informations sur l’affichage de vos paramètres DNS dans Windows 8.1, Vista, Windows 7, Windows Server 2012, Windows Server 2008 ou Windows Server 2008 R2, cela : sur le **Démarrer** menu, choisissez **aide et Support** , puis recherchez **changer les paramètres TCP/IP**.  
  
-   Pour plus d’informations, accédez à [le site web Microsoft Windows](http://go.microsoft.com/fwlink/?LinkId=252720) et recherchez **changer les paramètres TCP/IP**.  
  
 Si vous ne pouvez pas résoudre le problème DNS, vous pouvez essayer d'exécuter le débogueur distant sous un compte différent. Cette erreur se produit uniquement lorsque vous exécutez le débogueur distant sous le compte système local ou le compte de service réseau. Si vous exécutez le débogueur distant sous un autre compte, il peut utiliser l'authentification NTLM, qui ne nécessite pas de DNS. . Pour connaître la procédure, consultez [erreur : service du débogueur distant Visual Studio sur l’ordinateur cible ne peut pas se reconnecter à cet ordinateur](../debugger/error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md).