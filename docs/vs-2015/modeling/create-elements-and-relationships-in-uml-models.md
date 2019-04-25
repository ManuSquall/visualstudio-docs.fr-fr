---
title: Créer des éléments et des relations dans les modèles UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML API
ms.assetid: cae81d32-8cc7-4f7c-9f00-20119952bc51
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: ce1f236347ad811f1c5d115f30907b7e3356e3af
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "60099271"
---
# <a name="create-elements-and-relationships-in-uml-models"></a>Créer des éléments et des relations dans des modèles UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dans le code de programme d'une extension de Visual Studio, vous pouvez créer et supprimer des éléments et des relations.  
  
## <a name="create-a-model-element"></a>Créer un élément de modèle  
  
### <a name="namespace-imports"></a>Importations d'espaces de noms  
 Vous devez inclure les instructions `using` suivantes.  
  
 Les méthodes de création sont définies en tant que méthodes d'extension dans cet espace de noms :  
  
 `using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;`  
  
### <a name="obtain-the-owner-of-the-element-you-want-to-create"></a>Obtenir le propriétaire de l'élément à créer  
 Un modèle forme une arborescence unique, de sorte que chaque élément possède un propriétaire, à l'exception de la racine du modèle. La racine du modèle est de type `IModel`, ce qui est un type de `IPackage`.  
  
 Si vous créez un élément qui sera affiché dans un diagramme particulier, par exemple, le diagramme actuel de l'utilisateur, vous devez généralement le créer dans le package lié à ce diagramme. Exemple :  
  
```  
IPackage linkedPackage = Context.CurrentDiagram.Element as IPackage;  
```  
  
 Ce tableau récapitule la propriété des éléments de modèle communs :  
  
|Élément à créer|Propriétaire|  
|---------------------------|-----------|  
|`IActor, IUseCase, IComponent, IClass, IInterface, IEnumeration`<br /><br /> `IActivity, IInteraction`|`IPackage, IModel`|  
|`IAttribute, IOperation`|`IClass, IInterface`|  
|`IPart, IPort`|`IComponent`|  
|`IAction, IObjectNode`|`IActivity`|  
|`ILifeline, IMessage, ICombinedFragment`|`IInteraction`|  
  
### <a name="invoke-the-create-method-on-the-owner"></a>Appeler la méthode de création sur le propriétaire  
 Le nom de la méthode est au format : `Create`*OwnedType*`()`. Exemple :  
  
```  
IUseCase usecase1 = linkedPackage.CreateUseCase();  
```  
  
 Certains types ont des méthodes de création plus complexes, en particulier dans les diagrammes de séquence. Consultez [des diagrammes de séquence UML modifier à l’aide de l’API UML](../modeling/edit-uml-sequence-diagrams-by-using-the-uml-api.md).  
  
 Pour certains types d'éléments, vous pouvez modifier le propriétaire d'un élément pendant sa durée de vie, à l'aide de `SetOwner(newOwner)`.  
  
### <a name="set-the-name-and-other-properties"></a>Définir le nom et d'autres propriétés  
  
```  
usecase1.Name = "user logs in";  
```  
  
### <a name="example"></a>Exemple  
  
```  
using Microsoft.VisualStudio.Uml.Classes;  
using Microsoft.VisualStudio.Uml.Extensions;  
...  
 void InstantiateObserverPattern (IPackage package, string namePrefix)  
 {    IInterface observer = package.CreateInterface();  
      observer.Name = namePrefix + "Observer";  
      IOperation operation = observer.CreateOperation();  
      operation.Name = "Update";  
      IClass subject = package.CreateClass();  
      subject.Name = namePrefix + "Subject"; ...  
```  
  
## <a name="create-an-association"></a>Créer une association  
  
#### <a name="to-create-an-association"></a>Pour créer une association  
  
1. Obtenez le propriétaire de l'association, lequel correspond généralement au package ou modèle contenant l'extrémité source de la relation.  
  
2. Appelez la méthode de création requise sur le propriétaire.  
  
3. Définissez les propriétés de la relation, notamment son nom.  
  
     Exemple :  
  
    ```  
    IAssociation association = subject.Package.CreateAssociation(subject, observer);  
    association .Name = "Observes";  
    ```  
  
4. Définissez les propriétés de chaque extrémité de la relation. Il existe toujours deux `MemberEnds`. Exemple :  
  
    ```  
    association .MemberEnds[0].Name = "subject";   // role name  
    association .MemberEnds[1].Name = "observers"; // role name  
    association .MemberEnds[1].SetBounds("0..*");           
                // multiplicity defaults to "1"  
    association.MemberEnds[0].Aggregation = AggregationKind.Composite;  
    ```  
  
## <a name="create-a-generalization"></a>Créer une généralisation  
  
```  
IGeneralization generalization =   
  subclass.CreateGeneralization(superClass);  
```  
  
## <a name="delete-an-element-relationship-or-generalization-from-the-model"></a>Supprimer un élément, une relation ou une généralisation du modèle  
  
```  
anElement.Delete();  
```  
  
 Quand vous supprimez un élément d'un modèle :  
  
- Chaque relation qui établit un lien vers lui est également supprimée.  
  
- Chaque forme qui le représentait dans un diagramme est également supprimée.  
  
## <a name="see-also"></a>Voir aussi  
 [Étendre des diagrammes et des modèles UML](../modeling/extend-uml-models-and-diagrams.md)   
 [Afficher un modèle UML sur des diagrammes](../modeling/display-a-uml-model-on-diagrams.md)
