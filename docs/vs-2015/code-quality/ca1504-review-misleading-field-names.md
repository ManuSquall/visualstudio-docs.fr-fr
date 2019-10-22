---
title: 'Ca1504 : passez en revue les noms de champs trompeurs | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ReviewMisleadingFieldNames
- CA1504
helpviewer_keywords:
- CA1504
- ReviewMisleadingFieldNames
ms.assetid: 94136ff1-4aaf-4dc2-9170-48c171ab7499
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: c3f1cca5dd33047a4d19c78013dd535e0e9dd6f2
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72607754"
---
# <a name="ca1504-review-misleading-field-names"></a>CA1504 : Vérifier les noms de champs trompeurs
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ReviewMisleadingFieldNames|
|CheckId|CA1504|
|Category|Microsoft. maintenabilité|
|Modification avec rupture|Sans rupture|

## <a name="cause"></a>Cause
 Le nom d’un champ d’instance commence par « s_ » ou le nom d’un `static` (`Shared` dans [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) le champ commence par « m _ ».

## <a name="rule-description"></a>Description de la règle
 Les noms de champs qui commencent par « s_ » sont associés à des données statiques par de nombreux utilisateurs. De même, les noms de champs qui commencent par « m _ » sont associés à des données d’instance (membre). Pour faciliter la maintenance du code, les noms doivent respecter les conventions généralement utilisées.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, renommez le champ en utilisant le préfixe approprié. Vous pouvez également faire en sorte que le champ accepte le suffixe actuel en ajoutant ou en supprimant le modificateur `static`.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle.
