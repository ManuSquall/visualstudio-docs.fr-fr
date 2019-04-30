---
title: Onglet messages, la boîte de dialogue Options des messages | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- message options, Messages
ms.assetid: fb9fa211-e82c-40a5-9e4b-ba8de07313c0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: de50e6fe997ce10266cbb51f2fd91c318ab2bd1f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62905528"
---
# <a name="messages-tab-message-options-dialog-box"></a>Onglet Messages de la boîte de dialogue Options des messages
Utilisez le **Messages** onglet à sélectionner les types de messages à la liste dans [vue Messages](../debugger/messages-view.md)et pour spécifier les critères de recherche de message. Pour afficher le [la boîte de dialogue Options des messages](../debugger/message-options-dialog-box.md), choisissez **Messages du journal** à partir de la **Spy** menu.

 En règle générale, vous sélectionnez **groupes de messages**et d’ajuster la sélection en sélectionnant individuels **les Messages à afficher**. Le **tous les** bouton sélectionne tous les types de messages et le **aucun** bouton efface tous les types.

 Les paramètres suivants sont disponibles sur le **Messages** onglet :

 **Les messages à afficher** sélectionner des messages spécifiques à afficher. Lorsque vous créez une nouvelle fenêtre de Messages, il peut afficher tous les messages. Lorsque vous filtrez des messages à partir de la **Messages** onglet, ce filtre s’applique uniquement aux nouveaux messages, pas les messages qui ont déjà été affichés dans la vue de Windows.

 **Groupes de messages** sélectionner des groupes de messages pour l’affichage. Les groupes disponibles sont les suivantes :

- WM_USER : avec un code supérieur ou égal à WM_USER

- Inscrit : inscrit avec le **RegisterWindowMessage** appeler

- Inconnu : messages inconnus dans la plage 0 à (WM_USER - 1)

  Notez que ces **groupes de messages** ne sont pas mappées à des entrées spécifiques sous **Messages à afficher**. Lorsque vous sélectionnez un groupe, la sélection est appliquée directement au flux de messages.

  Une case à cocher grisée dans **groupes de messages** indique que le **Messages à afficher** zone de liste a été modifiée pour les messages de ce groupe ; tous les types de messages de ce groupe sont sélectionnés.

  **Enregistrer les paramètres par défaut** enregistrer les paramètres actuels pour une utilisation ultérieure en tant qu’options de recherche de message. Ces paramètres sont également enregistrés en quittant Spy ++.