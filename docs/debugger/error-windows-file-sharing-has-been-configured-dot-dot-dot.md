---
title: 'Erreur : Le partage de fichiers Windows a été configuré... | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.remote_credentials_prohibited
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
ms.openlocfilehash: 591b051cb6164f4c8d260be3de29833154c96255
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31472787"
---
# <a name="error-windows-file-sharing-has-been-configured"></a>Erreur : Le partage de fichiers Windows a été configuré...
Le partage de fichiers Windows a été configuré pour que vous vous connectiez sur l'ordinateur distant avec un autre nom d'utilisateur. Cela est incompatible avec le débogage distant  
  
 La configuration actuelle de partage de fichiers prévoit de pouvoir se connecter à l'ordinateur distant à l'aide d'un nom d'utilisateur différent. Le débogage distant n'est pas possible dans ce scénario.  
  
 Pour corriger cette erreur, ouvrez une session sur l'ordinateur à l'aide de l'autre nom de compte, ou modifiez le partage de fichiers pour utiliser le nom de compte sous lequel vous déboguez.  
  
 Si vous souhaitez vous connecter à l'ordinateur distant à l'aide de ce nom d'utilisateur, vous devez d'abord vous déconnecter de l'ordinateur distant.  
  
### <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1.  Ouvrez une session sur votre ordinateur local, l'ordinateur à partir duquel vous déboguez, à l'aide de l'autre nom de compte.  
  
     - ou -  
  
     . Déconnectez-vous de l'ordinateur distant, puis reconfigurez le partage de fichiers pour vous connecter à un autre ordinateur à l'aide du nom de votre compte :  
  
    1.  Sur le **Démarrer** menu, pointez sur **Accessoires**, puis cliquez sur **invite de commandes**.  
  
    2.  À l'invite de commande Windows, tapez :  
  
         `net use /delete computer_name`  
  
    3.  Modifiez les paramètres de partage de fichiers à l'aide de l'une des méthodes proposées dans l'aide Windows.