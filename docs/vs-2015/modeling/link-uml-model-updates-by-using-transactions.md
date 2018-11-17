---
title: Lier des mises à jour du modèle UML à l’aide de transactions | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML API, transactions
ms.assetid: a1df6c38-a3d1-4a3f-82bc-c8f363ab916e
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: fb8bb5dfd5238871324b786f120d618d70f14b43
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51800404"
---
# <a name="link-uml-model-updates-by-using-transactions"></a>Lier des mises à jour de modèles UML à l’aide de transactions
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Lorsque vous définissez une extension des concepteurs UML dans Visual Studio, vous pouvez regrouper plusieurs modifications dans une transaction unique appelée un *contexte d’annulation lié*. Pour connaître les versions de Visual Studio qui prennent en charge les modèles UML, consultez [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 Par défaut, chaque modification apportée par votre code à un modèle peut être annulée séparément par l'utilisateur. Par exemple, si vous définissez une commande de menu qui intervertit les noms de deux classes UML, un utilisateur peut appeler la commande et exécuter une annulation unique. Cela annulerait la modification apportée à un nom, mais pas à l'autre, et laisserait donc votre modèle dans un état non souhaitable.  
  
 Pour éviter cela, votre code peut exécuter une série de modifications dans une transaction. Ainsi, aux yeux de l'utilisateur les modifications semblent n'en être qu'une seule. Une commande d'annulation ultérieure annulera toute la série.  
  
 Un autre avantage est que votre code peut annuler un ensemble de modifications partiellement complet en levant une exception ou en abandonnant la transaction.  
  
## <a name="to-group-changes-into-a-single-transaction"></a>Pour regrouper plusieurs modifications dans une même transaction  
 Assurez-vous que vos références de projet incluent cet assembly .NET :  
  
 **Microsoft.VisualStudio.Modeling.Sdk. [version] .dll**  
  
 Dans votre classe, déclarez une propriété importée de type <xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement.ILinkedUndoContext> :  
  
 `using Microsoft.VisualStudio.Modeling.ExtensionEnablement;`  
  
 `...`  
  
 `class … {`  
  
 `[Import]`  
  
 `public ILinkedUndoContext LinkedUndoContext { get; set; }`  
  
 Dans une méthode qui modifie le modèle, insérez vos modifications dans une transaction :  
  
 `using (ILinkedUndoTransaction transaction =`  
  
 `LinkedUndoContext.BeginTransaction("my updates"))`  
  
 `{`  
  
 `// code to update model elements or shapes goes here`  
  
 `transaction.Commit();`  
  
 `}`  
  
 Notez les points suivants :  
  
-   Vous devez toujours inclure `Commit()` à la fin de la transaction. Si une transaction est supprimée sans avoir été validée, elle sera restaurée. Autrement dit, le modèle sera restauré à son état au début de la transaction.  
  
-   Si une exception se produit et n'est pas interceptée dans la transaction, celle-ci sera restaurée. Placer le bloc `using` de la transaction à l'intérieur d'un bloc `try…catch` est une pratique courante.  
  
-   Vous pouvez imbriquer des transactions.  
  
-   Vous pouvez fournir un nom non vide à `BeginTransaction()`.  
  
-   Seul le magasin de modèles UML est affecté par ces transactions. Les transactions de modélisation n'affectent pas les variables, les magasins externes comme les fichiers et les bases de données, les diagrammes de couche et les modèles de code.  
  
## <a name="example"></a>Exemple  
  
```  
    using Microsoft.VisualStudio.Modeling.ExtensionEnablement;  
    using Microsoft.VisualStudio.Uml.Interfaces;  
    using Microsoft.VisualStudio.Uml.Classes;  
    using Microsoft.VisualStudio.Uml.Extensions;  
    using System.Linq;  
    using System.ComponentModel.Composition;  
 ...  
  [Import]  
  public ILinkedUndoContext LinkedUndoContext { get; set; }  
  
  /// <summary>  
  /// Swap the names of the currently selected elements.  
  /// </summary>  
  public void Execute(IMenuCommand command)  
  {  
    var selectedShapes =  
      Context.CurrentDiagram.GetSelectedShapes<IClassifier>();  
    if (selectedShapes.Count() < 2) return;  
    IClassifier firstElement = selectedShapes.First().Element;  
    IClassifier lastElement = selectedShapes.Last().Element;  
    string firstName = firstElement.Name;  
    // Perform changes inside a transaction so that undo  
    // works as a single change.  
    using (ILinkedUndoTransaction transaction =   
      LinkedUndoContext.BeginTransaction("Swap names"))  
    {  
        firstElement.Name = lastElement.Name;  
        lastElement.Name = firstName;  
        transaction.Commit();  
    }  
 }  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Programmation avec l’API UML](../modeling/programming-with-the-uml-api.md)   
 [Définir une commande de menu sur un diagramme de modélisation](../modeling/define-a-menu-command-on-a-modeling-diagram.md)   
 [Étendre des diagrammes et des modèles UML](../modeling/extend-uml-models-and-diagrams.md)



