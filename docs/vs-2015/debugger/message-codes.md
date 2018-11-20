---
title: Codes de message | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- message codes
ms.assetid: 9f91f4e2-c1f1-4349-9f11-2fbbf59654be
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0464042c17a3ed0836b99183dacbe4918823c752
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51724632"
---
# <a name="message-codes"></a>Codes des messages
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Chaque ligne du message indiqué dans [vue Messages](../debugger/messages-view.md) contient un « P », du,' de,' ou le code de « R ». Ces codes ont les significations suivantes :  
  
|Code|Signification|  
|----------|-------------|  
|P|Le message a été publié dans la file d’attente avec le **PostMessage** (fonction). Aucune information n’est disponible concernant la dernière disposition du message.|  
|S|Le message a été envoyé avec la **SendMessage** (fonction). Cela signifie que l’expéditeur ne reprend pas le contrôle jusqu'à ce que le destinataire traite et retourne le message. Le récepteur peut, par conséquent, passer une valeur de retour à l’expéditeur.|  
|s|Le message a été envoyé, mais la sécurité empêche l’accès à la valeur de retour.|  
|R|De chacun ' a une ligne « R » (retour) correspondante qui répertorie la valeur de retour du message. Parfois, les appels de message sont imbriquées, ce qui signifie que ce gestionnaire d’un message envoie un autre message.|



