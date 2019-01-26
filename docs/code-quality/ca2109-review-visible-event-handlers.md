---
title: "CA2109 : Passez en revue les gestionnaires d'événements visibles"
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA2109
- ReviewVisibleEventHandlers
helpviewer_keywords:
- ReviewVisibleEventHandlers
- CA2109
ms.assetid: 8f8fa0ee-e94e-400e-b516-24d8727725d7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a3b0cb900b2a59e2c52ca2f00ee1573116dc5fe5
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55029685"
---
# <a name="ca2109-review-visible-event-handlers"></a>CA2109 : Passez en revue les gestionnaires d'événements visibles

|||
|-|-|
|TypeName|ReviewVisibleEventHandlers|
|CheckId|CA2109|
|Category|Microsoft.Security|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Une méthode de gestion d’événements publique ou protégée a été détectée.

## <a name="rule-description"></a>Description de la règle
 Une méthode visible de l’extérieur de la gestion des événements présente un problème de sécurité qui requiert une révision.

N’exposez pas les méthodes de gestion des événements, sauf si cela est absolument nécessaire. Un gestionnaire d’événements, un type délégué, qui appelle la méthode exposée peut être ajouté à n’importe quel événement, à condition que le gestionnaire et événements les signatures correspondent. Événements peuvent potentiellement être déclenchés par n’importe quel code et sont souvent déclenchés par le code système hautement fiable en réponse aux actions utilisateur comme un clic sur un bouton. Ajout d’une vérification de sécurité à une méthode de gestion d’événements n’empêche pas de code à partir de l’inscription d’un gestionnaire d’événements qui appelle la méthode.

 Une demande ne peut pas protéger de manière fiable une méthode appelée par un gestionnaire d’événements. Demandes de sécurité contribuent protéger le code contre les appelants non fiables en examinant les appelants sur la pile des appels. Code qui ajoute un gestionnaire d’événements à un événement n’est pas nécessairement présent sur la pile des appels lorsque les méthodes de gestionnaire d’événements sont exécutées. Par conséquent, la pile des appels peut avoir uniquement hautement approuvé les appelants lorsque la méthode de gestionnaire d’événements est appelée. Cela entraîne des demandes faites par la méthode de gestionnaire d’événements réussisse. En outre, l’autorisation demandée peut être déclarée lorsque la méthode est appelée. Pour ces raisons, le risque de correction d’une violation de cette règle ne peut être évalué après avoir examiné la méthode de gestion des événements. Lorsque vous examinez votre code, considérez les points suivants :

- Votre gestionnaire d’événements effectue des opérations dangereuses ou exploitables, telles que la déclaration d’autorisations ou la suppression des autorisations de code non managé ?

- Quelles sont les menaces de sécurité vers et à partir de votre code, car il peut s’exécuter à tout moment avec uniquement hautement approuvé les appelants sur la pile ?

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, examinez la méthode et évaluez les éléments suivants :

- Vous pouvez rendre la méthode de gestion des événements non publics ?

- Vous pouvez déplacer toutes les fonctionnalités dangereuses hors du Gestionnaire d’événements ?

- Si une demande de sécurité est imposée, il est possible d’une autre manière ?

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Supprimez un avertissement de cette règle uniquement après un examen minutieux de la sécurité pour vous assurer que votre code ne constitue pas une menace de sécurité.

## <a name="example"></a>Exemple
 Le code suivant montre une méthode de gestion d’événements qui permettre être utilisés à mauvais escient par du code malveillant.

 [!code-csharp[FxCop.Security.EventSecLib#1](../code-quality/codesnippet/CSharp/ca2109-review-visible-event-handlers_1.cs)]

## <a name="see-also"></a>Voir aussi

- <xref:System.Security.CodeAccessPermission.Demand%2A?displayProperty=fullName>
- <xref:System.EventArgs?displayProperty=fullName>