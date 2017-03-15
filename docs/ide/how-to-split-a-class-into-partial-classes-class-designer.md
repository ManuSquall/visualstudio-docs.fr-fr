---
title: "How to: Split a Class into Partial Classes (Class Designer) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Class Designer, partial classes"
  - "partial classes, Class Designer"
ms.assetid: 6f6b0b30-3996-4569-9200-20482b3adf90
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 10
---
# How to: Split a Class into Partial Classes (Class Designer)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vous pouvez diviser la déclaration d'une classe ou structure entre plusieurs déclarations à l'aide du mot clé `Partial` dans Visual Basic ou du mot clé `partial` dans Visual C\#.  Vous pouvez utiliser autant de déclarations partielles que vous le souhaitez, dans autant de fichiers sources différents que vous désirez ou dans un seul fichier source.  Toutefois, toutes les déclarations doivent se trouver dans le même assembly et même espace de noms.  
  
 Les classes partielles sont utiles dans plusieurs situations.  Par exemple, lorsque vous travaillez sur de grands projets, séparer une classe en plusieurs fichiers permet à plusieurs programmeurs de travailler en même temps.  Lorsque vous travaillez avec le code que Visual Studio génère, vous pouvez modifier la classe sans devoir recréer le fichier source.  \(Les exemples de code que Visual Studio génère incluent des Windows Forms et des code wrapper de Service Web.\) Vous pouvez donc créer un code qui utilise des classes générées automatiquement sans devoir modifier le fichier créé par Visual Studio.  
  
 Il existe deux types de méthodes partielles.  Dans Visual C\#, ils sont appelés déclarer et implémenter ; dans Visual Basic, ils sont appelés déclaration et implémentation.  
  
 Le Concepteur de classes prend en charge des classes et des méthodes partielles.  La forme de type dans le diagramme de classes fait référence à l'emplacement de la déclaration.  Si la classe partielle est définie dans plusieurs fichiers, vous pouvez spécifier l'emplacement de la déclaration que le Concepteur de classes utilisera en définissant la propriété **Nouvel emplacement de membre** dans la fenêtre **Propriétés**.  Autrement dit, lorsque vous double\-cliquez sur une forme de classe, le Concepteur de classes accède au fichier source qui contient la déclaration de classe identifiée par la propriété **Nouvel emplacement de membre**.  Lorsque vous double\-cliquez sur une méthode partielle dans une forme de classe, le Concepteur de classes accède à la déclaration de la classe partielle.  Également, dans la fenêtre **Propriétés**, la propriété **Nom de fichier** fait référence à l'emplacement de la déclaration.  Pour une classe partielle, la liste **Nom de fichier** répertorie tous les fichiers qui contiennent la déclaration et le code d'implémentation de la classe.  Toutefois, pour les méthodes partielles, **Nom de fichier** répertorie uniquement le fichier qui contient la déclaration de méthode partielle.  
  
 L'exemple suivant fractionne la définition de `Employee` de classe en deux déclarations, chacune d'elles définissant une procédure différente.  Les deux définitions partielles dans les exemples pourraient être dans un fichier source ou dans deux fichiers sources différents.  
  
> [!NOTE]
>  Visual Basic utilise des définitions de classe partielle pour séparer le code généré par Visual Studio du code généré par l'utilisateur.  Le code est séparé dans des fichiers sources discrets.  Par exemple, le **Concepteur Windows Form** définit des classes partielles pour les contrôles, tels que `Form`.  Vous ne devez pas modifier le code généré dans ces contrôles.  
  
 Pour plus d'informations sur les types partiels dans Visual Basic, consultez [Partial](/dotnet/visual-basic/language-reference/modifiers/partial).  
  
## Exemple  
 Pour fractionner une définition de classe dans Visual Basic, utilisez le mot clé `Partial`, comme illustré dans l'exemple suivant.  
  
```vb#  
' First part of class definition.  
Partial Public Class Employee  
    Public Sub CalculateWorkHours()  
    End Sub  
End Class  
  
' Second part of class definition.  
Partial Public Class Employee  
    Public Sub CalculateTaxes()  
    End Sub  
End Class  
```  
  
## Exemple  
 Pour fractionner une définition de classe dans Visual C\#, utilisez le mot clé `partial`, comme illustré dans l'exemple suivant.  
  
```c#  
// First part of class definition.  
public partial class Employee  
{  
    public void CalculateWorkHours()  
    {  
    }  
}  
  
// Second part of class definition.  
public partial class Employee  
{  
    public void CalculateTaxes()  
    {  
    }  
}  
```  
  
## Voir aussi  
 [Classes et méthodes partielles](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)   
 [partiel, Type](/dotnet/csharp/language-reference/keywords/partial-type)   
 [partielle, méthode \(Référence C\#\)](/dotnet/csharp/language-reference/keywords/partial-method)   
 [Partial](/dotnet/visual-basic/language-reference/modifiers/partial)