---
title: Une erreur DCOM s’est produite lors de la tentative de contact de l’ordinateur distant. Accès refusé.
titleSuffix: ''
description: "'Une erreur DCOM s’est produite lors de la tentative de contact de l’ordinateur distant. Accès refusé.» Affichez les informations relatives à cette référence des erreurs de débogage distant Visual Studio."
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.remote.dcom_access_denied
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- remote debugging, DCOM error
- remote DCOM access denied error
- DCOM, access errors
ms.assetid: 9d7dfc1b-9fe0-4f54-9c50-9c0e0f8358c5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c430462a224cb4604c09984a5397e540ce752b8a
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2020
ms.locfileid: "97729195"
---
# <a name="a-dcom-error-occurred-trying-to-contact-the-remote-computer-access-is-denied"></a>Une erreur DCOM s’est produite lors de la tentative de contact de l’ordinateur distant. Accès refusé.
Le débogage distant utilise DCOM pour les communications entre l’ordinateur hôte et l’ordinateur distant dans les situations suivantes :

- Le débogueur est défini sur **Mode de compatibilité natif** ou l’option **Mode de compatibilité managé** est activée dans la page **Outils > Options > Débogage**.

- Vous déboguez du code C++ managé (C++/CLI).

- Dans Visual Studio 2013, l’option **Activer Modifier & Continuer natif** est activée dans la page **Outils &gt; Options &gt; Débogage**.

- Quelques scénarios de débogage tiers

  Cette erreur se produit lorsque le processus Visual Studio ne peut pas s'authentifier (ou que les informations d'identification fournies ont été considérées inappropriées) lors du processus du débogueur distant sur DCOM. Une ou plusieurs des solutions suivantes peuvent résoudre le problème :

- Désactivez  **Mode de compatibilité natif** et **Mode de compatibilité managé**.

- Dans Visual Studio 2013, désactivez **Activer Modifier &amp; Continuer natif**.

- Redémarrez les deux ordinateurs.

- Si le débogage distant requiert la saisie des informations d'identification, activez l'option pour enregistrer les informations d'identification.

## <a name="see-also"></a>Voir aussi

- [Erreurs de débogage distant et dépannage](../debugger/remote-debugging-errors-and-troubleshooting.md)
- [Débogage à distance](../debugger/remote-debugging.md)