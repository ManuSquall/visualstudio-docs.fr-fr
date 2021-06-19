---
title: Contrôler la couleur, le style de trait et d’autres propriétés des formes
description: Fournit des informations sur le contrôle des propriétés de forme, telles que la couleur et le style de ligne.
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.custom: SEO-VS-2020
ms.workload:
- multiple
ms.openlocfilehash: 836c77f3651b7686e9366fe75ea7922a248fd28f
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389629"
---
# <a name="controlling-color-line-style-and-other-shape-properties"></a>Contrôle de la couleur, du style de ligne et d'autres propriétés des formes

Certaines propriétés de forme telles que Color peuvent être « exposées ». Autrement dit, les propriétés peuvent être liées à une propriété de domaine de la forme. D’autres doivent être contrôlés directement.

## <a name="exposing-a-property"></a>Exposer une propriété
 Certaines propriétés de forme telles que la couleur peuvent être liées à la valeur d’une propriété de domaine.

 Dans la définition DSL, sélectionnez une classe de forme, de connecteur ou de diagramme. Dans le menu contextuel, choisissez **Ajouter exposé**, puis choisissez la propriété de votre choix, par exemple couleur de remplissage.

 La forme a maintenant une propriété de domaine que vous pouvez définir dans le code de programme ou en tant qu’utilisateur.

## <a name="dynamically-updating-an-exposed-property"></a>Mise à jour dynamique d’une propriété exposée
 En général, vous souhaitez rendre la propriété exposée dépendante d’une autre propriété. Par exemple, vous souhaiterez peut-être qu’une forme s’active en rouge chaque fois qu’une propriété de domaine particulière est inférieure à zéro. Pour créer cette dépendance, créez une [règle](../modeling/rules-propagate-changes-within-the-model.md). Par exemple :

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