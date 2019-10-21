---
title: 'Ca2212 : ne Marquez pas les composants de service avec WebMethod | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2212
- DoNotMarkServicedComponentsWithWebMethod
helpviewer_keywords:
- CA2212
- DoNotMarkServicedComponentsWithWebMethod
ms.assetid: 774bc55d-e588-48ee-8f38-c228580feca2
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 2ee166f8bbc14e66968cd4f7c265331854905ac9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662947"
---
# <a name="ca2212-do-not-mark-serviced-components-with-webmethod"></a>CA2212 : Ne marquez pas les composants pris en charge avec WebMethod
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotMarkServicedComponentsWithWebMethod|
|CheckId|CA2212|
|Category|Microsoft. usage|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Une méthode d’un type qui hérite de <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName> est marquée avec <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>.

## <a name="rule-description"></a>Description de la règle
 <xref:System.Web.Services.WebMethodAttribute> s’applique aux méthodes au sein d’un service Web XML qui ont été créées à l’aide de ASP.NET ; elle rend l’appel de la méthode à partir des clients Web distants. La méthode et la classe doivent être publiques et s’exécuter dans une application Web ASP.NET. les types <xref:System.EnterpriseServices.ServicedComponent> sont hébergés par des applications COM+ et peuvent utiliser des services COM+. <xref:System.Web.Services.WebMethodAttribute> n’est pas appliqué aux types <xref:System.EnterpriseServices.ServicedComponent>, car ils ne sont pas destinés aux mêmes scénarios. Plus précisément, l’ajout de l’attribut à la méthode <xref:System.EnterpriseServices.ServicedComponent> ne rend pas l’appel de la méthode à partir des clients Web distants. Étant donné que <xref:System.Web.Services.WebMethodAttribute> et une méthode <xref:System.EnterpriseServices.ServicedComponent> ont des comportements et des exigences en conflit pour le contexte et le workflow de transaction, le comportement de la méthode est incorrect dans certains scénarios.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, supprimez l’attribut de la méthode <xref:System.EnterpriseServices.ServicedComponent>.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle. Il n’existe aucun scénario dans lequel la combinaison de ces éléments est correcte.

## <a name="see-also"></a>Voir aussi
 <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName> <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>
