---
title: Contrôle de la couleur, du style de ligne et d'autres propriétés des formes
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 710e4a20d0b9cc60a32786836fda7716a70f86e5
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2018
---
# <a name="controlling-color-line-style-and-other-shape-properties"></a>Contrôle de la couleur, du style de ligne et d'autres propriétés des formes
Certaines propriétés de la forme tels que les couleurs peuvent être « exposés -', qui est lié à une propriété de domaine de la forme. D’autres doivent être contrôlés directement.

## <a name="exposing-a-property"></a>Exposition d’une propriété
 Certaines propriétés telles que la couleur de la forme peuvent être liées à la valeur d’une propriété de domaine.

 Dans la définition DSL, sélectionnez une forme, le connecteur ou la classe de schéma. Dans le menu contextuel, choisissez **ajouter exposées**, puis choisissez la propriété de votre choix, comme la couleur de remplissage.

 La forme a maintenant une propriété de domaine que vous pouvez définir dans le code de programme ou en tant qu’utilisateur.

## <a name="dynamically-updating-an-exposed-property"></a>Mise à jour dynamique d’une propriété exposée
 En général, vous souhaitez rendre la propriété exposée dépendante sur une autre propriété. Par exemple, vous souhaiterez peut-être une forme en rouge chaque fois qu’une propriété de domaine particulier est inférieure à zéro. Pour effectuer cette dépendance, créez un [règle](../modeling/rules-propagate-changes-within-the-model.md). Par exemple :

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