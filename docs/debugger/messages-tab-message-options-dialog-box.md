---
title: Onglet messages de la boîte de dialogue Options des messages | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- message options, Messages
ms.assetid: fb9fa211-e82c-40a5-9e4b-ba8de07313c0
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2c0a97a5b42e27c6db770e0c74a64e214561cea9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99891603"
---
# <a name="messages-tab-message-options-dialog-box"></a>Onglet Messages de la boîte de dialogue Options des messages
Utilisez l’onglet **messages** pour sélectionner les types de messages à répertorier dans la [vue messages](../debugger/messages-view.md)et pour spécifier les critères de recherche des messages. Pour afficher la [boîte de dialogue Options des messages](../debugger/message-options-dialog-box.md), choisissez **journaux des messages** dans le menu **Espion** .

 En règle générale, vous sélectionnez d’abord des **groupes de messages**, puis vous affinez la sélection en sélectionnant des **messages individuels à afficher**. Le bouton **tous** sélectionne tous les types de messages et le bouton **aucun** efface tous les types.

 Les paramètres suivants sont disponibles sous l’onglet **messages** :

 **Messages à afficher** Sélectionnez des messages spécifiques à afficher. Lorsque vous créez une nouvelle fenêtre de messages, elle peut afficher tous les messages. Lorsque vous filtrez des messages à partir de l’onglet **messages** , ce filtre s’applique uniquement aux nouveaux messages, et non aux messages qui ont déjà été affichés dans la vue Windows.

 **Groupes de messages** Sélectionnez les groupes de messages à afficher. Les groupes disponibles sont les suivants :

- WM_USER : avec un code supérieur ou égal à WM_USER

- Inscrit : inscrit avec l’appel **RegisterWindowMessage**

- Inconnu : messages inconnus dans la plage allant de 0 à (WM_USER-1)

  Notez que ces **groupes de messages** ne correspondent pas à des entrées spécifiques sous **messages à afficher**. Lorsque vous sélectionnez un groupe, la sélection est appliquée directement au flux de message.

  Une case à cocher grisée dans les **groupes de messages** indique que la zone de liste **messages à afficher** a été modifiée pour les messages de ce groupe ; tous les types de messages de ce groupe ne sont pas sélectionnés.

  **Enregistrer les paramètres par défaut** Enregistrez les paramètres actuels pour une utilisation ultérieure en tant qu’options de recherche de messages. Ces paramètres sont également enregistrés en quittant Spy + +.