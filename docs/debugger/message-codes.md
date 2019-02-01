---
title: Codes de message | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- message codes
ms.assetid: 9f91f4e2-c1f1-4349-9f11-2fbbf59654be
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c3899da3b668406a701ce5c1c4935b531754d10e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55017082"
---
# <a name="message-codes"></a>Codes des messages
Chaque ligne du message indiqué dans [vue Messages](../debugger/messages-view.md) contient un « P », du,' de,' ou le code de « R ». Ces codes ont les significations suivantes :  
  
|Code|Signification|  
|----------|-------------|  
|P|Le message a été publié dans la file d’attente avec le **PostMessage** (fonction). Aucune information n’est disponible concernant la dernière disposition du message.|  
|S|Le message a été envoyé avec la **SendMessage** (fonction). Cela signifie que l’expéditeur ne reprend pas le contrôle jusqu'à ce que le destinataire traite et retourne le message. Le récepteur peut, par conséquent, passer une valeur de retour à l’expéditeur.|  
|s|Le message a été envoyé, mais la sécurité empêche l’accès à la valeur de retour.|  
|R|De chacun ' a une ligne « R » (retour) correspondante qui répertorie la valeur de retour du message. Parfois, les appels de message sont imbriquées, ce qui signifie que ce gestionnaire d’un message envoie un autre message.|