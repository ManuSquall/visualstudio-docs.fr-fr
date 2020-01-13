---
title: 'Ca1900 : les champs de type valeur doivent être portables | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1900
- ValueTypeFieldsShouldBePortable
helpviewer_keywords:
- ValueTypeFieldsShouldBePortable
- CA1900
ms.assetid: 1787d371-389f-4d39-b305-12b53bc0dfb9
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 23b5705b7ee81e56945050fe63dd2f086894bd08
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/13/2020
ms.locfileid: "75917932"
---
# <a name="ca1900-value-type-fields-should-be-portable"></a>CA1900 : Les champs de type valeur doivent être portables
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pour obtenir la documentation la plus récente sur Visual Studio, consultez [ca1900 : les champs de type valeur doivent être portables](/visualstudio/code-quality/ca1900-value-type-fields-should-be-portable).

|||
|-|-|
|TypeName|ValueTypeFieldsShouldBePortable|
|CheckId|CA1900|
|Catégorie|Microsoft. Portability|
|Modification avec rupture|Avec rupture : si le champ peut être consulté à l’extérieur de l’assembly.<br /><br /> Sans rupture : si le champ n’est pas visible à l’extérieur de l’assembly.|

## <a name="cause"></a>Cause
 Cette règle vérifie que les structures déclarées avec une disposition explicite s’aligneront correctement lorsqu’elles sont marshalées vers du code non managé sur les systèmes d’exploitation 64 bits. IA-64 n’autorise pas les accès à la mémoire non alignée et le processus se bloquera si cette violation n’est pas résolue.

## <a name="rule-description"></a>Description de la règle
 Les structures dont la disposition explicite contient des champs mal alignés provoquent des incidents sur les systèmes d’exploitation 64 bits.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Tous les champs inférieurs à 8 octets doivent avoir des décalages qui sont un multiple de leur taille, et les champs de 8 octets ou plus doivent avoir des décalages qui sont un multiple de 8. Une autre solution consiste à utiliser `LayoutKind.Sequential` au lieu de `LayoutKind.Explicit`, si raisonnable.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Cet avertissement doit être supprimé uniquement s’il se produit en cas d’erreur.
