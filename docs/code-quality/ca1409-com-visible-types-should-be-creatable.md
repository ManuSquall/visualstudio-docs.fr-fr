---
title: "CA1409 : Les types visibles par Com doivent être créés | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ComVisibleTypesShouldBeCreatable
- CA1409
helpviewer_keywords:
- ComVisibleTypesShouldBeCreatable
- CA1409
ms.assetid: 9f59569b-de15-4a38-b7cb-cff152972243
caps.latest.revision: "18"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: f12dda380f887aca50b764d0ec20f9db1c0cd07c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="ca1409-com-visible-types-should-be-creatable"></a>CA1409 : Les types visibles par COM doivent pouvoir être créés
|||  
|-|-|  
|TypeName|ComVisibleTypesShouldBeCreatable|  
|CheckId|CA1409|  
|Category|Microsoft.Interoperability|  
|Modification avec rupture|Sans rupture|  
  
## <a name="cause"></a>Cause  
 Un type référence marqué spécifiquement comme visible pour COM Component Object Model () contient un constructeur public paramétré, mais ne contient pas de constructeur public par défaut (sans paramètre).  
  
## <a name="rule-description"></a>Description de la règle  
 Impossible de créer un type sans constructeur public par défaut par les clients COM. Toutefois, le type toujours accessibles par les clients COM si un autre moyen est disponible pour créer le type et le passer au client (par exemple, via la valeur de retour d’un appel de méthode).  
  
 La règle ignore les types qui sont dérivés de <xref:System.Delegate?displayProperty=fullName>.  
  
 Par défaut, les éléments suivants sont visibles par COM : assemblys, types publics, membres d’instance publics dans des types publics et tous les membres de types valeur publics.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour corriger une violation de cette règle, ajoutez un constructeur public par défaut ou supprimez le <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> à partir du type.  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Il est possible de supprimer un avertissement de cette règle si d’autres moyens sont fournis pour créer et passez l’objet vers le client COM sans.  
  
## <a name="related-rules"></a>Règles associées  
 [CA1017 : Marquez les assemblys avec ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Qualification des types .NET pour l’interopérabilité](/dotnet/framework/interop/qualifying-net-types-for-interoperation)   
 [Interopération avec du code non managé](/dotnet/framework/interop/index)