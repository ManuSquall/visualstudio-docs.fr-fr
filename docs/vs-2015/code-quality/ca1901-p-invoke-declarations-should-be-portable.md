---
title: 'CA1901 : les déclarations P-Invoke doivent être portables | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1901
- PInvokeDeclarationsShouldBePortable
helpviewer_keywords:
- CA1901
- PInvokeDeclarationsShouldBePortable
ms.assetid: 90361812-55ca-47f7-bce9-b8775d3b8803
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: e669d87ad5ecc53c1523db16ab77578c6a703a33
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545260"
---
# <a name="ca1901-pinvoke-declarations-should-be-portable"></a>CA1901 : Les déclarations P/Invoke doivent être portables
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Élément|Valeur|
|-|-|
|TypeName|PInvokeDeclarationsShouldBePortable|
|CheckId|CA1901|
|Category|Microsoft. Portability|
|Modification avec rupture|Avec rupture : si P/Invoke est visible à l’extérieur de l’assembly. Sans rupture : si P/Invoke n’est pas visible à l’extérieur de l’assembly.|

## <a name="cause"></a>Cause :
 Cette règle évalue la taille de chaque paramètre et la valeur de retour d’un P/Invoke et vérifie que leur taille, lorsqu’elle est marshalée à du code non managé sur des plateformes 32 bits et 64 bits, est correcte. La violation la plus courante de cette règle consiste à passer un entier à taille fixe où une variable dépendante de la taille du pointeur est requise pour la plateforme.

## <a name="rule-description"></a>Description de la règle
 L’un des scénarios suivants ne respecte pas cette règle :

- La valeur de retour ou le paramètre est typé sous la forme d’un entier de taille fixe lorsqu’il doit être typé en tant que `IntPtr` .

- La valeur de retour ou le paramètre est tapé comme un `IntPtr` quand il doit être tapé comme un entier de taille fixe.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
 Vous pouvez corriger cette violation en utilisant `IntPtr` ou `UIntPtr` pour représenter des handles au lieu de `Int32` ou `UInt32` .

## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements
 Vous ne devez pas supprimer cet avertissement.

## <a name="example"></a>Exemple
 L’exemple suivant illustre une violation de cette règle.

```csharp
internal class NativeMethods
{
    [DllImport("shell32.dll", CharSet=CharSet.Auto)]
    internal static extern IntPtr ExtractIcon(IntPtr hInst,
        string lpszExeFileName, IntPtr nIconIndex);
}
```

 Dans cet exemple, le `nIconIndex` paramètre est déclaré en tant que `IntPtr` , qui est de 4 octets en largeur sur une plateforme 32 bits et de 8 octets en largeur sur une plateforme 64 bits. Dans la déclaration non managée qui suit, vous pouvez voir que `nIconIndex` est un entier non signé de 4 octets sur toutes les plateformes.

```csharp
HICON ExtractIcon(HINSTANCE hInst, LPCTSTR lpszExeFileName,
    UINT nIconIndex);
```

## <a name="example"></a>Exemple
 Pour corriger la violation, remplacez la déclaration par ce qui suit :

```csharp
internal class NativeMethods{
    [DllImport("shell32.dll", CharSet=CharSet.Auto)]
    internal static extern IntPtr ExtractIcon(IntPtr hInst,
        string lpszExeFileName, uint nIconIndex);
}
```

## <a name="see-also"></a>Voir aussi
 [Avertissements de portabilité](../code-quality/portability-warnings.md)
