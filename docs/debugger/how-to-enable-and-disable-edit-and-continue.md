---
title: "Comment&#160;: activer et d&#233;sactiver Modifier &amp; Continuer | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "/INCREMENTAL (option de l'éditeur de liens)"
  - "Appliquer les modifications du code (commande)"
  - "mode arrêt, appliquer les modifications du code"
  - "changements de code, appliquer en mode arrêt"
  - "Modifier & Continuer, appliquer les modifications du code"
  - "Modifier & Continuer, désactiver"
  - "Modifier & Continuer, activer"
  - "Lancer (commande)"
  - "INCREMENTAL (option de l'éditeur de liens)"
  - "Pas à pas (commande)"
ms.assetid: fd961a1c-76fa-420d-ad8f-c1a6c003b0db
caps.latest.revision: 26
caps.handback.revision: 24
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Comment&#160;: activer et d&#233;sactiver Modifier &amp; Continuer
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous pouvez activer ou désactiver Modifier & Continuer dans la boîte de dialogue **Options** au moment du design.  Vous ne pouvez pas modifier ce paramètre pendant le débogage.  
  
 Modifier & Continuer ne fonctionne que dans les versions Debug.  Pour C\+\+ natif, Modifier & Continuer exige l'option \/INCREMENTAL.  
  
## Procédures  
  
#### Pour activer ou désactiver Modifier & Continuer  
  
1.  Dans le menu **Outils**, cliquez sur **Options**.  
  
2.  Dans la boîte de dialogue **Options**, ouvrez le nœud **Débogage** et sélectionnez la catégorie **Modifier & Continuer**.  
  
3.  Pour activer, activez la case à cocher **Activer Modifier et Continuer** .  Pour désactiver, désactivez la case à cocher.  
  
    > [!NOTE]
    >  Si IntelliTrace est activé et si vous collectez des événements et des informations d'appel IntelliTrace, les fonctions Modifier et Continuer sont désactivées.  Pour plus d'informations, consultez [Configurer IntelliTrace pour collecter des informations de débogage](http://msdn.microsoft.com/fr-fr/7657ecab-e07e-4b1b-872d-f05d966be37e).  
  
4.  Cliquez sur **OK**.  
  
## Voir aussi  
 [Modifier&Continuer](../debugger/edit-and-continue.md)   
 [Modifier & Continuer, Débogage, boîte de dialogue Options](../Topic/Edit%20and%20Continue,%20Debugging,%20Options%20Dialog%20Box.md)