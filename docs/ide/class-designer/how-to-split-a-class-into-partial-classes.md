---
title: Diviser une classe en classes partielles
description: Découvrez comment utiliser le mot clé Partial pour diviser la déclaration d’une classe ou d’une structure en plusieurs déclarations dans Concepteur de classes.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Class Designer, partial classes
- partial classes, Class Designer
ms.assetid: 6f6b0b30-3996-4569-9200-20482b3adf90
author: TerryGLee
ms.author: tglee
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 9a29aed406d216e2fd72d9763cd9d0522f9cdd17
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99951821"
---
# <a name="how-to-split-a-class-into-partial-classes-in-class-designer"></a>Guide pratique pour diviser une classe en classes partielles dans le Concepteur de classes

Vous pouvez utiliser le mot clé `partial` (`Partial` en Visual Basic) pour diviser la déclaration d’une classe ou d’une structure en plusieurs déclarations. Vous pouvez utiliser autant de déclarations partielles que vous le souhaitez.

Les déclarations peuvent figurer dans un ou plusieurs fichiers sources. Toutes les déclarations doivent être dans le même assembly et le même espace de noms.

Les classes partielles sont utiles dans plusieurs situations. Sur un grand projet, par exemple, le fait de séparer une classe en plusieurs fichiers permet à plusieurs programmeurs de travailler sur le projet en même temps. Quand vous utilisez du code généré par Visual Studio, vous pouvez changer la classe sans avoir à recréer le fichier source. (Des exemples de code généré par Visual Studio incluent Windows Forms et le code wrapper de service Web.) Vous pouvez ainsi créer du code qui utilise des classes générées automatiquement sans avoir à modifier le fichier créé par Visual Studio.

Il existe deux types de méthodes partielles. En C#, on parle de méthodes déclarantes et implémentantes. En Visual Basic, on parle de méthodes de déclaration et d’implémentation.

**Concepteur de classes** prend en charge les classes et les méthodes partielles. La forme de type du diagramme de classes fait référence à un emplacement de déclaration unique de la classe partielle. Si la classe partielle est définie dans plusieurs fichiers, vous pouvez spécifier l’emplacement de Déclaration **Concepteur de classes** utilisera en définissant la propriété **nouvel emplacement de membre** dans la fenêtre **Propriétés** . Autrement dit, lorsque vous double-cliquez sur une forme de classe, **Concepteur de classes** accède au fichier source qui contient la déclaration de classe identifiée par la propriété **nouvel emplacement de membre** . Lorsque vous double-cliquez sur une méthode partielle dans une forme de classe, **Concepteur de classes** accède à la déclaration de méthode partielle. En outre, dans la fenêtre **Propriétés**, la propriété **Nom de fichier** référence l’emplacement de la déclaration. Pour les classes partielles, la propriété **Nom de fichier** répertorie tous les fichiers qui contiennent du code de déclaration et d’implémentation pour cette classe. Toutefois, pour les méthodes partielles, la propriété **Nom de fichier** répertorie uniquement le fichier qui contient la déclaration de méthode partielle.

L’exemple suivant fractionne la définition de la classe `Employee` en deux déclarations, dont chacune définit une procédure différente. Les deux définitions partielles des exemples peuvent se trouver dans le même fichier source ou dans deux fichiers sources différents.

> [!NOTE]
> Visual Basic utilise des définitions de classe partielle pour séparer le code généré par Visual Studio du code créé par l’utilisateur. Le code est réparti dans des fichiers sources distincts. Par exemple, le **Concepteur Windows Form** définit des classes partielles pour des contrôles tels que `Form`. Vous ne devez pas modifier le code généré dans ces contrôles.

Pour plus d’informations sur les types partiels en Visual Basic, consultez [Partiel](/dotnet/visual-basic/language-reference/modifiers/partial).

## <a name="example"></a>Exemple

Pour diviser une définition de classe, utilisez le mot clé `partial` (`Partial` en Visual Basic), comme indiqué dans l’exemple suivant :

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

## <a name="see-also"></a>Voir aussi

- [Classes et méthodes partielles](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)
- [partial, type (référence C#)](/dotnet/csharp/language-reference/keywords/partial-type)
- [partial, méthode (Référence C#)](/dotnet/csharp/language-reference/keywords/partial-method)
- [Partial (Visual Basic)](/dotnet/visual-basic/language-reference/modifiers/partial)
