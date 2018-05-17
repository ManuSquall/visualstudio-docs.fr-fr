---
title: 'Avertissement de sécurité : Attachement à un processus appartenant à un utilisateur non fiable peut être dangereux. Si les informations ci-dessous semblent suspectes ou si vous n’êtes pas sûr, n’attachez pas ce processus | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 68d88e01dde07789467272db830cae45ca5d60c4
ms.sourcegitcommit: eefffa7ebe339d1297cdc12f51a813e7849d7e95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2018
---
# <a name="security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process"></a>Avertissement de sécurité : Attachement à un processus appartenant à un utilisateur non fiable peut être dangereux. Si les informations ci-dessous semblent suspectes ou si vous n’êtes pas sûr, n’attachez pas ce processus
Cette boîte de dialogue d'avertissement s'affiche lorsque vous effectuez un attachement à un processus qui contient un code de niveau de confiance partiel ou qui appartient à un utilisateur non fiable, juste avant l'attachement. Un processus non fiable qui contient un code malveillant a la possibilité d'endommager l'ordinateur qui effectue le débogage. Si vous avez raison méfier du processus, vous devez cliquer sur **Annuler** pour empêcher le débogage.  
  
 Pour supprimer cet avertissement lors du débogage d’un scénario légitime, fermez Visual Studio et la valeur de la valeur de cette clé de Registre 1 : `HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\<version>\Debugger\DisableAttachSecurityWarning`, puis redémarrez Visual Studio. Après avoir terminé le débogage du scénario, réinitialisez la valeur à 0, et redémarrez Visual Studio.  
  
 Outre vous-même, les « utilisateurs de confiance » comprennent un ensemble d'utilisateurs standard qui sont généralement définis sur des ordinateurs sur lesquels le .NET Framework est installé, comme `aspnet`, `localsystem`, `networkservice` et `localservice`.  
  
## <a name="uielement-list"></a>Liste des éléments d’interface  
 Name  
 Nom de l'assembly à déboguer  
  
 Utilisateur  
 Utilisateur actuel  
  
 Attach  
 Cliquez pour poursuivre le débogage après attachement  
  
 Ne pas attacher  
 Ne pas attacher au processus  
  
## <a name="see-also"></a>Voir aussi  
 [Attacher au processus en cours d’exécution](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Sécurité du débogueur](../debugger/debugger-security.md)