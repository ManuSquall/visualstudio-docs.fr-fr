---
title: 'Erreur : une vérification de la sécurité a échoué, car le service d’administration IIS n’a pas répondu | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.iis_not_responding
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
ms.openlocfilehash: f668de3d7c7e9a8bd075beb972199cf849feea65
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72737870"
---
# <a name="error-a-security-check-failed-because-the-iis-admin-service-did-not-respond"></a>Erreur : une vérification de la sécurité a échoué, car le service de l'administration IIS n'a pas répondu
Cette erreur se produit lorsque le service IIS Admin ne répond pas. Il s'agit généralement d'un problème relatif à l'installation IIS. En premier lieu, vérifiez que le service s’exécute à l’aide de l’outil **Services** des **Outils d’administration**.

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Réinstallez IIS, à l’aide de l’application **Ajout/Suppression de programmes** du Panneau de configuration.

- ou

- Supprimez IIS de votre ordinateur, à l’aide de l’application Ajout/Suppression de programmes du Panneau de configuration. Si vous avez supprimé IIS et que les problèmes persistent, examinez le Registre et assurez-vous que cette clé n'existe plus :

    `HKEY_CLASSES_ROOT\CLSID\{A9E69610-B80D-11D0-B9B9-00A0C922E750}`

     ou

- Désactivez le service de l'administration IIS, à l'aide du panneau de configuration Outils d'administration. Cela permet de désactiver IIS sur votre ordinateur.

     Après avoir exécuté l'une de ces trois opérations, redémarrez votre ordinateur.

     Pour plus d'informations, consultez la documentation IIS.

## <a name="see-also"></a>Voir aussi
- [Débogage d’applications web : erreurs et dépannage](../debugger/debugging-web-applications-errors-and-troubleshooting.md)