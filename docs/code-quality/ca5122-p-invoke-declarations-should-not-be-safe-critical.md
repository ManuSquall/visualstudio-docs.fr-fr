---
title: 'Déclarations de ca5122 : P-Invoke ne doivent pas être sécurisées critique | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
ms.assetid: f2581a6d-2a0e-40c1-b600-f5dc70909200
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 537c705afa002d4895cf8213acf90be485821fc9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="ca5122-pinvoke-declarations-should-not-be-safe-critical"></a>CA5122 : les déclarations P/Invoke ne doivent pas être sécurisées
|||  
|-|-|  
|TypeName|PInvokesShouldNotBeSafeCriticalFxCopRule|  
|CheckId|CA5122|  
|Category|Microsoft.Security|  
|Modification avec rupture|Rupture|  
  
## <a name="cause"></a>Cause  
 Une déclaration P/Invoke a été marquée avec <xref:System.Security.SecuritySafeCriticalAttribute>:  
  
```csharp  
[assembly: AllowPartiallyTrustedCallers]  
  
// ...  
public class C  
{  
    [SecuritySafeCritical]  
    [DllImport("kernel32.dll")]  
    public static extern bool Beep(int frequency, int duration); // CA5122 - safe critical p/invoke  
   }  
  
```  
  
 Dans cet exemple, `C.Beep(...)` a été marqué comme méthode critique sécurisée.  
  
## <a name="rule-description"></a>Description de la règle  
 Les méthodes sont marquées SecuritySafeCritical lorsqu'elles effectuent une opération relative à la sécurité, mais elle peuvent également être utilisées en toute sécurité par du code transparent. L'une des règles fondamentales de la transparence de la sécurité est que le code transparent peut ne jamais appeler directement le code natif via un P/Invoke. Par conséquent, marquer une méthode P/Invoke comme critique sécurisé ne permet pas au code transparent de l’appeler et s’avère trompeur pour l’analyse de sécurité.  
  
## <a name="how-to-fix-violations"></a>Comment corriger les violations  
 Pour rendre un P/Invoke accessible au code transparent, vous devez lui exposer une méthode de wrapper critique sécurisée :  
  
```csharp  
[assembly: AllowPartiallyTrustedCallers  
  
class C  
{  
   [SecurityCritical]  
   [DllImport("kernel32.dll", EntryPoint="Beep")]  
   private static extern bool BeepPinvoke(int frequency, int duration); // Security Critical P/Invoke  
  
   [SecuritySafeCritical]  
   public static bool Beep(int frequency, int duration)  
   {  
      return BeepPInvoke(frequency, duration);  
   }  
}  
  
```  
  
## <a name="when-to-suppress-warnings"></a>Quand supprimer les avertissements  
 Ne supprimez aucun avertissement de cette règle.