---
title: 'CA2121 : les constructeurs statiques doivent être privés | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2121
- StaticConstructorsShouldBePrivate
helpviewer_keywords:
- CA2121
- StaticConstructorsShouldBePrivate
ms.assetid: ee93c620-8fc1-4e47-866c-d389c3ca9f2e
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 7f95b33e1391ca755a6c0df261fa2bd05bd3c7a0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544311"
---
# <a name="ca2121-static-constructors-should-be-private"></a>CA2121 : Les constructeurs statiques doivent être privés
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Élément|Valeur|
|-|-|
|TypeName|StaticConstructorsShouldBePrivate|
|CheckId|CA2121|
|Category|Microsoft.Security|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause :
 Un type a un constructeur statique qui n’est pas privé.

## <a name="rule-description"></a>Description de la règle
 Un constructeur statique, également connu sous le nom de constructeur de classe, est utilisé pour initialiser un type. Le système appelle le constructeur statique avant la création de la première instance du type ou le référencement de tout membre statique. L’utilisateur n’a aucun contrôle sur le moment où le constructeur statique est appelé. Si un constructeur statique n’est pas privé, il peut être appelé par un code autre que le système. Selon les opérations effectuées dans le constructeur, cette possibilité peut provoquer un comportement inattendu.

 Cette règle est appliquée par les compilateurs C# et Visual Basic .NET.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Les violations sont généralement provoquées par l’une des actions suivantes :

- Vous avez défini un constructeur statique pour votre type et vous ne l’avez pas privé.

- Le compilateur du langage de programmation a ajouté un constructeur statique par défaut à votre type et ne l’a pas rend privé.

  Pour corriger le premier type de violation, rendez votre constructeur statique privé. Pour corriger le deuxième genre, ajoutez un constructeur statique privé à votre type.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez pas ces violations. Si votre conception de logiciel requiert un appel explicite à un constructeur statique, il est probable que la conception contient des défauts sérieux et qu’elle doit être examinée.
