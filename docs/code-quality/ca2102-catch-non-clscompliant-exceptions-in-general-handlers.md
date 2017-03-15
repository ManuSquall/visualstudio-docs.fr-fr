---
title: "CA2102&#160;: Interceptez les exceptions non CLSCompliant dans les gestionnaires g&#233;n&#233;raux | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2102"
  - "CatchNonClsCompliantExceptionsInGeneralHandlers"
helpviewer_keywords: 
  - "CA2102"
ms.assetid: bf2df68f-d386-4379-ad9e-930a2c2e930d
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2102&#160;: Interceptez les exceptions non CLSCompliant dans les gestionnaires g&#233;n&#233;raux
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|CatchNonClsCompliantExceptionsInGeneralHandlers|  
|CheckId|CA2102|  
|Catégorie|Microsoft.Security|  
|Modification avec rupture|Modification sans rupture|  
  
## Cause  
 Un membre dans un assembly qui n'est pas marqué avec le <xref:System.Runtime.CompilerServices.RuntimeCompatibilityAttribute> ou qui est marqué avec `RuntimeCompatibility(WrapNonExceptionThrows = false)` contient un bloc catch qui gère <xref:System.Exception?displayProperty=fullName> et ne contient pas de bloc catch général immédiatement après.  Cette règle ignore les assemblys de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)].  
  
## Description de la règle  
 Un bloc catch qui gère <xref:System.Exception> intercepte toutes les exceptions conformes CLS \(Common Language Specification\).  Toutefois, il n'intercepte pas d'exceptions non conformes CLS.  Les exceptions non conformes CLS peuvent être levées à partir du code natif ou du code managé qui était généré par l'Assembleur MSIL \(Microsoft Intermediate Language\).  Notez que les compilateurs de C\# et [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] ne permettent pas de lever des exceptions non conformes à CLS et [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] n'intercepte pas les exceptions non conformes à CLS.  Si l'intention du bloc catch est de gérer toutes les exceptions, utilisez la syntaxe de bloc catch général suivante.  
  
-   C\#: `catch {}`  
  
-   C\+\+: `catch(...) {}` ou `catch(Object^) {}`  
  
 Une exception non conforme CLS et non gérée devient un problème de sécurité lorsque les autorisations octroyées précédemment sont supprimées dans le bloc catch.  Comme les exceptions non conformes à CLS ne sont pas interceptées, une méthode malveillante qui lève une exception non conforme à CLS pourrait être exécutée avec des autorisations élevées.  
  
## Comment corriger les violations  
 Pour résoudre une violation de cette règle lorsque l'intention est d'intercepter toutes les exceptions, remplacez ou ajoutez un bloc catch général ou marquez l'assembly avec `RuntimeCompatibility(WrapNonExceptionThrows = true)`.  Si les autorisations sont supprimées du bloc catch, dupliquez les fonctionnalités dans le bloc catch général.  Si l'intention n'est pas de gérer toutes les exceptions, remplacez le bloc catch qui gère <xref:System.Exception> par les blocs catch qui gèrent des types d'exceptions spécifiques.  
  
## Quand supprimer les avertissements  
 Il est possible de supprimer sans risque un avertissement de cette règle si le bloc try ne contient pas d'instructions susceptibles de générer une exception non conforme CLS.  Dans la mesure où un code managé ou natif peut lever une exception non conforme CLS, une connaissance de tous les codes qui peuvent être exécutés dans tous les chemins d'accès de code à l'intérieur du bloc try est requise.  Notez que les exceptions non conformes CLS ne sont pas levées par le Common Language Runtime.  
  
## Exemple  
 L'exemple suivant présente une classe MSIL qui lève une exception non conforme CLS.  
  
```  
.assembly ThrowNonClsCompliantException {}  
.class public auto ansi beforefieldinit ThrowsExceptions  
{  
   .method public hidebysig static void  
         ThrowNonClsException() cil managed  
   {  
      .maxstack  1  
      IL_0000:  newobj     instance void [mscorlib]System.Object::.ctor()  
      IL_0005:  throw  
   }  
}  
```  
  
## Exemple  
 L'exemple suivant présente une méthode contenant un bloc catch général qui satisfait la règle.  
  
 [!code-cs[FxCop.Security.CatchNonClsCompliantException#1](../code-quality/codesnippet/CSharp/ca2102-catch-non-clscompliant-exceptions-in-general-handlers_1.cs)]  
  
 Compilez les exemples précédents comme suit.  
  
```  
ilasm /dll ThrowNonClsCompliantException.il  
csc /r:ThrowNonClsCompliantException.dll CatchNonClsCompliantException.cs  
```  
  
## Règles connexes  
 [CA1031 : Ne pas intercepter des types d'exception générale](../Topic/CA1031:%20Do%20not%20catch%20general%20exception%20types.md)  
  
## Voir aussi  
 [Exceptions et gestion des exceptions](/dotnet/csharp/programming-guide/exceptions/exceptions-and-exception-handling)   
 [Ilasm.exe \(IL Assembler\)](../Topic/Ilasm.exe%20\(IL%20Assembler\).md)   
 [Overriding Security Checks](http://msdn.microsoft.com/fr-fr/4acdeff5-fc05-41bf-8505-7387cdbfca28)   
 [Indépendance du langage et composants indépendants du langage](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md)