---
title: Pare-feu sans authentification | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
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
ms.openlocfilehash: a8548880df8c69fa59d58bf4c13f7f547ad359bd
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90852717"
---
# <a name="error-firewall-no-authentication"></a>Erreur : Pare-feu Aucune authentification
Le pare-feu de connexion Internet sur l'ordinateur distant n'est pas installé pour autoriser le débogage distant. Pour le débogage distant avec `No Authentication`, msvsmon.exe doit être ajouté à la liste d'exceptions. L'ouverture de certains ports IPSEC peut également être nécessaire.

> [!NOTE]
> Le débogueur distant peut configurer automatiquement le Pare-feu Windows. Lorsque vous utilisez un pare-feu autre que le Pare-feu Windows tel qu'un pare-feu logiciel tiers ou un pare-feu matériel, il doit être configuré manuellement pour autoriser le débogage distant. Pour ce faire, autorisez le trafic sur les ports TCP/IP sur lesquels msvsmon.exe effectue une écoute. Par défaut, il s'agit des ports 4018 et 4019, où 4018 est utilisé sur tous les systèmes d'exploitation, et 4019 est utilisé uniquement sur Windows x64 pour permettre le débogage des processus x86.

 Pour plus d’informations, consultez [débogage distant](../debugger/remote-debugging.md).