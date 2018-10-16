---
title: 'CA2121 : Les constructeurs statiques doivent être privés | Microsoft Docs'
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
- CA2121
- StaticConstructorsShouldBePrivate
helpviewer_keywords:
- CA2121
- StaticConstructorsShouldBePrivate
ms.assetid: ee93c620-8fc1-4e47-866c-d389c3ca9f2e
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 9425cabbc024e445df97d9b909f1803b7a972571
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2018
ms.locfileid: "49267317"
---
# <a name="ca2121-static-constructors-should-be-private"></a>CA2121 : Les constructeurs statiques doivent être privés
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
|||
|-|-|
|TypeName|StaticConstructorsShouldBePrivate|
|CheckId|CA2121|
|Category|Microsoft.Security|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Un type a un constructeur statique qui n’est pas privé.

## <a name="rule-description"></a>Description de la règle
 Un constructeur statique, également appelé constructeur de classe, est utilisé pour initialiser un type. Le système appelle le constructeur statique avant la création de la première instance du type ou le référencement de tout membre statique. L’utilisateur n’a aucun contrôle sur quand le constructeur statique est appelé. Si un constructeur statique n’est pas privé, il peut être appelé par un code autre que le système. Selon les opérations effectuées dans le constructeur, cette possibilité peut provoquer un comportement inattendu.

 Cette règle est appliquée par les compilateurs c# et Visual Basic .NET.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Violations sont généralement provoquées par une des actions suivantes :

-   Vous défini un constructeur statique pour votre type et que vous n’avez pas effectué privé.

-   Le compilateur de langage de programmation ajouté un constructeur statique par défaut pour votre type et n’avez pas effectué privé.

 Pour résoudre le premier type de violation, rendez votre constructeur statique privé. Pour résoudre le second type, ajoutez un constructeur statique privé à votre type.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez pas ces violations. Si votre conception de logiciels requiert un appel explicite à un constructeur statique, il est probable qu’il contient de sérieux défauts et doivent être examinés.



