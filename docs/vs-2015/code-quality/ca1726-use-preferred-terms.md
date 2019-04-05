---
title: 'CA1726 : Utilisez les termes préférés | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
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
ms.openlocfilehash: e31c459d2d5ce8dc114605716c09f8360eca23d3
ms.sourcegitcommit: 3201da3499051768ab59f492699a9049cbc5c3c6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/22/2019
ms.locfileid: "59001843"
---
# <a name="ca1726-use-preferred-terms"></a>CA1726 : Utilisez les termes par défaut
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pour obtenir la dernière documentation sur Visual Studio, consultez [CA1726 : Utiliser des termes](https://docs.microsoft.com/visualstudio/code-quality/ca1726-use-preferred-terms) sur docs.microsoft.com.  
  
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
|ne sont pas|AreNot|  
|Annulé|Canceled|  
|Ne peut pas|Ne peut pas|  
|ComPlus|EnterpriseServices|  
|Impossible|CouldNot|  
|Didnt|DidNot|  
|Lecteur|DoesNot|  
|Dont|DoNot|  
|Indicateur ou indicateurs|Il n’existe aucun terme de remplacement. Ne pas utiliser.|  
|Hadnt|HadNot|  
|N’a pas encore|HasNot|  
|ne l’avez pas|HaveNot|  
|Indices|Index|  
|Isnt|IsNot|  
|LogIn|LogOn|  
|LogOut|LogOff|  
|Shouldnt|ShouldNot|  
|SignOn|SignIn|  
|SignOff|SignOut|  
|Wasnt|WasNot|  
|n’ont pas été|WereNot|  
|Ne doit pas|WillNot|  
|Wouldnt|WouldNot|  
|Accessible en écriture|Accessible en écriture|  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour corriger une violation de cette règle, remplacez le terme par le terme de remplacement par défaut.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Supprimez un avertissement de cette règle uniquement si le nom de l’identificateur se rapporte intentionnellement et spécifiquement au terme d’origine au lieu du terme favori.  
  
## <a name="related-rules"></a>Règles associées  
 [Avertissements liés à l’affectation de noms](../code-quality/naming-warnings.md)
