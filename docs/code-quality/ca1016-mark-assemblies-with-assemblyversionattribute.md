---
title: "CA1016 : Marquer les assemblys avec AssemblyVersionAttribute | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- MarkAssembliesWithAssemblyVersion
- CA1016
helpviewer_keywords:
- CA1016
- MarkAssembliesWithAssemblyVersion
ms.assetid: 4340aed8-d92b-4cde-a398-cb6963c6da5a
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 414a533e781be82cd0ffef1e9db234738ef07f16
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2017
---
# <a name="ca1016-mark-assemblies-with-assemblyversionattribute"></a>CA1016 : Marquer les assemblys avec AssemblyVersionAttribute
|||  
|-|-|  
|TypeName|MarkAssembliesWithAssemblyVersion|  
|CheckId|CA1016|  
|Catégorie|Microsoft.Design|  
|Modification avec rupture|Sans rupture|  
  
## <a name="cause"></a>Cause  
 L’assembly n’a pas un numéro de version.  
  
## <a name="rule-description"></a>Description de la règle  
 L’identité d’un assembly est composée des informations suivantes :  
  
-   Nom de l'assembly  
  
-   Numéro de version  
  
-   Culture  
  
-   Clé publique (pour les assemblys à nom fort).  
  
 Le [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] utilise le numéro de version pour identifier un assembly de manière unique, et créer une liaison avec des types présents dans des assemblys à nom fort. Le numéro de version est utilisé conjointement avec la version et la stratégie d'éditeur. Par défaut, les applications s'exécutent uniquement avec la version d'assembly avec laquelle elles ont été construites.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour corriger une violation de cette règle, ajouter un numéro de version à l’assembly à l’aide de la <xref:System.Reflection.AssemblyVersionAttribute?displayProperty=fullName> attribut. Lisez l'exemple suivant.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle pour les assemblys qui sont utilisés par des tiers, ou dans un environnement de production.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre un assembly qui a le <xref:System.Reflection.AssemblyVersionAttribute> attribut appliqué.  
  
 [!code-csharp[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/CSharp/ca1016-mark-assemblies-with-assemblyversionattribute_1.cs)]
 [!code-vb[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/VisualBasic/ca1016-mark-assemblies-with-assemblyversionattribute_1.vb)]
 [!code-cpp[FxCop.Design.AssembliesVersion#1](../code-quality/codesnippet/CPP/ca1016-mark-assemblies-with-assemblyversionattribute_1.cpp)]  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des versions des assemblys](/dotnet/framework/app-domains/assembly-versioning)   
 [Comment : créer une stratégie d'éditeur](/dotnet/framework/configure-apps/how-to-create-a-publisher-policy)