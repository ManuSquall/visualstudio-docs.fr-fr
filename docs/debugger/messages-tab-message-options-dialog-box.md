---
title: Onglet messages, la boîte de dialogue Options des messages | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- message options, Messages
ms.assetid: fb9fa211-e82c-40a5-9e4b-ba8de07313c0
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1f7675039f8e5f5fb5c1d5899b96682ab60a2bc0
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: fr-FR
ms.lasthandoff: 01/02/2019
ms.locfileid: "53830589"
---
# <a name="messages-tab-message-options-dialog-box"></a>Onglet Messages de la boîte de dialogue Options des messages
Utilisez le **Messages** onglet à sélectionner les types de messages à la liste dans [vue Messages](../debugger/messages-view.md)et pour spécifier les critères de recherche de message. Pour afficher le [la boîte de dialogue Options des messages](../debugger/message-options-dialog-box.md), choisissez **Messages du journal** à partir de la **Spy** menu.  
  
 En règle générale, vous sélectionnez **groupes de messages**et d’ajuster la sélection en sélectionnant individuels **les Messages à afficher**. Le **tous les** bouton sélectionne tous les types de messages et le **aucun** bouton efface tous les types.  
  
 Les paramètres suivants sont disponibles sur le **Messages** onglet :  
  
 **Messages à afficher**  
 Sélectionnez les messages spécifiques à afficher. Lorsque vous créez une nouvelle fenêtre de Messages, il peut afficher tous les messages. Lorsque vous filtrez des messages à partir de la **Messages** onglet, ce filtre s’applique uniquement aux nouveaux messages, pas les messages qui ont déjà été affichés dans la vue de Windows.  
  
 **Groupes de messages**  
 Sélectionnez les groupes de messages pour l’affichage. Les groupes disponibles sont les suivantes :  
  
- WM_USER : avec un code supérieur ou égal à WM_USER  
  
- Inscrit : inscrit avec le **RegisterWindowMessage** appeler  
  
- Inconnu : messages inconnus dans la plage 0 à (WM_USER - 1)  
  
  Notez que ces **groupes de messages** ne sont pas mappées à des entrées spécifiques sous **Messages à afficher**. Lorsque vous sélectionnez un groupe, la sélection est appliquée directement au flux de messages.  
  
  Une case à cocher grisée dans **groupes de messages** indique que le **Messages à afficher** zone de liste a été modifiée pour les messages de ce groupe ; tous les types de messages de ce groupe sont sélectionnés.  
  
  **Enregistrer les paramètres par défaut**  
  Enregistrer les paramètres actuels pour une utilisation ultérieure en tant qu’options de recherche de message. Ces paramètres sont également enregistrés en quittant Spy ++.