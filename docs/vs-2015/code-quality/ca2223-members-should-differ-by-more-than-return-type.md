---
title: 'Ca2223 : les membres ne doivent pas différer de plus que le type de retour | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MembersShouldDifferByMoreThanReturnType
- CA2223
helpviewer_keywords:
- CA2223
- MembersShouldDifferByMoreThanReturnType
ms.assetid: eb326d9f-50d9-48cb-84be-d41c84a8fe09
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 1fab269e8f583f8b55f52eb70a5a813450f8a184
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658895"
---
# <a name="ca2223-members-should-differ-by-more-than-return-type"></a>CA2223 : Les membres ne doivent pas différer uniquement par leur type de retour
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MembersShouldDifferByMoreThanReturnType|
|CheckId|CA2223|
|Category|Microsoft. usage|
|Modification avec rupture|Rupture|

## <a name="cause"></a>Cause
 Deux membres publics ou protégés ont des signatures identiques, à l’exception du type de retour.

## <a name="rule-description"></a>Description de la règle
 Bien que le common language runtime autorise l’utilisation de types de retour pour différencier des membres autrement identiques, cette fonctionnalité n’est pas dans le Common Language Specification et n’est pas non plus une fonctionnalité courante des langages de programmation .NET. Lorsque les membres diffèrent uniquement par le type de retour, les développeurs et les outils de développement peuvent ne pas faire de distinction correcte entre eux.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Pour corriger une violation de cette règle, modifiez la conception des membres afin qu’ils soient uniques uniquement en fonction de leurs noms et types de paramètres, ou n’exposez pas les membres.

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Ne supprimez aucun avertissement de cette règle.

## <a name="example"></a>Exemple
 L’exemple suivant, en langage MSIL (Microsoft Intermediate Language), affiche un type qui viole cette règle. Notez que cette règle ne peut pas être violée C# à l’aide de ou Visual Basic .net.

```

.namespace UsageLibrary
{
  .class public auto ansi beforefieldinit ReturnTypeTest
         extends [mscorlib]System.Object
  {
    .method public hidebysig instance int32
            AMethod(int32 x) cil managed
    {
      // Code size       6 (0x6)
      .maxstack  1
      .locals init (int32 V_0)
      IL_0000:  ldc.i4.0
      IL_0001:  stloc.0
      IL_0002:  br.s       IL_0004

      IL_0004:  ldloc.0
      IL_0005:  ret
    } // end of method ReturnTypeTest::AMethod

    .method public hidebysig instance string
            AMethod(int32 x) cil managed
    {
      // Code size       10 (0xa)
      .maxstack  1
      .locals init (string V_0)
      IL_0000:  ldstr      "test"
      IL_0005:  stloc.0
      IL_0006:  br.s       IL_0008

      IL_0008:  ldloc.0
      IL_0009:  ret
    } // end of method ReturnTypeTest::AMethod

    .method public hidebysig specialname rtspecialname
            instance void  .ctor() cil managed
    {
      // Code size       7 (0x7)
      .maxstack  1
      IL_0000:  ldarg.0
      IL_0001:  call       instance void [mscorlib]System.Object::.ctor()
      IL_0006:  ret
    } // end of method ReturnTypeTest::.ctor

  } // end of class ReturnTypeTest

} // end of namespace UsageLibrary
```
