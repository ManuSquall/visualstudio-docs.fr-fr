---
title: 'Avertissement de sécurité : L’attachement à un processus appartenant à un utilisateur non approuvé peut être dangereux. Si les informations suivantes semblent suspectes ou si vous n’êtes pas sûr, ne vous attachez pas à ce processus | Microsoft Docs'
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 05b78ea0ca06a0ba9670e61cc065cf539ea21ebc
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72729777"
---
# <a name="security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process"></a>Avertissement de sécurité : L’attachement à un processus appartenant à un utilisateur non approuvé peut être dangereux. Si les informations suivantes semblent suspectes ou si vous avez des doutes, ne faites pas d’attachement à ce processus
Cette boîte de dialogue d'avertissement s'affiche lorsque vous effectuez un attachement à un processus qui contient un code de niveau de confiance partiel ou qui appartient à un utilisateur non fiable, juste avant l'attachement. Un processus non fiable qui contient un code malveillant a la possibilité d'endommager l'ordinateur qui effectue le débogage. Si vous avez des raisons de vous méfier du processus, cliquez sur **Annuler** pour empêcher le débogage.

 Pour supprimer cet avertissement lors du débogage d’un scénario légitime, fermez Visual Studio, puis définissez la valeur de cette clé de Registre sur 1 : `HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\<version>\Debugger\DisableAttachSecurityWarning`, puis redémarrez Visual Studio. Après avoir terminé le débogage du scénario, réinitialisez la valeur à 0, et redémarrez Visual Studio.

 Outre vous-même, les « utilisateurs de confiance » comprennent un ensemble d'utilisateurs standard qui sont généralement définis sur des ordinateurs sur lesquels le .NET Framework est installé, comme `aspnet`, `localsystem`, `networkservice` et `localservice`.

## <a name="uielement-list"></a>Liste des éléments d’interface
 Nom de l’assembly requis pour le débogage

 Utilisateur actuel de l’utilisateur

 Attacher une pression pour continuer à déboguer en attachant

 Ne pas attacher ne pas attacher au processus

## <a name="see-also"></a>Voir aussi
- [S’attacher à des processus en cours d’exécution](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Sécurité du débogueur](../debugger/debugger-security.md)