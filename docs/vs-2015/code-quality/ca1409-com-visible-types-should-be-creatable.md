---
title: 'CA1409 : les types visibles par com doivent pouvoir être créés | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ComVisibleTypesShouldBeCreatable
- CA1409
helpviewer_keywords:
- ComVisibleTypesShouldBeCreatable
- CA1409
ms.assetid: 9f59569b-de15-4a38-b7cb-cff152972243
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 180a8d6bbc7f035fa0ae2eeafaa4e2c884cddc8d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547327"
---
# <a name="ca1409-com-visible-types-should-be-creatable"></a>CA1409 : Les types visibles par Com doivent pouvoir être créés
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Élément|Valeur|
|-|-|
|TypeName|ComVisibleTypesShouldBeCreatable|
|CheckId|CA1409|
|Category|Microsoft. Interoperability|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Un type référence qui est spécifiquement marqué comme visible par le modèle COM (Component Object Model) contient un constructeur public paramétré, mais ne contient pas de constructeur public par défaut (sans paramètre).

## <a name="rule-description"></a>Description de la règle
 Un type sans constructeur public par défaut ne peut pas être créé par des clients COM. Toutefois, les clients COM peuvent toujours accéder au type si un autre moyen est disponible pour créer le type et le passer au client (par exemple, via la valeur de retour d’un appel de méthode).

 La règle ignore les types dérivés de <xref:System.Delegate?displayProperty=fullName> .

 Par défaut, les éléments suivants sont visibles par COM : assemblys, les types publics, les membres d’instance publics dans les types publics et tous les membres des types valeur publics.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, ajoutez un constructeur public par défaut ou supprimez du <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> type.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer sans risque un avertissement de cette règle si d’autres méthodes sont fournies pour créer et passer l’objet au client COM.

## <a name="related-rules"></a>Règles associées
 [CA1017 : Marquer les assemblys avec ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>Voir aussi
 [Qualification des types .net pour l’interopérabilité](https://msdn.microsoft.com/library/4b8afb52-fb8d-4e65-b47c-fd82956a3cdd) [avec le code non managé](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
