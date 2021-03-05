---
description: Cette erreur se produit lorsque le service IIS Admin ne répond pas.
title: Une vérification de la sécurité a échoué, car le service d’administration IIS n’a pas répondu | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 42c0a5a1a1fdb3a997f46a6933df9c8681fe0498
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102147080"
---
# <a name="error-a-security-check-failed-because-the-iis-admin-service-did-not-respond"></a>Erreur : une vérification de la sécurité a échoué, car le service de l'administration IIS n'a pas répondu
Cette erreur se produit lorsque le service IIS Admin ne répond pas. Il s'agit généralement d'un problème relatif à l'installation IIS. En premier lieu, vérifiez que le service s’exécute à l’aide de l’outil **Services** des **Outils d’administration**.

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

- Réinstallez IIS, à l’aide de l’application **Ajout/Suppression de programmes** du Panneau de configuration.

- -ou-

- Supprimez IIS de votre ordinateur, à l’aide de l’application Ajout/Suppression de programmes du Panneau de configuration. Si vous avez supprimé IIS et que les problèmes persistent, examinez le Registre et assurez-vous que cette clé n'existe plus :

    `HKEY_CLASSES_ROOT\CLSID\{A9E69610-B80D-11D0-B9B9-00A0C922E750}`

     -ou-

- Désactivez le service de l'administration IIS, à l'aide du panneau de configuration Outils d'administration. Cela permet de désactiver IIS sur votre ordinateur.

     Après avoir exécuté l'une de ces trois opérations, redémarrez votre ordinateur.

     Pour plus d'informations, consultez la documentation IIS.

## <a name="see-also"></a>Voir aussi
- [Débogage d'applications Web : erreurs et dépannage](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
