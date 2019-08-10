---
title: 'CA1901 : Les déclarations P-Invoke doivent être portables'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1901
- PInvokeDeclarationsShouldBePortable
helpviewer_keywords:
- CA1901
- PInvokeDeclarationsShouldBePortable
ms.assetid: 90361812-55ca-47f7-bce9-b8775d3b8803
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4a45b7061ae9d183ec7ee02a3b733ee9340b3689
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921304"
---
# <a name="ca1901-pinvoke-declarations-should-be-portable"></a>CA1901 : Les déclarations P/Invoke doivent être portables

|||
|-|-|
|TypeName|PInvokeDeclarationsShouldBePortable|
|CheckId|CA1901|
|Catégorie|Microsoft. Portability|
|Modification avec rupture|Avec rupture: si P/Invoke est visible à l’extérieur de l’assembly. Sans rupture: si P/Invoke n’est pas visible à l’extérieur de l’assembly.|

## <a name="cause"></a>Cause
Cette règle évalue la taille de chaque paramètre et la valeur de retour d’un P/Invoke et vérifie que leur taille, lorsqu’elle est marshalée à du code non managé sur des plateformes 32 bits et 64 bits, est correcte. La violation la plus courante de cette règle consiste à passer un entier à taille fixe où une variable dépendante de la taille du pointeur est requise pour la plateforme.

## <a name="rule-description"></a>Description de la règle
L’un des scénarios suivants ne respecte pas cette règle:

- La valeur de retour ou le paramètre est typé sous la forme d’un entier de taille fixe lorsqu’il `IntPtr`doit être typé en tant que.

- La valeur de retour ou le paramètre est tapé `IntPtr` comme un quand il doit être tapé comme un entier de taille fixe.

## <a name="how-to-fix-violations"></a>Comment corriger les violations
Vous pouvez corriger cette violation en utilisant `IntPtr` ou `UIntPtr` pour représenter des handles `Int32` au `UInt32`lieu de ou.

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

Dans cet exemple, le `nIconIndex` paramètre est déclaré `IntPtr`en tant que, qui est de 4 octets en largeur sur une plateforme 32 bits et de 8 octets en largeur sur une plateforme 64 bits. Dans la déclaration non managée qui suit, vous pouvez voir que `nIconIndex` est un entier non signé de 4 octets sur toutes les plateformes.

```csharp
HICON ExtractIcon(HINSTANCE hInst, LPCTSTR lpszExeFileName,
    UINT nIconIndex);
```

## <a name="example"></a>Exemple
Pour corriger la violation, remplacez la déclaration par ce qui suit:

```csharp
internal class NativeMethods{
    [DllImport("shell32.dll", CharSet=CharSet.Auto)]
    internal static extern IntPtr ExtractIcon(IntPtr hInst,
        string lpszExeFileName, uint nIconIndex);
}
```

## <a name="see-also"></a>Voir aussi
[Portability Warnings](../code-quality/portability-warnings.md)