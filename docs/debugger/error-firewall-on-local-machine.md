---
title: 'Erreur : Pare-feu sur ordinateur Local | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.firewall.localmachine
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
ms.openlocfilehash: e85c97d5950f71d9552bba944450603e47a5ab49
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
ms.locfileid: "31472865"
---
# <a name="error-firewall-on-local-machine"></a>Erreur : Pare-feu sur ordinateur local
Le pare-feu de connexion Internet sur l'ordinateur local, à partir duquel vous exécutez Visual Studio, n'est pas configuré pour autoriser le débogage distant. Pour le débogage distant managé ou natif avec le transport par défaut, le port TCP 135 doit être ouvert pour le trafic DCOM. Le partage de fichiers et d'imprimantes doit être ouvert, et devenv.exe doit être ajouté à la liste d'exceptions. L'ouverture de certains ports IPSEC peut également être nécessaire.  
  
 Pour plus d’informations, consultez [débogage distant](../debugger/remote-debugging.md).