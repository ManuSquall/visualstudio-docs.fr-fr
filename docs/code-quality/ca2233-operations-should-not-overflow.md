---
title: "CA2233&#160;: Les op&#233;rations ne doivent pas d&#233;border | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "OperationsShouldNotOverflow"
  - "CA2233"
helpviewer_keywords: 
  - "CA2233"
  - "OperationsShouldNotOverflow"
ms.assetid: 3a2b06ba-6d1b-4666-9eaf-e053ef47ffaa
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 19
---
# CA2233&#160;: Les op&#233;rations ne doivent pas d&#233;border
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|OperationsShouldNotOverflow|  
|CheckId|CA2233|  
|Catégorie|Microsoft.Usage|  
|Modification avec rupture|Modification sans rupture|  
  
## Cause  
 Une méthode exécute une opération arithmétique et ne valide pas à l'avance les opérandes pour empêcher le dépassement de capacité.  
  
## Description de la règle  
 Les opérations arithmétiques ne doivent pas être exécutées sans valider au préalable les opérandes afin de s'assurer que le résultat de l'opération ne se trouve pas hors de la plage des valeurs possibles pour les types de données impliqués.  Selon le contexte d'exécution et les types de données impliqués, le dépassement de capacité arithmétique peut engendrer un <xref:System.OverflowException?displayProperty=fullName> ou la suppression des bits de poids fort du résultat.  
  
## Comment corriger les violations  
 Pour corriger une violation de cette règle, validez les opérandes avant d'exécuter l'opération.  
  
## Quand supprimer les avertissements  
 Il est possible de supprimer sans risque un avertissement de cette règle si les valeurs possibles des opérandes sont dans l'incapacité systématique de provoquer le dépassement de capacité de l'opération arithmétique.  
  
## Exemple de violation  
  
### Description  
 Une méthode dans l'exemple suivant manipule un entier qui viole cette règle.  [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] requiert la désactivation de l'option de dépassement **Supprimer** pour son déclenchement.  
  
### Code  
 [!code-vb[FxCop.Usage.OperationOverflow#1](../code-quality/codesnippet/VisualBasic/ca2233-operations-should-not-overflow_1.vb)]
 [!code-cs[FxCop.Usage.OperationOverflow#1](../code-quality/codesnippet/CSharp/ca2233-operations-should-not-overflow_1.cs)]  
  
### Commentaires  
 Si, dans cet exemple, la méthode est passée <xref:System.Int32.MinValue?displayProperty=fullName>, l'opération va faire l'objet d'un dépassement de capacité négatif.  Le bit le plus significatif du résultat est alors ignoré.  Le code suivant montre comment cela se produit.  
  
 \[C\#\]  
  
```  
public static void Main()  
{  
    int value = int.MinValue;    // int.MinValue is -2147483648   
    value = Calculator.Decrement(value);   
    Console.WriteLine(value);  
}  
```  
  
 \[VB\]  
  
```  
Public Shared Sub Main()       
    Dim value = Integer.MinValue    ' Integer.MinValue is -2147483648   
    value = Calculator.Decrement(value)   
    Console.WriteLine(value)   
End Sub  
```  
  
### Sortie  
  
```  
2147483647  
```  
  
## Résoudre avec validation du paramètre d'entrée  
  
### Description  
 L'exemple suivant résout la violation précédente en validant la valeur d'entrée.  
  
### Code  
 [!CODE [FxCop.Usage.OperationOverflowFixed#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflowFixed#1)]  
  
## Résoudre avec un bloc checked  
  
### Description  
 L'exemple suivant résout la violation précédente en encapsulant l'opération dans un bloc checked.  Si l'opération provoque un dépassement de capacité, une <xref:System.OverflowException?displayProperty=fullName> sera levée.  
  
 Notez que les blocs checked ne sont pas pris en charge dans [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)].  
  
### Code  
 [!CODE [FxCop.Usage.OperationOverflowChecked#1](../CodeSnippet/VS_Snippets_CodeAnalysis/FxCop.Usage.OperationOverflowChecked#1)]  
  
## Activer la vérification des dépassements de capacité arithmétiques positifs et négatifs  
 Si vous activez la vérification des dépassements de capacité arithmétiques positifs et négatifs en C\#, cela équivaut à encapsuler chaque opération sur des entiers dans un bloc checked.  
  
 **Pour activer la vérification des dépassements de capacité arithmétiques positifs et négatifs en C\#**  
  
1.  Dans l' **Explorateur de solutions**, cliquez avec le bouton droit sur votre projet, puis sélectionnez **Propriétés**.  
  
2.  Sélectionnez l'onglet **Build**, puis cliquez sur **Avancé**.  
  
3.  Sélectionnez **Vérifier les dépassements de capacité arithmétiques positifs et négatifs** et cliquez sur **OK**.  
  
## Voir aussi  
 <xref:System.OverflowException?displayProperty=fullName>   
 [Opérateurs C\#](/dotnet/csharp/language-reference/operators/index)   
 [Checked et unchecked](/dotnet/csharp/language-reference/keywords/checked-and-unchecked)