---
title: Alias, commande | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- tools.alias
helpviewer_keywords:
- aliases, Visual Studio commands
- commands, aliases
- Tools.Alias command
- command aliases
- alias command
ms.assetid: bdf857df-b5d5-450f-8c10-a6fd4dccc130
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f9fb6a4da0b18cf022ee388ff4a6fa5f399dc650
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49258516"
---
# <a name="alias-command"></a>Alias, commande
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Crée un alias pour une commande complète, pour une commande complète et des arguments ou pour un autre alias.  
  
> [!TIP]
>  Tapez `>alias` sans aucun argument pour afficher la liste actuelle des alias et leur définition.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Tools.Alias [/delete] [/reset] [aliasname] [aliasstring]  
```  
  
## <a name="arguments"></a>Arguments  
 `aliasname`  
 Facultatif. Nom du nouvel alias. Si aucune valeur n’est fournie pour `aliasname`, la liste des alias en cours accompagnés de leur définition s’affiche.  
  
 `aliasstring`  
 Facultatif. Nom complet de la commande ou alias existant suivi des paramètres souhaités pour créer un alias. Si aucune valeur n’est fournie pour `aliasstring`, le nom et la chaîne associés à l’alias spécifié s’affichent.  
  
## <a name="switches"></a>Commutateurs  
 /delete ou /del ou /d  
 Facultatif. Supprime l’alias spécifié, qui n’apparaît plus dans la liste de saisie semi-automatique.  
  
 /reset  
 Facultatif. Rétablit les paramètres d’origine de la liste d’alias prédéfinis. En d’autres termes, ce commutateur restaure tous les alias prédéfinis et supprime tous les alias définis par l’utilisateur.  
  
## <a name="remarks"></a>Notes  
 Dans la mesure où un alias représente des commandes, il doit être placé au début de la ligne de commande.  
  
 Lors de l’émission de cette commande, vous devez inclure les commutateurs immédiatement après la commande, et non après les alias, sans quoi le commutateur lui-même sera inclus dans la chaîne de l’alias.  
  
 Le commutateur `/reset` demande confirmation avant de restaurer les alias. Il n’existe pas de forme abrégée de `/reset`.  
  
## <a name="examples"></a>Exemples  
 Cet exemple crée un alias, `upper`, pour la commande Edit.MakeUpperCase complète.  
  
```  
>Tools.Alias upper Edit.MakeUpperCase  
```  
  
 Cet exemple supprime l’alias `upper`.  
  
```  
>Tools.alias /delete upper  
```  
  
 Cet exemple affiche la liste de tous les alias en cours accompagnés de leur définition.  
  
```  
>Tools.Alias  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Commandes Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Fenêtre Commande](../../ide/reference/command-window.md)   
 [Zone Rechercher/Commande](../../ide/find-command-box.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)



