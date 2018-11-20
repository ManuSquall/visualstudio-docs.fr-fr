---
title: Ouvrir un modèle UML à l’aide de l’API Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML API, opening models in Visual Studio
ms.assetid: 38423682-f2a7-4d2a-a2cd-fd680e9b4b4d
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 62b8700e85ccab271dbfdc4f9bac504ee64197a6
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/16/2018
ms.locfileid: "51779617"
---
# <a name="open-a-uml-model-by-using-the-visual-studio-api"></a>Ouvrir un modèle UML à l'aide de l'API Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez aussi ouvrir des modèles et des diagrammes dans l'interface utilisateur de Visual Studio à l'aide de l'API.  
  
 Si vous souhaitez seulement lire un modèle dans le code du programme sans le rendre visible à l'utilisateur, vous pouvez appliquer les méthodes suivantes :  
  
-   Visual Studio Model Bus vous permet d'accéder aux modèles et aux éléments qu'ils contiennent, et fournit une méthode standard pour créer des liens entre deux modèles. Pour plus d’informations, consultez [intégrer des modèles UML avec d’autres modèles et outils](../modeling/integrate-uml-models-with-other-models-and-tools.md).  
  
-   Vous pouvez ouvrir un modèle en mode lecture seule. Pour plus d’informations, consultez [lire un modèle UML dans le code de programme](../modeling/read-a-uml-model-in-program-code.md).  
  
##  <a name="Showing"></a> Ouverture des modèles et des diagrammes dans Visual Studio  
 Pour ouvrir un modèle dans l'interface utilisateur, utilisez l'API Visual Studio standard `EnvDTE.DTE`. Il existe deux casts utiles que vous pouvez effectuer sur les éléments de projet de modélisation :  
  
- `EnvDTE.Project` peut être casté vers et depuis `IModelingProject`, si le projet est un projet de modélisation et s'il est chargé dans l'AppDomain actuel.  
  
- `EnvDTE.ProjectItem` peut être casté vers et depuis `IDiagramContext`, si l'élément est un diagramme UML.  
  
  Pour l'exemple suivant, votre projet doit importer ces références :  
  
- EnvDTE  
  
- Microsoft.VisualStudio.ArchitectureTools.Extensibility  
  
- Microsoft.VisualStudio.Modeling.Sdk.[version]  
  
- Microsoft.VisualStudio.Modeling.Sdk.Diagrams.[version]  
  
- Microsoft.VisualStudio.Shell.Immutable. [version]  
  
- Microsoft.VisualStudio.Uml.Interfaces  
  
- System.ComponentModel.Composition  
  
  Cet exemple ouvre un modèle UML dans Visual Studio :  
  
```  
using EnvDTE; // Visual Studio API for loading diagrams  
using   
using System.ComponentModel.Composition;  
using Microsoft.VisualStudio.Modeling;   
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;    
   // for ICommandExtension and other handler types  
using Microsoft.VisualStudio.Uml.Classes;   
   // for basic UML types  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
   // for model construction methods  
using EnvDTE;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility;  
Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;   
                             // for IDiagram   
...  
```  
  
 Dans une extension Visual Studio, vous pouvez effectuer cette déclaration pour obtenir l'accès au fournisseur de services hôte :  
  
```  
[Import] public Microsoft.VisualStudio.Shell.SVsServiceProvider ServiceProvider {get;set;}  
...  
```  
  
 Dans une méthode, vous pouvez accéder à un projet, par exemple le projet actuel :  
  
```  
DTE dte = (DTE)ServiceProvider.GetService(typeof(DTE));  
Project project = dte.ActiveDocument.ProjectItem.ContainingProject;  
IModelingProject modelingProject = project as IModelingProject;  
if (modelingProject == null) return; // not a modeling project  
  
// Access the model's store and contents.  
IModelStore store = modelingProject.Store;  
foreach (IElement element in store.Root.OwnedElements) {...}  
  
// Open all the project's diagrams.  
foreach (ProjectItem item in project.ProjectItems)  
{   
     IDiagramContext modelingItem = item as IDiagramContext;  
     if (modelingItem == null)  
         continue; // not a model diagram  
     IDiagram diagram = modelingItem.CurrentDiagram;  
     if (diagram == null)  
     {  
        // Diagram is closed. Open it.  
        item.Open().Activate();  
        diagram = modelingItem.CurrentDiagram;  
     }  
     // Access the shapes.  
     foreach (IShape<IElement> shape   
               in diagram.GetChildShapes<IElement>())  
     {  
       IElement displayedElement = shape.Element;  
       ...  
     }  
   }  
}   
```  
  
## <a name="see-also"></a>Voir aussi  
 [Programmation avec l’API UML](../modeling/programming-with-the-uml-api.md)   
 [Étendre des diagrammes et des modèles UML](../modeling/extend-uml-models-and-diagrams.md)



