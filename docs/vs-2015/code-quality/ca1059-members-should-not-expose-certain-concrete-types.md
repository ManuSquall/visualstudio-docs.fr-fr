---
title: 'CA1059 : Les membres ne doivent pas exposer certains types concrets | Microsoft Docs'
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
- CA1059
- MembersShouldNotExposeCertainConcreteTypes
helpviewer_keywords:
- MembersShouldNotExposeCertainConcreteTypes
- CA1059
ms.assetid: 59f61f52-8d6c-49cb-aefb-191910523a3c
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 894b4c22aaab2b0cce81053e6466b791a50b089a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49816883"
---
# <a name="ca1059-members-should-not-expose-certain-concrete-types"></a>CA1059 : Les membres ne doivent pas exposer certains types concrets
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MembersShouldNotExposeCertainConcreteTypes|
|CheckId|CA1059|
|Category|Microsoft.Design|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Un membre extérieurement visible est un certain type concret ou expose certains types concrets via un de ses paramètres ou valeur de retour. Actuellement, cette règle signale l’exposition des types concrets suivants :

-   Un type dérivé <xref:System.Xml.XmlNode?displayProperty=fullName>.

## <a name="rule-description"></a>Description de la règle
 Un type concret est un type qui présente une implémentation complète et, par conséquent, peut être instancié. Pour permettre une utilisation généralisée du membre, remplacez le type concret par l’interface suggérée. Ainsi, le membre à accepter tout type qui implémente l’interface ou être utilisés là où un type qui implémente l’interface est attendu.

 Le tableau suivant répertorie les types concrets ciblés et leurs remplacements suggérés.

|Type concret|Replacement|
|-------------------|-----------------|
|<xref:System.Xml.XPath.XPathDocument>|<xref:System.Xml.XPath.IXPathNavigable?displayProperty=fullName>.<br /><br /> À l’aide de l’interface découple le membre d’une implémentation spécifique d’une source de données XML.|

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, modifiez le type concret par l’interface suggérée.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Il est possible de supprimer un message à partir de cette règle si la fonctionnalité spécifique fournie par le type concret est requise.

## <a name="related-rules"></a>Règles associées
 [CA1011 : Envisagez de passer les types de base comme paramètres](../code-quality/ca1011-consider-passing-base-types-as-parameters.md)



