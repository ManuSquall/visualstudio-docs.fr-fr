---
title: "CA5122 : les d&#233;clarations P/Invoke ne doivent pas &#234;tre s&#233;curis&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f2581a6d-2a0e-40c1-b600-f5dc70909200
caps.latest.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 4
---
# CA5122 : les d&#233;clarations P/Invoke ne doivent pas &#234;tre s&#233;curis&#233;es
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|PInvokesShouldNotBeSafeCriticalFxCopRule|  
|CheckId|CA5122|  
|Catégorie|Microsoft.Security|  
|Modification avec rupture|Rupture|  
  
## Cause  
 Une déclaration P\/Invoke a été marquée avec <xref:System.Security.SecuritySafeCriticalAttribute>:  
  
```c#  
[assembly: AllowPartiallyTrustedCallers]  
  
// ...  
public class C  
{  
    [SecuritySafeCritical]  
    [DllImport("kernel32.dll")]  
    public static extern bool Beep(int frequency, int duration); // CA5122 – safe critical p/invoke  
   }  
  
```  
  
 Dans cet exemple, `C.Beep(...)` a été marqué comme méthode critique sécurisée.  
  
## Description de la règle  
 Les méthodes sont marquées SecuritySafeCritical lorsqu'elles effectuent une opération relative à la sécurité, mais elle peuvent également être utilisées en toute sécurité par du code transparent.  L'une des règles fondamentales de la transparence de la sécurité est que le code transparent peut ne jamais appeler directement le code natif via un P\/Invoke.  Par conséquent, marquer une méthode P\/Invoke comme critique sécurisé ne permet pas au code transparent de l'appeler et s'avère trompeur pour l'analyse de sécurité.  
  
## Comment corriger les violations  
 Pour rendre un P\/Invoke accessible au code transparent, vous devez lui exposer une méthode de wrapper critique sécurisée :  
  
```c#  
[assembly: AllowPartiallyTrustedCallers  
  
class C  
{  
   [SecurityCritical]  
   [DllImport(“kernel32.dll”, EntryPoint=”Beep”)]  
   private static extern bool BeepPinvoke(int frequency, int duration); // Security Critical P/Invoke  
  
   [SecuritySafeCritical]  
   public static bool Beep(int frequency, int duration)  
   {  
      return BeepPInvoke(frequency, duration);  
   }  
}  
  
```  
  
## Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.