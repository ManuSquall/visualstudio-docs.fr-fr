---
title: "CA2103 : V&#233;rifiez la s&#233;curit&#233; imp&#233;rative | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2103"
  - "ReviewImperativeSecurity"
helpviewer_keywords: 
  - "CA2103"
  - "ReviewImperativeSecurity"
ms.assetid: d24fde71-bdf6-46c0-8965-9a73dc33c1aa
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2103 : V&#233;rifiez la s&#233;curit&#233; imp&#233;rative
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ReviewImperativeSecurity|  
|CheckId|CA2103|  
|Catégorie|Microsoft.Security|  
|Modification avec rupture|Oui|  
  
## Cause  
 Une méthode utilise la sécurité impérative et est susceptible de construire l'autorisation à l'aide d'informations d'état ou de valeurs de retour qui peuvent changer pendant que la demande est active.  
  
## Description de la règle  
 La sécurité impérative utilise des objets managés pour spécifier des autorisations et des actions de sécurité pendant l'exécution d'un code, par comparaison à la sécurité déclarative qui utilise des attributs pour stocker des autorisations et des actions dans des métadonnées.  La sécurité impérative est très flexible car vous pouvez définir l'état d'un objet d'autorisation et sélectionner des actions de sécurité à l'aide d'informations qui ne sont pas disponibles avant le moment d'exécution.  Cette souplesse s'accompagne du risque que les informations d'exécution que vous utilisez pour déterminer l'état d'une autorisation ne restent pas inchangées au cours de l'application de l'action.  
  
 Utilisez la sécurité de déclaration dès que possible.  Les demandes déclaratives sont plus faciles à comprendre.  
  
## Comment corriger les violations  
 Révisez les demandes de sécurité impératives pour garantir que l'état de l'autorisation ne repose pas sur des informations susceptibles d'évoluer tant que l'autorisation est en cours d'utilisation.  
  
## Quand supprimer les avertissements  
 Il est possible de supprimer sans risque un avertissement de cette règle si l'autorisation ne repose pas sur des données changeantes.  Toutefois, il est préférable de changer la demande impérative en son équivalent déclaratif.  
  
## Voir aussi  
 [Instructions de codage sécurisé](../Topic/Secure%20Coding%20Guidelines.md)   
 [Données et modélisation](../Topic/Data%20and%20Modeling%20in%20the%20.NET%20Framework.md)