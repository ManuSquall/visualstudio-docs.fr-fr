---
title: "CA1053 : Les types de conteneurs statiques ne doivent pas avoir de constructeurs | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- StaticHolderTypesShouldNotHaveConstructors
- CA1053
helpviewer_keywords:
- CA1053
- StaticHolderTypesShouldNotHaveConstructors
ms.assetid: 10302b9a-fa5e-4935-a06a-513d9600f613
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a9e9d6272fbb21644daab96bb3ccd7d02b023840
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="ca1053-static-holder-types-should-not-have-constructors"></a>CA1053 : Les types de conteneurs statiques ne doivent pas comporter de constructeur
|||  
|-|-|  
|TypeName|StaticHolderTypesShouldNotHaveConstructors|  
|CheckId|CA1053|  
|Catégorie|Microsoft.Design|  
|Modification avec rupture|Rupture|  
  
## <a name="cause"></a>Cause  
 Un type public ou imbriqué déclare uniquement des membres statiques et dispose d'un constructeur par défaut public ou protégé.  
  
## <a name="rule-description"></a>Description de la règle  
 Le constructeur est inutile car l'appel à des membres statiques ne requiert aucune instance du type. En outre, étant donné que le type n’a pas de membres non statiques, création d’une instance ne donne pas accès à un des membres du type.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour corriger une violation de cette règle, supprimez le constructeur par défaut ou rendez-le privé.  
  
> [!NOTE]
>  Certains compilateurs créent automatiquement un constructeur public par défaut si le type ne définit pas de constructeur. Si c’est le cas avec le type, ajoutez un constructeur par défaut privé pour éliminer la violation.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle. La présence du constructeur suggère que le type n’est pas un type static.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre un type qui viole cette règle. Notez qu’il n’y a aucun constructeur par défaut dans le code source. Lorsque ce code est compilé dans un assembly, le compilateur c# insérera un constructeur par défaut, ce qui enfreint cette règle. Pour corriger cela, déclarez un constructeur privé.  
  
 [!code-csharp[FxCop.Design.StaticTypes#1](../code-quality/codesnippet/CSharp/ca1053-static-holder-types-should-not-have-constructors_1.cs)]