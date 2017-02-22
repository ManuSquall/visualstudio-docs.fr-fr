---
title: "Onglet Messages de la bo&#238;te de dialogue Options des messages | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "options des messages, Messages"
ms.assetid: fb9fa211-e82c-40a5-9e4b-ba8de07313c0
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Onglet Messages de la bo&#238;te de dialogue Options des messages
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Utilisez l'onglet **Messages** pour sélectionner les types de messages à lister dans la [vue Messages](../debugger/messages-view.md), ainsi que pour spécifier les critères de recherche des messages.  Pour afficher la [boîte de dialogue Options des messages](../debugger/message-options-dialog-box.md), sélectionnez **Enregistrer les messages** dans le menu **Espionner**.  
  
 En règle générale, vous sélectionnez d'abord des **groupes de messages**, puis vous affinez votre choix en sélectionnant individuellement les **messages à afficher**.  Le bouton **Tous** permet de sélectionner tous les types de messages, alors que le bouton **Aucun** permet d'effacer tous les types de messages.  
  
 Les paramètres suivants sont disponibles sous l'onglet **Messages** :  
  
 **Messages à afficher**  
 Sélectionne des messages spécifiques à afficher.  Lorsque vous créez une nouvelle fenêtre Messages, elle peut afficher tous les messages.  Lorsque vous filtrez des messages à partir de l'onglet **Messages**, ce filtre s'applique seulement aux nouveaux messages, pas aux messages qui ont déjà été affichés dans la vue Fenêtres.  
  
 **Groupes de messages**  
 Sélectionnez des groupes de messages à afficher.  Les groupes disponibles sont les suivants :  
  
-   WM\_USER : avec un code supérieur ou égal à WM\_USER  
  
-   Inscrit : inscrit avec l'appel **RegisterWindowMessage**  
  
-   Inconnu : messages inconnus dans la plage allant de 0 à \(WM\_USER – 1\)  
  
 Notez que ces **groupes de messages** ne sont pas mappés à des entrées spécifiques sous **Messages à afficher**.  Lorsque vous sélectionnez un groupe, la sélection est appliquée directement au flux de messages.  
  
 Une case à cocher grisée dans **Groupes de messages** indique que la zone de liste **Messages à afficher** a été modifiée pour les messages de ce groupe ; tous les types de messages de ce groupe ne sont pas sélectionnés.  
  
 **Enregistrer les paramètres par défaut**  
 Enregistrez les paramètres actuels en tant qu'options de recherche de messages pour une utilisation ultérieure.  Ces paramètres sont également enregistrés lorsque vous quittez Spy\+\+.