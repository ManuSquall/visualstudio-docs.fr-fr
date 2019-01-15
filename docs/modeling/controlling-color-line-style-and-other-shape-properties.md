---
title: Contrôle de la couleur, du style de ligne et d'autres propriétés des formes
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: ea0b73470bc9f3bed76328c55d823cef3c5b8e9e
ms.sourcegitcommit: 38db86369af19e174b0aba59ba1918a5c4fe4a61
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2019
ms.locfileid: "54269317"
---
# <a name="controlling-color-line-style-and-other-shape-properties"></a>Contrôle de la couleur, du style de ligne et d'autres propriétés des formes

Certaines propriétés telles que la couleur de la forme « exploitable ». Autrement dit, les propriétés peuvent être liées à une propriété de domaine de la forme. Les autres ont à être directement contrôlée.

## <a name="exposing-a-property"></a>Exposer une propriété
 Certaines propriétés telles que la couleur de la forme peuvent être liées à la valeur d’une propriété de domaine.

 Dans la définition DSL, sélectionnez une forme, connecteur ou une classe de diagramme. Dans le menu contextuel, choisissez **ajouter les objets exposés**, puis choisissez la propriété souhaitées, par exemple, la couleur de remplissage.

 La forme a maintenant une propriété de domaine que vous pouvez définir dans le code de programme ou en tant qu’utilisateur.

## <a name="dynamically-updating-an-exposed-property"></a>Mise à jour dynamique d’une propriété exposée
 En règle générale, vous souhaitez rendre la propriété exposée dépendantes d’une autre propriété. Par exemple, vous souhaiterez peut-être une forme en rouge chaque fois qu’une propriété de domaine particulière est inférieure à zéro. Pour rendre cette dépendance, vous devez créer un [règle](../modeling/rules-propagate-changes-within-the-model.md). Exemple :

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
namespace ExampleNamespace
{
 // Attribute associates the rule with class:
 [RuleOn(typeof(CarShape), FireTime = TimeToFire.TopLevelCommit)]
 // The rule is a class derived from one of the abstract rules:
 class CarShapeAddRule : AddRule
 {
 // Override the abstract method:
 public override void ElementAdded(ElementAddedEventArgs e)
 {
 base.ElementAdded(e);
 CarShape shape = e.ModelElement as CarShape;
 Store store = shape.Store;
 // Ignore this call if we're currently loading a model:
 if (store.TransactionManager.CurrentTransaction.IsSerializing)
  return;
 Car car = shape.ModelElement as Car;
 // Code here propagates change as required - for example:
 shape.FillColor = car.Somebool ? System.Drawing.Color.Red : System.Drawing.Color.Green;
 }
}
 // The rule must be registered:
 public partial class ExampleDomainModel
 {
 protected override Type[] GetCustomDomainModelTypes()
 {
  List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());
  types.Add(typeof(CarShapeAddRule));
  // If you add more rules, list them here.
  return types.ToArray();
 }
 }
}
```