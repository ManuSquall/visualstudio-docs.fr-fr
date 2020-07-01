---
title: 'CA2109 : passez en revue les gestionnaires d’événements visibles | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2109
- ReviewVisibleEventHandlers
helpviewer_keywords:
- ReviewVisibleEventHandlers
- CA2109
ms.assetid: 8f8fa0ee-e94e-400e-b516-24d8727725d7
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 3ddcab6e0f416837bcd7b01521a6d77ddce691b9
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85520976"
---
# <a name="ca2109-review-visible-event-handlers"></a>CA2109 : Passez en revue les gestionnaires d'événements visibles
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Élément|Valeur|
|-|-|
|TypeName|ReviewVisibleEventHandlers|
|CheckId|CA2109|
|Category|Microsoft.Security|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Une méthode de gestion d’événements publique ou protégée a été détectée.

## <a name="rule-description"></a>Description de la règle
 Une méthode de gestion des événements visible de l’extérieur présente un problème de sécurité qui nécessite une révision.

 Les méthodes de gestion d’événements ne doivent pas être exposées sauf nécessité absolue. Un gestionnaire d’événements, un type délégué, qui appelle la méthode exposée peut être ajouté à n’importe quel événement à condition que le gestionnaire et les signatures d’événements correspondent. Les événements peuvent potentiellement être déclenchés par n’importe quel code, et sont souvent déclenchés par du code système hautement fiable en réponse aux actions de l’utilisateur, telles que le clic sur un bouton. L’ajout d’une vérification de sécurité à une méthode de gestion des événements n’empêche pas le code d’inscrire un gestionnaire d’événements qui appelle la méthode.

 Une demande ne peut pas protéger de manière fiable une méthode appelée par un gestionnaire d’événements. Les demandes de sécurité aident à protéger le code contre les appelants non fiables en examinant les appelants sur la pile des appels. Le code qui ajoute un gestionnaire d’événements à un événement n’est pas nécessairement présent sur la pile des appels lorsque les méthodes du gestionnaire d’événements s’exécutent. Par conséquent, la pile des appels peut avoir uniquement des appelants d’un niveau de confiance élevé quand la méthode du gestionnaire d’événements est appelée. Cela entraîne la permutation des demandes effectuées par la méthode de gestionnaire d’événements. En outre, l’autorisation demandée peut être déclarée lorsque la méthode est appelée. Pour ces raisons, le risque de ne pas corriger une violation de cette règle ne peut être évalué qu’après examen de la méthode de gestion des événements. Lorsque vous examinez votre code, tenez compte des points suivants :

- Votre gestionnaire d’événements effectue-t-il des opérations dangereuses ou exploitables, telles que l’assertion des autorisations ou la suppression de l’autorisation de code non managé ?

- Quelles sont les menaces de sécurité liées à votre code et qui peuvent être exécutées à tout moment, avec uniquement des appelants ayant un niveau de confiance élevé sur la pile ?

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, passez en revue la méthode et évaluez les éléments suivants :

- Pouvez-vous rendre la méthode de gestion des événements non publique ?

- Pouvez-vous déplacer toutes les fonctionnalités dangereuses hors du gestionnaire d’événements ?

- Si une demande de sécurité est imposée, peut-il être accompli d’une autre manière ?

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Supprimez un avertissement de cette règle uniquement après un examen minutieux de la sécurité pour vous assurer que votre code ne constitue pas une menace pour la sécurité.

## <a name="example"></a>Exemple
 Le code suivant illustre une méthode de gestion des événements qui peut être utilisée à des fins malveillantes par du code malveillant.

 [!code-csharp[FxCop.Security.EventSecLib#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.EventSecLib/cs/FxCop.Security.EventSecLib.cs#1)]

## <a name="see-also"></a>Voir aussi
 <xref:System.Security.CodeAccessPermission.Demand%2A?displayProperty=fullName> <xref:System.EventArgs?displayProperty=fullName>
 [Demandes de sécurité](https://msdn.microsoft.com/324c14f8-54ff-494d-9fd1-bfd20962c8ba)
