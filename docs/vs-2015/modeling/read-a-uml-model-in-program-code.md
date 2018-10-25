---
title: Lire un modèle UML dans le code de programme | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML API, reading models
ms.assetid: 0f63105e-6079-498a-94f1-318c0f5f9621
caps.latest.revision: 25
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: c9bb652ee6b7ea9500d2ac153ca06d8b11430c9e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2018
ms.locfileid: "49942543"
---
# <a name="read-a-uml-model-in-program-code"></a>Lire un modèle UML dans le code de programme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Vous pouvez charger un modèle UML et ses diagrammes à l'aide de l'API UML.  
  
##  <a name="Reading"></a> Lecture d’un modèle de Code de programme  
 Pour accéder au contenu d'un modèle sans l'afficher dans une fenêtre [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], utilisez `ModelingProject.LoadReadOnly()`.  
  
 Exemple :  
  
```  
using Microsoft.VisualStudio.Uml.Classes;   
               // for IElement  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility;   
               // for ModelingProject  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
               // for IModelStore  
...   
string projectPath = @"C:\MyProjectFolder\MyProject.modelproj";  
using (IModelingProjectReader projectReader =  
           ModelingProject.LoadReadOnly(projectPath))  
{  
   IModelStore store = projectReader.Store;  
   foreach (IClass umlClass in store.AllInstances<IClass>())  
   {   
       ...  
   }  
}  
```  
  
 Si vous voulez lire les formes dans un diagramme, vous devez lire le projet, puis le diagramme.  
  
 Exemple :  
  
```  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;   
                             // for IDiagram  
...  
foreach (string diagramFile in projectReader. DiagramFileNames)  
{   
  IDiagram diagram = projectReader.LoadDiagram(diagramFile);  
  foreach (IShape<IElement> shape   
         in diagram.GetChildShapes<IElement>())  
  { ... }  
}  
```  
  
## <a name="alternative-methods"></a>Autres méthodes  
 Pour de nombreuses applications, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Modelbus vous permet de référencer des modèles et des éléments qu’ils contiennent, avec une robustesse et une flexibilité encore les méthodes décrites dans cette rubrique. Il fournit une méthode standard pour créer des liens entre des éléments arbitraires, dans le même modèle ou dans des modèles différents. Pour plus d’informations, consultez [intégrer des modèles UML avec d’autres modèles et outils](../modeling/integrate-uml-models-with-other-models-and-tools.md).  
  
 Vous pouvez aussi ouvrir des modèles et des diagrammes dans l'interface utilisateur à l'aide de l'API [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Pour plus d’informations, consultez [ouvrir un modèle UML à l’aide de l’API Visual Studio](../modeling/open-a-uml-model-by-using-the-visual-studio-api.md).  
  
##  <a name="Standalone"></a> Applications autonomes  
 L'exemple de la section précédente fonctionne dans les extensions Visual Studio. Il est possible de lire un modèle dans une application autonome, mais vous devez ajouter des références à votre projet [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
> [!NOTE]
>  Les détails relatifs à la lecture d'un modèle dans une application autonome sont susceptibles de changer dans les versions ultérieures du produit. Certaines fonctionnalités accessibles dans la version actuelle risquent de ne plus être disponibles dans les versions ultérieures.  
  
#### <a name="to-add-references-to-read-a-model-in-a-stand-alone-application"></a>Pour ajouter des références pour lire un modèle dans une application autonome  
  
1. Dans l’Explorateur de solutions, cliquez sur le projet dans lequel vous créez l’application, puis cliquez sur **propriétés**. Dans l’éditeur de propriétés, dans le **Application** onglet, définissez **Framework cible** vers la version requise du .NET Framework.  
  
2. Ajoutez les références [!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)] dont vous avez besoin pour accéder aux modèles UML, en général :  
  
   -   Microsoft.VisualStudio.Uml.Interfaces.dll  
  
   -   Microsoft.VisualStudio.ArchitectureTools.Extensibility.dll  
  
3. Outre les références répertoriées dans les sections précédentes, ajoutez les références de projet suivantes à partir de **\Program Files\Microsoft Visual Studio [version] \Common7\IDE\PrivateAssemblies**:  
  
   - Microsoft.VisualStudio.Uml.dll  
  
   - Microsoft.VisualStudio.TeamArchitect.ModelStore.Dsl.dll  
  
     Si vous souhaitez lire des diagrammes dans votre application, vous aurez peut-être besoin des références suivantes :  
  
   - Microsoft.VisualStudio.TeamArchitect.ActivityDesigner.Dsl.dll  
  
   - Microsoft.VisualStudio.TeamArchitect.ComponentDesigner.Dsl.dll  
  
   - Microsoft.VisualStudio.TeamArchitect.LogicalClassDesigner.Dsl.dll  
  
   - Microsoft.VisualStudio.TeamArchitect.SequenceDesigner.Dsl.dll  
  
   - Microsoft.VisualStudio.TeamArchitect.UseCase.Dsl.dll  
  
## <a name="see-also"></a>Voir aussi  
 [Programmation avec l’API UML](../modeling/programming-with-the-uml-api.md)   
 [Étendre des diagrammes et des modèles UML](../modeling/extend-uml-models-and-diagrams.md)



