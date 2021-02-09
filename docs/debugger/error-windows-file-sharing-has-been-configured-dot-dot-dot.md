---
title: Le partage de fichiers Windows a été configuré... | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.remote_credentials_prohibited
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d1cc81c8ef39aeeb716a26209a4aded0c69dcf95
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99870868"
---
# <a name="error-windows-file-sharing-has-been-configured"></a>Erreur : Le partage de fichiers Windows a été configuré...
Le partage de fichiers Windows a été configuré pour que vous vous connectiez sur l'ordinateur distant avec un autre nom d'utilisateur. Cela est incompatible avec le débogage distant

 La configuration actuelle de partage de fichiers prévoit de pouvoir se connecter à l'ordinateur distant à l'aide d'un nom d'utilisateur différent. Le débogage distant n'est pas possible dans ce scénario.

 Pour corriger cette erreur, ouvrez une session sur l'ordinateur à l'aide de l'autre nom de compte, ou modifiez le partage de fichiers pour utiliser le nom de compte sous lequel vous déboguez.

 Si vous souhaitez vous connecter à l'ordinateur distant à l'aide de ce nom d'utilisateur, vous devez d'abord vous déconnecter de l'ordinateur distant.

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

1. Ouvrez une session sur votre ordinateur local, l'ordinateur à partir duquel vous déboguez, à l'aide de l'autre nom de compte.

     Ou

     . Déconnectez-vous de l'ordinateur distant, puis reconfigurez le partage de fichiers pour vous connecter à un autre ordinateur à l'aide du nom de votre compte :

    1. Dans le menu **Démarrer**, pointez sur **Accessoires**, puis cliquez sur **Invite de commandes**.

    2. À l'invite de commande Windows, tapez :

         `net use /delete computer_name`

    3. Modifiez les paramètres de partage de fichiers à l'aide de l'une des méthodes proposées dans l'aide Windows.