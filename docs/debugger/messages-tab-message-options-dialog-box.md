---
title: "Onglet messages, la boîte de dialogue Options des messages | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- message options, Messages
ms.assetid: fb9fa211-e82c-40a5-9e4b-ba8de07313c0
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: b7c9d533d73039de699f59c2343f3f91f888710c
ms.sourcegitcommit: 9e6ff74da1afd8bd2f0e69387ce81f2a74619182
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/04/2018
---
# <a name="messages-tab-message-options-dialog-box"></a>Onglet Messages de la boîte de dialogue Options des messages
Utilisez le **Messages** tab pour sélectionner les types de messages à la liste dans [vue Messages](../debugger/messages-view.md)et pour spécifier les critères de recherche de messages. Pour afficher le [la boîte de dialogue Options des messages](../debugger/message-options-dialog-box.md), choisissez **des Messages de journal** à partir de la **Spy** menu.  
  
 En règle générale, vous sélectionnez **groupes de messages**et d’ajuster la sélection en sélectionnant individuels **les Messages à afficher**. Le **tous les** bouton sélectionne tous les types de messages et le **aucun** bouton efface tous les types.  
  
 Les paramètres suivants sont disponibles sur le **Messages** onglet :  
  
 **Messages à afficher**  
 Sélectionnez les messages spécifiques à afficher. Lorsque vous créez une nouvelle fenêtre de Messages, il peut afficher tous les messages. Lorsque vous filtrez des messages à partir de la **Messages** onglet, ce filtre s’applique uniquement aux nouveaux messages, pas les messages qui ont déjà été affichés dans la vue fenêtres.  
  
 **Groupes de messages**  
 Sélectionnez les groupes de message à afficher. Les groupes disponibles sont les suivantes :  
  
-   WM_USER : avec un code supérieur ou égal à WM_USER  
  
-   Inscrit : inscrit avec le **RegisterWindowMessage** appeler  
  
-   Inconnu : messages inconnus dans la plage 0 à (WM_USER - 1)  
  
 Notez que ces **groupes de messages** ne correspondent pas à des entrées spécifiques sous **Messages à afficher**. Lorsque vous sélectionnez un groupe, la sélection est appliquée directement dans le flux de message.  
  
 Une case à cocher grisée dans **groupes de messages** indique que le **Messages à afficher** zone de liste a été modifiée pour les messages de ce groupe ; tous les types de messages de ce groupe sont sélectionnés.  
  
 **Enregistrer les paramètres par défaut**  
 Enregistrer les paramètres actuels pour une utilisation ultérieure en tant qu’options de recherche de message. Ces paramètres sont également enregistrés en quittant Spy ++.