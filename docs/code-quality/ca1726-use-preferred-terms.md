---
title: 'CA1726 : Utilisez les termes | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- UsePreferredTerms
- CA1726
helpviewer_keywords:
- UsePreferredTerms
ms.assetid: 642b2acd-3a33-4d1f-b0a7-67073ae73be2
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5e37ed041d03e82a63929a7bc525c73ea4062333
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="ca1726-use-preferred-terms"></a>CA1726 : Utilisez les termes par défaut
|||  
|-|-|  
|TypeName|UsePreferredTerms|  
|CheckId|CA1726|  
|Category|Microsoft.Naming|  
|Modification avec rupture|Avec rupture - lorsque déclenchée sur les assemblys<br /><br /> Sans rupture - lorsque déclenchée sur les paramètres de type|  
  
## <a name="cause"></a>Cause  
 Le nom d'un identificateur visible de l'extérieur contient un terme pour lequel un autre terme par défaut existe. Vous pouvez également le nom comprend le terme indicateur ou indicateurs.  
  
## <a name="rule-description"></a>Description de la règle  
 Cette règle analyse un identificateur dans des jetons. Chaque jeton unique et chaque combinaison de jetons doubles contigu sont comparée à des termes qui sont générés dans la règle et dans la section déconseillé des dictionnaires personnalisés. Le tableau suivant présente les termes qui sont intégrées à la règle et leurs solutions de remplacement par défaut.  
  
|Terme obsolète|Terme favori|  
|-------------------|--------------------|  
|ne sont pas|Ne sont pas|  
|Annulé|Canceled|  
|Impossible|Ne peut pas|  
|ComPlus|EnterpriseServices|  
|Couldnt|N’a pas pu|  
|N’a pas|DidNot|  
|Lecteur|Ne|  
|Ne pas|Ne pas|  
|Indicateur ou indicateurs|Il n’existe aucun terme de remplacement. Ne pas utiliser.|  
|n’était pas|HadNot|  
|N’a pas|HasNot|  
|ne l’avez pas|HaveNot|  
|Indices|Index|  
|n’est pas|IsNot|  
|Connexion|Ouverture de session|  
|Déconnexion|Fermeture de session|  
|Shouldnt|ShouldNot|  
|Authentification|Ouverture de session|  
|Approbation|Déconnexion|  
|Wasnt|WasNot|  
|n’ont pas été|N’ont pas été|  
|Impossible|WillNot|  
|Wouldnt|WouldNot|  
|Accessible en écriture|Accessible en écriture|  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour corriger une violation de cette règle, remplacez le terme par le terme de remplacement par défaut.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Supprimer un avertissement de cette règle uniquement si le nom de l’identificateur se rapporte intentionnellement et spécifiquement au terme d’origine au lieu du terme favori.  
  
## <a name="related-rules"></a>Règles associées  
 [Avertissements liés à l’affectation de noms](../code-quality/naming-warnings.md)