---
title: 'CA2212 : Ne marquez pas les composants pris en charge avec WebMethod | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2212
- DoNotMarkServicedComponentsWithWebMethod
helpviewer_keywords:
- CA2212
- DoNotMarkServicedComponentsWithWebMethod
ms.assetid: 774bc55d-e588-48ee-8f38-c228580feca2
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 695cf05f1407f7a463f210c920e54148c49b3ef3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49847043"
---
# <a name="ca2212-do-not-mark-serviced-components-with-webmethod"></a>CA2212 : Ne marquez pas les composants pris en charge avec WebMethod
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotMarkServicedComponentsWithWebMethod|
|CheckId|CA2212|
|Category|Microsoft.Usage|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Une méthode dans un type qui hérite de <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName> est marquée avec <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>.

## <a name="rule-description"></a>Description de la règle
 <xref:System.Web.Services.WebMethodAttribute> s’applique aux méthodes au sein d’un service Web XML créés à l’aide d’ASP.NET ; rend la méthode pouvant être appelé à partir de clients Web distants. La méthode et la classe doivent être publique et en cours d’exécution dans une application Web ASP.NET. <xref:System.EnterpriseServices.ServicedComponent> types sont hébergés par les applications COM + et peuvent utiliser les services COM +. <xref:System.Web.Services.WebMethodAttribute> n’est pas appliquée à <xref:System.EnterpriseServices.ServicedComponent> car elles ne sont pas destinées aux mêmes scénarios. Plus précisément, ajout de l’attribut à la <xref:System.EnterpriseServices.ServicedComponent> méthode ne fait pas la méthode pouvant être appelé à partir de clients Web distants. Étant donné que <xref:System.Web.Services.WebMethodAttribute> et un <xref:System.EnterpriseServices.ServicedComponent> méthode ont des comportements en conflit et la configuration requise pour le contexte et les flux de transaction, le comportement de la méthode est incorrect dans certains scénarios.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, supprimez l’attribut à partir de la <xref:System.EnterpriseServices.ServicedComponent> (méthode).

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle. Il n’existe aucun scénario où la combinaison de ces éléments est correct.

## <a name="see-also"></a>Voir aussi
 <xref:System.EnterpriseServices.ServicedComponent?displayProperty=fullName> <xref:System.Web.Services.WebMethodAttribute?displayProperty=fullName>



