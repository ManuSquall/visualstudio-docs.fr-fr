---
title: 'CA1504 : Vérifier les noms de champs trompeurs | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- ReviewMisleadingFieldNames
- CA1504
helpviewer_keywords:
- CA1504
- ReviewMisleadingFieldNames
ms.assetid: 94136ff1-4aaf-4dc2-9170-48c171ab7499
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 651d1897b06cd7d7d214fcfbfd25a3be13f60ed7
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47588018"
---
# <a name="ca1504-review-misleading-field-names"></a>CA1504 : Vérifier les noms de champs trompeurs
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [CA1504 : vérifier les noms de champs trompeurs](https://docs.microsoft.com/visualstudio/code-quality/ca1504-review-misleading-field-names).

|||
|-|-|
|TypeName|ReviewMisleadingFieldNames|
|CheckId|CA1504|
|Category|Microsoft.Maintainability|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Le nom d’un champ d’instance commence par « s_ » ou le nom d’un `static` (`Shared` dans [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) champ commence par « m_ ».

## <a name="rule-description"></a>Description de la règle
 Les noms de champs qui commencent par « s_ » sont associés à des données statiques par de nombreux utilisateurs. De même, les noms de champs qui commencent par « m_ » sont associés à des données d’instance (membre). Pour le code plus facile à maintenir, les noms doivent suivre les conventions fréquemment utilisées.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, renommez le champ à l’aide du préfixe approprié. Vous pouvez également accorder le champ avec le suffixe actuel en ajoutant ou supprimant le `static` modificateur.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle.



