---
title: Codes de message | Microsoft Docs
description: Découvrez la signification des codes de message affichés sur chaque ligne de message de la vue messages.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: e4b836a5d4c1faad6b4c0375e2ec51d759816889
ms.sourcegitcommit: 620d30c60da8f9805fce524fe4951cf40f28297d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97903608"
---
# <a name="message-codes"></a>Codes des messages
Chaque ligne de message affichée dans la [vue messages](../debugger/messages-view.md) contient un code’P, ', ', 'ou’R'. Ces codes ont les significations suivantes :

|Code|Signification|
|----------|-------------|
|P|Le message a été publié dans la file d’attente avec la fonction **PostMessage** . Aucune information n’est disponible concernant la disposition finale du message.|
|S|Le message a été envoyé avec la fonction **SendMessage** . Cela signifie que l’expéditeur ne reprend pas le contrôle tant que le destinataire ne traite pas et ne renvoie pas le message. Le récepteur peut donc retourner une valeur de retour à l’expéditeur.|
|s|Le message a été envoyé, mais la sécurité empêche l’accès à la valeur de retour.|
|R|Chaque ligne’a une ligne’R' (retour) correspondante qui répertorie la valeur de retour du message. Parfois, les appels de message sont imbriqués, ce qui signifie qu’un gestionnaire de messages envoie un autre message.|