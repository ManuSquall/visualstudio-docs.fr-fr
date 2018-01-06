---
title: "Erreur : Pare-feu sur ordinateur Local | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: vs.debug.error.firewall.localmachine
dev_langs:
- CSharp
- VB
- FSharp
- C++
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 160e71e357046b69019323ada5ff9cde006460bc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="error-firewall-on-local-machine"></a>Erreur : Pare-feu sur ordinateur local
Le pare-feu de connexion Internet sur l'ordinateur local, à partir duquel vous exécutez Visual Studio, n'est pas configuré pour autoriser le débogage distant. Pour le débogage distant managé ou natif avec le transport par défaut, le port TCP 135 doit être ouvert pour le trafic DCOM. Le partage de fichiers et d'imprimantes doit être ouvert, et devenv.exe doit être ajouté à la liste d'exceptions. L'ouverture de certains ports IPSEC peut également être nécessaire.  
  
 Pour plus d’informations, consultez [débogage distant](../debugger/remote-debugging.md).