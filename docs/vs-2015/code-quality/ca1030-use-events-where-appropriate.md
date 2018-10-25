---
title: 'CA1030 : Utiliser des événements appropriés | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- UseEventsWhereAppropriate
- CA1030
helpviewer_keywords:
- CA1030
- UseEventsWhereAppropriate
ms.assetid: ea051367-deeb-40f9-9b65-eb818f1e133a
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: b1b4989b5b8ca47bc41328c75610cf984926aae2
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49870131"
---
# <a name="ca1030-use-events-where-appropriate"></a>CA1030 : Utiliser des événements lorsque cela est approprié
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UseEventsWhereAppropriate|
|CheckId|CA1030|
|Category|Microsoft.Design|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Un nom de la méthode publique, protégée ou privée commence par l’une des opérations suivantes :

-   Composant additionnel

-   RemoveOn

-   Incendie

-   Raise

## <a name="rule-description"></a>Description de la règle
 Cette règle détecte des méthodes qui présentent des noms qui ordinairement seraient utilisés pour des événements. Événements suivent le modèle de design observateur ou publier / abonner ; ils sont utilisés lorsqu’un changement d’état dans un objet doit être communiqué à d’autres objets. Si une méthode est appelée en réponse à un changement d’état clairement définie, la méthode doit être appelée par un gestionnaire d’événements. Les objets qui appellent la méthode doivent déclencher des événements au lieu d'appeler directement la méthode.

 Voici quelques exemples courants d’événements sont trouvent dans des applications d’interface utilisateur où une action de l’utilisateur comme un clic sur un bouton provoque un segment de code à exécuter. Le [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] modèle d’événement n’est pas limité aux interfaces utilisateur ; il doit être utilisé partout où vous devez communiquer l’état passe à un ou plusieurs objets.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Si la méthode est appelée lorsque l’état d’un objet change, vous devez envisager de modifier la conception à utiliser le [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] modèle d’événement.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Supprimer un avertissement de cette règle si la méthode ne fonctionne pas avec le [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] modèle d’événement.



