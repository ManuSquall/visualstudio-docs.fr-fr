---
title: 'CA2149 : Les méthodes transparentes ne doivent pas appeler du code natif | Microsoft Docs'
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
- CA2149
ms.assetid: 28951bd7-f3db-4871-99aa-bad68d1ead80
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 887252eca86205858b168c7f5a4a6c33cb0cc67d
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2018
ms.locfileid: "47588022"
---
# <a name="ca2149-transparent-methods-must-not-call-into-native-code"></a>CA2149 : Les méthodes transparentes ne doivent pas appeler du code natif
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous trouverez la dernière version de cette rubrique dans [CA2149 : méthodes transparentes ne doivent pas appeler du code natif](https://docs.microsoft.com/visualstudio/code-quality/ca2149-transparent-methods-must-not-call-into-native-code).

|||
|-|-|
|TypeName|TransparentMethodsMustNotCallNativeCode|
|CheckId|CA2149|
|Category|Microsoft.Security|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Une méthode appelle une fonction native via un stub de méthode tel que P/Invoke.

## <a name="rule-description"></a>Description de la règle
 Cette règle se déclenche sur toute méthode transparente qui appelle directement en code natif (par exemple, via un appel P/Invoke). Les violations de cette règle provoquent une <xref:System.MethodAccessException> dans le modèle de transparence de niveau 2 et une demande complète pour <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A> dans le modèle de transparence de niveau 1.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, marquez la méthode qui appelle le code natif avec le <xref:System.Security.SecurityCriticalAttribute> ou <xref:System.Security.SecuritySafeCriticalAttribute> attribut.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemple
 [!code-csharp[FxCop.Security.CA2149.TransparentMethodsMustNotCallNativeCode#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2149.transparentmethodsmustnotcallnativecode/cs/ca2149 - transparentmethodsmustnotcallnativecode.cs#1)]



