---
title: "Cette t&#226;che n&#233;cessite l&#39;&#233;l&#233;vation des autorisations dans Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.UACDialog"
ms.assetid: a03d3509-5e6e-411a-9aec-0766d7ee3a0e
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Cette t&#226;che n&#233;cessite l&#39;&#233;l&#233;vation des autorisations dans Visual Studio
Cette erreur s'affiche si une commande Visual Studio est appelée par un utilisateur dont le compte a des autorisations insuffisantes pour effectuer l'opération.  
  
 Certaines commandes de Visual Studio doivent être exécutées avec un compte qui a des droits d'accès utilisateur est suffisant pour activer la commande de lire ou écrire tous les fichiers et clés de Registre nécessaires.  Pour obtenir ces droits, vous devez fermer et rouvrir Visual Studio avec un compte qui a élevé l'accès, tel qu'un administrateur.  
  
 Pour plus d'informations sur les autorisations en exécutant Visual Studio, consultez l' [Autorisations utilisateur](../ide/user-permissions-and-visual-studio.md).  
  
### Pour corriger cette erreur  
  
1.  Dans la boîte de dialogue, cliquez sur **Redémarrer en utilisant un compte différent**.  
  
     Cela vous invite à enregistrer la solution actuellement chargée, puis ferme Visual Studio et le redémarre, et vous invite à basculer vers un compte différent.  
  
2.  À l'invite d'ouverture de session, connectez\-vous avec un compte qui a des droits plus élevés que ceux du compte précédent, par exemple un compte Administrateur.  
  
     Au démarrage de Visual Studio, celui\-ci recharge la dernière solution et la ligne de commande.  
  
> [!NOTE]
>  Vous connecter avec un compte qui a des droits plus élevés ne garantit pas nécessairement que la commande de Visual Studio s'exécute.  Certaines commandes peuvent s'exécuter sans succès même si vous utilisez un compte Administrateur.