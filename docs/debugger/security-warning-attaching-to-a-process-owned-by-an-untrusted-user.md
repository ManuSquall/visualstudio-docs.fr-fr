---
description: Cette boîte de dialogue d'avertissement s'affiche lorsque vous effectuez un attachement à un processus qui contient un code de niveau de confiance partiel ou qui appartient à un utilisateur non fiable, juste avant l'attachement.
title: 'Avertissement de sécurité : l’attachement à un processus appartenant à un utilisateur non approuvé peut être dangereux. Si les informations suivantes semblent suspectes ou si vous n’êtes pas sûr, ne vous attachez pas à ce processus | Microsoft Docs'
ms.date: 1/15/2021
ms.topic: conceptual
f1_keywords:
- vs.debug.attachsecuritywarning
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 52246c1e-a371-40a0-b756-a435cc51876f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9fe65e753a0e825eed0c09fdefc4e93168d27ecb
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102160314"
---
# <a name="security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process"></a>Avertissement de sécurité : l’attachement à un processus appartenant à un utilisateur non approuvé peut être dangereux. Si les informations suivantes semblent suspectes ou si vous avez des doutes, ne faites pas d’attachement à ce processus

Cette boîte de dialogue d'avertissement s'affiche lorsque vous effectuez un attachement à un processus qui contient un code de niveau de confiance partiel ou qui appartient à un utilisateur non fiable, juste avant l'attachement. Un processus non fiable qui contient un code malveillant a la possibilité d'endommager l'ordinateur qui effectue le débogage. Si vous avez des raisons de vous méfier du processus, cliquez sur **Annuler** pour empêcher le débogage.

Dans les scénarios IIS, vous pouvez voir cet avertissement si vous utilisez un pool d’applications personnalisé, qui n’est pas fiable.

Pour supprimer cet avertissement lors du débogage d’un scénario légitime :

1. Fermez Visual Studio.

1. Affectez la valeur `DisableAttachSecurityWarning` 1 à la clé de registre.

   Recherchez ou créez la clé sous `HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\<version>\Debugger` , puis affectez-lui la valeur 1.

   À compter de Visual Studio 2017, si vous souhaitez afficher les paramètres de Registre complets, vous devez charger la ruche de Registre privée. Pour plus d’informations, consultez Guide pratique [pour examiner le registre de Visual Studio 2017](https://github.com/microsoft/VSProjectSystem/blob/master/doc/overview/examine_registry.md). Veillez à décharger la ruche de Registre privée avant de démarrer Visual Studio.

1. Démarrez Visual Studio.

1. Après avoir terminé le débogage du scénario, réinitialisez la valeur à 0, et redémarrez Visual Studio.

Outre vous-même, les « utilisateurs de confiance » comprennent un ensemble d'utilisateurs standard qui sont généralement définis sur des ordinateurs sur lesquels le .NET Framework est installé, comme `aspnet`, `localsystem`, `networkservice` et `localservice`.

## <a name="uielement-list"></a>Liste des éléments de l'interface utilisateur

 Nom de l’assembly requis pour le débogage

 Utilisateur actuel de l’utilisateur

 Attacher une pression pour continuer à déboguer en attachant

 Ne pas attacher ne pas attacher au processus

## <a name="see-also"></a>Voir aussi
- [Joindre aux processus en cours d’exécution](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Sécurité du débogueur](../debugger/debugger-security.md)
