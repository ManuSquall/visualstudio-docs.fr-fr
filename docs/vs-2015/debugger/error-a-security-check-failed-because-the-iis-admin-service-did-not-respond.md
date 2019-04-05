---
title: 'Erreur : Une vérification de sécurité a échoué, car le Service IIS Admin n’a pas répondu. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.iis_not_responding
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
ms.assetid: 6060e94e-71dc-49f2-bb59-2584216eadbf
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9434ad3d67b8cf724323bdb9614d3bfdbd569882
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58947879"
---
# <a name="error-a-security-check-failed-because-the-iis-admin-service-did-not-respond"></a>Erreur : Une vérification de la sécurité a échoué, car le service de l’administration IIS n’a pas répondu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cette erreur se produit lorsque le service IIS Admin ne répond pas. Il s'agit généralement d'un problème relatif à l'installation IIS. En premier lieu, vérifiez que le service s’exécute à l’aide de l’outil **Services** des **Outils d’administration**.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Réinstallez IIS, à l’aide de l’application **Ajout/Suppression de programmes** du Panneau de configuration.  
  
-   - ou -  
  
-   Supprimez IIS de votre ordinateur, à l’aide de l’application Ajout/Suppression de programmes du Panneau de configuration. Si vous avez supprimé IIS et que les problèmes persistent, examinez le Registre et assurez-vous que cette clé n'existe plus :  
  
    ```  
    HKEY_CLASSES_ROOT\CLSID\{A9E69610-B80D-11D0-B9B9-00A0C922E750}  
    ```  
  
     - ou -  
  
-   Désactivez le service de l'administration IIS, à l'aide du panneau de configuration Outils d'administration. Cela permet de désactiver IIS sur votre ordinateur.  
  
     Après avoir exécuté l'une de ces trois opérations, redémarrez votre ordinateur.  
  
     Pour plus d'informations, consultez la documentation IIS.  
  
## <a name="see-also"></a>Voir aussi  
 [Débogage d’applications web : erreurs et dépannage](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
