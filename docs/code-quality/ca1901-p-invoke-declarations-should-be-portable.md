---
title: "CA1901&#160;: Les d&#233;clarations P/Invoke doivent &#234;tre portables | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1901"
  - "PInvokeDeclarationsShouldBePortable"
helpviewer_keywords: 
  - "CA1901"
  - "PInvokeDeclarationsShouldBePortable"
ms.assetid: 90361812-55ca-47f7-bce9-b8775d3b8803
caps.latest.revision: 23
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 23
---
# CA1901&#160;: Les d&#233;clarations P/Invoke doivent &#234;tre portables
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|PInvokeDeclarationsShouldBePortable|  
|CheckId|CA1901|  
|Catégorie|Microsoft.Portability|  
|Modification avec rupture|Avec rupture \- Si P\/Invoke est visible à l'extérieur de l'assembly.  Sans rupture \- Si P\/Invoke n'est pas visible à l'extérieur de l'assembly.|  
  
## Cause  
 Cette règle évalue la taille de chaque paramètre et la valeur de retour d'un P\/Invoke, et vérifie que leur taille est correcte lorsqu'elle est marshalée au code non managé sur les plateformes 32 bits et 64 bits.  La violation la plus courante de cette règle consiste à passer un entier de taille fixe lorsqu'une variable de la taille d'un pointeur dépendant de la plateforme est requise.  
  
## Description de la règle  
 L'un des scénarios suivants viole cette règle :  
  
-   La valeur ou le paramètre renvoyé est saisi comme un entier de taille fixe lorsqu'il doit être tapé comme un `IntPtr`.  
  
-   La valeur ou le paramètre renvoyé est saisi comme un `IntPtr` lorsqu'il doit être tapé comme un entier de taille fixe.  
  
## Comment corriger les violations  
 Vous pouvez corriger cette violation en utilisant `IntPtr` ou `UIntPtr` pour représenter des handles au lieu de `Int32` ou `UInt32`.  
  
## Quand supprimer les avertissements  
 Vous ne devez pas supprimer cet avertissement.  
  
## Exemple  
 L'exemple suivant indique une violation de cette règle.  
  
```c#  
internal class NativeMethods  
{  
    [DllImport("shell32.dll", CharSet=CharSet.Auto)]  
    internal static extern IntPtr ExtractIcon(IntPtr hInst,   
        string lpszExeFileName, IntPtr nIconIndex);  
}  
```  
  
 Dans cet exemple, le paramètre d' `nIconIndex` est déclaré comme `IntPtr`, qui est de longueur 4 octets sur une plateforme 32 bits et 8 octets sur une plateforme 64 bits.  Dans la déclaration non managée qui suit, vous pouvez voir qu' `nIconIndex` est un entier non signé de 4 octets sur toutes les plateformes.  
  
```c#  
HICON ExtractIcon(HINSTANCE hInst, LPCTSTR lpszExeFileName,   
    UINT nIconIndex);  
```  
  
## Exemple  
 Pour résoudre la violation, modifiez la déclaration comme suit :  
  
```c#  
internal class NativeMethods{  
    [DllImport("shell32.dll", CharSet=CharSet.Auto)]   
    internal static extern IntPtr ExtractIcon(IntPtr hInst,   
        string lpszExeFileName, uint nIconIndex);  
}  
```  
  
## Voir aussi  
 [Avertissements liés à la portabilité](../code-quality/portability-warnings.md)