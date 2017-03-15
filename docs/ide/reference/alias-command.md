---
title: "Alias, commande | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "tools.alias"
helpviewer_keywords: 
  - "alias (commande)"
  - "alias, commandes Visual Studio"
  - "alias de commande"
  - "commandes, alias"
  - "Tools.Alias (commande)"
ms.assetid: bdf857df-b5d5-450f-8c10-a6fd4dccc130
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 12
---
# Alias, commande
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Crée un nouvel alias pour une commande complète, une commande complète et ses arguments ou même pour un autre alias.  
  
> [!TIP]
>  Tapez `>alias` sans aucun argument pour afficher tous les alias en cours et leur définition.  
  
## Syntaxe  
  
```  
Tools.Alias [/delete] [/reset] [aliasname] [aliasstring]  
```  
  
## Arguments  
 `aliasname`  
 Optionnel.  Nom du nouvel alias.  Si aucune valeur n'est fournie pour l'argument `aliasname`, la liste des alias en cours accompagnés de leur définition s'affiche.  
  
 `aliasstring`  
 Optionnel.  Nom complet de la commande ou alias existant suivi des paramètres souhaités pour créer un nouvel alias.  Si aucune valeur n'est fournie pour l'argument `aliasstring`, le nom et la chaîne associés à l'alias spécifié s'affichent.  
  
## Commutateurs  
 \/delete ou \/del ou \/d  
 Optionnel.  Supprime l'alias spécifié ; cet alias n'apparaît plus dans la liste de saisie semi\-automatique.  
  
 \/reset  
 Optionnel.  Rétablit la liste d'alias prédéfinis dans son état initial.  En d'autres termes, ce commutateur restaure tous les alias prédéfinis et supprime tous les alias définis par l'utilisateur.  
  
## Notes  
 Dans la mesure où un alias représente des commandes, il doit être placé au début de la ligne de commande.  
  
 Lorsque vous soumettez cette commande, vous devez inclure les commutateurs immédiatement après la commande, et non après les alias, sans quoi le commutateur lui\-même sera inclus dans la chaîne de l'alias.  
  
 Le commutateur `/reset` demande confirmation avant de restaurer les alias.  Il n'existe pas de forme abrégée de `/reset`.  
  
## Exemples  
 Cet exemple crée un alias, `upper`, pour la commande Edit.MakeUpperCase complète.  
  
```  
>Tools.Alias upper Edit.MakeUpperCase  
```  
  
 Cet exemple supprime l'alias `upper`.  
  
```  
>Tools.alias /delete upper  
```  
  
 Cet exemple affiche la liste des alias en cours accompagnés de leur définition.  
  
```  
>Tools.Alias  
```  
  
## Voir aussi  
 [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Commande, fenêtre](../../ide/reference/command-window.md)   
 [Zone Rechercher\/Commande](../../ide/find-command-box.md)   
 [Alias de commandes Visual Studio](../../ide/reference/visual-studio-command-aliases.md)