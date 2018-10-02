---
title: 'CA1726 : Utilisez les termes par défaut | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- UsePreferredTerms
- CA1726
helpviewer_keywords:
- UsePreferredTerms
ms.assetid: 642b2acd-3a33-4d1f-b0a7-67073ae73be2
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: b13c43a563a158a2eeb8484e29810c5b91d110aa
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2018
ms.locfileid: "47494774"
---
# <a name="ca1726-use-preferred-terms"></a>CA1726 : Utilisez les termes par défaut
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pour obtenir la dernière documentation sur Visual Studio 2017, consultez [CA1726 : utilisez les termes préférés](https://docs.microsoft.com/visualstudio/code-quality/ca1726-use-preferred-terms) sur docs.microsoft.com.  
  
|||  
|-|-|  
|TypeName|UsePreferredTerms|  
|CheckId|CA1726|  
|Category|Microsoft.Naming|  
|Modification avec rupture|Rupture - lorsque déclenchée sur les assemblys<br /><br /> Sans rupture - lorsque déclenchée sur les paramètres de type|  
  
## <a name="cause"></a>Cause  
 Le nom d'un identificateur visible de l'extérieur contient un terme pour lequel un autre terme par défaut existe. Vous pouvez également le nom inclut le terme indicateur ou indicateurs.  
  
## <a name="rule-description"></a>Description de la règle  
 Cette règle analyse un identificateur dans des jetons. Chaque jeton unique et chaque combinaison de jetons doubles contigus sont comparés aux termes qui sont intégrés dans la règle et dans la section déconseillé des dictionnaires personnalisés. Le tableau suivant présente les termes qui sont intégrées dans la règle et leurs solutions de remplacement par défaut.  
  
|Terme obsolète|Terme favori|  
|-------------------|--------------------|  
|ne sont pas|Ne sont pas|  
|Annulé|Canceled|  
|Ne peut pas|Ne peut pas|  
|ComPlus|EnterpriseServices|  
|Impossible|N’a pas pu|  
|N’a pas|DidNot|  
|Lecteur|Ne|  
|Non|Ne pas connecter|  
|Indicateur ou indicateurs|Il n’existe aucun terme de remplacement. Ne pas utiliser.|  
|n’avait pas|HadNot|  
|N’a pas encore|HasNot|  
|ne l’avez pas|HaveNot|  
|Indices|Index|  
|n’est pas|IsNot|  
|Connexion|Ouverture de session|  
|Déconnexion|Fermeture de session|  
|Shouldnt|ShouldNot|  
|Authentification|Connexion|  
|Approbation|Déconnexion|  
|Wasnt|WasNot|  
|n’ont pas été|N’ont pas été|  
|Ne doit pas|WillNot|  
|Wouldnt|WouldNot|  
|Accessible en écriture|Accessible en écriture|  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour corriger une violation de cette règle, remplacez le terme par le terme de remplacement par défaut.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Supprimez un avertissement de cette règle uniquement si le nom de l’identificateur se rapporte intentionnellement et spécifiquement au terme d’origine au lieu du terme favori.  
  
## <a name="related-rules"></a>Règles associées  
 [Avertissements liés à l’affectation de noms](../code-quality/naming-warnings.md)

