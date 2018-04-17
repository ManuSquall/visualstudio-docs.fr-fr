---
title: 'CA1009 : Déclarer correctement les gestionnaires d’événements | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA1009
- DeclareEventHandlersCorrectly
helpviewer_keywords:
- CA1009
- DeclareEventHandlersCorrectly
ms.assetid: ab65c471-1449-49d2-9896-7b9af74284b4
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9d207bff88129cb9cc6769cc47ae6e70cbe74d1c
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="ca1009-declare-event-handlers-correctly"></a>CA1009 : Déclarer les gestionnaires d'événements correctement
|||  
|-|-|  
|TypeName|DeclareEventHandlersCorrectly|  
|CheckId|CA1009|  
|Category|Microsoft.Design|  
|Modification avec rupture|Rupture|  
  
## <a name="cause"></a>Cause  
 Un délégué qui gère un événement public ou protégé n’a pas de type de retour ou les noms de paramètres de la signature appropriée.  
  
## <a name="rule-description"></a>Description de la règle  
 Les méthodes du gestionnaire d'événements acceptent deux paramètres. Le premier est de type <xref:System.Object?displayProperty=fullName> et est nommé 'sender'. Il s'agit de l'objet qui déclenche l'événement. Le deuxième paramètre est de type <xref:System.EventArgs?displayProperty=fullName> et se nomme « e ». Il s'agit des données qui sont associées à l'événement. Par exemple, si l’événement est déclenché chaque fois qu’un fichier est ouvert, les données d’événement contient généralement le nom du fichier.  
  
 Méthodes de gestionnaire d’événements ne doivent pas retourner une valeur. Dans le langage de programmation c#, ceci est indiqué par le type de retour `void`. Un gestionnaire d’événements peut appeler plusieurs méthodes dans plusieurs objets. Si les méthodes étaient autorisées à retourner une valeur, plusieurs valeurs de retour sont produit pour chaque événement, et seulement la valeur de la dernière méthode appelée serait disponible.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour corriger une violation de cette règle, corrigez la signature, type de retour ou les noms de paramètre du délégué. Pour plus d’informations, consultez l’exemple suivant.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre un délégué qui est adapté à la gestion des événements. Les méthodes qui peuvent être appelées par ce gestionnaire d’événements est conforme à la signature spécifiée dans les règles de conception. `AlarmEventHandler` est le nom de type du délégué. `AlarmEventArgs` dérive de la classe de base de données d’événement, <xref:System.EventArgs>, et contient les données d’événement d’alarme.  
  
 [!code-cpp[FxCop.Design.EventsTwoParams#1](../code-quality/codesnippet/CPP/ca1009-declare-event-handlers-correctly_1.cpp)]
 [!code-csharp[FxCop.Design.EventsTwoParams#1](../code-quality/codesnippet/CSharp/ca1009-declare-event-handlers-correctly_1.cs)]
 [!code-vb[FxCop.Design.EventsTwoParams#1](../code-quality/codesnippet/VisualBasic/ca1009-declare-event-handlers-correctly_1.vb)]  
  
## <a name="related-rules"></a>Règles associées  
 [CA2109 : Passez en revue les gestionnaires d’événements visibles](../code-quality/ca2109-review-visible-event-handlers.md)  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.EventArgs?displayProperty=fullName>   
 <xref:System.Object?displayProperty=fullName>   
 [Gestion et déclenchement d’événements](/dotnet/standard/events/index)  