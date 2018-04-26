---
title: 'CA2212 : Ne marquez pas les composants pris en charge avec WebMethod'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 67d2e2790db4a3e8061dcd949b79c127e67f022d
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="ca2212-do-not-mark-serviced-components-with-webmethod"></a>CA2212 : Ne marquez pas les composants pris en charge avec WebMethod
|||
|-|-|
|TypeName|DoNotMarkServicedComponentsWithWebMethod|
|CheckId|CA2212|
|Category|Microsoft.Usage|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Une méthode dans un type qui hérite de <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName> est marquée avec <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>.

## <a name="rule-description"></a>Description de la règle
 <xref:System.Web.Services.WebMethodAttribute> s’applique aux méthodes au sein d’un service Web XML qui ont été créés à l’aide d’ASP.NET ; Il rend la méthode peut être appelée à partir de clients Web distants. La méthode et la classe doivent être publique et en cours d’exécution dans une application Web ASP.NET. <xref:System.EnterpriseServices.ServicedComponent> types sont hébergés par les applications COM + et peuvent utiliser les services COM +. <xref:System.Web.Services.WebMethodAttribute> n’est pas appliquée à <xref:System.EnterpriseServices.ServicedComponent> types, car elles ne sont pas prévues pour les mêmes scénarios. En particulier, en ajoutant l’attribut à la <xref:System.EnterpriseServices.ServicedComponent> méthode ne rend pas la méthode peut être appelée à partir de clients Web distants. Étant donné que <xref:System.Web.Services.WebMethodAttribute> et un <xref:System.EnterpriseServices.ServicedComponent> méthode ont des comportements incompatibles et la configuration requise pour le contexte et de flux de transaction, le comportement de la méthode est incorrect dans certains scénarios.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, supprimez l’attribut de la <xref:System.EnterpriseServices.ServicedComponent> (méthode).

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle. Il n’existe pas de scénarios où la combinaison de ces éléments est correct.

## <a name="see-also"></a>Voir aussi
 <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName> <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>