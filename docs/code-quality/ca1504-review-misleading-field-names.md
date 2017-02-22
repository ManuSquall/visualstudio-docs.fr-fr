---
title: "CA1504&#160;: V&#233;rifier les noms de champs trompeurs | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ReviewMisleadingFieldNames"
  - "CA1504"
helpviewer_keywords: 
  - "CA1504"
  - "ReviewMisleadingFieldNames"
ms.assetid: 94136ff1-4aaf-4dc2-9170-48c171ab7499
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 15
---
# CA1504&#160;: V&#233;rifier les noms de champs trompeurs
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ReviewMisleadingFieldNames|  
|CheckId|CA1504|  
|Catégorie|Microsoft.Maintainability|  
|Modification avec rupture|Modification sans rupture|  
  
## Cause  
 Le nom d'un champ d'instance commence par "s\_" ou le nom d'un champ `static` \(`Shared` dans [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\) commence par "m\_".  
  
## Description de la règle  
 Les noms de champs qui commencent par "s\_" sont associés aux données statiques par de nombreux utilisateurs.  De même, les noms de champs qui commencent par "m\_" sont associés aux données d'instance \(membre\).  Pour faciliter la gestion du code, les noms doivent suivre les conventions communément utilisées.  
  
## Comment corriger les violations  
 Pour résoudre une violation de cette règle, renommez le champ à l'aide du préfixe approprié.  Vous pouvez également accorder le champ avec le suffixe actuel en ajoutant ou en supprimant le modificateur `static`.  
  
## Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.