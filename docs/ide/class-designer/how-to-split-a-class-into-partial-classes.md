---
title: Guide pratique pour fractionner une classe en classes partielles (Concepteur de classes)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Class Designer, partial classes
- partial classes, Class Designer
ms.assetid: 6f6b0b30-3996-4569-9200-20482b3adf90
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3d0aa5b844b3743ab80c11971caa26340effe671
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-split-a-class-into-partial-classes-class-designer"></a>Guide pratique pour fractionner une classe en classes partielles (Concepteur de classes)

Vous pouvez utiliser le mot clé `partial` (`Partial` en Visual Basic) pour diviser la déclaration d’une classe ou d’une structure en plusieurs déclarations. Vous pouvez utiliser autant de déclarations partielles que vous le souhaitez.

Les déclarations peuvent figurer dans un ou plusieurs fichiers sources. Toutes les déclarations doivent être dans le même assembly et le même espace de noms.

Les classes partielles sont utiles dans plusieurs situations. Sur un grand projet, par exemple, le fait de séparer une classe en plusieurs fichiers permet à plusieurs programmeurs de travailler sur le projet en même temps. Quand vous utilisez du code généré par Visual Studio, vous pouvez changer la classe sans avoir à recréer le fichier source. Le code Windows Forms et le code wrapper de service web sont des exemples de code généré par Visual Studio. Vous pouvez donc écrire du code qui utilise des classes autogénérées sans avoir à modifier le fichier créé par Visual Studio.

Il existe deux types de méthodes partielles. En C#, on parle de méthodes déclarantes et implémentantes. En Visual Basic, on parle de méthodes de déclaration et d’implémentation.

Le **Concepteur de classes** prend en charge les classes et les méthodes partielles. La forme de type du diagramme de classes fait référence à un emplacement de déclaration unique de la classe partielle. Si la classe partielle est définie dans plusieurs fichiers, vous pouvez spécifier l’emplacement de déclaration utilisé par le **Concepteur de classes** en définissant la propriété **Nouvel emplacement de membre** dans la fenêtre **Propriétés**. Autrement dit, quand vous double-cliquez sur une forme de classe, le **Concepteur de classes** accède au fichier source qui contient la déclaration de classe identifiée par la propriété **Nouvel emplacement de membre**. Quand vous double-cliquez sur une méthode partielle dans une forme de classe, le **Concepteur de classes** accède à la déclaration de méthode partielle. En outre, dans la fenêtre **Propriétés**, la propriété **Nom de fichier** référence l’emplacement de la déclaration. Pour les classes partielles, la propriété **Nom de fichier** répertorie tous les fichiers qui contiennent du code de déclaration et d’implémentation pour cette classe. Toutefois, pour les méthodes partielles, la propriété **Nom de fichier** répertorie uniquement le fichier qui contient la déclaration de méthode partielle.

L’exemple suivant fractionne la définition de la classe `Employee` en deux déclarations, dont chacune définit une procédure différente. Les deux définitions partielles des exemples peuvent se trouver dans le même fichier source ou dans deux fichiers sources différents.

> [!NOTE]
> Visual Basic utilise des définitions de classe partielle pour séparer le code généré par Visual Studio du code créé par l’utilisateur. Le code est réparti dans des fichiers sources distincts. Par exemple, le **Concepteur Windows Form** définit des classes partielles pour des contrôles tels que `Form`. Vous ne devez pas modifier le code généré dans ces contrôles.


Pour plus d’informations sur les types partiels en Visual Basic, consultez [Partiel](/dotnet/visual-basic/language-reference/modifiers/partial).

## <a name="visual-basic-example"></a>Exemple Visual Basic

Pour fractionner une définition de classe en Visual Basic, utilisez le mot clé `Partial`, comme indiqué dans l’exemple suivant.

```vb
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

## <a name="c-example"></a>Exemple C#

Pour fractionner une définition de classe en C#, utilisez le mot clé `partial`, comme indiqué dans l’exemple suivant.

```csharp
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

## <a name="see-also"></a>Voir aussi

- [Classes et méthodes partielles](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)
- [partial (type)](/dotnet/csharp/language-reference/keywords/partial-type)
- [partial, méthode (Référence C#)](/dotnet/csharp/language-reference/keywords/partial-method)
- [Partial](/dotnet/visual-basic/language-reference/modifiers/partial)