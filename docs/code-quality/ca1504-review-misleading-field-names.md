---
title: 'CA1504 : Vérifier les noms de champs trompeurs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ReviewMisleadingFieldNames
- CA1504
helpviewer_keywords:
- CA1504
- ReviewMisleadingFieldNames
ms.assetid: 94136ff1-4aaf-4dc2-9170-48c171ab7499
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 31c147c67854dd59f1fb7c9202f553edfb4a77a8
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234507"
---
# <a name="ca1504-review-misleading-field-names"></a>CA1504 : Vérifier les noms de champs trompeurs

|||
|-|-|
|TypeName|ReviewMisleadingFieldNames|
|CheckId|CA1504|
|Category|Microsoft.Maintainability|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
Le nom d’un champ d’instance commence par « s_ » ou le nom d' `static` un`Shared` champ [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)](dans) commence par « m _ ».

## <a name="rule-description"></a>Description de la règle
Les noms de champs qui commencent par « s_ » sont associés à des données statiques par de nombreux utilisateurs. De même, les noms de champs qui commencent par « m _ » sont associés à des données d’instance (membre). Pour faciliter la maintenance du code, les noms doivent respecter les conventions généralement utilisées.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
Pour corriger une violation de cette règle, renommez le champ en utilisant le préfixe approprié. Vous pouvez également faire en sorte que le champ accepte le suffixe actuel en ajoutant `static` ou en supprimant le modificateur.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
Ne supprimez aucun avertissement de cette règle.