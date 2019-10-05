---
title: 'CA2149 : Les méthodes transparentes ne doivent pas appeler du code natif'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2149
ms.assetid: 28951bd7-f3db-4871-99aa-bad68d1ead80
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 8e75b12b820b3ff3ac5a26f83148a49ca87c12ad
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231953"
---
# <a name="ca2149-transparent-methods-must-not-call-into-native-code"></a>CA2149 : Les méthodes transparentes ne doivent pas appeler du code natif

|||
|-|-|
|TypeName|TransparentMethodsMustNotCallNativeCode|
|CheckId|CA2149|
|Category|Microsoft.Security|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
Une méthode appelle une fonction native par le biais d’un stub de méthode tel que P/Invoke.

## <a name="rule-description"></a>Description de la règle
Cette règle se déclenche sur toute méthode transparente qui appelle directement en code natif, par exemple, via un appel P/Invoke. Les violations de cette règle entraînent <xref:System.MethodAccessException> une dans le modèle de transparence de niveau 2 et une demande <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A> complète pour dans le modèle de transparence de niveau 1.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
Pour corriger une violation de cette règle, marquez la méthode qui appelle le code natif avec <xref:System.Security.SecurityCriticalAttribute> l' <xref:System.Security.SecuritySafeCriticalAttribute> attribut ou.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemple
[!code-csharp[FxCop.Security.CA2149.TransparentMethodsMustNotCallNativeCode#1](../code-quality/codesnippet/CSharp/ca2149-transparent-methods-must-not-call-into-native-code_1.cs)]