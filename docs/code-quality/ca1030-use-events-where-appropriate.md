---
title: "CA1030 : Utiliser des événements lorsque cela est approprié | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- UseEventsWhereAppropriate
- CA1030
helpviewer_keywords:
- CA1030
- UseEventsWhereAppropriate
ms.assetid: ea051367-deeb-40f9-9b65-eb818f1e133a
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4c07aac3780abc10dd3995b21b5c9636607166f8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="ca1030-use-events-where-appropriate"></a>CA1030 : Utiliser des événements lorsque cela est approprié
|||  
|-|-|  
|TypeName|UseEventsWhereAppropriate|  
|CheckId|CA1030|  
|Catégorie|Microsoft.Design|  
|Modification avec rupture|Sans rupture|  
  
## <a name="cause"></a>Cause  
 Nom d’une méthode publique, protégée ou privée commence par l’une des opérations suivantes :  
  
-   Composant additionnel  
  
-   RemoveOn  
  
-   Incendie  
  
-   Raise  
  
## <a name="rule-description"></a>Description de la règle  
 Cette règle détecte des méthodes qui présentent des noms qui ordinairement seraient utilisés pour des événements. Les événements suivent le modèle de design observateur ou publier / abonner ; ils sont utilisés lorsqu’un changement d’état dans un objet doit être communiqué à d’autres objets. Si une méthode est appelée en réponse à un changement d’état clairement définie, la méthode doit être appelée par un gestionnaire d’événements. Les objets qui appellent la méthode doivent déclencher des événements au lieu d'appeler directement la méthode.  
  
 Des exemples courants d’événements sont trouvent dans les applications d’interface utilisateur où une action de l’utilisateur en cliquant sur un bouton provoque un segment de code à exécuter. Le [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] modèle d’événement n’est pas limité aux interfaces utilisateur ; il doit être utilisé partout où vous devez communiquer l’état passe à un ou plusieurs objets.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Si la méthode est appelée lorsque l’état d’un objet change, vous devez envisager de modifier la conception pour utiliser le [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] modèle d’événement.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Supprimez un avertissement de cette règle si la méthode ne fonctionne pas avec le [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] modèle d’événement.