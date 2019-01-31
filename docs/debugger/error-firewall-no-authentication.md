---
title: 'Erreur : Aucune authentification du pare-feu | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.firewall.noauth
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e565d1372131272f8653df328dbbe9749a8b1ddb
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55035300"
---
# <a name="error-firewall-no-authentication"></a>Erreur : aucune authentification du pare-feu
Le pare-feu de connexion Internet sur l'ordinateur distant n'est pas installé pour autoriser le débogage distant. Pour le débogage distant avec `No Authentication`, msvsmon.exe doit être ajouté à la liste d'exceptions. L'ouverture de certains ports IPSEC peut également être nécessaire.  
  
> [!NOTE]
>  Le débogueur distant peut configurer automatiquement le Pare-feu Windows. Lorsque vous utilisez un pare-feu autre que le Pare-feu Windows tel qu'un pare-feu logiciel tiers ou un pare-feu matériel, il doit être configuré manuellement pour autoriser le débogage distant. Pour ce faire, autorisez le trafic sur les ports TCP/IP sur lesquels msvsmon.exe effectue une écoute. Par défaut, il s'agit des ports 4018 et 4019, où 4018 est utilisé sur tous les systèmes d'exploitation, et 4019 est utilisé uniquement sur Windows x64 pour permettre le débogage des processus x86.  
  
 Pour plus d’informations, consultez [le débogage à distance](../debugger/remote-debugging.md).