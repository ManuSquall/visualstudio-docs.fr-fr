---
title: "Erreur&#160;: Vous n&#39;&#234;tes pas autoris&#233; &#224; inspecter l&#39;identit&#233; du processus. | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
ms.assetid: 6233d060-85b8-42be-ae5f-bde7e1d0f241
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Erreur&#160;: Vous n&#39;&#234;tes pas autoris&#233; &#224; inspecter l&#39;identit&#233; du processus.
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous n'êtes pas autorisé à inspecter l'identité du processus.Cela peut être dû à la configuration de votre système.  
  
 Le débogueur n'a pas pu inspecter l'identité du processus, qui contient des informations nécessaires au débogage.  La cause la plus probable est la désactivation des services Terminal Server.  Les services Terminal Server sont activés par défaut.  Pour les réactiver, procédez comme suit.  
  
### Pour activer les services Terminal Server  
  
1.  Cliquez sur **Démarrer**, puis choisissez **Panneau de configuration**.  
  
2.  Dans Panneau de configuration, choisissez **Basculer vers l'affichage classique**, si nécessaire, puis double\-cliquez sur **Outils d'administration**.  
  
3.  Dans la fenêtre **Outils d'administration**, double\-cliquez sur **Gestion de l'ordinateur**.  
  
4.  Dans la fenêtre Gestion de l'ordinateur, développez le nœud **Services et applications**.  
  
5.  Sous **Services et applications**, cliquez sur **Services**.  
  
     Une liste de services apparaît dans le volet droit.  
  
6.  Dans la liste **Services**, cliquez avec le bouton droit sur **Services Terminal Server**, puis choisissez **Propriétés**.  
  
7.  Dans la fenêtre **Propriétés des services Terminal Server**, accédez à l'onglet **Général** et affectez **Manuel** à l'option **Type de démarrage**.  
  
8.  Cliquez sur **OK**.  
  
9. Redémarrez l'ordinateur.  
  
     Cette procédure n'active pas automatiquement le Bureau à distance.  Pour activer le Bureau à distance sur votre ordinateur, effectuez la procédure supplémentaire suivante.  
  
### Pour activer le Bureau à distance  
  
1.  Cliquez sur **Démarrer**, puis cliquez avec le bouton droit sur **Poste de travail**.  
  
2.  Choisissez **Propriétés**.  
  
     La fenêtre **Propriétés système** s'affiche.  
  
3.  Cliquez sur **À distance**.  
  
4.  Sous **Bureau à distance**, sélectionnez **Autoriser les utilisateurs à se connecter à distance à cet ordinateur**.  
  
5.  Cliquez sur **OK**.  
  
## Voir aussi  
 [Erreurs de débogage distant et dépannage](../debugger/remote-debugging-errors-and-troubleshooting.md)