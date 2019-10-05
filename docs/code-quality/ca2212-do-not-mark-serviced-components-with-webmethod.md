---
title: 'CA2212 : Ne marquez pas les composants pris en charge avec webMethod'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2212
- DoNotMarkServicedComponentsWithWebMethod
helpviewer_keywords:
- CA2212
- DoNotMarkServicedComponentsWithWebMethod
ms.assetid: 774bc55d-e588-48ee-8f38-c228580feca2
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7b2ace5f6e51fc7a8d29faab14cc2332fd808f93
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231654"
---
# <a name="ca2212-do-not-mark-serviced-components-with-webmethod"></a>CA2212 : Ne marquez pas les composants pris en charge avec webMethod

|||
|-|-|
|TypeName|DoNotMarkServicedComponentsWithWebMethod|
|CheckId|CA2212|
|Category|Microsoft.Usage|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause

Une méthode d’un type qui hérite de <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName> est marquée avec <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>.

## <a name="rule-description"></a>Description de la règle

<xref:System.Web.Services.WebMethodAttribute>s’applique aux méthodes d’un service Web XML qui ont été créées à l’aide de ASP.NET ; elle rend l’appel de la méthode à partir des clients Web distants. La méthode et la classe doivent être publiques et s’exécuter dans une application Web ASP.NET. <xref:System.EnterpriseServices.ServicedComponent>les types sont hébergés par des applications COM+ et peuvent utiliser des services COM+. <xref:System.Web.Services.WebMethodAttribute>n’est pas appliqué <xref:System.EnterpriseServices.ServicedComponent> aux types, car ils ne sont pas destinés aux mêmes scénarios. Plus précisément, l’ajout de l' <xref:System.EnterpriseServices.ServicedComponent> attribut à la méthode ne rend pas l’appel de la méthode à partir des clients Web distants. Étant <xref:System.Web.Services.WebMethodAttribute> donné que <xref:System.EnterpriseServices.ServicedComponent> et une méthode ont des comportements et des exigences en conflit pour le contexte et le workflow de transaction, le comportement de la méthode est incorrect dans certains scénarios.

## <a name="how-to-fix-violations"></a>Comment corriger les violations

Pour corriger une violation de cette règle, supprimez l’attribut de <xref:System.EnterpriseServices.ServicedComponent> la méthode.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements

Ne supprimez aucun avertissement de cette règle. Il n’existe aucun scénario dans lequel la combinaison de ces éléments est correcte.

## <a name="see-also"></a>Voir aussi

- <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName>
- <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>