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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a37fc9c1df938c1cb4817b74d2ebb1d239377823
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53827232"
---
# <a name="error-firewall-no-authentication"></a>Erreur : aucune authentification du pare-feu
Le pare-feu de connexion Internet sur l'ordinateur distant n'est pas installé pour autoriser le débogage distant. Pour le débogage distant avec `No Authentication`, msvsmon.exe doit être ajouté à la liste d'exceptions. L'ouverture de certains ports IPSEC peut également être nécessaire.  
  
> [!NOTE]
>  Le débogueur distant peut configurer automatiquement le Pare-feu Windows. Lorsque vous utilisez un pare-feu autre que le Pare-feu Windows tel qu'un pare-feu logiciel tiers ou un pare-feu matériel, il doit être configuré manuellement pour autoriser le débogage distant. Pour ce faire, autorisez le trafic sur les ports TCP/IP sur lesquels msvsmon.exe effectue une écoute. Par défaut, il s'agit des ports 4018 et 4019, où 4018 est utilisé sur tous les systèmes d'exploitation, et 4019 est utilisé uniquement sur Windows x64 pour permettre le débogage des processus x86.  
  
 Pour plus d’informations, consultez [le débogage à distance](../debugger/remote-debugging.md).