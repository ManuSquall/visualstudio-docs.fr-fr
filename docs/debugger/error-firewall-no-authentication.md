---
title: "Erreur : Pare-feu aucune authentification | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.error.firewall.noauth
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: dda1acb8-bed7-4bc8-9991-9cdc49c2ac1e
caps.latest.revision: "10"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1750c0ab8bafe53136d01ba27ada9c242b318c3a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="error-firewall-no-authentication"></a>Erreur : Pare-feu Aucune authentification
Le pare-feu de connexion Internet sur l'ordinateur distant n'est pas installé pour autoriser le débogage distant. Pour le débogage distant avec `No Authentication`, msvsmon.exe doit être ajouté à la liste d'exceptions. L'ouverture de certains ports IPSEC peut également être nécessaire.  
  
> [!NOTE]
>  Le débogueur distant peut configurer automatiquement le Pare-feu Windows. Lorsque vous utilisez un pare-feu autre que le Pare-feu Windows tel qu'un pare-feu logiciel tiers ou un pare-feu matériel, il doit être configuré manuellement pour autoriser le débogage distant. Pour ce faire, autorisez le trafic sur les ports TCP/IP sur lesquels msvsmon.exe effectue une écoute. Par défaut, il s'agit des ports 4018 et 4019, où 4018 est utilisé sur tous les systèmes d'exploitation, et 4019 est utilisé uniquement sur Windows x64 pour permettre le débogage des processus x86.  
  
 Pour plus d’informations, consultez [débogage distant](../debugger/remote-debugging.md).