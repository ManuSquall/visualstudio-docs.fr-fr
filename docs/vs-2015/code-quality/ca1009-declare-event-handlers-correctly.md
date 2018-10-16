---
title: 'CA1009 : Déclarer les gestionnaires d’événements correctement | Microsoft Docs'
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
- CA1009
- DeclareEventHandlersCorrectly
helpviewer_keywords:
- CA1009
- DeclareEventHandlersCorrectly
ms.assetid: ab65c471-1449-49d2-9896-7b9af74284b4
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: c2833382ef8befa861a0947dd1c58e39bd69480f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49236676"
---
# <a name="ca1009-declare-event-handlers-correctly"></a>CA1009 : Déclarer les gestionnaires d'événements correctement
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|DeclareEventHandlersCorrectly|
|CheckId|CA1009|
|Category|Microsoft.Design|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Un délégué qui gère un événement public ou protégé n’a pas la signature correcte, de type de retour, ou les noms de paramètre.

## <a name="rule-description"></a>Description de la règle
 Les méthodes du gestionnaire d'événements acceptent deux paramètres. Le premier est de type <xref:System.Object?displayProperty=fullName> et est nommé 'sender'. Il s'agit de l'objet qui déclenche l'événement. Le deuxième paramètre est de type <xref:System.EventArgs?displayProperty=fullName> et est nommé « e ». Il s'agit des données qui sont associées à l'événement. Par exemple, si l’événement est déclenché chaque fois qu’un fichier est ouvert, les données d’événement contient généralement le nom du fichier.

 Méthodes de gestionnaire d’événements ne doivent pas retourner une valeur. Dans le langage de programmation c#, cela est indiqué par le type de retour `void`. Un gestionnaire d’événements peut appeler plusieurs méthodes dans plusieurs objets. Si les méthodes étaient autorisées à retourner une valeur, plusieurs valeurs de retour se produirait pour chaque événement, et seule la valeur de la dernière méthode a été appelée serait disponible.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, corrigez la signature, type de retour ou les noms de paramètre du délégué. Pour plus d’informations, consultez l’exemple suivant.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemple
 L’exemple suivant montre un délégué qui est adapté à la gestion des événements. Les méthodes qui peuvent être appelées par ce gestionnaire d’événements conformes à la signature spécifiée dans les instructions de conception. `AlarmEventHandler` est le nom de type du délégué. `AlarmEventArgs` dérive de la classe de base de données d’événement, <xref:System.EventArgs>, et contient les données d’événement d’alarme.

 [!code-cpp[FxCop.Design.EventsTwoParams#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.EventsTwoParams/cpp/FxCop.Design.EventsTwoParams.cpp#1)]
 [!code-csharp[FxCop.Design.EventsTwoParams#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.EventsTwoParams/cs/FxCop.Design.EventsTwoParams.cs#1)]
 [!code-vb[FxCop.Design.EventsTwoParams#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.EventsTwoParams/vb/FxCop.Design.EventsTwoParams.vb#1)]

## <a name="related-rules"></a>Règles associées
 [CA2109 : Passez en revue les gestionnaires d’événements visibles](../code-quality/ca2109-review-visible-event-handlers.md)

## <a name="see-also"></a>Voir aussi
 <xref:System.EventArgs?displayProperty=fullName> <xref:System.Object?displayProperty=fullName>
 [NIB : Événements et délégués](http://msdn.microsoft.com/en-us/d98fd58b-fa4f-4598-8378-addf4355a115)



