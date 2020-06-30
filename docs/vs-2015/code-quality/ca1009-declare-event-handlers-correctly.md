---
title: 'CA1009 : déclarer les gestionnaires d’événements correctement | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1009
- DeclareEventHandlersCorrectly
helpviewer_keywords:
- CA1009
- DeclareEventHandlersCorrectly
ms.assetid: ab65c471-1449-49d2-9896-7b9af74284b4
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 6a4a4e2e6990772b50568043c4d18ff29248571d
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547886"
---
# <a name="ca1009-declare-event-handlers-correctly"></a>CA1009 : Déclarer les gestionnaires d'événements correctement
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Élément|Valeur|
|-|-|
|TypeName|DeclareEventHandlersCorrectly|
|CheckId|CA1009|
|Category|Microsoft. Design|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Un délégué qui gère un événement public ou protégé n’a pas la signature, le type de retour ou les noms de paramètres appropriés.

## <a name="rule-description"></a>Description de la règle
 Les méthodes du gestionnaire d'événements acceptent deux paramètres. Le premier est de type <xref:System.Object?displayProperty=fullName> et est nommé’sender'. Il s'agit de l'objet qui déclenche l'événement. Le deuxième paramètre est de type <xref:System.EventArgs?displayProperty=fullName> et est nommé’e'. Il s'agit des données qui sont associées à l'événement. Par exemple, si l’événement est déclenché chaque fois qu’un fichier est ouvert, les données d’événement contiennent généralement le nom du fichier.

 Les méthodes de gestionnaire d’événements ne doivent pas retourner de valeur. Dans le langage de programmation C#, cela est indiqué par le type de retour `void` . Un gestionnaire d’événements peut appeler plusieurs méthodes dans plusieurs objets. Si les méthodes étaient autorisées à retourner une valeur, plusieurs valeurs de retour se produiront pour chaque événement, et seule la valeur de la dernière méthode appelée serait disponible.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, corrigez la signature, le type de retour ou les noms de paramètres du délégué. Pour plus d’informations, consultez l’exemple suivant.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemple
 L’exemple suivant montre un délégué qui est adapté à la gestion des événements. Les méthodes qui peuvent être appelées par ce gestionnaire d’événements sont conformes à la signature spécifiée dans les règles de conception. `AlarmEventHandler`est le nom de type du délégué. `AlarmEventArgs`dérive de la classe de base pour les données d’événement, <xref:System.EventArgs> et contient les données d’événement d’alarme.

 [!code-cpp[FxCop.Design.EventsTwoParams#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.EventsTwoParams/cpp/FxCop.Design.EventsTwoParams.cpp#1)]
 [!code-csharp[FxCop.Design.EventsTwoParams#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.EventsTwoParams/cs/FxCop.Design.EventsTwoParams.cs#1)]
 [!code-vb[FxCop.Design.EventsTwoParams#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.EventsTwoParams/vb/FxCop.Design.EventsTwoParams.vb#1)]

## <a name="related-rules"></a>Règles associées
 [CA2109 : Passez en revue les gestionnaires d'événements visibles](../code-quality/ca2109-review-visible-event-handlers.md)

## <a name="see-also"></a>Voir aussi
 <xref:System.EventArgs?displayProperty=fullName> <xref:System.Object?displayProperty=fullName>
 [PLUME : événements et délégués](https://msdn.microsoft.com/d98fd58b-fa4f-4598-8378-addf4355a115)
